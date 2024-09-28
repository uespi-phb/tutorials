<p><img src="../images/flutter.svg" width=128 /></p>

># **Flutter**

Flutter é um kit de desenvolvimento de interface de usuário (UI toolkit e framework), de código aberto, criado pela empresa Google em 2015. Baseado na linguagem de programação Dart, possibilita a criação de aplicativos compilados nativamente, para os sistemas operacionais Android, iOS, Windows, Mac, Linux e Web.

> ## Instalação no Linux Ubuntu

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
Para que as instruções a seguir funcionem corretamente é necessário que as Variáveis de Ambiente do Projeto tenham sido configuradas.
</div>

> Configuração das [Variáveis de Ambiente](../common/env.md) do Projeto.

Edite o arquivo **~/.devrc** que conterá todas as variáveis do ambiente de desenvolvivmento
~~~bash
# Flutter & Dart
export FLUTTER_BASE="$DEV_BASE/flutter"
export PATH="$FLUTTER_BASE/bin:$PATH"
~~~

Ao concluir a edição do arquivo **~/.devrc** execute os comandos:
~~~bash
source ~/.bashrc

mkdir -p $FLUTTER_BASE

# Observe o "." no final do comando
git clone https://github.com/flutter/flutter.git -b stable .

flutter upgrade
flutter --version

flutter config --android-sdk $ANDROID_HOME

yes | flutter doctor --android-licenses

# Ignore o aviso "[!] Android Studio (not installed)"
flutter doctor
~~~

O projeto Flutter do front-end MIES deve ser baixado do repositório no Github.

O comando abaixo mostra como o projeto foi inicialmente criado, antes de seu enviado para o repositório:
~~~bash
cd $MIES_BASE

flutter --create --project-name frontend --platform=android,ios,web ./frontend
~~~

> ## Baixar o Projeto Front-end do GitHub

Abra um terminal e vá para o diretório base do projeto Minha IES definido pela variável de ambiente [MIES_BASE](../common/env.md):
~~~bash
cd $MIES_BASE
git clone git@github.com:minha-ies/frontend.git
~~~

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
Os repositórios do Projeto Minha IES são privados. Você precisa ter permissão de uso para baixar o código fonte.
Para obter permissão entre em contato com um dos coordenadores do projeto.
</div>

> ## Estrutura do Projeto

| Pasta    | Descrição | Auto Gerado |
|----------|-----------|-------------|
|.git      | Repositório local do git | Não |
| android  | Contém os executáveis para Android | Sim |
| ios      | Contém os executáveis para IOS | Sim |
| web      | Contém os executáveis para Web | Sim |
| docs     | Documentação do projeto Front-end | Não |
| lib      | Código fonte do front-end | Não |
| tests    | Código fonte de testes do front-end | Não |
