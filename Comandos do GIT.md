# 💻 Comandos no GIT

<details>

<summary> Manipulação de diretório e arquivos </summary>

- Cria uma pasta chamada curso no diretório atual
	```
	mkdir curso
	```

- Cria os arquivos 'aula1.txt' e 'aula2.txt' na pasta 'curso'
	```
	touch curso/aula1.txt curso/aula2.txt
	```

- Mostra o contéudo de um arquivo
	```
	cat 'nome do arquivo'
	```
</details>

<details>

<summary> Comandos Básicos </summary>


- Inicia o git

	```
	git init
	```	 

- Mostra o status do arq, alterações, inclusões e exclusões

	``` 
	git status
	```

- Prepara o "nome do arq" para ser adicionado no próximo commit 

	```
	git add "nome do arq" 
	```
	
- Prepara todos os arquivos para serem adicionados no próximo commit 

	``` 
	git add .
	```

- Retira um arquivo da area de preparação

	``` 
	git reset nome_arquivo
	```
	ou usando o 

	``` 
	git restore --staged nome_arquivo
	```
	
- Cria um commit com todas as modificações que foram incluidas

	```
	git commit -m "mensagem dq foi feito nessa alteração"
	```
	
- Configuração do git para indentificar quem está fazendo o commit

	``` 
	git config --global user.email "email"
	git config --global user.name "nome que aparecera nos commits"
	```

- Configuração para onde (qual repositorio/branch) enviar os commit

	``` 
	git remote add origin "link do repositorio"
	```

	Configura a branch padrão para mandar os commits	
	```
	git push --set-upstream origin "nome da branch" 
	```
	

- __**Acho**__  que configura o branch como padrão para o pull

	```
	git pull --set-upstream origin "nome da branch" 
	```

- __**Acho**__  que configura o branch como padrão para o push (pois o comando git push --set-up... para de funcionar)	

	``` 
	git push origin HEAD:Pesquisas
	```		

- Envia o commit para o repositório

	``` 
	git push 
	```
	
- Mostra o histórico das alteração nas versões: O último commit é a versão do topo com "HEAD@{0}:"

	``` 
	git reflog
	```
	
- Permite restaurar a um commit anterior usando o seu código como indentificação. Esse codigo é os primeiros 7 digitos da linha do commit

	``` 
	git reset --hard <codigo do commit>
	```

	**Atenção:** usar apenas se for autorizado pelo responsável da branch
	

- Fecha o terminal do git

	```
	exit 
	```
</details>

<details>

<summary> Comandos nas branchs </summary>

- Mostra as branchss disponíveis 

	``` 
	git branch
	```
O * na frente do nome indica que é essa branch que está sendo utilizada no momento

- Cria uma nova branch 

	``` 
	git branch nome_nova_branch
	```
	
- Muda para a branch especificada

	``` 
	git checkout nome_da_branch
	```

- Permite criar e mudar para uma nova branch
	```
	git checkout -b nome_da_nova_Branch nome_da_Branch_atual
	```
	
	Configura a branch padrão para mandar os commits
	```
	git push --set-upstream origin nome_da_nova_Branch
	```


- Atualiza os arquivos da máquina com os do servidor

	``` 
	git pull
	```
	
	**Obs:** usado para receber **atualização** do arquivos e **antes** de fazer o merge (mesclagem) ou o push

- Estando na branch principal esse comando mesclará as modificaçõe da branch segundaria com a principal

	``` 
	git merge nome_branch_segundaria
	```
</details>

<details>

<summary> Git config:</summary>


- Mostra as configurações do usuário

	```
	git config user.name
	git config user.email
	```

 - Mostra a branch configurada como padrão
	```
	git config init.defaultBranch
	```
 
 - Renomeia a branch padrão globalmente
	```    
	git config --global init.defaultBranch <nome da branch>
	``` 
 - Lista todas as configurações globais
	```   
	git config --global --list 
	``` 
 - Mostra o tipo de armazenamento das credenciais (cache temporário/apenas para um usuário, store permanente/todos os usuários)
	```    
	git config --global credential.helper
	``` 
- Mostra o local onde está armazenado o arquivo
	```
	git config --global --show-origin credential.helper 
	```
- Mostra quais repositórios está conectado
	```
	git remote -v 
	```
- Clona apenas a branch especificada, se não passar o nome da branch será clonado só a branch principal
	```
	git clone <url> <nome da pasta local> --branch <nome da branch> --single-branch 
	```

</details>


<details>


<summary> Git ignore:</summary>

- Adiciona uma determinada pasta no arquivo '.gitignore' para ser ignorada quando executar o 'git push'

	```
	echo 'caminho da pasta/' > .gitignore
	```

	para arquivos

	```
	echo 'nome_arquivo' > .gitignore
	```
- Remove uma determinada pasta do arquivo oculto '.gitignore' 

	```
	echo > .gitignore
	```

	Obs: O pasta do ambiente virtual (env) e arquivos de configuração ou informações pessoais podem ser incluidas no '.gitignore'

</details>


<details>


<summary> Desfazendo alterações: </summary>

- Remove uma pasta e todos os arquivos dentro dela

	```
	rm -rf 'nome da pasta'
	```
- Restaura o arquivo ao seu estado anterior ao salvamento, discartando todas as alterações que foram feitas

	```
	git restore 'nome da pasta/arquivo'
	```

- Mostra o historico de commits atuais
	```	
	git log
	```

- Corrige a mensagem do último commit

	```
	git commit --amend -m "nova mensagem" 
	```

- Entra no editor vim para alterar mensagem do último commit

	```
	git commit --amend
	```
	#Aperta a tecla 'i' para editar a mensagem
	#Para escrever e sair: esc + : + wq + enter



- Restaurando a versão há um commit anterior

	- Restaura os arquivos dos commits posteriores ao commit especificado para a area de prepação (stagin area: status após o comando 'git add .') e remove os commits posteriores deixando apenas a versão especificada para refazer o commit
		```
		git reset --soft "hash (id) do commit"
		```

	- Ação padrão do comando reset: Coloca os arquivos dos commits posteriores ao commit especificado na área de preparação como arquivos desconhecidos (untracked files: estado anterior ao comando 'git add . ')
		```
		git reset --mixed "hash (id) do commit"
		```

	- Restaura o estado completo do commit especificado, apagando tudo o que foi feito depois desse commit assim como o histórico de commits
		```
		git reset --hard "hash (id) do commit"
		```
	- Obs: Essas alterações devem ser feitas antes de enviar o commit para o repositóro com o 'git push'

- Mostra o historico de alterações de commits
	```	
	git reflog
	```

- Remove um determinado arquivo da area de preparação após ter feito o comando 'git add .'
	```
	git reset 'nome arquivo'	
	```

	ou usando o comando


	```
	git reset --staged 'nome arquivo'	
	```



- Crie um novo repositório na linha de comando

	```
	echo "Projeto 1" >> README.md 
	git init 
	git add README.md 
	git commit -m "first commit" 
	git branch -M main 
	git remote add origin url_do_repositorio
	git push -u origem principal
	```

- Envie um repositório existente a partir da linha de comando

	``` 
	git remote add origin link_do_repositorio
	git branch -M main 
	git push -u origin main
	``` 

</details>



<details>


<summary> Links sobre o GIT Bash </summary>


- Link do [repositório](https://github.com/Dev-JoaoM/Sobre-o-GitHub)

- Link de Tutorial do [GIT BASH](https://www.youtube.com/watch?v=kB5e-gTAl_s)

- Autenticação via [token](https://web.dio.me/course/versionamento-de-codigo-com-git-e-github/learning/3d13d85f-2508-4396-9657-4643d3302c79?back=/track/coding-future-vivo-python-ai-backend-developer&tab=undefined&moduleId=undefined)

- Autenticação via Chave [SSH](https://web.dio.me/course/versionamento-de-codigo-com-git-e-github/learning/a53b7d6e-d7a2-40de-a8f9-cc30b42fc93d?back=/track/coding-future-vivo-python-ai-backend-developer&tab=undefined&moduleId=undefined)

- Acessas as chaves ssh

	```
	ls -al ~/.ssh
	```

Sobre o [VSCode](https://www.youtube.com/watch?v=TW3KoPkuWEA)

Sobre o [Readme](https://www.youtube.com/watch?v=TsaLQAetPLU)

Clonar um [repositório](https://docs.github.com/pt/repositories/creating-and-managing-repositories/cloning-a-repository)

Tutorial [Git](https://github.com/matheusbattisti/tutorial_git)

Iniciando um [repositório com Git](https://www.alura.com.br/artigos/iniciando-repositorio-git)

Ebook: [Comandos mais utilizados de git](https://horadecodar.com.br/ebook-comandos-mais-utilizados-de-git/)

Criando um repositório remoto em [GitHub](https://www.alura.com.br/artigos/criando-repositorio-remoto-github)

Clonando um repositório com [Git e GitHub](https://www.alura.com.br/artigos/clonando-repositorio-git-github)

Repositório de Comandos [Leocomelli](https://gist.github.com/leocomelli/2545add34e4fec21ec16)

https://www.google.com/search?sca_esv=469084b56d0a10d6&rlz=1C1GCEA_enBR1076BR1076&q=como+baixar+um+repositorio+do+git+e+testar+localmente&tbm=vid&source=lnms&prmd=vsinbmtz&sa=X&ved=2ahUKEwivkP_98qqFAxVpr5UCHR_eBkQQ0pQJegQICRAB&biw=1536&bih=776&dpr=1.25

https://www.youtube.com/watch?v=Qgj8LKpvlhc

https://www.youtube.com/watch?v=Qgj8LKpvlhc

https://www.youtube.com/watch?v=d5d7DsQ5uXA

https://www.youtube.com/playlist?list=PLHz_AreHm4dm7ZULPAmadvNhH6vk9oNZA

https://www.youtube.com/watch?v=7Qnm1RTjvvo

https://www.youtube.com/watch?v=DqTITcMq68k

https://www.youtube.com/watch?v=Zwv9qRyVeU4&t=293s

https://www.youtube.com/watch?v=POpFXae0NP0

https://www.youtube.com/watch?v=Zwv9qRyVeU4

https://www.youtube.com/watch?v=TrDBJ9HO3yE

https://www.youtube.com/watch?v=EGmzAs1G0z0

https://www.youtube.com/watch?v=ts-H3W1uLMM

https://www.youtube.com/watch?v=UBAX-13g8OM


</details>