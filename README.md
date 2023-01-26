## Jumba
### Comandos

Build dos containers

`docker-compose build -d`

Instalando as dependências do laravel 

`docker-compose exec -w /var/www/html/jumba-app app composer install`

Instalando as dependências do npm

`docker-compose run --rm -w /var/www/html/jumba-app npm install`

Configurações da aplicação

`docker-compose exec -w /var/www/html/jumba-app app php artisan config:cache`

Criando as migrações do banco de dados  

`docker-compose exec -w /var/www/html/jumba-app app php artisan migrate --seed`
 
Para acessar a aplicação 

`docker-compose run --rm -p 5173:5173 -w /var/www/html/jumba-app npm run dev -- --host`

### Start Application 

Acesse: [jumba.localhost:8080](http://jumba.localhost:8080)

**_NOTE:_** Para fazer o login, pegar qualquer email do banco de dados e usar a senha: `password`

#### _DB CONECCTION_
DB_HOST=db\
DB_PORT=33060\
DB_DATABASE=jumba\
DB_USERNAME=jumbauser\
DB_PASSWORD=jumbatest

### Start Jobs
`docker-compose exec -w /var/www/html/jumba-app app php artisan queue:work --timeout=2000`

### Start Tests  

Configurando o banco de dados Sqlite

`docker-compose exec -w /var/www/html/jumba-app app php artisan --env=testing migrate`

Rodar todos os teste 

`docker-compose exec -w /var/www/html/jumba-app app php artisan --env=testing test`

Rodar apenas os teste unitários

`docker-compose exec -w /var/www/html/jumba-app app php artisan --env=testing test --testsuite=Unit`

Rodar apenas os teste de integração

`docker-compose exec -w /var/www/html/jumba-app app php artisan --env=testing test --testsuite=Feature`