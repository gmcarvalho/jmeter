# jmeter

O Jmeter é um software open source, capaz de realizar testes de performance e carga. 

Suponha que você tenha um aplicativo e quer simular uma grande quantidade de usuários acessando ao mesmo tempo, ou analisar as métricas de tempo de resposta ou capacidade, pra isso estou aqui hoje, para te apresentar o Jmeter e algumas das suas funcionalidades. 
___
### Documentação

Esse é o [link](https://jmeter.apache.org/) da documentação, através dele você consegue baixar o software, e ver as funcionalidades disponíveis. 
___
### Baixando e rodando o software

Para baixar o binário, você pode clicar [nesse link](https://jmeter.apache.org/download_jmeter.cgi)

![download](https://github.com/gmcarvalho/jmeter/assets/33256112/814ca543-b43d-4b9a-8397-da061889b83a)


Após baixado, você vai descompactar no diretório desejado.

![descompactar](https://github.com/gmcarvalho/jmeter/assets/33256112/cc155e6f-9578-4e7e-a912-559017c55bbb)

Feito isso, para rodar o software, bastanta ir na pasta descompactada, ir em `bin > ApacheJMeter.jar` 
Ao clicar no Jar vai abrir a seguinte tela: 

![jmeter](https://github.com/gmcarvalho/jmeter/assets/33256112/421af5ac-914f-449c-9a4e-4a8a9fab4827)

___
### Primeiro teste 

Agora que você já está com tudo preparado, vou te mostrar a configuração mais simples pra começar a usar o Jmeter.
Para isso vamos criar um plano de teste, onde vamos chamar 3 requisições a 3 sites distintos, sendo eles: Amazon, Shopee, e Magazine Luiza. 

* 1º Passo - Adicionar uma Thread Group no Plano de Teste

![thread_group](https://github.com/gmcarvalho/jmeter/assets/33256112/e8127c90-06ac-405b-b664-79835defb5d9)


![Captura de Tela 2024-03-15 às 09 49 56](https://github.com/gmcarvalho/jmeter/assets/33256112/da290830-bff3-4e8d-b048-2732d6effac0)

2º Passo - Adicionar uma requisição Http na Thread Group

![request](https://github.com/gmcarvalho/jmeter/assets/33256112/b9080eb2-76e4-4d7d-8b7d-52130c58efe4)

Vamos adicionar 3 HttpRequest, uma para cada site que vamos requisitar. 

![Captura de Tela 2024-03-15 às 10 09 05](https://github.com/gmcarvalho/jmeter/assets/33256112/4fd21e37-eaf4-4ddd-b926-fcc753c381a5)

3º Passo Adicionar um Listener - Um listener coleta e exibe os resultados dos testes. 
Nesse teste adicionamos um `View Results Tree` e o `Summary Report`

![listener02](https://github.com/gmcarvalho/jmeter/assets/33256112/73379619-5b57-439e-bd9f-09d5b0b30f31)


![listener01](https://github.com/gmcarvalho/jmeter/assets/33256112/aeb566f2-9b4c-4e08-8dd4-ac907de4eb74)

4º Passo: Rodar o teste 

Ao clicar na seta verdinha, basta acompanhar os listener, para ver o resultado. 

Esse é o resultado de Summary report, nele você consegue ver as 3 amostras que foram solicitadas, bem como a média de requisição em milisegundos, throuput, taxa de erros, e outras informações. 

![resultado_summary](https://github.com/gmcarvalho/jmeter/assets/33256112/ab9344a2-a062-4690-a2fa-5d9722857d62)

Já esse abaixo é o resultado da árvore de resultados

![resultado_arvore](https://github.com/gmcarvalho/jmeter/assets/33256112/7c42132e-126d-481f-8aa9-03d5601f87c6)

___

### Vamos ao segundo teste

Quando fizemos o primeiro teste, ele é bem simples, mas simulando uma situação mais real, quando entramos num aplicativo, 
executamos várias outras ações, entramos em outras abas, fazemos filtro, executamos login, adicionamos produto ao carrinho, entre outras coisas. 
Isso é um exemplo, que pode ser abstraído e convertido também para o seu negócio. 

Com isso vamos modificar um pouco nosso plano de teste. Bora lá?! 

Perceba na imagem abaixo, que foi criado 3 Thread Groups, cada uma Thread Group possui uma configuração distinta. E o que isso quer dizer? 
Estou aqui tentando simular 3 perfis de usuários distintos, cada um está fazendo uma busca diferente, e adicionando um produto ao carrinho. 
Quando você quer tornar seu teste mais realista, é bom separar em mais Thread Groups, e fazer configurações distintas de cada perfil. 

![teste 2](https://github.com/gmcarvalho/jmeter/assets/33256112/86d0a672-c762-4f2d-9f9c-91691f7b1450)

Para essa primeira Thread Group, temos algumas configurações, agora vamos a algumas explicações. É só clicar na setinha abaixo, para expandir a esxplicação de cada opçao. 

<details>

<summary> Thread Groups </summary>


  Grupo de usuários virtuais que executam conjunto específico de requisições

</details>

<details>

<summary> Number of Threads (users) </summary>


  Qtde de usuários virtuais que serão criados dentro do grupo. Cada usuário do grupo simula um usuário real dentro da aplicação. Portanto o número de threads determina quantos usuários simultâneos estarão acessando a aplicação 
  durante o teste. Por exemplo, se você definir `Number Of Threads (users) como 100`, isso significa que 100 usuários virtuais estarão ativos simultaneamente durante o teste. 

</details>

<details>

  <summary> Rump-Up (seconds) </summary>
  

  Este campo define o tempo que o JMeter leva para iniciar todos os threads (usuários virtuais) dentro do grupo.
  
  Ele especifica o intervalo de tempo em que os threads são iniciados gradualmente até atingir o número total de threads definido no campo "Number of Threads".
  
  Por exemplo: 
  
  * Se você definir o `Ramp-up period` como 60 segundos e o `Number of Threads` como 100, isso significa que o JMeter levará 60 segundos para iniciar todos os 100 threads, 
  com uma taxa de aproximadamente 1,67 threads por segundo (100 threads / 60 segundos).
  
  * Se você definir o `Ramp-up period` como 10 segundos e o `Number of Threads` como 10, isso significa que o Jmeter levará 10 segundos para iniciar as 10 threads, ou seja, uma thread instanciada por segundo. (10 threads/ 10 segundos).
  

</details>

<details>

<summary> Loop Count </summary>


  Este campo define quantas vezes cada thread (usuário virtual) executará o conjunto de requisições dentro do grupo.
  
  Se definido como:
  
  * -1, cada thread executará indefinidamente até que o teste seja interrompido manualmente.
  * 0, não vai rodar nenhuma requisição
  * 1 ou +, vai executar o conjunto de requisições a quantidade de vezes atribuída.
  
  Ex: se você definir o `Loop count` como 5, cada thread executará o conjunto de requisições 5 vezes antes de encerrar sua execução.

</details>

<details>
  
<summary> Specify Thread Lifetime </summary>


  Caso você deseja deixar seu teste rodando por determinado tempo, ou infinitamente até que você o pause. Você pode configurar algo parecido com isso: 
  
  
  ![infinito](https://github.com/gmcarvalho/jmeter/assets/33256112/9c5cb26a-0498-4321-a374-104eec58ae2a)
  
  Nesse exemplo, foi configurado 2 threads de usuários que vão ser executadas simultaneamente, e que vão repetir suas requisições durante 5 minutos `Duration (seconds) = 300`. 
  O `loop count` nesse caso fica definido como infinito. 
  
  O `Startup delay (seconds)` define um delay para iniciar a requisição. 

</details>

___

### Otimizando algumas configurações

Se vocês perceberem na imagem abaixo, temos um `HTTP Request Defaults` na nossa 3ª Thrad Group. 

Essa configuração serve para quando algumas informações de request são as mesmas, e com isso ao invés de ficar configurando em todas as requsiições, você pode centralizar. 

Como fazer isso? 

<img width="780" alt="request_default" src="https://github.com/gmcarvalho/jmeter/assets/33256112/2308ca6d-bf19-4130-87b7-0a5ab366dd10">

Perceba, que você pode configurar tanto a request default, como também header, coockies e outras coisas. 

<img width="730" alt="request" src="https://github.com/gmcarvalho/jmeter/assets/33256112/106949ad-a7e9-44e3-95d7-ba70f9214d32">

Como o servidor é o mesmo, o método http, e o protocolo, foi centralizado na request defaults, não sendo necessário a configuração nas requests. Lá ficou apenas os paths que são diferentes. 

No caso do `HTTP Header Manager`, ele centraliza algumas coinfigurações de Header, veja um exemplo:

<img width="1453" alt="header" src="https://github.com/gmcarvalho/jmeter/assets/33256112/d3696c10-5bcd-45ef-bf7d-674c71a8daa6">

Se você for fazer um método post por exemplo, e necessite adicionar um token de autorização, pode fazê-lo nessa configuração de Header. 

___

### Teste global e métricas

<img width="1783" alt="teste" src="https://github.com/gmcarvalho/jmeter/assets/33256112/3859425d-4c04-4168-b54c-ff0535813493">

Perceba nessa imagem acima, que temos Listeners `View Result Tree` e `Summary Report` em cada Thread Group, o que resulta em métricas apenas desse grupo específico, 
mas temos uma atrelada ao Plano de Teste `View Result in Table` que vai metrificar o resultado de todos os grupos. 

Isso é só para mostrar que cosneguimos testar isolado e também de forma gloral todas as threads de usuários. 

Nesse resultado do teste tivemos 10 amostras, que corresponde a todas as requests que criamos. 

___

### O 3º teste 

Nesse teste foi configurado um time de 5 minutos em cada Thread Group `Duration (seconds) = 300`

<img width="1789" alt="teste2" src="https://github.com/gmcarvalho/jmeter/assets/33256112/a350a426-5268-4eb0-8438-8bede49f1ca4">

COnfigurações para cada Thread Group com:

* Number Of Threads (users) = 1
* Ramp-up (seconds) = 1
* Loop Count = Infinite
* Same user on each interation marcado
* Duration (seconds) = 300

Perceba que ao rodar durante esses 5 minutos, algumas requisições apresentaram falha com erro 503, e por isso contem já a taxa de erro nas métricas. 

___ 

### O 4º teste - Startando grupos de forma simultânea, e aumentando a qtde de thread of number em cada grupo para 2

Nesse teste foi aumentado o número de thrads virtuais por grupo de usuários, e adicionado um temporizador para iniciar 3 Thread Groups simultaneamente. 

As seguintes configurações foram feitas: 

Desmarcamos a opção de rodar as Threads Groups de forma consecutiva
<img width="1448" alt="desmarcando_conseqcutivo" src="https://github.com/gmcarvalho/jmeter/assets/33256112/e1a629f3-2fee-4f8c-84e7-10d1a2d0c854">

Adicionamos um sincronizador

<img width="676" alt="sincronizador" src="https://github.com/gmcarvalho/jmeter/assets/33256112/5d68da73-67e5-4ff2-9ad7-cc6aaafcfb40">

Agora só está habilitado uma requisição por grupo, para ficar mais fácil a demonstração. 

Cada Thread Group está configurado da seguinte forma: 

<img width="636" alt="thrad" src="https://github.com/gmcarvalho/jmeter/assets/33256112/46e4deda-8b56-41be-b2c5-979ad2547dda">

* Number of Threads = 2
* Rumpo-up (seconds) = 2
* Loop Count = 1

Ou seja, serão instanciados 2 usuários virtuais por grupo, dentro de 2 segundos (uma thread groupo por segundo) 
A requisição de cada usuário vai rodar uma vez. 

O Synchronizing Times foi configurado com: 


<img width="730" alt="sync" src="https://github.com/gmcarvalho/jmeter/assets/33256112/dfb4638a-399d-4aa1-b68d-0e00b22c5e7d">

* Number of simulated Users to Group by = 4
* Timeout in milisegundos = 0

<details>

<summary> O que significa essa configuração do tempo de sincronização?  </summary>

  * No `Synchronizing Timer`, você pode definir o número de threads que precisam estar prontas para continuar. 
  Por exemplo, se você definir esse número como 4, isso significa que todas as 4 Thread Groups precisarão estar prontas para que qualquer uma delas continue.

  * Você pode definir um tempo limite de espera para o sincronismo. Isso especifica quanto tempo o JMeter aguardará antes de avançar, mesmo que o número necessário de threads não tenha sido alcançado. 
  Se você quiser que todas as suas Thread Groups iniciem ao mesmo tempo, você pode definir esse tempo limite de espera como zero, para garantir que o teste não avance até que todas as 4 Thread Groups estejam prontas.

  * Coloque o `Synchronizing Timer` antes das suas Thread Groups no plano de teste, para garantir que ele seja executado antes do início das Thread Groups.

</details>


Resultado: 

<img width="1781" alt="result" src="https://github.com/gmcarvalho/jmeter/assets/33256112/1b06e5e6-40c2-468b-ae30-133d6d5cbf89">


Conforme as explicações acima, observe que quando configurado um temporizador, para esperar 4 thread groups estarem prontas para iniciar, tivemos os 4 grupos iniciando ao mesmo tempo. 
Isso serve, para quando for testar sua aplicação, você pense em cada detalhe, quantas Threads Groups, ou seja perfis distintos, você deseja que inicie simultaneamente, ou em quanto tempo de delay um vai começar, 
se você quer que eles sejam chamados de forma consecutiva, e assim por diante. 

Outro detalhe é que, agora que temos 8 thread groups, cada um instanciando 2 usuários virtuais, e também tendo uma só requisição por grupo, dá pra ver que 14 amostras foram feitas. 
É importante observar esse número quando estiver rodando mais requisições, com mais usuários visrtuais, pra extrair métricas que fazem sentido, se atentando a esses pontos de configuração. 

As métricas de tempo de carregamento, latência, tempo de resposta, tempo de conexão, isso tudo vai servir para entender melhor como seus serviços estão funcionando e respondendo, podendo juntamente aos testes avaliar como sua máquina está operando, como está o tempo de resposta das suas requisições e então traçar melhorias para reduzir se for necessário, entre outras coisas. 

O Jmeter tem muitos recursos, controladores lógicos, outros tipos de temporizadores, tem plugin com mais gráficos e métricas, então é importante entender o básico e ir procurando por mais recursos se necessário. 

___

No diretório vai ter alguns arquivos de plano de teste, se baixá-los é possível reutilizar no seu jmeter. 






