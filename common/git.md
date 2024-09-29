<p><img src="../images/git.svg" width=128 /></p>

># **Git**

O [Git](https://git-scm.com) é um sistema de controle de versão distribuído amplamente utilizado no desenvolvimento de software, criado por Linus Torvalds em 2005. Seu principal objetivo é gerenciar o histórico de alterações no código-fonte de projetos, permitindo que desenvolvedores colaborem de forma eficiente e segura.

Ao contrário de outros sistemas de controle de versão centralizados, o Git é distribuído, o que significa que cada desenvolvedor possui uma cópia completa do histórico do projeto em seu repositório local. Isso garante maior flexibilidade, autonomia e segurança, já que mudanças podem ser rastreadas, revertidas e integradas com facilidade, mesmo em ambientes com colaboradores geograficamente dispersos.

Algumas das principais características do Git incluem:

1. **Versionamento de código**: O Git permite que os desenvolvedores registrem versões específicas de um projeto ao longo do tempo, facilitando o acompanhamento e a reversão de alterações indesejadas.

2. **Branching e merging**: Ele oferece suporte avançado para criação de ramificações ("branches"), permitindo o desenvolvimento de novas funcionalidades de forma paralela, sem afetar a versão principal do projeto. A fusão de diferentes branches pode ser realizada de forma eficiente e com controle detalhado sobre conflitos.

3. **Desempenho e eficiência**: Por ser distribuído, o Git opera com alta performance em operações como commits, diffs e merges, uma vez que a maioria dessas operações é realizada localmente. Somente operações como o envio e recebimento de alterações requerem acesso remoto.

4. **Integridade e segurança**: Cada mudança no código é identificada por um hash criptográfico único (SHA-1), garantindo a integridade do histórico e prevenindo alterações maliciosas.

O Git se tornou uma ferramenta essencial para desenvolvedores de software devido à sua robustez, flexibilidade e vasta comunidade de suporte. Ele é amplamente utilizado em conjunto com plataformas como GitHub, GitLab e Bitbucket, que oferecem repositórios remotos, integrações com sistemas de CI/CD e funcionalidades colaborativas adicionais.

## Instalação no Linux Ubuntu
~~~bash
sudo apt install git
~~~

### Configuração local do repositório

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
Os procedimentos de configuração descritos a seguir são específicos para cada repositório Git. Portanto, devem ser executados nos repositórios <u>de cada projeto</u>.
</div>

Os caminhos (paths) para a pasta raiz de projetos e das ferramentas de desenvolvimento estão definidos nas variáveis de ambiente descritas abaixo ([Variáveis de Ambiente](../common/env.md)):

~~~bash
DEV_APPS     # Pasta base das ferramentas de desenvolvimento (Node, Java, Flutter, Android Studio, etc)
DEV_ROOT     # Pasta base dos seus projetos
~~~

Por exemplo, para configurar o Git no repositório raiz do projeto:
~~~bash
# Criar pasta do projeto
mkdir -p $DEV_ROOT
# Entrar na pasta do projeto
cd $DEV_ROOT

# Definir "main" como nome da branch principal
git config --global init.defaultBranch main
# Criar repositório Git
git init
# Definir o VSCode como editor padrão do Git
git config --local core.editor "code --wait"
# Abrir no VSCode as configurações do Git
git config --local --edit
~~~

Edite o conteúdo do arquivo de configuração do Git. Este arquivo será gravado em **.git/config**:
~~~ini
[user]
	name = John Doe         # Seu nome
	email = john@email.com  # Seu email no Github
[core]
	editor = code --wait
[push]
	followtags = true
	default = current
[alias]
	c = !git add --all && git commit -m
	s = !git status -s
	l = !git log --pretty=format:'%C(blue)%h%C(red)%d %C(white)%s - %C(cyan)%cn, %C(green)%cr'
	t = !sh -c 'git tag -a $1 -m $1' -
	ammend = !git add --all && git commit --amend --no-edit
	undo = !git reset HEAD~
~~~

### Cria e Configurar uma Conta no GitHub com Chave SSH

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
Este procedimento apenas é necessário se você ainda não possua uma conta no GitHub. Caso já possuam uma conta, vá para o tópico seguinte: <a href="#vincular-repositório-local-ao-github">Vincular Repositório Local ao GitHub</a>
</div>

O GitHub é uma das plataformas mais populares para hospedagem de código-fonte e colaboração em projetos de software, especialmente quando usamos Git como sistema de controle de versão. Uma prática comum e recomendada é o uso de autenticação por chave SSH para se conectar ao GitHub, garantindo maior segurança ao gerenciar repositórios. 

Este tutorial guiará você na criação de uma conta no GitHub e na configuração de uma chave SSH para autenticação.

#### 1. Criar uma Conta no GitHub

##### Passo 1: Acesse o site do GitHub
- Navegue para o site do GitHub em [https://github.com](https://github.com).
- Clique em **Sign up** (Cadastrar-se) no canto superior direito da página.

##### Passo 2: Preencha as Informações
- **Username (Nome de usuário)**: Escolha um nome de usuário único que será o seu identificador público no GitHub.
- **Email address (Endereço de e-mail)**: Forneça um endereço de e-mail válido que será usado para associar sua conta e para notificações.
- **Password (Senha)**: Crie uma senha forte para proteger sua conta.

Após preencher essas informações, clique no botão para continuar e siga as etapas de verificação e confirmação de conta.

##### Passo 3: Personalização e Preferências
O GitHub pode solicitar algumas preferências, como o seu nível de experiência com Git ou GitHub. Isso ajuda a personalizar sua experiência na plataforma. Depois de completar essas etapas, você terá acesso à sua nova conta.

##### Passo 4: Verificação de E-mail
Verifique a caixa de entrada do seu e-mail para uma mensagem de confirmação do GitHub. Clique no link de confirmação para ativar sua conta.

#### 2. Gerar e Configurar uma Chave SSH para Autenticação

O SSH (Secure Shell) é um protocolo que fornece uma maneira segura de acessar e manipular repositórios remotos. Ao invés de fornecer suas credenciais (nome de usuário e senha) cada vez que interage com o GitHub, você pode configurar uma chave SSH para autenticação automática e segura.

##### Passo 1: Verifique você já possui uma chave SSH
Antes de gerar uma nova chave SSH, verifique se já existe uma chave gerada no seu sistema. No terminal execute o comando:

~~~bash
ls -al ~/.ssh
~~~

Se esse diretório contiver arquivos como `id_rsa` e `id_rsa.pub`, você já possui uma chave SSH gerada. Caso contrário, siga os próximos passos para criar uma nova.

##### Passo 2: Gerar uma nova chave SSH
Se não houver uma chave SSH, ou se você deseja criar uma nova, execute o comando a seguir no terminal para gerar uma nova chave SSH:

~~~bash
ssh-keygen -t rsa -b 4096 -C "fulano@email.com"
~~~

Onde:
- **-t rsa** especifica o algoritmo de criptografia (RSA).
- **-b 4096** define o tamanho da chave (4096 bits é um bom padrão para segurança).
- **-C "seu-email@example.com"** adiciona um comentário à chave, geralmente o seu e-mail para referência.

##### Passo 3: Adicionar sua chave SSH ao agente SSH
O próximo passo é adicionar sua nova chave SSH ao agente SSH, que gerencia suas chaves privadas e facilita o processo de autenticação:

1. Inicie o agente SSH, se ele não estiver em execução:

    ~~~bash
    eval "$(ssh-agent -s)"
    ~~~

2. Adicione sua chave SSH ao agente:

    ~~~bash
    ssh-add ~/.ssh/id_rsa
    ~~~

##### Passo 4: Adicionar a chave SSH ao GitHub
Agora que você gerou a chave SSH, o próximo passo é vinculá-la à sua conta no GitHub.

1. Copie o conteúdo da chave pública SSH para o clipboard. Isso pode ser feito com o comando:

    ~~~bash
    cat ~/.ssh/id_rsa.pub
    ~~~

   Copie a saída do comando, que será algo como:

    ~~~
    ssh-rsa AAAAB3NzaC1yc2EAAAABIwAAAQEAs... fulano@email.com
    ~~~

2. Acesse o GitHub e faça login na sua conta.
3. No canto superior direito, clique na sua foto de perfil e vá até **Settings** (Configurações).
4. No menu lateral, clique em **SSH and GPG keys**.
5. Clique em **New SSH Key** (Nova chave SSH).
6. No campo "Title" (Título), você pode dar um nome para a chave (por exemplo, "Meu Laptop"). No campo "Key" (Chave), cole a chave SSH copiada.
7. Clique em **Add SSH Key** (Adicionar chave SSH).

##### Passo 4: Testando a conexão SSH
Após adicionar a chave SSH, você pode testar a conexão com o GitHub para garantir que tudo foi configurado corretamente. No terminal, execute o seguinte comando:

~~~bash
ssh -T git@github.com
~~~

Se tudo estiver correto, você verá uma mensagem semelhante a:

~~~
Hi seu-usuario! You've successfully authenticated, but GitHub does not provide shell access.
~~~

Isso significa que a autenticação foi bem-sucedida e você pode começar a interagir com seus repositórios GitHub via SSH.

### Vincular Repositório Local ao GitHub

Vincular um repositório Git local ao GitHub é uma prática comum e essencial no desenvolvimento de software, especialmente em ambientes colaborativos. Essa vinculação permite que o repositório local, onde o desenvolvedor mantém o histórico de desenvolvimento do código, se conecte a um repositório remoto no GitHub, facilitando o compartilhamento, a colaboração e o backup do projeto.

#### Por que vincular um repositório Git local ao GitHub?

1. **Colaboração em equipe**: Ao hospedar o repositório no GitHub, outros desenvolvedores podem clonar o repositório, propor alterações e colaborar no projeto por meio de pull requests e revisões de código.
   
2. **Backup seguro**: Manter o código apenas em um repositório local implica em risco de perda de dados. Vinculando o repositório ao GitHub, você garante que o código está armazenado em um ambiente seguro e acessível na nuvem.

3. **Acesso remoto**: Com o repositório no GitHub, você pode acessar o código de qualquer lugar, em qualquer dispositivo, facilitando o trabalho remoto e a continuidade do desenvolvimento fora do ambiente de trabalho habitual.

4. **Integrações e automação**: GitHub oferece uma série de integrações, como ferramentas de CI/CD (Integração Contínua e Entrega Contínua), além de outras funcionalidades para automação de testes, deploys e controle de qualidade.

#### Como vincular um repositório Git local ao GitHub?

A vinculação de um repositório Git local a um repositório remoto no GitHub pode ser feita em alguns passos simples. Supondo que você já tenha um repositório Git local configurado, os passos são os seguintes:

##### 1. Crie um repositório no GitHub
Primeiro, é necessário criar um novo repositório no GitHub. Para isso, siga estes passos:

- Acesse sua conta no GitHub.
- Clique no botão "New" (Novo) para criar um novo repositório.
- Preencha os campos como o nome do repositório, uma descrição (opcional) e escolha se ele será público ou privado.
- Não adicione nenhum arquivo (como README ou `.gitignore`) ao criar o repositório, pois o repositório local já tem um histórico Git. Apenas crie o repositório vazio.

##### 2. Vincule o repositório remoto ao repositório local
Agora, no terminal ou linha de comando, vá até o diretório do seu repositório Git local e vincule o repositório GitHub recém-criado como o repositório remoto.

~~~bash
git remote add origin git@github.com:seu-usuario/seu-repositorio.git
~~~

Esse comando define um nome (geralmente `origin`) para o repositório remoto. Substitua `seu-usuario` e `seu-repositorio` pelo seu nome de usuário no GitHub e o nome do repositório que você acabou de criar.

##### 3. Faça o envio (push) das alterações locais para o GitHub
Após adicionar o repositório remoto, é necessário enviar (push) as alterações do repositório local para o GitHub. Para isso, execute o seguinte comando:

~~~bash
git push -u origin master
~~~

Aqui, `master` se refere à branch principal do repositório (que pode ser chamada de `main`, dependendo da configuração). O comando `-u` cria um vínculo entre sua branch local e a branch remota, facilitando futuros envios de alterações.

#### 4. Autenticação
Dependendo da configuração do GitHub, você poderá ser solicitado a inserir suas credenciais (nome de usuário e senha) ou fornecer um token de autenticação pessoal (Personal Access Token). A autenticação garante que apenas usuários autorizados possam enviar alterações para o repositório.

#### 5. Verifique se a vinculação foi bem-sucedida
Para verificar se o repositório remoto foi adicionado corretamente, você pode usar o comando:

~~~bash
git remote -v
~~~

Esse comando listará os repositórios remotos configurados, juntamente com suas URLs. Se tudo estiver correto, você verá o repositório remoto `origin` listado.

### Conventional Commits

A padronização de procedimentos é um elemento essencial para o trabalho em equipe. Desta forma, a padronização de código, documentação e mesmo de mensagens de commit deve ser considerada em um ambiente de desenvolvimento profissional.

No contexto das mensagens de commit, recomenda-se o uso do padrão *Conventional Commits* para a submissão de *commits* do Git nos repositórios do projeto.

A especificação do [Conventional Commits](https://www.conventionalcommits.org/pt-br/v1.0.0) é uma convenção simples que visa padronizar as mensagens de commit. Ela define um conjunto de regras para criar um histórico de commit explícito, o que facilita a criação de ferramentas automatizadas baseadas na especificação. Esta convenção se encaixa com o *Semantic Versioning* ([SemVer](https://semver.org)), descrevendo os recursos, correções e modificações que mantém a compatibilidade nas mensagens de commit.

O padrão do *Conventional Commits* especifica que a mensagem de commit deve observar a seguinte estrutura, onde os campos entre colchetes não são obrigatórios:
~~~ini
<tipo>[escopo opcional]: <assunto>
[corpo opcional]
[rodapé(s) opcional(is)]
~~~

Na maioria dos casos, uma versão simplificada desta estrutura é suficiente. Sugere-se a seguinte estrutura:
~~~ini
<tipo>: <assunto>
~~~

#### Tipos de _commits_ recomendados

 Tipo   |Descrição
--------|---------------------------------------------------
feat    |nova funcionalidade (*feature*) adicionada ao projeto
refactor|refatoração do código, sem inclusão ou remoção de novas funcionalidades
fix     |correção (*fix*) de um problema (*bug*) no código
chore   |adição de nova configuração ou biblioteca ao projeto
docs    |modificação na documentação do projeto
test    |inclusão de teste unitário

#### Regras para composição de mensagens de <i>commit</i>

Sugere-se a utilização das seguintes regras nas mensagens de commit:

1. As mensagens devem ser escritas em inglês;
2. Todos os caracteres da mensagem devem estar em caixa baixa (*lower case*). Exceção para siglas e identificadores (nomes de variáveis, classes, etc) que devem seguir a mesma grafia utilizada no código;
3. As sentenças <u>não devem</u> ser terminadas com ponto ou qualquer outro sinal de pontuação;
4. Os verbos utilizados nas sentenças devem estar no tempo imperativo (_add_, _create_, _fix_, _modify_, etc), nunca no passado, presente ou futuro;
5. Apenas os elementos **\<tipo\>** e **\<descrição\>** devem ser usados na estrutura das mensagens de commit.

#### Exemplos de commits <u>dentro do padrão</u> sugerido:

~~~bash
git commit -m "fix: fix issue loading data in LoadCache class"
git commit -m "feat: move interface EncryptAdapter to its own file"
git commit -m "chore: add GetX package"
git commit -m "test: ensure Composite returns local data"
git commit -m "refactor: move SUT creation to setUp method"
~~~

#### Exemplos de commits <u>fora do padrão</u> do projeto:
~~~bash
git commit -m "fix: fix issue loading data in loadcache class"
git commit -m "feat: move interface EncryptAdapter to its own file."
git commit -m "chore: Add GetX package"
git commit -m "test: assegura que Composite retorna dados locais"
git commit -m "refactor: moved SUT creation to setUp method"
~~~
O que há de errado nas mensagens de _commit_ acima?

1. Nome da classe (identificador) "loadcache" não escrito como no código (deveria ser "LoadCache");
2. Mensagem terminada com sinal de pontuação;
3. Palavra "Add" com primeira letra maiúscula (deveria ser "add");
4. Mensagem escrita em português;
5. Verbo "moved" no passado (deveria ser "move").

### Validação de mensagens de commit

O _Git Hooks_ é um recurso que permite que comandos do Git sejam interceptados antes e/ou após sua execução. Tais _hooks_ permitem, por exemplo, que um _commit_ possa ter sua mensagem verificada antes que seja efetivamente registrado no repositório.

Para garantir a padronização das mensagens de _commit_ será utilizado um _script_ bash para validar as mensagens de _commit_ nos repositórios do projeto. Este _script_ será executado automaticamente pelo _Git Hooks_ sempre que um _commit_ do projeto for executado.

O _script_ abaixo deve ser copiado para o seguinte arquivo dentro do repositório do projeto:  **.git/hooks/commit-msg**:

~~~bash
#!/bin/bash
#
# This script validates commit messages to comply to
# Git Conventional Commits
#
# It should be copied to .git/hooks directory of each
# git repository
#

# Minimal message length
minlen=10

message=$(cat "$1")
len=$(expr $minlen - 2)
regex="^(chore|docs|feat|fix|refactor|test): ([a-z].+{$len,}[^.])$"

normal="\033[0m"
red="\033[0;31m"
yellow="\033[1;33m"
green="\033[0;32m"
white="\033[1;97m"
grey="\033[0;37m"

if ! [[ "${message}" =~ ${regex} ]]; then
  echo
  echo -e "${red}####################################"
  echo -e "${red}#    Invalid Git Commit Message    #"
  echo -e "${red}####################################"
  echo
  echo -e "${white}commit message: ${red}${message}"
  echo -e "${white}correct format: ${green}<type>: <subject>"
  echo
  echo -e "${yellow}type:"
  echo -e "${yellow}  ${green}feat     ${grey}A new feature."
  echo -e "${yellow}  ${green}fix      ${grey}A bug fix."
  echo -e "${yellow}  ${green}docs     ${grey}Documentation only changes."
  echo -e "${yellow}  ${green}refactor ${grey}A code change that neither fixes a bug nor adds a feature."
  echo -e "${yellow}  ${green}test     ${grey}Adding missing tests or correcting existing ones."
  echo -e "${yellow}  ${green}chore    ${grey}Changes to the build process or auxiliary tools and"
  echo -e "${grey}           libraries such as documentation generation."
  echo
  echo -e "${yellow}subject:"
  echo -e "${grey}  Brief summary ${green}(min $minlen chars)${grey} of the change in present tense."
  echo -e "${grey}  Not capitalized. No period at the end."
  echo

  exit 1
fi

exit 0
~~~

Em seguida é necessário dar permissão de execução para o arquivo do _script_:
~~~bash
chmod +x .git/hooks/commit-msg
~~~

Teste se o o procedimento acima está realmente bloqueando _commits_ inválidos:

~~~bash
cd $DEV_ROOT

# Erro: mensagem sem tipo
touch file1.txt
git add .
git commit -m 'add axios package'

# Erro: mensagem curta
touch file2.txt
git add .
git commit -m 'chore: axios'

# Erro: mensagem terminada com "."
touch file3.txt
git add .
git commit -m 'chore: add axios package.'

# Erro: mensagem iniciada com letra maiuscula
touch file4.txt
git add .
git commit -m 'chore: Add axios package'

# Mensagem correta
touch file5.txt
git add .
git commit -m 'chore: add axios package'
~~~


## Referências

Título                | Link
----------------------|----------------------
Minicurso de Git      | https://www.youtube.com/watch?v=ts-H3W1uLMM
Cheatsheet do Git     | https://education.github.com/git-cheat-sheet-education.pdf
Gerenciar sua conta no GitHub | https://docs.github.com/pt/account-and-profile/setting-up-and-managing-your-personal-account-on-github
