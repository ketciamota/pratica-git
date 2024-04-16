# pratica-git
Repositório para a prática de comandos do Git

git config --global core.editor "code --wait"
O comando acima define o Visual Studio Code como o editor padrão das mensagens de commit

git commit --allow-empty
O parâmetro --allow-empty permite a criação de um commit vazio, para fins de testes e prática do Git.

git commit -a 
O parâmetro -a adiciona todos os arquivos modificados e não ignorados ao commit atual.

git checkout -b novoBranch
git switch -c novoBranch
O parâmetro -b alterna para novoBranch criando o branch. o mesmo acontece com o comando git switch com o parâmetro -c.

git branch -D nomeBranch
git push --delete origin nomeBranch
Para apagar um branch é preciso primeiro apagá-lo localmente (1º comando) e depois propagar a deleção para o repositório remoto (2º comando).

~~~bash
git log --graph --online
~~~

O comando `log`exibe o histórico de commits em detalhe. Com as flags `--graph`e `--online`
exibe o histórico em um formato mais compreensível, atravé de grafo (grafo?)

###   Rebase interativo

Para alterar o autor de um commit, você pode utilizar o rebase interativo e o comando `commit --amend`

**Antes porém**, verifique se o editor de mensagem do commit est´=a configurado para o editor do próprio VS CODE.

~~~bash
git rebase -i <referenciaCommit>
~~~

No editor de commits, altere a instrução do commit desejado de `pick`para `edit`. Em seguida, grave e feche o editor. 

o rebase fará uma pausa para que vc altere as informções do autor.

~~~bash
git commit --amend --reset-author --no-edit
~~~

Caso vc queira especificar o autor, utilize a flag `--author="Nome do Autor <email@autor>"` neste exato formato.

Caso seu comit seja vazio, acrescente ainda a flag `--allow-empty`.

Após o reparo do commit, continue o processo do rebase com o comando abaixo.

~~~bash
git rebase --continue
~~~

Finalmente, **confira o novo histórico localmente** e envie ao repositorio remoto **forçadamente**.

~~~bash
git push --force
~~~
