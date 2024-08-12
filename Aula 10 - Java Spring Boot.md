# Aula 10 - Java Spring Boot

[Top 10 backend frameworks in 2024](https://www.turing.com/resources/backend-frameworks#top-10-backend-frameworks-in-2024)


**Ambiente**  
*Eclipse IDE for Enterprise Java and Web Developers*   
*Version: 2024-06 (4.32.0)*   
*Build id: 20240606-1231*   
*MySQL 8.0.33*

---

Este tutorial abrange todos os aspectos essenciais do desenvolvimento de uma aplicação web completa, utilizando o Spring Framework e aplicando boas práticas de design e segurança. O objetivo é desenvolver um sistema web completo utilizando Java, Spring Framework, MySQL, Tomcat e Eclipse, aplicando o padrão MVC e incorporando funcionalidades como cadastro de usuários, agendamentos, login, e gerenciamento de procedimentos estéticos.


O **Spring Framework** é um dos frameworks mais populares e poderosos no ecossistema Java, amplamente adotado para o desenvolvimento de aplicações empresariais robustas e escaláveis. Introduzido em 2002, o Spring nasceu com o objetivo de simplificar o desenvolvimento de aplicações Java, oferecendo uma alternativa leve e modular à complexidade do Java Enterprise Edition (Java EE). Desde então, evoluiu para se tornar uma plataforma abrangente que suporta uma ampla gama de padrões de arquitetura e boas práticas de desenvolvimento, com forte foco na modularidade, injeção de dependência e orientação a aspectos.

### **Principais Conceitos e Filosofias do Spring Framework**

1. **Inversão de Controle (IoC) e Injeção de Dependência (DI)**:
   - **Inversão de Controle (IoC)** é um princípio onde o controle do fluxo de uma aplicação é invertido; em vez de o código da aplicação controlar diretamente a execução e a criação de objetos, o controle é delegado ao framework. 
   - **Injeção de Dependência (DI)**, um aspecto do IoC, permite que as dependências de um objeto (como serviços ou componentes) sejam fornecidas externamente em vez de o próprio objeto ser responsável por criá-las. Isso promove um design mais modular e testável. No Spring, essa injeção é geralmente feita por meio de configurações de XML ou, mais frequentemente em versões modernas, por meio de anotações.

2. **Programação Orientada a Aspectos (AOP)**:
   - **AOP** permite a separação das preocupações transversais (como logging, segurança, transações, etc.) da lógica de negócios principal. Isso é alcançado através da aplicação de "aspectos" que podem ser aplicados em diferentes pontos de execução (join points) da aplicação. O Spring Framework integra AOP de forma transparente, permitindo que essas preocupações sejam tratadas de maneira modular e reutilizável.

3. **Modularidade e Flexibilidade**:
   - O Spring é altamente modular, composto por uma série de projetos e módulos que podem ser usados independentemente ou em conjunto. Os principais módulos incluem:
     - **Spring Core**: O núcleo do framework, que inclui IoC e DI.
     - **Spring AOP**: Suporte para programação orientada a aspectos.
     - **Spring MVC**: Um framework para construir aplicações web seguindo o padrão Model-View-Controller.
     - **Spring Data**: Simplifica o acesso a bancos de dados, ORM e NoSQL.
     - **Spring Security**: Framework de segurança para autenticação e autorização.
     - **Spring Boot**: Ferramenta que facilita a configuração e o desenvolvimento de aplicações Spring, fornecendo configurações automáticas e servidores embutidos.

4. **Suporte a Padrões de Arquitetura**:
   - O Spring Framework suporta uma variedade de padrões de arquitetura, incluindo MVC, RESTful web services, e microservices. Essa flexibilidade torna o Spring uma escolha ideal para diferentes tipos de aplicações, desde simples serviços web até sistemas empresariais distribuídos.

5. **Ecosistema e Comunidade**:
   - O Spring é apoiado por uma vasta comunidade de desenvolvedores, que contribuem para a sua evolução contínua. Além disso, a Pivotal (agora parte da VMware) e outros mantenedores fornecem suporte comercial e atualizações regulares.

### **Por que Escolher o Spring Framework?**

O Spring Framework é escolhido por desenvolvedores e empresas devido à sua robustez, flexibilidade, e por facilitar a adoção de boas práticas de desenvolvimento. Ele promove um design limpo e modular, permite a fácil integração com outras tecnologias e frameworks, e é altamente configurável, permitindo que os desenvolvedores ajustem e personalizem suas aplicações de acordo com as necessidades específicas. Além disso, com o advento do Spring Boot, o desenvolvimento de aplicações Spring se tornou ainda mais ágil, permitindo que os desenvolvedores criem, testem e implementem aplicações prontas para produção com um mínimo de configuração manual.

Em resumo, o Spring Framework oferece um ambiente completo para o desenvolvimento de aplicações empresariais em Java, combinando simplicidade, modularidade, e uma vasta gama de funcionalidades que cobrem praticamente todas as necessidades de uma aplicação moderna.


### **Arquitetura de Software MVC e Estrutura do Projeto**

O padrão **Model-View-Controller (MVC)** é uma das arquiteturas de software mais populares e amplamente adotadas no desenvolvimento de aplicações, especialmente em ambientes web. Ele separa a aplicação em três componentes principais, cada um com responsabilidades bem definidas: **Model**, **View** e **Controller**. Essa separação de preocupações facilita a manutenção, o desenvolvimento colaborativo, e a escalabilidade da aplicação.

#### **Por que usar MVC?**

O principal objetivo do MVC é desacoplar as partes da aplicação para que possam ser desenvolvidas, testadas e mantidas de forma independente. Isso traz vários benefícios:

- **Facilita a Manutenção**: Cada componente pode ser alterado ou atualizado sem impactar diretamente os outros. Por exemplo, você pode modificar a interface de usuário (View) sem alterar a lógica de negócios (Model).
- **Promove a Reutilização de Código**: A lógica de negócios encapsulada no Model pode ser reutilizada por diferentes partes da aplicação ou até mesmo por outras aplicações.
- **Facilita o Teste e a Depuração**: Separar as responsabilidades em diferentes camadas torna mais fácil isolar problemas e realizar testes unitários de cada componente.
- **Suporte ao Desenvolvimento Colaborativo**: Desenvolvedores podem trabalhar simultaneamente em diferentes componentes da aplicação, como frontend e backend, sem interferências diretas.

#### **Componentes do MVC**

##### **1. Model (Modelo)**

**Definição:**  
O **Model** é a camada que representa os dados da aplicação e a lógica de negócios. Em uma aplicação Java, os Models são frequentemente mapeados para as tabelas de um banco de dados, utilizando tecnologias como JPA (Java Persistence API).

**Funções Principais:**

- **Representação de Dados**: O Model encapsula os dados da aplicação em objetos que correspondem às entidades de negócio. Por exemplo, em uma clínica de estética, você teria Models para `User` (Usuário), `Professional` (Profissional), `Procedure` (Procedimento), e `Appointment` (Agendamento).
  
- **Interação com o Banco de Dados**: O Model é responsável por persistir e recuperar os dados do banco de dados. Isso inclui operações de criação, leitura, atualização e exclusão (CRUD). Com o uso de JPA e Spring Data JPA, a interação com o banco de dados se torna mais simplificada, permitindo que os desenvolvedores manipulem dados sem a necessidade de escrever SQL diretamente.

- **Regras de Negócio**: Além de gerenciar dados, o Model também pode incluir a lógica de negócios. Por exemplo, um Model pode garantir que um procedimento estético só possa ser agendado se o profissional estiver disponível na data e hora solicitadas.

**Exemplo Prático:**  
No sistema de agendamento de uma clínica de estética, o Model `User` representa um cliente da clínica:

```java
@Entity
public class User {
   @Id
   @GeneratedValue(strategy = GenerationType.IDENTITY)
   private Long id;
   private String name;
   private String email;
   private String password;

   @OneToMany(mappedBy = "user")
   private List<Appointment> appointments;

   // Getters e Setters
}
```

##### **2. View (Visão)**

**Definição:**  
A **View** é a camada responsável pela apresentação dos dados ao usuário. Ela define como a interface de usuário (UI) será exibida e como os dados serão renderizados para o usuário final.

**Funções Principais:**

- **Renderização de Interfaces de Usuário**: A View transforma os dados recebidos do Controller em uma interface visual. Em aplicações web Java, essa interface é normalmente composta por páginas HTML geradas por motores de templates como Thymeleaf, JSP, ou outras tecnologias frontend.
  
- **Interação com o Usuário**: A View captura a entrada do usuário, como formulários preenchidos, e os envia para o Controller processar. Ela também é responsável por exibir mensagens e feedback ao usuário, como confirmações de ações ou erros de validação.

- **Layout e Estilo**: Embora a View seja responsável pela estrutura e conteúdo das páginas, o layout e estilo visual são geralmente geridos por tecnologias complementares como CSS (Cascading Style Sheets) e frameworks de design como Bootstrap.

**Exemplo Prático:**  
A página de agendamento de um procedimento estético pode ser uma View que renderiza um formulário para o usuário selecionar o profissional, procedimento, data e hora:

```html
<!DOCTYPE html>
<html xmlns:th="http://www.thymeleaf.org">
<head>
   <title>Agendar Procedimento</title>
</head>
<body>
   <h2>Agendar Novo Procedimento</h2>
   <form th:action="@{/schedule}" th:object="${appointment}" method="post">
       <div>
           <label>Profissional: </label>
           <select th:field="*{professional}">
               <option th:each="professional : ${professionals}" th:value="${professional.id}" th:text="${professional.name}"></option>
           </select>
       </div>
       <div>
           <label>Procedimento: </label>
           <select th:field="*{procedure}">
               <option th:each="procedure : ${procedures}" th:value="${procedure.id}" th:text="${procedure.name}"></option>
           </select>
       </div>
       <div>
           <label>Data e Hora: </label>
           <input type="datetime-local" th:field="*{appointmentTime}" />
       </div>
       <div>
           <input type="submit" value="Agendar" />
       </div>
   </form>
</body>
</html>
```

[Documentação Thymeleaf](https://www.thymeleaf.org)


##### **3. Controller (Controlador)**

**Definição:**  
O **Controller** atua como intermediário entre o Model e a View. Ele é responsável por processar as requisições HTTP enviadas pelo usuário, interagir com o Model para manipulação dos dados, e selecionar a View apropriada para apresentar o resultado ao usuário.

**Funções Principais:**

- **Recepção de Requisições**: O Controller recebe as requisições feitas pelo usuário, como a submissão de um formulário ou o clique em um link. Ele é responsável por entender o que o usuário deseja fazer.
  
- **Interação com o Model**: O Controller consulta ou atualiza os dados do Model conforme necessário. Por exemplo, ao receber uma requisição para agendar um procedimento, o Controller valida a disponibilidade do profissional e salva o agendamento no banco de dados.
  
- **Seleção da View**: Após processar a requisição, o Controller escolhe qual View será renderizada. Ele também passa os dados necessários para essa View. No Spring, o retorno do método do Controller pode ser o nome da View a ser renderizada.

**Exemplo Prático:**  
Um Controller para gerenciar agendamentos pode ter métodos para exibir o formulário de agendamento, processar a submissão desse formulário, e listar os agendamentos realizados:

```java
@Controller
public class AppointmentController {

   @Autowired
   private AppointmentService appointmentService;

   @GetMapping("/schedule")
   public String showScheduleForm(Model model) {
       model.addAttribute("appointment", new Appointment());
       model.addAttribute("professionals", appointmentService.findAllProfessionals());
       model.addAttribute("procedures", appointmentService.findAllProcedures());
       return "schedule";
   }

   @PostMapping("/schedule")
   public String scheduleAppointment(@ModelAttribute("appointment") Appointment appointment) {
       appointmentService.saveAppointment(appointment);
       return "redirect:/appointments";
   }

   @GetMapping("/appointments")
   public String viewAppointments(Model model) {
       model.addAttribute("appointments", appointmentService.findAllAppointments());
       return "appointments";
   }
}
```

---
## Prática

### **Parte 1: Configuração do Projeto**

**Configuração do Projeto no Eclipse**:
   - Vamos configurar um projeto Spring Boot no Eclipse, com as dependências necessárias para desenvolver o sistema.

### Passo a Passo para Instalar o Spring Tool Suite 4 (STS 4) no Eclipse

A instalação do **Spring Tool Suite 4 (STS 4)** no Eclipse é um processo simples e direto, realizado através do Eclipse Marketplace. A seguir, estão os passos detalhados para a instalação:

#### **1. Abrir o Eclipse IDE**

- **Inicie o Eclipse IDE**: Certifique-se de que o Eclipse está totalmente carregado.

#### **2. Acessar o Eclipse Marketplace**

- **Acessar o Marketplace**:
  - No menu superior, clique em `Help`.
  - No menu suspenso, selecione `Eclipse Marketplace...`.

#### **3. Buscar o Spring Tool Suite 4**

- **Pesquisar por Spring Tools 4**:
  - Na barra de pesquisa do Eclipse Marketplace, digite **"Spring Tools 4"**.
  - Clique em `Go` ou pressione `Enter`.


#### **4. Instalar o Spring Tool Suite 4**

- **Selecionar o Plugin**:
  - Nos resultados da pesquisa, localize o **Spring Tools 4 (aka Spring Tool Suite 4)**.
  - Clique no botão `Install` ao lado do plugin.

- **Seguir as Instruções de Instalação**:
  - O Eclipse começará a instalar o plugin. Durante o processo, você pode ser solicitado a selecionar os componentes específicos do Spring Tools que deseja instalar. Por padrão, todos os componentes necessários estão pré-selecionados.
  - Revise e aceite os termos de licença e, em seguida, clique em `Finish`.

#### **5. Reiniciar o Eclipse**

- **Reiniciar para Concluir a Instalação**:
  - Após a instalação ser concluída, o Eclipse solicitará que você reinicie o IDE para que as mudanças entrem em vigor.
  - Clique em `Restart Now` para reiniciar o Eclipse.


### **6. Verificar a Instalação**

- **Confirmar a Instalação**:
  - Após a reinicialização, você pode verificar se o Spring Tools 4 foi instalado corretamente indo em `Help > Eclipse Marketplace...` e selecionando a aba `Installed`.
  - O **Spring Tools 4** deve estar listado entre os plugins instalados.

#### **7. Começar a Usar o Spring Tools 4**

- **Criar um Projeto Spring Boot**:
  - Agora que o STS 4 está instalado, você pode criar um novo projeto Spring Boot. Vá para `File > New > Spring Starter Project` e siga os prompts para configurar seu projeto.


### **Criar um Novo Projeto Spring Boot**:


1. **Criar um Novo Projeto Spring Boot**:
   - Abra o Eclipse e crie um projeto Spring Boot utilizando o Spring Starter Project, com as seguintes dependências:
     - `Spring Web`
     - `Spring Data JPA`
     - `Thymeleaf`
     - `Spring Security`
     - `MySQL Driver`
   - Nome do projeto: `ClinicaEstetica`.

2. **Configuração do Banco de Dados MySQL**:
   - Crie um banco de dados no MySQL chamado `clinica_estetica`.
   - Configure o arquivo `application.properties` para conectar-se ao banco de dados MySQL.

   ```properties
   spring.datasource.url=jdbc:mysql://localhost:3306/clinica_estetica
   spring.datasource.username=web
   spring.datasource.password=123
   spring.datasource.driver-class-name=com.mysql.cj.jdbc.Driver
   spring.jpa.hibernate.ddl-auto=update
   spring.jpa.show-sql=true
   spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.MySQL8Dialect
   ```

### **Parte 2: Modelagem do Sistema - Usuários, Profissionais, Procedimentos e Agendamentos**

#### **Teoria: Modelagem de Dados**

1. **Entidades e Relacionamentos**:
   - **Usuários**: Representa os clientes da clínica, com informações de login e dados pessoais.
   - **Profissionais**: Funcionários da clínica que realizam os procedimentos.
   - **Procedimentos**: Serviços oferecidos pela clínica, como limpeza de pele, massagem, etc.
   - **Agendamentos**: Registra os horários e procedimentos marcados pelos usuários com os profissionais.

2. **Relacionamentos**:
   - Um **Usuário** pode ter vários **Agendamentos**.
   - Um **Profissional** pode realizar vários **Agendamentos**.
   - Um **Procedimento** pode ser agendado várias vezes.

#### **Prática: Criação dos Models**

1. **Model `User`**:

   ```java
   package com.example.clinica.model;

   import javax.persistence.*;
   import java.util.List;

   @Entity
   public class User {

       @Id
       @GeneratedValue(strategy = GenerationType.IDENTITY)
       private Long id;

       private String name;
       private String email;
       private String password;

       @OneToMany(mappedBy = "user")
       private List<Appointment> appointments;

       // Getters and Setters
   }
   ```

2. **Model `Professional`**:

   ```java
   package com.example.clinica.model;

   import javax.persistence.*;
   import java.util.List;

   @Entity
   public class Professional {

       @Id
       @GeneratedValue(strategy = GenerationType.IDENTITY)
       private Long id;

       private String name;
       private String specialty;

       @OneToMany(mappedBy = "professional")
       private List<Appointment> appointments;

       // Getters and Setters
   }
   ```

3. **Model `Procedure`**:

   ```java
   package com.example.clinica.model;

   import javax.persistence.*;
   import java.util.List;

   @Entity
   public class Procedure {

       @Id
       @GeneratedValue(strategy = GenerationType.IDENTITY)
       private Long id;

       private String name;
       private String description;

       @OneToMany(mappedBy = "procedure")
       private List<Appointment> appointments;

       // Getters and Setters
   }
   ```

4. **Model `Appointment`**:

   ```java
   package com.example.clinica.model;

   import javax.persistence.*;
   import java.time.LocalDateTime;

   @Entity
   public class Appointment {

       @Id
       @GeneratedValue(strategy = GenerationType.IDENTITY)
       private Long id;

       @ManyToOne
       @JoinColumn(name = "user_id")
       private User user;

       @ManyToOne
       @JoinColumn(name = "professional_id")
       private Professional professional;

       @ManyToOne
       @JoinColumn(name = "procedure_id")
       private Procedure procedure;

       private LocalDateTime appointmentTime;

       // Getters and Setters
   }
   ```

### **Parte 3: Repositórios e Serviços - Operações CRUD**

#### **Teoria: Repositórios e Lógica de Negócio**

1. **Repositórios**:
   - Interfaces que estendem `JpaRepository`, permitindo a execução de operações CRUD sobre as entidades de forma simples e eficiente.

2. **Serviços**:
   - Camada intermediária que encapsula a lógica de negócio e fornece métodos que serão utilizados pelos controladores.

#### **Prática: Criação dos Repositórios e Serviços**

1. **Repositório `UserRepository`**:

   ```java
   package com.example.clinica.repository;

   import com.example.clinica.model.User;
   import org.springframework.data.jpa.repository.JpaRepository;

   public interface UserRepository extends JpaRepository<User, Long> {
       User findByEmail(String email);
   }
   ```

2. **Repositório `ProfessionalRepository`**:

   ```java
   package com.example.clinica.repository;

   import com.example.clinica.model.Professional;
   import org.springframework.data.jpa.repository.JpaRepository;

   public interface ProfessionalRepository extends JpaRepository<Professional, Long> {
   }
   ```

3. **Repositório `ProcedureRepository`**:

   ```java
   package com.example.clinica.repository;

   import com.example.clinica.model.Procedure;
   import org.springframework.data.jpa.repository.JpaRepository;

   public interface ProcedureRepository extends JpaRepository<Procedure, Long> {
   }
   ```

4. **Repositório `AppointmentRepository`**:

   ```java
   package com.example.clinica.repository;

   import com.example.clinica.model.Appointment;
   import org.springframework.data.jpa.repository.JpaRepository;

   public interface AppointmentRepository extends JpaRepository<Appointment, Long> {
   }
   ```

5. **Serviço `UserService`**:

   ```java
   package com.example.clinica.service;

   import com.example.clinica.model.User;
   import com.example.clinica.repository.UserRepository;
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.stereotype.Service;

   @Service
   public class UserService {

       @Autowired
       private UserRepository userRepository;

       public User findByEmail(String email) {
           return userRepository.findByEmail(email);
       }

       public void saveUser(User user) {
           userRepository.save(user);
       }
   }
   ```

6. **Serviço `AppointmentService`**:

   ```java
   package com.example.clinica.service;

   import com.example.clinica.model.Appointment;
   import com.example.clinica.repository.AppointmentRepository;
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.stereotype.Service;

   import java.util.List;

   @Service
   public class AppointmentService {

       @Autowired
       private AppointmentRepository appointmentRepository;

       public List<Appointment> findAllAppointments() {
           return appointmentRepository.findAll();
       }

       public void saveAppointment(Appointment appointment) {
           appointmentRepository.save(appointment);
       }
   }
   ```

### **Parte 4: Controladores e Interface Web com Thymeleaf**

#### **Teoria: Controladores e Views**

1. **Controladores**:
   - Os controladores Spring, anotados com `@Controller`, gerenciam o fluxo da aplicação e são responsáveis por mapear as requisições HTTP para os métodos apropriados.

2. **Views com Thymeleaf**:
   - **Thymeleaf** permite criar interfaces de usuário dinâmicas usando HTML. É ideal para renderizar páginas que interagem diretamente com os dados manipulados pelos controladores.

#### **Prática: Criação dos Controladores e Páginas Web**

1. **Controlador `UserController`**:

   ```java
   package com.example.clinica.controller;

   import com.example.clinica.model.User;
   import com.example.clinica.service.UserService;
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.stereotype.Controller;
   import org.springframework.ui.Model;
   import org.springframework.web.bind.annotation.GetMapping;
   import org.springframework.web.bind.annotation.ModelAttribute;
   import org.springframework.web.bind.annotation.PostMapping;

   @Controller
   public class UserController {

       @Autowired
       private UserService userService;

       @GetMapping("/register")
       public String showRegistrationForm(Model model) {
           User user = new User();
           model.addAttribute("user", user);
           return "register";
       }

       @PostMapping("/register")
       public String registerUser(@ModelAttribute("user") User user) {
           userService.saveUser(user);
           return "redirect:/login";
       }

       @GetMapping("/login")
       public String showLoginForm() {
           return "login";
       }
   }
   ```

2. **Controlador `AppointmentController`**:

   ```java
   package com.example.clinica.controller;

   import com.example.clinica.model.Appointment;
   import com.example.clinica.model.Professional;
   import com.example.clinica.model.Procedure;
   import com.example.clinica.service.AppointmentService;
   import com.example.clinica.service.ProfessionalService;
   import com.example.clinica.service.ProcedureService;
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.stereotype.Controller;
   import org.springframework.ui.Model;
   import org.springframework.web.bind.annotation.GetMapping;
   import org.springframework.web.bind.annotation.ModelAttribute;
   import org.springframework.web.bind.annotation.PostMapping;

   import java.util.List;

   @Controller
   public class AppointmentController {

       @Autowired
       private AppointmentService appointmentService;

       @Autowired
       private ProfessionalService professionalService;

       @Autowired
       private ProcedureService procedureService;

       @GetMapping("/appointments")
       public String viewAppointments(Model model) {
           List<Appointment> appointments = appointmentService.findAllAppointments();
           model.addAttribute("appointments", appointments);
           return "appointments";
       }

       @GetMapping("/schedule")
       public String showScheduleForm(Model model) {
           Appointment appointment = new Appointment();
           List<Professional> professionals = professionalService.findAll();
           List<Procedure> procedures = procedureService.findAll();
           model.addAttribute("appointment", appointment);
           model.addAttribute("professionals", professionals);
           model.addAttribute("procedures", procedures);
           return "schedule";
       }

       @PostMapping("/schedule")
       public String scheduleAppointment(@ModelAttribute("appointment") Appointment appointment) {
           appointmentService.saveAppointment(appointment);
           return "redirect:/appointments";
       }
   }
   ```

3. **Páginas Web com Thymeleaf**:

   - **`register.html`**: Página de registro de usuário.

     ```html
     <!DOCTYPE html>
     <html xmlns:th="http://www.thymeleaf.org">
     <head>
         <title>Register</title>
     </head>
     <body>
         <h2>Register New User</h2>
         <form th:action="@{/register}" th:object="${user}" method="post">
             <div>
                 <label>Name: </label>
                 <input type="text" th:field="*{name}" />
             </div>
             <div>
                 <label>Email: </label>
                 <input type="email" th:field="*{email}" />
             </div>
             <div>
                 <label>Password: </label>
                 <input type="password" th:field="*{password}" />
             </div>
             <div>
                 <input type="submit" value="Register" />
             </div>
         </form>
     </body>
     </html>
     ```

   - **`login.html`**: Página de login de usuário.

     ```html
     <!DOCTYPE html>
     <html xmlns:th="http://www.thymeleaf.org">
     <head>
         <title>Login</title>
     </head>
     <body>
         <h2>Login</h2>
         <form action="/login" method="post">
             <div>
                 <label>Email: </label>
                 <input type="email" name="email" />
             </div>
             <div>
                 <label>Password: </label>
                 <input type="password" name="password" />
             </div>
             <div>
                 <input type="submit" value="Login" />
             </div>
         </form>
     </body>
     </html>
     ```

   - **`schedule.html`**: Página de agendamento.

     ```html
     <!DOCTYPE html>
     <html xmlns:th="http://www.thymeleaf.org">
     <head>
         <title>Schedule Appointment</title>
     </head>
     <body>
         <h2>Schedule New Appointment</h2>
         <form th:action="@{/schedule}" th:object="${appointment}" method="post">
             <div>
                 <label>Professional: </label>
                 <select th:field="*{professional}" th:object="${professionals}">
                     <option th:each="professional : ${professionals}" th:value="${professional}" th:text="${professional.name}"></option>
                 </select>
             </div>
             <div>
                 <label>Procedure: </label>
                 <select th:field="*{procedure}" th:object="${procedures}">
                     <option th:each="procedure : ${procedures}" th:value="${procedure}" th:text="${procedure.name}"></option>
                 </select>
             </div>
             <div>
                 <label>Date and Time: </label>
                 <input type="datetime-local" th:field="*{appointmentTime}" />
             </div>
             <div>
                 <input type="submit" value="Schedule" />
             </div>
         </form>
     </body>
     </html>
     ```

   - **`appointments.html`**: Página de listagem de agendamentos.

     ```html
     <!DOCTYPE html>
     <html xmlns:th="http://www.thymeleaf.org">
     <head>
         <title>Appointments</title>
     </head>
     <body>
         <h2>All Appointments</h2>
         <table border="1">
             <tr>
                 <th>User</th>
                 <th>Professional</th>
                 <th>Procedure</th>
                 <th>Date and Time</th>
             </tr>
             <tr th:each="appointment : ${appointments}">
                 <td th:text="${appointment.user.name}"></td>
                 <td th:text="${appointment.professional.name}"></td>
                 <td th:text="${appointment.procedure.name}"></td>
                 <td th:text="${appointment.appointmentTime}"></td>
             </tr>
         </table>
     </body>
     </html>
     ```

### **Parte 5: Implementação de Autenticação com Spring Security**

#### **Teoria: Segurança em Aplicações Web**

1. **Spring Security**:
   - Um framework de segurança poderoso e personalizável para proteger aplicações web. Ele facilita a implementação de autenticação (login) e autorização (controle de acesso) em aplicações Spring.

2. **Autenticação e Autorização**:
   - **Autenticação**: Processo de verificar a identidade do usuário.
   - **Autorização**: Processo de determinar se o usuário autenticado tem permissão para acessar recursos específicos.

#### **Prática: Configuração do Spring Security**

1. **Configurar Spring Security**:
   - Crie uma classe de configuração de segurança para definir as regras de autenticação.

   ```java
   package com.example.clinica.config;

   import org.springframework.context.annotation.Bean;
   import org.springframework.context.annotation.Configuration;
   import org.springframework.security.config.annotation.web.builders.HttpSecurity;
   import org.springframework.security.core.userdetails.UserDetailsService;
   import org.springframework.security.core.userdetails.UsernameNotFoundException;
   import org.springframework.security.crypto.bcrypt.BCryptPasswordEncoder;
   import org.springframework.security.web.SecurityFilterChain;

   import com.example.clinica.model.User;
   import com.example.clinica.repository.UserRepository;

   @Configuration
   public class SecurityConfig {

       @Bean
       public SecurityFilterChain securityFilterChain(HttpSecurity http) throws Exception {
           http
               .authorizeRequests()
                   .antMatchers("/register", "/login").permitAll()
                   .anyRequest().authenticated()
                   .and()
               .formLogin()
                   .loginPage("/login")
                   .defaultSuccessUrl("/appointments", true)
                   .permitAll()
                   .and()
               .logout()
                   .permitAll();

           return http.build();
       }

       @Bean
       public BCryptPasswordEncoder passwordEncoder() {
           return new BCryptPasswordEncoder();
       }

       @Bean
       public UserDetailsService userDetailsService(UserRepository userRepository) {
           return email -> {
               User user = userRepository.findByEmail(email);
               if (user == null) {
                   throw new UsernameNotFoundException("User not found");
               }
               return org.springframework.security.core.userdetails.User
                   .withUsername(user.getEmail())
                   .password(user.getPassword())
                   .roles("USER")
                   .build();
           };
       }
   }
   ```

2. **Ajuste no `UserService` para Criptografar Senhas**:

   ```java
   @Service
   public class UserService {

       @Autowired
       private UserRepository userRepository;

       @Autowired
       private BCryptPasswordEncoder passwordEncoder;

       public void saveUser(User user) {
           user.setPassword(passwordEncoder.encode(user.getPassword()));
           userRepository.save(user);
       }
   }
   ```

3. **Ajuste no `login

.html` para Spring Security**:

   ```html
   <form th:action="@{/login}" method="post">
       <div>
           <label>Email: </label>
           <input type="email" name="username" />
       </div>
       <div>
           <label>Password: </label>
           <input type="password" name="password" />
       </div>
       <div>
           <input type="submit" value="Login" />
       </div>
   </form>
   ```

### **Conclusão e Revisão**

#### **Teoria: Recapitulação e Boas Práticas**

1. **Revisão do Padrão MVC**:
   - Como o MVC organiza a aplicação de forma modular, separando as responsabilidades e facilitando a manutenção e escalabilidade.

2. **Segurança**:
   - A importância de implementar segurança em aplicações web, utilizando Spring Security para autenticação e autorização.

#### **Prática: Teste e Validação**

1. **Testar Funcionalidades**:
   - Registro de novos usuários, login, agendamentos e visualização de procedimentos.
   - Verificar a criptografia de senhas e a proteção de páginas via autenticação.

2. **Deploy no Apache Tomcat**:
   - Configuração e deploy da aplicação no Apache Tomcat para ambiente de produção.

### **Recursos Extras e Próximos Passos**

1. **Documentação**:
   - Referências para a documentação oficial do Spring Framework, Spring Security e Thymeleaf.

2. **Próximos Passos**:
   - Implementar autorização baseada em funções, adicionar testes automatizados e expandir o sistema com novas funcionalidades como cancelamento de agendamentos, notificações e relatórios.
