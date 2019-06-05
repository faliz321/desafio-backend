# Api de cadastro de usuários em laravel 5.8 + passport com autenticação

Esse é o nosso desafio para a vaga de desenvolvedor Back-end  no [Grupo Zanon](http://www.grupozanon.com.br/). 
- Autor: Hugo Cesar Alonso Generoso

# Dependências para executar o projeto
    SQL Server instalado e executando na porta 3306.
    Versão 5.8 do Laravel instalado.    

# Instalando e executando o projeto
Crie um usuário root sem senha (apenas para testar a api).
Crie um banco de dados MySQL com o nome "desafio-backend". 
Clone este repositório na pasta desejada.
Acesse a pasta do projeto clonado e execute os comandos no terminal.
```sh
 cd desafio-backend
 composer install
 php artisan:generate key
 php artisan:migrate
 php artisan:db seed
 php artisan:passport install
 php artisan serve
```
O projeto já será executado no endereço <http://127.0.0.1:8000>.
Quando o artisan:migrate foi executado, todas as tabelas do projeto serão criadas no db "desafio-backend".
Quando o artisan:db seed foi executado, um usário admin será criado com o email huggo11@icloud.com e a senha "testezanon", a conta de admin será usada como camada de segurança para fazer alterações na tabela de usuários.

# Usando o postman para testar a Api

    #Efetuando o login de aministrador da ferramenta (admin usado no exemplo):
        Em uma nova aba selecione o metodo "POST"
        A url para login é "127.0.0.1:8000/api/v1/login"
        Parametros:
                "key"     |  "value"
                 -------------------------------
                 email    |  huggo11@icloud.com
                 password |  testezanon
                 
    Envie a requisição e a resposta irá lhe devolver o token de autenticação do usuário logado, copie-o para usar na autenticação das chamadas que modificam o usuário;
    
    -
    
    #Recebendo os dados usuário logado atualmente:
        Em uma nova aba selecione o metodo "GET"
        #Importante na aba de "Authorization" do Postman selecionar um token do tipo "Bearer Token" com o valor do token que foi recebido no login.
        A url para ver os dados do usuário logado é "127.0.0.1:8000/api/v1/getUser"
        A resposta irá lhe retornar os dados do usuário logado.
    
    -
    
    #Efetuando o registro de um novo usuário (necessário login como admin):
        Em uma nova aba selecione o metodo "POST"
        #Importante na aba de "Authorization" do Postman selecionar um token do tipo "Bearer Token" com o valor do token que foi recebido no login.
        A url para registrar um usuário é 1"27.0.0.1:8000/api/v1/registerUser"
        Parametros:
                "key"          |  "value"
                 ------------------------------------
                 name          |  Usuario Teste
                 email         |  teste@teste.com
                 password      |  testezanon123
                 c_password    |  testezanon123
                 cpf           |  00000000001

    Envie a requisição e resposta irá lhe devolver o resultado da chamada dizendo se o usuário foi registrado ou se ocorreu um erro.
    
    -
    
    #Editando um usuário (necessário login como admin):
    Em uma nova aba selecione o metodo "POST"
    #Importante na aba de "Authorization" do Postman selecionar um token do tipo "Bearer Token" com o valor do token que foi recebido no login.
    A url para editar um usuário é "127.0.0.1:8000/api/v1/editUser"
    Parametros:
                "key"          |  "value"
                 ------------------------------------
                 name          |  Novo Nome Usuário
                 email         |  teste@teste.com

    Envie a requisição e a resposta irá lhe devolver o resultado da chamada dizendo se o usuário foi editado ou se ocorreu um erro.
    
    -
    
    #Removendo um usuário (necessário login como admin):
    Em uma nova aba selecione o metodo "POST"
    #Importante na aba de "Authorization" do Postman selecionar um token do tipo "Bearer Token" com o valor do token que foi recebido no login.
    A url para remover um usuário é é "127.0.0.1:8000/api/v1/removeUser"
    Parametros:
                "key"          |  "value"
                 -----------------------------------
                 email         |  teste@teste.com

    Envie a requisição e a resposta irá lhe devolver o resultado da chamada dizendo se o usuário foi removido ou se ocorreu um erro.
    
    -
    
    #Efetuando o logout de usuário:
        Em uma nova aba selecione o metodo "POST"
        A url para logout é "127.0.0.1:8000/api/v1/logout"
                 
    Envie a requisição e a resposta irá lhe devolver o o resultado da chamada dizendo se o usuário foi deslogado ou se ocorreu um erro;
    
    

**Qualquer dúvida estou à disposição. Obrigado ao pessoal do Grupo Zanon pela oportunidade de participar da equipe :)**
