# **Aula 3: Redirecionamento, Despacho, Sessões e Cookies em Servlets**

### **1. Introdução**
- Nesta aula, vamos explorar como **Servlets** em **Java** são usados para controlar o fluxo de requisições HTTP e manter informações de estado em aplicações web.
- Vamos abordar quatro tópicos importantes:
  1. **Redirecionamento**: Enviar o cliente para outra URL.
  2. **Despacho (Request Dispatch)**: Encaminhar a requisição para outro servlet ou página interna.
  3. **Sessões**: Armazenar dados temporários associados ao usuário.
  4. **Cookies**: Armazenar pequenos pedaços de dados no navegador do cliente.

---

### **Tópico 1: Redirecionamento**

#### **O que é Redirecionamento?**

O redirecionamento ocorre quando o servidor instrui o navegador a solicitar uma nova URL. Quando usamos o método `sendRedirect()`, o servidor responde ao cliente com um código HTTP 3xx (geralmente **302 Found**), indicando que o navegador deve acessar outra página.

- **Quando usar**:
  - Após o login para redirecionar o usuário à página principal.
  - Quando uma página foi movida e o servidor precisa redirecionar o cliente para o novo local.

#### **Exemplo Prático: Redirecionamento Simples para uma Página de Boas-Vindas**

##### **1.1. HTML Formulário de Login (index.html)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Login Page</title>
</head>
<body>
    <h2>Login</h2>
    <form action="login" method="post">
        <label for="username">Username:</label>
        <input type="text" id="username" name="username" required><br>
        <label for="password">Password:</label>
        <input type="password" id="password" name="password" required><br>
        <button type="submit">Login</button>
    </form>
</body>
</html>
```

##### **1.2. Servlet: LoginServlet.java**

```java
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;

public class LoginServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String username = request.getParameter("username");
        String password = request.getParameter("password");

        if ("admin".equals(username) && "123".equals(password)) {
            response.sendRedirect("welcome.html");
        } else {
            response.sendRedirect("error.html");
        }
    }
}
```

##### **1.3. Página de Boas-Vindas (welcome.html)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Welcome</title>
</head>
<body>
    <h1>Welcome, admin!</h1>
</body>
</html>
```

##### **1.4. Página de Erro (error.html)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Error</title>
</head>
<body>
    <h1>Login Failed! Invalid credentials.</h1>
</body>
</html>
```

---

### **Tópico 2: Despacho (Request Dispatcher)**

#### **O que é Despacho (Request Dispatch)?**

O **despacho** (ou **forwarding**) é o processo de encaminhar uma requisição de um servlet para outro servlet ou página dentro da mesma aplicação, sem que o cliente (navegador) faça uma nova requisição. Diferente do redirecionamento, o endereço da URL não muda, e o cliente não vê a troca.

- **Quando usar**:
  - Quando é necessário reutilizar a lógica de outro servlet ou página para processar parte da requisição.
  - Quando se deseja manter a URL original visível ao usuário.

#### **Exemplo Prático: Encaminhando a Requisição para Outro Servlet**

##### **2.1. Servlet: MainServlet.java**

```java
import jakarta.servlet.RequestDispatcher;
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;

public class MainServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String param = request.getParameter("param");

        // Adiciona um atributo à requisição para ser lido no próximo servlet
        request.setAttribute("message", "Received Parameter: " + param);

        // Despacha a requisição para o ProcessServlet
        RequestDispatcher dispatcher = request.getRequestDispatcher("/ProcessServlet");
        dispatcher.forward(request, response);
    }
}
```

##### **2.2. Servlet: ProcessServlet.java**

```java
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;

public class ProcessServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        String message = (String) request.getAttribute("message");
        
        // Exibe a mensagem passada pelo MainServlet
        out.println("<h1>" + message + "</h1>");
    }
}
```

##### **2.3. HTML Form para Disparar o Despacho (index.html)**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Dispatcher Example</title>
</head>
<body>
    <h2>Dispatcher Example</h2>
    <form action="MainServlet" method="get">
        <label for="param">Enter Parameter:</label>
        <input type="text" id="param" name="param" required><br>
        <button type="submit">Send Parameter</button>
    </form>
</body>
</html>
```

---

### **Tópico 3: Sessões**

#### **O que é uma Sessão?**

As **sessões** permitem que o servidor armazene informações específicas do usuário entre requisições HTTP, garantindo que dados como autenticação e preferências sejam mantidos enquanto o usuário navega no site. O estado é preservado no lado do servidor.

- **Quando usar**:
  - Para gerenciar logins de usuários.
  - Para manter dados temporários como carrinhos de compras, preferências ou progresso de navegação.

#### **Exemplo Prático: Sessões para Login**

##### **3.1. Servlet: LoginSessionServlet.java**

```java
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import jakarta.servlet.http.HttpSession;
import java.io.IOException;

public class LoginSessionServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String username = request.getParameter("username");

        // Cria uma nova sessão para o usuário
        HttpSession session = request.getSession();
        session.setAttribute("username", username);

        // Redireciona para o dashboard
        response.sendRedirect("dashboard");
    }
}
```

##### **3.2. Servlet: DashboardServlet.java**

```java
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import jakarta.servlet.http.HttpSession;
import java.io.IOException;
import java.io.PrintWriter;

public class DashboardServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();

        // Obtém a sessão atual
        HttpSession session = request.getSession(false);
        if (session != null) {
            String username = (String) session.getAttribute("username");
            out.println("<h1>Welcome, " + username + "!</h1>");
        } else {
            out.println("<h1>No active session. Please login.</h1>");
        }
    }
}
```

##### **3.3. Servlet: LogoutServlet.java**

```java
import jakarta.servlet.ServletException;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import jakarta.servlet.http.HttpSession;
import java.io.IOException;

public class LogoutServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        // Invalida a sessão atual
        HttpSession session = request.getSession(false);
        if (session != null) {
            session.invalidate();
        }
        response.sendRedirect("login.html");
    }
}
```

---

### **Tópico 4: Cookies**

#### **O que é um

 Cookie?**

Um **cookie** é um pequeno pedaço de dados armazenado no navegador do cliente. Ele é enviado pelo servidor ao cliente e armazenado localmente, sendo reenviado ao servidor a cada requisição subsequente. Cookies são usados para manter informações do usuário entre requisições.

- **Quando usar**:
  - Para manter preferências do usuário, como idioma ou tema.
  - Para lembrar informações de login entre sessões.

#### **Exemplo Prático: Criando e Lendo Cookies**

##### **4.1. Servlet: CookieServlet.java**

```java
import jakarta.servlet.ServletException;
import jakarta.servlet.http.Cookie;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;

public class CookieServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String username = request.getParameter("username");

        // Cria um cookie e define o tempo de expiração para 1 hora
        Cookie userCookie = new Cookie("username", username);
        userCookie.setMaxAge(60 * 60); // 1 hora
        response.addCookie(userCookie);

        response.sendRedirect("welcome-cookie");
    }
}
```

##### **4.2. Servlet: WelcomeCookieServlet.java**

```java
import jakarta.servlet.ServletException;
import jakarta.servlet.http.Cookie;
import jakarta.servlet.http.HttpServlet;
import jakarta.servlet.http.HttpServletRequest;
import jakarta.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;

public class WelcomeCookieServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        Cookie[] cookies = request.getCookies();
        String username = null;

        // Percorre os cookies para encontrar o cookie de nome "username"
        if (cookies != null) {
            for (Cookie cookie : cookies) {
                if ("username".equals(cookie.getName())) {
                    username = cookie.getValue();
                    break;
                }
            }
        }

        response.setContentType("text/html");
        PrintWriter out = response.getWriter();

        if (username != null) {
            out.println("<h1>Welcome back, " + username + "!</h1>");
        } else {
            out.println("<h1>User not found!</h1>");
        }
    }
}
```

---

### **Lista de Exercícios**

#### **Tópico 1: Redirecionamento**
1. **(Fácil)** Crie um servlet que redirecione o usuário para uma página de boas-vindas após o login.
2. **(Intermediário)** Modifique o exemplo anterior para redirecionar o usuário com base no sucesso ou falha do login.

#### **Tópico 2: Despacho (Dispatch)**
1. **(Fácil)** Crie um servlet que receba um parâmetro e despache a requisição para outro servlet, que exibe o valor recebido.
2. **(Intermediário)** Crie um servlet que despache a requisição para uma página JSP que exiba os dados processados no primeiro servlet.

#### **Tópico 3: Sessões**
1. **(Fácil)** Crie um servlet que armazene o nome do usuário em uma sessão após o login e exiba o nome em outra página.
2. **(Intermediário)** Implemente um sistema de login com sessão, onde o usuário pode fazer logout, e a sessão é invalidada.

#### **Tópico 4: Cookies**
1. **(Fácil)** Crie um servlet que armazene o nome do usuário em um cookie e, em outro servlet, recupere e exiba o valor do cookie.
2. **(Intermediário)** Crie um servlet que armazene o nome do usuário em um cookie com tempo de expiração e outro que remova o cookie.
