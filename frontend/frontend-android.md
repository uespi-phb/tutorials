<p><img src="../images/android.png" width=128 /></p>

># **Android SDK**

O **Android SDK (_Software Development Kit_)** é um conjunto de ferramentas de desenvolvimento fornecido pelo Google para criar aplicativos Android. Ele inclui um compilador, bibliotecas, emuladores, e outras ferramentas necessárias para escrever, compilar, depurar e testar aplicativos Android.

### Componentes Principais do Android SDK:

1. **Bibliotecas Android**: Contém as APIs (interfaces de programação de aplicativos) necessárias para interagir com os serviços e funcionalidades do Android, como acesso a hardware, armazenamento, interface do usuário, redes, entre outros.
   
2. **Emulador Android**: Uma ferramenta que simula dispositivos Android, permitindo aos desenvolvedores testar e depurar seus aplicativos sem precisar de um dispositivo físico.
   
3. **Android Debug Bridge (ADB)**: Um utilitário de linha de comando que facilita a comunicação com dispositivos Android conectados. Ele é amplamente usado para depuração, instalação de aplicativos e execução de comandos no dispositivo.

4. **Ferramentas de Build**: Inclui utilitários como o **Gradle** para compilar o código, empacotar recursos e gerar arquivos APK (pacotes de aplicativos Android) que podem ser instalados em dispositivos.

5. **Android Virtual Device (AVD) Manager**: Permite a criação e a configuração de emuladores personalizados, onde os desenvolvedores podem simular diferentes dispositivos Android, com variadas versões de sistema operacional, tamanhos de tela e especificações de hardware.

O Android SDK é essencial para o desenvolvimento de aplicativos Android, oferecendo tudo o que é necessário para criar, testar e implantar aplicativos de forma eficiente. O kit de desenvolvimento é utilizado tanto por desenvolvedores iniciantes quanto por equipes avançadas, e é integrado a IDEs (ambientes de desenvolvimento) como o **Android Studio** para facilitar a criação de aplicativos.

> ## Instalação no Linux

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
Para que as instruções a seguir funcionem corretamente é necessário que as <a href="../common/env.md">Variáveis de Ambiente</a> tenham sido configuradas e o <a href="../common/java.md">Ambiente Java</a> tenha sido instalado.
</div>

Edite o arquivo **~/.devrc** e acrescente ao final:
```bash
export ANDROID_BASE="$DEV_APPS/android"
export ANDROID_USER_HOME="$ANDROID_BASE/.android"
export ANDROID_SDK_ROOT="$ANDROID_BASE/sdk"
export ANDROID_EMULATOR_HOME="$ANDROID_USER_HOME"
export ANDROID_AVD_HOME="$ANDROID_EMULATOR_HOME/avd"
export ANDROID_HOME="$ANDROID_SDK_ROOT"

export PATH="$ANDROID_HOME/cmdline-tools/latest/bin:$ANDROID_HOME/platform-tools:$ANDROID_HOME/tools:$PATH"
```

Ao concluir a edição do arquivo **~/.bashrc** execute o comando:
```bash
source ~/.bashrc
```

Instale o Android SDK e outras ferramentas:

1. Navegue para a página oficial do [Android](https://developer.android.com/studio#downloads)
2. No final da página, baixe o arquivo de instalação do **_Command line tools only_** na pasta **~/Downloads**:

Execute os seguintes comandos no terminal:
```bash
cd $DEV_APPS

mkdir -p $ANDROID_HOME $ANDROID_SDK_ROOT $ANDROID_AVD_HOME
unzip -d $ANDROID_HOME ~/Downloads/commandlinetools-linux-*.zip
rm -f ~/Downloads/commandlinetools-linux-*.zip

cd $ANDROID_HOME

mkdir cmdline-tools/latest
mv cmdline-tools/{bin,lib,source.properties,NOTICE.txt} cmdline-tools/latest

sdkmanager --version

# Show packages available on stabe channel 0
sdkmanager --channel=0 --list

# Install Android current version (33 on example below)
yes | sdkmanager --channel=0 "platforms;android-33" "build-tools;33.0.2" "platform-tools" "tools" "emulator"

# Update installed packages
sdkmanager --update

# Accept Android SDK licenses
yes | sdkmanager --licenses
```
