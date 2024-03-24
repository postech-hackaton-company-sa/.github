# Hackaton Company SA

A Hackaton Company SA, uma empresa de grande porte com mais de 100.000 colaboradores e que atende diversas áreas, inclusive tecnologia, está em um ponto de transição crucial.

| Projeto                   | Cobertura de Código SonarCloud | Pipeline status |
|---------------------------|--------------------------------| ------ |
| [postech-hackaton-ponto-eletronico](https://github.com/postech-hackaton-company-sa/postech-hackaton-ponto-eletronico) | [![Coverage](https://sonarcloud.io/api/project_badges/measure?project=postech-hackaton-company-sa_postech-hackaton-ponto-eletronico&metric=coverage)](https://sonarcloud.io/summary/new_code?id=postech-hackaton-company-sa_postech-hackaton-ponto-eletronico) | ![Pipeline](https://github.com/postech-hackaton-company-sa/postech-hackaton-ponto-eletronico/actions/workflows/pipeline.yml/badge.svg)
| [postech-hackaton-relatorios](https://github.com/postech-hackaton-company-sa/postech-hackaton-relatorios) | [![Coverage](https://sonarcloud.io/api/project_badges/measure?project=postech-hackaton-company-sa_postech-hackaton-relatorios&metric=coverage)](https://sonarcloud.io/summary/new_code?id=postech-hackaton-company-sa_postech-hackaton-relatorios) | ![Pipeline](https://github.com/postech-hackaton-company-sa/postech-hackaton-relatorios/actions/workflows/pipeline.yml/badge.svg) |
| [postech-hackaton-funcionarios](https://github.com/postech-hackaton-company-sa/postech-hackaton-funcionarios) | [![Coverage](https://sonarcloud.io/api/project_badges/measure?project=postech-hackaton-company-sa_postech-hackaton-funcionarios&metric=coverage)](https://sonarcloud.io/summary/new_code?id=postech-hackaton-company-sa_postech-hackaton-funcionarios) | ![Pipeline](https://github.com/postech-hackaton-company-sa/postech-hackaton-funcionarios/actions/workflows/pipeline.yml/badge.svg) |
| [postech-hackaton-apigateway](https://github.com/postech-hackaton-company-sa/postech-hackaton-apigateway) | [![Coverage](https://sonarcloud.io/api/project_badges/measure?project=postech-hackaton-company-sa_postech-hackaton-apigateway&metric=coverage)](https://sonarcloud.io/summary/new_code?id=postech-hackaton-company-sa_postech-hackaton-apigateway) | ![Pipeline](https://github.com/postech-hackaton-company-sa/postech-hackaton-apigateway/actions/workflows/pipeline.yml/badge.svg) |

## Ponto Eletrônico

<p align="center">
  <img src="https://github.com/postech-hackaton-company-sa/.github/blob/main/profile/logo-ponto-eletronico.png?raw=true" />
</p>

## Escolha arquitetural

<p align="justify">
  O uso de microserviços em vez de uma abordagem monolítica foi uma decisão estratégica crucial para a Hackaton Company SA, especialmente considerando sua magnitude com mais de 100.000 colaboradores. Compreendendo a necessidade de escala horizontal para acomodar esse volume de usuários, optou-se por uma arquitetura distribuída. A escalabilidade é fundamental para garantir que o sistema possa crescer de forma flexível e eficiente à medida que a empresa expande. Além disso, a arquitetura de microserviços permite uma maior modularidade e independência entre os componentes do sistema, o que facilita o desenvolvimento, implantação e manutenção contínua. Dessa forma, a empresa pode iterar mais rapidamente, implementar melhorias e responder de forma ágil às demandas em evolução do negócio e dos usuários. Essa abordagem também oferece a flexibilidade necessária para integrar novas funcionalidades e serviços conforme necessário, mantendo a coesão e a robustez do sistema como um todo.
</p>

### Arquitetura AWS

<p align="center">
  <img src="https://github.com/postech-hackaton-company-sa/.github/blob/main/profile/aws-mvp1.svg?raw=true" width="80%"/>
</p>

<p align="justify">
  A escolha de uma solução pensada para a AWS, com diversos componentes integrados, foi motivada por uma série de razões estratégicas e técnicas. O uso do <code>API Gateway</code> para receber as requisições oferece uma camada de segurança e controle de acesso eficaz, além de possibilitar a fácil escalabilidade do sistema conforme necessário. O emprego do Lambda para realizar as autenticações no <code>Cognito</code> garante uma autenticação segura e eficiente dos usuários, aproveitando os serviços de gerenciamento de identidade da AWS.
</p>
<p align="justify">
  A utilização de um <code>VPN link</code> conectando-se ao <code>Load Balancer</code> é crucial para garantir uma comunicação segura e confiável entre os componentes internos do sistema. O <code>Load Balancer</code>, por sua vez, distribui o tráfego de forma equilibrada entre os três componentes principais do cluster interno.
</p>
<p align="justify">
  No que diz respeito aos bancos de dados, a escolha de utilizar tanto um banco de dados relacional (<code>RDS</code>) quanto um banco de dados NoSQL (<code>DocumentDB</code>) está alinhada com as necessidades específicas de cada componente do sistema. O <code>RDS</code> é ideal para o gerenciamento das contas de funcionários devido à sua estrutura organizada e capacidade de realizar consultas complexas e transações seguras. Por outro lado, o <code>DocumentDB</code> é utilizado para o registro do ponto eletrônico devido à sua capacidade de escalar horizontalmente e lidar com grandes volumes de dados de forma eficiente. Além disso, o <code>DocumentDB</code> também é acessado pelo Lambda de geração de relatórios
</p>
<p align="justify">
  Embora não estejam representadas no diagrama arquitetural, outras ferramentas de monitoramento disponibilizadas pela AWS, como o <code>CloudWatch</code> para monitoramento de logs, métricas e alarmes, e o <code>AWS X-Ray</code> para análise de desempenho e depuração de aplicativos, serão utilizadas em todos os serviços. Essas soluções adicionais são essenciais para garantir o monitoramento contínuo da saúde e do desempenho do sistema, bem como para identificar e solucionar problemas rapidamente.
</p>

### Configurações importantes

Para atender aos requisitos não funcionais definidos, adotaremos várias estratégias e práticas utilizando as ferramentas disponíveis na AWS e Kubernetes:

**Desempenho:**

Utilizaremos o Kubernetes para escalar horizontalmente os serviços conforme a demanda. Durante os horários de pico identificados, como 9h, 12h, 14h e 18h, configuraremos políticas de escalabilidade automática para aumentar o número de réplicas dos serviços, garantindo que o sistema possa lidar com o aumento repentino de tráfego.

**Escalabilidade:**

O Kubernetes proporcionará uma arquitetura escalável, permitindo que novos nós sejam adicionados automaticamente ao cluster para acomodar o crescimento da empresa. A utilização de contêineres e serviços gerenciados pela AWS, como o Amazon <code>EKS</code>, simplificará a escalabilidade do sistema sem a necessidade de alterações significativas na arquitetura.

**Disponibilidade:**

Configuraremos estratégias de alta disponibilidade no Kubernetes, garantindo que os serviços estejam operacionais 24/7. Utilizaremos recursos como balanceamento de carga, replicação de pods e distribuição geográfica dos nós para garantir a resiliência do sistema. Além disso, implementaremos monitoramento contínuo com ferramentas como o AWS CloudWatch para detectar e mitigar falhas rapidamente.

**Segurança:**

Adotaremos as melhores práticas de segurança da AWS e do Kubernetes para proteger os dados dos usuários. Isso inclui o uso de criptografia de dados em repouso e em trânsito, autenticação forte e autorização granular. Faremos uso de serviços como AWS Identity and Access Management (IAM) para controlar o acesso aos recursos.

**Integridade dos Dados:**

Utilizaremos bancos de dados gerenciados pela AWS, como Amazon RDS e Amazon DocumentDB, que garantem a integridade dos dados por meio de replicação, backups automáticos e recuperação em caso de falhas.

**Manutenibilidade:**

Adotaremos práticas de DevOps, como CI/CD (Continuous Integration/Continuous Deployment), para garantir uma entrega contínua de código.

**Resiliência:**

Configuraremos estratégias de recuperação de falhas no Kubernetes, como a reinicialização automática de pods e a recuperação de nós. 

### Pipeline
<p align="center">
<img src="https://github.com/postech-hackaton-company-sa/.github/blob/main/profile/image.png?raw=true" />
</p>

<p align="justify">
  Primeiro, o job "check" é acionado quando ocorre um push no repositório ou manualmente. Nesse ponto, o ambiente Java com JDK 17 é configurado e os pacotes SonarCloud e Gradle são gerenciados em cache. O projeto é construído e analisado utilizando o Gradle, e os resultados são enviados para o SonarCloud. Em seguida, o job "build" é executado apenas se houver um push na branch principal (main) e se o job "check" for concluído com sucesso. Aqui, a imagem Docker do aplicativo é criada e publicada no Docker Hub, com base no hash do commit mais recente. Por fim, o job "deploy" é acionado nas mesmas condições do "build" e após a conclusão bem-sucedida do job "build". Esse job simula a atualização do aplicativo na EC2, onde a imagem mais recente é puxada do Docker Hub, o contêiner antigo é removido (simulado), um novo contêiner Docker é executado (simulado) e são realizadas etapas simuladas de limpeza.
</p>

### Arquitetura com docker-compose

<p align="center">
  <img src="https://github.com/postech-hackaton-company-sa/.github/blob/main/profile/mvp1-arquitetura-dockercompose.svg?raw=true"/>
</p>

Uma primeira abordagem foi criada com a utilizacao de puramente Docker. Esta solucao pode ser usada com o arquivo presente no arquivo [docker-compose](./../infra/docker-compose.yaml) da pasta `infra`.

O fluxo dos dados se assemelha com a solucao proposta para a AWS, sem toda a seguranca e comodidade da cloud. O usuario deve realizar o login atraves do KeyCloak e uma vez que tenha o JWT ele pode realizar a chamada dos demais servicos e, a depender da role do usuario, ele conseguira ou nao obter os dados que deseja, ou realizar as acoes.

Ao inves do servico de envio de email da AWS SES, optou-se por uma abordagem mais primitiva, com o uso integrado da biblioteca `JavaMailSender` no servico de relatorios.

#### Como rodar a aplicação

Para rodar um Docker Compose localmente, siga os seguintes passos:

1. Certifique-se de ter o Docker e o Docker Compose instalados em sua máquina. Você pode instalá-los seguindo as instruções oficiais do Docker para seu sistema operacional.
2. Baixe o arquivo docker-compose.yaml do repositório no GitHub. O link do arquivo se encontra neste [link](https://github.com/postech-hackaton-company-sa/.github/blob/main/infra/docker-compose.yaml).
3. Abra um terminal e navegue até o diretório onde o arquivo docker-compose.yaml foi baixado.
4. Execute o comando docker-compose up para iniciar os serviços definidos no arquivo docker-compose.yaml. Isso irá construir e iniciar todos os contêineres Docker conforme definido no arquivo.
5. Aguarde até que todos os contêineres sejam iniciados. Você verá mensagens de log indicando o status de inicialização de cada serviço.
6. Depois que todos os serviços estiverem rodando, você poderá acessá-los conforme necessário.

Para parar os serviços, pressione Ctrl + C no terminal onde o docker-compose up está sendo executado e, em seguida, execute docker-compose down para desligar e remover todos os contêineres.

### Melhorias futuras

- [ ] A depender do volume de consultas talvez faça sentido alterar o serviço postech-hackaton-posto-eletronico para uma arquitetura CQRS.
- [ ] Realizar uma analise de seguranca com OWASP ZAP


### MVP 2

#### Arquitetura

<p align="center">
  <img src="https://github.com/postech-hackaton-company-sa/.github/blob/main/profile/aws-mvp2.svg?raw=true" width="120%"/>
</p>

<p align="center">
  Para o segundo MVP da nossa solução, estamos expandindo ainda mais as capacidades do sistema, adicionando dois novos serviços essenciais: o Serviço Administrativo e o Serviço de Notificações.
</p>

<p align="center">
  O Serviço Administrativo tem como função principal aprovar ou recusar edições nos registros de ponto eletrônico solicitadas pelos funcionários. Essas solicitações são encaminhadas ao administrador, que pode revisá-las e tomar a ação apropriada. A comunicação entre o Serviço Administrativo e os funcionários será realizada por meio de mensagens usando a solução da AWS <code>SNS</code> e <code>SQS</code>, garantindo uma comunicação eficiente e confiável.
</p>
<p align="center">
  Por sua vez, o Serviço de Notificações trabalhará em estreita colaboração com o Serviço de Pontos Eletrônicos, utilizando também mensagens para se comunicar. Isso permitirá que o Serviço de Notificações saiba quase em tempo real quando um funcionário registra seu ponto, evitando assim o envio de notificações erradas ou desatualizadas aos funcionários. Além disso, o Serviço de Notificações usará a solução da AWS chamada <code>AWS Batch</code> para realizar um dump dos dados dos funcionários fora do horário comercial para sua base de dados local. Essa abordagem é necessária devido ao grande volume de funcionários e garante uma manipulação eficiente e escalável dos dados.
</p>
