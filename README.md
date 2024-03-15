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













