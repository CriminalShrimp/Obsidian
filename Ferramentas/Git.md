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

git checkout <span style="color:rgb(65, 105, 255)">OPÇÕES</span> **BRANCH**- Realiza as trocas entre as branch, e também pode restaurar versões de arquivos.
	-<span style="color:rgb(65, 105, 255)">-b</span>
		Cria uma nova branch, e também podemos definir um ponto inicial após a branch. Também existe o <span style="color:rgb(65, 105, 255)">B</span>, que se caso já exista essa branch ela só muda o ponto inicial.

git commit <span style="color:rgb(65, 105, 255)">OPÇÕES</span> - "Registra" as mudanças realizadas no repositório.
	<span style="color:rgb(65, 105, 255)">-a</span>, --all
		Envia todos os arquivos modificados
	-<span style="color:rgb(65, 105, 255)">--amend</span>
		Usando o `-m` é possível modificar a mensagem do ultimo commit, sem usar o `-m` o editor de texto será aberto para digitar a mensagem. Usando `--no-edit` adicionamos os arquivos sem mudar a mensagem anterior
	<span style="color:rgb(65, 105, 255)">-m,</span> --message "MENSAGEM"
		Adiciona sua mensagem ao commit, usando `-am` é possível enviar todos os arquivos e o comentário junto. Além disso existe como adicionar dados específicos no commit usando o `GIT_AUTHOR_` (identifica o autor original do código) que ou `GIT_COMMITTER_` (identifica quem realizou o commit), e com eles é possível usar `DATE`, `EMAIL` e `NAME`.
 
git clone **REPOSITORIO** - Realiza o clone de um repositório especificado para um novo diretório.

git diff <span style="color:rgb(65, 105, 255)">OPÇÕES</span> - Mostra a diferença entre arquivos.
	brach
		Colocando duas branchs uma em seguida da outra é possível compara as diferenças entre elas.
	file
		Colocando o nome do arquivo é possível verificar as diferenças comente naquele arquivo.
	commit
		É possível comparar diferenças entre commits colocando seus identificadores um após o outro (usando `git log` para obter este dado)

git init - Cria um repositório Git vazio. 

git merge **BRANCH** - Junta duas ou mais branchs na branch atual. 

git push <span style="color:rgb(65, 105, 255)">OPÇÕES</span> **REPOSITORIO** **BRANCH** - Manda as alterações realizas localmente para o repositório remoto.
	<span style="color:rgb(65, 105, 255)">-a</span>, --all
		Envia todas as branchs para o repositório.
	<span style="color:rgb(65, 105, 255)">-u</span>, --set-upstream
		Associa a local a branch remota, depois dessa ligação ser realizada é necessário só digita `git push` para "subir" as alterações.

git pull **REPOSITORIO** **BRANCH** - Baixa as alterações de um repositório remoto para o local. Digamos que ele serve para sincronizar com todo o projeto.


git switch **BRANCH** - Vai de uma branch para outra. Uma boa opção para usar junto é o -c, que cria uma nova branch.

### Reverter Mudanças

git restore - 

git reset - 

git revert COMMIT - Volta as mudanças realizadas.
