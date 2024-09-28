<p><img src="../images/java.svg" width=128 /></p>

># **Java**

Java é uma linguagem de programação orientada a objetos desenvolvida na década de 90 pela empresa Sun Microsystems. Diferente das linguagens de programação modernas, que são compiladas para código nativo, Java é compilada para um bytecode que é interpretado por uma máquina virtual (Java Virtual Machine, abreviada JVM).

> ## Instalação no Linux

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
Para que as instruções a seguir funcionem corretamente é necessário que as Variáveis de Ambiente do Projeto tenham sido configuradas.
</div>

> Configuração das [Variáveis de Ambiente](../common/env.md) do Projeto.

Edite o arquivo **~/.devrc** e acrescente ao final:

~~~bash
# Java SDK
export JAVA_HOME="/usr/lib/jvm/java-11-openjdk-amd64"
export PATH="/usr/lib/jvm/java-11-openjdk-amd64:$PATH"
~~~

Ao concluir a edição do arquivo **~/.devrc** execute os comandos:
~~~bash
source ~/.bashrc

sudo apt install -y default-jre default-jdk
~~~

