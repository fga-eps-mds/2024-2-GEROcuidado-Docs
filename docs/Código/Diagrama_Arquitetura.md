# Documento de Arquitetura

## 1. Introdução

Esse documento tem a finalidade de explicar sobre as decisões arquiteturais do projeto, nesse documento o foco será entender mais sobre como funcionará o sistema como um todo, ou seja, como é feita a interação do usuário com o produto, quais são os microsserviços e de que forma eles foram definidos, entre outras possíveis dúvidas que possam surgir. Esse documento foi desenvolvido com base no documento de arquitetura do projeto GeroCuidado no semestre 2024.1.

## 2. Escopo

O GEROcuidado é um aplicativo projetado para auxiliar seus usuários, que incluem cuidadores formais e informais, idosos autônomos e familiares, na organização e acompanhamento da saúde dos idosos, seja como parte de suas responsabilidades de cuidador ou de sua própria família, como um pai ou uma mãe. No caso dos idosos autônomos, esse acompanhamento é realizado de si mesmo.

O MVP acordado com os proprietários do aplicativo (Enactus), foi que neste semestre 2024.2, o GEROcuidado será uma evolução do aplicativo entregue no semestre anterior, junto com a possibilidade de utilizar o aplicativo de forma offline sem a funcionalidade do fórum. As funcionalidades novas acordadas para serem desenvolvidas foram:

*	Recuperação de senha
*	Criar um novo evento na agenda do idoso.
*	Atualizar as informações do perfil do cuidador
*	Denunciar um comentário ofensivo
*	Gerar relatório das métricas de saúde
*	Exportar as métricas de saúde em PDF
*	Adicionar comentário em posts do fórum

## 3. Arquitetura

A arquitetura abaixo ilustra a forma como irá funcionar todas as partes, sendo elas o Frontend, onde ocorre o input através da interface de usuário, após esse input, caso o aplicativo esteja conectado à internet é encaminhado para o microsserviço especificado, sendo eles o Microsserviço Usuário atrelado as funcionalidades de CRUD quanto aos usuários e perfis de usuário, Microsserviço Fórum associado a parte do fórum, publicações, like e comentário e finalmente o  Microsserviço Saúde, responsável pelas informações de saúde do idoso, como pressão, oxigenação do sangue, entre outros. Além disso temos os bancos de cada microsserviços, responsável por armazenar todas essas informações. Abaixo a arquitetura ilustrando todos esses pedaços:

![Arquitetura](../assets/Arquitetura.png)

### Frontend

O front-end do GEROcuidado é uma aplicação nativa android, que poderá ser baixada e instalada diretamente nos smartphones dos usuários. A aplicação é construída de tal forma que poderá ser usada com e sem conexão com a internet. Os serviços descritos abaixo servem como uma nuvem de dados para o que o usuário já consegue realizar no aplicativo.

O front-end é desenvolvido em [React Native](https://reactnative.dev/) utilizando Javascript como linguagem principal. O banco de dados utilizado é o [WatermelonDB](https://watermelondb.dev/docs), que utiliza como recurso o próprio SQLite disponibilizado no Android.

### Microsserviço Usuário

O microsserviço de Usuário no aplicativo GEROcuidado desempenha um papel essencial na autenticação e gestão de usuários, abrangendo cuidadores formais, idosos autônomos e familiares. Este microsserviço oferece funcionalidades fundamentais relacionadas ao registro e gerenciamento de contas de usuário, permitindo que os usuários acessem as diversas funcionalidades do sistema. Suas principais funcionalidades incluem:

1. **CRUD de Usuário (Create, Read, Update, Delete):** Os cuidadores formais, idosos autônomos e familiares têm a capacidade de se registrar na plataforma, fornecendo informações pessoais, como nome, endereço de e-mail, senha segura e outros detalhes relevantes. Esse processo de registro é fundamental para criar uma conta no aplicativo, permitindo o acesso às funcionalidades e recursos disponíveis.

Além disso, o microsserviço de Usuário também se concentra em questões de segurança, implementando políticas de senhas robustas e fornecendo uma funcionalidade de recuperação de senha para garantir a proteção dos dados dos usuários. Isso ajuda a garantir que apenas usuários autorizados tenham acesso ao sistema e que suas informações estejam protegidas.

Em resumo, o microsserviço de Usuário é a pedra angular da autenticação e do gerenciamento de contas de usuário no aplicativo GEROcuidado, permitindo que cuidadores, idosos autônomos e familiares acessem e utilizem as funcionalidades do sistema de forma segura e eficiente.

### Microsserviço Fórum

O microsserviço de Fórum no aplicativo GEROcuidado desempenha um papel crucial na interação e comunicação entre os usuários, que incluem cuidadores formais, cuidadores informais, idosos autônomos e familiares. Este microsserviço é projetado para fornecer funcionalidades relacionadas ao compartilhamento de informações, discussões e interações no fórum do aplicativo. Suas principais funcionalidades incluem:

1. **CRUD de Publicação no Fórum:** Os usuários, que podem ser cuidadores formais, cuidadores informais, idosos autônomos ou familiares, têm a capacidade de criar, ler, atualizar e excluir (CRUD) publicações no fórum. Isso permite que os usuários compartilhem informações, façam perguntas, forneçam dicas ou discutam tópicos relacionados ao cuidado de idosos.

2. **Moderação de Publicações:** O microsserviço de Fórum também inclui funcionalidades de moderação. Os moderadores, designados para garantir a qualidade e o respeito no fórum, têm a capacidade de revisar e moderar as publicações. Isso inclui a capacidade de aprovar, editar ou excluir publicações para evitar informações imprecisas ou conteúdo inadequado.

3. **Interação com Publicações:** Além das funcionalidades CRUD, os usuários têm a capacidade de interagir com as publicações no fórum. Eles podem "curtir" publicações (likes) e deixar comentários para criar discussões e promover a interação entre os membros da comunidade.

Através do microsserviço de Fórum, o aplicativo GEROcuidado promove uma comunidade de usuários onde cuidadores formais, cuidadores informais, idosos autônomos e familiares podem trocar informações, apoio e experiências, promovendo um ambiente de aprendizado e colaboração. O foco na moderação garante que o fórum permaneça informativo e respeitoso.

### Microsserviço Saúde

O microsserviço de Saúde no aplicativo GEROcuidado desempenha um papel fundamental na gestão e acompanhamento da saúde dos idosos, cuidadores formais, cuidadores informais e familiares. Este microsserviço é projetado para fornecer funcionalidades relacionadas ao registro, acompanhamento e gerenciamento de informações de saúde, bem como rotinas de cuidados. Suas principais funcionalidades incluem:

1. **CRUD de Informações de Saúde do Idoso:** Os cuidadores formais, cuidadores informais, idosos autônomos e familiares têm a capacidade de registrar, atualizar, visualizar e apagar informações de saúde, como métricas vitais (por exemplo, frequência cardíaca, oxigenação do sangue) e outras informações relevantes para o acompanhamento da saúde. Isso permite que os usuários acompanhem de perto a saúde dos idosos sob seus cuidados ou suas próprias métricas de saúde.

2. **CRUD de Rotina:** Os cuidadores, tanto formais quanto informais, podem cadastrar, visualizar, editar e remover informações sobre a rotina dos idosos que cuidam. Isso inclui informações sobre medicamentos, atividades físicas e alimentação, permitindo o controle dos horários e o cumprimento das necessidades específicas de cada idoso. Além disso, os idosos independentes também têm a opção de gerenciar sua própria rotina, registrando informações sobre medicamentos, atividades físicas e alimentação para serem lembrados dos horários.

3. **Criação de Notificações:** Os usuários podem receber notificações do aplicativo para lembrá-los de realizar atividades cadastradas, como tomar medicamentos, realizar exercícios ou seguir uma dieta específica. Isso ajuda a garantir que as tarefas de cuidado sejam cumpridas de forma consistente.

4. **Adição de Agenda/Calendário:** Os cuidadores podem agendar tarefas em um calendário para receber notificações sobre atividades importantes. Isso cria um calendário que permite o agendamento de tarefas e eventos relacionados ao cuidado dos idosos, garantindo que o cuidador seja lembrado das atividades no momento certo.

5. **CRUD de Idosos:** Os cuidadores formais, cuidadores informais e familiares podem gerenciar o cadastro de idosos no sistema, incluindo informações detalhadas sobre os idosos, como nome, idade, condições de saúde e preferências. Isso facilita o acompanhamento individualizado de cada idoso e o acesso rápido às informações de saúde e rotina específicas de cada um.

O microsserviço de Saúde é essencial para o acompanhamento eficaz da saúde dos idosos e a gestão de rotinas de cuidado, garantindo que as métricas de saúde sejam registradas e monitoradas, as rotinas sejam cumpridas e as notificações sejam usadas para manter todos os envolvidos informados sobre as atividades necessárias para a saúde e o bem-estar dos idosos.

## 4. Versionamento do Documento

| Data | Versão | Descrição | Autor |
| :-----: | :-------------: | :---------------: | :-: |
| 09/02/2025 | 1.0 | Versão inicial do Documento | [Artur Vinícius Dias Nunes](https://github.com/ArturVinicius) |