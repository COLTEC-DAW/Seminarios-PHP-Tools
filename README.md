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

A primeira, Messages, apresenta mensagens que você quiser mostrar (como um printf no C), como variáveis e strings, como no exemplo acima.

A segunda, Request, apresenta os detalhes da requisição que foi feita para aquela página, com os detalhes das variáveis **$_GET, $_POST, $_COOKIE** e **$_SERVER**.

A terceira, Timeline, mostra o que aconteceu na sua página com o passar do tempo.

A quarta, Exceptions, mostra os erros "pegados" pelo seu código, como num trecho com "try catch", no qual você "pega" uma exceção caso um erro aconteça.

A última, Database, se trata de informações sobre o banco de dados que o php está tratando, mostrando todos os comandos de teste feitos e dizendo quais comandos deram certo e quais comandos não funcionaram por algum motivo.

Com todas essas possibilidades, uma aplicação web em php de grande porte tem uma grande organização quanto a visualização do que está acontecendo na página, quanto às requisições, cookies, variáveis, erros e o banco de dados. Essa ferramenta traz uma possibilidade de realmente debugar e testar sua aplicação web com bastante organização e bem facilmente.

## Ferramentas Similares

1. **PHP MD**
- ([PHP Mess Detector](https://phpmd.org/)) é uma ferramenta "user friendly" e fácil de configurar que procura por possíveis problemas no código fonte inserido, erros esses como possiveis bugs, código não-otimizado, expressões complicadas demais e variáveis não utilizadas.

2. **Kint**
- ([Kint](https://github.com/kint-php/kint)) é uma ferramenta que tem como proposta mostrar a informação de debug da maneira mais limpa o possível, basicamente um "var_dump() e debug_backtrace() com esteroides".

3. **Krumo**
- ([Krumo](https://xdebug.org/index.php)) é uma ferramenta que literalmente se diz uma reposição de "print_r() e var_dump()". Sua função é mostrar informação estruturada sobre qualquer variável PHP.