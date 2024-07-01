## Aula 3: Desenvolvimento de Sistemas Web usando JSP (Java Server Pages)

### Introdução ao Desenvolvimento Web com JEE e JSP

**Pergunta:** O que é JEE (Java Enterprise Edition) e como ele se relaciona com o desenvolvimento web?
**Resposta:** O Java Enterprise Edition (JEE) é uma plataforma para o desenvolvimento de aplicativos corporativos em Java. Ele fornece um conjunto de APIs e serviços para facilitar o desenvolvimento de aplicativos robustos e escaláveis. No contexto do desenvolvimento web, o JEE fornece tecnologias como Servlets, JSP (JavaServer Pages), JSTL (JavaServer Pages Standard Tag Library), e EJB (Enterprise JavaBeans) para criar aplicativos web dinâmicos e escaláveis.

### Introdução ao JSP

**Pergunta:** O que são JavaServer Pages (JSP) e como elas são usadas no desenvolvimento web?
**Resposta:** JSP é uma tecnologia utilizada para criar páginas web dinâmicas em Java. Ela permite a mistura de código HTML com elementos Java, facilitando a criação de páginas web que podem interagir com dados, processar formulários e realizar outras operações dinâmicas. As páginas JSP são arquivos de texto com extensão ".jsp" que contêm HTML, XML, JavaScript, e fragmentos de código Java. O servidor JSP processa esses arquivos para criar páginas web dinâmicas, substituindo as tags JSP por código Java e, em seguida, executando esse código antes de enviar a página resultante para o cliente.

### Configurando o Ambiente

**Pergunta:** Como configurar o ambiente para desenvolvimento de JSP com Apache Tomcat?
**Resposta:** Para começar a desenvolver com JSP usando Apache Tomcat, é necessário primeiro instalar o Apache Tomcat no seu sistema e configurar sua IDE de desenvolvimento para que ela possa se comunicar com o Tomcat. Em seguida, é necessário criar um projeto web no seu IDE e configurá-lo para ser implantado no Tomcat.

### Criando Páginas JSP

**Pergunta:** Como criar uma página JSP básica?
**Resposta:** Para criar uma página JSP, crie um arquivo com a extensão .jsp e escreva seu código HTML normalmente. Você pode inserir trechos de código Java entre tags `<% %>` para realizar operações dinâmicas. Por exemplo:

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Exemplo de Página JSP</title>
</head>
<body>
    <h1>Olá, Mundo!</h1>
    <p>A data atual é: <%= new java.util.Date() %></p>
</body>
</html>
```

### Exemplo de Uso de JSP

**Pergunta:** Como criar uma página JSP que recebe e exibe dados do usuário?
**Resposta:** Vamos criar uma página JSP simples que solicita ao usuário seu nome e exibe uma mensagem de boas-vindas personalizada.

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Formulário de Boas-vindas</title>
</head>
<body>
    <form action="mensagem.jsp" method="post">
        Nome: <input type="text" name="nome">
        <input type="submit" value="Enviar">
    </form>
</body>
</html>
```

Agora, criaremos uma página JSP chamada `mensagem.jsp` que receberá o nome do usuário e exibirá a mensagem de boas-vindas:

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Mensagem de Boas-vindas</title>
</head>
<body>
    <% 
        String nome = request.getParameter("nome");
        if (nome != null && !nome.isEmpty()) {
    %>
            <h1>Olá, <%= nome %>! Bem-vindo!</h1>
    <%
        } else {
    %>
            <h1>Olá, visitante! Bem-vindo!</h1>
    <%
        }
    %>
</body>
</html>
```

### Exercício 1

**Pergunta:** Crie uma página JSP que permita ao usuário calcular a área de um retângulo. A página deve solicitar os valores da base e altura do retângulo e exibir a área calculada.
**Resposta:**

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Calculadora de Área de Retângulo</title>
</head>
<body>
    <form action="calcular.jsp" method="post">
        Base: <input type="number" name="base"><br>
        Altura: <input type="number" name="altura"><br>
        <input type="submit" value="Calcular Área">
    </form>
</body>
</html>
```

Crie uma página JSP chamada `calcular.jsp` que calculará a área do retângulo:

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Resultado do Cálculo</title>
</head>
<body>
    <% 
        double base = Double.parseDouble(request.getParameter("base"));
        double altura = Double.parseDouble(request.getParameter("altura"));
        double area = base * altura;
    %>
    <h1>A área do retângulo é: <%= area %></h1>
</body>
</html>
```

### Exercício 2

**Pergunta:** Desenvolva uma aplicação web simples que permita aos usuários calcular a média de três notas. A aplicação deve ter uma página de entrada para inserção das notas e uma página de resultado que exibe a média calculada.
**Resposta:** Primeiro, crie uma página JSP chamada `index.jsp` para a entrada das notas:

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
    <title>Calculadora de Média</title>
</head>
<body>
    <h1>Calculadora de Média</h1>
    <form action="calcularMedia.jsp" method="post">
        Nota 1: <input type="text" name="nota1"><br>
        Nota 2: <input type="text" name="nota2"><br>
        Nota 3: <input type="text" name="nota3"><br>
        <input type="submit" value="Calcular Média">
    </form>
</body>
</html>
```

Em seguida, crie uma página JSP chamada `calcularMedia.jsp` para calcular a média e exibir o resultado:

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="java.text.DecimalFormat" %>
<!DOCTYPE html>
<html>
<head>
    <title>Resultado do Cálculo</title>
</head>
<body>
    <%
        double nota1 = Double.parseDouble(request.getParameter("nota1"));
        double nota2 = Double.parseDouble(request.getParameter("nota2"));
        double nota3 = Double.parseDouble(request.getParameter("nota3"));
        double media = (nota1 + nota2 + nota3) / 3;
        DecimalFormat df = new DecimalFormat("#.##");
        String formattedMedia = df.format(media);
    %>
    <h1>A média das notas é: <%= formattedMedia %></h1>
</body>
</html>
```

### Exercício 3

**Pergunta:** Crie uma página JSP que solicite ao usuário dois números e exiba o maior número entre eles.
**Resposta:**

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Maior Número</title>
</head>
<body>
    <form action="maiorNumero.jsp" method="post">
        Número 1: <input type="number" name="numero1"><br>
        Número 2: <input type="number" name="numero2"><br>
        <input type="submit" value="Verificar Maior Número">
    </form>
</body>
</html>
```

Crie uma página JSP chamada `maiorNumero.jsp` que exibirá o maior número entre os dois informados:

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Resultado</title>
</head>
<body>
    <%
        double numero1 = Double.parseDouble(request.getParameter("numero1"));
        double numero2 = Double.parseDouble(request.getParameter("numero2"));
        double maior = (numero1 > numero2) ? numero1 : numero2;
    %>
    <h1>O maior número é: <%= maior %></h1>
</body>
</html>
```

### Exercício 4

**Pergunta:** Crie uma aplicação web usando JSP que permita ao usuário converter uma temperatura de Celsius para Fahrenheit.
**Resposta:**

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Conversor de Temperatura</title>
</head>
<body>
    <form action="converter.jsp" method="post">
        Temperatura em Celsius: <input type="number" step="0.1" name="celsius"><br>
        <input type="submit" value="Converter para Fahrenheit">
    </form>
</body>
</html>
```

Crie uma página JSP chamada `converter.jsp` que fará a conversão da temperatura e exibirá o resultado:

```jsp
<!DOCTYPE html>
<html>
<head>
    <title>Resultado da Conversão</title>
</head>
<body>
    <%
        double celsius = Double.parseDouble(request.getParameter("celsius"));
        double fahrenheit = (celsius * 9/5) + 32;
    %>
    <h1>A temperatura em Fahrenheit é: <%= fahrenheit %

></h1>
</body>
</html>
```
