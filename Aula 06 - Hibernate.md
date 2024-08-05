## Desenvolvimento de Sistemas Web
### Aula 07: Mapeamento Objeto Relacional (ORM) com Java Hibernate
##### **Este material foi gerado com auxílio de IA-Gen. Seu conteúdo foi concebido, organizado e revisado pelo professor.*

**Objetivo da Aula:**  
Nesta aula, os alunos aprenderão a configurar um projeto Java utilizando o Maven como gerenciador de pacotes. Vamos explorar como utilizar o Hibernate para mapear objetos Java para tabelas em um banco de dados MySQL, cobrindo desde a configuração inicial até a execução de operações CRUD. Além disso, abordaremos a teoria sobre o `SessionFactory` do Hibernate e como ele é usado para gerenciar as sessões e transações no contexto de persistência de dados.

---

### Estrutura da Aula

#### 1. Revisão Teórica de Padrões de Projeto, DAO, ORM, JPA e Hibernate (20 minutos)
- **Padrões de Projeto**
- **DAO (Data Access Object)**
- **ORM (Object-Relational Mapping)**
- **JPA (Jakarta Persistence API)**
- **Hibernate**

#### 2. Configuração do Ambiente com Maven no Eclipse (20 minutos)
- **Criação de um Novo Projeto Maven**
- **Adicionar Dependências do Hibernate e MySQL**

#### 3. Teoria sobre SessionFactory do Hibernate (10 minutos)
- **Definição e Propósito**
- **Como Funciona o SessionFactory**
- **Melhores Práticas**

#### 4. Mapeamento de Entidades com Anotações (15 minutos)
- **Entidades e Tabelas**
- **Anotações Básicas: @Entity, @Table, @Id, @GeneratedValue**
- **Anotações de Relacionamentos: @OneToOne, @OneToMany, @ManyToOne, @ManyToMany**

#### 5. Operações CRUD com Hibernate (15 minutos)
- **Criar, Ler, Atualizar e Deletar Entidades**
- **Sessão Hibernate e Transações**

#### 6. Exercícios Práticos (10 minutos)
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

**1.4. JPA (Jakarta Persistence API)**
- **Definição:** JPA é uma especificação Jakarta que fornece um framework para gerenciar dados relacionais em aplicações Java. Ele define a forma como os objetos Java são mapeados para tabelas no banco de dados.
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

---

### Parte 2: Configuração do Ambiente com Maven no Eclipse

**2.1. Criação de um Novo Projeto Maven**

**Passo a Passo:**
1. Abra o Eclipse e vá para `File > New > Project`.
2. Selecione `Maven Project` e clique em `Next`.
3. Escolha o diretório de trabalho do projeto e clique em `Next`.
4. Selecione uma `Archetype` como `maven-archetype-quickstart` para um projeto básico e clique em `Next`.
5. Preencha as informações do projeto: `Group Id` (por exemplo, `com.example`), `Artifact Id` (por exemplo, `desenvolvimento-web`), `Version`, e clique em `Finish`.

**2.2. Adicionar Dependências do Hibernate e MySQL**

- Abra o arquivo `pom.xml` no seu projeto Maven e adicione as seguintes dependências:

```xml
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>desenvolvimento-web</artifactId>
    <version>1.0-SNAPSHOT</version>

    <dependencies>
        <!-- Hibernate Core -->
        <dependency>
            <groupId>org.hibernate</groupId>
            <artifactId>hibernate-core</artifactId>
            <version>5.4.32.Final</version>
        </dependency>

        <!-- Jakarta Persistence API -->
        <dependency>
            <groupId>jakarta.persistence</groupId>
            <artifactId>jakarta.persistence-api</artifactId>
            <version>2.2.3</version>
        </dependency>

        <!-- MySQL Connector -->
        <dependency>
            <groupId>mysql</groupId>
            <artifactId>mysql-connector-java</artifactId>
            <version>8.0.33</version>
        </dependency>

        <!-- SLF4J Logging -->
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-api</artifactId>
            <version>1.7.32</version>
        </dependency>
        <dependency>
            <groupId>org.slf4j</groupId>
            <artifactId>slf4j-simple</artifactId>
            <version>1.7.32</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <!-- Compiler Plugin -->
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>3.8.1</version>
                <configuration>
                    <source>11</source>
                    <target>11</target>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
```

**Explicação das Dependências:**
- **Hibernate Core:** Biblioteca principal do Hibernate para mapeamento objeto-relacional.
- **Jakarta Persistence API:** Define as interfaces JPA que o Hibernate implementa.
- **MySQL Connector:** Driver JDBC para conectar o Java com o banco de dados MySQL.
- **SLF4J:** Biblioteca de logging utilizada pelo Hibernate.

---

### Parte 3: Teoria sobre SessionFactory do Hibernate

**3.1. O que é SessionFactory?**
- **Definição:** O `SessionFactory` é uma fábrica de sessões (Session Factory) no Hibernate. Ele é responsável por criar e gerenciar objetos `Session`, que representam a conexão com o banco de dados. O `SessionFactory` é a espinha

 dorsal de qualquer aplicação Hibernate, atuando como um ponto de configuração compartilhado.
  
- **Propósito:** O `SessionFactory` é projetado para ser instanciado uma única vez por aplicação e mantido em cache para reutilização, uma vez que a criação dele é uma operação custosa. Ele é thread-safe e pode ser compartilhado entre várias threads na aplicação.

**3.2. Como Funciona o SessionFactory?**
- **Configuração:** O `SessionFactory` é configurado a partir do arquivo `hibernate.cfg.xml` ou programaticamente usando `Configuration` em Java.
- **Sessões:** Ele cria objetos `Session`, que são utilizados para realizar operações CRUD (Create, Read, Update, Delete) e consultas HQL.
- **Gerenciamento de Transações:** As transações são gerenciadas dentro de uma sessão, com o `SessionFactory` fornecendo as sessões necessárias para essa operação.

**3.3. Melhores Práticas:**
- **Única Instância:** Sempre crie uma única instância do `SessionFactory` por aplicação, geralmente usando um padrão Singleton.
- **Eficiência:** Manter o `SessionFactory` aberto durante o ciclo de vida da aplicação para maximizar a eficiência e o desempenho.
- **Gerenciamento Adequado de Sessões:** Use `try-with-resources` ou blocos `finally` para garantir que sessões e transações sejam fechadas corretamente, evitando vazamentos de conexão.

**Exemplo de Configuração do SessionFactory:**

```java
package com.example.util;

import org.hibernate.SessionFactory;
import org.hibernate.cfg.Configuration;

public class HibernateUtil {
    private static final SessionFactory sessionFactory = buildSessionFactory();

    private static SessionFactory buildSessionFactory() {
        try {
            // Cria o SessionFactory a partir do arquivo hibernate.cfg.xml
            return new Configuration().configure().buildSessionFactory();
        } catch (Throwable ex) {
            // Log de exceção
            System.err.println("Falha na criação do SessionFactory: " + ex);
            throw new ExceptionInInitializerError(ex);
        }
    }

    public static SessionFactory getSessionFactory() {
        return sessionFactory;
    }
}
```

---

### Parte 4: Mapeamento de Entidades com Anotações

**4.1. Entidades e Tabelas**

**Definição:** Uma entidade representa uma tabela no banco de dados.

**Passo a Passo:**
1. Crie um pacote chamado `com.example.model`.
2. Dentro deste pacote, crie as classes `ServicoEstetico` e `SessaoEstetica`.

**Conteúdo da Classe `ServicoEstetico`:**

```java
package com.example.model;

import jakarta.persistence.*;
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

**Conteúdo da Classe `SessaoEstetica`:**

```java
package com.example.model;

import jakarta.persistence.*;
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

**4.2. Anotações Básicas**
- **@Entity:** Indica que a classe é uma entidade.
- **@Table:** Especifica a tabela do banco de dados que a entidade mapeia.
- **@Id:** Define o campo como chave primária.
- **@GeneratedValue:** Especifica como o valor do campo será gerado.

**4.3. Anotações de Relacionamentos**
- **@OneToMany:** Indica um relacionamento um-para-muitos.
- **@ManyToOne:** Indica um relacionamento muitos-para-um.

---

### Parte 5: Operações CRUD com Hibernate

**5.1. Sessão Hibernate e Transações**

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
            System.err.println("Falha na criação do SessionFactory: " + ex);
            throw new ExceptionInInitializerError(ex);
        }
    }

    public static SessionFactory getSessionFactory() {
        return sessionFactory;
    }
}
```

**5.2. Operações CRUD**

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

---

### Parte 6: Exercícios Práticos

**Exercício 1: Configuração e Mapeamento de Entidades**
- **Tarefa:** Configure o Hibernate no seu projeto e crie entidades para as tabelas `servicos_esteticos` e `sessoes_esteticas`.

**Exercício 2: Operações CRUD**
- **Tarefa:** Implemente as operações CRUD (Create, Read, Update, Delete) para a entidade `ServicoEstetico`.

**Exercício 3: Relacionamento Entre Entidades**
- **Tarefa:** Crie o relacionamento entre `ServicoEstetico` e `SessaoEstetica` utilizando anotações JPA/Hibernate.

**Exercício 4: Consultas Personalizadas**
- **Tarefa:** Implemente uma consulta para listar todos os serviços que têm sessões agendadas em uma data específica.

---

### Conclusão

Neste tutorial, os alunos aprenderam sobre os conceitos fundamentais de ORM e como utilizar o Hibernate para mapear entidades Java a tabelas de banco de dados. Através de instruções detalhadas, exemplos práticos e exercícios, os alunos aplicaram os conceitos aprendidos para criar, ler, atualizar e deletar entidades em uma aplicação web usando Hibernate.

### Links de Leitura Recomendada

1. **Documentação do Hibernate:** [Hibernate ORM Documentation](https://hibernate.org/orm/documentation/)
2. **Tutorial do Jakarta Persistence:** [Jakarta Persistence Tutorial](https://jakarta.ee/specifications/persistence/)
3. **Baeldung - Guia do Hibernate:** [Hibernate Guide](https://www.baeldung.com/hibernate-5)
4. **Vlad Mihalcea's Blog:** [Vlad Mihalcea's Blog](https://vladmihalcea.com/)
5

. **Stack Overflow - Hibernate Tag:** [Hibernate Questions](https://stackoverflow.com/questions/tagged/hibernate)

---

Com estas alterações, o material da aula inclui uma explicação completa sobre o uso do `SessionFactory` no Hibernate, bem como a configuração do projeto usando o Maven para gerenciar dependências. Este formato ajuda a criar uma base sólida para o desenvolvimento de sistemas web Java com persistência de dados.