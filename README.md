# Gerenciador de dependências: Composer

**Ananda Teodoro**

**Carolina Alves**

**Clarisse Scofield**

## 1. Introdução
Composer é uma ferramenta para gerenciamento de dependências em PHP. Ele permite que você declare as bibliotecas dependentes que seu projeto precisa e as instala para você. Com algumas poucas linhas de configurações você define todas as bibliotecas de terceiros ou mesmo suas que deseja/precisa utilizar em seu projeto, o composer encarrega-se de baixá-las e criar um autoloader deixando-as prontas para uso. 
O Composer funciona, basicamente, através de duas vertentes: um repositório para os pacotes [Packagist](https://packagist.org/) e instruções via linha de comando para gerenciamento dos pacotes (para procurar, instalar, atualizar, remover, etc).
A instalação dos pacotes é feita por projeto e, por default, nada é instalado globalmente - no entanto, suporta um projeto "global" por conveniência através do comando global. Por isso, o Composer é considerado mais um Gerenciador de Dependências do que um Gerenciador de Pacotes.

## 2. Instalação e configuração
### 2.1 Windows
#### Baixando o executável:
Faça o download no seguinte link: [Download](https://getcomposer.org/Composer-Setup.exe).
Com esse download, terá acesso à última versão do Composer. Dessa forma, é possível executar o Composer de qualquer diretório do seu computador.

#### Usando o terminal:

```
php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"

php -r "if (hash_file('SHA384', 'composer-setup.php') === '669656bab3166a7aff8a7506b8cb2d1c292f042046c5a994c43155c0be6190fa0355160742ab2e1c88d40d5be660b410') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"

php composer-setup.php

php -r "unlink('composer-setup.php');"
```

Em seguida, baixe o mais recente compositor.phar no diretório atual. O comando é indicado ao final da última linha de comando do script acima.
 
O script segue a seguinte ordem:

    1. Download do instalador para o diretório atual.

    2. Verificação do instalador SHA-384.

    3. Execução do instalador.

    4. Remoção do instalador.

### 2.2 Linux/Unix/OSX
#### Baixando o executável:
Fazendo o download do executável através do link: [Download](https://getcomposer.org/installer).

A instalação por meio de linha de comando é igual à descrita para o Windows. Agora, apenas execute:
`php composer.phar`

Você pode instalar o Composer em um diretório específico usando  `--install-dir`  e adicionalmente (re)nomeá-lo também usando `--filename`. Ao executar o instalador ao seguir as instruções do download, adicione os seguintes parâmetros:
`php composer-setup.php --install-dir=bin --filename=composer`

Agora, apenas execute `php bin/composer` para executar o Composer.

#### Globalmente:
Pode colocar o Composer PHAR em qualquer lugar que desejar. Depois de executar o instalador seguindo as instruções da página de download, você pode executar isso para mover composer.phar para um diretório que está no seu caminho:
`mv composer.phar /usr/local/bin/composer`

Agora, apenas execute `composer` para executar o Composer em vez de `php composer.phar`.

## 3. Getting Started
### 1º passo: 
Criar um arquivo composer.json, sua estrutura básica é a seguinte:
```
{
    "name": "Nome do projeto",
  	"description": "Breve descrição do que a aplicação se propõe a fazer",
   	"authors":  [
                    {
                            "name": "Seu nome",
                            "email": "seu-email@seu-dominio.com"
                    }
    		    ],
   	"require": 
                {
      			  "php": ">=5.2.8"
  		        }
}
```

### 2º passo:
Incluir pacotes usando o Packagist. Exemplo: 
```
...
    "require": 
    {
        "php": ">=5.2.8",
        "kevinlebrun/slug.php": "1.**"
    }
...

```
Neste caso o pacote é *kevinlebrun/slug.php* e a versão é *1.*.

### 3º passo:
Ir na pasta raíz do seu projeto (que é a mesma que o `_composer.json_` e o `_composer.phar_` se encontram) e rode o comando:  `php composer.phar install`.
Obs: Perceba que na pasta em que encontra-se sua aplicação agora existem a pasta vendor, um arquivo `_composer.phar_` (que já encontrava-se ali), um arquivo `_composer.json_` (que já encontrava-se ali) e um arquivo `_composer.lock_` – que é o arquivo gerado automaticamente após a instalação com sucesso.

### 4º passo:
Crie um arquivo chamado `index.php` e inclua o autoloader do composer conforme o exemplo abaixo e utilizar o pacote requerido.
```
    <?php
    header('Content-Type: text/html; charset=utf-8');

    require 'vendor/autoload.php'; 
    ...
```

Obs: O comando `php composer.phar install` é utilizado somente uma vez em seu repositório. Para qualquer alteração do` _composer.json_` que caracteriza-se como uma nova dependência ou remoção de uma existente deve ser utilizado o comando `php composer.phar update`. O composer também tem um comando para baixar a sua última versão: `php composer.phar self-update`.

## 4. Ferramentas similares
Existem ferramentas similares ao Composer para diversas linguagens de programação. Na linguagem Java, temos as ferramentas Apache Maven, Apache Ivy e Gradle. Em Ruby, temos o RubyGems. C# tem o Nuget e JavaScript tem o NPM e o Yarn.