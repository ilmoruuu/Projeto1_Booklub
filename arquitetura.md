# Documentação da Arquitetura de Software

## 1. Arquitetura de Software Escolhida 

### 1.1. Qual arquitetura de software foi escolhida para o projeto?
O Booklub consistirá em duas aplicações, back-end e front-end. A primeira
consiste em uma *API* *Rest* desenvolvida usando a linguagem *Java* e
*framework* *Spring Boot*. A segunda é um aplicativo *mobile* desenvolvido
utilizando a linguagem *Dart* e *framework* *Flutter*. A comunicação entre as
duas aplicações será feita utilizando uma arquitetura cliente-servidor.

Em relação às arquiteturas internas da aplicações, serão utilizados o MVC 
(Model, View, Controller) e MVVM (Model, View, View Model) no *Back-end* e
*Front-end*, respectivamente.

#### 1.1.1. Arquitetura Front-end

O **Front-end do Booklub** adota uma arquitetura baseada no padrão [MVVM (Model-View-ViewModel)](https://docs.flutter.dev/app-architecture/guide), com adaptações que visam maior clareza, escalabilidade e facilidade de manutenção.

#### 1.1.2. Arquitetura Back-end
No *back-end* adotamos a arquitetura MVC e uma versão simplificada do *Domain-Driven Design (DDD)* devido ao escopo inicial do sistema.

### 1.2. Justifique a escolha dessa arquitetura em relação ao tipo de sistema proposto:
A arquitetura cliente-servidor foi escolhida para guiar a comunicação entre o
sistema *back-end* e *front-end* para seguir os princípios do Rest. A utilização
de tal arquitetura favorece alguns aspectos como:

- **Separação de responsabilidades**: o cliente preocupa-se com a interface de 
usuário e sua experiência, enquanto o servidor lida com o armazenamento, regras 
de negócios e fornecimento de dados;

- **Escalabilidade**: servidores podem ser escalados para atender múltiplos 
clientes em diferentes plataformas (*web*, *mobile*, *IoT*);

- **Reutilização e Interoperabilidade**: a mesma *API* *Rest* desenvolvida pode 
ser utilizada por diferentes aplicativos e sistemas, já que a comunicação 
via *HTTP* é um protocolo amplamente suportado;

- **Manutenibilidade**: alterações no front-end (cliente) não exigem mudanças 
no **back-end** e vice-versa, contanto que a **API** continue respeitando o 
contrato estabelecido;

No *front-end*, a arquitetura *MVVC* favorece a separação de responsabilidades 
entre a interface, a lógica de negócios e o acesso a dados, sendo também a
arquitetura recomendada pela própria equipe de desenvolvimento do *Flutter*.

No *back-end* a arquitetura escolhida foi o *MVC* em conjunto com uma versão 
simplificada do *DDD*, focando nas funcionalidades essenciais e interações entre 
os componentes do sistema. A simplificação visa permitir uma rápida evolução 
do projeto enquanto mantemos uma estrutura clara e bem organizada.


## 2. Diagrama da Arquitetura

### 2.1. Insira o diagrama da arquitetura proposta  

#### 2.1.1. Front-end

![Diagrama do padrão arquitetural *MVVM*](https://docs.flutter.dev/assets/images/docs/app-architecture/guide/feature-architecture-simplified-with-logic-layer.png)  


![Diagrama com estrutura do projeto](https://i.imgur.com/iHU3Ydg.png)

#### 2.1.2. Back-end
![Diagrama com DDD simplificado](https://i.imgur.com/PvItI7K.png)

### 2.2. Descreva os componentes e camadas do sistema representados no diagrama

#### 2.1.1. Front-end
A estrutura do projeto *front-end* organiza os componentes em três camadas 
principais, alinhadas ao MVVM, mas distribuídas de forma a separar claramente a 
lógica de domínio da infraestrutura:

- **`ui` (UI Layer)**: contém as páginas, componentes visuais reutilizáveis, layouts e os *view models*, responsáveis por gerenciar o estado da interface e a lógica de interação do usuário.
- **`domain` (Domain/Logic Layer)**: concentra as regras de negócio, entidades, interfaces para *repositories* e *gateways*, além de *use cases* opcionais para lógica complexa ou reutilizável.
- **`infra` (Data/Infrastructure Layer)**: implementa os *repositories*, *gateways* e *services* que acessam APIs e outras fontes externas de dados, isolando a lógica de infraestrutura da lógica de negócio.

Essa organização favorece testes, reutilização de código e evolução da aplicação com menor acoplamento entre as partes.

Observe que, como dito anteriormente, os componentes que compõe a arquitetura
*MVVM* ainda estão presentes nesta arquitetura adaptada. A seguir, está um
esquema que destaca através de quadrados tracejados violetas, os componentes
e suas respecitivas camadas no modelo *MVVM* que estão presentes nesta 
arquitetura.

![Diagrama que mostra onde as camadas do *MVVM* se encaixam na arquitetura do projeto](https://i.imgur.com/erSQOtk.png)

#### 2.1.2. Back-end
No *back-end* a arquitetura será organizada em quatro camadas principais, conforme descrito 
a seguir:

**Camada 1: Camada de Apresentação (*Presentation*)**  
Esta camada é responsável pela interação com o usuário ou com outros sistemas,
como o frontend do aplicativo do *Booklub*. A *API* expõe os endpoints *RESTful*
que permitem a comunicação entre o cliente e o servidor. Cada endpoint 
corresponde a uma ação no domínio (criar clubes, adicionar usuários, etc.) e
recebe ou envia dados no formato *JSON*.

**Responsabilidades:**  
- Receber requisições HTTP. 
- Validar dados de entrada.
- Chamar os serviços da camada de Aplicação. 
- Retornar as respostas para o cliente.

**Camada 2: Camada de Aplicação (*App*)**  
A camada de aplicação orquestra a lógica de negócios (camada de 
negócios) com a lógica de implementação (camada de infraestrutura) para entregar
resultados à camada de apresentação. Ela contém os serviços de aplicação,
responsáveis por processar as requisições recebidas da camada de 
apresentação e interagir com a camada de domínio. Nela também estão os *Data
Transfer Objects (DTO)* que definem diferentes formas como os dados das
entidades do modelo de negócios são expostas à camada de apresentação

**Responsabilidades:**  
- Processar os casos de uso (ex.: criar um novo clube, inscrever um usuário 
  em um clube, etc.).
- Validar a lógica de negócios, se necessário.
- Invocar os repositórios da camada de Domínio para persistir ou recuperar dados.

**Camada 3: Camada de Domínio (*Domain*)**  
A camada de domínio contém o núcleo do sistema, onde reside a lógica de negócios
essencial. Devido ao escopo inicial do projeto, e para manter a simplicidade, 
essa camada apenas conterá as entidades do sistema e interfaces dos repositórios
e *gateways*. Essas interfaces fornecem uma abstração para partes do sistema que
requerem detalhes de implementação como acesso a *API*s e banco de dados que não
têm ligação direta com o domínio de negócios, o que permite desacoplar a lógica 
de negócios das tecnologias utilizadas. O objetivo dessa camada é refletir o
modelo de negócios de forma rica e coesa.

**Responsabilidades:**  
- Modelar o domínio do problema (ex.: Clube, Usuário, Livro).
- Definir interfaces para abstrair detalhes de implementação (*repositories* e
  *gateways*)

**Camada 4: Camada de Infraestrutura (*Infra*)**  
A camada de infraestrutura lida com os aspectos técnicos do sistema que não 
estão diretamente relacionados à lógica de negócios, como persistência de dados, 
comunicação com APIs externas, segurança e envio de e-mails. Ela fornece 
implementações concretas às interfaces definidas na camada de domínio e usadas 
na camada de aplicação.

**Responsabilidades:**  
- Implementar a persistência de dados.
- Conectar-se com APIs externas.
- Implementar serviços de autenticação e segurança.

## 3. Escolhas Tecnológicas 

### 3.1. Quais tecnologias foram escolhidas para implementar o sistema?
- Linguagem de programação: *Java* e *Dart*
- Frameworks e bibliotecas: *Spring Boot* e *Flutter*
- Banco de dados: *PostgreSQL*
- Outras ferramentas (ex: autenticação, testes, versionamento):
    - API para pegar informações dos livros: Google Books
    - API para autenticação: Keycloak
    - API para armazenar mídias: MinIO

### 3.2. Justifique suas escolhas em relação aos requisitos do sistema
A linguagem *Java*, em conjunto com o *framework Spring Boot*, é uma das maneiras 
mais comuns e consolidadas de criar uma *API Rest*, devido às facilidades
oferecidas pelas bibliotecas que integram o *framework*, o que permite um 
desenvolvimento rápido e estruturado de aplicações robustas.

Por outro lado, o *Dart* e o *Flutter* foram escolhidos no desenvolvimento
*front-end* devido à sua grande portabilidade, já que um único projeto pode ser
aproveitado para ambientes *desktop*, *mobile* e *web*. Assim, apesar do
objetivo inicial do *Booklub* ser desenvolver um aplicativo *mobile*, tal
flexibilidade facilitará expansões futuras a outras plataformas.

O banco *PostgreSQL* foi escolhido devido à maior familiaridade que os membros
da equipe de desenvolvimento apresentam com a ferramenta, além de ser uma das
ferramentas de gerenciamento de bancos de dados mais utilizadas no mercado.

As *API*s externas foram utilizadas para suportar algumas funcionalidades extras 
ao ecossistema do *Booklub*. A *API* *Google Books* irá fornecer informações 
sobre livros, além de fornecer meios de pesquisá-los. O *KeyCloak* foi escolhido
para terceirizar a lógica de autenticação e poupar o tempo de desenvolvimento 
com uma autenticação própria, já que essa ferramenta oferece diversas 
facilidades como integração rápida com o PostgreSQL e geração de *Tokens* *JWT*. 
Por fim, o MinIO foi utilizado para armazenar arquivos de mídia, apresentando
o diferencial de ser uma alternativa *open source* ao serviço *AWS S3* fornecido
pela *Amazon*.
