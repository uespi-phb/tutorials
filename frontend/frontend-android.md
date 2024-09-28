<p><img src="../images/android.png" width=128 /></p>

># **Android SDK**

Desenvolvimento de software para Android é o processo pelo qual um novo aplicativo é criado para o sistema operacional Android. Para produção de aplicativos para Android é necessário utilizado o Android _Software Development Kit_ (SDK).

O _Software Development Kit_ (SDK) do Android inclui uma lista de várias ferramentas de desenvolvimento, tais como: debugger, bibliotecas, um emulador baseado em QEMU, documentação, códigos de exemplo e tutoriais.

> ## Instalação no Linux

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
Para que as instruções a seguir funcionem corretamente é necessário que as Variáveis de Ambiente do Projeto tenham sido configuradas.
</div>

> Configuração das [Variáveis de Ambiente](../common/env.md) do Projeto.

Edite o arquivo **~/.devrc** e acrescente ao final:
~~~bash
export ANDROID_BASE="$DEV_BASE/android"
export ANDROID_USER_HOME="$ANDROID_BASE/.android"
export ANDROID_SDK_ROOT="$ANDROID_BASE/sdk"
export ANDROID_EMULATOR_HOME="$ANDROID_USER_HOME"
export ANDROID_AVD_HOME="$ANDROID_EMULATOR_HOME/avd"
export ANDROID_HOME="$ANDROID_SDK_ROOT"

export PATH="$ANDROID_HOME/cmdline-tools/latest/bin:$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$PATH"
~~~

Ao concluir a edição do arquivo **~/.bashrc** execute o comando:
~~~bash
source ~/.bashrc
~~~

Instale o Android SDK e outras ferramentas:

1. Navegue para a página oficial do [Android](https://developer.android.com/studio#downloads)
2. No final da página, baixe o arquivo de instalação do _SDK Manager Command Line Tools_ na pasta **~/Downloads**:

Execute os seguintes comandos no terminal:
~~~bash
cd $DEV_BASE

mkdir -p $ANDROID_HOME
unzip -d $ANDROID_HOME ~/Downloads/commandlinetools-linux-*.zip
rm -f ~/Downloads/commandlinetools-linux-*.zip

cd $ANDROID_HOME

mkdir cmdline-tools/latest
mv cmdline-tools/{bin,lib,source.properties,NOTICE.txt} cmdline-tools/latest

sdkmanager --version

# Exibe pacotes do canal 0 (stable)
sdkmanager --channel=0 --list

# Obtém a versão atual do Android (33 no exemplo abaixo)
yes | sdkmanager --channel=0 "platforms;android-33" "build-tools;33.0.2" "platform-tools" "tools" "emulator"

# Atualiza todos os pacotes instalados
sdkmanager --update

# Aceita as licenças do Android SDK
yes | sdkmanager --licenses
~~~
