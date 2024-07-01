# Atividade 1: Sistema de Gerenciamento de Serviços para Clínica Estética com Agendamento de Sessões

## Objetivo
Nesta atividade, você irá desenvolver um sistema web para uma clínica estética que permite o gerenciamento de serviços oferecidos, incluindo o agendamento de sessões. O sistema possibilitará aos usuários visualizar os serviços disponíveis, agendar sessões para cada serviço e visualizar detalhes das sessões agendadas.

## Parte 1: Definição da Arquitetura do Sistema:

1. Modelo de Dados:
   - O sistema terá uma classe `Service` para representar os diferentes serviços oferecidos pela clínica estética. Cada serviço terá os seguintes atributos: `id`, `name`, `description` e `price`.
   - Além disso, haverá uma classe `Session` para representar as sessões agendadas para cada serviço. Cada sessão terá os atributos `id`, `serviceId`, `date` e `time`.

2. Servlets:
   - Crie Servlets para realizar as operações CRUD (Create, Read, Update, Delete) nos serviços e sessões. Por exemplo: `ListServicesServlet`, `AddServiceServlet`, `ViewServiceServlet`, `UpdateServiceServlet`, `DeleteServiceServlet`, `ListSessionsServlet`, `AddSessionServlet`, `DeleteSessionServlet`.
   - Utilize os Servlets para processar requisições HTTP, interagir com os objetos de modelo e encaminhar o fluxo para as páginas JSP correspondentes.

3. JSPs:
   - Crie páginas JSP para representar as diferentes telas do sistema, como a lista de serviços, detalhes de cada serviço, formulário de agendamento de sessões e lista de sessões agendadas.
   - Utilize JSPs para exibir dados dinâmicos e interagir com os Servlets por meio de solicitações e respostas HTTP.

## Parte 2: Desenvolvimento do Sistema:

1. Listagem de Serviços:
   - Crie uma página JSP chamada `listServices.jsp` para exibir a lista de serviços oferecidos pela clínica estética.
   - Utilize um Servlet (`ListServicesServlet`) para recuperar a lista de serviços do modelo e encaminhá-la para a página JSP.
   - Na página JSP, itere sobre a lista de serviços e exiba os detalhes de cada serviço, incluindo botões para visualizar detalhes e agendar sessões.

2. Visualização de Detalhes do Serviço:
   - Desenvolva uma página JSP chamada `viewService.jsp` para exibir os detalhes de um serviço específico, incluindo sua descrição e preço.
   - Implemente um Servlet (`ViewServiceServlet`) para recuperar os detalhes do serviço com base no ID fornecido na solicitação e encaminhá-los para a página JSP.

3. Agendamento de Sessões:
   - Crie um formulário em uma página JSP (`addSession.jsp`) para permitir aos usuários agendar sessões para um serviço específico.
   - Desenvolva um Servlet (`AddSessionServlet`) para processar o formulário e adicionar a sessão ao modelo.
   - Após o agendamento bem-sucedido, redirecione o usuário de volta à página de visualização do serviço.

4. Listagem de Sessões Agendadas:
   - Crie uma página JSP chamada `listSessions.jsp` para exibir a lista de sessões agendadas para um serviço específico.
   - Utilize um Servlet (`ListSessionsServlet`) para recuperar a lista de sessões do modelo com base no serviço selecionado e encaminhá-la para a página JSP.
   - Na página JSP, exiba os detalhes de cada sessão agendada, incluindo data e hora.

## Parte 3: Integração e Testes:
1. Integre os Servlets e as páginas JSP desenvolvidas ao projeto principal.
2. Execute o servidor web e teste todas as funcionalidades do sistema, certificando-se de que é possível visualizar os serviços, agendar sessões e visualizar as sessões agendadas.
3. Verifique se as páginas JSP estão sendo renderizadas corretamente e se os dados estão sendo exibidos conforme o esperado.

## Passo 4: Conclusão:
Disponibilizar no GitHub.

---

# Solução

#### Parte 1: Definição da Arquitetura do Sistema

**Modelo de Dados**

```java
// Service.java
package com.example.model;

public class Service {
    private int id;
    private String name;
    private String description;
    private double price;

    // Getters e setters
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getDescription() {
        return description;
    }

    public void setDescription(String description) {
        this.description = description;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        if (price < 0) {
            throw new IllegalArgumentException("Price must be a positive number");
        }
        this.price = price;
    }
}
```

```java
// Session.java
package com.example.model;

import java.util.Date;

public class Session {
    private int id;
    private int serviceId;
    private Date date;
    private String time;

    // Getters e setters
    public int getId() {
        return id;
    }

    public void setId(int id) {
        this.id = id;
    }

    public int getServiceId() {
        return serviceId;
    }

    public void setServiceId(int serviceId) {
        this.serviceId = serviceId;
    }

    public Date getDate() {
        return date;
    }

    public void setDate(Date date) {
        this.date = date;
    }

    public String getTime() {
        return time;
    }

    public void setTime(String time) {
        this.time = time;
    }
}
```

**Serviços CRUD**

```java
// ListServicesServlet.java
package com.example.servlet;

import com.example.model.Service;
import com.example.dao.ServiceDao;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.RequestDispatcher;
import java.io.IOException;
import java.util.List;

/**
 * Servlet implementation class ListServicesServlet
 * Handles listing of services.
 */
@WebServlet("/listServices")
public class ListServicesServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            ServiceDao serviceDao = new ServiceDao();
            List<Service> services = serviceDao.getAllServices();
            request.setAttribute("services", services);
            RequestDispatcher dispatcher = request.getRequestDispatcher("listServices.jsp");
            dispatcher.forward(request, response);
        } catch (Exception e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "An error occurred while listing services.");
        }
    }
}
```

```java
// ViewServiceServlet.java
package com.example.servlet;

import com.example.model.Service;
import com.example.dao.ServiceDao;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.RequestDispatcher;
import java.io.IOException;

/**
 * Servlet implementation class ViewServiceServlet
 * Handles viewing of a specific service.
 */
@WebServlet("/viewService")
public class ViewServiceServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            int id = Integer.parseInt(request.getParameter("id"));
            ServiceDao serviceDao = new ServiceDao();
            Service service = serviceDao.getServiceById(id);
            request.setAttribute("service", service);
            RequestDispatcher dispatcher = request.getRequestDispatcher("viewService.jsp");
            dispatcher.forward(request, response);
        } catch (NumberFormatException | NullPointerException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid service ID.");
        } catch (Exception e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "An error occurred while retrieving service details.");
        }
    }
}
```

```java
// AddServiceServlet.java
package com.example.servlet;

import com.example.model.Service;
import com.example.dao.ServiceDao;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

/**
 * Servlet implementation class AddServiceServlet
 * Handles adding of a new service.
 */
@WebServlet("/addService")
public class AddServiceServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            String name = request.getParameter("name");
            String description = request.getParameter("description");
            double price = Double.parseDouble(request.getParameter("price"));

            Service service = new Service();
            service.setName(name);
            service.setDescription(description);
            service.setPrice(price);

            ServiceDao serviceDao = new ServiceDao();
            serviceDao.addService(service);

            response.sendRedirect("listServices");
        } catch (NumberFormatException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid price format.");
        } catch (Exception e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "An error occurred while adding the service.");
        }
    }
}
```

```java
// DeleteServiceServlet.java
package com.example.servlet;

import com.example.dao.ServiceDao;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

/**
 * Servlet implementation class DeleteServiceServlet
 * Handles deleting of a service.
 */
@WebServlet("/deleteService")
public class DeleteServiceServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            int id = Integer.parseInt(request.getParameter("id"));
            ServiceDao serviceDao = new ServiceDao();
            serviceDao.deleteService(id);
            response.sendRedirect("listServices");
        } catch (NumberFormatException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid service ID.");
        } catch (Exception e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "An error occurred while deleting the service.");
        }
    }
}
```

```java
// UpdateServiceServlet.java
package com.example.servlet;

import com.example.model.Service;
import com.example.dao.ServiceDao;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

/**
 * Servlet implementation class UpdateServiceServlet
 * Handles updating of a service.
 */
@WebServlet("/updateService")
public class UpdateServiceServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            int id = Integer.parseInt(request.getParameter("id"));
            String name = request.getParameter("name");
            String description = request.getParameter("description");
            double price = Double.parseDouble(request.getParameter("price"));

            Service service = new Service();
            service.setId(id);
            service.setName(name);
            service.setDescription(description);
            service.setPrice(price);

            ServiceDao serviceDao = new ServiceDao();
            serviceDao.updateService(service);

            response.sendRedirect("listServices");
        } catch (NumberFormatException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid input format.");
        } catch (Exception e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "An error occurred while updating the service.");
        }
    }
}
```

**Sessões CRUD**

```java
// ListSessionsServlet.java
package com.example.servlet;

import com.example.model.Session;
import com.example.dao.SessionDao;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import javax.servlet.RequestDispatcher;
import java.io.IOException;
import java.util.List;

/**
 * Servlet implementation class ListSessionsServlet
 * Handles listing of sessions.
 */
@WebServlet("/listSessions")
public class ListSessionsServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            int serviceId = Integer.parseInt(request.getParameter("serviceId"));
            SessionDao sessionDao = new SessionDao();
            List<Session> sessions = sessionDao.getSessionsByServiceId(serviceId);
            request.setAttribute("sessions", sessions);
            RequestDispatcher dispatcher = request.getRequestDispatcher("listSessions.jsp");
            dispatcher.forward(request, response);
        } catch (NumberFormatException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST,

 "Invalid service ID.");
        } catch (Exception e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "An error occurred while listing sessions.");
        }
    }
}
```

```java
// AddSessionServlet.java
package com.example.servlet;

import com.example.model.Session;
import com.example.dao.SessionDao;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.text.SimpleDateFormat;
import java.util.Date;

/**
 * Servlet implementation class AddSessionServlet
 * Handles adding of a new session.
 */
@WebServlet("/addSession")
public class AddSessionServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            int serviceId = Integer.parseInt(request.getParameter("serviceId"));
            String dateString = request.getParameter("date");
            String time = request.getParameter("time");

            SimpleDateFormat dateFormat = new SimpleDateFormat("yyyy-MM-dd");
            Date date = dateFormat.parse(dateString);

            Session session = new Session();
            session.setServiceId(serviceId);
            session.setDate(date);
            session.setTime(time);

            SessionDao sessionDao = new SessionDao();
            sessionDao.addSession(session);

            response.sendRedirect("viewService?id=" + serviceId);
        } catch (NumberFormatException | java.text.ParseException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid input format.");
        } catch (Exception e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "An error occurred while adding the session.");
        }
    }
}
```

```java
// DeleteSessionServlet.java
package com.example.servlet;

import com.example.dao.SessionDao;
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;

/**
 * Servlet implementation class DeleteSessionServlet
 * Handles deleting of a session.
 */
@WebServlet("/deleteSession")
public class DeleteSessionServlet extends HttpServlet {
    private static final long serialVersionUID = 1L;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            int id = Integer.parseInt(request.getParameter("id"));
            SessionDao sessionDao = new SessionDao();
            sessionDao.deleteSession(id);
            response.sendRedirect("listSessions?serviceId=" + request.getParameter("serviceId"));
        } catch (NumberFormatException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid session ID.");
        } catch (Exception e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "An error occurred while deleting the session.");
        }
    }
}
```

**Páginas JSP**

```jsp
<!-- listServices.jsp -->
<%@ page import="java.util.List" %>
<%@ page import="com.example.model.Service" %>
<!DOCTYPE html>
<html>
<head>
    <title>Lista de Serviços</title>
</head>
<body>
    <h1>Serviços Disponíveis</h1>
    <form action="addService" method="post">
        Nome: <input type="text" name="name"><br>
        Descrição: <input type="text" name="description"><br>
        Preço: <input type="number" step="0.01" name="price"><br>
        <input type="submit" value="Adicionar Serviço">
    </form>
    <table border="1">
        <tr>
            <th>Nome</th>
            <th>Descrição</th>
            <th>Preço</th>
            <th>Ações</th>
        </tr>
        <%
            List<Service> services = (List<Service>) request.getAttribute("services");
            for (Service service : services) {
        %>
        <tr>
            <td><%= service.getName() %></td>
            <td><%= service.getDescription() %></td>
            <td><%= service.getPrice() %></td>
            <td>
                <a href="viewService?id=<%= service.getId() %>">Ver Detalhes</a>
                <a href="deleteService?id=<%= service.getId() %>">Excluir</a>
            </td>
        </tr>
        <% } %>
    </table>
</body>
</html>
```

```jsp
<!-- viewService.jsp -->
<%@ page import="com.example.model.Service" %>
<!DOCTYPE html>
<html>
<head>
    <title>Detalhes do Serviço</title>
</head>
<body>
    <%
        Service service = (Service) request.getAttribute("service");
    %>
    <h1><%= service.getName() %></h1>
    <p><%= service.getDescription() %></p>
    <p>Preço: <%= service.getPrice() %></p>
    <h2>Agendar Sessão</h2>
    <form action="addSession" method="post">
        <input type="hidden" name="serviceId" value="<%= service.getId() %>">
        Data: <input type="date" name="date"><br>
        Hora: <input type="time" name="time"><br>
        <input type="submit" value="Agendar">
    </form>
    <h2>Sessões Agendadas</h2>
    <a href="listSessions?serviceId=<%= service.getId() %>">Ver Sessões</a>
</body>
</html>
```

```jsp
<!-- listSessions.jsp -->
<%@ page import="java.util.List" %>
<%@ page import="com.example.model.Session" %>
<!DOCTYPE html>
<html>
<head>
    <title>Lista de Sessões</title>
</head>
<body>
    <h1>Sessões Agendadas</h1>
    <table border="1">
        <tr>
            <th>Data</th>
            <th>Hora</th>
            <th>Ações</th>
        </tr>
        <%
            List<Session> sessions = (List<Session>) request.getAttribute("sessions");
            for (Session session : sessions) {
        %>
        <tr>
            <td><%= session.getDate() %></td>
            <td><%= session.getTime() %></td>
            <td>
                <a href="deleteSession?id=<%= session.getId() %>&serviceId=<%= session.getServiceId() %>">Excluir</a>
            </td>
        </tr>
        <% } %>
    </table>
</body>
</html>
```

### Parte 3: Integração e Testes

**Integração**
- Certifique-se de que todos os Servlets e JSPs estejam corretamente configurados no `web.xml` ou utilizando anotações.

**Testes**
- Execute o servidor web e teste todas as funcionalidades para garantir que o sistema esteja funcionando como esperado.
- Verifique a renderização das páginas JSP e a exibição dos dados.

### Parte 4: Conclusão

- Disponibilize o código no GitHub.

### Melhorias e Implementações Adicionais

**1. Validação de Dados**

```java
// No modelo Service.java
public void setPrice(double price) {
    if (price < 0) {
        throw new IllegalArgumentException("Price must be a positive number");
    }
    this.price = price;
}
```

**2. Segurança**

```java
// Sanitização no AddServiceServlet.java
String name = StringEscapeUtils.escapeHtml4(request.getParameter("name"));
String description = StringEscapeUtils.escapeHtml4(request.getParameter("description"));
```

**3. Exceções**

```java
// Tratamento de exceções no ViewServiceServlet.java
catch (NumberFormatException | NullPointerException e) {
    e.printStackTrace();
    response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid service ID.");
} catch (Exception e) {
    e.printStackTrace();
    response.sendError(HttpServletResponse.SC_INTERNAL_SERVER_ERROR, "An error occurred while retrieving service details.");
}
```

**4. Experiência do Usuário**

```java
// Feedback ao usuário em listServices.jsp
<% if (request.getAttribute("message") != null) { %>
    <p><%= request.getAttribute("message") %></p>
<% } %>
```

**5. Casos de Teste**

#### 5.1. Testes de Serviços

**Teste de Criação de Serviço**

- **Caso de Teste:** Criar um serviço com dados válidos.
  - **Entradas:** Nome: "Massagem Relaxante", Descrição: "Massagem completa para relaxamento", Preço: 100.00
  - **Resultado Esperado:** Serviço criado com sucesso e listado em `listServices.jsp`.

- **Caso de Teste:** Criar um serviço com preço negativo.
  - **Entradas:** Nome: "Tratamento Facial", Descrição: "Tratamento completo para a pele", Preço: -50.00
  - **Resultado Esperado:** Erro de validação e mensagem de preço inválido.

- **Caso de Teste:** Criar um serviço com campos vazios.
  - **Entradas:** Nome: "", Descrição: "", Preço: 0.00
  - **Resultado Esperado:** Erro de validação e mensagens indicando que os campos não podem ser vazios.

**Teste de Atualização de Serviço**

- **Caso de Teste:** Atualizar um serviço com dados válidos.
  - **Entradas:** ID: 1, Nome: "Massagem Terapêutica", Descrição: "Massagem para alívio de dores", Preço: 120.00
  - **Resultado Esperado:** Serviço atualizado com sucesso e refletido em `listServices.jsp`.

- **Caso de Teste:** Atualizar um serviço inexistente.
  - **Entradas:** ID: 999, Nome: "Serviço Inexistente", Descrição: "Teste de serviço", Preço: 50.00
  - **Resultado Esperado:** Erro de serviço não encontrado.

**Teste de Exclusão de Serviço**

- **Caso de Teste:** Excluir um serviço existente.
  - **Entradas:** ID: 1
  - **Resultado Esperado:** Serviço excluído com sucesso e removido de `listServices.jsp`.

- **Caso de Teste:** Excluir um serviço inexistente.
  - **Entradas:** ID: 999
  - **Resultado Esperado:** Erro de serviço não encontrado.

#### 5.2. Testes de Sessões

**Teste de Agendamento de Sessão**

- **Caso de Teste:** Agendar uma sessão com dados válidos.
  - **Entradas:** ID do Serviço: 1, Data: "2023-12-01", Hora: "14:00"
  - **Resultado Esperado:** Sessão agendada com sucesso e listada em `listSessions.jsp`.

- **Caso de Teste:** Agendar uma sessão para um serviço inexistente.
  - **Entradas:** ID do Serviço: 999, Data: "2023-12-01", Hora: "14:00"
  - **Resultado Esperado:** Erro de serviço não encontrado.

- **Caso de Teste:** Agendar uma sessão com campos vazios.
  - **Entradas:** ID do Serviço: 1, Data: "", Hora: ""
  - **Resultado Esperado:** Erro de validação e mensagens indicando que os campos não podem ser vazios.

**Teste de Exclusão de Sessão**

- **Caso de Teste:** Excluir uma sessão existente.
  - **Entradas:** ID: 1
  - **Resultado Esperado:** Sessão excluída com sucesso e removida de `listSessions.jsp`.

- **Caso de Teste:** Excluir uma sessão inexistente.
  - **Entradas:** ID: 999
  - **Resultado Esperado:** Erro de sessão não encontrada.

#### 5.3. Testes de Segurança

**Teste de Sanitização de Inputs**

- **Caso de Teste:** Inserir código malicioso nos campos de entrada.
  - **Entradas:** Nome: "<script>alert('XSS')</script>", Descrição: "<script>alert('XSS')</script>", Preço: 100.00
  - **Resultado Esperado:** Código malicioso é exibido como texto e não é executado, prevenindo XSS.

**Teste de Validação de Sessão**

- **Caso de Teste:** Acessar páginas restritas sem estar logado.
  - **Entradas:** Acessar diretamente `addSession.jsp` ou `listSessions.jsp` sem fazer login.
  - **Resultado Esperado:** Redirecionamento para a página de login.

#### 5.4. Testes de Experiência do Usuário

**Teste de Feedback ao Usuário**

- **Caso de Teste:** Adicionar um serviço com sucesso.
  - **Entradas:** Nome: "Massagem Relaxante", Descrição: "Massagem completa para relaxamento", Preço: 100.00
  - **Resultado Esperado:** Mensagem de sucesso exibida na página `listServices.jsp`.

- **Caso de Teste:** Falha ao adicionar um serviço devido a erro de validação.
  - **Entradas:** Nome: "", Descrição: "", Preço: -50.00
  - **Resultado Esperado:** Mensagem de erro exibida na página `addService.jsp`.

#### 5.5. Testes de Integração

**Teste de Integração entre Serviços e Sessões**

- **Caso de Teste:** Criar um serviço e agendar uma sessão para este serviço.
  - **Entradas:** 
    - Serviço: Nome: "Massagem Relaxante", Descrição: "Massagem completa para relaxamento", Preço: 100.00
    - Sessão: Data: "2023-12-01", Hora: "14:00"
  - **Resultado Esperado:** Serviço criado e sessão agendada com sucesso, ambos listados corretamente em suas respectivas páginas.

**Teste de Redirecionamento após Operações CRUD**

- **Caso de Teste:** Redirecionamento após adicionar um serviço.
  - **Entradas:** Nome: "Tratamento Facial", Descrição: "Tratamento completo para a pele", Preço: 150.00
  - **Resultado Esperado:** Redirecionamento para `listServices.jsp` com o novo serviço listado.

#### 5.6 Implementação de Testes Automatizados

Esses casos de teste podem ser implementados usando frameworks de teste como JUnit para testes de unidade e Selenium para testes de interface. Aqui estão alguns exemplos de como implementar esses testes em JUnit.

#### Exemplo de Teste com JUnit

```java
import static org.junit.Assert.*;
import org.junit.Test;
import com.example.model.Service;

public class ServiceTest {

    @Test
    public void testServiceCreation() {
        Service service = new Service();
        service.setName("Massagem Relaxante");
        service.setDescription("Massagem completa para relaxamento");
        service.setPrice(100.00);
        
        assertEquals("Massagem Relaxante", service.getName());
        assertEquals("Massagem completa para relaxamento", service.getDescription());
        assertEquals(100.00, service.getPrice(), 0.01);
    }

    @Test(expected = IllegalArgumentException.class)
    public void testInvalidPrice() {
        Service service = new Service();
        service.setPrice(-50.00);
    }
}
```

#### Exemplo de Teste com Selenium

```java
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;
import org.junit.After;
import org.junit.Before;
import org.junit.Test;

public class ServiceSeleniumTest {
    private WebDriver driver;

    @Before
    public void setUp() {
        System.setProperty("webdriver.chrome.driver", "/path/to/chromedriver");
        driver = new ChromeDriver();
    }

    @Test
    public void testAddService() {
        driver.get("http://localhost:8080/addService.jsp");
        
        WebElement nameField = driver.findElement(By.name("name"));
        WebElement descriptionField = driver.findElement(By.name("description"));
        WebElement priceField = driver.findElement(By.name("price"));
        WebElement submitButton = driver.findElement(By.cssSelector("input[type='submit']"));
        
        nameField.sendKeys("Massagem Relaxante");
        descriptionField.sendKeys("Massagem completa para relaxamento");
        priceField.sendKeys("100.00");
        submitButton.click();
        
        // Verificar se o serviço foi adicionado com sucesso
        WebElement successMessage = driver.findElement(By.id("success-message"));
        assertEquals("Serviço adicionado com sucesso!", successMessage.getText());
    }

    @After
    public void tearDown() {
        driver.quit();
    }
}
```

Esses exemplos mostram como estruturar e implementar testes para validar as funcionalidades e condições de borda do sistema.


