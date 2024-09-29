<p><img src="../images/env.png" width=128 /></p>

># **Variáveis de Ambiente**

Variáveis de ambiente são valores nomeados dinamicamente que podem afetar o modo como os processos em execução irão se comportar em um computador.

Elas são parte do ambiente no qual um processo executa. Por exemplo, um processo em execução pode consultar o valor da variável de ambiente TEMP para descobrir um local adequado para armazenar arquivos temporários, ou a variável HOME para encontrar a estrutura de diretórios pertencente ao usuário que está executando o processo. Desta forma, elas podem afetar a forma como um processo se comporta.


## Linux Ubuntu

<div style="color: black; background-color: lightgrey; margin: 10px 5px; vertical-align: middle; padding:10px 10px 10px 20px; border-radius: 2px; border-left: 5px solid darkorange">
As variáveis de ambiente aqui definidas serão utilizadas nos demais procedimentos de configuração do ambiente de desenvolvimento.
</div>


Edite o arquivo **~/.devrc** e defina as seguintes variáveis de ambiente em seu sistema.
~~~bash
# Diretório base para as ferramentas de desenvolvimento (Android, Flutter, Node.JS, etc)
export DEV_APPS="/data/dev"
# Localização dos repositórios de projetos
export DEV_ROOT="$HOME/workspace"
~~~

Acrescente o seguinte comando no final do arquivo **~/.bashrc**
~~~
source ~/.devrc
~~~

Em seguida execute os comandos
~~~
source ~/.bashrc

sudo mkdir -p $DEV_APPS
sudo chown $USER $DEV_APPS

mkdir -p $DEV_ROOT
~~~

Instale os seguintes pacotes do Ubuntu com ferramentas para a configuração do ambiente:
~~~bash
sudo apt -y install git curl wget file zip unzip
~~~
