<p><img src="../images/java.svg" width=128 /></p>

># **Ambiente de Desenvolvimento Java**

Java é uma linguagem de programação orientada a objetos desenvolvida na década de 90 pela empresa Sun Microsystems. Diferente das linguagens de programação modernas, que são compiladas para código nativo, Java é compilada para um bytecode que é interpretado por uma máquina virtual (Java Virtual Machine, abreviada JVM).

> ## Instalação no Linux Ubuntu

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
Para que as instruções a seguir funcionem corretamente é necessário que as <a href="../common/env.md">Variáveis de Ambiente</a> do Projeto tenham sido configuradas.
</div>

Instale o OpenJDK no sistema.

```bash
sudo apt update
sudo apt install -y openjdk-17-jdk
```

Defina o valor da  variável de ambiente `JAVA_HOME`. Para obter o local de instalação do Java, execute o comando abaixo e copie o texto exibido na tela.
```bash
dirname $(dirname $(readlink -f $(which java)))

# Example: /usr/lib/jvm/java-17-openjdk-amd64
```

Edite o arquivo **~/.devrc** e acrescente:

```bash
# Java SDK
export JAVA_HOME="/usr/lib/jvm/java-17-openjdk-amd64"
export PATH="$PATH:$JAVA_HOME"
```

Ao concluir a edição do arquivo **~/.devrc** execute os comandos:
```bash
source ~/.devrc

java -version
```
