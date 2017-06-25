# Seminários: PHP Tools

## Introdução

O Debug é parte importante do processo de criação de qualquer tipo de aplicação web, então é muito útil ter uma ferramenta funcional e própria para essa finalidade em PHP. Essa ferramenta possibilita que o desenvolvedor procure por erros em seus códigos PHP sem comprometer a lógica do código ou o design da página. O PHP Debug Bar é uma ferramenta bem documentada que funciona como um console - de design simpático e minimalista - que mostra mensagens que você precisar, como variáveis ou mensagens para procurar erros no seu código.

## Instalação & Configuração

1. **Composer** Para instalar o PHP Debug Bar em sistema operacional Windows, primeiro precisamos do utilitário ([Composer](https://getcomposer.org/)) para gerenciar nossas dependências PHP.
2. Para que seja feita a instalação no projeto, deve-se criar um arquivo **composer.json** no mesmo diretório. Depois de criado, devemos especificar a debugbar como dependência no arquivo. Ele deverá ficar parecido com isso:
    ```
    {
        "require": {
            "maximebf/debugbar": ">=1.0.0"
        }
    }
    ```
3. Feito, deve-se executar o comando **composer install para php**:
    $ php composer.phar install

    - Caso não exista um arquivo com esse nome na sua pasta, é possível fazer o download no site oficial do ([Composer](https://getcomposer.org/)).

## Getting Started

Para utilizar a ferramenta, é preciso importá-la nos códigos php do seu projeto, lembrando que pelo design pattern **Don’t Repeat Yourself (DRY)
**, a melhor forma de fazer isso é apenas incluir o código, e não copiá-lo em todos os usos):

    ```
    <?php

    require('vendor/autoload.php');

    use DebugBar\StandardDebugBar;

    $debugbar = new StandardDebugBar();
    $debugbarRenderer = $debugbar->getJavascriptRenderer();

    $debugbar["messages"]->addMessage("hello world!");
    ?>
    <html>
        <head>
            <?php echo $debugbarRenderer->renderHead() ?>
        </head>
        <body>
            ...
            <?php echo $debugbarRenderer->render() ?>
        </body>
    </html>
    ```

O código acima é um exemplo que renderiza a barra de debug e mostra uma mensagem.

A ferramenta possui 5 abas principais, sendo elas **Messages**, **Request**, **Timeline**, **Exceptions** e **Database**.

A primeira, Messages, apresenta 


**Quantidade de alunos por grupo: 3**

**Data: 27/06/2017**

**Valor: 7 pontos**

Esse seminários tem como objetivo apresentar aos colegas de turma as ferramentas existentes para o desenvolvimento de sistemas web, com foco em PHP. O seu grupo deverá escolher um dos seguintes temas abaixo:

- Gerenciador de Dependências ([Composer](https://getcomposer.org/)) -> **Ananda, Carol e Clarisse**
- Bibliotecas de Teste ([PHPUnit](https://phpunit.de/)) -> **Victor, Raul e Francisco**
- Debugging ([PHP Debug Bar](http://phpdebugbar.com/)) -> **Wender, Matheus e Paulo**
- Mockup de dados ([Faker](https://github.com/fzaninotto/Faker)) -> **Gustavo, Eduardo e Lucas Macedo**
- Ambientes virtuais de desenvolvimento ([Vagrant](https://www.vagrantup.com/)) -> **Lucas Paulo, Arthur e Ping**

O trabalho de seu grupo deverá ser dividido em duas partes: Roteiro e Apresentação

## Roteiro

O roteiro deverá ser composto de um arquivo `README.md` descrevendo o tópico selecionado. Seu roteiro deverá ter, **obrigatóriamente**, as seguintes seções:

1. **Introdução:** Essa seção deverá introduzir os conceitos do assunto que seu grupo irá abordar. Você deverá mostrar o problema e como a ferramenta se propõe a resolver esse problema.
2. **Instalação & Configuração:** Nessa seção seu grupo deverá mostrar os passos necessários para instalar e configurar a ferramenta.
3. **Getting Started:** Aqui seu grupo deverá elaborar um pequeno tutorial de uso exemplificando como a ferramenta poderá ser utilizada no desenvolvimento de uma aplicação web. Vocês deverão mostrar passo a passo como utilizar a ferramenta no desenvolvimento de uma aplicação web do mundo real.
4. **Ferramentas similares:** Liste pelo menos três ferramentas que também lidam com o tópico selecionado. Se não encontrar algo similar em PHP procure em outras linguagens (Java, C#, JavaScript, etc.). Fale resumidamente cada uma dessas bibliotecas e referencie para sua página principal.

*OBS: Sinta-se a vontade para adicionar outras seções no documento da forma que você achar conveniente.* 

## Apresentação

Você deverá realizar para a turma uma apresentação entre 10 e 15 minutos sobre o tópico pesquisado pelo seu grupo. Sua apresentação deverá representar uma síntese do que está descrito no roteiro.

Segue alguns critérios que serão avaliados na apresentação (lista não exaustiva):

* Tempo de apresentação
* Organização
* Participação individual
* Profundidade

## Formato de Entrega

Seu grupo deverá fazer um fork desse repositório. Esse fork deverá conter o arquivo `README.md` referente ao roteiro escrito pelo grupo, junto dos slides que serão utilizados na apresentação.

## Escolha do Tema

O grupo poderá selecionar seu tema fazendo um pull request desse repositório e adicionar o nome de seus integrantes após o tópico selecionado. Os temas serão atribuidos por ordem de pull-request.

## Montagem dos Grupos

Os grupos deverão, **obrigatóriamente**, ser compostos por alunos das duas extintas subturmas (103 e 106).
