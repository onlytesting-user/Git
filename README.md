# Sumário:

1° - [Comandos para o arquivo de configuração do Git](#1-comandos-para-o-arquivo-de-configuração-do-git) <br>
2° - [Comandos para chaves SSH](#2-comandos-para-chaves-ssh) <br>
3° - [Comandos Básicos Iniciais](#3-comandos-básicos-iniciais) <br>
4° - [Comandos para Branches](#4-comandos-para-branches) <br>
5° - [Comandos para Consulta](#5-comandos-para-consulta) <br>
6° - [Comandos para Mesclar Diferenças](#6-comandos-para-mesclar-diferenças) <br>
7° - [Comandos para Restauração](#7-comandos-para-restauração) <br>
8° - [Comandos para Exclusão](#8-comandos-para-exclusão) <br>
9° - [Comandos para Manipulação de Stash](#9-comandos-para-manipulação-de-stash) <br>
10° - [Melhor não usar](#10-melhor-não-usar)

<br>

# 1° Comandos para o arquivo de configuração do Git

<br>

```
git config --global user.name "nome no Github"
```

_Define seu nome de usuário globalmente. Coloque o mesmo nome do cadastrado no Github_

<br>

```
git config --global user.email "seu e-mail no Github"
```

_Define seu endereço de e-mail globalmente. Coloque o mesmo e-mail do cadastrado no Github_

<br>

```
git config --global init.defaultBranch main
```

_Redefine o nome padrão da Branch de master para main_

<br>

```
git config --global core.editor "code --wait"
```

_Define o VS Code como editor padrão para comandos Git como git commit_

<br>

```
git config --global core.autocrlf input
```

_Define que o Git converterá CRLF para LF quando você adicionar arquivos ao repositório, mas não converterá LF de volta para CRLF quando você fizer checkout_

<br>

```
git config --global --list
```

_Lista todas as mudanças globalmente feitas por você (como as feitas acima)_

<br>

# 2° Comandos para chaves SSH

```
ssh-keygen -t ed.25519 -C "seu e-mail no Github"
```

_Cria uma chave SSH para o seu e-mail do Github mencionado_

<br>

```
ls
```

_Conferir chaves SSH já registradas, se houver alguma_

<br>

```
cat id_ed25519.pub
```

_Mostra a chave pública, sendo essa a que você deve colocar no GitHub_

**_OBS: certifique-se de que está dentro da pasta .ssh (essa pasta fica dentro do seu usuário)_**

<br>

# 3° Comandos Básicos Iniciais

- Crie um arquivo chamado .gitignore se quiser colocar algum arquivo do projeto que não deve ser rastreado para o Stage e nem subir para o repositório Virtual, como o vscode.config

- Quando já tiver conectado ao Github:

```
git init
```

_Inicia um repositório, só deve ser executado uma vez por programa_

**_OBS: se você já tiver criado o repositório no Github, não é necessário usar esse comando_**

<br>

```
git clone <link do repositório no Github>
```

_Clona um repositório existente_

<br>

```
git clone <link do repositório no Github>
--branch <nome da branch> --single-branch
```

_Clona o repositório de uma única Branch mencionada, caso o projeto tenha mais de uma, é claro_

<br>

```
git add .
```

_Cataloga as alterações em todos os arquivos que sofreram algum tipo de alteração e o(s) põe em uma área intermediária chamada de Stage_

<br>

```
git add <nome do arquivo 1>, <nome do arquivo 2>
```

_Cataloga as alterações nos arquivos citados e a põe em uma área intermediária chamada de Stage. Separe diferentes arquivos por vírgula_

<br>

```
git commit -m "texto do commit"
```

_Comita as alterações e exibe um texto detalhando-a_

### Primeiro commit:

- **_Initializing Repository_**

<br>

```
git commit
```

_Abre o terminal para editar e escrever commits maiores e mais detalhados. Utilize o Convencional Commit, de preferência_

**Tipo:**

**[ <br>
&nbsp;&nbsp; feat, fix, <br>
&nbsp;&nbsp; style, refactor, <br>
&nbsp;&nbsp; test, build, <br>
&nbsp;&nbsp; ci, perf, <br>
&nbsp;&nbsp; revert, docs <br>
]**

**feat:** _Implementação de uma nova funcionalidade_

**fix:** _Correção de algum bug ou problema_

**style:** _Faz modificações relacionadas ao estilo de código, como formatação ou/e indentação_

**refactor:** _Refatora o código, sem alterar sua funcionalidade. Ex: passar um simples bloco condicional if-else clássico para um operador ternário ou um complexo bloco if-else para switch case_

**test:** _Adiciona ou modifica testes_

**build:** _Modificações relacionadas ao sistema de build - como Dockerfile e docker-compose - ou dependências que afetem a estrutura do build ou a configuração do ambiente_

**ci:** _Modificações em arquivos de configuração ou scripts relacionados à integração contínua_

**perf:** _Melhora o desempenho de um componente ou sistema_

**revert:** _Reverte um commit anterior_

**docs:** _Atualiza ou adiciona documentação._

**Ex:**

1. Alterações no README.md (para arquitetura, explicações, release notes, exemplos e demonstrações de uso) ;
2. Alterações em documentação de APIs, modificações em comentários de códigos que sejam uma explicação técnica mais detalhada ;
3. Modificação, criação ou adição de diagramas UML.

<br>

**chore:** _Atividade de manutenção geral, ajustes._

**Ex:**

1. Atualização de pacotes e dependências que não exijem mudanças na estrutura do build ou na configuração do ambiente ;
2. Correção de erros de digitação ;
3. Mudanças no nome de variáveis para melhor legibilidade ;
4. Atualizar comentários desatualizados, remover comentários redundantes ou desnecessários, como limpar código comentado que não deve mais estar no repositório. Fazer pequenas melhorias nos comentários para manter a consistência ou clareza, sem adicionar documentação técnica detalhada.

<br>

**config:** _Alterações nas configurações do projeto._

**Ex:**

1. Alterar a tag InvariantGlobalization do arquivo csproj de 'true' para 'false' ;
2. Alterações em configurações de ambiente local, como ajustes de portas, URLs de serviços internos, etc. Como mudar porta padrão do servidor de desenvolvimento para evitar conflitos ;
3. Mudanças em arquivos de configuração que afetam o comportamento do sistema, como arquivos YAML, JSON, XML, etc. Como atualizar configuração de banco de dados no arquivo de configuração principal ;
4. Mudanças em arquivos de configuração de build, como 'pom.xml', 'package.json', 'build.gradle', entre outros. Como ajustar versão do compilador Java no arquivo pom.xml ;
5. Mudanças em variáveis de ambiente usadas para configurar o ambiente de desenvolvimento ou produção do projeto. Como atualizar variável de ambiente para URL de API de produção.

<br>

**infra:** _Modificações na infraestrutura do projeto._

**Ex:**

1. Configurações de Servidores e Ambientes. Como configurar firewall para permitir acesso à porta 8080 no servidor de produção ;
2. Configuração de Ferramentas de Monitoramento e Logging. Como configurar integração do sistema com ferramenta de monitoramento Prometheus ;
3. Provisionamento e Configuração de Infraestrutura. Como atualizar script de provisionamento para instalar dependências necessárias no ambiente de desenvolvimento ;
4. Configuração de Redes e Balanceamento de Carga. Como configurar DNS para redirecionar tráfego para o novo servidor de aplicação.

<br>

### Estrutura:

**< tipo >:** _< descrição simples >_

**p1 ->** _< explique o porquê de fazer o commit >_

**p2 ->** _< explique o que o commit faz >_

**_OBS: os commits devem ser escritos no tempo presente e não no passado. Também devem estar sempre no imperativo (`add`, `fix`, `update`)_**

<br>

```
git remote add origin <link do repositório no Github>
```

_Conecta o repositório local ao virtual_

<br>

```
git push -u origin <nome da branch>
```

_Envia de fato as alterações feitas localmente ao repositório virtual. Só necessita ser executado na primeira vez que você enviar informações daquele mesmo arquivo para aquela determinada branch._

**_OBS: Caso você crie uma branch diferente, precisará executar esse comando de push primeiro com o nome da branch criada para, após, passar a utilizar o push abaixo também com o nome da nova branch_**

<br>

```
git push origin <nome da branch>
```

_Envia as alterações feitas localmente para o repositório virtual. Deve ser assim todas as outras vezes que você fizer um push com exceção da primeira_

<br>

# 4° Comandos para Branches

```
git checkout -b <nome da Branch>
```

_Cria uma nova Branch e já a define como atual na sessão_

<br>

```
git branch <nome da Branch>
```

_Apenas cria a Branch. Para definí-la como a atual da sessão será necessário usar o git checkout_

<br>

```
git branch -v
```

_Mostra o último commit de cada Branch_

<br>

```
git checkout main
```

_Muda para a Branch citada e a torna a atual da sessão_

<br>

```
git merge <nome da Branch>
```

_Mescla a Branch atual com a Branch citada_

<br>

```
git branch -d <nome da Branch>
```

_Só exclui a Branch citada se já tiver sido feito o merge dela com outra Branch existente_

<br>

```
git branch -D <nome da Branch>
```

_Exclui a Branch mesmo que não tenha sido feito nenhum merge_

<br>

# 5° Comandos para Consulta

```
git status
```

_Confere e retorna se existe algum arquivo cuja as informações ainda não foram catalogadas pelo git add (no caso, não colocadas no stage) e indica a Branch atual_

<br>

```
git log
```

_Confere e retorna todos os commits feitos, incluindo o texto dele obviamente e quem fez a alteração_

<br>

```
git reflog
```

_Confere e retorna todos os commits feitos, mas com informações mais detalhadas sobre cada um deles_

<br>

# 6° Comandos para Mesclar
Diferenças

```
git fetch
```

_Mostra todas as diferenças entre o repositório local e o virtual_


```
git diff
```

_Usado para examinar todas as diferenças entre a branch local e a branch remota_

<br>

```
git pull origin main
```

_Puxa as alterações do repositório virtual para o local. É executado depois do git remote add_

<br>

# 7° Comandos para Restauração

_No desenvolvimento com versionamento de código usando Git e GitHub, existem três áreas principais:_

**1. Área de Trabalho (Working Directory):** É onde você faz suas alterações no código localmente na sua máquina.

**2. Área de Preparação (Staging Area ou Index):** É onde você coloca as alterações que deseja commitar. As alterações são adicionadas à área de preparação usando o comando `git add`.

**3. Repositório Local (Local Repository):** É onde os commits são armazenados localmente. As alterações na área de preparação são salvas no repositório local com o comando `git commit`.

_Além dessas três áreas, quando você utiliza um serviço de hospedagem de repositórios como o GitHub, você tem:_

**4. Repositório Remoto (Remote Repository):** É o repositório que fica hospedado no GitHub. As alterações do repositório local são enviadas para o repositório remoto usando o comando `git push`.


```
git restore <nome do arquivo>
```

_Restaura o arquivo citado para o estado no último commit. Se houver alterações não comitadas, elas serão desfeitas_


```
git restore --staged <nome do arquivo>
```

_Remove o arquivo especificado da área de preparação (stage), revertendo-o para o estado do último commit. Não afeta o diretório de trabalho_

**Ex:**

```
git restore --source=HEAD Imagens/code.png
```

<br>

```
git reset HEAD <nome do arquivo>
```

_Remove o arquivo especificado da área de preparação (stage), mas mantém as alterações no diretório de trabalho_

<br>

```
git reset --soft <id do commit>
```

_Desfaz os commits do repositório local até o commit especificado, mas mantém as alterações tanto no stage quanto no diretório de trabalho_

<br>

```
git reset --mixed <id do commit>
```

**Ou**

```
git reset <id do commit>
```

_Desfaz os commits do repositório local até o commit especificado, mantendo as alterações no diretório de trabalho, mas removendo-as da área de preparação **(stage)**_

<br>

```
git reset --hard <id do commit>
```

_Desfaz os commits do repositório local até o commit especificado, removendo todas as alterações tanto do diretório de trabalho quanto da área de preparação **(stage)**_

**_OBS: Este comando deve ser usado com cuidado, pois as alterações descartadas não podem ser recuperadas facilmente_**

<br>

# 8° Comandos para Exclusão

```
git rm <nome do arquivo>
```

_Excluí o arquivo citado do stage (área de preparação) e do diretório físico, mas é necessário um commit para exclusão do diretório virtual_

<br>

```
git rm -rf <nome do arquivo>
```

_Exclusão forçada de diretórios inteiros (área de preparação, diretório físico e virtual)_

<br>

```
git rm --cached <nome do arquivo>
```

_Para de rastrear o arquivo citado, mas não o remove fisicamente_

_Use os comandos abaixo quando o arquivo/pasta em questão já estiver no github:_

_Use `--cached -r <nome do arquivo> para parar de rastrear pastas individualmente ou -r --cached .` para parar de rastrear todas as pastas._

<br>

# 9° Comandos para Manipulação de Stash

```
git stash
```

_Armazena temporariamente alterações locais que ainda não foram commitadas, permitindo que você trabalhe em outras Branchs ou faça outras alterações sem levar essas consigo_

<br>

```
git stash save
```

_Para armazenar as alterações atuais no diretório de trabalho e no stage_

<br>

```
git stash list
```

_Para ver a lista de stashes salvos_

<br>

```
git stash apply
```

_Para aplicar as alterações do stash mais recente de volta ao seu diretório de trabalho_

<br>

```
git stash drop
```

_Para remover o stash mais recente após aplicar suas alterações_

<br>

```
git stash pop
```

_Para aplicar e remover o stash mais recente em uma única etapa_

<br>

# 10° Melhor não usar

```
git commit --amend
```

**_OBS¹: Tente nunca usar esse comando, ele provoca erros de commit, te obrigando a fazer um git pull. De preferência, escreva e revise bem seus commits ao invés de alterá-los com o -- amend._**

**_Obs²: Use esse comando apenas depois de fazer o primeiro commit. Se executar antes, ele sempre irá falhar._**

_Permite corrigir textos de commits e fazer alterações posteriores a definição de um commit A fazerem parte dele sem necessariamente subir um commit B (claro, tem que fazer isso antes de um `git push`)_

• Se estiver no vein:

**Para poder digitar no terminal =** i

**Para sair do modo INSERT =** esc

**Para sair =** :wq

<br>

```
git --amend -m "texto do commit"
```

_Faz o mesmo que o ammend comum, mas ao invés dele, não abre o terminal_
