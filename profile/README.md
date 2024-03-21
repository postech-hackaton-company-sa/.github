# Hackaton Company SA

A Hackaton Company SA, uma empresa de grande porte com mais de 100.000 colaboradores e que atende diversas áreas, inclusive tecnologia, está em um ponto de transição crucial.

## To do list



## Ponto Eletrônico

<p align="center">
  <img src="https://github.com/postech-hackaton-company-sa/.github/blob/main/profile/logo-ponto-eletronico.png?raw=true" />
</p>

<p align="justify">
  O uso de microserviços em vez de uma abordagem monolítica foi uma decisão estratégica crucial para a Hackaton Company SA, especialmente considerando sua magnitude com mais de 100.000 colaboradores. Compreendendo a necessidade de escala horizontal para acomodar esse volume de usuários, optou-se por uma arquitetura distribuída. A escalabilidade é fundamental para garantir que o sistema possa crescer de forma flexível e eficiente à medida que a empresa expande. Além disso, a arquitetura de microserviços permite uma maior modularidade e independência entre os componentes do sistema, o que facilita o desenvolvimento, implantação e manutenção contínua. Dessa forma, a empresa pode iterar mais rapidamente, implementar melhorias e responder de forma ágil às demandas em evolução do negócio e dos usuários. Essa abordagem também oferece a flexibilidade necessária para integrar novas funcionalidades e serviços conforme necessário, mantendo a coesão e a robustez do sistema como um todo.
</p>

### Arquitetura AWS

<p align="center">
  <img src="https://github.com/postech-hackaton-company-sa/.github/blob/main/profile/aws-mvp1.svg?raw=true" width="80%"/>
</p>

| Projeto                   | Cobertura de Código SonarCloud |
|---------------------------|--------------------------------|
| [postech-hackaton-ponto-eletronico](https://github.com/postech-hackaton-company-sa/postech-hackaton-ponto-eletronico) | [![Coverage](https://sonarcloud.io/api/project_badges/measure?project=postech-hackaton-company-sa_postech-hackaton-ponto-eletronico&metric=coverage)](https://sonarcloud.io/summary/new_code?id=postech-hackaton-company-sa_postech-hackaton-ponto-eletronico) |
| [postech-hackaton-relatorios](https://github.com/postech-hackaton-company-sa/postech-hackaton-relatorios) | Not yet |
| [postech-hackaton-funcionarios](https://github.com/postech-hackaton-company-sa/postech-hackaton-funcionarios) | Not yet |

<p align="justify">
  A escolha de uma solução pensada para a AWS, com diversos componentes integrados, foi motivada por uma série de razões estratégicas e técnicas. O uso do <code>API Gateway</code> para receber as requisições oferece uma camada de segurança e controle de acesso eficaz, além de possibilitar a fácil escalabilidade do sistema conforme necessário. O emprego do Lambda para realizar as autenticações no <code>Cognito</code> garante uma autenticação segura e eficiente dos usuários, aproveitando os serviços de gerenciamento de identidade da AWS.
</p>
<p align="justify">
  A utilização de um <code>VPN link</code> conectando-se ao <code>Load Balancer</code> é crucial para garantir uma comunicação segura e confiável entre os componentes internos do sistema. O <code>Load Balancer</code>, por sua vez, distribui o tráfego de forma equilibrada entre os três componentes principais do cluster interno.
</p>
<p align="justify">
  No que diz respeito aos bancos de dados, a escolha de utilizar tanto um banco de dados relacional (<code>RDS</code>) quanto um banco de dados NoSQL (<code>DocumentDB</code>) está alinhada com as necessidades específicas de cada componente do sistema. O <code>RDS</code> é ideal para o gerenciamento das contas de funcionários devido à sua estrutura organizada e capacidade de realizar consultas complexas e transações seguras. Por outro lado, o <code>DocumentDB</code> é utilizado para o registro do ponto eletrônico devido à sua capacidade de escalar horizontalmente e lidar com grandes volumes de dados de forma eficiente. Além disso, o <code>DocumentDB</code> também é acessado pelo Lambda de geração de relatórios
</p>

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



### Melhorias futuras

- [ ] A depender do volume de consultas talvez faça sentido alterar o serviço postech-hackaton-posto-eletronico para uma arquitetura CQRS.

### MVP 2

#### Arquitetura

<p align="center">
  <img src="https://github.com/postech-hackaton-company-sa/.github/blob/main/profile/aws-mvp2.svg?raw=true" width="120%"/>
</p>

-> Explicacao
