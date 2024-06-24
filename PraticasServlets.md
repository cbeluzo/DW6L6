### Soluções para a Lista de Exercícios de Java Servlets

##### **Este material foi gerado com auxílio de ferramenta de Inteligência Artificial (ChatGPT 4.0). O seu conteúdo foi concebido, organizado e revisado pelo professor seguindo a ementa do plano da disciplina.**


#### Sumário

1. [Exercício de Estrutura Básica](#exercicio-1-servlet)
2. [Exercício de Manipulação de Parâmetros](#exercicio-2-servlet)
3. [Exercício de Manipulação de Formulários](#exercicio-3-servlet)
4. [Exercício de Redirecionamento](#exercicio-4-servlet)
5. [Exercício de Uso de Sessions](#exercicio-5-servlet)
6. [Exercício de Manipulação de Cookies](#exercicio-6-servlet)
7. [Exercício de Upload de Arquivos](#exercicio-7-servlet)
8. [Exercício de Segurança](#exercicio-8-servlet)

---

### <a name="exercicio-1-servlet"></a> 1. Exercício de Estrutura Básica
Crie um Servlet simples que responda a uma requisição GET e exiba uma mensagem de "Olá Mundo" no navegador.

```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class HelloWorldServlet
 * Exercicio: Crie um Servlet simples que responda a uma requisicao GET e exiba uma mensagem de "Ola Mundo" no navegador.
 */
@WebServlet("/helloWorld")
public class HelloWorldServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>Olá Mundo</h1>");
        out.println("</body></html>");
    }
}
```

### <a name="exercicio-2-servlet"></a> 2. Exercício de Manipulação de Parâmetros
Desenvolva um Servlet que receba parâmetros de consulta (query parameters) da URL e exiba esses parâmetros no navegador.

```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class ParameterServlet
 * Exercicio: Desenvolva um Servlet que receba parametros de consulta (query parameters) da URL e exiba esses parametros no navegador.
 */
@WebServlet("/showParams")
public class ParameterServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        String param1 = request.getParameter("param1");
        String param2 = request.getParameter("param2");
        out.println("<html><body>");
        out.println("<h1>Parametros recebidos:</h1>");
        out.println("<p>param1: " + param1 + "</p>");
        out.println("<p>param2: " + param2 + "</p>");
        out.println("</body></html>");
    }
}
```

### <a name="exercicio-3-servlet"></a> 3. Exercício de Manipulação de Formulários
Crie um Servlet que receba dados de um formulário HTML enviado por POST e exiba esses dados no navegador.

```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class FormDataServlet
 * Exercicio: Crie um Servlet que receba dados de um formulario HTML enviado por POST e exiba esses dados no navegador.
 */
@WebServlet("/submitForm")
public class FormDataServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        String nome = request.getParameter("nome");
        String email = request.getParameter("email");
        out.println("<html><body>");
        out.println("<h1>Dados recebidos do formulário:</h1>");
        out.println("<p>Nome: " + nome + "</p>");
        out.println("<p>Email: " + email + "</p>");
        out.println("</body></html>");
    }
}
```

### <a name="exercicio-4-servlet"></a> 4. Exercício de Redirecionamento
Desenvolva um Servlet que redirecione o navegador para outra página depois de receber uma requisição.

```java
import java.io.IOException;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class RedirectServlet
 * Exercicio: Desenvolva um Servlet que redirecione o navegador para outra pagina depois de receber uma requisicao.
 */
@WebServlet("/redirectTo")
public class RedirectServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.sendRedirect("https://www.example.com");
    }
}
```

### <a name="exercicio-5-servlet"></a> 5. Exercício de Uso de Sessions
Implemente um Servlet que utilize sessões para manter o estado do usuário, como contador de visitas.

```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.HttpSession;

/**
 * Servlet implementation class VisitCounterServlet
 * Exercicio: Implemente um Servlet que utilize sessoes para manter o estado do usuario, como contador de visitas.
 */
@WebServlet("/visitCounter")
public class VisitCounterServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        HttpSession session = request.getSession();
        Integer visitCount = (Integer) session.getAttribute("visitCount");
        if (visitCount == null) {
            visitCount = 1;
        } else {
            visitCount += 1;
        }
        session.setAttribute("visitCount", visitCount);

        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>Visita número: " + visitCount + "</h1>");
        out.println("</body></html>");
    }
}
```

### <a name="exercicio-6-servlet"></a> 6. Exercício de Manipulação de Cookies
Crie um Servlet que adicione um cookie à resposta e outro que leia o valor desse cookie em requisições subsequentes.

```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.Cookie;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

/**
 * Servlet implementation class CookieServlet
 * Exercicio: Crie um Servlet que adicione um cookie a resposta e outro que leia o valor desse cookie em requisicoes subsequentes.
 */
@WebServlet("/cookieHandler")
public class CookieServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // Adicionando um cookie à resposta
        Cookie userCookie = new Cookie("username", "JavaStudent");
        userCookie.setMaxAge(60 * 60 * 24); // 1 dia
        response.addCookie(userCookie);

        // Lendo cookies da requisição
        Cookie[] cookies = request.getCookies();
        String username = "desconhecido";
        if (cookies != null) {
            for (Cookie cookie : cookies) {
                if (cookie.getName().equals("username")) {
                    username = cookie.getValue();
                }
            }
        }

        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>Bem-vindo, " + username + "</h1>");
        out.println("</body></html>");
    }
}
```

### <a name="exercicio-7-servlet"></a> 7. Exercício de Upload de Arquivos
Desenvolva um Servlet que permita o upload de um arquivo e salve-o no servidor.

```java
import java.io.File;
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.StandardCopyOption;
import javax.servlet.ServletException;
import javax.servlet.annotation.MultipartConfig;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.http.Part;

/**
 * Servlet implementation class FileUploadServlet
 * Exercicio: Desenvolva um Servlet que permita o upload de um arquivo e salve-o no servidor.
 */
@WebServlet("/uploadFile")
@MultipartConfig
public class FileUploadServlet extends

 HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        Part filePart = request.getPart("file");
        String fileName = filePart.getSubmittedFileName();
        File uploads = new File("/uploads");
        if (!uploads.exists()) {
            uploads.mkdir();
        }
        File file = new File(uploads, fileName);

        try (var fileContent = filePart.getInputStream()) {
            Files.copy(fileContent, file.toPath(), StandardCopyOption.REPLACE_EXISTING);
        }

        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>Arquivo " + fileName + " enviado com sucesso!</h1>");
        out.println("</body></html>");
    }
}
```

### <a name="exercicio-8-servlet"></a> 8. Exercício de Segurança
Implemente um Servlet que valide dados de entrada, como campos de formulário, para evitar ataques de injeção de SQL ou XSS (cross-site scripting).

```java
import java.io.IOException;
import java.io.PrintWriter;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import org.apache.commons.text.StringEscapeUtils;

/**
 * Servlet implementation class SecurityServlet
 * Exercicio: Implemente um Servlet que valide dados de entrada, como campos de formulario, para evitar ataques de injecao de SQL ou XSS (cross-site scripting).
 */
@WebServlet("/validateInput")
public class SecurityServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String userInput = request.getParameter("input");
        
        // Sanitização da entrada para evitar XSS
        String sanitizedInput = StringEscapeUtils.escapeHtml4(userInput);

        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<html><body>");
        out.println("<h1>Entrada validada:</h1>");
        out.println("<p>" + sanitizedInput + "</p>");
        out.println("</body></html>");
    }
}
```