<p><img src="../images/flutter.svg" width=128 /></p>

># **Ambiente de Desenvolvimento Flutter**

O **Flutter** é um **framework de código aberto** desenvolvido pelo Google para a criação de aplicações **nativas** e **multiplataforma**. Ele permite que desenvolvedores criem aplicativos para Android, iOS, web e desktop a partir de uma única base de código. Lançado inicialmente em 2017, o Flutter se destaca pela sua capacidade de renderizar interfaces de usuário de alta performance e de fácil customização.

##### Principais Características:

1. **Desenvolvimento Multiplataforma**:
   - Com o Flutter, você escreve o código uma vez e pode compilá-lo para várias plataformas, como Android, iOS, Web, Windows, macOS e Linux. Isso reduz o tempo de desenvolvimento e facilita a manutenção, já que uma única base de código cobre diversas plataformas.

2. **Linguagem Dart**:
   - Flutter utiliza a linguagem de programação **Dart**, também criada pelo Google. O Dart foi escolhido por seu desempenho e facilidade de uso, além de oferecer suporte a **hot reload**, permitindo que os desenvolvedores vejam alterações no código quase instantaneamente, sem a necessidade de recompilar o aplicativo.

3. **Renderização Nativa**:
   - O Flutter usa um motor de renderização próprio que permite criar interfaces de usuário altamente personalizadas e com animações fluidas. Diferente de outras soluções que utilizam "ponte" (bridge) para interagir com elementos nativos de cada plataforma, o Flutter desenha diretamente na tela, garantindo alta performance.

4. **Componentes e Widgets Personalizáveis**:
   - No Flutter, tudo é um **widget**. Widgets são blocos básicos de construção de uma interface, e o Flutter oferece uma ampla biblioteca de widgets prontos para uso (material design para Android e Cupertino para iOS). Além disso, os desenvolvedores podem criar widgets personalizados com flexibilidade e facilidade.

5. **Hot Reload**:
   - Uma das funcionalidades mais populares do Flutter é o **Hot Reload**, que permite aos desenvolvedores verem as mudanças feitas no código quase instantaneamente na interface da aplicação. Isso acelera muito o processo de desenvolvimento e depuração.

6. **Alto Desempenho**:
   - Como o Flutter não depende de componentes nativos da plataforma e renderiza tudo com seu próprio motor gráfico, o desempenho é próximo ao de aplicativos nativos, sem a sobrecarga de bibliotecas de interface de usuário de terceiros.

##### Aplicações Práticas:

- **Desenvolvimento Mobile**: O Flutter é amplamente utilizado para criar aplicativos móveis para Android e iOS, com empresas como Alibaba, eBay e Google Ads adotando a tecnologia em seus aplicativos.
- **Aplicativos Web e Desktop**: Recentemente, o Flutter expandiu seu suporte para desenvolvimento web e desktop, permitindo que desenvolvedores criem aplicações que funcionam também em navegadores e sistemas operacionais como Windows, macOS e Linux.


## Instalação no Linux Ubuntu

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
Para que as instruções a seguir funcionem corretamente é necessário que as <a href="../common/env.md">Variáveis de Ambiente</a> tenham sido configuradas e os Ambientes <a href="../common/java.md">Java</a> e <a href="./frontend-android.md">Android SDK</a> tenham sido instalados.
</div>

Edite o arquivo **~/.devrc** que conterá todas as variáveis do ambiente de desenvolvivmento
```bash
# Flutter & Dart
export FLUTTER_BASE="$DEV_APPS/flutter"
export PATH="$FLUTTER_BASE/bin:$PATH"
```

Ao concluir a edição do arquivo **~/.devrc** execute os comandos:
```bash
source ~/.bashrc

mkdir -p $FLUTTER_BASE
cd $FLUTTER_BASE

# Note "." at the end of the command
git clone https://github.com/flutter/flutter.git -b stable .

flutter upgrade
flutter --version

flutter config --android-sdk $ANDROID_HOME

yes | flutter doctor --android-licenses

# Ignore warning "[!] Android Studio (not installed)"
flutter doctor
```