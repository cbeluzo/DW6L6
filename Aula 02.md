<a name="topo"></a>
# **Aula 2: Conceitos Fundamentais em Sistemas Web**

*Este material foi gerado com AI-Gen. A estrutura e conteúdo foi concebida e revisada pelo autor.*


### Objetivo da Aula
Nesta segunda aula do curso de Desenvolvimento Web Avançado, vamos aprofundar nossos conhecimentos nos conceitos essenciais relacionados a sistemas web. Discutiremos a evolução histórica das aplicações web e analisaremos casos de sucesso e fracasso no desenvolvimento web.

### Introdução aos Conceitos Fundamentais em Sistemas Web

1. **O que são Sistemas Web? Como eles se diferenciam de outras aplicações?**
   - Sistemas web são aplicações que funcionam através da internet, acessadas por meio de navegadores. Eles diferem de aplicações desktop por serem executados remotamente e não necessitarem de instalação no dispositivo do usuário. Além disso, sistemas web são escaláveis e podem ser acessados por múltiplos usuários simultaneamente.

2. **O que é a Arquitetura Cliente-Servidor?**
   - A arquitetura cliente-servidor é um modelo de comunicação onde o cliente (geralmente um navegador) faz requisições a um servidor. O servidor processa essas requisições e envia respostas de volta ao cliente. Essa relação permite a distribuição de tarefas e a separação de responsabilidades entre as partes.

3. **O que é o Protocolo HTTP?**
   - O Protocolo HTTP (Hypertext Transfer Protocol) é o padrão fundamental para comunicação na web. Ele define como os clientes (navegadores) e servidores trocam informações. As requisições HTTP são usadas para solicitar recursos (como páginas HTML, imagens e arquivos) e as respostas contêm esses recursos ou informações relevantes.

### Evolução Histórica das Aplicações Web

1. **Web 1.0**
   - **Características:** A Web 1.0 é conhecida como a “Web estática”. As páginas eram estáticas e a interação do usuário era limitada. As informações eram lidas e os usuários não podiam contribuir com conteúdo ou fazer alterações nas páginas.
   - **Limitações:** A principal limitação da Web 1.0 era a falta de interatividade. Os usuários não podiam interagir com o conteúdo da mesma forma que podem hoje. Além disso, a Web 1.0 era principalmente unidirecional, o que significa que os usuários podiam apenas receber informações, não compartilhá-las.

2. **Web 2.0: Transformações e interatividade na web**
   - **Transformações:** A Web 2.0 introduziu a “Web participativa”, onde os usuários não são apenas consumidores de informações, mas também criadores. Isso foi possível graças a tecnologias como blogs, redes sociais, wikis, que permitem aos usuários interagir e colaborar na web de maneira nunca antes vista.
   - **Interatividade:** A interatividade da Web 2.0 é possibilitada por várias tecnologias e conceitos, incluindo AJAX, RSS, SOA, mashups, que permitem aos usuários interagir com as páginas da web e entre si.

3. **Web 3.0 (Semantic Web): Visão futura da web com foco em dados semânticos**
   - **Definição:** A Web 3.0, também conhecida como “Web Semântica”, é uma extensão da Web 2.0 que visa tornar os dados na web facilmente interpretáveis por máquinas. Ela difere da Web 2.0 em seu foco em fornecer um significado (semântica) aos dados, permitindo que computadores e pessoas trabalhem em cooperação.
   - **Características:** Algumas das principais características da Web 3.0 incluem: dados ligados, que permitem que os dados sejam interconectados e mais úteis; inteligência artificial, que permite que máquinas entendam informações; e personalização, onde a web pode se adaptar e responder às necessidades individuais dos usuários.

### URL (Uniform Resource Locator)

- **Definição:** É um endereço da web que aponta para um recurso específico na internet. Ela é a “etiqueta” que você digita na barra de endereços do seu navegador para acessar um site, uma página da web ou um documento.
- **Importância:** URLs bem elaboradas melhoram a experiência do usuário e contribuem para a otimização de mecanismos de busca (SEO). Elas direcionam os usuários para páginas específicas, seções ou recursos dentro de um site.
- **Estrutura:** Uma URL contém várias partes:
  - Protocolo de Comunicação de Rede: Geralmente HTTP (Hypertext Transfer Protocol) ou HTTPS (Hypertext Transfer Protocol Secure).
  - Subdomínio (opcional): Por exemplo, www.
  - Nome do Domínio: Como hostinger.com ou microsoft.com.
  - Extensão de Domínio: Como .com, .org ou .br.
  - Caminho para o Recurso: Indica a localização específica do recurso no servidor.
  - Parâmetros (opcional): Informações adicionais passadas na URL.

### Perguntas e Respostas (Conceitos Teóricos):

1. **O que é uma aplicação web?**
   - Uma aplicação web é um software acessado por meio de um navegador e executado em um servidor web.

2. **Qual é o papel do protocolo HTTP na comunicação web?**
   - O protocolo HTTP (Hypertext Transfer Protocol) permite a transferência de dados entre o cliente e o servidor.

3. **O que diferencia a Web 2.0 da Web 1.0?**
   - A Web 2.0 introduziu maior interatividade, colaboração e participação dos usuários.

4. **Quais são os principais componentes de uma arquitetura cliente-servidor?**
   - Os principais componentes são o cliente (navegador) e o servidor web.

5. **Qual é o papel do servidor de aplicação web (como o Apache Tomcat) no desenvolvimento Java EE?**
   - O servidor de aplicação web hospeda e executa aplicações Java EE, gerenciando solicitações e respostas.

### Diferença entre um Servidor Web e um Servidor de Aplicação:

1. **Servidor Web:**
   - Um servidor web é responsável por hospedar sites e entregar páginas web para dispositivos clientes, como navegadores.
   - Ele lida com requisições feitas no protocolo HTTP (Hypertext Transfer Protocol) e seus derivados.
   - O servidor web pode servir dados estáticos, como páginas HTML, arquivos e imagens.
   - Exemplos de servidores web incluem o Apache HTTP Server (ou simplesmente Apache) e o Nginx.

2. **Servidor de Aplicação:**
   - Um servidor de aplicação hospeda e gerencia aplicativos, fornecendo serviços mais complexos.
   - Ele suporta protocolos como HTTP/s e RPC/RMI (Remote Procedure Call / Remote Method Invocation).
   - Além de servir páginas web, o servidor de aplicação executa lógica de negócios, processamento de transações e acesso a dados.
   - Exemplos de servidores de aplicação incluem o Apache Tomcat, WildFly (antigo JBoss) e IBM WebSphere.

### Diferença entre um Servidor Web e um Container de Servlet:

1. **Servidor Web:**
   - Um servidor web é responsável por hospedar sites e entregar páginas web para dispositivos clientes, como navegadores.
   - Ele lida com requisições feitas no protocolo HTTP (Hypertext Transfer Protocol) e seus derivados.
   - O servidor web pode servir dados estáticos, como páginas HTML, arquivos e imagens.
   - Exemplos de servidores web incluem o Apache HTTP Server (ou simplesmente Apache) e o Nginx.

2. **Container de Servlet (ou Servlet Container):**
   - Um container de servlet é um ambiente onde os servlets (componentes Java que processam requisições web) são executados.
   - Ele faz parte da especificação de Servlets e é específico para a tecnologia Java.
   - O container de servlet é responsável por gerenciar o ciclo de vida dos servlets, processar requisições HTTP e fornecer funcionalidades como sessões, autenticação e segurança.
   - Exemplos populares de containers de servlet incluem o Apache Tomcat e o Jetty.

### Java EE (Java Platform, Enterprise Edition)

- **Definição:** O Java EE é uma plataforma poderosa para construir sistemas empresariais e aplicações web escaláveis usando a linguagem Java. É um padrão para desenvolvimento de aplicações corporativas e web em Java.
- **Componentes Java EE:**
  - **Servlets:** Componentes Java que processam requisições HTTP.
  - **JavaServer Pages (JSP):** Páginas dinâmicas que misturam código Java com HTML.
  - **Enterprise JavaBeans (EJB):** Componentes para lógica de negócios e persistência de dados.
  - **Java Persistence API (JPA):** Mapeamento objeto-relacional para acesso a bancos de dados.
  - **Contexts and Dependency Injection (CDI):** Gerenciamento de componentes e injeção de dependências.

### Criando uma Aplicação Web em Java com o Apache Tomcat

**Passos para criar uma aplicação web em Java usando o Apache Tomcat:**

1. **Instale o Apache Tomcat:**
   - Faça o download do Tomcat a partir do site oficial.
   - Extraia o arquivo baixado para um diretório de sua escolha.

2. **Crie um Projeto Web:**
   - Abra sua IDE Java (como Eclipse, IntelliJ IDEA ou NetBeans).
   - Crie um novo projeto web (Dynamic Web Project) e escolha o servidor Apache Tomcat como destino.

3. **Estrutura do Projeto:**
   - O projeto web terá uma estrutura de diretórios padrão, incluindo

:
     - `src/main/java`: Onde você criará seus servlets e classes Java.
     - `src/main/webapp`: Contém arquivos JSP, HTML, CSS e recursos estáticos.
     - `WEB-INF`: Pasta especial que contém o arquivo `web.xml` (configurações da aplicação).

4. **Crie um Servlet:**
   - Crie uma classe Java que estenda `HttpServlet`.
   - Implemente os métodos `doGet` e `doPost` para processar as requisições HTTP.
   - Anote o servlet com `@WebServlet("/seu-caminho")`.

5. **Crie Páginas JSP:**
   - Crie arquivos JSP na pasta `webapp`.
   - Use tags JSP para misturar código Java com HTML.

6. **Configure o Deployment Descriptor (web.xml):**
   - No arquivo `web.xml`, defina mapeamentos para seus servlets e outras configurações.

7. **Implante a Aplicação no Tomcat:**
   - Copie o diretório do seu projeto (com os arquivos compilados) para a pasta `webapps` do Tomcat.
   - Inicie o Tomcat executando o script `startup.sh` (Linux) ou `startup.bat` (Windows).

8. **Acesse a Aplicação:**
   - Abra o navegador e acesse `http://localhost:8080/seu-projeto/seu-caminho`.

9. **Teste a Aplicação:**
   - Verifique se o servlet e as páginas JSP estão funcionando corretamente.

### Servlets

**Definição:** Servlets são classes Java desenvolvidas de acordo com uma estrutura bem definida. Quando instaladas e configuradas em um Servidor que implemente um Servlet Container, elas podem tratar requisições recebidas de clientes Web, como navegadores.

- **Funcionalidade:**
  - Um Servlet é uma classe Java que estende as propriedades de um servidor que hospeda uma aplicação.
  - Ele possibilita a abertura facilitada da sua aplicação para comunicação via métodos HTTP.

- **Processamento de Requisições:**
  - Quando um cliente (navegador) faz uma requisição, o Servlet pode capturar os parâmetros dessa requisição.
  - Ele efetua qualquer processamento inerente a uma classe Java e devolve uma página HTML como resposta.

- **Protocolo HTTP:**
  - Os Servlets são frequentemente usados com o protocolo HTTP (Hypertext Transfer Protocol).
  - Eles podem se comunicar sobre qualquer protocolo cliente-servidor, mas o HTTP é o mais comum.

### Exemplo de Código

#### Servlet (HelloWorldServlet.java):
```java
import javax.servlet.*;
import javax.servlet.http.*;
import java.io.*;

public class HelloWorldServlet extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>Hello, World!</h1>");
        out.println("</body></html>");
    }
}
```

### Exercícios Práticos:

1. **Exibir Data e Hora:**
   - Implemente um servlet que exiba a data e hora atual na página.

2. **Formulário HTML:**
   - Crie um formulário HTML que envie dados para um servlet e exiba uma mensagem personalizada.

3. **Servlet Interativo:**
   - Desenvolva um servlet que interage com o usuário através de um formulário HTML.

**Passos:**

1. **Configuração do ambiente:**
   - Certifique-se de ter um servidor de aplicação (como Tomcat ou Jetty) e um IDE (como Eclipse ou IntelliJ) instalados e configurados.

2. **Criação do projeto:**
   - Crie um novo projeto web no seu IDE.

3. **Criação do Servlet:**
   - Crie uma nova classe Java no seu projeto e estenda a classe `HttpServlet`. Implemente os métodos `doGet()` e `doPost()`.

4. **Implementação do `doGet()`:**
   - No método `doGet()`, escreva o código para enviar um formulário HTML ao cliente. O formulário deve incluir campos para o usuário inserir informações.

5. **Implementação do `doPost()`:**
   - No método `doPost()`, escreva o código para ler os dados enviados pelo cliente através do formulário. Você pode usar o método `request.getParameter()` para isso.

6. **Resposta ao cliente:**
   - Ainda no método `doPost()`, escreva o código para enviar uma resposta ao cliente. A resposta pode ser uma mensagem confirmando o recebimento dos dados.

7. **Configuração do web.xml:**
   - No arquivo `web.xml` do seu projeto, adicione uma entrada para o seu servlet. Isso irá mapear uma URL para o seu servlet.

8. **Teste o seu Servlet:**
   - Inicie o seu servidor de aplicação e acesse o seu servlet através da URL que você mapeou no `web.xml`. Preencha o formulário e verifique se a resposta é enviada corretamente.

#### Código do Servlet Interativo (MeuServletInterativo.java):
```java
import java.io.*;
import javax.servlet.*;
import javax.servlet.http.*;

public class MeuServletInterativo extends HttpServlet {
    public void doGet(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<form method='post'>");
        out.println("Nome: <input type='text' name='nome' />");
        out.println("<input type='submit' value='Enviar' />");
        out.println("</form>");
        out.println("</body></html>");
    }

    public void doPost(HttpServletRequest request, HttpServletResponse response)
            throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        String nome = request.getParameter("nome");
        out.println("<html><body>");
        out.println("<h1>Ola, " + nome + "!</h1>");
        out.println("</body></html>");
    }
}
```

*Este servlet exibe um formulário HTML quando acessado com um método GET. Quando o formulário é enviado (método POST), ele lê o parâmetro ‘nome’ do pedido e exibe uma saudação personalizada. Lembre-se de substituir “MeuServletInterativo” pelo nome que você deseja dar ao seu servlet.

Em uma aplicação real, você precisaria adicionar tratamento de erros e possivelmente outras funcionalidades. Além disso, este código pressupõe que você está familiarizado com a configuração de servlets em seu servidor web e com a compilação de código Java. Se você não estiver, pode ser útil consultar a documentação do seu servidor web ou um tutorial de Java para obter instruções passo a passo.

---

**Exercícios:**
1) Alterar o servlet para fazer uma autenticação de usuário e senha. Armzenar o usuário e senha em variáveis locais.

2) Criar uma aplicação web que permite fazer registro de usuário (email) e senha. Quando usuário se cadastra, as informações são armazendas em um vetor (Array). Quando o usuário faz o login, a aplicação verifica se usuario existe no vetor, e se a senha corresponde aquela armazenda no vetor.

---
