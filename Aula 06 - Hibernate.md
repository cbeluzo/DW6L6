## Desenvolvimento de Sistemas Web
### Aula 07: Mapeamento Objeto Relacional (ORM) com Java Hibernate
##### **Este material foi gerado com auxílio de IA-Gen. Seu conteúdo foi concebido, organizado e revisado pelo professor.*

**Objetivo da Aula:**
Nesta aula, os alunos aprenderão os conceitos fundamentais de Mapeamento Objeto Relacional (ORM) e como utilizar o Hibernate, uma das ferramentas ORM mais populares em Java. Serão apresentados exemplos práticos a cada tópico explicado e exercícios para aplicar os conceitos aprendidos utilizando Hibernate em uma aplicação web de exemplo. A aula será formatada como um tutorial, com instruções detalhadas para os alunos executarem as tarefas.

---

#### 1. Revisão Teórica de Padrões de Projeto, DAO, ORM, JPA e Hibernate (20 minutos)
- **Padrões de Projeto**
- **DAO (Data Access Object)**
- **ORM (Object-Relational Mapping)**
- **JPA (Java Persistence API)**
- **Hibernate**

#### 2. Configuração do Ambiente no Eclipse
- **Adicionar Dependências do Hibernate**
- **Configuração do Hibernate**
- **Criação de Arquivo de Configuração Hibernate (hibernate.cfg.xml)**

#### 3. Mapeamento de Entidades com Anotações
- **Entidades e Tabelas**
- **Anotações Básicas: @Entity, @Table, @Id, @GeneratedValue**
- **Anotações de Relacionamentos: @OneToOne, @OneToMany, @ManyToOne, @ManyToMany**

#### 4. Operações CRUD com Hibernate
- **Criar, Ler, Atualizar e Deletar Entidades**
- **Sessão Hibernate e Transações**

#### 5. Exercícios Práticos
- **Configuração e Mapeamento de Entidades**
- **Operações CRUD**

---

### Parte 1: Revisão Teórica de Padrões de Projeto, DAO, ORM, JPA e Hibernate

**1.1. Padrões de Projeto**
- **Definição:** Padrões de Projeto (Design Patterns) são soluções reutilizáveis para problemas comuns no desenvolvimento de software. Eles ajudam a tornar o código mais modular, flexível e fácil de manter.
- **Tipos de Padrões:**
  - **Criacionais:** Tratam da criação de objetos. Exemplo: Singleton, Factory Method.
  - **Estruturais:** Lidam com a composição de classes e objetos. Exemplo: Adapter, Composite.
  - **Comportamentais:** Se concentram na interação entre objetos. Exemplo: Observer, Strategy.

**1.2. DAO (Data Access Object)**
- **Definição:** O padrão DAO é usado para separar a lógica de acesso a dados da lógica de negócios. Ele fornece uma interface abstrata para operações de banco de dados, facilitando a manutenção e teste do código.
- **Benefícios:**
  - **Encapsulamento:** Isola a lógica de acesso a dados.
  - **Reusabilidade:** Código de acesso a dados pode ser reutilizado em diferentes partes da aplicação.
  - **Flexibilidade:** Facilita a troca do banco de dados ou a alteração da lógica de persistência sem impactar a lógica de negócios.

**Exemplo de DAO:**
```java
public interface ServicoEsteticoDao {
    void saveServicoEstetico(ServicoEstetico servicoEstetico);
    ServicoEstetico getServicoEstetico(int id);
    void updateServicoEstetico(ServicoEstetico servicoEstetico);
    void deleteServicoEstetico(int id);
}
```

**1.3. ORM (Object-Relational Mapping)**
- **Definição:** ORM é uma técnica de programação que facilita a conversão de dados entre sistemas incompatíveis usando orientação a objetos. Ele mapeia objetos de um sistema orientado a objetos para tabelas de um sistema de banco de dados relacional.
- **Benefícios:**
  - **Redução de Código:** Automatiza grande parte do código de acesso a dados.
  - **Portabilidade:** Facilita a migração entre diferentes sistemas de gerenciamento de banco de dados.
  - **Manutenção:** Simplifica a manutenção do código, pois as mudanças no banco de dados não afetam diretamente o código da aplicação.
  - **Abstração:** Fornece uma camada de abstração entre a aplicação e o banco de dados, tornando a aplicação menos dependente de detalhes específicos de implementação do banco de dados.

**1.4. JPA (Java Persistence API)**
- **Definição:** JPA é uma especificação Java que fornece um framework para gerenciar dados relacionais em aplicações Java. Ele define a forma como os objetos Java são mapeados para tabelas no banco de dados.
- **Principais Componentes:**
  - **EntityManager:** Interface principal para interagir com o contexto de persistência.
  - **Entity:** Classe Java que é mapeada para uma tabela do banco de dados.
  - **Persistence Unit:** Conjunto de todas as classes que são persistidas juntas.

**1.5. Hibernate**
- **Definição:** Hibernate é uma implementação do JPA. Ele facilita o mapeamento entre classes Java e tabelas de banco de dados, e gerencia automaticamente as operações CRUD.
- **Principais Recursos:**
  - **Mappings:** Define como as classes Java são mapeadas para tabelas do banco de dados.
  - **Transações:** Gerencia transações de banco de dados.
  - **Consultas HQL:** Hibernate Query Language, uma linguagem de consulta orientada a objetos semelhante ao SQL.

### Parte 2: Configuração do Ambiente no Eclipse

**2.1. Adicionar Dependências do Hibernate**

**Passo a Passo:**
1. Abra seu projeto no Eclipse.
2. Clique com o botão direito no projeto e selecione `Build Path > Configure Build Path`.
3. Vá para a aba `Libraries` e clique em `Add External JARs`.
4. Adicione o JAR do Hibernate e o JAR do MySQL Connector ao projeto. Caso não os tenha, baixe-os:
   - [Hibernate Core](https://hibernate.org/orm/downloads/)
   - [MySQL Connector](https://dev.mysql.com/downloads/connector/j/)

   Exemplos de arquivos JAR a adicionar:
   - (hibernate-core-5.4.30.Final.jar)[https://repo.maven.apache.org/maven2/org/hibernate/orm/hibernate-core/6.5.2.Final/hibernate-core-6.5.2.Final.jar]
   - (mysql-connector-java-8.0.33.jar)[https://dev.mysql.com/downloads/connector/j/?os=26]
   - Outras dependências do Hibernate (commons-logging, hibernate-annotations, etc.)

5. Clique em `Apply and Close`.

**2.2. Configuração do Hibernate**

**Passo a Passo:**
1. No seu projeto, crie uma pasta chamada `src/main/resources` (ou apenas `src` se o projeto não estiver estruturado para Maven).
2. Dentro desta pasta, crie o arquivo `hibernate.cfg.xml`.

**Conteúdo do `hibernate.cfg.xml`:**

```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE hibernate-configuration PUBLIC
        "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
        "https://hibernate.org/dtd/hibernate-configuration-3.0.dtd">
<hibernate-configuration>
    <session-factory>
        <property name="hibernate.dialect">org.hibernate.dialect.MySQLDialect</property>
        <property name="hibernate.connection.driver_class">com.mysql.cj.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:mysql://localhost:3306/clinicadb</property>
        <property name="hibernate.connection.username">root</property>
        <property name="hibernate.connection.password">password</property>
        <property name="hibernate.hbm2ddl.auto">update</property>
        <property name="hibernate.show_sql">true</property>
        <property name="hibernate.format_sql">true</property>
        
        <!-- Mapping Classes -->
        <mapping class="com.example.model.ServicoEstetico"/>
        <mapping class="com.example.model.SessaoEstetica"/>
    </session-factory>
</hibernate-configuration>
```

### Parte 3: Mapeamento de Entidades com Anotações

**3.1. Entidades e Tabelas**
- **Definição:** Uma entidade representa uma tabela no banco de dados.

**Exemplo de Classe de Entidade:**

**Passo a Passo:**
1. Crie um pacote chamado `com.example.model`.
2. Dentro deste pacote, crie a classe `ServicoEstetico`.

**Conteúdo da Classe `ServicoEstetico`:**

```java
package com.example.model;

import javax.persistence.*;
import java.math.BigDecimal;
import java.util.Set;

@Entity
@Table(name = "servicos_esteticos")
public class ServicoEstetico {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    @Column(name = "name")
    private String name;

    @Column(name = "description")
    private String description;

    @Column(name = "price")
    private BigDecimal price;

    @OneToMany(mappedBy = "servicoEstetico", cascade = CascadeType.ALL)
    private Set<SessaoEstetica> sessoesEsteticas;

    // Getters and Setters
}
```

**3.2. Anotações Básicas**
- **@Entity:** Indica que a classe é uma entidade.
- **@Table:** Especifica a tabela do banco de dados que a entidade mapeia.
- **@Id:** Define o campo como chave primária.
- **@GeneratedValue:** Especifica como o valor do campo será gerado.

**3.3. Anotações de

 Relacionamentos**

**Passo a Passo:**
1. Dentro do pacote `com.example.model`, crie a classe `SessaoEstetica`.

**Conteúdo da Classe `SessaoEstetica`:**

```java
package com.example.model;

import javax.persistence.*;
import java.util.Date;

@Entity
@Table(name = "sessoes_esteticas")
public class SessaoEstetica {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private int id;

    @ManyToOne
    @JoinColumn(name = "servico_estetico_id", nullable = false)
    private ServicoEstetico servicoEstetico;

    @Column(name = "date")
    private Date date;

    @Column(name = "time")
    private String time;

    // Getters and Setters
}
```

### Parte 4: Operações CRUD com Hibernate

**4.1. Sessão Hibernate e Transações**

**Configuração da Fábrica de Sessões:**

**Passo a Passo:**
1. Crie um pacote chamado `com.example.util`.
2. Dentro deste pacote, crie a classe `HibernateUtil`.

**Conteúdo da Classe `HibernateUtil`:**

```java
package com.example.util;

import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class HibernateUtil {
    private static final SessionFactory sessionFactory = buildSessionFactory();

    private static SessionFactory buildSessionFactory() {
        try {
            return new Configuration().configure().buildSessionFactory();
        } catch (Throwable ex) {
            throw new ExceptionInInitializerError(ex);
        }
    }

    public static SessionFactory getSessionFactory() {
        return sessionFactory;
    }
}
```

**4.2. Operações CRUD**

**Exemplo: Criar Entidade**

**Passo a Passo:**
1. Crie um pacote chamado `com.example.dao`.
2. Dentro deste pacote, crie a classe `ServicoEsteticoDaoImpl`.

**Conteúdo da Classe `ServicoEsteticoDaoImpl`:**

```java
package com.example.dao;

import com.example.model.ServicoEstetico;
import com.example.util.HibernateUtil;
import org.hibernate.Session;
import org.hibernate.Transaction;

public class ServicoEsteticoDaoImpl implements ServicoEsteticoDao {
    @Override
    public void saveServicoEstetico(ServicoEstetico servicoEstetico) {
        Transaction transaction = null;
        try (Session session = HibernateUtil.getSessionFactory().openSession()) {
            transaction = session.beginTransaction();
            session.save(servicoEstetico);
            transaction.commit();
        } catch (Exception e) {
            if (transaction != null) {
                transaction.rollback();
            }
            e.printStackTrace();
        }
    }

    @Override
    public ServicoEstetico getServicoEstetico(int id) {
        try (Session session = HibernateUtil.getSessionFactory().openSession()) {
            return session.get(ServicoEstetico.class, id);
        }
    }

    @Override
    public void updateServicoEstetico(ServicoEstetico servicoEstetico) {
        Transaction transaction = null;
        try (Session session = HibernateUtil.getSessionFactory().openSession()) {
            transaction = session.beginTransaction();
            session.update(servicoEstetico);
            transaction.commit();
        } catch (Exception e) {
            if (transaction != null) {
                transaction.rollback();
            }
            e.printStackTrace();
        }
    }

    @Override
    public void deleteServicoEstetico(int id) {
        Transaction transaction = null;
        try (Session session = HibernateUtil.getSessionFactory().openSession()) {
            transaction = session.beginTransaction();
            ServicoEstetico servicoEstetico = session.get(ServicoEstetico.class, id);
            if (servicoEstetico != null) {
                session.delete(servicoEstetico);
                transaction.commit();
            }
        } catch (Exception e) {
            if (transaction != null) {
                transaction.rollback();
            }
            e.printStackTrace();
        }
    }
}
```

### Parte 5: Exercícios Práticos

**Exercício 1: Configuração e Mapeamento de Entidades**
- **Tarefa:** Configure o Hibernate no seu projeto e crie entidades para as tabelas `servicos_esteticos` e `sessoes_esteticas`.

**Exercício 2: Operações CRUD**
- **Tarefa:** Implemente as operações CRUD (Create, Read, Update, Delete) para a entidade `ServicoEstetico`.

**Exercício 3: Relacionamento Entre Entidades**
- **Tarefa:** Crie o relacionamento entre `ServicoEstetico` e `SessaoEstetica` utilizando anotações JPA/Hibernate.

**Exercício 4: Consultas Personalizadas**
- **Tarefa:** Implemente uma consulta para listar todos os serviços que têm sessões agendadas em uma data específica.

---

### Material Complementar
- [Hibernate ORM Documentation](https://hibernate.org/orm/documentation/)

- [Java EE 7 Tutorial - JPA](https://docs.oracle.com/javaee/7/tutorial/persistence-intro.htm)

- [Coursera - Java Programming and Software Engineering Fundamentals](https://www.coursera.org/specializations/java-programming)
 