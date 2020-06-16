# EC2 Management

EC2 Management é uma plataforma que visa expandir a gestão de [instâncias EC2](https://docs.aws.amazon.com/pt_br/AWSEC2/latest/UserGuide/ec2-instances-and-amis.html) (Elastic Compute Cloud) e [instâncias RDS](https://docs.aws.amazon.com/AmazonRDS/latest/UserGuide/Overview.DBInstance.html) criadas no ambiente [AWS (Amazon Web Services)](https://aws.amazon.com/pt/what-is-aws/).

EC2 Management ofecece funcionalidades que não estão presentes nos consoles EC2 e RDS padrões distribuídos pela AWS:

1. Agrupamento de instâncias, permitindo que uma ação seja aplicada sobre mais de uma instância ao mesmo tempo.
2. Agendamento para iniciar, parar e reiniciar um grupo de instâncias, permitindo otimizar o consumo de recurso e o custo para se manter instâncias em execução na AWS.

## Por que usar a EC2 Management?

É possível realizar o mesmo que as funcionalidades oferecidas pela EC2 Management utilizando os serviços oferecidos nativamente pela AWS?
A resposta é simples, sim. Já a implementação, talvez não tão simples assim...

### Um cenário de uso de instâncias EC2

Imagine o seguinte cenário, quatro instâncias EC2, uma executa aplicações utilizadas pelo setor de RH, uma executa aplicações utilizadas pelo setor financeiro, uma é um servidor que executa aplicações disponibilizadas para os seus usuários finais e uma gera relatórios de performance, gerência e BI.

Os colaboradores de sua organização trabalham de segunda a sexta, das 8h às 18h.
As aplicações em seu servidor precisam estar disponíveis aos seus usuários finais 24 horas nos 7 dias da semana.
As reuniões estratégicas que utilizam os dados dos relatórios acontecem apenas nas segundas-feiras.

No cenário descrito acima, apenas a instância EC2 que executa aplicações disponibilizadas para os seus usuários finais precisa executar 24 horas por dia.
As instâncias que executam aplicações para o RH e o financeiro precisam apenas estar ligadas durante o horário de expediente e a instância que gera os relatórios precisa ficar ligada por algumas horas no final de semana.

### Soluções alternativas

Podemos agrupar instâncias EC2 através do `AWS Resources Groups`.
Então, utilizar o `AWS Systems Manager Automation` ou `AWS Systems Manager Run Command` para realizar uma ação sobre esse grupo de instâncias ao mesmo tempo.

O `AWS OpsWorks` disponibiliza uma forma de agendar o ligar e desligar de instâncias EC2 que fazem parte de uma _OpsWorks Stack_ ou que possuem um _Chef cookbook_.
`AWS CloudWatch Event Rules` também podem ser utilizadas para implementar algo similar a jobs periódicos que enviarão comandos às instâncias EC2.

Além dos SDKs oferecidos para diversas linguagem de programação e as automações que podem ser feitas através de scripts e o AWS CLI.

As soluções altenativas apresentadas acima não são as únicas, fazendo uma busca pela Internet é possível encontrar outras. O problema comum em todas essas alternativas é: VOCÊ terá que criar, implementar e manter essas soluções em execução ou terá que ter alguém em seu time que possua o conhecimento sobre as ferramentas e serviços que mantem sua solução rodando.

Com a EC2 Management, apenas o administrador precisa ter um conhecimento mínimo sobre os serviços que a plataforma utiliza para interagir com a AWS, por exemplo, instâncias EC2 e o AWS IAM.
Grupos de instâncias e agendamentos são feitos através de uma interface gráfica Web, sem a necessidade de configurar manualmente cada serviço utilizado para suportar as funcionalidades oferecidas pela EC2 Management.

## Sobre este documento

Este documento é um tutorial para apresentar os primeiros passos para usuários que tem interesse em interagir com a plataforma EC2 Management. Para acessar a plataforma, basta clicar nesse [link](https://ec2management.infomach.com.br/login).

Caso seja sua primeira vez utilizando a plataforma EC2 Management, é recomendado que leia as seções na ordem que serão apresentadas, ou seja, primeiro a seção 1, depois a seção 2, então 3, etc.
Alguns passos em uma seção podem depender de passos realizados em seções anteriores, por exemplo, para criar um agendamento na seção 4 é necessário antes ter criado um ambiente na seção 3.

O tutorial está divido nas seguintes seções:

1. [Login](docs/login/LOGIN.md). Tela inicial onde se acessa uma conta já existente ou se cria uma nova conta.
2. [Configurações](docs/settings/SETTINGS.md). Onde se adiciona as permissões necessárias para que a plaforma EC2 Management possa manipular instâncias EC2 e RDS na AWS.
3. [Console](docs/console/CONSOLE.md). Painel para criar ambientes (grupos de instâncias) e realizar ações como, `"iniciar um ambiente"`.
4. [Agendamento](docs/scheduling/SCHEDULING.md). Onde se cria agendamentos para iniciar, parar ou reiniciar ambientes.
5. [Usuários](docs/users/USERS.md). Criação, edição e remoção de usuários e grupos de usuários na EC2 Management. Esses usuários são diferentes dos [usuários IAM](https://docs.aws.amazon.com/pt_br/IAM/latest/UserGuide/id_users.html) na AWS.
6. [Histórico](docs/history/HISTORY.md). Visualizar ações realizadas na plataforma EC2 Management, por exemplo, criar um usuário, criar um ambiente, deletar um agendamento, etc.

## Pré-requisitos para utilizar a plataforma EC2 Management

EC2 Management interage com serviços da AWS, logo, é necessário possuir uma conta na AWS ou um usuário IAM de uma conta AWS. Assim, caso ainda não possua sua conta, siga os passos na página oficial da AWS sobre como criar uma nova conta.

**Para cadastrar-se na AWS**

1. Abra https://portal.aws.amazon.com/billing/signup
2. Siga as instruções online.
   > Parte do procedimento de cadastro envolve uma chamada telefônica e a digitação de um código de verificação usando o teclado do telefone

Também é necessário possuir instâncias EC2 e/ou RDS já criadas, mas não é obrigatório estarem em execução. Para criar uma instância EC2 na AWS, siga os passos desse link:

> https://docs.aws.amazon.com/pt_br/AWSEC2/latest/UserGuide/EC2_GetStarted.html

## Próxima etapa

Acesse ou crie sua conta na plataforma EC2 Management. O passo a passo pode ser encontrado na [Seção 1 - Login](docs/login/LOGIN.md).

## Mande seu feedback!

Gostou da EC2 Management? Ajude-nos a melhorá-la!
Envie um e-mail para [prod@infomach.com.br](mailto:prod@infomach.com.br) e nos diga o que pode ser adicionado, melhorado ou corrigido na plataforma.

Envie também sua opinião sobre o tutorial disponibilizado. Se foi útil, o que poder ser melhorado e se contém erros de conceito ou ortográficos.
