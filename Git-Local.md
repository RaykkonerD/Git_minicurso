## Git

O Git é um sistema de controle de versão distribuído e amplamente adotado.


## Git local

### Iniciando Git

```bash
git init
```

Ele é responsável por transformar uma pasta em repositório git, cria seu repositório local. Lembre que é aconselhável criar uma nova pasta para seu repositório e só depois depois executar esse comando.

### Alocando um repositório remoto

```bash
git remote add origin <servidor>
```

Ao executar este comando, o seu repositório local será conectado a um repositório remoto (online). O parâmetro servidor deve ser uma URL para o repositório remoto.

### Outra maneira de fazer a inicialização
Primeiro temos que fazer um repositório online. Depois desse passo, chegamos na tela de instruções:

Depois disso, podemos pegar a url e colocar no clone do git, para que o git salve esse repositório como local na nossa maquina, ou seja, ele vai ser tanto online quanto local. O comando para isso é:
git clone <url>

### Fazendo add, commit e push

Comandos:

- Para adicionar um arquivo na área de estado:

```bash
git add <arquivo> ou git add .
```

- Para fazer commit:

```bash
git commit ou git commit -m “Titulo da mensagem do commit”
```

- Para enviar para o repositório remoto:

```bash
git push 
```

Esses são os três comandos que rotineiramente utilizaremos para atualizações nos repositórios. O git add vai adicionar os arquivos na área de estado. O git commit vai referencia-los e nomear as modificações, como também dizer quem alterou e outros dados. E por ultimo o git push é responsável por mandar para o repositório remoto.
