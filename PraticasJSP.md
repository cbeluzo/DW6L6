### Soluções para a Lista de Exercícios de JSP

Prof. Carlos Beluzo - beluzo@ifsp.edu.br

##### **Este material foi gerado com auxílio de ferramenta de Inteligência Artificial (ChatGPT 4o). O seu conteúdo foi concebido, organizado e revisado pelo professor seguindo a ementa do plano da disciplina.*

#### Sumário

1. [Exercício de Estrutura Básica](#exercicio-1)
2. [Exercício de Looping](#exercicio-2)
3. [Exercício de Condição](#exercicio-3)
4. [Exercício de Interação com o Usuário](#exercicio-4)
5. [Exercício de Manipulação de Dados](#exercicio-5)
6. [Exercício de Uso de Funções](#exercicio-6)

---

### <a name="exercicio-1"></a> 1. Exercício de Estrutura Básica
Escreva um arquivo JSP que exiba uma página HTML simples com uma mensagem de boas-vindas. Utilize a sintaxe JSP para incorporar Java no código HTML.

```jsp
<!-- welcome.jsp -->
<!DOCTYPE html>
<html>
<head>
    <title>Bem-vindo</title>
</head>
<body>
    <h1><%= "Olá, Bem-vindo ao Mundo JSP!" %></h1>
</body>
</html>
```

### <a name="exercicio-2"></a> 2. Exercício de Looping
Crie um arquivo JSP que utilize um loop para exibir uma lista de números de 1 a 10 em uma tabela HTML.

```jsp
<!-- numbers.jsp -->
<!DOCTYPE html>
<html>
<head>
    <title>Números de 1 a 10</title>
</head>
<body>
    <h1>Números de 1 a 10</h1>
    <table border="1">
        <tr>
            <th>Número</th>
        </tr>
        <% for (int i = 1; i <= 10; i++) { %>
        <tr>
            <td><%= i %></td>
        </tr>
        <% } %>
    </table>
</body>
</html>
```

### <a name="exercicio-3"></a> 3. Exercício de Condição
Desenvolva um arquivo JSP que utilize uma instrução de condição para exibir diferentes mensagens dependendo do valor de uma variável Java. Por exemplo, se a variável for verdadeira, exiba uma mensagem de sucesso, caso contrário, exiba uma mensagem de erro.

```jsp
<!-- condition.jsp -->
<!DOCTYPE html>
<html>
<head>
    <title>Condição JSP</title>
</head>
<body>
    <%
        boolean sucesso = true;
    %>
    <% if (sucesso) { %>
        <h1>Operação realizada com sucesso!</h1>
    <% } else { %>
        <h1>Ocorreu um erro na operação.</h1>
    <% } %>
</body>
</html>
```

### <a name="exercicio-4"></a> 4. Exercício de Interação com o Usuário
Crie um formulário HTML em um arquivo JSP que solicite ao usuário seu nome. Em seguida, exiba uma mensagem de saudação personalizada utilizando a entrada do usuário.

```jsp
<!-- form.jsp -->
<!DOCTYPE html>
<html>
head>
    <title>Formulário de Saudação</title>
</head>
<body>
    <h1>Digite seu nome:</h1>
    <form action="greeting.jsp" method="post">
        Nome: <input type="text" name="nome">
        <input type="submit" value="Enviar">
    </form>
</body>
</html>
```

```jsp
<!-- greeting.jsp -->
<!DOCTYPE html>
<html>
head>
    <title>Saudação</title>
</head>
<body>
    <%
        String nome = request.getParameter("nome");
    %>
    <h1>Olá, <%= nome %>! Bem-vindo!</h1>
</body>
</html>
```

### <a name="exercicio-5"></a> 5. Exercício de Manipulação de Dados
Escreva um arquivo JSP que utilize um ArrayList Java para armazenar uma lista de nomes. Exiba esses nomes em uma lista HTML não ordenada.

```jsp
<!-- names.jsp -->
<%@ page import="java.util.ArrayList" %>
<!DOCTYPE html>
<html>
head>
    <title>Lista de Nomes</title>
</head>
<body>
    <h1>Lista de Nomes</h1>
    <%
        ArrayList<String> nomes = new ArrayList<>();
        nomes.add("Alice");
        nomes.add("Bob");
        nomes.add("Carlos");
    %>
    <ul>
        <% for (String nome : nomes) { %>
            <li><%= nome %></li>
        <% } %>
    </ul>
</body>
</html>
```

### <a name="exercicio-6"></a> 6. Exercício de Uso de Funções
Desenvolva um arquivo JSP que defina uma função Java personalizada e a invoque a partir do código JSP para realizar uma tarefa específica, como calcular a soma de dois números passados como parâmetros.

```jsp
<!-- sum.jsp -->
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
head>
    <title>Soma de Números</title>
</head>
<body>
    <h1>Calculadora de Soma</h1>
    <form action="result.jsp" method="post">
        Número 1: <input type="number" name="num1"><br>
        Número 2: <input type="number" name="num2"><br>
        <input type="submit" value="Calcular">
    </form>
</body>
</html>
```

```jsp
<!-- result.jsp -->
<%@ page import="java.io.*" %>
<!DOCTYPE html>
<html>
head>
    <title>Resultado da Soma</title>
</head>
<body>
    <%
        int num1 = Integer.parseInt(request.getParameter("num1"));
        int num2 = Integer.parseInt(request.getParameter("num2"));

        int soma(int a, int b) {
            return a + b;
        }

        int resultado = soma(num1, num2);
    %>
    <h1>Resultado: <%= resultado %></h1>
</body>
</html>
```

---

Essas são as soluções para a lista de exercícios de JSP. As explicações foram incluídas como comentários dentro do código para facilitar a compreensão dos exercícios.