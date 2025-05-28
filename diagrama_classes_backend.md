# 📘 Diagrama de Classes – Backend do Projeto Booklub

![Diagrama de classes do backend do projeto](https://i.imgur.com/no2geRD.png)

> Diagrama gerado para representar a estrutura de classes, entidades, serviços, controladores e gateways do backend da aplicação **Booklub**.

---

## Visão Geral

O sistema está organizado seguindo uma arquitetura limpa, com separação clara entre **entidades de domínio**, **serviços**, **repositórios**, **gateways** e **controladores**. Abaixo, explicamos cada camada.

---

## Camada de Entidades (Domínio)

As classes em **verde** representam entidades de domínio:

* **User**: representa um usuário da plataforma.
* **Club**: representa um clube que pode conter vários usuários.
* **BookUser**, **BookRatings**, **ClubPendingEntry**: entidades auxiliares que modelam relacionamentos como avaliações, participação em clubes e associação com livros.
* **BookTier**: representa a tier de um livro (provavelmente usada em gamificação ou categorização).

Relacionamentos:

* `User` possui uma associação *muitos-para-muitos* com `Club`.
* `BookRatings` e `BookUser` associam `User` com livros.
* `ClubPendingEntry` atua como entidade intermediária para solicitações de entrada em clubes.

---

## Camada de Serviços

As classes em **vermelho** representam os serviços responsáveis pela lógica de negócio:

* **UserServiceImpl**
* **AuthServiceImpl**
* **ClubServiceImpl**
* **ClubMembersServiceImpl**
* **BookUserServiceImpl**
* **BookRatingsServiceImpl**
* **UserMediaStorageServiceImpl**
* **GoogleBooksServiceImpl**

Cada serviço depende de repositórios e gateways específicos para executar suas responsabilidades, mantendo as regras de negócio isoladas da infraestrutura.

---

## Camada de Repositórios e Gateways

As classes em **roxo** representam abstrações de acesso a dados ou serviços externos:

* **UserRepository**, **ClubRepository**, **BookUserRepository**, **BookRatingsRepository**: abstrações de persistência.
* **MediaStorageGateway**, **GoogleBooksGateway**, **KeycloakGateway**: gateways para serviços externos (como armazenamento e autenticação).

Os serviços usam esses componentes para obter ou persistir dados sem depender de implementações concretas.

---

## Camada de Controladores

As classes em **azul claro** representam os controladores REST:

* **UserController**
* **AuthController**
* **BookUserController**
* **BookRatingsController**
* **BookController**

Esses controladores são responsáveis por receber requisições HTTP e delegar a lógica aos serviços correspondentes.

---

## Relações Importantes

* Os serviços dependem de entidades (relação de *uso*, com setas tracejadas no UML).
* Os repositórios são utilizados por serviços via injeção de dependência (associação).
* Controladores utilizam serviços diretamente.
* Entidades não possuem dependência com serviços ou controladores, respeitando a separação de camadas.