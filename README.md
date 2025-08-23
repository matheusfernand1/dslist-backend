Aqui está um guia simples para subir e testar sua aplicação DSList usando Docker e Maven.

## Como subir a aplicação

1. **Clone o repositório**
   ```bash
   git clone https://github.com/matheusfernand1/dslist-backend.git
   cd dslist-backend
   ```

2. **Configure variáveis de ambiente**
   Crie um arquivo `.env` (ou defina as variáveis no Docker Compose) com:
   ```
   DB_URL=jdbc:postgresql://<host>:<porta>/<database>
   DB_USERNAME=<usuario>
   DB_PASSWORD=<senha>
   ```

3. **Construa e rode com Docker**
   ```bash
   docker build -t dslist-app .
   docker run -p 8080:8080 --env-file .env dslist-app
   ```
   Ou, se usar Docker Compose, adapte o serviço conforme necessário.

## Como testar a aplicação

1. **Acesse a API**
    - Abra o navegador ou use o Postman para acessar:  
      `http://localhost:8080`

2. **Endpoints principais**
    - Listas de jogos:  
      `GET /lists`
    - Jogos por lista:  
      `GET /lists/{listId}/games`

3. **Testes automatizados**
    - Para rodar os testes do projeto:
      ```bash
      mvn test
      ```

## Observações

- O perfil ativo padrão é `prod`. Para mudar, altere o parâmetro no Dockerfile ou defina a variável `APP_PROFILE`.
- Certifique-se que o banco de dados PostgreSQL está rodando e acessível.
- Certifique-se de que o script create.sql foi executado para criar as tabelas necessárias, caso nao tenha sido, basta executar o script manualmente.

Pronto! Sua aplicação estará disponível em `localhost:8080`.