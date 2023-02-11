<a name="readme-top"></a>

<h1 align="center">Projeto Blogs API 📑</h1>

<details>
  <summary>Sumário</summary><br />
  <ol>
    <li><a href="#sobre-o-projeto">Sobre o Projeto</a></li>
    <li><a href="#tecnologias">Tecnologias</a></li>
    <li><a href="#funcionalidades">Funcionalidades</a></li>
    <li><a href="#como-executar-o-projeto">Como Executar o Projeto</a></li>
    <li><a href="#endpoints">Endpoints</a></li>
    <li><a href="#habilidades">Habilidades</a></li>
    <li><a href="#sobre-a-trybe">Sobre a Trybe</a></li>
    <li><a href="#contato">Contato</a></li>
  </ol>
</details>

## Sobre o Projeto

Projeto **22** do curso de Desenvolvimento Web da [Trybe][trybe-site-url].

<!-- DESCRIÇÃO DO PROJETO -->

<br/>

## Tecnologias

- [Docker][docker-url]
- [dotenv][dotenv-url]
- [ESLint][eslint-url]
- [Express][express-url]
- [JavaScript][javascript-url]
- [Joi][joi-url]
- [JWT][jwt-url]
- [MySQL][mysql-url]
- [Node.js][node-url]
- [Nodemon][nodemon-url]
- [Sequelize][sequelize-url]

<br/>

## Funcionalidades

<!-- <ul>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul> -->

<br/>

## Como Executar o Projeto

Para rodar o projeto, siga os passos abaixo.

1. Clone o repositório;

```
git@github.com:garciaagui/trybe-project-22_blogs-api.git
```

2. Navegue até a raiz do projeto;

```
cd trybe-project-22_blogs-api/
```

- 🔘 Agora, decida se o projeto será rodado localmente ou via Docker.

<details>
  <summary><strong>💽 Localmente</strong></summary>

1. Certifique-se que você tenha o **node** instalado na versão 16 ou superior. Confira [aqui](https://nodejs.org/pt-br/download/package-manager/) a documentação oficial.

2. Na raiz do projeto, instale as dependências do projeto.

```
npm install
```

</details>

<details>
  <summary><strong>🐋 Docker</strong></summary>
  
1. Certifique-se que você tenha o **docker-compose** instalado na versão 1.29 ou superior. Links oportunos caso você precise instalar ou atualizar: [Tutorial DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04-pt) e [documentação oficial](https://docs.docker.com/compose/install/);

2. Suba os containers executando o comando abaixo. Dois containers serão inicializados: `blogs_api` (node) e `blogs_api_db` (mysql).

```
docker-compose up -d --build
```

3. Acesse a CLI do container `blogs_api` com o comando abaixo ou abra-o no VS Code. Para a última opção, recomendo a extensão da Microsoft [Dev Containers](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers).

```
docker exec -it blogs_api bash
```

4. Dentro do container `blogs_api`, instale as dependências do projeto.

```
npm install
```

</details>

<br/>

## Endpoints

Abaixo você pode conferir um detalhamento dos endpoints utilizados no projeto. Para realizar as requisições HTTP e consultar o comportamento de cada endpoint, você pode utilizar a extensão [Thunder Client](https://www.thunderclient.com/).

> ⚠️ Atente-se ao token gerado durante o login, ele será necessário para todas as operações. Lembre-se também que seu tempo de expiração é de 1h.

<details>
  <summary><strong>Login</strong></summary>

### POST /login

- Valida o login do usuário e retorna um token gerado com jsonwebtoken (jwt).
- O token gerado deve ser inserido no Header `Authorization` para autenticar outras operações. Lembre-se de guardá-lo e tenha em mente que seu tempo de expiração é de 1h.
- URL: `http://localhost:PORT/login`
- O corpo da requisição deve seguir o formato abaixo:

```
{
  "email": "lewishamilton@gmail.com",
  "password": "123456"
}
```

---

</details>

<details>
  <summary><strong>User</strong></summary>

### GET /user

- Retorna todos os users cadastrados no banco de dados.
- URL: `http://localhost:PORT/user`

### GET /user/:id

- Retorna o user cujo id foi passado no endpoint.
- Exemplo de URL: `http://localhost:PORT/user/1`

### POST /user

- Adiciona um novo user ao banco de dados.
- URL: `http://localhost:PORT/user`
- O corpo da requisição deve seguir o formato abaixo:

```
{
  "displayName": "Brett Wiltshire",
  "email": "brett@email.com",
  "password": "123456",
  "image": "http://4.bp.blogspot.com/_YA50adQ-7vQ/S1gfR_6ufpI/AAAAAAAAAAk/1ErJGgRWZDg/S45/brett.png"

  // a image não é obrigatória
}
```

### DELETE /user/me

- Deleta o user que está logado, baseado no id que esta dentro do token.
- URL: `http://localhost:PORT/user/me`

---

</details>

<details>
  <summary><strong>Categories</strong></summary>

### GET /categories

- Retorna todas as categorias cadastradas no banco de dados.
- URL: `http://localhost:PORT/categories`

### POST /categories

- Adiciona uma nova categoria ao banco de dados.
- URL: `http://localhost:PORT/categories`
- O corpo da requisição deve seguir o formato abaixo:

```
{
  "name": "Typescript"
}
```

---

</details>

<details>
  <summary><strong>Post</strong></summary>

### GET /post

- Retorna todos os blog posts registrados no banco de dados.
- URL: `http://localhost:PORT/post`

### GET /post/:id

- Retorna o blog post cujo id foi passado no endpoint.
- Exemplo de URL: `http://localhost:PORT/post/1`

### GET /post/search

- Retorna todos os blog posts cujos title ou content possuam o termo pesquisado na query.
- Exemplo de URL: `http://localhost:PORT/post/search?q=vamos`

### POST /post

- Adiciona um novo blog post ao banco de dados.
- URL: `http://localhost:PORT/post`
- O corpo da requisição deve seguir o formato abaixo:

```
{
  "title": "Latest updates, August 1st",
  "content": "The whole text for the blog post goes here in this key",
  "categoryIds": [1, 2]
}
```

### PUT /post/:id

- Atualiza o blog post cujo id foi passado no endpoint.
- Exemplo de URL: `http://localhost:PORT/post/1`
- O corpo da requisição deve seguir o formato abaixo:

```
{
  "title": "Latest updates, August 1st",
  "content": "The whole text for the blog post goes here in this key"
}
```

### DELETE /post/:id

- Deleta o blog post cujo id foi passado no endpoint.
- Exemplo de URL: `http://localhost:PORT/post/1`

---

</details>

<br/>

## Habilidades

<!-- <ul>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
  <li></li>
</ul> -->

<br/>

## Sobre a Trybe

_"A [Trybe][trybe-site-url] é uma escola do futuro para qualquer pessoa que queira melhorar de vida e construir uma carreira de sucesso em tecnologia, onde a pessoa só paga quando conseguir um bom trabalho."_

_"O programa conta com mais de 1.500 horas de aulas presenciais e online, aborda introdução ao desenvolvimento de software, front-end, back-end, ciência da computação, engenharia de software, metodologias ágeis e habilidades comportamentais._"

<br/>

## Contato

Projeto desenvolvido por Guilherme Garcia. Seguem abaixo minhas redes sociais e meios de contato. 🤘

[![Gmail][gmail-badge]][gmail-url]
[![Linkedin][linkedin-badge]][linkedin-url]
[![GitHub][github-badge]][github-url]
[![Instagram][instagram-badge]][instagram-url]

<p align="right"><a href="#readme-top">Voltar ao topo</a></p>

<!-- MARKDOWN LINKS & IMAGES -->

[trybe-site-url]: https://www.betrybe.com/

<!-- Stacks URLs -->

[docker-url]: https://www.docker.com/
[dotenv-url]: https://www.dotenv.org/
[eslint-url]: https://eslint.org/
[express-url]: https://expressjs.com/
[javascript-url]: https://developer.mozilla.org/en-US/docs/Web/JavaScript
[joi-url]: https://joi.dev/api/?v=17.7.0
[jwt-url]: https://jwt.io/
[mysql-url]: https://www.mysql.com/
[node-url]: https://nodejs.org/en/
[nodemon-url]: https://nodemon.io/
[sequelize-url]: https://sequelize.org/

<!-- Contact URLs & Badges -->

[gmail-badge]: https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white
[gmail-url]: mailto:garciaguig@gmail.com
[linkedin-badge]: https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white
[linkedin-url]: https://www.linkedin.com/in/garciaagui/
[github-badge]: https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white
[github-url]: https://github.com/garciaagui
[instagram-badge]: https://img.shields.io/badge/Instagram-E4405F?style=for-the-badge&logo=instagram&logoColor=white
[instagram-url]: https://www.instagram.com/garciaagui/
