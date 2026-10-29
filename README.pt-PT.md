# GamEducation

**Plataforma web e biblioteca de integração Android para aprendizagem através de jogos.**

[English](README.md) · [Visão geral](#visão-geral) · [Tecnologias](#tecnologias) · [O meu contributo](#o-meu-contributo)

![GamEducation — projeto final de Engenharia Informática no IPCB](assets/cover.svg)

| Contexto | Informação |
| --- | --- |
| Instituição | Instituto Politécnico de Castelo Branco, Portugal |
| Curso | Engenharia Informática |
| Período | 2023–2024 |
| Tipo de projeto | Projeto académico de final de curso |
| Equipa | Dois estudantes: João Dias e Luís Mateus |
| O meu papel | Codesenvolvimento da plataforma web, biblioteca Android e integração do jogo |
| Código | Privado; este repositório apresenta o projeto |

## Visão geral

O GamEducation liga conteúdos pedagógicos geridos por professores a jogos Android. A integração combina uma plataforma web em PHP/MySQL com a `GamEducationLibrary`, um módulo de biblioteca Android reutilizável incorporado nos jogos. O Snake demonstra a utilização dessa biblioteca.

Os professores podem organizar alunos e grupos, preparar perguntas e conteúdos e associar atividades a jogos através de códigos de acesso. Durante o jogo, a biblioteca apresenta as atividades educativas e devolve os resultados através de callbacks que o jogo pode utilizar.

## O que desenvolvemos

### Plataforma web

- Fluxos para professores, administradores e programadores de jogos.
- Gestão de alunos, grupos e categorias de conteúdos.
- Criação de conteúdos didáticos, perguntas e questionários.
- Perguntas de escolha múltipla, verdadeiro/falso, múltiplas respostas, correspondência, ordenação e preenchimento de espaços.
- Códigos de acesso para relacionar atividades e jogos.
- Registo de avaliações e comunicação de problemas nos jogos.

### Biblioteca de integração Android

- A `GamEducationLibrary` é compilada como módulo de biblioteca Android, em Kotlin e Java, e incluída como dependência no Snake.
- Trata da introdução e validação de códigos de acesso junto do backend PHP.
- Apresenta conteúdos e perguntas dentro do jogo através de WebView.
- Usa uma ponte JavaScript e callbacks para devolver os resultados das atividades ao jogo que a integra.
- Comunica com a plataforma web através de HTTP/JSON.

### Snake como exemplo de integração

- Jogo Android Snake com mecânicas de progressão e recompensas.
- Incorpora a biblioteca e solicita atividades educativas em determinados momentos do jogo.
- Utiliza os resultados das atividades para decidir como retomar o jogo ou atribuir recompensas.

## Arquitetura

![Arquitetura conceptual do GamEducation](assets/architecture.svg)

A interface web permite aos professores preparar atividades educativas. O backend PHP disponibiliza os fluxos de atividades e códigos de acesso e usa MySQL para guardar utilizadores, conteúdos, associações aos jogos e avaliações.

Dentro do Snake, a `GamEducationLibrary` gere a interação educativa: obtém a atividade junto do PHP, apresenta-a numa WebView e devolve o resultado ao jogo através de um callback. O jogo continua responsável pelas suas próprias mecânicas e decisões sobre recompensas.

O Snake abre diretamente e usa a biblioteca para introduzir códigos de acesso, apresentar atividades e receber os resultados por callbacks. Esta integração precisa do backend PHP/MySQL, mas não exige instalar uma aplicação GamEducation Android separada.

## Implementação Android anterior

O histórico do projeto conserva também uma aplicação Android independente em Kotlin/Jetpack Compose, correspondente a uma abordagem de integração anterior. A implementação posterior do Snake incorpora a biblioteca, trata as interações educativas dentro do jogo e não chama essa aplicação. Por isso, a aplicação fica como contexto da evolução do desenvolvimento, fora da arquitetura principal apresentada acima.

## Tecnologias

| Área | Tecnologias | Aplicação no projeto |
| --- | --- | --- |
| Backend | PHP | Fluxos da aplicação, acesso a conteúdos e submissão de avaliações |
| Base de dados | MySQL, SQL | Modelação relacional de conteúdos, utilizadores, grupos e avaliações |
| Interface web | HTML, CSS, JavaScript, Bootstrap | Páginas de gestão e interações educativas |
| Implementação Android anterior | Kotlin, Jetpack Compose | Ecrãs de uma aplicação independente conservada no histórico; não é necessária para a integração do Snake com a biblioteca |
| Integração Android | Kotlin, Java, WebView, ponte JavaScript | Módulo de biblioteca reutilizável, atividades educativas e callbacks para o jogo |
| Comunicação | HTTP, JSON, OkHttp, Gson | Troca de dados entre Android e PHP |
| Desenvolvimento | Git, GitHub, Gradle, Android Studio | Colaboração e ferramentas dos projetos Android |

## O meu contributo

Codesenvolvi o GamEducation com o meu colega de projeto, Luís Mateus. Trabalhámos em conjunto na plataforma PHP/MySQL, na biblioteca Android e na integração do Snake, bem como na implementação Android anterior.

O projeto deu-me experiência prática na implementação de funcionalidades web e Android, na modelação e utilização de dados relacionais e na comunicação entre componentes por HTTP/JSON. As decisões de desenho e implementação foram tomadas em colaboração.

## Experiência de engenharia

- Integração de componentes web e Android com interfaces e ambientes de execução diferentes.
- Modelação das relações entre conteúdos, perguntas, alunos e atividades de jogo.
- Implementação de vários formatos de pergunta e dos fluxos de resposta correspondentes.
- Desenvolvimento de uma camada Android reutilizável e de um jogo como exemplo de integração.
- Coordenação de trabalho partilhado numa equipa académica de duas pessoas.

## Resultado

A implementação académica baseada na biblioteca reúne uma plataforma pedagógica web, uma biblioteca Android reutilizável e o Snake como exemplo de integração. Permitiu aplicar conhecimentos de backend, bases de dados relacionais, interfaces web, Android, módulos de biblioteca e integração de jogos.

## Autoria e disponibilidade

Desenvolvido em conjunto por [João Dias](https://github.com/JoaoDias28) e [Luís Mateus](https://github.com/luismateus10), no curso de Engenharia Informática do Instituto Politécnico de Castelo Branco.

O código original mantém-se privado. Esta apresentação contém apenas uma descrição e diagramas explicativos, sem código da aplicação, exportações da base de dados ou registos de utilizadores. Posso explicar a arquitetura, as decisões técnicas e o trabalho realizado em colaboração numa entrevista.
