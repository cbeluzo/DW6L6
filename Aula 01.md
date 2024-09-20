<a name="topo"></a>
# **Aula 1: Desenvolvimento de Sistemas Web - Introdução**

*Este material foi gerado com AI-Gen. A estrutura e conteúdo foi concebida e revisada pelo autor.*

<center> <img src="img/1.webp" alt="Imagem 1" width="600"/> </center>

**SUMÁRIO**

[1. Contextualização](#1)   
[2. Preparação de Ambiente e Ferramentas de Desenvolvimento](#2)   
[3. Criação do Primeiro Projeto Web Simples](#3)   
[4.  Atividade Prática 1: Criando meu primeiro Projeto Web](#4)   
[5. Atividade Prática 2: Criando uma Página de Índice e Tratamento de Erros 404*](#5)   
[6.  Atividade Prática 3: Criando um Menu de Navegação para Páginas Estáticas](#6)   

---
<a name="1"></a>
## **1. Contextualização**

### **1.1 Objetivos da Aula**
Nesta aula, você aprenderá sobre a importância do desenvolvimento de sistemas web no cenário atual e os objetivos principais do curso. Além disso, serão introduzidos conceitos fundamentais que você aplicará durante o curso, como **MVC (Model-View-Controller)**, **DTO (Data Transfer Object)**, **Hibernate**, **APIs RESTful** e **microserviços**.

1. **Importância do Desenvolvimento Web no Cenário Atual**
>O desenvolvimento web é essencial em uma era onde grande parte das interações ocorre online. Aplicações web são usadas em diversos setores para oferecer serviços e produtos de forma eficiente e acessível. Saber desenvolver sistemas web robustos e escaláveis, capazes de lidar com grandes volumes de usuários e dados, é uma competência indispensável para qualquer profissional de TI.

2. **Objetivos do Curso**
>    - **Criar e gerenciar APIs RESTful**: Você aprenderá a desenvolver APIs RESTful para conectar o frontend ao backend, seguindo as melhores práticas de arquitetura de software.
>
>    - **Implementar o padrão DTO (Data Transfer Object)**: O uso de DTOs permite que você transfira dados de forma eficiente e segura entre diferentes camadas de uma aplicação, separando a lógica de negócio da apresentação dos dados.
>
>   - **Utilizar Hibernate para o gerenciamento de dados**: Com o Hibernate, você poderá trabalhar com o mapeamento objeto-relacional (ORM), que facilita a interação com bancos de dados relacionais sem precisar escrever consultas SQL complexas.
>
>   - **Aplicar o padrão MVC**: Este padrão de arquitetura permitirá que você organize suas aplicações de forma modular, separando a lógica de apresentação, controle e manipulação dos dados.
>
>   - **Desenvolver microserviços**: O curso também abordará como dividir uma aplicação em pequenos serviços independentes (microserviços), promovendo escalabilidade e manutenção simplificada.

3. **Relevância das Habilidades para Profissionais de TI**
>   O mercado exige cada vez mais desenvolvedores que saibam lidar com APIs, bancos de dados e arquitetura de microserviços. Esses conhecimentos são fundamentais para a criação de sistemas modernos, flexíveis e escaláveis. Ao final deste curso, você terá habilidades em:
>
>   - **Desenvolvimento backend com Java**: Criar sistemas robustos, focados em escalabilidade e segurança.
>
>   - **APIs RESTful**: Conectar o frontend e backend de forma eficiente e seguindo padrões da web.
>
>   - **DTO e Hibernate**: Gerenciar dados de forma eficiente, minimizando o uso de recursos e evitando erros de manipulação de dados.
>
>   - **Microserviços**: Arquitetar sistemas distribuídos, que podem crescer de forma modular e autônoma.

### **1.2. Atividade Prática**
- **Discussão em Grupos**
>  Discutam em pequenos grupos como diferentes setores (como saúde, finanças, e-commerce) utilizam sistemas web e como esses sistemas podem se beneficiar do uso de APIs RESTful, DTOs e microserviços. Cada grupo deve apresentar um exemplo prático de como essas tecnologias são aplicadas para resolver problemas reais.

---

### **1.3. Tópicos a serem abordados no curso**

1. **Padrão MVC (Model-View-Controller)**
>   O MVC é um padrão de design que separa a aplicação em três camadas principais:
>
>   - **Model (Modelo)**: Responsável pela manipulação de dados e lógica de negócios.
>
>   - **View (Visão)**: Cuida da interface com o usuário e apresentação de dados.
>
>   - **Controller (Controle)**: Gerencia a comunicação entre o Model e a View, processando as requisições dos usuários e atualizando a interface.

2. **DTO (Data Transfer Object)**
>   O DTO é um objeto simples que transporta dados entre diferentes camadas da aplicação. Ao usar DTOs, você consegue separar os dados que serão expostos ao frontend da lógica de negócio do backend, o que melhora a segurança e facilita a manutenção do código.

3. **Hibernate e Mapeamento Objeto-Relacional (ORM)**
>   O Hibernate é um framework de ORM que facilita a interação com bancos de dados, permitindo que você use objetos Java para representar e manipular dados, em vez de escrever queries SQL diretamente. Isso torna o código mais limpo, reutilizável e fácil de manter.

4. **APIs RESTful**
>   As APIs RESTful permitem que diferentes sistemas se comuniquem pela web de maneira padronizada. No curso, você aprenderá a criar APIs seguindo os princípios REST (Representational State Transfer), que promovem a separação entre cliente e servidor, tornando as aplicações mais flexíveis e escaláveis.

5. **Microserviços**
>   A arquitetura de microserviços divide a aplicação em pequenos serviços independentes, cada um com sua própria responsabilidade. Isso facilita a escalabilidade, pois cada serviço pode ser desenvolvido, implantado e mantido de forma autônoma, sem impactar o restante da aplicação.

---

### **1.4 Perguntas de Reflexão**

> 1. **Qual é a importância do desenvolvimento web no cenário atual?**
> 
> 2. **Quais são os principais objetivos deste curso?**
> 
> 3. **Como as tecnologias como DTO, Hibernate e microserviços podem beneficiar o desenvolvimento de sistemas web?**

---

> 1. **Qual é a importância do desenvolvimento web no cenário atual?**
>   - **Resposta esperada:** O desenvolvimento web é fundamental para a criação de sistemas que suportam a interação entre usuários e serviços de forma eficiente e acessível, sendo uma base para a maioria das aplicações modernas.
>
>2. **Quais são os principais objetivos deste curso?**
>   - **Resposta esperada:** Capacitar os alunos a desenvolverem sistemas web backend eficientes e escaláveis, utilizando Java, Apache Tomcat, Hibernate, DTO, RESTful e microserviços.
>
>3. **Como as tecnologias como DTO, Hibernate e microserviços podem beneficiar o desenvolvimento de sistemas web?**
>   - **Resposta esperada:** O uso de DTOs facilita o transporte seguro de dados, o Hibernate simplifica a interação com bancos de dados, e os microserviços permitem uma arquitetura mais flexível e escalável.

<center>

[Início](#topo)

</center>

---
<a name="2"></a>
## **2. Ferramentas de Desenvolvimento**

### **2.1 Instalação do JDK (Java Development Kit)**

Para começar a programar em Java, é essencial instalar o **JDK (Java Development Kit)**, que é o conjunto de ferramentas fundamentais para desenvolver e executar aplicações Java. O JDK inclui:

>1. **Compilador (javac)**: Transforma o código-fonte Java em bytecode, que pode ser executado pela Java Virtual Machine (JVM).
>
>2. **Java Runtime Environment (JRE)**: Um ambiente de execução que contém a JVM e as bibliotecas necessárias para rodar aplicações Java.
>
>3. **Ferramentas de Desenvolvimento**: Inclui depuradores, analisadores de performance e outras ferramentas que ajudam no processo de desenvolvimento.

O JDK é indispensável para qualquer desenvolvedor que deseje trabalhar com Java, pois oferece tudo o que é necessário para escrever, compilar e executar programas Java.

#### 2.1.1 **Tecnologias Similares/Alternativas para Desenvolvimento Web**

Embora o **JDK** seja fundamental para o desenvolvimento em Java, existem várias tecnologias alternativas que podem ser usadas no desenvolvimento de aplicações web, cada uma com suas particularidades. Abaixo estão algumas delas:

1. **Node.js**
>   - **Linguagem**: JavaScript (ou TypeScript)
>
>   - **Ambiente**: Node.js é uma plataforma de execução baseada em JavaScript que utiliza o motor V8 do Google Chrome. Ele permite que desenvolvedores usem JavaScript para programação tanto no backend quanto no frontend.
>
>   - **Vantagem**: Alta escalabilidade, boa performance em aplicações de I/O intensivo, e uma grande comunidade de desenvolvedores. Também permite o uso de uma única linguagem (JavaScript) em toda a stack.

2. **Python com Django ou Flask**
>   - **Linguagem**: Python
>
>   - **Frameworks**: Django (completo) e Flask (minimalista) são os dois principais frameworks web em Python.
>
>   - **Vantagem**: Python é uma linguagem altamente legível e fácil de aprender, com uma ampla gama de bibliotecas para desenvolvimento rápido de aplicações. Django oferece uma solução completa para desenvolvimento web, enquanto Flask permite maior flexibilidade e controle.

3. **Ruby com Ruby on Rails**
>   - **Linguagem**: Ruby
>
>   - **Framework**: Ruby on Rails (ou Rails)
>
>   - **Vantagem**: Rails é conhecido por permitir o desenvolvimento rápido de aplicações devido à sua ênfase na simplicidade e na convenção em vez de configuração. É muito utilizado em startups e projetos que precisam de rápida implementação.

4. **PHP com Laravel**
>   - **Linguagem**: PHP
>
>   - **Framework**: Laravel
>
>   - **Vantagem**: PHP é amplamente utilizado para desenvolvimento web e é conhecido por sua simplicidade e facilidade de hospedagem. O Laravel adiciona uma camada de modernidade ao PHP, com recursos como roteamento, sessões e integração com bancos de dados facilitada.

5. **ASP.NET Core**
>   - **Linguagem**: C#
>
>   - **Framework**: ASP.NET Core, desenvolvido pela Microsoft.
>
>   - **Vantagem**: O ASP.NET Core oferece excelente integração com o ecossistema da Microsoft e é utilizado para criar aplicações web robustas e escaláveis. Ele oferece alta performance e suporte para o desenvolvimento de APIs e aplicações MVC.

6. **Go (Golang)**
>   - **Linguagem**: Go (ou Golang)
>
>   - **Ambiente**: Go é uma linguagem desenvolvida pelo Google, ideal para desenvolvimento de sistemas e aplicações web altamente concorrentes e escaláveis.
>
>   - **Vantagem**: Go oferece performance similar a linguagens compiladas, como C ou C++, e é muito usada em sistemas distribuídos e de alta performance.

7. **Java com Spring Framework**
>   - **Linguagem**: Java
>
>   - **Framework**: Spring Framework é um dos frameworks mais populares no desenvolvimento de aplicações web corporativas em Java.
>
>   - **Vantagem**: O Spring Framework fornece um ecossistema robusto para o desenvolvimento de aplicações web escaláveis e seguras, com suporte para injeção de dependências, transações, APIs RESTful e integração com bancos de dados.

Essas alternativas permitem flexibilidade na escolha de uma tecnologia adequada dependendo do contexto do projeto, a equipe de desenvolvimento e os requisitos de desempenho e escalabilidade. Cada tecnologia tem sua própria comunidade, ferramentas, e suporte, permitindo que o desenvolvedor escolha o melhor caminho para seu ambiente de trabalho.

#### 2.1.2 **Passo a Passo da Instalação do JDK**

#### **Windows**
1. Acesse o site oficial da Oracle ([https://www.oracle.com/java/technologies/javase-jdk11-downloads.html](https://www.oracle.com/java/technologies/javase-jdk11-downloads.html)) e faça o download da versão mais recente do JDK compatível com seu sistema operacional.
2. Execute o instalador e siga as instruções na tela.
3. Após a instalação, configure a variável de ambiente `JAVA_HOME`:
   - Clique com o botão direito em "Este Computador" e selecione "Propriedades".
   - Vá em "Configurações Avançadas do Sistema" e clique em "Variáveis de Ambiente".
   - Na seção de "Variáveis do Sistema", clique em "Novo" e adicione `JAVA_HOME` como o nome da variável, com o caminho do diretório onde o JDK foi instalado como valor.
   - Adicione o caminho `JAVA_HOME\bin` à variável `PATH`.
4. Verifique a instalação no **Prompt de Comando** com o comando:
   ```bash
   java -version
   ```

#### **macOS**
1. Acesse o mesmo link da Oracle e faça o download da versão do JDK compatível com macOS.
2. Execute o pacote `.dmg` baixado e siga as instruções para instalação.
3. Abra o Terminal e configure a variável de ambiente `JAVA_HOME` no arquivo `.bash_profile` ou `.zshrc`:
   ```bash
   export JAVA_HOME=$(/usr/libexec/java_home)
   ```
4. Verifique a instalação no **Terminal** com o comando:
   ```bash
   java -version
   ```

#### **Linux (Ubuntu)**
1. No terminal, adicione o repositório oficial e instale o JDK:
   ```bash
   sudo apt update
   sudo apt install openjdk-11-jdk
   ```
2. Verifique a instalação com o comando:
   ```bash
   java -version
   ```

#### **Perguntas para revisão**
1. **Por que é necessário instalar o JDK para o desenvolvimento Java?**
   - O JDK é necessário porque contém as ferramentas e bibliotecas essenciais para o desenvolvimento e execução de aplicativos Java, incluindo o compilador e utilitários de gerenciamento de pacotes.

2. **Quais são os passos para instalar o JDK no Windows?**
   - Fazer o download do JDK no site oficial da Oracle, executar o instalador, configurar a variável de ambiente `JAVA_HOME` e verificar a instalação com o comando `java -version`.

3. **Como garantir que a instalação do JDK foi bem-sucedida?**
   - A instalação bem-sucedida pode ser verificada ao rodar o comando `java -version` no terminal ou prompt de comando. Isso exibirá a versão do Java instalada.

---

### **2.2 Configuração da IDE (Eclipse)**

A escolha da **IDE (Integrated Development Environment)** é um passo essencial para o desenvolvimento web. O **Eclipse** será a ferramenta utilizada neste curso, pois oferece uma integração completa com Java e várias tecnologias que utilizaremos, como Hibernate, Spring, e RESTful APIs.

#### **Por que usar o Eclipse?**
- **Ampla compatibilidade** com frameworks Java como Spring e Hibernate.
- **Refatoração eficiente** e suporte a diversas linguagens de programação.
- **Integração nativa com ferramentas de build**, como Maven e Gradle, facilitando a configuração e manutenção de projetos complexos.
- **Suporte a plugins** para funcionalidades adicionais, como desenvolvimento web e integração com servidores.

#### **Passo a Passo da Instalação do Eclipse:**

#### **Windows / macOS / Linux**
1. Acesse o site oficial do Eclipse ([https://www.eclipse.org/downloads/](https://www.eclipse.org/downloads/)) e faça o download do **Eclipse IDE for Enterprise Java and Web Developers**.
2. Execute o instalador e siga as instruções para concluir a instalação.
3. Durante a instalação, certifique-se de que o JDK está corretamente configurado em seu sistema, pois o Eclipse utilizará esse ambiente.
4. Após a instalação, abra o Eclipse e crie um novo projeto Java:
   - Selecione **File > New > Dynamic Web Project**.
   - Configure o nome do projeto e o JDK que será utilizado.
   - Escolha **Apache Tomcat** como o servidor de destino, caso o Tomcat já esteja instalado.
5. Verifique se a IDE está configurada corretamente criando uma classe Java simples e executando o código.

#### **Plugins importantes para instalação:**
- **Lombok Plugin**: Facilita a criação de classes Java, reduzindo a necessidade de código repetitivo, como getters e setters.
- **Spring Tools**: Suporta o desenvolvimento com o framework Spring, fornecendo autocompletar e sugestões para anotações Spring.
- **Docker Tooling**: Adiciona suporte para desenvolvimento e execução de containers Docker diretamente no Eclipse.

#### **Configurando o Servidor Tomcat no Eclipse**
1. No menu principal do Eclipse, vá até **Window > Preferences > Server > Runtime Environments**.
2. Clique em **Add** e selecione **Apache Tomcat** na lista.
3. Navegue até o local onde o Tomcat está instalado no seu sistema e adicione-o como um servidor.
4. Após configurado, adicione o Tomcat como servidor no seu projeto:
   - Clique com o botão direito no nome do projeto > **Run As > Run on Server**.
   - Selecione o **Tomcat** e configure-o para rodar o projeto.

#### **Perguntas:**
1. **Por que escolher o Eclipse como IDE para desenvolvimento web com Java?**
   - O Eclipse oferece suporte abrangente a frameworks como Spring e Hibernate, além de recursos de refatoração e depuração eficientes, tornando o desenvolvimento de aplicações web mais produtivo.

2. **Quais são os passos para instalar e configurar o Eclipse?**
   - O processo inclui o download da IDE no site oficial do Eclipse, instalação do JDK e configuração do Apache Tomcat como servidor para executar e testar os projetos.

3. **Quais são as funcionalidades destacadas do Eclipse que beneficiam desenvolvedores web?**
   - Funcionalidades como autocompletar de código, integração com frameworks Java, suporte a Docker e integração com servidores como Apache Tomcat, são essenciais para um desenvolvimento web eficiente.

---
<a name="3"></a>
## **3. Configuração de Estrutura de Projeto Web**

Agora que o ambiente de desenvolvimento está configurado, vamos criar um projeto web básico e entender a importância da organização do código e dos componentes principais. Este será o primeiro passo prático no desenvolvimento de um sistema web, permitindo que você aplique os conceitos e ferramentas aprendidos até aqui.

### **3.1 Estrutura de Projeto Web em Java**

Uma estrutura de projeto bem organizada é essencial para o desenvolvimento de aplicações robustas e de fácil manutenção. Em Java, projetos web geralmente seguem uma estrutura de diretórios específica para separar o código, os recursos web e as bibliotecas.

#### **Passo a Passo para Criar um Projeto Web Básico:**

1. **Criando um novo projeto no Eclipse**
   - Abra o Eclipse e selecione **File > New > Dynamic Web Project**.
   - Configure o nome do projeto (ex: `ProjetoWebSimples`) e selecione a versão do **JDK** que você instalou anteriormente.
   - Escolha o **Apache Tomcat** como servidor de aplicação. Se ele ainda não estiver configurado, você pode adicionar o Tomcat durante a criação do projeto.
   - Defina o diretório onde o projeto será salvo e clique em **Finish** para criar o projeto.

2. **Estrutura básica de um projeto web em Java**
   Após a criação do projeto, o Eclipse irá gerar uma estrutura de diretórios padrão, que deve incluir:

   - **src/**: Diretório que contém o código-fonte Java.
   - **WebContent/** ou **webapp/**: Diretório com arquivos relacionados ao frontend, como HTML, CSS, JavaScript, e arquivos de configuração como `web.xml`.
   - **lib/**: Diretório onde são armazenadas as bibliotecas e dependências externas do projeto.
   - **META-INF/**: Contém arquivos de configuração do aplicativo, como `MANIFEST.MF`.
   - **WEB-INF/**: Diretório que contém os arquivos de configuração do servidor e as classes Java compiladas.

3. **Explicação da função de cada componente**
   - **src/**: Aqui você criará as classes Java que contêm a lógica da sua aplicação.
   - **WebContent/** ou **webapp/**: Este diretório armazena o conteúdo acessível ao usuário, como páginas HTML, arquivos JavaScript, imagens e outros recursos estáticos.
   - **WEB-INF/**: Este diretório armazena arquivos que não devem ser acessados diretamente pelos usuários, como o arquivo `web.xml`, que define configurações do servidor e o mapeamento das URLs para os servlets.

4. **Primeiro Servlet e Configuração no `web.xml`**
   - No diretório **src**, crie um pacote chamado `com.exemplo.web`.
   - Crie uma nova classe Java chamada `HelloServlet` no pacote `com.exemplo.web`:
   ```java
   package com.exemplo.web;

   import javax.servlet.ServletException;
   import javax.servlet.http.HttpServlet;
   import javax.servlet.http.HttpServletRequest;
   import javax.servlet.http.HttpServletResponse;
   import java.io.IOException;
   import java.io.PrintWriter;

   public class HelloServlet extends HttpServlet {
       protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
           response.setContentType("text/html");
           PrintWriter out = response.getWriter();
           out.println("<h1>Hello, World!</h1>");
       }
   }
   ```
   - No arquivo `web.xml`, dentro de **WEB-INF**, adicione o mapeamento para o servlet:
   ```xml
   <web-app>
       <servlet>
           <servlet-name>HelloServlet</servlet-name>
           <servlet-class>com.exemplo.web.HelloServlet</servlet-class>
       </servlet>
       <servlet-mapping>
           <servlet-name>HelloServlet</servlet-name>
           <url-pattern>/hello</url-pattern>
       </servlet-mapping>
   </web-app>
   ```
   - Este mapeamento permite que, ao acessar o endereço `/hello`, o Tomcat execute o `HelloServlet`.

#### **Perguntas:**
1. **Qual é a importância da estrutura inicial do projeto web?**
   - A estrutura inicial organiza os arquivos do projeto de forma que eles possam ser facilmente mantidos e escalados. Isso facilita a colaboração entre desenvolvedores e a compreensão do fluxo da aplicação.

2. **O que compõe a estrutura básica de um projeto web em Java?**
   - A estrutura básica inclui diretórios como `src` (para o código-fonte), `WebContent` ou `webapp` (para os recursos web) e `WEB-INF` (para arquivos de configuração do servidor).

3. **Por que é importante iniciar com um projeto simples?**
   - Projetos simples ajudam a entender os conceitos fundamentais antes de mergulhar em projetos mais complexos. Eles fornecem uma base sólida para lidar com estruturas e funcionalidades mais avançadas no futuro.

---

### **3.2 Configuração e Execução do Servidor de Aplicação Local (Apache Tomcat)**

Agora que temos a estrutura do projeto, vamos configurar o servidor de aplicação **Apache Tomcat** para que possamos rodar e testar nossa aplicação localmente.

#### **Passo a Passo para Configurar e Executar o Tomcat:**

1. **Configuração do Tomcat no Eclipse**
   - No Eclipse, vá para **Window > Preferences > Server > Runtime Environments**.
   - Clique em **Add** e selecione **Apache Tomcat** na lista.
   - Navegue até o local onde o Apache Tomcat está instalado e adicione-o como servidor.
   - Agora, vá até o painel **Servers** e adicione o **Tomcat** à sua configuração de projeto clicando com o botão direito e selecionando **Add and Remove** para adicionar o projeto ao servidor.

2. **Executando o servidor local**
   - Com o Tomcat configurado, clique com o botão direito no projeto e selecione **Run As > Run on Server**.
   - O Eclipse abrirá um console onde você verá as mensagens de log do servidor. Se tudo estiver configurado corretamente, você verá a mensagem indicando que o servidor foi iniciado com sucesso.
   - Abra um navegador e acesse `http://localhost:8080/hello` para verificar o funcionamento do servlet que criamos.

3. **Verificação do funcionamento do servidor**
   - Acesse a página inicial do Tomcat ou verifique os logs no console do Eclipse para confirmar que o servidor está funcionando corretamente.

#### **Perguntas:**
1. **Por que é necessário um servidor de aplicação local para o desenvolvimento web?**
   - O servidor local permite testar e depurar a aplicação antes de ela ser implantada em um ambiente de produção, proporcionando um ambiente controlado para desenvolvimento.

2. **Quais são os passos para configurar o Apache Tomcat como servidor local?**
   - Instalar o Tomcat, configurá-lo no Eclipse e adicionar o projeto para ser executado no servidor.

3. **Como verificar se o servidor local está funcionando corretamente?**
   - A verificação pode ser feita acessando o navegador em `http://localhost:8080/` ou verificando os logs do servidor no console do Eclipse.

---

### **3.2 Configuração e Execução do Servidor de Aplicação Local (Apache Tomcat)**

Agora que temos a estrutura do projeto, vamos configurar o servidor de aplicação **Apache Tomcat** para rodar e testar nossa aplicação localmente.

#### **Passo a Passo para Configurar e Executar o Tomcat:**

1. **Configuração do Tomcat no Eclipse**
   - No **Eclipse**, acesse **Window > Preferences > Server > Runtime Environments**.
   - Clique em **Add** e selecione **Apache Tomcat** na lista.
   - Escolha a versão do **Tomcat** e configure o caminho para o diretório onde o Apache Tomcat foi instalado no seu sistema.
   - Após configurar o Tomcat, vá para o painel **Servers**.
   - Adicione o Tomcat como servidor clicando com o botão direito em **Servers** e selecionando **New > Server > Apache Tomcat**. 
   - Adicione o seu projeto ao servidor clicando com o botão direito no nome do servidor e selecionando **Add and Remove**. Mova o seu projeto para o lado da implantação.

2. **Executando o servidor local**
   - Com o Tomcat configurado, clique com o botão direito no servidor no painel **Servers** e selecione **Start** ou **Run As > Run on Server**.
   - O **Eclipse** abrirá um console onde você verá as mensagens de log do servidor. Se tudo estiver configurado corretamente, você verá uma mensagem indicando que o servidor foi iniciado com sucesso.
   - Abra um navegador e acesse `http://localhost:8080/hello` para verificar o funcionamento do servlet que criamos.

3. **Verificação do funcionamento do servidor**
   - Acesse a página inicial do Tomcat ou verifique os logs no console do **Eclipse** para confirmar que o servidor está funcionando corretamente.

#### **Perguntas:**
1. **Por que é necessário um servidor de aplicação local para o desenvolvimento web?**
   - O servidor local permite testar e depurar a aplicação antes de ela ser implantada em um ambiente de produção, proporcionando um ambiente controlado para desenvolvimento.

2. **Quais são os passos para configurar o Apache Tomcat como servidor local?**
   - Instalar o Tomcat, configurá-lo no **Eclipse** e adicionar o projeto ao servidor para que ele possa ser executado localmente.

3. **Como verificar se o servidor local está funcionando corretamente?**
   - A verificação pode ser feita acessando o navegador em `http://localhost:8080/` ou verificando os logs do servidor no console do **Eclipse**.

---

### **3.3 Verificação do Ambiente de Desenvolvimento**

Depois de configurar e executar o servidor local, é importante garantir que todo o ambiente de desenvolvimento esteja corretamente configurado, para que o fluxo de trabalho seja eficiente.

#### **Checklist para Verificação:**
- Verifique se a versão correta do **JDK** está instalada.
- Confirme se o **Eclipse** está configurado e funcionando corretamente.
- Certifique-se de que o **Apache Tomcat** está rodando e que o projeto foi implantado corretamente.
- Execute o servlet criado e verifique se ele responde corretamente no navegador.

#### **Execução de um Exemplo Simples**
- Execute o exemplo "Hello, World!" para garantir que a comunicação entre o servidor e o navegador está funcionando conforme o esperado.

#### **Perguntas:**
1. **Por que é crucial verificar se o ambiente de desenvolvimento está corretamente configurado?**
   - A verificação garante que todos os componentes estão prontos para o desenvolvimento, evitando problemas futuros que possam atrasar o progresso do projeto.

2. **Quais são os itens incluídos em um checklist para verificar o ambiente de desenvolvimento?**
   - O checklist inclui a verificação do JDK, da IDE **Eclipse**, do servidor local (Tomcat) e da execução correta do projeto.

3. **Como executar um exemplo simples para confirmar o funcionamento do ambiente?**
   - Um exemplo como o "Hello, World!" pode ser executado para garantir que o servidor está funcionando corretamente e que o ambiente está pronto para o desenvolvimento.

---

<a name="4"></a>
## **4. Atividade Prática 1: Criando uma Página de Índice e Tratamento de Erros 404**

### **Objetivo da Atividade:**
O objetivo desta atividade é ampliar suas habilidades em desenvolvimento web utilizando **Servlets** e **páginas HTML**. Você criará uma página de índice (`index.html`) para a aplicação, configurará um servlet para processar a página inicial e, em seguida, criará uma página personalizada para o tratamento de erros 404 (`error.html`), que será exibida quando um recurso não for encontrado.

### **Passo a Passo da Atividade:**

#### **1. Criação da Página Inicial (index.html)**

- No diretório **WebContent** (ou **webapp**, dependendo da configuração), crie um arquivo chamado `index.html`.
- Adicione o seguinte conteúdo HTML simples:
  ```html
  <!DOCTYPE html>
  <html lang="pt-br">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Página Inicial</title>
  </head>
  <body>
      <h1>Bem-vindo à Página Inicial</h1>
      <p>Esta é a página inicial da nossa aplicação web.</p>
      <a href="/hello">Ir para o Servlet "Hello, World!"</a>
  </body>
  </html>
  ```

#### **2. Modificando o Servlet "HelloServlet"**

- Se você já criou o servlet `HelloServlet` na Atividade Prática anterior, ele continuará funcionando para a URL `/hello`.
- Certifique-se de que o servlet está mapeado corretamente no arquivo **`web.xml`** dentro da pasta **WEB-INF**:
  ```xml
  <servlet>
      <servlet-name>HelloServlet</servlet-name>
      <servlet-class>com.meuprojeto.web.HelloServlet</servlet-class>
  </servlet>
  <servlet-mapping>
      <servlet-name>HelloServlet</servlet-name>
      <url-pattern>/hello</url-pattern>
  </servlet-mapping>
  ```

#### **3. Criação da Página de Erro 404 (error.html)**

- No diretório **WebContent**, crie um arquivo chamado `error.html` para tratar o erro 404 (página não encontrada).
- Adicione o seguinte conteúdo HTML:
  ```html
  <!DOCTYPE html>
  <html lang="pt-br">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Erro 404</title>
  </head>
  <body>
      <h1>Erro 404 - Página Não Encontrada</h1>
      <p>Desculpe, a página que você está tentando acessar não existe.</p>
      <a href="/">Voltar à Página Inicial</a>
  </body>
  </html>
  ```

#### **4. Configuração do Tratamento de Erros no `web.xml`**

- Para exibir a página personalizada `error.html` em caso de erro 404, adicione a seguinte configuração ao arquivo **`web.xml`**:
  ```xml
  <error-page>
      <error-code>404</error-code>
      <location>/error.html</location>
  </error-page>
  ```

#### **5. Testando a Aplicação**

1. **Executando o Projeto no Tomcat:**
   - Certifique-se de que o **Apache Tomcat** está configurado no **Eclipse**. Se o Tomcat ainda não estiver configurado, vá em **Window > Preferences > Server > Runtime Environments**, adicione o **Apache Tomcat** e configure o caminho de instalação.
   - Após a configuração, clique com o botão direito no projeto, selecione **Run As > Run on Server** e escolha o servidor Tomcat.
   - Ao acessar `http://localhost:8080/`, a página `index.html` deve ser carregada.

2. **Testando o Servlet:**
   - Acesse `http://localhost:8080/hello` para garantir que o servlet está funcionando e exibindo a mensagem "Hello, World!".

3. **Testando o Erro 404:**
   - Tente acessar uma URL inexistente, como `http://localhost:8080/inexistente`. O servidor deve exibir a página `error.html` com a mensagem de erro 404.

---

<a name="5"></a>
## **5. Atividade Prática 2: Criando uma Aplicação Web de Cadastro de Produtos**

### **Objetivo da Atividade:**
O objetivo desta atividade é garantir que você adquira as habilidades necessárias para configurar corretamente o ambiente de desenvolvimento e criar um projeto web funcional. Neste exemplo, você desenvolverá uma aplicação web de **Cadastro de Produtos** usando **Java** e **Apache Tomcat** no **Eclipse**. A aplicação será simples, mas com um formulário de cadastro que envia os dados para um servlet, o qual os processa e exibe de volta ao usuário.

### **Passo a Passo da Atividade:**

#### **1. Criação do Projeto Web no Eclipse**
- Abra o **Eclipse** e selecione **File > New > Dynamic Web Project**.
- Configure o nome do projeto (por exemplo, `CadastroDeProdutos`) e selecione a versão do **JDK** que foi previamente configurada.
- Escolha **Apache Tomcat** como o servidor de destino.
- Defina o local onde o projeto será salvo e clique em **Finish** para criar o projeto.

#### **2. Criando o Formulário de Cadastro de Produtos (HTML)**

- No diretório **WebContent**, crie um arquivo HTML chamado `cadastro-produto.html`.
- Adicione o seguinte conteúdo ao arquivo para criar um formulário simples de cadastro de produtos:
  ```html
  <!DOCTYPE html>
  <html lang="pt-br">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Cadastro de Produto</title>
  </head>
  <body>
      <h1>Cadastro de Produto</h1>
      <form action="/cadastro" method="post">
          <label for="nome">Nome do Produto:</label>
          <input type="text" id="nome" name="nome" required><br><br>
          <label for="preco">Preço:</label>
          <input type="number" id="preco" name="preco" required><br><br>
          <input type="submit" value="Cadastrar">
      </form>
  </body>
  </html>
  ```

#### **3. Criando o Servlet para Processar o Formulário**

- No diretório **src**, crie um pacote chamado `com.meuprojeto.web`.
- Dentro do pacote, crie uma classe Java chamada `CadastroProdutoServlet`:
  ```java
  package com.meuprojeto.web;

  import javax.servlet.ServletException;
  import javax.servlet.http.HttpServlet;
  import javax.servlet.http.HttpServletRequest;
  import javax.servlet.http.HttpServletResponse;
  import java.io.IOException;
  import java.io.PrintWriter;

  public class CadastroProdutoServlet extends HttpServlet {
      protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
          String nome = request.getParameter("nome");
          String preco = request.getParameter("preco");

          response.setContentType("text/html");
          PrintWriter out = response.getWriter();
          out.println("<h1>Produto Cadastrado com Sucesso!</h1>");
          out.println("<p>Nome do Produto: " + nome + "</p>");
          out.println("<p>Preço: R$" + preco + "</p>");
          out.println("<a href='/cadastro-produto.html'>Cadastrar outro produto</a>");
      }
  }
  ```

#### **4. Configuração do Servlet no `web.xml`**

- No diretório **WEB-INF**, abra o arquivo `web.xml` (se não existir, crie-o).
- Adicione o mapeamento do servlet:
  ```xml
  <web-app>
      <servlet>
          <servlet-name>CadastroProdutoServlet</servlet-name>
          <servlet-class>com.meuprojeto.web.CadastroProdutoServlet</servlet-class>
      </servlet>
      <servlet-mapping>
          <servlet-name>CadastroProdutoServlet</servlet-name>
          <url-pattern>/cadastro</url-pattern>
      </servlet-mapping>
  </web-app>
  ```

#### **5. Configuração e Execução do Servidor Local (Tomcat)**

- Certifique-se de que o **Apache Tomcat** está configurado no **Eclipse**. Caso não esteja, vá para **Window > Preferences > Server > Runtime Environments**, adicione o Tomcat e configure o diretório de instalação.
- Para rodar o servidor, clique com o botão direito no projeto e selecione **Run As > Run on Server**.
- Abra o navegador e acesse `http://localhost:8080/cadastro-produto.html`. Preencha o formulário com os dados do produto e clique em **Cadastrar**.

#### **6. Testando a Aplicação**

1. **Preencha o Formulário**: Na página `cadastro-produto.html`, preencha o nome e o preço de um produto.
2. **Envio e Processamento**: Quando o formulário for enviado, o servlet `CadastroProdutoServlet` processará os dados e exibirá uma mensagem confirmando o cadastro, junto com os detalhes do produto.
3. **Cadastrar Outro Produto**: Clique no link "Cadastrar outro produto" para voltar ao formulário.

#### **7. Verificação do Ambiente de Desenvolvimento**
- Após a execução do projeto, faça uma revisão completa do ambiente para garantir que tudo está funcionando corretamente. Verifique:
  - O **JDK** está configurado corretamente.
  - O **Eclipse** está funcionando sem erros.
  - O **Apache Tomcat** foi corretamente configurado e está rodando.
  - O servlet responde corretamente ao envio do formulário.

---

<a name="6"></a>
Aqui está a **Atividade Prática 3** com a inclusão dos **Servlets**, adaptada para o uso do **Eclipse**:

---

## **6. Atividade Prática 3: Criando um Menu de Navegação e Servlets para Páginas de Cadastro e Lista de Clientes**

### **Objetivo da Atividade:**
O objetivo desta atividade é expandir a estrutura da aplicação web com a criação de uma página inicial que contém um menu de navegação para outras páginas: **Cadastro de Clientes** e **Lista de Clientes**. Além disso, você criará dois **Servlets** que processam e exibem os dados para essas páginas, simulando a interação básica de navegação e processamento de dados.

### **Passo a Passo da Atividade:**

#### **1. Modificando a Página Inicial (index.html)**

- Atualize o arquivo `index.html` para incluir um menu de navegação. O menu deve ter links para as páginas **Cadastro de Clientes** e **Lista de Clientes**:
  ```html
  <!DOCTYPE html>
  <html lang="pt-br">
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Página Inicial</title>
  </head>
  <body>
      <h1>Bem-vindo à Página Inicial</h1>
      <p>Escolha uma das opções abaixo:</p>
      <ul>
          <li><a href="/cadastro-clientes">Cadastro de Clientes</a></li>
          <li><a href="/lista-clientes">Lista de Clientes</a></li>
      </ul>
  </body>
  </html>
  ```

#### **2. Criando a Página de Cadastro de Clientes com Servlet**

##### **2.1 Criação do Servlet para Cadastro de Clientes**

- No diretório **src**, crie um pacote chamado `com.meuprojeto.web`.
- Dentro do pacote, crie uma classe Java chamada `CadastroClienteServlet`:
  ```java
  package com.meuprojeto.web;

  import javax.servlet.ServletException;
  import javax.servlet.http.HttpServlet;
  import javax.servlet.http.HttpServletRequest;
  import javax.servlet.http.HttpServletResponse;
  import java.io.IOException;
  import java.io.PrintWriter;

  public class CadastroClienteServlet extends HttpServlet {
      protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
          response.setContentType("text/html");
          PrintWriter out = response.getWriter();
          out.println("<h1>Cadastro de Clientes</h1>");
          out.println("<p>Aqui você poderá cadastrar novos clientes (em breve).</p>");
          out.println("<a href='/'>Voltar à Página Inicial</a>");
      }
  }
  ```

##### **2.2 Configuração do Servlet no `web.xml`**

- No diretório **WEB-INF**, abra o arquivo `web.xml` (ou crie-o, caso ainda não exista).
- Adicione o mapeamento do servlet para **Cadastro de Clientes**:
  ```xml
  <servlet>
      <servlet-name>CadastroClienteServlet</servlet-name>
      <servlet-class>com.meuprojeto.web.CadastroClienteServlet</servlet-class>
  </servlet>
  <servlet-mapping>
      <servlet-name>CadastroClienteServlet</servlet-name>
      <url-pattern>/cadastro-clientes</url-pattern>
  </servlet-mapping>
  ```

#### **3. Criando a Página de Lista de Clientes com Servlet**

##### **3.1 Criação do Servlet para Lista de Clientes**

- No diretório **src**, crie uma classe Java chamada `ListaClienteServlet` dentro do pacote `com.meuprojeto.web`:
  ```java
  package com.meuprojeto.web;

  import javax.servlet.ServletException;
  import javax.servlet.http.HttpServlet;
  import javax.servlet.http.HttpServletRequest;
  import javax.servlet.http.HttpServletResponse;
  import java.io.IOException;
  import java.io.PrintWriter;

  public class ListaClienteServlet extends HttpServlet {
      protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
          response.setContentType("text/html");
          PrintWriter out = response.getWriter();
          out.println("<h1>Lista de Clientes</h1>");
          out.println("<p>Aqui você verá a lista de clientes cadastrados (em breve).</p>");
          out.println("<a href='/'>Voltar à Página Inicial</a>");
      }
  }
  ```

##### **3.2 Configuração do Servlet no `web.xml`**

- Adicione o mapeamento do servlet para **Lista de Clientes** no arquivo **`web.xml`**:
  ```xml
  <servlet>
      <servlet-name>ListaClienteServlet</servlet-name>
      <servlet-class>com.meuprojeto.web.ListaClienteServlet</servlet-class>
  </servlet>
  <servlet-mapping>
      <servlet-name>ListaClienteServlet</servlet-name>
      <url-pattern>/lista-clientes</url-pattern>
  </servlet-mapping>
  ```

#### **4. Testando a Navegação e os Servlets**

1. **Executando o Projeto no Tomcat:**
   - Certifique-se de que o **Apache Tomcat** está rodando e que o projeto foi corretamente implantado no **Eclipse**. Caso o Tomcat ainda não esteja configurado, vá para **Window > Preferences > Server > Runtime Environments** e adicione o Tomcat.
   - Execute o projeto clicando com o botão direito no nome do projeto e selecionando **Run As > Run on Server**.
   - Acesse `http://localhost:8080/` para ver a página inicial com o menu.

2. **Testando a Navegação entre Páginas:**
   - Clique nos links **Cadastro de Clientes** e **Lista de Clientes** para verificar se os **Servlets** correspondentes estão funcionando e exibindo as mensagens.
   - Use o link "Voltar à Página Inicial" em cada servlet para retornar ao menu principal.





