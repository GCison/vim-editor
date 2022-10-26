# Vimrc Guia de configuração para Termux - Customize o editor vim com Mapemaneto de comandos, temas, plugins, autocomplete e muito mais.

## Para extrairmos o máximo de eficicência no ambiente de desenvolvimento com o Editor vim, é necessário explorarmos as inumeras alternativas de configurações e melhorias, disponíveis para o editor mais poderoso de linha de comando.
<br>

Nesse treinamento, vamos aprender juntos a como realizar as configurações necessárias para customizar o seu .vimrc.

Veja os principais tópicos abordados:

 - Configurações básicas
 - Instalação de Plugins
   - para temas
   - para gerenciamento de pastas e arquivos
   - entre outros
 - Dobradura de código
 - Script Vim
 - Linha/barra de status

No termux, existem três possibilidades de tipos de instalação do vim, que são elas:
 - vim
 - vim-gtk
 - vim-python

!!!! Primeiramente antes de iniciar os procedimentos de configuração, cetifique-se de que o vim já esteja instalado. Para isso, utilize o seguinte comando:

    vim --version


### Instalação
Caso ainda não tenha sido instalado, realize o processo de instalação,  através do seguinte comando:

    pkg install vim

ou

    pkg install vim-gtk

ou 

    pkg install vim-python

### Desinstalação
Para realizar o processo de desinstalação do vim, geralmente utilizo os seguintes comandos:

    pkg unistall vim
    pkg remove vim
    apt purge vim

### Arquitetura de configurações
Abaixo, segue a arquitetura básica dos diretórios para configuração

    .vim/
        ├── autoload/
        ├── backup/
        ├── colors/
        └── plugged/

### Criando arquitetura de diretórios
Na raiz do termux, ou seja, na "home" precisamos criar a pasta base do vim:

    mkdir ~/.vim

Em seguida, crie as demais pastas:

    mkdir ~/.vim/autoload
    mkdir ~/.vim/backup
    mkdir ~/.vim/colors
    mkdir ~/.vim/plugged

### Criando o arquivo principal de configuração .vimrc
Agora, vamos criar o arquivo base .vimrc, na raiz do termux "home"

        :> .vimrc

## Configurações básicas do Vim
<br>
Iremos realizar as configurações básicas no arquivo <code>.vimrc</code>. Caso você deseje acrescentar comentários, basta colocar uma aspas simples no início da frase. <code>"comentário aqui...</code>

<br>

Para facilitar o organização do nosso, iremos contruir blocos de instruções de acordo com cada grupo. E o primeiro, será responsável pelas configurações básicas:

No arquivo de configuração <code>.vimrc </code> crie a seguinte instrução:

    " CONFIGURAÇÕES BÁSICAS --------------------------------------------------------- {{{
    " Configurações aqui...

    " }}}

<br>

Feito isso, vamos colocar as primeiras configurações. Todas possuem comentários com uma breve descrição sobre suas funcionalidades

<br>



    " CONFIGURAÇÕES BÁSICAS --------------------------------------------------------- {{{
    " Configurações aqui...

    " habiliti o destaque de sintaxe
    syntax on

    " habilita a exibição de linhas
    set number

    " destaca linha horizontal e vertical do cursor
    set cursorline
    set cursorcolumn

    " Não salve arquivo de backup
    set nobackup

    " Define a largura da tabulação(tab) para 4 espaços
    set shiftwidth=4

    " Define a largura da guia (tab widht) para 4 colunas
    set tabstop=4

    " Use caracteres espaciais em vez de guias.
    set expandtab

    " Não deixe o cursor rolar abaixo ou acima do número N de linhas ao rolar.
    set scrolloff=10

    " Do not wrap lines. Allow long lines to extend as far as the line goes.
    set nowrap

    " While searching though a file incrementally highlight matching characters as you type.
    set incsearch

    " Ignore capital letters during search.
    set ignorecase

    " Override the ignorecase option if searching for capital letters.
    " This will allow you to search specifically for capital letters.
    set smartcase

    " Show partial command you type in the last line of the screen.
    set showcmd

    " Show the mode you are on the last line.
    set showmode

    " Show matching words during a search.
    set showmatch

    " Use highlighting when doing a search.
    set hlsearch

    " Set the commands to save in history default number is 20.
    set history=1000

    " Enable auto completion menu after pressing TAB.
    set wildmenu

    " Make wildmenu behave like similar to Bash completion.
    set wildmode=list:longest

    " There are certain files that we would never want to edit with Vim.
    " Wildmenu will ignore files with these extensions.
    set wildignore=*.docx,*.jpg,*.png,*.gif,*.pdf,*.pyc,*.exe,*.flv,*.img,*.xlsx

    " }}}


## NERDTree
<br>
O NERDTree é um explorador de sistema de arquivos para o editor vim. Usando este plugin, os usuários podem navegar visualmente por hierarquias complexas de diretório, abrir rapidamente arquivos para leitura ou edição e executar operações básicas do sistema de arquivos.

NERDTree é um explorador de sistema de arquivos para o editor vim. Com este plug-in, os usuários podem navegar em visualizações de diretório complexas, abrir arquivos rapidamente para leitura ou edição e realizar operações básicas do sistema de arquivos.

Exemplo | Valor
--------| --------:
Carro   | R$ 45.304,22
Casa    | R$ 109.435,09