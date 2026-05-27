**Sumário**
	**Tags:** #Ferramentas 
	**Conteúdo:**
		git-scm.com/docs/git - Documentação do git.
		https://gitmastery.me - Plataforma para Aprender Git gamificado.
		youtu.be/pyM5QLS2h6M?si=SntctgqgUziPWeqt - Básico do Git.
		
----

Git é um **sistema de controle de versionamento** e também para criação de projetos comunitários de código aberto ou **Open Source**, usado tanto para projetos pessoais, até por grandes empresas por todo o mundo. Antes de observar um cenário real onde podemos usar essa ferramenta, temos que ver alguns termos que são usados junta a ela.

**Commit**: Confirmar as alterações realizada nos arquivos, normalmente ao fazer isso é falado "commitei".

**Branch**: É uma versão paralela da atual do seu repositório, ela não afeta a versão principal, sendo assim nenhuma alteração será feita na versão oficial, então é possível fazer teste alterações e adicionar coisas novas sem se preocupar no que pode afetar.

**Fork**: Cria uma copia do projeto em questão para a sua conta.

**Merge**: Quando queremos juntas as Branchs na principal (master/main), usamos o termos "fazer a Marge".

**Push**: Fazer um push significa enviar as alterações feitas localmente para o repositório web.

**Repositório**: Existe dois tipos de repositórios, o que é onde esta sendo trabalhado no computador, o repositório local, e temos o que fica salvo na web chamado normalmente de repositório remoto.

**GitHub** x **GitLab**: São as duas maiores plataformas que usam git, sendo o **GitHub** a mais popular pois é mais focado em um publico geral, em quando o **GitLab** é mais um "tudo em um" focando em seu uso em empresas.

## Comandos

Temos os comandos de serviços padrões como `status`, `help`, `config`. Além dos comandos mais básicos temos muitos outros tanto para fazer o versionamento tanto para fazer o envio dos arquivos.

git add **ARQUIVO** - Adiciona arquivos desejados, se usar o `.` ele adiciona todos os arquivos da pasta atual.

git branch <span style="color:rgb(65, 105, 255)">OPÇÕES</span> **BRANCH** - Pode lista, cria ou deleta branchs. Sem nenhuma opção basta apenas informar o nome da branch e ela ira ser criada.
	<span style="color:rgb(65, 105, 255)">-d</span>, --delete
		Deleta a branch desejada.
	<span style="color:rgb(65, 105, 255)">-a</span>, --all
		Realiza a listagem de todas as branchs, tanto remotas quando locais.
	<span style="color:rgb(65, 105, 255)">-l</span>, --list <span style="color:rgb(0, 176, 80)">PARAMETRO</span>
		Lista as todas as branchs que baterem com o parâmetro especificado.

git checkout <span style="color:rgb(65, 105, 255)">OPÇÕES</span> **BRANCH**- Realiza as trocas entre as branch, e também pode restaurar versões de arquivos mas tem outros comandos para .
	<span style="color:rgb(65, 105, 255)">-b</span>
		Cria uma nova branch, e também podemos definir um ponto inicial após a branch. Também existe o <span style="color:rgb(65, 105, 255)">B</span>, que se caso já exista essa branch ela só muda o ponto inicial.

git commit - 
	m

git clone **REPOSITORIO** - Realiza o clone de um repositório especificado para um novo diretório.

git init - 

git merge - 

git push - 

git pull -

git switch -

git 


### Reverter Mudanças

git restore - 

git reset - 

git revert - 

