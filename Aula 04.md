## Aula 4: Utilizando Redirecionamento e Despacho com Servlets e JSP

### Objetivo da Aula
Nesta aula, exploraremos como usar redirecionamento e despacho (forwarding) em aplicativos web Java usando Servlets e JSP. Entenderemos como esses recursos podem ser usados para direcionar requisições entre diferentes páginas da web dentro de um aplicativo web.

O redirecionamento e o despacho em aplicativos web Java usando Servlets e JSP são fundamentais para direcionar solicitações entre diferentes partes de um aplicativo web e para controlar o fluxo de navegação do usuário. Compreender como usar redirecionamento e despacho é essencial para o desenvolvimento eficaz de aplicativos web Java.

### Redirecionamento (Redirect) em Servlets

O redirecionamento é usado quando desejamos enviar o navegador do cliente para outra página da web. Durante o redirecionamento, o servidor envia uma resposta HTTP com um código de status de redirecionamento (como 301 ou 302) e a URL para a qual o navegador deve ser redirecionado. Em Servlets, podemos usar o método `sendRedirect()` do objeto `HttpServletResponse` para realizar o redirecionamento.

### Despacho (Forwarding) em Servlets

O despacho (forwarding) é usado quando queremos encaminhar uma solicitação de um Servlet para outro recurso no servidor, como outro Servlet, um arquivo JSP ou mesmo um arquivo HTML. O despacho é feito no lado do servidor e o navegador do cliente não é informado sobre o despacho. O Servlet pode encaminhar a solicitação usando o método `getRequestDispatcher().forward()`.

### Redirecionamento e Despacho em JSP

Assim como em Servlets, podemos realizar redirecionamento e despacho em JSP. Para redirecionar em uma página JSP, podemos usar a diretiva `<jsp:forward>` e especificar a URL para onde queremos redirecionar. Para o despacho, também podemos usar `<jsp:forward>` ou podemos usar o objeto `RequestDispatcher` diretamente em código Java embutido na página JSP.

### Exemplos Práticos

#### Exemplo de Redirecionamento em Servlet

```java
@WebServlet("/redirectServlet")
public class RedirectServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
       

 response.sendRedirect("redirectedPage.jsp");
    }
}
```

#### Exemplo de Despacho em Servlet

```java
@WebServlet("/dispatchServlet")
public class DispatchServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        RequestDispatcher dispatcher = request.getRequestDispatcher("dispatchedPage.jsp");
        dispatcher.forward(request, response);
    }
}
```

#### Exemplo de Redirecionamento em JSP

```jsp
<jsp:forward page="redirectedPage.jsp" />
```

#### Exemplo de Despacho em JSP

```jsp
<%
    RequestDispatcher dispatcher = request.getRequestDispatcher("dispatchedPage.jsp");
    dispatcher.forward(request, response);
%>
```

### Exercício 1

**Desenvolva um aplicativo web que tenha duas páginas JSP e um Servlet. A primeira página JSP deve ter um formulário onde o usuário insere seu nome. Após o envio do formulário, o Servlet deve receber o nome e usar o redirecionamento para enviar o usuário para a segunda página JSP, onde uma mensagem de boas-vindas com o nome fornecido será exibida.**

#### Página JSP de Entrada (index.jsp)

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Formulário de Boas-vindas</title>
</head>
<body>
    <form action="welcomeServlet" method="post">
        Nome: <input type="text" name="nome">
        <input type="submit" value="Enviar">
    </form>
</body>
</html>
```

#### Servlet de Redirecionamento (WelcomeServlet.java)

```java
@WebServlet("/welcomeServlet")
public class WelcomeServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String nome = request.getParameter("nome");
        request.setAttribute("nome", nome);
        RequestDispatcher dispatcher = request.getRequestDispatcher("welcome.jsp");
        dispatcher.forward(request, response);
    }
}
```

#### Página JSP de Boas-vindas (welcome.jsp)

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Boas-vindas</title>
</head>
<body>
    <h1>Olá, <%= request.getAttribute("nome") %>! Bem-vindo!</h1>
</body>
</html>
```

### Exercício 2

**Desenvolva uma aplicação web de comércio eletrônico com várias funcionalidades, como login, carrinho de compras e finalização de pedido. Utilize redirecionamento para encaminhar o usuário para a página do painel do cliente após o login bem-sucedido e para retornar à página de login em caso de credenciais inválidas.**

#### Página de Login (login.jsp)

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <title>Login</title>
</head>
<body>
    <h1>Login</h1>
    <form action="loginServlet" method="post">
        Username: <input type="text" name="username"><br>
        Password: <input type="password" name="password"><br>
        <input type="submit" value="Login">
    </form>
    <p><%= request.getAttribute("errorMessage") %></p>
</body>
</html>
```

#### Servlet de Login (LoginServlet.java)

```java
@WebServlet("/loginServlet")
public class LoginServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String username = request.getParameter("username");
        String password = request.getParameter("password");
        
        // Lógica de verificação de credenciais (fictícia)
        if (username.equals("admin") && password.equals("admin123")) {
            response.sendRedirect("customerPanel.jsp");
        } else {
            request.setAttribute("errorMessage", "Credenciais inválidas. Tente novamente.");
            RequestDispatcher dispatcher = request.getRequestDispatcher("login.jsp");
            dispatcher.forward(request, response);
        }
    }
}
```

#### Página do Painel do Cliente (customerPanel.jsp)

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <title>Painel do Cliente</title>
</head>
<body>
    <h1>Bem-vindo ao seu Painel do Cliente</h1>
    <!-- Conteúdo do painel do cliente aqui -->
</body>
</html>
```

### Exercício 3

**Desenvolva uma aplicação web que permita ao usuário selecionar um produto e adicionar ao carrinho de compras. Utilize despacho para enviar a solicitação do Servlet para uma página JSP que exibe o carrinho de compras.**

#### Página JSP de Produtos (products.jsp)

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Produtos</title>
</head>
<body>
    <h1>Selecione um Produto</h1>
    <form action="addProductServlet" method="post">
        <select name="produto">
            <option value="Produto 1">Produto 1</option>
            <option value="Produto 2">Produto 2</option>
            <option value="Produto 3">Produto 3</option>
        </select>
        <input type="submit" value="Adicionar ao Carrinho">
    </form>
</body>
</html>
```

#### Servlet de Adição ao Carrinho (AddProductServlet.java)

```java
@WebServlet("/addProductServlet")
public class AddProductServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String produto = request.getParameter("produto");
        HttpSession session = request.getSession();
        List<String> carrinho = (List<String>) session.getAttribute("carrinho");
        if (carrinho == null) {
            carrinho = new ArrayList<>();
        }
        carrinho.add(produto);
        session.setAttribute("carrinho", carrinho);
        RequestDispatcher dispatcher = request.getRequestDispatcher("carrinho.jsp");
        dispatcher.forward(request, response);
    }
}
```

#### Página JSP do Carrinho de Compras (carrinho.jsp)

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Carrinho de Compras</title>
</head>
<body>
    <h1>Seu Carrinho de Compras</h1>
    <ul>
        <%
            List<String> carrinho = (List<String>) session.getAttribute("carrinho");
            if (carrinho != null) {
                for (String produto : carrinho) {
                    out.println("<li>" + produto + "</li>");
                }
            } else {
                out.println("<li>Carrinho vazio</li>");
            }
        %>
    </ul>
</body>
</html>
```

### Exercício 4

**Desenvolva uma aplicação web que permita ao usuário fazer logout. Utilize redirecionamento para enviar o usuário de volta à página de login após o logout.**

#### Servlet de Logout (LogoutServlet.java)

```java
@WebServlet("/logoutServlet")
public class LogoutServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        HttpSession session = request.getSession();
        session.invalidate();
        response.sendRedirect("login.jsp");
    }
}
```

#### Atualização na Página do Painel do Cliente (customerPanel.jsp)

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <title>Painel do Cliente</title>
</head>
<body>
    <h1>Bem-vindo ao seu Painel do Cliente</h1>
    <form action="logoutServlet" method="get">
        <input type="submit" value="Logout">
    </form>
    <!-- Conteúdo do painel do cliente aqui -->
</body>
</html>
```

### Recursos Adicionais

- [Documentação do HttpServlet](https://docs.oracle.com/javaee/7/api/javax/servlet/http/HttpServlet.html)
- [Documentação do RequestDispatcher](https://docs.oracle.com/javaee/7/api/javax/servlet/RequestDispatcher.html)

---
