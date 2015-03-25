# Configuração de Ambiente RoR
r
teste
r

Este manual apresenta os passos de configuração de ambiente de desenvolvimento em Ruby on Rails uso com Rbenv no Ubuntu, compreendendo uma iniciativa do Grupo de Pesquisa e Extensão em Tecnologia da Informação (GTE) do [Instituto Federal de Educação, Ciência e Tecnologia do Amapá](https://ifap.edu.br/).
[(IFAP)](https://ifap.edu.br/)

## Sumário

* [Sobre o Ruby on Rails](#sobre-o-ruby-on-rails)
* [Atualizações no sistema](#atualiza-oes-no-sistema)
  * [Understanding PATH](#understanding-path)
    * [Upgrading](#upgrading)

## Sobre o Ruby on Rails

Configurar uma estação linux para desenvolver em Ruby on Rails não é uma tarefa complicada como se poderia imaginar. O importante é perceber que há uma lógica de camadas de dependências em infraestrutura que, embora seja válida a ideia de executá-la por meio de scripts, também é interessante saber fazer na mão.

## Atualizações no sistema

### Understanding PATH

Inicialmente, deve-se atualizar o sistema:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```
Feito isso, pode-se passar à instalação dos pacotes:
````
$ sudo apt-get install build-essential openssl libreadline6 libreadline6-dev curl git-core zlib1g zlib1g-dev libssl-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt-dev autoconf libc6-dev libgdbm-dev ncurses-dev automake libtool bison subversion pkg-config libffi-dev nodejs
````

Agora é o momento de instalar o versionador que irá gerenciar o Ruby, que poderá ser o RVM ou Rbenv.
O Ruby enVironment (Version) Manager, mais conhecido como RVM, vem servindo ao seu propósito desde outubro de 2007 pelas mãos do entusiasta Wayne E. Seguin. As informação para sua instalação podem ser encontradas [aqui](https://rvm.io) e mais [aqui](https://github.com/wayneeseguin/rvm).
Por outro lado, o Simple Ruby Version Management, ou simplesmente Rbenv, foi iniciado em agosto de 2011 e vem ganhando a preferência como gerenciador de versão do Ruby, sendo a opção deste tutorial: Uma vez que o git-core já foi instalado, podemos realizar um git clone do Rbenv e do plugin “ruby-build” a partir do repositório do bom Sam Stephenson:
````
$ git clone https://github.com/sstephenson/rbenv.git ~/.rbenv $ git clone https://github.com/sstephenson/ruby-build.git ~/.rbenv/plugins/ruby-build
````
Nota: o “ruby-build” é opcional, embora recomendável. Agora deve-se adicionar ~/.rbenv/bin ao seu `$PATH` : 
````
$ echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.profile
````

E aí você pode perguntar: “mas o que é o path?” [Leonardo Amorim](http://www.vivaolinux.com.br/artigo/O-que-e-PATH-como-funciona-e-como-trabalhar-com-ele) diz: `$PATH:` 
> É uma variável do sistema Linux que indica trajetória (tradução do inglês) dos binários (executáveis dos programas), que podem ser executados sem indicar o caminho completo (geralmente ele é muito longo) da onde eles estão.

Para ativar o rbenv:
````
$ echo 'eval "$(rbenv init -)"' >> ~/.bash_profile
````
E recarregar a sessão do shell: 
````
$ exec $SHELL -l
````
Para quem ainda não sabe, [Leonardo Xavier](http://www.vivaolinux.com.br/artigo/Uma-introducao-ao-shell-%28parte-1%29) diz:
> O shell é um módulo que atua como interface usuário - sistema operacional, possuindo diversos comandos internos que permitem ao usuário solicitar serviços do sistema operacional. O shell também implementa um linguagem simples de programação que permite o desenvolvimento de pequenos programas (os famosos shell scripts)

Finalmente podemos testar o Rbenv:
````
$ rbenv
````

Para visualizar as versões disponíveis para instalação:
````
$ rbenv install -l
````
Para instalar uma versão:
````
$ rbenv install 1.9.3-p392
````

Mesmo sendo possível instalar várias versões, é importante especificar a versão default:
````
$ rbenv global 1.9.3-p392
````
A documentação para definir versões customizada de projetos está [aqui](https://github.com/sstephenson/rbenv#rbenv-local).
Uma vez setada versão do ruby, caberá o [bundler](http://bundler.io/) gerenciar as dependências das gems nos projetos a serem desenvolvidos: 
````
gem install bundler
````
O comando gem está relacionado ao acesso do [RubyGems](https://rubygems.org), projeto de iniciado em abril de 2009 que visa hospedar as gems utilizadas pela comunidade ruby. Atualmente, o [RubyGems](https://rubygems.org) conta 115 rubistas e, em 20/03/15, 98.412 gems.
Finalmente, passamos instalação do rails:
````
$ gem install rails
````

Agora é corre para o abraço e iniciar o desenvolvimento.
