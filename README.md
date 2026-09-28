# Atividade backend - PWIII

## Pré-requisitos

- Node.js instalado
- Xampp instalado, incializando o Apache (por ser local) e o MySQL

## Como rodar o projeto

### 1. Iniciar o MySQL pelo Xampp

Abra o Xampp e clique em **Start** referente ao **Apache** e **MySQL**. Ele deve ficar verde caso funcione.

### 2. Instalar as dependências

```CMD (necessário pois o PowerShell/Terminal do Win não funciona)
cd backend
npm install
```

### 3. Criar o banco de dados pelo phpMyAdmin

1. Com o MySQL do Xampp rodando, acesse `http://localhost/phpmyadmin` pelo navegador de preferência;
2. Clique na aba **SQL**, próximo à opção "**Status**";
3. Abra o arquivo `schema.sql` deste projeto, copie todo o conteúdo e cole na área citada;
4. Clique em Executar (canto inferior direito).

Isso cria o banco `bancoback` e a tabela `tasks`. Você pode conferir clicando no banco `bancoback` no menu à esquerda.

### 4. Configurar o arquivo `.env`

Antes de iniciar o servidor, verifique se os dados do arquivo .env correspondem à sua instalação do MySQL/ Xampp (usuário, senha e porta). Por padrão, o projeto assume sem senha, como no Xampp padrão.

### 5. Iniciar o servidor

Modo desenvolvimento (reinicia automaticamente a cada alteração):

```bash
npm run dev
```

Se tudo estiver certo, o terminal mostrará:

```
Servidor rodando em http://localhost:3333
```

### 6. Testar a API

O navegador só consegue testar rotas GET direto pela URL. Para testar as rotas de criar, concluir e excluir tarefas (POST, PATCH, DELETE), use a extensão REST Client do VS Code:

1. Abra a extensão REST Client (procure por "REST Client" de Huachao Mao na aba de Extensões do VS Code e instale, se ainda não tiver).
2. Abra o arquivo `rotas.http`, que já vem com todas as rotas prontas para teste.
3. Clique no link **Send Request** que aparece acima de cada requisição.
4. A resposta da API vai abrir em uma aba ao lado, mostrando o status HTTP e o corpo da resposta em JSON.

Rotas GET (também podem ser testadas direto no navegador):

```
http://localhost:3333/health
http://localhost:3333/api/tasks
```

### Exemplo — criar tarefa

```json
POST /api/tasks
Content-Type: application/json

{
  "title": "Estudar sobre Node.js e suas extensões",
  "dueDate": "2026-09-30"
}
```

### Exemplo — concluir tarefa

```json
PATCH /api/tasks/1
Content-Type: application/json

{ "completed": true }
```
