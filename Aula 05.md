# Utilizando MySQL com Conector JDBC
---
**Objetivo da Aula:**
Nesta aula, os alunos aprenderão os conceitos fundamentais de bancos de dados relacionais e como conectar uma aplicação Java a um banco de dados MySQL utilizando o conector JDBC. A aula será dividida em três partes: conceitos fundamentais, exercícios de fixação e uma atividade prática que adapta o sistema de gerenciamento de serviços para clínica estética, desenvolvido anteriormente, para utilizar o banco de dados MySQL.

---

### Parte 1: Conceitos Fundamentais e Configuração

#### 1. Conceitos Fundamentais

**1.1. Banco de Dados Relacional**
- **Definição:** Um banco de dados relacional é um tipo de banco de dados que organiza os dados em tabelas, que podem ser relacionadas entre si. Cada tabela é composta por linhas (registros) e colunas (campos).
- **Chaves Primárias e Estrangeiras:**
  - **Chave Primária (Primary Key):** É um campo ou combinação de campos que identificam unicamente cada registro em uma tabela.
  - **Chave Estrangeira (Foreign Key):** É um campo que cria um vínculo entre duas tabelas, referenciando a chave primária de outra tabela.
- **Normalização:** Processo de organização dos dados para reduzir a redundância e melhorar a integridade dos dados.
- **SGBD (Sistema de Gerenciamento de Banco de Dados):** Software que permite criar, gerenciar e manipular bancos de dados. Exemplos incluem MySQL, PostgreSQL, Oracle e SQL Server.

**1.2. SQL (Structured Query Language)**
- **Definição:** SQL é uma linguagem padrão utilizada para gerenciar e manipular bancos de dados relacionais.
- **Comandos SQL Comuns:**
  - **DDL (Data Definition Language):** `CREATE`, `ALTER`, `DROP` - utilizados para definir e modificar a estrutura do banco de dados.
  - **DML (Data Manipulation Language):** `SELECT`, `INSERT`, `UPDATE`, `DELETE` - utilizados para manipular os dados dentro das tabelas.
  - **DCL (Data Control Language):** `GRANT`, `REVOKE` - utilizados para controlar o acesso aos dados.
  - **TCL (Transaction Control Language):** `COMMIT`, `ROLLBACK`, `SAVEPOINT` - utilizados para gerenciar transações no banco de dados.

**1.3. JDBC (Java Database Connectivity)**
- **Definição:** JDBC é uma API Java que permite a comunicação entre uma aplicação Java e um banco de dados. Ele fornece métodos para conectar ao banco de dados, executar consultas SQL e manipular resultados.
- **Componentes Principais:**
  - **DriverManager:** Gerencia um conjunto de drivers de banco de dados. Utilizado para estabelecer a conexão com o banco de dados.
  - **Connection:** Representa a conexão com o banco de dados.
  - **Statement:** Utilizado para executar comandos SQL estáticos.
  - **PreparedStatement:** Utilizado para executar comandos SQL parametrizados, prevenindo ataques de injeção de SQL.
  - **ResultSet:** Representa o conjunto de resultados de uma consulta SQL.

**1.4. Métodos Mais Utilizados do JDBC**

**a) DriverManager**
- **Descrição:** Classe utilizada para gerenciar um conjunto de drivers de banco de dados. Fornece métodos para estabelecer uma conexão com um banco de dados.
- **Métodos Comuns:**
  - `getConnection(String url)`: Estabelece uma conexão com o banco de dados usando a URL fornecida.
  - `getConnection(String url, String user, String password)`: Estabelece uma conexão com o banco de dados usando a URL, nome de usuário e senha fornecidos.

**Exemplo:**
```java
Connection conn = DriverManager.getConnection("jdbc:mysql://localhost:3306/clinicadb", "root", "password");
```

**b) Connection**
- **Descrição:** Representa uma conexão com um banco de dados. Fornece métodos para criar `Statement` e `PreparedStatement`, bem como para gerenciar transações.
- **Métodos Comuns:**
  - `createStatement()`: Cria um objeto `Statement` para enviar instruções SQL ao banco de dados.
  - `prepareStatement(String sql)`: Cria um objeto `PreparedStatement` para enviar instruções SQL parametrizadas ao banco de dados.
  - `close()`: Fecha a conexão com o banco de dados.

**Exemplo:**
```java
Statement stmt = conn.createStatement();
PreparedStatement pstmt = conn.prepareStatement("INSERT INTO services (name, description, price) VALUES (?, ?, ?)");
conn.close();
```

**c) Statement**
- **Descrição:** Utilizado para executar instruções SQL estáticas e retornar resultados. É criado a partir de um objeto `Connection`.
- **Métodos Comuns:**
  - `executeQuery(String sql)`: Executa uma instrução SQL que retorna um conjunto de resultados (`ResultSet`).
  - `executeUpdate(String sql)`: Executa uma instrução SQL que pode ser um `INSERT`, `UPDATE` ou `DELETE`, retornando o número de linhas afetadas.

**Exemplo:**
```java
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM services");
int rowsAffected = stmt.executeUpdate("UPDATE services SET price = 120.00 WHERE id = 1");
stmt.close();
```

**d) PreparedStatement**
- **Descrição:** Utilizado para executar instruções SQL parametrizadas. É criado a partir de um objeto `Connection`.
- **Métodos Comuns:**
  - `setString(int parameterIndex, String value)`: Define um valor do tipo `String` para o parâmetro especificado.
  - `setInt(int parameterIndex, int value)`: Define um valor do tipo `int` para o parâmetro especificado.
  - `setBigDecimal(int parameterIndex, BigDecimal value)`: Define um valor do tipo `BigDecimal` para o parâmetro especificado.
  - `executeQuery()`: Executa a instrução SQL e retorna um conjunto de resultados (`ResultSet`).
  - `executeUpdate()`: Executa a instrução SQL e retorna o número de linhas afetadas.

**Exemplo:**
```java
PreparedStatement pstmt = conn.prepareStatement("INSERT INTO services (name, description, price) VALUES (?, ?, ?)");
pstmt.setString(1, "Massagem Relaxante");
pstmt.setString(2, "Massagem completa para relaxamento");
pstmt.setBigDecimal(3, new BigDecimal("100.00"));
int rowsAffected = pstmt.executeUpdate();
pstmt.close();
```

**e) ResultSet**
- **Descrição:** Representa um conjunto de resultados de uma consulta SQL. Fornece métodos para iterar pelos resultados e recuperar os valores das colunas.
- **Métodos Comuns:**
  - `next()`: Move o cursor para o próximo registro no conjunto de resultados.
  - `getInt(String columnLabel)`: Retorna o valor da coluna especificada como um `int`.
  - `getString(String columnLabel)`: Retorna o valor da coluna especificada como um `String`.
  - `getBigDecimal(String columnLabel)`: Retorna o valor da coluna especificada como um `BigDecimal`.

**Exemplo:**
```java
Statement stmt = conn.createStatement();
ResultSet rs = stmt.executeQuery("SELECT * FROM services");
while (rs.next()) {
    int id = rs.getInt("id");
    String name = rs.getString("name");
    String description = rs.getString("description");
    BigDecimal price = rs.getBigDecimal("price");
    System.out.printf("ID: %d, Nome: %s, Descrição: %s, Preço: %s%n", id, name, description, price);
}
rs.close();
stmt.close();
```

**f) CallableStatement**
- **Descrição:** Utilizado para executar chamadas a procedimentos armazenados no banco de dados. É criado a partir de um objeto `Connection`.
- **Métodos Comuns:**
  - `registerOutParameter(int parameterIndex, int sqlType)`: Registra o tipo de dados SQL do parâmetro de saída.
  - `setString(int parameterIndex, String value)`: Define um valor do tipo `String` para o parâmetro especificado.
  - `execute()`: Executa a chamada ao procedimento armazenado.
  - `getString(int parameterIndex)`: Retorna o valor do parâmetro de saída como um `String`.

**Exemplo:**
```java
CallableStatement cstmt = conn.prepareCall("{call GetServiceName(?, ?)}");
cstmt.setInt(1, 1);
cstmt.registerOutParameter(2, java.sql.Types.VARCHAR);
cstmt.execute();
String serviceName = cstmt.getString(2);
System.out.println("Nome do Serviço: " + serviceName);
cstmt.close();
```

---


#### 2. Configuração do Ambiente

**2.1. Instalação do MySQL**
- **Download e Instalação:** Baixe o instalador do MySQL a partir do site oficial ([MySQL Downloads](https://dev.mysql.com/downloads/)). Siga as instruções de instalação fornecidas pelo instalador.
- **Configuração Inicial:** Durante a instalação, você será solicitado a configurar uma senha para o usuário root. Guarde essa senha para uso posterior.

**2.2. Configuração do Banco de Dados**
- **Criar Banco de Dados e Tabelas:** Utilize o MySQL Workbench ou a linha de comando do MySQL para criar o banco de dados e as tabelas necessárias.

```sql
-- Criação do banco de dados
CREATE DATABASE clinicadb;
USE clinicadb;

-- Criação da tabela services
CREATE TABLE services (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10, 2) NOT NULL
);

-- Criação da tabela sessions
CREATE TABLE sessions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    serviceId INT,
    date DATE,
    time TIME,
    FOREIGN KEY (serviceId) REFERENCES services(id)
);
```

**2.3. Adicionar o Conector JDBC ao Projeto**
- **Download do Conector JDBC:** Baixe o MySQL Connector/J a partir do site oficial ([MySQL Connector/J](https://dev.mysql.com/downloads/connector/j/)).
- **Adicionar ao Projeto:**
  - **Eclipse:** Clique com o botão direito no projeto > Build Path > Configure Build Path > Add External JARs > Selecione o `mysql-connector-java-<version>.jar`.
  - **IntelliJ IDEA:** File > Project Structure > Modules > Dependencies > + > JARs or directories > Selecione o `mysql-connector-java-<version>.jar`.

**2.4. Configuração da Conexão JDBC**
- **Classe de Conexão:**
  - Crie uma classe utilitária para gerenciar a conexão com o banco de dados.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DatabaseConnection {
    private static final String URL = "jdbc:mysql://localhost:3306/clinicadb";
    private static final String USER = "root";
    private static final String PASSWORD = "password";

    public static Connection getConnection() throws SQLException {
        return DriverManager.getConnection(URL, USER, PASSWORD);
    }
}
```

### Parte 2: Exercícios de Fixação

**Exercício 1: Conectar ao Banco de Dados**
- **Objetivo:** Escrever um programa Java que se conecte ao banco de dados MySQL e exiba uma mensagem de sucesso.
- **Passos:**
  - Importar as bibliotecas necessárias.
  - Utilizar a classe `DatabaseConnection` para obter a conexão.
  - Exibir uma mensagem de sucesso.

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class ConnectToDatabase {
    private static final String URL = "jdbc:mysql://localhost:3306/clinicadb";
    private static final String USER = "root";
    private static final String PASSWORD = "password";

    public static void main(String[] args) {
        try (Connection connection = DriverManager.getConnection(URL, USER, PASSWORD)) {
            System.out.println("Conexão com o banco de dados estabelecida com sucesso!");
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

**Exercício 2: Inserir Dados na Tabela `services`**
- **Objetivo:** Escrever um programa Java que insira um novo serviço na tabela `services`.
- **Passos:**
  - Utilizar `DatabaseConnection` para obter a conexão.
  - Criar um `PreparedStatement` com a instrução SQL para inserção.
  - Definir os parâmetros do `PreparedStatement`.
  - Executar a inserção e exibir uma mensagem de sucesso.

```java
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.math.BigDecimal;

public class InsertService {
    public static void main(String[] args) {
        String sql = "INSERT INTO services (name, description, price) VALUES (?, ?, ?)";
        try (Connection connection = DatabaseConnection.getConnection();
             PreparedStatement pstmt = connection.prepareStatement(sql)) {
            pstmt.setString(1, "Massagem Relaxante");
            pstmt.setString(2, "Massagem completa para relaxamento");
            pstmt.setBigDecimal(3, new BigDecimal("100.00"));
            int rows = pstmt.executeUpdate();
            if (rows > 0) {
                System.out.println("Um novo serviço foi inserido com sucesso!");
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

**Exercício 3: Consultar Dados da Tabela `services`**
- **Objetivo:** Escrever um programa Java que recupere e exiba todos os serviços da tabela `services`.
- **Passos:**
  - Utilizar `DatabaseConnection` para obter a conexão.
  - Criar um `Statement` e executar a consulta SQL.
  - Iterar sobre o `ResultSet` e exibir os dados dos serviços.

```java
import java.sql.Connection;
import java.sql.ResultSet;
import java.sql.Statement;
import java.sql.SQLException;
import java.math.BigDecimal;

public class ListServices {
    public static void main(String[] args) {
        String sql = "SELECT * FROM services";
        try (Connection connection = DatabaseConnection.getConnection();
             Statement stmt = connection.createStatement();
             ResultSet rs = stmt.executeQuery(sql)) {
            while (rs.next()) {
                int id = rs.getInt("id");
                String name = rs.getString("name");
                String description = rs.getString("description");
                BigDecimal price = rs.getBigDecimal("price");
                System.out.printf("ID: %d, Nome: %s, Descrição: %s, Preço: %s%n", id, name, description, price);
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

**Exercício 4: Atualizar Dados na Tabela `services`**
- **Objetivo:** Escrever um programa Java que atualize o preço de um serviço na tabela `services`.
- **Passos:**
  - Utilizar `DatabaseConnection` para obter a

 conexão.
  - Criar um `PreparedStatement` com a instrução SQL para atualização.
  - Definir os parâmetros do `PreparedStatement`.
  - Executar a atualização e exibir uma mensagem de sucesso.

```java
import java.sql.Connection;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.math.BigDecimal;

public class UpdateServicePrice {
    public static void main(String[] args) {
        String sql = "UPDATE services SET price = ? WHERE id = ?";
        try (Connection connection = DatabaseConnection.getConnection();
             PreparedStatement pstmt = connection.prepareStatement(sql)) {
            pstmt.setBigDecimal(1, new BigDecimal("120.00"));
            pstmt.setInt(2, 1); // Assume que o serviço com ID 1 existe
            int rows = pstmt.executeUpdate();
            if (rows > 0) {
                System.out.println("O preço do serviço foi atualizado com sucesso!");
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }
}
```

---

### Parte 3: Revisando Conceitos

1. **O que é um banco de dados relacional e quais são suas principais características?**
   - **Resposta Esperada:** Um banco de dados relacional é um tipo de banco de dados que organiza os dados em tabelas, que podem ser relacionadas entre si através de chaves primárias e estrangeiras. Suas principais características incluem integridade referencial, normalização, suporte a transações, e uso de SQL para gerenciamento e manipulação de dados.

2. **Explique a diferença entre os comandos SQL DDL, DML, DCL e TCL, dando exemplos de cada.**
   - **Resposta Esperada:** 
     - **DDL (Data Definition Language):** Comandos que definem a estrutura do banco de dados. Ex: `CREATE TABLE`, `ALTER TABLE`, `DROP TABLE`.
     - **DML (Data Manipulation Language):** Comandos que manipulam os dados dentro das tabelas. Ex: `SELECT`, `INSERT`, `UPDATE`, `DELETE`.
     - **DCL (Data Control Language):** Comandos que controlam o acesso aos dados. Ex: `GRANT`, `REVOKE`.
     - **TCL (Transaction Control Language):** Comandos que gerenciam transações no banco de dados. Ex: `COMMIT`, `ROLLBACK`, `SAVEPOINT`.

3. **O que é JDBC e quais são seus componentes principais?**
   - **Resposta Esperada:** JDBC (Java Database Connectivity) é uma API Java que permite a comunicação entre uma aplicação Java e um banco de dados. Seus componentes principais incluem `DriverManager`, `Connection`, `Statement`, `PreparedStatement`, `ResultSet` e `CallableStatement`.

4. **Quais são as vantagens de usar `PreparedStatement` em vez de `Statement`?**
   - **Resposta Esperada:** 
     - **Segurança:** `PreparedStatement` previne ataques de injeção de SQL ao utilizar parâmetros em vez de concatenar strings.
     - **Eficiência:** Consultas parametrizadas podem ser pré-compiladas pelo banco de dados, resultando em melhor desempenho para execuções repetidas.
     - **Facilidade de Uso:** `PreparedStatement` facilita a definição de parâmetros dinâmicos, melhorando a legibilidade e manutenção do código.

5. **Descreva os passos para estabelecer uma conexão com um banco de dados MySQL utilizando JDBC.**
   - **Resposta Esperada:** 
     - Adicionar o driver JDBC do MySQL ao projeto.
     - Importar as classes necessárias (`java.sql.Connection`, `java.sql.DriverManager`, etc.).
     - Usar `DriverManager.getConnection` para estabelecer a conexão, fornecendo a URL do banco de dados, nome de usuário e senha.
     - Fechar a conexão ao final.

6. **Quais são os benefícios de usar bancos de dados em sistemas Java web?**
   - **Resposta Esperada:** 
     - **Persistência de Dados:** Permite armazenar dados de forma duradoura.
     - **Consistência:** Garantia de integridade dos dados através de transações e chaves.
     - **Escalabilidade:** Capacidade de gerenciar grandes volumes de dados e usuários simultâneos.
     - **Segurança:** Controle de acesso e permissões sobre os dados.
     - **Flexibilidade:** Suporte a consultas complexas e manipulação de dados.

7. **O que é uma transação e como ela é gerenciada em JDBC?**
   - **Resposta Esperada:** Uma transação é uma sequência de operações que são executadas como uma única unidade de trabalho. Em JDBC, transações são gerenciadas através dos métodos `setAutoCommit(false)`, `commit()` e `rollback()` da interface `Connection`. As operações dentro da transação são confirmadas ou revertidas em conjunto para garantir a consistência dos dados.

8. **Explique o conceito de chave primária e chave estrangeira em um banco de dados relacional.**
   - **Resposta Esperada:** 
     - **Chave Primária (Primary Key):** É um campo ou combinação de campos que identificam unicamente cada registro em uma tabela.
     - **Chave Estrangeira (Foreign Key):** É um campo em uma tabela que cria um vínculo com a chave primária de outra tabela, estabelecendo um relacionamento entre elas.

9. **Quais são os padrões de projeto comuns ao trabalhar com JDBC em aplicações Java?**
   - **Resposta Esperada:** 
     - **DAO (Data Access Object):** Padrão que separa a lógica de acesso a dados da lógica de negócio, facilitando a manutenção e testes.
     - **Singleton:** Padrão utilizado para garantir que apenas uma instância de uma classe (como uma classe de conexão) seja criada, controlando o acesso aos recursos compartilhados.
     - **Factory:** Padrão utilizado para criar objetos de conexão de forma centralizada, permitindo mudanças de implementação sem afetar o código cliente.

10. **Quais são os passos para adicionar um conector JDBC ao seu projeto Java em uma IDE como Eclipse ou IntelliJ IDEA?**
    - **Resposta Esperada:**
      - **Eclipse:**
        - Clique com o botão direito no projeto > Build Path > Configure Build Path > Add External JARs > Selecione o `mysql-connector-java-<version>.jar`.
      - **IntelliJ IDEA:**
        - File > Project Structure > Modules > Dependencies > + > JARs or directories > Selecione o `mysql-connector-java-<version>.jar`.

---

### Conclusão

Estas questões de revisão abrangem os conceitos fundamentais, benefícios, vantagens e padrões relacionados ao uso de bancos de dados em sistemas Java web. Elas ajudarão os alunos a consolidar seu entendimento sobre JDBC e a aplicação prática desses conceitos em projetos reais.

### Parte 4: Atividade Prática

**Enunciado:**
Adapte o sistema de gerenciamento de serviços para clínica estética para utilizar conexão com banco de dados MySQL. Utilize os conceitos aprendidos e implemente a persistência dos dados nas tabelas `services` e `sessions`.

**Solução:**

**Configuração do Banco de Dados:**

```sql
CREATE DATABASE clinicadb;
USE clinicadb;

CREATE TABLE services (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    price DECIMAL(10, 2) NOT NULL
);

CREATE TABLE sessions (
    id INT AUTO_INCREMENT PRIMARY KEY,
    serviceId INT,
    date DATE,
    time TIME,
    FOREIGN KEY (serviceId) REFERENCES services(id)
);
```

**Classe de Conexão com o Banco de Dados:**

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public class DatabaseConnection {
    private static final String URL = "jdbc:mysql://localhost:3306/clinicadb";
    private static final String USER = "root";
    private static final String PASSWORD = "password";

    public static Connection getConnection() throws SQLException {
        return DriverManager.getConnection(URL, USER, PASSWORD);
    }
}
```

**Classe ServiceDao:**

```java
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class ServiceDao {

    public void addService(Service service) throws SQLException {
        String sql = "INSERT INTO services (name, description, price) VALUES (?, ?, ?)";
        try (Connection connection = DatabaseConnection.getConnection();
             PreparedStatement pstmt = connection.prepareStatement(sql)) {
            pstmt.setString(1, service.getName());
            pstmt.setString(2, service.getDescription());
            pstmt.setBigDecimal(3, service.getPrice());
            pstmt.executeUpdate();
        }
    }

    public List<Service> getAllServices() throws SQLException {
        List<Service> services = new ArrayList<>();
        String sql = "SELECT * FROM services";
        try (Connection connection = DatabaseConnection.getConnection();
             Statement stmt = connection.createStatement();
             ResultSet rs = stmt.executeQuery(sql)) {
            while (rs.next()) {
                Service service = new Service();
                service.setId(rs.getInt("id"));
                service.setName(rs.getString("name"));
                service.setDescription(rs.getString("description"));
                service.setPrice(rs.getBigDecimal("price"));
                services.add(service);
            }
        }
        return services;
    }

    public Service getServiceById(int id) throws SQLException {
        String sql = "SELECT * FROM services WHERE id = ?";
        try (Connection connection = DatabaseConnection.getConnection();
             PreparedStatement pstmt = connection.prepareStatement(sql)) {
            pstmt.set

Int(1, id);
            try (ResultSet rs = pstmt.executeQuery()) {
                if (rs.next()) {
                    Service service = new Service();
                    service.setId(rs.getInt("id"));
                    service.setName(rs.getString("name"));
                    service.setDescription(rs.getString("description"));
                    service.setPrice(rs.getBigDecimal("price"));
                    return service;
                }
            }
        }
        return null;
    }

    public void updateService(Service service) throws SQLException {
        String sql = "UPDATE services SET name = ?, description = ?, price = ? WHERE id = ?";
        try (Connection connection = DatabaseConnection.getConnection();
             PreparedStatement pstmt = connection.prepareStatement(sql)) {
            pstmt.setString(1, service.getName());
            pstmt.setString(2, service.getDescription());
            pstmt.setBigDecimal(3, service.getPrice());
            pstmt.setInt(4, service.getId());
            pstmt.executeUpdate();
        }
    }

    public void deleteService(int id) throws SQLException {
        String sql = "DELETE FROM services WHERE id = ?";
        try (Connection connection = DatabaseConnection.getConnection();
             PreparedStatement pstmt = connection.prepareStatement(sql)) {
            pstmt.setInt(1, id);
            pstmt.executeUpdate();
        }
    }
}
```

**Classe SessionDao:**

```java
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class SessionDao {

    public void addSession(Session session) throws SQLException {
        String sql = "INSERT INTO sessions (serviceId, date, time) VALUES (?, ?, ?)";
        try (Connection connection = DatabaseConnection.getConnection();
             PreparedStatement pstmt = connection.prepareStatement(sql)) {
            pstmt.setInt(1, session.getServiceId());
            pstmt.setDate(2, new java.sql.Date(session.getDate().getTime()));
            pstmt.setTime(3, java.sql.Time.valueOf(session.getTime()));
            pstmt.executeUpdate();
        }
    }

    public List<Session> getSessionsByServiceId(int serviceId) throws SQLException {
        List<Session> sessions = new ArrayList<>();
        String sql = "SELECT * FROM sessions WHERE serviceId = ?";
        try (Connection connection = DatabaseConnection.getConnection();
             PreparedStatement pstmt = connection.prepareStatement(sql)) {
            pstmt.setInt(1, serviceId);
            try (ResultSet rs = pstmt.executeQuery()) {
                while (rs.next()) {
                    Session session = new Session();
                    session.setId(rs.getInt("id"));
                    session.setServiceId(rs.getInt("serviceId"));
                    session.setDate(rs.getDate("date"));
                    session.setTime(rs.getTime("time").toString());
                    sessions.add(session);
                }
            }
        }
        return sessions;
    }

    public void deleteSession(int id) throws SQLException {
        String sql = "DELETE FROM sessions WHERE id = ?";
        try (Connection connection = DatabaseConnection.getConnection();
             PreparedStatement pstmt = connection.prepareStatement(sql)) {
            pstmt.setInt(1, id);
            pstmt.executeUpdate();
        }
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
import java.sql.SQLException;
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
        } catch (SQLException e) {
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
import java.sql.SQLException;

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
        } catch (NumberFormatException | SQLException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid service ID.");
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
import java.math.BigDecimal;
import java.sql.SQLException;

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
            BigDecimal price = new BigDecimal(request.getParameter("price"));

            Service service = new Service();
            service.setName(name);
            service.setDescription(description);
            service.setPrice(price);

            ServiceDao serviceDao = new ServiceDao();
            serviceDao.addService(service);

            response.sendRedirect("listServices");
        } catch (NumberFormatException | SQLException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid input format.");
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
import java.sql.SQLException;

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
        } catch (NumberFormatException | SQLException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid service ID.");
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
import java.math.BigDecimal;
import java.sql.SQLException;

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
            BigDecimal price = new BigDecimal(request.getParameter("price"));

            Service service = new Service();
            service.setId(id);
            service.setName(name);
            service.setDescription(description);
            service.setPrice(price);

            ServiceDao serviceDao = new ServiceDao();
            serviceDao.updateService(service);

            response.sendRedirect("listServices");
        } catch (NumberFormatException | SQLException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid input format.");
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
import java.sql.SQLException;
import java.util.List;

/**
 * Servlet implementation class ListSessionsServlet
 * Handles listing of sessions.
 */
@WebServlet("/listSessions")
public class ListSessionsServlet extends HttpServlet {
    private static final long serialVersionUID = 1L

;

    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        try {
            int serviceId = Integer.parseInt(request.getParameter("serviceId"));
            SessionDao sessionDao = new SessionDao();
            List<Session> sessions = sessionDao.getSessionsByServiceId(serviceId);
            request.setAttribute("sessions", sessions);
            RequestDispatcher dispatcher = request.getRequestDispatcher("listSessions.jsp");
            dispatcher.forward(request, response);
        } catch (NumberFormatException | SQLException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid service ID.");
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
import java.sql.Date;
import java.sql.SQLException;

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
            Date date = Date.valueOf(request.getParameter("date"));
            String time = request.getParameter("time");

            Session session = new Session();
            session.setServiceId(serviceId);
            session.setDate(date);
            session.setTime(time);

            SessionDao sessionDao = new SessionDao();
            sessionDao.addSession(session);

            response.sendRedirect("viewService?id=" + serviceId);
        } catch (NumberFormatException | SQLException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid input format.");
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
import java.sql.SQLException;

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
        } catch (NumberFormatException | SQLException e) {
            e.printStackTrace();
            response.sendError(HttpServletResponse.SC_BAD_REQUEST, "Invalid session ID.");
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

---
