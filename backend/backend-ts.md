<p><img src="../images/typescript.svg" width=128 /></p>

># **Ambiente de Desenvolvimento TypeScript**

O **TypeScript** é uma linguagem de programação de código aberto desenvolvida pela Microsoft, que estende o JavaScript adicionando recursos como **tipagem estática** e **verificação de tipos**. Ele é considerado um _superset_ de JavaScript, o que significa que todo código JavaScript é válido dentro de um arquivo TypeScript. Entretanto, TypeScript oferece funcionalidades adicionais que facilitam o desenvolvimento de aplicações maiores e mais complexas, promovendo maior robustez e manutenção do código.

#### Características Principais do TypeScript

1. **Tipagem Estática**
   Um dos principais diferenciais do TypeScript em relação ao JavaScript é a tipagem estática. Em JavaScript, as variáveis podem assumir qualquer tipo durante a execução do código, o que pode resultar em erros difíceis de detectar. Com TypeScript, é possível declarar explicitamente o tipo das variáveis, funções e objetos.

   Isso permite que o compilador identifique erros de tipo antes mesmo de o código ser executado, o que melhora significativamente a **segurança** e a **previsibilidade**.

2. **Compilação para JavaScript**
   O TypeScript, por si só, não é interpretado diretamente pelos navegadores ou por ambientes de execução como Node.js ou Deno. Ele precisa ser **compilado** para JavaScript, que é a linguagem que os navegadores e o Node.js entendem. Durante essa compilação, o código TypeScript é convertido em código JavaScript equivalente.

   Isso significa que, ao final do processo, o código gerado é puro JavaScript e pode ser executado em qualquer ambiente compatível com JavaScript, como navegadores, servidores e dispositivos móveis.

3. **Suporte a ES6/ESNext**
   TypeScript não só suporta as funcionalidades modernas do ECMAScript (ES6 e versões mais recentes), como também possibilita que você utilize essas funcionalidades mesmo em ambientes que ainda não oferecem suporte nativo a elas. O TypeScript pode ser configurado para gerar código JavaScript compatível com diferentes versões do ECMAScript, permitindo que você aproveite recursos avançados enquanto ainda garante compatibilidade com navegadores mais antigos.

4. **Interfaces e Classes**
   O TypeScript traz funcionalidades típicas de linguagens orientadas a objetos, como **interfaces** e **classes**. Com isso, é possível criar contratos para objetos e modelar estruturas mais robustas, tornando o código mais organizado e fácil de entender.

5. **Verificação de Erros em Tempo de Compilação**
   O TypeScript identifica potenciais erros durante a fase de compilação, antes mesmo que o código seja executado. Isso reduz a ocorrência de erros em tempo de execução, o que melhora a qualidade do software e a experiência de desenvolvimento.

6. **Suporte a Módulos**
   O TypeScript permite o uso de módulos para organizar o código em diferentes arquivos e pastas. Isso é essencial em projetos maiores, pois ajuda a modularizar a lógica da aplicação, melhorando a legibilidade e a manutenção.

7. **Integração com Ferramentas de Desenvolvimento**
   O TypeScript possui excelente integração com ferramentas de desenvolvimento e editores de código como o **Visual Studio Code**. Isso inclui recursos como autocompletar, realce de sintaxe e verificação de erros em tempo real. Esses recursos tornam o desenvolvimento mais rápido e eficiente, especialmente em projetos de grande escala.

8. **Opções de Configuração Flexíveis**
   O TypeScript oferece um arquivo de configuração (`tsconfig.json`) que permite ajustar como o código será compilado. Algumas das opções incluem:
   - O nível de permissividade com os tipos (`strict`).
   - O alvo da compilação JavaScript (`target`), que define qual versão do ECMAScript será usada.
   - O diretório de saída dos arquivos compilados.
   
   Este nível de personalização permite que você adapte o TypeScript às necessidades específicas de qualquer projeto.

#### Vantagens do TypeScript

1. **Código Mais Seguro e Previsível**: A tipagem estática e a verificação de erros em tempo de compilação evitam muitos erros comuns, tornando o código mais confiável e fácil de manter.

2. **Melhor Organização em Grandes Projetos**: O suporte a classes, interfaces e módulos faz do TypeScript uma ótima escolha para aplicações de larga escala, onde a manutenção de código se torna um desafio.

3. **Escalabilidade**: Por ser compatível com JavaScript, o TypeScript permite que equipes com diferentes níveis de familiaridade com a linguagem façam a transição gradual do JavaScript para o TypeScript. A introdução da tipagem estática pode ser feita progressivamente, aumentando a segurança e escalabilidade do projeto sem comprometer a flexibilidade.

4. **Ferramentas de Desenvolvimento Avançadas**: Ferramentas como o Visual Studio Code oferecem uma experiência de desenvolvimento muito aprimorada ao trabalhar com TypeScript, graças a funcionalidades como IntelliSense (autocompletar inteligente), que melhora a produtividade dos desenvolvedores.


## Configuração de um Ambiente de Desenvolvimento TypeScript no Linux

### 1. Instalação do Node.js, NPM e NVM

O TypeScript (TS) é compilado para JavaScript (JS) em um processo conhecido como transpilação. Para se executar código JS fora do navegador, em um ambiente backend por exemplo, é necessário ter instalado no sistema um ambiente de execução JS, como o Node.js.

O Node.js permite executar scripts fora de um navegador web, especificamente no lado do servidor. Ele foi lançado em 2009 por Ryan Dahl, e revolucionou o desenvolvimento web ao permitir que JS, tradicionalmente restrito ao frontend (navegadores), fosse utilizado no backend. O Node.js é baseado no mecanismo V8 da Google, que é o motor JS que também alimenta o Google Chrome.

O Node.js vem acompanhado do utilitário NPM (_Node Package Manager_), o gerenciador de pacotes padrão para JS, que permite que os desenvolvedores instalem e gerenciem bibliotecas e dependências de forma simples e eficiente. O NPM possui um vasto repositório de pacotes reutilizáveis para diversas funcionalidades, desde ferramentas de desenvolvimento até bibliotecas complexas para autenticação, banco de dados, comunicação em tempo real entre muitas outras.

O NVM (Node Version Manager) é uma ferramenta essencial para desenvolvedores que precisam gerenciar várias versões do Node.js em um único sistema. Ele permite instalar, alternar e manter múltiplas versões do Node.js, facilitando o desenvolvimento de diferentes projetos com requisitos variados.

##### Passo 1: Atualizar os pacotes do sistema e dependências necessárias

Antes de iniciar a instalação, certifique-se de que todos os pacotes do seu sistema estão atualizados e que possui as dependências necessárias instaladas. No terminal, execute:

~~~bash
sudo apt -y update
sudo apt -y install build-essential libssl-dev curl
~~~

##### Passo 2: Instalar o Node.js, NPM e NVM

Agora, vamos baixar e instalar o NVM a partir do repositório oficial do GitHub. Use o **curl** para fazer o download e executar o script de instalação:

~~~bash
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash
~~~
> **Nota**: A versão do NVM (`v0.40.1` neste exemplo) pode mudar conforme novas versões sejam lançadas. Você pode sempre verificar a versão mais recente no [repositório do NVM no GitHub](https://github.com/nvm-sh/nvm).

Em seguida crie a variável de ambiente que define o local de instalação do NVM acrescentando no final do arquivo `.bashrc`:

~~~bash
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"
~~~

Atualize o ambiente e teste a instalação do NVM:
~~~bash
source ~/.bashrc
nvm -v
~~~


### 4. Carregar o NVM no Shell

O script de instalação do NVM automaticamente adiciona as configurações necessárias ao arquivo de inicialização do shell, como `.bashrc`, `.bash_profile` ou `.zshrc`, dependendo do shell que você usa.

Para garantir que o NVM esteja disponível no terminal sem reiniciar o shell, execute:

```bash
source ~/.bashrc
```

Se você estiver usando o **zsh**, execute:

```bash
source ~/.zshrc
```

---

### 5. Verificar a Instalação do NVM

Para verificar se o NVM foi instalado corretamente, execute o comando abaixo no terminal:

```bash
nvm --version
```

Se o comando retornar um número de versão, isso significa que o NVM foi instalado com sucesso.

---

### 6. Instalar uma Versão do Node.js com o NVM

Agora que o NVM está instalado, você pode usá-lo para instalar qualquer versão do Node.js. Por exemplo, para instalar a versão mais recente, execute:

```bash
nvm install node
```

Isso instalará a versão mais recente do Node.js.

Se você precisar de uma versão específica do Node.js (por exemplo, 14.x), você pode instalar essa versão com o comando:

```bash
nvm install 14
```

---

### 7. Definir uma Versão Padrão do Node.js

Depois de instalar uma ou mais versões do Node.js, você pode escolher qual versão usar como padrão. Para usar a versão 14, por exemplo, digite:

```bash
nvm use 14
```

Se você quiser definir essa versão como a versão padrão para todas as sessões futuras do terminal, execute:

```bash
nvm alias default 14
```

---

### 8. Listar Versões Instaladas

Para ver todas as versões do Node.js que você já instalou com o NVM, execute:

```bash
nvm ls
```

Esse comando listará todas as versões instaladas e indicará qual delas está atualmente em uso.

---

### 9. Alternar Entre Versões do Node.js

Se você tiver várias versões do Node.js instaladas, pode alternar entre elas facilmente. Por exemplo, para mudar para a versão 16, use:

```bash
nvm use 16
```

---

### Considerações Finais

Agora você tem o **NVM** instalado e configurado no Ubuntu, permitindo que você gerencie facilmente diferentes versões do Node.js. Isso é especialmente útil para desenvolvedores que trabalham em vários projetos com requisitos distintos de versões de Node.js.

Com o NVM, você pode instalar, desinstalar e alternar entre versões do Node.js com facilidade, sem a necessidade de gerenciar manualmente as instalações do Node.js.







Agora, vamos baixar e instalar o NVM a partir do repositório oficial do GitHub. Use o curl para fazer o download e executar o script de instalação:

~~~bash
Copiar código
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.4/install.sh | bash
Nota: A versão do NVM (v0.39.4 neste exemplo) pode mudar conforme novas versões sejam lançadas. Você pode sempre verificar a versão mais recente no repositório do NVM no GitHub.
~~~

Em distribuições baseadas no Debian (como o Ubuntu), podemos instalar o Node.js diretamente dos repositórios oficiais.

~~~bash
sudo apt -y install nodejs npm
~~~

Após a instalação, verifique se o Node.js e o npm foram instalados corretamente:

~~~bash
node -v
npm -v
~~~

Esses comandos devem retornar as versões do Node.js e do npm, respectivamente.

##### Passo 3: Instale a versão mais recente do Node.js

O Node.js disponível nos repositórios do sistema pode não ser a versão mais recente. Para garantir que você tenha a versão mais atual, siga as etapas abaixo para usar o NodeSource, que oferece as versões mais recentes do Node.js:

~~~bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs
~~~

Esse comando instala o Node.js da versão 18.x. Você pode ajustar o número para a versão que desejar.

### 2. Instalar o TypeScript

Agora que o Node.js e o npm estão instalados, o próximo passo é instalar o **TypeScript**, o qual pode ser configurador local ou globalmente. A escolha entre essas formas depende de como você deseja utilizar o TypeScript no projeto ou no sistema.

##### Instalação Local
Instalar o TypeScript localmente significa que ele será instalado dentro de um projeto específico, ficando disponível apenas para aquele projeto. Ele será listado como uma dependência no arquivo package.json, e a versão instalada será usada apenas no escopo desse projeto.

As principais vantagens da instalação local são:
- Mantém a consistência da versão do TypeScript usada no projeto, o que é importante quando diferentes projetos usam diferentes versões.
- O TypeScript não interfere com outros projetos no sistema.

##### Instalação Global
Instalar o TypeScript globalmente significa que ele será acessível em qualquer lugar do sistema, permitindo que você use o comando `tsc` para compilar TypeScript de qualquer projeto sem precisar instalá-lo localmente. Isso é útil se você deseja ter uma única versão do TypeScript disponível em todo o sistema.

Neste tutorial optaremos pela **instalação local** do TypeScript.

#### Passo 1: Criar um projeto

Instalar o TS localmente significa que ele será configurado como um pacote de um projeto específico. Desta forma, antes mais nada precisamos criar um novo projeto no Node.js e configurá-lo utilizando o NPM.

~~~bash
# Entrar na pasta base do projeto
cd $DEV_ROOT
# Criar um novo projeto
npm init -y
~~~

O comando `npm init` cria um novo projeto gravando suas configurações no arquivo `package.json` e instalará suas dependências dentro da pasta `node_modules`. Esta pasta sempre poderá ser gerada automaticamente a partir das configurações contidas no arquivo `package.json` por meio do comando `npm init`. 

Desta forma, não é desejável que a pasta `node_modules` seja incluída em nosso repositório Git. Para evitar isso devemos instruir o Git a ignorar esta pasta criando o arquivo `.gitignore`.

~~~bash
# Cria o arquivo .gitignore na raiz do projeto
echo -e 'node_modules\n' > .gitignore
~~~

#### Passo 2: Instalar o TypeScript como uma dependência do projeto

Uma **dependência** é um pacote ou biblioteca externa que um projeto de software precisa para funcionar corretamente. Ela fornece funcionalidades que são reutilizadas no projeto, evitando que o desenvolvedor tenha que escrever tudo do zero. Dependências podem incluir frameworks, bibliotecas de manipulação de dados, ferramentas de teste ou qualquer outro código que a aplicação necessite para implementar suas funcionalidades.

No contexto do **Node.js**, as dependências são gerenciadas pelo **npm (Node Package Manager)** e são registradas no arquivo `package.json` do projeto.

As dependências podem ser classificadas em duas categorias principais: **dependências de produção** e **dependências de desenvolvimento**, cada uma com um propósito específico no ciclo de vida da aplicação.

- **Dependências de Produção**: são pacotes ou bibliotecas que são essenciais para o funcionamento da aplicação em ambientes de produção. Isso significa que a aplicação não pode rodar corretamente sem essas dependências. Elas são instaladas e incluídas no ambiente de produção, já que são necessárias durante a execução do código.

- **Dependências de Desenvolvimento**: são pacotes ou bibliotecas que só são necessárias durante o processo de desenvolvimento, mas não são utilizadas no ambiente de produção, quando a aplicação está em execução. Elas ajudam no ciclo de desenvolvimento, testes, _linting_, transpilação ou qualquer outra tarefa que seja importante para o desenvolvedor, mas que não faz parte do código que é executado em produção.

O TS será instalado localmente como uma dependência de desenvolvimento do projeto (flag `-D`).

~~~bash
npm install -D typescript
~~~
