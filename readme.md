<h1>Simple-CRUD-Node</h1>

<p align="justify">O Projeto é um CRUD, onde o usuario pode criar sua conta, recuperar a senha por meio de token, ter acesso a estrutura de pastas para criar, atualizar e remover projetos que fazem parte da conta.</p>

<p align="justify">Os Testes de API REST foram feitos no Insomnia, As Rotas de Usuario e de Projetos estão na pasta Controllers. Quando o usuario esquece a senha, ele pode recuperar por email, com isso ele vai receber uma mensagem com um token.</p>

<p align="justify">Existem dois arquivos em JSON para fazer a configuração do email por SMTP(mailer.json) e a criação de um token secreto em MD5(auth.json), com isso o usuario tem até Uma hora, para a troca de senha. A relação do banco de dados está na pasta models, com o project, task e user.</p>

<p align="justify">Para solicitar as autenticações e os parâmetros de usuario, usei o JWT e Bearer, para ter um "padrão" de Token.</p>

<h2>Montei o projeto usando:</h2>
==

- <a href="https://nodejs.org/en/">NodeJS </a>
- <a href="https://www.mongodb.com/">MongoDB,</a>
- <a href="https://expressjs.com/">ExpressJS</a>
- Mailtrap (testes por email)

<h2>Usei as seguintes Tecnologias, para o node:</h2>
==

- <a href="https://www.npmjs.com/package/body-parser">body-parser</a>
- <a href="https://www.npmjs.com/package/nodemailer-express-handlebars">Express Handlebars </a>
- <a href="https://github.com/dcodeIO/bcrypt.js#readme">bcryptJS</a>
- <a href="https://github.com/auth0/node-jsonwebtoken#readme">Json WebToken</a>
- <A href="https://www.npmjs.com/package/path">path</A>


<h2>Instalação e uso:</h2>
=
Use o gerenciador de pacotes de sua preferência, depois de um node **src/index.js** no cmd ou terminal

Para testar a **API REST** eu uso o **Insonmia**. Mas pode ser usado qualquer ferramenta de API REST, como o Swagger, PostManV2, entre outros.

----

# *Conta de Usuario*

## 1. Para criar a conta use:

~~~html 

POST: http://localhost:3000/auth/register

~~~

~~~json 
{
	"name": "Alezzott",
	"email": "alezzott@test.com",
	"password": "123456"
}
~~~

---

## 2. Autenticar Conta:
~~~html
POST: /auth/authenticate
~~~

~~~ json 
{
	"email": "alezzott@test.como",
	"password": "12345678"
}

~~~
---

## 3. Esqueci a senha: 
~~~html
POST: /auth/forgot_password
~~~~

~~~json 
{
	"email": "alezzott@test.com"
}
~~~
---

## 4. Recuperar a conta com o token enviado por email:
~~~html
POST: /auth/reset_password
~~~

~~~json
{
	"email": "alezzott@test.com",
	"token": "57f34dad948935a93d1dce424019a7d9367f6kk7f1",
	"password": "12345678"
}
~~~
---

# *Projetos*

## 1. Criar um novo projeto
~~~~HTML
POST: /project
~~~~

~~~json
{
	"title": "Novo projeto",
	"description": "descrição de project",
	"tasks": [
		{
					 "title": "Nova Tarefa",
		"assignedTo": "612e4ca265ef692456c84777"
		},
		{
					 "title": "Outra Tarefa",
		"assignedTo": "612e4ca265ef692456c84777"
		}
	
	]
}
~~~

---

## 2. Atualizar projeto
*Use o "_id" que está em "user"*

~~~~HTML
PUT: /project/id_de_usuario
~~~~

~~~~json 
{
	"title": "Novo projeto",
	"description": "nova outra de project",
	"tasks": [
		{
			"title": "Tarefa 1",
			"assignedTo": "612e4ca265ef692456c84777"
		},
				{
			"title": "Tarefa 2",
			"assignedTo": "612e4ca265ef692456c84777"
		}
	]
}
~~~~
---



