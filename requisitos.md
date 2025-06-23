### Histórico de versões 

| Autor(es) | Versão | Data       | Descrição                               |
|-------|-------|------------|------------------------------------------|
| Murilo Lucena, Salomão Mendes e Michael Albuquerque | 1.0.0  | 29/05/2025 | Primeira versão do documento|



### Introdução 

#### 1.1 Propósito 
O propósito deste documento é fornecer uma visão geral do sistema denominado “Booklub”, uma plataforma mobile que conecta usuários com gostos literários semelhantes através de clubes, detalhando seus objetivos, funcionalidades e requisitos. Ele servirá como guia para a equipe de desenvolvimento e para as partes interessadas, garantindo clareza e consenso sobre o que será entregue.

#### 1.2 Escopo
O sistema “Booklub” abrangerá:
- Criação e edição do perfil do usuário,
- Criação e gerenciamento de Clubes,
- Registo, avaliação e resenhas de livros lidos,
- Acompanhamento de leituras de livros,
- Organização de encontros através do livro,
- Compra de livros.

Inicialmente o escopo não contempla funcionalidades de chamadas de áudio ou vídeo para os encontros.

#### 1.3 Visão Geral
O documento apresenta inicialmente um panorama do projeto, descrevendo a ideia do sistema e suas principais funcionalidades. Em seguida, detalha requisitos funcionais e não funcionais, regras de negócio, além de diagramas de caso de uso e de classes. Por fim, traz a rastreabilidade dos requisitos e as considerações finais.

---

### Descrição Geral 

#### 2.1 Perspectiva do Produto
A plataforma integra-se ao ecossistema de aplicações de leitura, permitindo que os usuários criem e participem de clubes de leitura. A plataforma será acessível via aplicativo móvel, dessa forma, facilitando o acesso a todos os usuários que desejam participar de um clube de leitura.

#### 2.2 Funções do Produto 
1. **Criação de perfil**: Permite criar, editar e excluir um perfil de usuário.
2. **Gerenciamento de clube**: Permite criar, buscar e participar de clubes de leitura, definir livro do mês e organizar encontros.
3. **Gestão de leituras**: Permite a Exibição de leituras recentes, leituras concluídas, definição de metas, avaliações de livros.
4. **Encontros virtuais**: Permite o agendamento e localização para encontros presenciais.
5. **Conexões Sociais**: Permite que usuários adicionem outros usuários, visualizem perfis e atividades de leitura.


#### 2.3 Características dos Usuários
- **usuários Free**: Usuários que acessam funcionalidades básicas, com limite de número de clubes.
- **usuários (Free/Premium)**: Usuários que acessam recursos exclusivos como clubes privados, número ilimitado de clubes.
- **Administradores de Clube**: Usuários que gerenciam membros do clube, definem livros e encontros.

#### 2.4 Restrições Gerais
- O sistema deve operar em dispositivos móveis (compatível com Android 10 ou superior).
- O banco de dados deve ser acessível somente dentro da rede da empresa (por questões de segurança).
- A comunicação entre o sistema e o servidor deve ser criptografado via HTTPS

---

### Requisitos Específicos

#### 3.1 Requisitos Funcionais 
1. **RF001 - Cadastrar Usuário**: O sistema deve permitir o cadastro de novos usuários com informações básicas como nome,sobrenome, username, data de nascimento,email e senha.

2. **RF002 - Autenticar Usuário**: O sistema deve permitir a autenticação dos usuários anteriormente cadastrados. O usuário, já cadastrado deve fornecer as credenciais de email e senha para ter acesso ao sistema.

3. **RF003 - Editar Perfil**: O sistema deve permitir que o usuário já registrado possa alterar suas informações básicas como nome,sobrenome, username, data de nascimento,email e senha.

4. **RF004 - Criar um Clube**: O sistema deve permitir criar um novo clube de leitura.

5. **RF005 - Participar de Clube**: O sistema deve permitir o ingresso do usuário em clubes existentes.
6. **RF006 - Pesquisar Clubes**: O sistema deve permitir a busca de clubes por nome.
7. **RF007 - Definir Tipo de Clube**: O sistema deve permitir a definição do clube como “público” (free) ou “privado” (premium).

8. **RF008 - Definir Livro do Mês**: O sistema deve permitir a seleção do livro para a leitura mensal do clube.

9. **RF009 - Buscar Livro**: O sistema deve permitir que seja realizada uma busca pelo título do livro.

10. **RF010 - Definir Livro Seguinte**: O sistema deve permitir a pré-seleção do livro do próximo mês.

11. **RF011 - Definir Data do Encontro**: O sistema deve permitir o agendamento da reunião de discussão.

12. **RF012 - Definir Local do Encontro**: O sistema deve permitir que o local do encontro seja escolhido.

13. **RF013 - Realizar Avaliação de Livros**: O sistema deve permitir que usuários dêem notas de 0 a 5 para livros.

14. **RF014 - Realizar Avaliação de Dificuldade de Livros**: O sistema deve permitir que usuários avaliem o quão fácil ou difícil é a leitura de um livro em uma escala de 0 a 5.

15. **RF015 - Escrever Avaliações**: O sistema deve permitir que usuários escrevam resenhas/comentários sobre o livro.

16. **RF016 - Aceitar Membro**: O sistema deve permitir que os administradores dos clubes permitam a entrada de novos membros.  

17. **RF017 - Recusar membro**:  O sistema deve permitir que os administradores dos clubes recusem a entrada de novos membros.

18. **RF018 - Adicionar amigos**: O sistema deve permitir que os usuários realizem pedidos de amizade para outros usuários.

19. **RF015 - Remover amigos**: O sistema deve permitir que usuários possam retirar de sua lista de amizade outros usuários anteriormente adicionados como amigos. 

20. **RF020 - Notificar**: O sistema deve permitir que os usuários visualizem suas interações como os convites de clube, solicitação de amizades, livros do mês dos clubes em que é membro e badges alcançados.

#### 3.2 Requisitos Não Funcionais 
1. **RNF001 - Desempenho**: O sistema deve responder às requisições em até 2 segundos em média.
2. **RNF002 - Segurança**: Todo acesso ao sistema deve exigir autenticação de usuário e senha. O sistema ainda deve transmitir todos os dados via HTTPS.
3. **RNF003 - Disponibilidade**: O sistema deve ficar disponível 95% do tempo em horário estendido (8h às 20h). Deve ter um tempo de recuperação máximo de 1 hora para falhas críticas.
4. **RNF004 - Usabilidade**: A interface deve ser responsiva e intuitiva, facilitando o uso em diferentes dispositivos. A navegação principal deve ser acessível em até 3 toques.
5. **RNF005 - Compatibilidade**: O sistema deve ser compatível com dispositivos Android 10 ou superior. Suporte para diferentes tamanhos de tela.
6. **RNF006 - Acessibilidade**: Suporte a TalkBack, recursos de alto contraste e fontes redimensionáveis até 200% sem quebra de layout devem ser disponibilizados no sistema.
7. **RNF007 - Localização**: Suporte nativo a português (BR).
8. **RNF008 - Escalabilidade**: O sistema deve suportar até 5.000 usuários simultâneos, além de ser capaz de aumentar recursos em 50% durantes picos.


#### 3.3 Regras de Negócio
1. **RN001 - Limitação de Clubes**: Usuários “free” podem criar até 1 clube de leitura e podem participar de no máximo 2 clubes simultaneamente. Clubes “free” tem limite máximo de 10 membros
2. **RN002 - Controle de Acesso**: Apenas administradores podem definir livro do mês. Clubes privados exigem aprovação manual de novos membros.
3. **RN003 - Avaliações**: Usuários só podem avaliar livros após marcar como “lido”. Média de avaliações só visível para membros “premium”.
4. **RN004 - Encontros**: Cada clube deve ter pelo menos 1 encontro agendado por mês. Encontros devem ser defeinidos com no mínimo 7 dias de antecedência.
5. **RN005 - Amizades**: Solicitações não respondidas expiram após 30 dias. Um usuário pode realizar no máximo 20 solicitações de amizade por dia.
6. **RN006 - Conteúdo**: Resenhas/reviews devem conter entre 10 e 250 caracteres. Livros adultos somente visíveis para usuários com idade verificada, sendo maior ou igual a 18 anos.
7. **RN007 - Monetização**: Recursos premium exigem assinatura mensal ou anual.
8. **RN008 - Notificações**: Configurações de notificação devem ser personalizáveis.

---

### Modelos e Diagramas

#### 4.1 Casos de Uso

Cada caso de uso descreve o fluxo de ações, pré-condições e pós-condições para cada funcionalidade crítica do sistema.

**UC01 - Cadastrar Usuário**  
**Atores:** Usuário  
**Descrição:** Permite ao usuário visitante realizar o cadastro no sistema informando dados pessoais.  
**Pré-condições:** O usuário não deve estar cadastrado.  
**Pós-condições:** Um novo usuário é registrado na plataforma.  
**Fluxo Principal:**
1. O usuário acessa a tela de cadastro.  
2. Preenche nome, sobrenome, username, data de nascimento, email e senha.  
3. O sistema valida os dados.  
4. O sistema salva o usuário no banco de dados.  
5. O sistema confirma o cadastro.  

**UC02 - Autenticar Usuário**  
**Atores:** Usuário  
**Descrição:** Permite ao usuário acessar o sistema usando suas credenciais.  
**Pré-condições:** O usuário deve estar previamente cadastrado.  
**Pós-condições:** O usuário é autenticado e direcionado à tela principal.  
**Fluxo Principal:**
1. O usuário acessa a tela de login.  
2. Insere email e senha.  
3. O sistema valida as credenciais.  
4. O sistema concede acesso ao usuário.  

**UC03 - Editar Perfil**  
**Atores:** Usuário  
**Descrição:** Permite que o usuário altere seus dados pessoais.  
**Pré-condições:** O usuário deve estar autenticado.  
**Pós-condições:** Os dados do perfil são atualizados.  
**Fluxo Principal:**
1. O usuário acessa o perfil.  
2. Altera os dados desejados.  
3. O sistema valida e salva as alterações.  

**UC04 - Criar Clube**  
**Atores:** Usuário (Free ou Premium)  
**Descrição:** Permite criar um novo clube de leitura.  
**Pré-condições:** O usuário deve estar autenticado e respeitar o limite de criação.  
**Pós-condições:** Um novo clube é criado e vinculado ao usuário.  
**Fluxo Principal:**
1. O usuário acessa a tela de criação de clube.  
2. Preenche os dados do clube.  
3. Define se é público ou privado.  
4. O sistema salva e exibe o novo clube.  

**UC05 - Participar de Clube**  
**Atores:** Usuário  
**Descrição:** Permite que um usuário entre em clubes existentes.  
**Pré-condições:** O clube deve existir e estar dentro dos limites de membros.  
**Pós-condições:** O usuário é adicionado ao clube.  
**Fluxo Principal:**
1. O usuário acessa a tela de clubes.  
2. Seleciona um clube para participar.  
3. O sistema valida a entrada e adiciona o usuário ao clube.  

**UC06 - Pesquisar Clubes**  
**Atores:** Usuário  
**Descrição:** Permite ao usuário buscar clubes por nome.  
**Pré-condições:** O usuário deve estar autenticado.  
**Pós-condições:** O sistema retorna a lista de clubes correspondentes.  
**Fluxo Principal:**
1. O usuário digita o nome do clube.  
2. O sistema realiza a busca.  
3. Exibe os clubes encontrados.  

**UC07 - Definir Tipo de Clube**  
**Atores:**  Usuário (Administrador do Clube)  
**Descrição:** Permite escolher se o clube será público ou privado.  
**Pré-condições:** O clube ainda não foi criado.  
**Pós-condições:** O tipo do clube é definido.  
**Fluxo Principal:**
1. Durante a criação do clube, o usuário escolhe o tipo.  
2. O sistema salva a definição.  

**UC08 - Definir Livro do Mês**  
**Atores:** Usuário (Administrador do Clube)    
**Descrição:** Permite ao administrador definir o livro do mês.  
**Pré-condições:** O clube deve estar criado.  
**Pós-condições:** O livro do mês é definido e comunicado aos membros.  
**Fluxo Principal:**
1. O administrador acessa o painel do clube.  
2. Escolhe um livro.  
3. O sistema registra o livro do mês.  

**UC09 - Buscar Livro**  
**Atores:** Usuário  
**Descrição:** Permite buscar um livro por título.  
**Pré-condições:** Nenhuma.  
**Pós-condições:** Exibe resultados de livros compatíveis.  
**Fluxo Principal:**
1. O usuário digita o nome do livro.  
2. O sistema retorna os resultados.  

**UC10 - Definir Livro Seguinte**  
**Atores:** Usuário (Administrador do Clube)    
**Descrição:** Permite pré-definir o próximo livro do mês.  
**Pré-condições:** O clube deve ter pelo menos um livro atual.  
**Pós-condições:** O livro seguinte é salvo no planejamento.  
**Fluxo Principal:**
1. O administrador acessa a seção de planejamento.  
2. Seleciona o próximo livro.  
3. O sistema salva a escolha.  

**UC11 - Definir Data do Encontro**  
**Atores:** Usuário (Administrador do Clube)    
**Descrição:** Permite agendar uma data para encontro.  
**Pré-condições:** O clube deve estar ativo.  
**Pós-condições:** O encontro é agendado.  
**Fluxo Principal:**
1. O administrador escolhe a data.  
2. O sistema salva e notifica os membros.  

**UC12 - Definir Local do Encontro**  
**Atores:** Usuário (Administrador do Clube)    
**Descrição:** Permite definir o local do encontro.  
**Pré-condições:** Um encontro deve estar sendo planejado.  
**Pós-condições:** O local é registrado.  
**Fluxo Principal:**
1. O administrador insere o local.  
2. O sistema salva a informação.  

**UC13 - Avaliar Livro**  
**Atores:** Usuário  
**Descrição:** Permite dar nota ao livro lido (0 a 5).  
**Pré-condições:** O livro deve estar marcado como lido.  
**Pós-condições:** A avaliação é registrada.  
**Fluxo Principal:**
1. O usuário acessa o livro.  
2. Escolhe uma nota.  
3. O sistema salva a avaliação.  

**UC14 - Avaliar Dificuldade de Livro**  
**Atores:** Usuário  
**Descrição:** Permite avaliar a dificuldade da leitura (0 a 5).  
**Pré-condições:** O livro deve estar lido.  
**Pós-condições:** A avaliação de dificuldade é salva.  
**Fluxo Principal:**
1. O usuário seleciona o nível de dificuldade.  
2. O sistema armazena o dado.  

**UC15 - Escrever Avaliação**  
**Atores:** Usuário  
**Descrição:** Permite escrever uma resenha do livro.  
**Pré-condições:** O livro deve estar marcado como lido.  
**Pós-condições:** A resenha é salva e visível.  
**Fluxo Principal:**
1. O usuário escreve entre 10 e 250 caracteres.  
2. O sistema valida e publica.  

**UC16 - Aceitar Membro**  
**Atores:** Administrador do Clube  
**Descrição:** Aceita um novo membro em clubes privados.  
**Pré-condições:** O usuário deve ter solicitado ingresso.  
**Pós-condições:** O membro é adicionado ao clube.  
**Fluxo Principal:**
1. O administrador visualiza a solicitação.  
2. Aceita o usuário.  
3. O sistema adiciona o membro.  

**UC17 - Recusar Membro**  
**Atores:** Usuário (Administrador do Clube)   
**Descrição:** Recusa a entrada de um usuário.  
**Pré-condições:** O usuário deve ter solicitado ingresso.  
**Pós-condições:** O usuário não entra no clube.  
**Fluxo Principal:**
1. O administrador visualiza a solicitação.  
2. Recusa o ingresso.  
3. O sistema remove a solicitação.  

**UC18 - Adicionar Amigo**  
**Atores:** Usuário  
**Descrição:** Permite enviar solicitação de amizade.  
**Pré-condições:** O outro usuário deve existir.  
**Pós-condições:** A solicitação é enviada.  
**Fluxo Principal:**
1. O usuário encontra outro perfil.  
2. Clica em “Adicionar Amigo”.  
3. O sistema envia a solicitação.  

**UC19 - Remover Amigo**  
**Atores:** Usuário  
**Descrição:** Permite remover alguém da lista de amigos.  
**Pré-condições:** Os usuários devem já ser amigos.  
**Pós-condições:** O vínculo é desfeito.  
**Fluxo Principal:**
1. O usuário acessa a lista de amigos.  
2. Clica em “Remover”.  
3. O sistema remove o vínculo.  

**UC20 - Visualizar Notificações**  
**Atores:** Usuário  
**Descrição:** Permite ver notificações como convites, amizades e livros.  
**Pré-condições:** O usuário deve estar logado.  
**Pós-condições:** Notificações são marcadas como lidas.  
**Fluxo Principal:**
1. O usuário acessa o painel de notificações.  
2. Visualiza interações recentes.  
3. O sistema atualiza o status das notificações.  

#### Diagrama de Casos de Uso
![Diagrama de casos de uso do projeto](https://imgur.com/iyGCRuz.jpeg)


#### 4.2 Diagramas de Classe 
#### Backend do Projeto Booklub

![Diagrama de classes do backend do projeto](https://i.imgur.com/mPMsgcj.jpeg)

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


#### 4.3 Diagramas de Sequência 

---

### Rastreabilidade de Requisitos 

#### 5.1 Matriz de Rastreabilidade 
### ✅ Matriz de Rastreabilidade – Booklub

| Requisito | Caso de Uso                        | Componente/Classe(s)                                                   | Status    |
|-----------|------------------------------------|------------------------------------------------------------------------|-----------|
| RF001     | UC01 - Cadastrar Usuário           | AuthServiceImpl, UserServiceImpl, UserRepository, UserController       | Completo  |
| RF002     | UC02 - Autenticar Usuário          | AuthServiceImpl, KeycloakGateway, UserController                       | Completo  |
| RF003     | UC03 - Editar Perfil               | UserServiceImpl, UserRepository, UserController                        | Completo  |
| RF004     | UC04 - Criar Clube                 | ClubServiceImpl, ClubRepository, User, Club, UserController            | Completo  |
| RF005     | UC05 - Participar de Clube         | ClubMemberServiceImpl, ClubPendingEntry, ClubRepository                | Completo  |
| RF006     | UC06 - Pesquisar Clubes            | ClubServiceImpl, ClubRepository, UserController                        | Completo  |
| RF007     | UC07 - Definir Tipo de Clube       | ClubServiceImpl, Club, ClubRepository                                  | Completo  |
| RF008     | UC08 - Definir Livro do Mês        | ClubServiceImpl, ClubRepository, BookUserServiceImpl, BookUser         | Completo  |
| RF009     | UC09 - Buscar Livro                | GoogleBooksServiceImpl, GoogleBooksGateway, BookController             | Completo  |
| RF010     | UC10 - Definir Livro Seguinte      | BookUserServiceImpl, UserRepository, ClubRepository                    | Completo  |
| RF011     | UC11 - Definir Data do Encontro    | BookUserServiceImpl, BookUserRepository, ClubRepository                | Completo  |
| RF012     | UC12 - Definir Local do Encontro   | BookUserServiceImpl, BookUserRepository, ClubRepository                | Completo  |
| RF013     | UC13 - Avaliar Livro               | BookRatingsServiceImpl, BookRatingsRepository, BookRatings             | Completo  |
| RF014     | UC14 - Avaliar Dificuldade         | BookRatingsServiceImpl, BookRatingsRepository                          | Completo  |
| RF015     | UC15 - Escrever Avaliação          | BookRatingsServiceImpl, BookRatingsRepository                          | Completo  |
| RF016     | UC16 - Aceitar Membro              | ClubMemberServiceImpl, ClubPendingEntry, ClubRepository                | Completo  |
| RF017     | UC17 - Recusar Membro              | ClubMemberServiceImpl, ClubPendingEntry                                | Completo  |
| RF018     | UC18 - Adicionar Amigo             | UserController                                                         | Completo  |
| RF019     | UC19 - Remover Amigo               | UserController                                                         | Completo  |
| RF020     | UC20 - Visualizar Notificações     | UserController                                                         | Completo  |

---

### Conclusão 
Este documento serve como base para o desenvolvimento do sistema Booklub. Futuras revisões devem ser registradas no histórico de versões para manter o controle de mudanças e melhorias contínuas.

