<a name="topo"></a>
# **Aula 2: Conceitos Fundamentais em Sistemas Web**

### **1. Introdução aos Sistemas Web**

#### **Definição de Sistemas Web**
> Sistemas web são aplicações que funcionam na internet e são acessadas por meio de navegadores web, como Google Chrome, Mozilla Firefox ou Microsoft Edge. Diferentemente das aplicações tradicionais instaladas localmente em um computador, sistemas web são executados remotamente em servidores e permitem que os usuários interajam com a aplicação sem a necessidade de instalação de software no dispositivo.

- **Características Principais de Sistemas Web**:
  - Acessíveis de qualquer dispositivo conectado à internet, incluindo computadores, tablets e smartphones.
  - Atualizações e manutenções realizadas no servidor central, sem necessidade de intervenção nos dispositivos dos usuários.
  - Suporte para múltiplos usuários simultaneamente, com escalabilidade ajustada conforme a demanda de acesso.

#### **Diferença entre Sistemas Web e Aplicações Desktop**
Para compreender os sistemas web, é fundamental compará-los com as **aplicações desktop**, que são instaladas e executadas diretamente no dispositivo do usuário. Aqui estão as principais diferenças:

1. **Execução e Infraestrutura**:
   - **Aplicações Desktop**: Executadas localmente no computador ou dispositivo do usuário. Exigem a instalação de um software que roda nativamente no sistema operacional (e.g., Microsoft Word).
   - **Sistemas Web**: Executados em servidores remotos e acessados por meio de navegadores, onde o processamento é feito no servidor, e o navegador atua como interface para o usuário (e.g., Google Docs).

2. **Instalação e Manutenção**:
   - **Aplicações Desktop**: Precisam ser instaladas e atualizadas manualmente em cada dispositivo do usuário.
   - **Sistemas Web**: Não requerem instalação. Atualizações são feitas diretamente no servidor e refletem para todos os usuários simultaneamente, sem necessidade de ações locais.

3. **Acesso e Portabilidade**:
   - **Aplicações Desktop**: Acesso limitado ao dispositivo em que o software está instalado. Dependendo do sistema operacional, o software pode não ser compatível com outros dispositivos.
   - **Sistemas Web**: Acessíveis em qualquer dispositivo com um navegador web e conexão à internet, permitindo maior portabilidade e conveniência.

4. **Escalabilidade**:
   - **Aplicações Desktop**: Limitadas ao poder de processamento e memória do dispositivo do usuário.
   - **Sistemas Web**: A escalabilidade é gerida no servidor, permitindo que as aplicações atendam a milhares ou milhões de usuários simultaneamente, ajustando os recursos do servidor conforme necessário.

#### **Exemplo Comparativo: Microsoft Word vs. Google Docs**
Para ilustrar essas diferenças, podemos comparar duas ferramentas populares de edição de texto: **Microsoft Word** e **Google Docs**.

- **Microsoft Word (Aplicação Desktop)**:
  - **Instalação**: O Word precisa ser instalado no dispositivo do usuário, seja um computador com Windows ou Mac.
  - **Acesso**: Só pode ser acessado no dispositivo onde está instalado, a menos que o arquivo seja manualmente transferido para outro dispositivo.
  - **Atualizações**: Atualizações precisam ser instaladas individualmente em cada dispositivo, o que pode gerar inconsistências entre diferentes versões usadas por pessoas.
  - **Colaboração**: Colaboração em tempo real só é possível com o uso de serviços complementares, como o OneDrive, e depende de sincronização entre os dispositivos.

- **Google Docs (Sistema Web)**:
  - **Acesso via Navegador**: O Google Docs pode ser acessado de qualquer dispositivo com conexão à internet e um navegador, sem necessidade de instalação.
  - **Colaboração em Tempo Real**: Permite que múltiplos usuários editem o mesmo documento simultaneamente, com atualizações refletidas instantaneamente para todos os colaboradores.
  - **Escalabilidade e Manutenção**: O Google Docs é gerido pela infraestrutura de servidores do Google, permitindo que milhões de usuários o acessem e utilizem simultaneamente sem impacto no desempenho. Atualizações são automáticas e transparentes ao usuário.

#### **Vantagens dos Sistemas Web**
- **Facilidade de Acesso**: Usuários podem acessar suas contas e dados de qualquer lugar, desde que tenham conexão à internet.
- **Colaboração**: Muitos sistemas web suportam colaboração em tempo real, onde múltiplos usuários podem interagir simultaneamente com o mesmo conteúdo.
- **Custos de Manutenção Reduzidos**: Atualizações, patches de segurança e melhorias são feitas diretamente no servidor, economizando tempo e esforço de TI.
- **Integração com Outros Serviços Web**: Os sistemas web geralmente podem se integrar facilmente a outras plataformas, serviços de nuvem e APIs, criando um ecossistema unificado e poderoso.

#### **Limitações dos Sistemas Web**
Embora sistemas web ofereçam muitas vantagens, eles também apresentam algumas limitações:
- **Dependência de Conectividade**: Sistemas web precisam de uma conexão estável à internet para funcionarem corretamente, o que pode ser uma desvantagem em áreas com conectividade limitada.
- **Performance**: Para aplicações que exigem muito processamento (como jogos ou editores de vídeo), as versões web podem ter uma performance inferior em comparação com aplicativos desktop nativos.
- **Segurança e Privacidade**: Como os dados são transmitidos pela internet, sistemas web devem implementar fortes medidas de segurança para evitar brechas ou ataques cibernéticos.

---

### **2. Arquitetura Cliente-Servidor**

#### **Definição**
> A **arquitetura cliente-servidor** é um modelo de comunicação amplamente utilizado em sistemas web e aplicações distribuídas. Nessa arquitetura, o cliente e o servidor desempenham papéis distintos:
>- O **cliente** é responsável por iniciar a comunicação, geralmente fazendo requisições a um servidor em busca de dados ou serviços.
>- O **servidor** recebe as requisições do cliente, processa-as e envia as respostas apropriadas, que podem ser dados, arquivos ou informações processadas.

A principal característica dessa arquitetura é a separação das responsabilidades entre o cliente e o servidor, facilitando a escalabilidade e o gerenciamento dos sistemas.

#### **Componentes da Arquitetura Cliente-Servidor**
1. **Cliente**:
   - O cliente é qualquer dispositivo ou software que interage com o servidor para acessar os recursos ou serviços fornecidos por ele.
   - Normalmente, em sistemas web, o cliente é um navegador (como Google Chrome, Firefox ou Edge), mas também pode ser um aplicativo móvel ou um software de desktop.
   - Exemplo de Ação: O cliente pode enviar uma requisição ao servidor pedindo para acessar uma página da web, como quando você digita um URL no navegador.

2. **Servidor**:
   - O servidor é responsável por processar as requisições recebidas dos clientes e fornecer as respostas adequadas. Isso pode incluir acessar uma base de dados, processar lógica de negócios ou simplesmente servir arquivos estáticos (como HTML, CSS e JavaScript).
   - Em uma arquitetura web, o servidor pode ser um servidor de aplicação como **Apache Tomcat** (para aplicações Java) ou **NGINX** (para servir conteúdo estático ou agir como proxy reverso).

3. **Protocolo de Comunicação**:
   - O **HTTP (Hypertext Transfer Protocol)** é o protocolo mais comumente utilizado para a troca de dados entre cliente e servidor na web.
   - O cliente envia uma **requisição HTTP** ao servidor, e o servidor responde com um **status HTTP** (como 200 OK ou 404 Not Found) e o conteúdo solicitado (página HTML, JSON, etc.).

#### **Ciclo de Vida de uma Requisição HTTP**
Uma requisição HTTP típica segue o seguinte ciclo:

1. **Cliente envia a Requisição**:
   - Quando o usuário digita um URL em um navegador ou interage com um formulário, o cliente (navegador) faz uma requisição HTTP ao servidor.
   - Essa requisição pode ser de vários tipos, como GET (para buscar dados), POST (para enviar dados), PUT (para atualizar dados), ou DELETE (para remover dados).

2. **Servidor processa a Requisição**:
   - O servidor recebe a requisição, verifica os dados fornecidos e decide como processar.
   - Isso pode incluir lógica de negócios, interações com banco de dados, ou simplesmente retornar um arquivo HTML ou JSON.

3. **Servidor envia a Resposta**:
   - Após o processamento, o servidor envia uma resposta ao cliente, geralmente contendo o conteúdo solicitado (por exemplo, uma página HTML ou dados no formato JSON) e um código de status HTTP, indicando o resultado da operação (como 200 OK, 400 Bad Request, 500 Internal Server Error).

4. **Cliente exibe o Resultado**:
   - O navegador exibe a resposta para o usuário, seja como uma página web ou os dados de um serviço web.

#### **Exemplo de Funcionamento: Requisição HTTP GET para uma Página de E-commerce**
Imagine que um usuário deseja acessar a página de um produto em uma loja de e-commerce.

1. O usuário digita a URL `https://lojaexemplo.com/produto/12345` no navegador.
2. O navegador (cliente) faz uma **requisição GET** para o servidor da loja.
3. O servidor recebe a requisição, identifica o produto com o ID `12345`, consulta o banco de dados, e então prepara a página HTML correspondente.
4. O servidor envia a resposta ao cliente com o código de status **200 OK** e o conteúdo da página HTML.
5. O navegador processa e exibe a página de detalhes do produto ao usuário.

#### **Vantagens da Arquitetura Cliente-Servidor**
1. **Escalabilidade**: Ao separar as responsabilidades do cliente e do servidor, essa arquitetura permite que ambos os lados sejam dimensionados independentemente. Um servidor pode atender a milhares de clientes simultaneamente.
2. **Manutenção Centralizada**: O servidor centraliza o processamento, de modo que atualizações ou correções feitas no servidor são refletidas imediatamente para todos os clientes.
3. **Flexibilidade**: A arquitetura cliente-servidor pode suportar múltiplos tipos de clientes, como navegadores, aplicativos móveis, e softwares de desktop, todos interagindo com o mesmo servidor.

#### **Limitações da Arquitetura Cliente-Servidor**
1. **Dependência de Conexão**: O cliente deve estar conectado ao servidor para acessar os recursos. Se a conexão for lenta ou falhar, o cliente pode enfrentar dificuldades.
2. **Carga no Servidor**: Se o número de clientes crescer rapidamente, o servidor pode sobrecarregar, exigindo maior capacidade de processamento e ajustes de escalabilidade.

---

### **3. Protocolo HTTP**

#### **Definição e Importância**
>O **HTTP (Hypertext Transfer Protocol)** é o protocolo fundamental para a comunicação de dados na web. Ele define como as mensagens são formatadas e transmitidas entre clientes (como navegadores) e servidores. Toda interação básica na web, como carregar uma página, enviar um formulário ou baixar um arquivo, utiliza HTTP como meio de transporte para dados.

- **Definição**: HTTP é um protocolo de aplicação, usado para troca de informações entre sistemas distribuídos, colaborativos e orientados a hipermídia. Sua principal função é permitir a comunicação entre navegadores web (clientes) e servidores web.
  
- **Importância**: HTTP é essencial para o funcionamento da web, pois define um conjunto padrão de regras para transferir dados, seja texto, imagens, vídeos ou outros tipos de arquivos. Ele também suporta uma série de operações como leitura (GET), envio de dados (POST), atualização de informações (PUT) e exclusão de recursos (DELETE). Sem o HTTP, a internet moderna como conhecemos hoje não seria possível.

  O HTTP é **stateless** (sem estado), o que significa que cada requisição é independente e não mantém informações sobre as anteriores. Para persistir estados entre requisições (como sessões de login), tecnologias complementares, como cookies e tokens de autenticação, são utilizadas.

#### **Tipos de Requisição HTTP**
O HTTP define diversos **métodos de requisição** que especificam a ação desejada em relação a um recurso no servidor. Os principais métodos são:

1. **GET**:
   - **Descrição**: Usado para solicitar dados de um servidor. É o método mais comum, utilizado para obter páginas HTML, imagens, vídeos ou qualquer outro recurso.
   - **Características**: Os parâmetros de uma requisição GET são passados na URL (como parte da query string), tornando-os visíveis ao usuário e limitados em tamanho.
   - **Exemplo**: Acessar um URL como `https://example.com/produto?id=123` faz uma requisição GET para obter os detalhes de um produto.

2. **POST**:
   - **Descrição**: Usado para enviar dados ao servidor, geralmente para criar ou processar informações. O POST é amplamente utilizado em formulários e para enviar grandes volumes de dados ou dados sensíveis.
   - **Características**: Os dados são enviados no **corpo da requisição**, tornando o POST mais seguro que o GET para informações sensíveis. Não há limite de tamanho de dados.
   - **Exemplo**: Um formulário de login que envia o nome de usuário e senha para o servidor via POST.

3. **PUT**:
   - **Descrição**: Usado para **atualizar** um recurso existente no servidor. Uma requisição PUT substitui o recurso atual com os novos dados fornecidos.
   - **Características**: Envia os dados de atualização no corpo da requisição.
   - **Exemplo**: Atualizar os detalhes de um produto no servidor.

4. **DELETE**:
   - **Descrição**: Usado para **remover** um recurso no servidor.
   - **Exemplo**: Remover um item de um catálogo de produtos.

#### **Ciclo de Vida de uma Requisição HTTP**
1. **Cliente faz a Requisição**: O cliente (geralmente um navegador) envia uma requisição HTTP ao servidor. A requisição inclui:
   - O **método HTTP** (GET, POST, PUT, DELETE).
   - O **URL** do recurso que está sendo solicitado.
   - **Cabeçalhos HTTP** que fornecem informações adicionais sobre a requisição (como o tipo de conteúdo aceito, informações de autenticação, etc.).
   - O corpo da requisição (no caso de métodos como POST e PUT).
   
2. **Servidor processa a Requisição**: O servidor interpreta a requisição, executa a ação necessária (por exemplo, busca um arquivo, atualiza um banco de dados ou exclui um registro) e prepara uma resposta.

3. **Servidor envia a Resposta**: O servidor responde ao cliente com:
   - Um **código de status HTTP**, como 200 OK (requisição bem-sucedida), 404 Not Found (recurso não encontrado) ou 500 Internal Server Error (erro no servidor).
   - O conteúdo solicitado, como uma página HTML ou um arquivo JSON.
   - **Cabeçalhos HTTP** adicionais com metadados sobre a resposta.

4. **Cliente recebe e exibe a Resposta**: O navegador ou o cliente HTTP interpreta a resposta e exibe o conteúdo ao usuário, como uma página da web ou os dados retornados por uma API.

---

### **4. Evolução das Aplicações Web**

A web evoluiu significativamente desde sua criação, mudando a forma como os usuários interagem com conteúdo e serviços online. Essa evolução pode ser dividida em três fases principais: **Web 1.0**, **Web 2.0**, e **Web 3.0**, cada uma com características e tecnologias distintas.

#### **Web 1.0 (Web Estática)**

**Período**: Início dos anos 1990 até o início dos anos 2000.

- **Definição**: A **Web 1.0** é a primeira fase da internet, caracterizada por **páginas estáticas**, onde os usuários eram meramente consumidores de conteúdo. As páginas web eram basicamente documentos HTML estáticos, sem interatividade significativa.
  
- **Características**:
  - **Páginas Estáticas**: As informações eram fixas e raramente mudavam. O conteúdo era criado e publicado pelos administradores do site, sem participação dos usuários.
  - **Falta de Interatividade**: Os usuários podiam apenas visualizar informações e navegar entre páginas, mas não podiam contribuir com conteúdo, como ocorre em blogs e redes sociais hoje.
  - **Uso Limitado de Scripts**: Pouco ou nenhum uso de linguagens de script como JavaScript. A navegação entre páginas envolvia carregamento completo da página.
  - **Monodirecional**: A comunicação era unidirecional (do site para o usuário). Não havia um diálogo ou participação ativa do usuário no processo de criação de conteúdo.

- **Exemplo**: Os primeiros sites de empresas ou universidades, como o site original do **Yahoo** ou **AOL**, são exemplos de páginas da Web 1.0. Eles continham informações simples e links para outros sites, com pouca ou nenhuma interação com os usuários.

- **Limitações**:
  - **Conteúdo Estático**: Não havia possibilidade de os usuários alterarem o conteúdo de forma dinâmica, como ocorre em redes sociais.
  - **Pouca Flexibilidade**: O conteúdo era centralizado e administrado por poucos editores.

#### **Web 2.0 (Web Participativa ou Social)**

**Período**: Início dos anos 2000 até os dias atuais.

- **Definição**: A **Web 2.0** marcou uma revolução na internet, onde os usuários passaram a ser **participantes ativos**, não apenas consumidores de conteúdo. A ênfase na interação e colaboração deu origem ao conceito de **Web Social**.

- **Características**:
  - **Interatividade e Participação**: Com a Web 2.0, os usuários podem criar e compartilhar conteúdo. Exemplos incluem blogs, fóruns, redes sociais, e sites de colaboração como a **Wikipedia**.
  - **Tecnologias como AJAX**: O uso de tecnologias como **AJAX (Asynchronous JavaScript and XML)** permitiu a atualização de partes da página sem a necessidade de recarregar a página inteira, melhorando a experiência do usuário.
  - **Aplicações Dinâmicas**: A web começou a oferecer aplicativos mais ricos e interativos, como redes sociais (**Facebook**, **Twitter**) e plataformas de vídeo como o **YouTube**.
  - **SOA e APIs**: A adoção de **Arquiteturas Orientadas a Serviços (SOA)** e a criação de APIs permitiu que diferentes aplicações se comunicassem e se integrassem, facilitando o desenvolvimento de mashups (combinação de serviços de diferentes plataformas).
  - **Comunidades e Colaboração**: O foco passou a ser a colaboração e o compartilhamento de conteúdo, como fóruns de discussão, redes sociais e wikis.

- **Exemplo**: **Wikipedia** é um exemplo clássico da Web 2.0. Ela permite que qualquer usuário crie, edite e compartilhe conteúdo colaborativamente. Outro exemplo é o **Facebook**, onde os usuários criam e compartilham suas próprias postagens, fotos e vídeos, interagindo diretamente com outras pessoas.

- **Benefícios**:
  - **Interação e Colaboração**: Os usuários têm a capacidade de colaborar em tempo real, compartilhar conteúdo e interagir de forma direta.
  - **Crescimento das Redes Sociais**: A Web 2.0 impulsionou o crescimento de plataformas sociais que mudaram a maneira como as pessoas se conectam e compartilham experiências.

- **Limitações**:
  - **Centralização dos Dados**: Embora a Web 2.0 seja mais interativa, as grandes plataformas sociais controlam os dados dos usuários, criando questões de privacidade e monopólio de informação.

#### **Web 3.0 (Web Semântica)**

**Período**: Desde o início da década de 2010 até o presente, com um futuro ainda em desenvolvimento.

- **Definição**: A **Web 3.0**, ou **Web Semântica**, representa uma internet onde os dados são organizados de forma mais inteligente e interconectada, facilitando a compreensão automática por máquinas. Seu objetivo é tornar a web mais eficiente, conectada e personalizada, utilizando inteligência artificial (IA) para interpretar e usar os dados.

- **Características**:
  - **Dados Semânticos**: O foco da Web 3.0 é criar uma estrutura na qual as máquinas podem "entender" o significado dos dados na web, permitindo uma experiência mais inteligente e personalizada para os usuários.
  - **Interconectividade de Dados**: Dados de diferentes fontes são interligados de maneira inteligente, criando uma rede de informações mais rica e contextualizada.
  - **Inteligência Artificial e Machine Learning**: A IA desempenha um papel fundamental na Web 3.0, permitindo a análise e interpretação de grandes volumes de dados para personalizar a experiência do usuário e automatizar tarefas.
  - **Blockchain e Descentralização**: Outro pilar da Web 3.0 é a descentralização dos dados, com tecnologias como blockchain, que permitem que os usuários controlem melhor seus próprios dados, sem depender de grandes corporações centralizadas.
  - **Web Personalizada**: A web se adapta às necessidades e preferências de cada usuário, fornecendo conteúdo altamente relevante com base em dados semânticos e análises preditivas.

- **Exemplo**: **Wolfram Alpha**, um mecanismo de busca computacional que tenta interpretar consultas de forma semântica e fornecer respostas precisas. Outro exemplo são as aplicações baseadas em **blockchain** e **contratos inteligentes** no contexto de finanças descentralizadas (DeFi).

- **Benefícios**:
  - **Personalização Avançada**: Os usuários terão uma web personalizada com base nas suas preferências, comportamentos e interações passadas.
  - **Descentralização**: A Web 3.0 também introduz uma nova era de descentralização, onde os usuários têm controle sobre seus dados e identidades digitais.

- **Limitações**:
  - **Complexidade Técnica**: A implementação da Web 3.0 é tecnicamente complexa e ainda está em desenvolvimento.
  - **Privacidade**: A personalização e o uso extensivo de dados podem levantar preocupações sobre a privacidade, exigindo regulamentações adequadas.

#### **Estudo de Caso: Evolução da Wikipédia**
- **Web 2.0**: A **Wikipédia** é um dos melhores exemplos da Web 2.0, pois se baseia na participação colaborativa dos usuários. Eles podem criar e editar artigos, contribuindo para o conhecimento global. No entanto, o controle editorial e a moderação centralizada ainda são necessários para manter a qualidade e a confiabilidade dos artigos.

- **Previsão para Web 3.0**: Na **Web 3.0**, a Wikipédia poderia evoluir para uma plataforma descentralizada de conhecimento, onde os artigos são verificados automaticamente com base em fontes interligadas e onde os editores podem usar sistemas de reputação baseados em blockchain para garantir a autenticidade e precisão das informações. A integração de IA poderia permitir a geração automática de conteúdo ou a correção de informações incorretas, tornando a plataforma mais confiável e autossuficiente.

---

### **6. Diferença entre Servidor Web e Servidor de Aplicação**

#### **Servidor Web**

>**Definição**: Um **servidor web** é um software ou hardware dedicado a **hospedar e entregar conteúdo estático** para dispositivos clientes, como navegadores web. Esse conteúdo estático geralmente inclui arquivos HTML, CSS, JavaScript, imagens e outros tipos de arquivos que não requerem processamento dinâmico no lado do servidor.

- **Função Principal**: O servidor web processa requisições HTTP e retorna respostas com os recursos solicitados, como páginas HTML e arquivos de mídia. Ele lida com a comunicação entre o cliente e o servidor por meio do protocolo HTTP (ou HTTPS para comunicações seguras).
  
- **Exemplo de Conteúdo Estático**:
  - Páginas HTML simples.
  - Imagens e vídeos.
  - Arquivos de estilo CSS e scripts JavaScript.

- **Exemplos de Servidores Web**:
  - **Apache HTTP Server**: Um dos servidores web mais populares e amplamente utilizados para hospedar páginas estáticas.
  - **NGINX**: Usado tanto como servidor web quanto como proxy reverso, conhecido por seu desempenho superior ao servir conteúdos estáticos.

- **Responsabilidade**:
  - Gerenciar requisições HTTP.
  - Servir conteúdo estático, como arquivos de páginas e mídia.
  - Redirecionar ou rotear requisições para servidores de aplicação quando necessário.

- **Limitações**: Um servidor web não executa lógica de negócios nem interage com bancos de dados diretamente. Ele se limita a entregar o conteúdo disponível no servidor de arquivos ou redirecionar para outras camadas de aplicação que tratam processamento dinâmico.

#### **Servidor de Aplicação**

> **Definição**: Um **servidor de aplicação** vai além do servidor web, permitindo a **execução de lógica de negócios** e facilitando a **integração com bancos de dados**. Ele não apenas serve conteúdo estático, mas também processa requisições dinâmicas, executando código no lado do servidor (como Java, Python, Ruby, etc.) e gerando conteúdo dinâmico com base nas interações dos usuários e nos dados recebidos.

- **Função Principal**: Um servidor de aplicação recebe requisições de clientes (como navegadores ou APIs), processa a lógica de negócios (como consultas ao banco de dados ou cálculos complexos), e retorna a resposta adequada. Ele pode manipular tanto conteúdo estático quanto dinâmico, muitas vezes usando servidores web como front-end.

- **Exemplo de Conteúdo Dinâmico**:
  - Páginas web que são geradas dinamicamente com base em dados de um banco de dados (e.g., páginas de e-commerce, sistemas de login).
  - APIs RESTful que fornecem dados em formato JSON ou XML.
  - Aplicações empresariais que gerenciam transações e estados persistentes.

- **Exemplos de Servidores de Aplicação**:
  - **Apache Tomcat**: Um servidor de aplicação popular para aplicações web baseadas em Java. Ele também funciona como um container de servlets, gerenciando componentes Java para responder a requisições HTTP dinâmicas.
  - **WildFly (antigo JBoss)**: Um servidor de aplicação robusto para o desenvolvimento de aplicações empresariais em Java.
  - **GlassFish**: Outro servidor de aplicação Java EE para construir e hospedar aplicações empresariais.

- **Responsabilidade**:
  - Gerenciar o ciclo de vida da aplicação.
  - Executar lógica de negócios e processar interações com o banco de dados.
  - Gerenciar transações, segurança e autenticação de usuários.
  - Servir APIs e serviços web dinâmicos.

#### **Comparação entre Servidor Web e Servidor de Aplicação**

| **Característica**               | **Servidor Web**                                   | **Servidor de Aplicação**                                        |
|----------------------------------|---------------------------------------------------|-----------------------------------------------------------------|
| **Objetivo Principal**           | Servir conteúdo estático (HTML, CSS, imagens)      | Executar lógica de negócios e servir conteúdo dinâmico          |
| **Interação com Banco de Dados** | Não interage diretamente com banco de dados        | Pode se conectar e interagir com bancos de dados                |
| **Lógica de Negócios**           | Não executa lógica de negócios                     | Executa lógica de negócios, manipulação de dados e transações   |
| **Tecnologias**                  | Apache HTTP, NGINX                                | Tomcat, WildFly, GlassFish, IBM WebSphere                       |
| **Tipos de Conteúdo Servido**    | Conteúdo estático                                 | Conteúdo dinâmico (páginas geradas com base em dados do usuário) |
| **Escopo de Uso**                | Sites simples, blogs, landing pages                | Aplicações complexas, como e-commerce e sistemas empresariais    |

#### **Exemplo Prático**

- **Servidor Web com Apache HTTP Server**:
  1. Configure o **Apache HTTP Server** para hospedar um site de portfólio que contém apenas páginas HTML e imagens estáticas.
  2. O Apache servirá os arquivos HTML e as imagens diretamente para o navegador do usuário sem nenhum processamento adicional.

- **Servidor de Aplicação com Apache Tomcat**:
  1. Configure o **Apache Tomcat** para hospedar uma aplicação web dinâmica que contém um sistema de login e consultas a um banco de dados de usuários.
  2. A aplicação será capaz de processar requisições POST de formulários de login, acessar o banco de dados para verificar as credenciais do usuário, e retornar uma página gerada dinamicamente com base na resposta.

#### **Exemplo Prático Detalhado**: Configuração de Apache HTTP e Tomcat

1. **Servidor Web (Apache HTTP Server)**:
   - **Objetivo**: Hospedar um site estático contendo uma página HTML simples.
   - **Passos**:
     - Instalar o **Apache HTTP Server**.
     - Criar um arquivo HTML (`index.html`) no diretório raiz do Apache.
     - Acessar o site via navegador em `http://localhost/index.html` para visualizar o conteúdo estático.

   **Conteúdo de Exemplo**:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Meu Site Estático</title>
   </head>
   <body>
       <h1>Bem-vindo ao Meu Site</h1>
       <p>Este é um site estático hospedado no Apache HTTP Server.</p>
   </body>
   </html>
   ```

2. **Servidor de Aplicação (Apache Tomcat)**:
   - **Objetivo**: Hospedar uma aplicação dinâmica com sistema de login que interage com um banco de dados.
   - **Passos**:
     - Instalar o **Apache Tomcat**.
     - Criar um servlet Java para processar o formulário de login.
     - Configurar o servlet no `web.xml` e definir a lógica para verificar as credenciais do usuário no banco de dados.
     - Acessar a aplicação no navegador para testar o sistema de login.

   **Exemplo de Código Servlet**:
   ```java
   @WebServlet("/login")
   public class LoginServlet extends HttpServlet {
       protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
           String username = request.getParameter("username");
           String password = request.getParameter("password");

           // Lógica para verificar credenciais (simulada aqui)
           if ("admin".equals(username) && "admin123".equals(password)) {
               response.getWriter().println("Login bem-sucedido!");
           } else {
               response.getWriter().println("Login falhou.");
           }
       }
   }
   ```

---

### **6. Servlets**

#### **Definição**
>Um **Servlet** é uma classe Java que estende as funcionalidades de um servidor web, permitindo o processamento de **requisições HTTP** e a geração de respostas dinâmicas. Os servlets são componentes de software executados em um **Servlet Container** (como o **Apache Tomcat**), que gerencia o ciclo de vida dos servlets e facilita a comunicação entre o cliente (geralmente um navegador) e a aplicação Java hospedada no servidor.

- **Papel do Servlet**: Ao contrário de páginas estáticas, como HTML, os servlets permitem que a lógica de negócios seja processada no servidor em resposta às requisições dos clientes. Eles são usados para criar aplicações web dinâmicas, como sistemas de login, e-commerce, blogs, entre outros.

#### **Funcionalidade de um Servlet**
>Os **Servlets** operam de maneira eficiente como intermediários entre o cliente e o servidor, permitindo que uma aplicação Java no servidor manipule e responda a requisições HTTP. Através dos servlets, o servidor pode gerar conteúdo dinâmico (como páginas HTML geradas em tempo real) ou fornecer respostas formatadas (como dados JSON ou XML).

- **Processamento de Requisições**:
  - **Receber Requisições**: Quando um cliente (como um navegador) envia uma requisição HTTP ao servidor, o **Servlet Container** recebe essa requisição e direciona para o servlet apropriado.
  - **Processar Dados**: O servlet captura os parâmetros enviados na requisição (como dados de um formulário) e realiza a lógica de negócios apropriada, como a consulta de um banco de dados ou a execução de cálculos.
  - **Retornar Resposta**: Após processar os dados, o servlet gera uma resposta, que normalmente é uma página HTML, ou um retorno em formato JSON ou XML para APIs.

#### **Componentes do Servlet**
1. **Servlet Container**: Ambiente que gerencia o ciclo de vida dos servlets e gerencia as requisições e respostas HTTP. Exemplos de containers são **Apache Tomcat** e **Jetty**.
2. **Métodos HTTP**:
   - **doGet()**: Usado para processar requisições GET (comuns em consultas de páginas ou informações).
   - **doPost()**: Usado para processar requisições POST (comuns em submissão de formulários ou envio de dados ao servidor).

#### **Processamento de Requisições HTTP**
Um servlet trabalha diretamente com o **protocolo HTTP**, capturando as informações enviadas na requisição e retornando uma resposta baseada na lógica de negócio da aplicação. 

- **Ciclo de Vida de uma Requisição**:
  1. **Cliente Envia a Requisição**: O navegador envia uma requisição HTTP, como GET ou POST, para um recurso no servidor.
  2. **Captura de Parâmetros**: O servlet pode capturar parâmetros da URL (em requisições GET) ou do corpo da requisição (em requisições POST).
  3. **Lógica de Negócios**: O servlet processa os dados recebidos, executando a lógica de negócios, como a verificação de credenciais de login, consulta a banco de dados, ou cálculo de informações.
  4. **Geração de Resposta**: O servlet gera uma resposta, geralmente uma página HTML ou um objeto JSON, e a envia de volta ao cliente.

#### **Exemplo Prático: Criando um Servlet que Processa um Formulário**
Vamos criar um servlet simples que recebe dados de um formulário de login e responde com uma mensagem personalizada.

1. **HTML Formulário (cliente)**:
   ```html
   <!DOCTYPE html>
   <html lang="en">
   <head>
       <meta charset="UTF-8">
       <meta name="viewport" content="width=device-width, initial-scale=1.0">
       <title>Login</title>
   </head>
   <body>
       <h2>Formulário de Login</h2>
       <form action="/loginServlet" method="POST">
           <label for="username">Usuário:</label><br>
           <input type="text" id="username" name="username"><br><br>
           <label for="password">Senha:</label><br>
           <input type="password" id="password" name="password"><br><br>
           <input type="submit" value="Entrar">
       </form>
   </body>
   </html>
   ```

   - **Explicação**: O formulário HTML envia uma requisição POST ao servidor quando o usuário clica no botão "Entrar". Os dados do formulário (usuário e senha) são enviados ao servlet.

2. **Servlet Java (servidor)**:
   ```java
   import javax.servlet.ServletException;
   import javax.servlet.annotation.WebServlet;
   import javax.servlet.http.HttpServlet;
   import javax.servlet.http.HttpServletRequest;
   import javax.servlet.http.HttpServletResponse;
   import java.io.IOException;
   import java.io.PrintWriter;

   @WebServlet("/loginServlet")
   public class LoginServlet extends HttpServlet {
       protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
           // Capturando os parâmetros da requisição
           String username = request.getParameter("username");
           String password = request.getParameter("password");

           response.setContentType("text/html");
           PrintWriter out = response.getWriter();

           // Lógica de verificação simples
           if ("admin".equals(username) && "admin123".equals(password)) {
               out.println("<h1>Login bem-sucedido!</h1>");
           } else {
               out.println("<h1>Usuário ou senha inválidos.</h1>");
           }
       }
   }
   ```

   - **Explicação**:
     - O servlet captura os parâmetros `username` e `password` enviados pelo formulário.
     - Ele processa os dados e retorna uma página HTML que mostra se o login foi bem-sucedido ou não.
     - O servlet está configurado para ser acessado em `/loginServlet` e processa apenas requisições POST.

#### **Protocolo HTTP e Servlets**
>Os servlets são frequentemente usados com o **protocolo HTTP** (Hypertext Transfer Protocol), o padrão para a comunicação entre clientes e servidores na web. O HTTP é um protocolo **sem estado**, o que significa que cada requisição é independente das anteriores. Isso implica que servlets precisam de técnicas como **cookies**, **sessões**, ou **tokens de autenticação** para manter o estado entre diferentes requisições (como manter um usuário logado em um sistema).

- **Métodos Comuns de HTTP**:
  - **GET**: Usado para buscar dados, sem alterar o estado do servidor. Os parâmetros são enviados pela URL.
  - **POST**: Usado para enviar dados ao servidor (e.g., submissão de formulários). Os parâmetros são enviados no corpo da requisição, oferecendo maior segurança para dados sensíveis.

---

### **7. Tomcat: O Container de Servlets**

#### **Definição**
>O **Apache Tomcat** é um **servidor de aplicação leve** e amplamente utilizado que atua como um **container de Servlets**. Ele fornece um ambiente de execução para **Servlets** e **JavaServer Pages (JSP)**, permitindo que aplicações web dinâmicas sejam desenvolvidas e executadas em conformidade com as especificações da plataforma Java EE.

- **O que é um Container de Servlets**: Um container de servlets, como o Tomcat, gerencia o ciclo de vida dos **servlets** — classes Java que respondem a requisições HTTP — e garante que as requisições sejam processadas corretamente. Ele oferece um ambiente seguro e eficiente para que as aplicações Java interajam com clientes web, utilizando tecnologias como **Servlets** e **JSP**.

#### **Funcionalidade do Tomcat**
O **Tomcat** oferece uma série de funcionalidades que o tornam uma escolha popular para o desenvolvimento de aplicações web baseadas em Java:

1. **Gerenciamento de Servlets**:
   - O Tomcat gerencia automaticamente o ciclo de vida dos servlets, incluindo:
     - **Instanciação**: Carrega e inicializa o servlet quando solicitado pela primeira vez ou durante a inicialização do servidor.
     - **Processamento de Requisições**: Garante que cada requisição HTTP seja entregue ao servlet apropriado e que uma resposta seja gerada corretamente.
     - **Gerenciamento de Sessões**: Lida com o estado entre requisições HTTP, utilizando técnicas como cookies e sessões para identificar e rastrear usuários.
     - **Controle de Requisições e Respostas**: O Tomcat gerencia a troca de informações entre o cliente e o servidor, organizando cabeçalhos HTTP, parâmetros de requisição e resposta, e o ciclo de vida das requisições HTTP.

2. **Suporte a JSP (JavaServer Pages)**:
   - O **Tomcat** também oferece suporte completo ao **JSP (JavaServer Pages)**, uma tecnologia que permite misturar código Java com HTML para gerar páginas web dinâmicas.
   - **Integração com Servlets**: O Tomcat converte páginas JSP em servlets, integrando-as diretamente ao ciclo de vida do servlet. Isso permite que páginas dinâmicas sejam geradas de forma eficiente com base em dados processados pelo servidor.
   - **Exemplo de Uso de JSP**: Um formulário em uma página JSP pode capturar dados de um usuário, processar esses dados com Java no backend e gerar uma página HTML dinâmica com o resultado.

3. **Gerenciamento de Aplicações Web**:
   - O Tomcat oferece uma interface administrativa (Tomcat Manager) que permite:
     - Implantação, monitoramento e gerenciamento de aplicações web.
     - Reinicialização e monitoramento do status de cada servlet ou JSP.
     - Verificação de logs e diagnóstico de problemas em aplicações.

4. **Suporte a Padrões Java EE**:
   - Embora o Tomcat seja considerado um **servidor de aplicação leve**, ele oferece suporte a uma série de padrões Java EE, como **Servlets**, **JSP**, **JNDI** (Java Naming and Directory Interface), e **Security Realms**.

#### **Exemplo Prático: Configuração do Tomcat e Deploy de um Servlet**

Aqui está um exemplo passo a passo para configurar o Tomcat, implementar um servlet simples e testá-lo:

##### **1. Instalação e Configuração do Tomcat**
- **Passo 1**: Baixe o **Apache Tomcat** da [página oficial](https://tomcat.apache.org/).
- **Passo 2**: Extraia o arquivo e instale o Tomcat.
- **Passo 3**: Inicie o Tomcat executando o script de inicialização (`startup.bat` no Windows ou `startup.sh` no Linux).
- **Passo 4**: Acesse o **Tomcat Manager** no navegador em `http://localhost:8080/manager/html` (as credenciais padrão podem ser configuradas no arquivo `tomcat-users.xml`).

##### **2. Criar e Implementar um Servlet Simples**
Crie um servlet simples que exibe uma mensagem de boas-vindas:

```java
import javax.servlet.ServletException;
import javax.servlet.annotation.WebServlet;
import javax.servlet.http.HttpServlet;
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;
import java.io.IOException;
import java.io.PrintWriter;

@WebServlet("/hello")
public class HelloServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<h1>Bem-vindo ao Servlet!</h1>");
    }
}
```

- **Explicação**: Esse servlet responde a requisições **GET** na URL `/hello`, retornando uma simples mensagem HTML "Bem-vindo ao Servlet!".

##### **3. Fazer o Deploy da Aplicação no Tomcat**
- **Passo 1**: Coloque o arquivo `HelloServlet.java` em um diretório de projeto que segue a estrutura padrão do **Maven** ou **Java EE**.
- **Passo 2**: Compile o código e empacote a aplicação em um arquivo **.war** (Web Application Archive).
- **Passo 3**: Copie o arquivo **.war** para a pasta `webapps/` do diretório do Tomcat.
- **Passo 4**: O Tomcat irá automaticamente fazer o deploy da aplicação. Acesse o servlet no navegador: `http://localhost:8080/hello`.

##### **4. Testar a Aplicação**
Abra o navegador e vá para `http://localhost:8080/hello`. O servlet deverá responder com uma página web simples contendo a mensagem: 

```
Bem-vindo ao Servlet!
```

#### **Atividade Prática: Configurar o Tomcat e Implementar um Servlet**
Para reforçar os conceitos, os alunos devem realizar a seguinte atividade:

1. **Configurar o Tomcat**:
   - Os alunos devem instalar o Tomcat em seus ambientes de desenvolvimento e testar o acesso à interface do Tomcat Manager.
   
2. **Implementar e Fazer o Deploy de um Servlet**:
   - Cada aluno deve criar um servlet simples que recebe parâmetros de uma requisição (como nome do usuário) e retorna uma mensagem personalizada.
   - Exemplo: Um servlet que receba um parâmetro `nome` via URL e exiba "Bem-vindo, [nome]!".

3. **Deploy e Testes**:
   - Fazer o deploy da aplicação no Tomcat e testar o servlet no navegador. 
   - Os alunos devem experimentar o ciclo completo de desenvolvimento, desde a criação do servlet até o deploy e teste no servidor.

---


### **8.Requisições GET e POST em Servlets**

#### **Definição de Requisições GET e POST**
- **GET**: Utilizado para solicitar dados de um servidor. Os parâmetros da requisição são passados na URL e visíveis para o usuário.
  - **Exemplo**: Quando acessamos uma URL com parâmetros como `https://site.com/search?query=java`, o navegador envia uma requisição GET ao servidor com a palavra-chave `java` como parâmetro.
  - **Limitações**: Limite de tamanho dos parâmetros na URL, dados expostos e menos seguros.
  - **Quando usar**: Para buscar dados ou acessar páginas de forma simples, sem necessidade de segurança ou grandes volumes de dados.

- **POST**: Utilizado para enviar dados ao servidor, geralmente para submissão de formulários. Os parâmetros são passados no corpo da requisição, invisíveis na URL.
  - **Exemplo**: Submeter um formulário de login, onde o nome de usuário e a senha são enviados de forma segura por meio de uma requisição POST.
  - **Vantagens**: Maior segurança em relação ao GET (os parâmetros não ficam expostos na URL) e suporte a envio de grandes volumes de dados.
  - **Quando usar**: Para operações que alteram o estado do servidor ou quando há dados sensíveis a serem enviados, como senhas.

#### **Diferenças Práticas entre GET e POST**
- **Visibilidade**: GET envia os dados pela URL, enquanto POST envia os dados no corpo da requisição.
- **Tamanho dos Dados**: GET tem restrição de tamanho, enquanto POST permite o envio de grandes quantidades de dados.
- **Idempotência**: GET é considerado idempotente, ou seja, o mesmo pedido pode ser repetido sem alterar o estado do servidor. POST, por outro lado, pode modificar o estado do servidor a cada requisição.

#### **Como Servlets Processam Requisições GET e POST**
Os **Servlets** têm dois métodos principais para processar essas requisições: 
- **doGet()**: Usado para tratar requisições GET.
- **doPost()**: Usado para tratar requisições POST.

Quando uma requisição HTTP chega ao servidor, o **Servlet Container** (como o Tomcat) decide qual desses métodos chamar, dependendo do tipo de requisição recebida.

#### **Exemplo Prático: Implementando GET e POST em Servlets**

1. **Requisição GET:**
```java
@WebServlet("/getExample")
public class GetExampleServlet extends HttpServlet {
    protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String name = request.getParameter("name"); // Captura o parâmetro da URL
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        out.println("<h1>Hello, " + name + "</h1>"); // Responde com HTML simples
    }
}
```
- **Descrição**: Quando acessada com a URL `http://localhost:8080/getExample?name=John`, este servlet captura o parâmetro `name` e responde com uma página HTML dizendo "Hello, John".

2. **Requisição POST:**
```java
@WebServlet("/postExample")
public class PostExampleServlet extends HttpServlet {
    protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
        String username = request.getParameter("username"); // Captura os dados enviados pelo formulário
        String password = request.getParameter("password");
        response.setContentType("text/html");
        PrintWriter out = response.getWriter();
        if ("admin".equals(username) && "admin123".equals(password)) {
            out.println("<h1>Login successful!</h1>");
        } else {
            out.println("<h1>Login failed!</h1>");
        }
    }
}
```
- **Descrição**: Este servlet captura os dados de um formulário de login (usuário e senha) enviados via POST. Se o usuário e senha forem válidos, responde com "Login successful!", caso contrário, responde com "Login failed!".

---
---


# Lista de Exercícios 01 - Prática com Servlets

### **1. Exibir uma Mensagem Simples**
**Objetivo**: Criar um servlet que responda a uma requisição HTTP GET com uma mensagem simples.

- **Descrição**: Implemente um servlet que, ao ser acessado, exiba a mensagem "Bem-vindo ao mundo dos Servlets!".
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: Método `doGet`, resposta HTML simples.

---

### **2. Capturar Parâmetros da URL**
**Objetivo**: Criar um servlet que capture parâmetros passados pela URL e os exiba na resposta HTML.

- **Descrição**: Crie um servlet que receba o nome do usuário via parâmetro da URL (e.g., `/welcome?nome=Joao`) e exiba "Olá, Joao!" na resposta HTML.
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: Método `doGet`, `HttpServletRequest`, captura de parâmetros.

---

### **3. Processar um Formulário com Método POST**
**Objetivo**: Criar um servlet que processe um formulário HTML enviado via método POST e retorne uma mensagem de boas-vindas.

- **Descrição**: Crie um formulário de login simples (apenas o campo de nome de usuário). Ao submeter o formulário, o servlet deve processar os dados e exibir "Bem-vindo, [usuário]!".
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: Método `doPost`, captura de parâmetros via POST.

---

### **4. Contador de Acessos (Armazenamento em Variável)**
**Objetivo**: Criar um servlet que conte quantas vezes ele foi acessado.

- **Descrição**: Implemente um servlet que mantenha um contador de acessos. Cada vez que o servlet for acessado, o contador deve ser incrementado e o número de acessos exibido na página.
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: Armazenamento em variável de instância, atualização de valores.

---

### **5. Armazenar Nomes em ArrayList via GET**
**Objetivo**: Criar um servlet que armazene os nomes enviados via parâmetro da URL em um `ArrayList`.

- **Descrição**: Crie um servlet que receba o nome do usuário via parâmetro da URL (e.g., `/addNome?nome=Maria`) e armazene o nome em um `ArrayList`. O servlet também deve exibir todos os nomes armazenados.
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: `ArrayList`, método `doGet`, manipulação de lista de dados.

---

### **6. Armazenar Comentários com POST e Exibir Comentários (ArrayList)**
**Objetivo**: Criar um servlet que receba comentários via POST e os armazene em um `ArrayList`.

- **Descrição**: Crie um formulário HTML para envio de comentários (via POST). O servlet deve processar os comentários, armazená-los em um `ArrayList`, e exibir todos os comentários submetidos.
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: `ArrayList`, método `doPost`, exibição de dados armazenados.

---

### **7. Contador de Acessos por Usuário (Armazenamento em Variável)**
**Objetivo**: Criar um servlet que conte quantas vezes cada usuário acessou a página.

- **Descrição**: Crie um servlet que receba o nome de um usuário via URL (e.g., `/acesso?nome=Ana`). Para cada usuário, mantenha um contador de acessos em uma variável ou estrutura simples. O servlet deve exibir quantas vezes cada usuário acessou a página.
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: Variáveis, manipulação de contadores por usuário.

---

### **8. Cadastro Simples de Produtos (Armazenamento em ArrayList)**
**Objetivo**: Criar um servlet que receba o nome e preço de produtos e os armazene em um `ArrayList`.

- **Descrição**: Crie um formulário HTML para cadastro de produtos (nome e preço). O servlet deve processar o formulário e armazenar os dados em um `ArrayList`. Quando acessado, o servlet deve listar todos os produtos cadastrados.
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: `ArrayList`, captura de múltiplos dados, exibição de lista de produtos.

---

### **9. Remover Nomes de um ArrayList via GET**
**Objetivo**: Criar um servlet que permita remover um nome armazenado no `ArrayList` via URL.

- **Descrição**: O servlet deve permitir que um nome seja removido do `ArrayList` quando passado como parâmetro na URL (e.g., `/removeNome?nome=Maria`). Após a remoção, todos os nomes restantes devem ser exibidos.
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: `ArrayList`, método `remove()`, manipulação de lista via GET.

---

### **10. Lista de Tarefas (To-Do List) com Armazenamento em ArrayList**
**Objetivo**: Criar um servlet que permita adicionar e visualizar tarefas de uma lista de tarefas.

- **Descrição**: Crie um formulário HTML para adicionar tarefas à lista de tarefas. O servlet deve processar o formulário, armazenar as tarefas em um `ArrayList`, e exibir todas as tarefas cadastradas. A página deve permitir que novas tarefas sejam adicionadas continuamente.
- **Dificuldade**: Baixa.
- **Conceitos Aplicados**: `ArrayList`, manipulação de lista dinâmica, formulário via POST.


