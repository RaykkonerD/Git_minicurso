### Trabalhando com branches

Para criar essas ramificações (branches) existem alguns comandos. Tais como:

```bash
git branch 01_branch 
# 01_branch é a ramificação nova que você quer.
# ou pode ser.
git checkout -b 01_branch
# deste modo, ele cria a branch.
git branch -a
#para listar as branchs que existem no seu repositório.
```

Note que a branch em que estamos está em verde, a branch que foi criada localmente está em branco e a branch remota está em vermelho. Se fizermos a branch pelo comando git branch,depois temos que ir para ela através de outro comando, que é o:

```bash
git checkout 01_branch
#01_branch é a branch que você quer ir
```

Após esse comando, estaremos na branch que desejamos. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/edc23054-2195-48bc-ab53-34f70e4d7cb6/Untitled.png)

Agora você poderá fazer qualquer alteração nessa branch.

Quando concluir a tarefa e for o momento de enviar para seu repositório local, terá de fazer o mesmo processo de add, commit e push. Só que na parte do push, se fizer apenas o git push, vai da errado de primeira, pois você não alocou a branch no seu repositório online. Entretanto, na mensagem de erro já vai mostrar o comando certo para configurar o push pela primeira vez. 

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3c9c81cc-bbdd-4f1f-8625-3645defd013e/Untitled.png)

No nosso caso, o comando a ser feito é:Ao executar esse comando, iremos alocar as modificações no repositório remoto dentro da ramificação “01_branch”.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/09843110-770c-4ab8-aa1f-3da502a4157d/Untitled.png)

Para problematizar, temos o seguinte caso:

Já terminamos de desenvolver algo nessa nova branch e queremos fazer com que o código dela vá para a main. Como fazer?

Temos um comando para mesclar um branch com a outra, ou seja, juntar todas as modificações. O comando é:

```bash
git merge <branch>
```

Seguindo com isso, para juntar a nossa branch com a main, temos que ir para nossa branch main.

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/52cae58d-c710-46d5-9e05-707ef37f195f/Untitled.png)

Após isso fazemos nosso merge.Depois disso, para salvar nossas alterações no repositório online, devemos fazer o git push. (Como mostrado no git status, a nossa branch main está diferente da main do repositório online, então devemos fazer um git push para mandar nossas alterações).

![Untitled](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f9bdb358-3d80-4870-aebc-097047ae25bc/Untitled.png)

Com isso, podemos verificar que os arquivos que estavam na branch 01_branch, agora está na main.Atualizando Branch
Para fechar a parte de comandos básicos no git, vamos para a parte de atualizar a branch local com as ultimas alterações do código. Os comandos responsáveis por isso são:
git pull
# ou 
git fetch origin <branch>
git merge FETCH_HEAD
​
O git pull vai fazer a comparação dos dados que estão localmente e online, e colocar no local as partes que não estiver de acordo com a do online. 
Já o git fetch origin <branch> vai buscar a branch que você quer, fazer uma comparação entre a branch que você está e a que ele está olhando no remoto, e após isso ele irá salvar as diferenças em um estado de commit em FETCH_HEAD. Dessa maneira, se torna interessante se você quer fazer uma verificação antes de pegar as alterações da branch. 
Para verificar as diferenças entre a sua branch e o FETCH_HEAD temos o comando:
# Comparar duas branch
git diff <branch> <branch>
# ou se voce quiser saber a diferença entre a branch que voce está e o ultimo push que fez
git diff <branch_remota>
# comparar com o FETCH_HEAD
git diff FETCH_HEADMais comandos
O comando git log apresenta os detalhes das branches, com cada uma das ramificações e commits realizados nela.
git log
​
Automatização dos comandos de push e pull - Trabalhando com node
A automatizaçao é um para fazer tudo que foi dito aqui como básico de maneira mais generalizada, um exemplo é o commit que sempre vai ter como mensagem “refresh”. Mas vai funcionar bem para a parte de mandar os dados e limpar suas credenciais da máquina.
Essa automatização se dá por conta da suas credenciais, se você não estiver usando seu pc pessoal, você não quer que as suas credenciais fiquem salvas no pc do laboratório por exemplo. 
Para resolver isso existe o comando:
git credential reject
# esse comando vai receber 2 paramentros por linha de comando após sua iniciacao, que é o
# protocol e host
​
Uma aplicação prática desse comando é:
```bash
git credential reject
protocol=https
host=github.com
```

Essa automatização é para que não se preocupe com a parte de fazer um add, commit, pull e push toda vez que tiver terminado o desenvolvimento. Para que isso seja feito, basta você ir no package.json do seu projeto, e na parte de “scripts” adicionar a seguinte linha:

```json
"git-push": "git pull && git add . && git commit --message 'refresh' && git push && echo digite o protocol e o host: && git credential reject"
```

Como exemplo, executando esse comando no projeto de aprendizagem que criei, vamos ter o seguinte resultado:

- Para executar esse comando via npm, precisamos fazer:

```bash
npm run git-push
```Com um adendo muito importante. A parte de digitar o protocol e host, o protocol geralmente vai ser https, mas o host pode ser github.com ou gitlab.com, vai depender do seu local de desenvolvimento. (Como na monitoria estamos utilizando o git lab, entao o host sempre vai ser gitlab.com)
