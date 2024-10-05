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

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
ATENÇÃO: todos os procedimentos de configuração dependem das variáveis definidas em <a href="../common/env.md">Variáveis de Ambiente</a>.
</div>


### 1. Instalação do Node.js, NPM e NVM

O TypeScript (TS) é compilado para JavaScript (JS) em um processo conhecido como transpilação. Para se executar código JS fora do navegador, em um ambiente backend por exemplo, é necessário ter instalado no sistema um ambiente de execução JS, como o Node.js.

O Node.js permite executar scripts fora de um navegador web, especificamente no lado do servidor. Ele foi lançado em 2009 por Ryan Dahl, e revolucionou o desenvolvimento web ao permitir que JS, tradicionalmente restrito ao frontend (navegadores), fosse utilizado no backend. O Node.js é baseado no mecanismo V8 da Google, que é o motor JS que também alimenta o Google Chrome.

O Node.js vem acompanhado do utilitário NPM (_Node Package Manager_), o gerenciador de pacotes padrão para JS, que permite que os desenvolvedores instalem e gerenciem bibliotecas e dependências de forma simples e eficiente. O NPM possui um vasto repositório de pacotes reutilizáveis para diversas funcionalidades, desde ferramentas de desenvolvimento até bibliotecas complexas para autenticação, banco de dados, comunicação em tempo real entre muitas outras.

O NVM (Node Version Manager) é uma ferramenta essencial para desenvolvedores que precisam gerenciar várias versões do Node.js em um único sistema. Ele permite instalar, alternar e manter múltiplas versões do Node.js, facilitando o desenvolvimento de diferentes projetos com requisitos variados.

##### Passo 1: Atualizar os pacotes do sistema e dependências necessárias

Antes de iniciar a instalação, certifique-se de que todos os pacotes do seu sistema estão atualizados e que possui as dependências necessárias instaladas. No terminal, execute:

```bash
sudo apt -y update
sudo apt -y install build-essential libssl-dev curl
```

##### Passo 2: Instalar o NVM

Crie a variável de ambiente que define o local de instalação do NVM acrescentando os seguintes comandos no final do arquivo `~/.devrc`:

```bash
# NVM home
export NVM_DIR="$DEV_APPS/nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"

# Put NVM_DIR in PATH if not already
[[ ":$PATH:" != *":$NVM_DIR:"* ]] && export PATH="${PATH}:$NVM_DIR"
```

Atualize o ambiente, instale o NVM no local especificado ($NVM_DIR) e teste sua instalação:
```bash
source ~/.bashrc
mkdir $NVM_DIR
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.1/install.sh | bash

nvm -v
```
> **Nota**: A versão do NVM (`v0.40.1` neste exemplo ) pode mudar conforme novas versões sejam lançadas. Você sempre pode verificar a versão mais recente no [repositório do NVM no GitHub](https://github.com/nvm-sh/nvm).

Se o comando `nvm -v` retornar um número de versão, isso significa que o NVM foi instalado com sucesso.

##### Passo 3: Instalar o Node.js e o NPM

Agora que o NVM está instalado, você pode usá-lo para instalar qualquer versão do Node.js. Por exemplo, para instalar a versão mais recente, execute:

```bash
nvm install node

node -v
npm -v
```

Isso instalará a versão mais recente do Node.js na pasta `$NVM_DIR`. Se a instalação tiver sido bem sucedida os comandos `node -v` e `npm -v` irão apresentar as suas respectivas versões.

##### Passo 4: Instalar Outras Versões e/ou Definir uma Versão Padrão do Node.js (opcional)

Se você precisar de uma versão específica do Node.js (por exemplo, 14.x), você pode instalar essa versão com o comando:

```bash
nvm install 14
```

Depois de instalar uma ou mais versões do Node.js, você pode escolher qual versão usar como padrão. Para usar a versão 14, por exemplo, digite:

```bash
nvm use 14
```

Se você quiser definir essa versão como a versão padrão para todas as sessões futuras do terminal, execute:

```bash
nvm alias default 14
```

Para ver todas as versões do Node.js que você já instalou com o NVM, execute:

```bash
nvm ls
```

Esse comando listará todas as versões instaladas e indicará qual delas está atualmente em uso.

Se você tiver várias versões do Node.js instaladas, pode alternar entre elas facilmente. Por exemplo, para mudar para a versão 16, use:

```bash
nvm use 16
```

### 2. Instalar o TypeScript

Agora que o Node.js e o NPM estão instalados, o próximo passo é instalar o **TypeScript**, o qual pode ser configurado local ou globalmente. A escolha entre essas formas depende de como você deseja utilizar o TypeScript no projeto ou no sistema.

##### Instalação Local
Instalar o TypeScript localmente significa que ele será instalado dentro de um projeto específico, ficando disponível apenas para aquele projeto. Ele será listado como uma dependência no arquivo package.json, e a versão instalada será usada apenas no escopo desse projeto.

As principais vantagens da instalação local são:
- Mantém a consistência da versão do TypeScript usada no projeto, o que é importante quando diferentes projetos usam diferentes versões.
- O TypeScript não interfere com outros projetos no sistema.

##### Instalação Global
Instalar o TypeScript globalmente significa que ele será acessível em qualquer lugar do sistema, permitindo que você use o comando `tsc` para compilar TypeScript de qualquer projeto sem precisar instalá-lo localmente. Isso é útil se você deseja ter uma única versão do TypeScript disponível em todo o sistema.

Neste tutorial optaremos pela **instalação local** do TypeScript.

##### Passo 1: Criar um novo projeto (ou usar um existente)

Instalar o TS localmente significa que ele será configurado como um pacote de um projeto específico. Desta forma, antes mais nada precisamos criar um novo projeto no Node.js e configurá-lo utilizando o NPM.

```bash
# Create the root project folder
mkdir $DEV_ROOT/myproject
# Change to the project folder
cd $DEV_ROOT/myproject
# Create a new Node.js project inside folder
npm init -y
```

O comando `npm init` cria um novo projeto gravando suas configurações no arquivo `package.json` e instala suas dependências dentro da pasta `node_modules`. Esta pasta sempre poderá ser gerada automaticamente a partir das configurações contidas no arquivo `package.json` por meio do comando `npm init`. 

Desta forma, não é desejável que a pasta `node_modules` seja incluída em nosso repositório Git. Para evitar isso devemos instruir o Git para ignorar esta pasta criando o arquivo `.gitignore`.

```bash
# Create .gitignore file in project root
echo -e 'node_modules\n' > .gitignore
```

##### Passo 2: Instalar o TypeScript como uma dependência do projeto

Uma **dependência** é um pacote ou biblioteca externa que um projeto de software precisa para funcionar corretamente. Ela fornece funcionalidades que são reutilizadas no projeto, evitando que o desenvolvedor tenha que escrever tudo do zero. Dependências podem incluir frameworks, bibliotecas de manipulação de dados, ferramentas de teste ou qualquer outro código que a aplicação necessite para implementar suas funcionalidades.

No contexto do **Node.js**, as dependências são gerenciadas pelo **npm (Node Package Manager)** e são registradas no arquivo `package.json` do projeto.

As dependências podem ser classificadas em duas categorias principais: **dependências de produção** e **dependências de desenvolvimento**, cada uma com um propósito específico no ciclo de vida da aplicação.

- **Dependências de Produção**: são pacotes ou bibliotecas que são essenciais para o funcionamento da aplicação em ambientes de produção. Isso significa que a aplicação não pode rodar corretamente sem essas dependências. Elas são instaladas e incluídas no ambiente de produção, já que são necessárias durante a execução do código.

- **Dependências de Desenvolvimento**: são pacotes ou bibliotecas que só são necessárias durante o processo de desenvolvimento, mas não são utilizadas no ambiente de produção, quando a aplicação está em execução. Elas ajudam no ciclo de desenvolvimento, testes, _linting_, transpilação ou qualquer outra tarefa que seja importante para o desenvolvedor, mas que não faz parte do código que é executado em produção.

O TS será instalado localmente como uma dependência de desenvolvimento do projeto (flag `-D`).

```bash
npm install -D typescript

npx tsc -v
```
Se a instalação tiver sido bem sucedida, o comando `npx tsc -v` deverá exibir a versão do TS que foi instalada.

Como o TS foi instalado como uma dependência do projeto, você também pode verificar sua instalação analisando o arquivo de configuração do projeto Node.js `package.json` no campo `devDependencies`.

```json
{
  "name": "myproject",
  "version": "1.0.0",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "description": "",
  "devDependencies": {
    "typescript": "^5.6.2"
  },
  "engines": {
    "node": "20.x"
  }
}
```

##### Passo 3: Criar um arquivo de configuração do TypeScript no projeto

Para criar um arquivo de configuração do TypeScript em um projeto, você precisa gerar o arquivo `tsconfig.json`, que serve como um ponto central de configuração para o compilador. Ele especifica as opções de compilação, diretórios, arquivos, e o comportamento do compilador.

###### Configuração TS: Targets

Vamos criar um arquivo de configuração inicial personalizado onde iremos definir alguns parâmetros importantes. Para isto altere o conteúdo do arquivo `tsconfig.json` para:

```json
{
  "compilerOptions": {
    "target": "es2022",
    "rootDir": ".",
    "outDir": "./dist",
    "skipLibCheck": true,
    "sourceMap": true,
    "forceConsistentCasingInFileNames": true
  },
  "include": [
    "./src"
  ]
}
```
Aqui está uma explicação sucinta de cada uma das opções do arquivo **`tsconfig.json`** fornecido:

- **`target`**: `"es2022"`
  Define a versão do ECMAScript (JavaScript) para a qual o TypeScript irá transpilar o código. O valor `es2022` especifica que o código deve ser convertido para a versão ECMAScript 2022. Dependendo da versão, o código será convertido para suportar funcionalidades mais antigas ou mais modernas do JavaScript.

- **`outDir`**: `"./dist"`
  Especifica o diretório de saída para os arquivos compilados (JavaScript). Neste caso, os arquivos transpilados irão para a pasta **`./dist`**.

- **`rootDir`**: `"."`
  Define o diretório raiz dos arquivos de entrada (TypeScript). O TypeScript irá considerar `.` como a pasta raiz que contém os arquivos TypeScript que serão transpilados. É útil para garantir que a estrutura do diretório seja mantida na saída.

- **`skipLibCheck`**: `true`
  Ignora a verificação de tipo nos arquivos de declaração de biblioteca. Definido como `true` para acelerar a compilação, ignorando a verificação de tipos em arquivos externos de bibliotecas, que geralmente já estão bem testados.

- **`sourceMap`**: `true`
  - Gera arquivos **source map** ao compilar o TypeScript. Esses arquivos permitem que ferramentas de depuração (como navegadores) mapeiem o código compilado de volta ao código-fonte TypeScript original.

- **`forceConsistentCasingInFileNames`**: `true`
  - Garante que a diferenciação de maiúsculas e minúsculas em nomes de arquivos seja consistente entre diferentes sistemas operacionais.
  
- **`include`**: `["./src"]`
  - Especifica quais arquivos e diretórios devem ser incluídos no processo de compilação. Neste caso, apenas arquivos dentro da pasta **`./src`** serão compilados.

Por ser um ambiente de linha de comando, muitas vezes é necessário digitar comandos complexos para executar determinadas tarefas. Para facilitar esta tarefa é bastante comum criarmos _scripts_ no arquivo `package.json`. 

Tais _scripts_ são importantes para automatizar tarefas recorrentes e simplificar comandos complexos no desenvolvimento de projetos Node.js. Eles ajudam a padronizar o ambiente de trabalho, garantindo que todos os desenvolvedores usem os mesmos comandos e ferramentas, promovendo consistência em equipes de desenvolvimento. Assim, esses _scripts_ são uma forma simples de documentar os processos do projeto, tornando mais fácil a execução de tarefas como compilar, testar ou rodar _linters_, com comandos curtos e fáceis de lembrar.

Vamos criar um _script_ chamado "_build_" para realizar a compilação do nosso projeto, além de realizar alguns ajustes no arquivo `package.json`.

```json
{
  "name": "myproject",
  "description": "My Sample Project",
  "author": "Fulano de Tal",
  "license": "ISC",
  "version": "1.0.0",
  "main": "./dist/main/index.js",
  "scripts": {
    "build": "tsc"
  },
  "keywords": [],
  "devDependencies": {
    "typescript": "^5.6.2"
  }
}
```

Também vamos criar o arquivo principal de nosso projeto que tipicamente (mas não obrigatoriamente) se chama `index.ts`. Em seguida executaremos o _script_.

```bash
mkdir -p ./src/main
echo "console.log('Hello, World.')" > src/main/index.ts

npm run build
```
Após a execução do _script_, o compilador do TS irá criar a pasta `./dist` contendo os arquivos TS do projeto compilados para JS. Como a opção `sourceMap` está habilitada no `tsconfig.json`, para cada arquivo JS gerado em `./dist`, será criado um arquivo de mapeamento com extensão `.map`.

Uma boa prática adotada durante o _build_ de projetos TS é remover todos os arquivos da pasta `./dist` antes da compilação. Isto garante que os arquivos presentes na pasta sempre correspondam aos arquivos presentes na pasta `./src`.
```json
{
  // ...
  "scripts": {
    "start": "node dist/main/index.js",
    "build": "rm -rf ./dist && tsc"
  },
  // ...
}
```
> **Nota**: O comando `rm -rf` funciona apenas no Linux e MacOS. No Windows utilize o comando `rmdir /q /s`

###### Configuração TS: Modules

Nesta seção iremos configurar o TS para suportar a importação de módulos JS. Para isto altere o arquivo `tsconfig.json` para:

```json
{
  "compilerOptions": {
    "target": "es2022",
    "rootDir": ".",
    "outDir": "./dist",
    "skipLibCheck": true,
    "sourceMap": true,
    "forceConsistentCasingInFileNames": true,
    "module": "commonjs",
    "moduleResolution": "node",
    "esModuleInterop": true,
    "baseUrl": "./src",
    "paths": {
      "@/tests/*": [
        "./tests/*"
      ],
      "@/*": [
        "./src/*"
      ],
    }
  },
  "include": [
    "./src",
    "./tests"
  ]
}
```
- **`module`: `"commonjs"`**
   Define o sistema de módulos a ser usado no código transpilado. O `commonjs` é o padrão usado pelo Node.js e é amplamente suportado em módulos JavaScript. Isso permite usar `require` e `module.exports` no código gerado, em vez de `import` e `export`.

- **`moduleResolution`: `"node"`**
    Especifica como o TypeScript resolve os módulos importados. A opção `node` define o usa da estratégia de resolução de módulos do Node.js, procurando pacotes primeiro no diretório local, depois na pasta `node_modules`.

- **`esModuleInterop`: `true`**
   - Facilita a interoperabilidade entre módulos ECMAScript e CommonJS. Com `esModuleInterop`habilitado, o TypeScript permite usar sintaxe de `import` de estilo ES6 para pacotes que utilizam o padrão CommonJS, como o `require`. Isso evita erros ao usar bibliotecas comuns do Node.js com a sintaxe moderna de módulos.

- **`baseUrl`: `"./src"`**
   Define o diretório base para resolver módulos relativos. A opção `./src` significa que o TypeScript tratará o diretório `src` como o ponto de partida ao resolver importações relativas no projeto, facilitando o uso de caminhos mais curtos.

- **`paths`:**
   Especifica atalhos (_aliases_) para caminhos de importação, tornando o código mais organizado e legível.
   - `"@/*": ["*"]`: Define um _alias_ `"@/"` que corresponde ao diretório raiz do `src`. Isso permite que você use `@/` para referenciar arquivos dentro da pasta `src`.
   - `"@/tests/*": ["../tests/*"]`: Define um alias para arquivos de teste, permitindo que você importe arquivos da pasta `tests` usando o atalho `@/tests/` ao invés de caminhos relativos longos.

Essas configurações otimizam a maneira como o TypeScript trata módulos, dependências e importações, proporcionando flexibilidade e organização no código.

Observe que foi acrescentada a pasta `./tests` na configuração, o que fará o TS compilar os arquivos de teste para a pasta `./dist`. Porém, os arquivos de teste só são utilizados durante o desenvolvimento do projeto, isto é, não são necessários para o código de produção. 

Para evitar que os arquivos de testes sejam compilados juntos com o código de produção, criaremos uma configuração específica para a construção apenas do código de produção. Para isso, criaremos o arquivo `tsconfig.build.json`:
```json
{
  "extends": "./tsconfig.json",
  "exclude": [
    "./tests"
  ]
}
```
Agora devemos atualizar nosso _script_ `build` para utilizar este arquivo de configuração:
```json
{
  // ...
  "scripts": {
    "start": "node dist/main/index.js",
    "build": "rm -rf ./dist && tsc -p tsconfig.build.json"
  },
  // ...
}
```
##### `module-alias`

O `module-alias` é uma biblioteca do Node.js que permite criar atalhos (_alias_) para caminhos de importação em projetos JavaScript ou TypeScript. Com ele, você pode evitar o uso de caminhos longos ou complexos ao importar arquivos, substituindo-os por atalhos mais simples. Isso melhora a legibilidade e a manutenção do código.

Para utilizar o `module-alias` instale os seguintes pacotes:
```bash
npm install module-alias
npm install -D @types/module-alias @types/node
```

Para que o `module-alias` funcione é necessário que o mesmo seja carregado no início do arquivo fonte principal do projeto. Para tanto, crie/altere os seguintes arquivos:

`./src/config/module-alias.ts`
```typescript
import { addAlias } from 'module-alias'
import { resolve } from 'path'

addAlias('@', resolve('dist'))
```

`./src/main/index.ts`
```typescript
//
// Must be the very first import in application
//
import '../config/module-alias'
//
//
console.log('Hello, world.')

```

###### Configuração TS: Strict  Mode

O **strict mode** do TypeScript é uma configuração que ativa uma série de verificações rigorosas de tipo para garantir mais segurança e robustez no código. Ele habilita várias opções que forçam o desenvolvedor a ser mais explícito e cuidadoso com tipos, ajudando a prevenir erros comuns.

Quando ativado (`"strict": true` no `tsconfig.json`), são habilitada as seguintes verificações:

- **`noImplicitAny`**: Obriga a declarar o tipo de uma variável explicitamente quando este não pode ser inferido.
- **`strictNullChecks`**: Garante que variáveis que podem ser `null` ou `undefined` sejam tratadas adequadamente.
- **`strictFunctionTypes`**: Verifica com rigor a compatibilidade de tipos de funções.
- **`strictBindCallApply`**: Verifica corretamente os tipos de métodos como `bind`, `call` e `apply`.
- **`alwaysStrict`**: Emite código JavaScript no modo estrito (`"use strict"`).
- **`strictPropertyInitialization`**: Exige a inicialização de propriedades de classes no construtor.

O **strict mode** impõe verificações mais rígidas de tipos, tornando o código mais seguro e menos propenso a erros, mas também exige mais precisão do desenvolvedor na declaração e uso de tipos.

Acrescente a linha `"strict": true` ao arquivo `jsconfig.json`. A versão final do arquivo de configuração do TS deverá ser similar à apresentada abaixo:

```json
{
  "compilerOptions": {
    "target": "es2022",
    "rootDir": ".",
    "outDir": "./dist",
    "skipLibCheck": true,
    "sourceMap": true,
    "forceConsistentCasingInFileNames": true,
    "module": "commonjs",
    "moduleResolution": "node",
    "esModuleInterop": true,
    "strict": true,
    "baseUrl": "./src",
    "paths": {
      "@/tests/*": [
        "./tests/*"
      ],
      "@/*": [
        "./src/*"
      ],
    }
  },
  "include": [
    "./src",
    "./tests",
  ]
}
```

##### Passo 4: Configurar o Linter para o TS

Um _linter_ é uma ferramenta usada para analisar o código fonte de forma estática (sem executá-lo) para identificar problemas de estilo, más práticas e erros potenciais. Ele ajuda a garantir que o código siga padrões de qualidade e consistência, apontando problemas como:

- Violação de convenções de codificação.
- Uso de variáveis não definidas.
- Erros de sintaxe ou lógica.
- Problemas de formatação, como indentação incorreta ou espaçamento.

Um _linter_ pode ser configurado para seguir regras específicas de um projeto ou de uma equipe de desenvolvimento, promovendo uniformidade e prevenindo _bugs_.

O _ESLint_ é um dos _linters_ mais populares e amplamente usados para JavaScript e TypeScript. Ele permite definir e aplicar um conjunto de regras que verificam a qualidade do código, ajudando a encontrar e corrigir problemas automaticamente ou fornecendo sugestões de melhorias.

Suas principais funcionalidades são:
- **Verificação de sintaxe**: Encontra erros de sintaxe no código.
- **Melhorias de estilo**: Garante que o código siga convenções de estilo, como espaçamento, indentação, uso ou não de ponto e vírgula, etc.
- **Regras personalizáveis**: Permite configurar regras personalizadas, conforme as necessidades do projeto ou time.
- **Plugins**: Suporta _plugins_ para estender suas funcionalidades (suporte para React, Node.js, TypeScript, etc).
- **Autocorreção**: O _ESLint_ pode, em alguns casos, corrigir automaticamente problemas de estilo.

Para instalar o ESLint no projeto execute o seguinte comando:
```bash
npm install -D typescript-eslint @eslint/js @types/node
```

Em seguida crie o seguinte arquivo de configuração do ESLint (`eslint.config.mjs`) na raiz do projeto:
```js
import globals from "globals"
import pluginJs from "@eslint/js"
import tseslint from "typescript-eslint"

export default [
  {
    ignores: [
      "node_modules/*",
      "dist/*"
    ]
  },
  {
    languageOptions: {
      globals: globals.node
    }
  },
  pluginJs.configs.recommended,
  ...tseslint.configs.recommended,
  {
    name: "project/rules",
    rules: {
      "eol-last": ["error", "always"],
      "semi": ["error", "never"]
    }
  },
]
```

Crie os seguintes _scripts_ para simplificar a execução do ESLint no projeto:
```json
// package.json
{
  // ...
  "scripts": {
    "start": "node dist/main/index.js",
    "build": "rm -rf ./dist && tsc -p tsconfig.build.json",
    "lint": "eslint .",
    "lint:fix": "npm run lint -- --fix"
  },
  // ...
}
```

##### Passo 5: Configurar o Jest para o TS

**Testes de software** são fundamentais para garantir a qualidade, confiabilidade e segurança do código. Eles verificam se o software funciona conforme o esperado em diferentes situações, além de prevenir erros e regressões quando novos recursos são adicionados. Aqui estão algumas razões principais para usar testes de software:

1. **Prevenção de erros e regressões**:
   - Testes de software ajudam a identificar e corrigir bugs antes que o código seja implantado em produção. Quando novas funcionalidades são introduzidas, os testes garantem que o comportamento existente não seja afetado, prevenindo **regressões**.

2. **Manutenção e Refatoração**:
   - Em projetos de longo prazo, o código pode ser modificado ou refatorado várias vezes. Testes automatizados garantem que o código ainda funciona corretamente após essas alterações, tornando a manutenção muito mais segura e eficiente.

3. **Documentação viva**:
   - Testes servem como uma forma de documentação que descreve como o código deve funcionar. Eles fornecem uma "descrição executável" de como o sistema deve se comportar, ajudando desenvolvedores a entender melhor as funcionalidades e requisitos.

4. **Confiança no código**:
   - Com uma suíte de testes bem estruturada, as equipes de desenvolvimento ganham confiança para realizar mudanças, sabendo que, se algo quebrar, os testes irão alertá-los imediatamente.

5. **Melhoria da qualidade do software**:
   - Testes ajudam a melhorar a qualidade geral do código, incentivando os desenvolvedores a pensar em casos de uso extremos ou situações excepcionais que podem não ser óbvias durante o desenvolvimento inicial.

Para desevolver aplicações com suporte a testes de software é necessária a instalação e configuração de algum _framework_ de testes, como o Jest, Mocha, Karma, Ava, etc. Netse projeto utilizaremos o **Jest**.

O **Jest** é um **framework de testes automatizados** em JavaScript, desenvolvido pelo Facebook, que permite escrever testes de maneira simples e eficiente. Embora tenha sido projetado inicialmente para testar componentes React, ele é agnóstico à tecnologia, sendo adequado para qualquer aplicação JavaScript ou TypeScript. Suas principais características são:

1. **Configuração simples**:
   - O Jest funciona com configuração mínima ou nenhuma. Ele detecta automaticamente arquivos de teste sem que você precise configurar caminhos complexos ou definir padrões específicos.

2. **Execução paralela de testes**:
   - O Jest executa os testes em paralelo, otimizando o tempo de execução ao utilizar todos os núcleos da CPU. Isso resulta em uma execução mais rápida, especialmente em projetos grandes.

3. **Testes unitários, de integração e de snapshot**:
   - **Testes unitários**: Verificam o funcionamento de unidades menores de código, como funções individuais.
   - **Testes de integração**: Validam a interação entre diferentes partes do código.
   - **Testes de snapshot**: Armazenam a saída renderizada de um componente (ou função) e comparam com a versão anterior para detectar mudanças não intencionais.

4. **Mocking e spying**:
   - O Jest permite **mockar** (simular) dependências, funções ou APIs externas, isolando o código testado. Isso facilita testes de código que dependem de funções externas ou de resultados que variam com o tempo, como APIs.
   - Também suporta **spying**, que permite monitorar se uma função foi chamada e com quais parâmetros.

5. **Cobertura de código**:
   - O Jest gera relatórios detalhados de **cobertura de código**, mostrando quantas linhas, funções e branches do código foram testados. Isso ajuda a identificar partes não cobertas pelos testes.

Para instalar o Jest no projeto execute o seguinte comando:
```bash
npm install -D jest @types/jest ts-jest ts-node babel-jest @babel/core @babel/preset-env
```

Em seguinda crie ou atualize os seguintes arquivos do projeto:

**`jest.config.ts`**
```typescript
import type { Config } from 'jest'

const config: Config = {
  verbose: true,
  collectCoverageFrom: [
    '<rootDir>/src/**/*.ts',
    
  ],
  coverageDirectory: './coverage',
  coverageProvider: 'babel',
  moduleNameMapper: {
    '@/tests/(.+)': '<rootDir>/tests/$1',
    '@/(.+)': '<rootDir>/src/$1',
  },
  roots: [
    '<rootDir>/src',
    '<rootDir>/tests',
  ],
  testEnvironment: 'jest-environment-node',
  transform: {
    '\\.ts$': 'ts-jest'
  }
}

export default config
```
**`package.json`**
```json
{
  // ...
  "scripts": {
    // ...
    "test": "jest --passWithNoTests --no-cache --runInBand",
    "test:watch": "npm test -- --watch",
    "test:coverage": "npm test -- --coverage"  
  },
  // ...
}
```
##### Passo 6: Configurar o Lint Staged

O `lint-staged` é uma ferramenta que permite executar _linters_ (_ESLint_) e outros _scripts_ apenas nos arquivos que estão prestes a ser commitados (ou seja, que foram modificados e estão na "_staging area_" do Git). Ela é comumente usada em conjunto com alguma outra ferramenta para automatizar a execução de verificações de código (_linting_) e formatação antes que um _commit_ seja concluído.

**Por que usar o lint-staged?**

- **Melhoria da Qualidade do Código**: o _linting_ é uma prática que ajuda a detectar problemas de estilo e erros no código antes que ele seja integrado ao repositório. O `lint-staged` garante que os arquivos modificados sejam verificados antes do _commit_, evitando que código problemático seja integrado ao repositório principal.

- **Rapidez na Execução**: em vez de executar o _linter_ em todo o código da base do projeto, o `lint-staged` verifica apenas os arquivos que estão na _staging area_ do Git, ou seja, aqueles que foram alterados. Isso melhora significativamente a desempenho, pois a execução é mais rápida do que rodar o _linter_ em todo o projeto.

- **Automatização do Fluxo de Trabalho**: o `lint-staged` é geralmente configurado para funcionar com _hooks_ do Git. Isso significa que as verificações de _linting_ e formatação podem ser executadas automaticamente sempre que você tentar realizar um _commit_, forçando os desenvolvedores a corrigir problemas antes de subir o código para o respositório

- **Manutenção de Consistência**: em projetos colaborativos, é crucial garantir que todos os desenvolvedores sigam as mesmas práticas e padrões de código. O `lint-staged` força a verificação de padrões de formatação e boas práticas de codificação, ajudando a manter o código consistente entre diferentes membros da equipe.

Para instalar o `lint-staged` no projeto execute o seguinte comando:
```bash
npm install -D lint-staged
```

Depois crie seu arquivo de configuração `.lintstagedrc.json` na raiz do projeto:
```json
{
  "*.ts": [
    "npm run lint:fix",
    "npm run test:staged"
  ]
}
```

Em seguida crie o novo _script_ `test:staged` no `package.json`:
```json
{
  // ...
  "scripts": {
    // ...
    "test": "jest --passWithNoTests --no-cache --runInBand",
    "test:watch": "npm test -- --watch",
    "test:staged": "npm test -- --findRelatedTests",
    "test:coverage": "npm test -- --coverage"  
  },
  // ...
}
```

Agora é necessário garantir que sempre que for feito um _commit_ no projeto, os testes sejam executados para garantir que nenhum código com erro seja integrado ao repositório.

Para isto é necessário definir um script de _hook_ do Git, executando os seguintes comandos:
```bash
# Script to be executed before each commit
cat << EOF > .git/hooks/pre-commit
#!/bin/bash
npx lint-staged
EOF
chmod +x .git/hooks/pre-commit

# Script to be executed before each push
cat << EOF > .git/hooks/pre-push
#!/bin/bash
npm run test:coverage
EOF
chmod +x .git/hooks/pre-push
```

---
[Anterior: Variáveis de Ambiente](./backend-ts.md)
