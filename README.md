# Um guia completo do Editor Vim/.vimrc para alta performance, usabilidade, configuração e customização no ambiente Termux. 

## Para extrairmos o máximo de eficicência no ambiente de desenvolvimento com o editor vim, é necessário conhecermos os fundamentos da ferramenta e explorarmos as inumeras alternativas de configurações e melhorias possíveis, disponíveis para o editor.

### Nesse artigo vamos explorar o vim e todo o seu pontencial, visando o ambiente de senvolvimento no TERMUX.


### Principais tópicos:

 - Introdução
 - História
 - De onde vim e para onde vou?
 - O que você precisa saber antes de começar
 - Como funciona o vim
 - Comandos e edição de arquivos com o vim
   - Modos de configuração
   - Criando arquivos
   - Abrindo arquivos
   - 

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

Primeiramente antes de iniciar os procedimentos de configuração, cetifique-se de que o vim já esteja instalado. Para isso, utilize o seguinte comando:

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
        ├── settings/
        └── plugged/

### Criando arquitetura de diretórios
Na raiz do termux, ou seja, na "home" precisamos criar a pasta base do vim:

    mkdir ~/.vim

Em seguida, crie as demais pastas:

    mkdir ~/.vim/autoload
    mkdir ~/.vim/backup
    mkdir ~/.vim/colors
    mkdir ~/.vim/plugged

___

## Arquivo .vimrc

Nesse ponto, vamos iniciar as configurações do arquivo principal

### Criando o arquivo principal de configuração .vimrc
Agora, vamos criar o arquivo base .vimrc, na raiz do termux "home"

        :> .vimrc

### Organizador Vimrc
Uma coisa que em particular, eu me preocupo, é a forma como programas são criados. E por mais simples que seja, quando eu iniciei as configurações do arquivo <code>.vimrc</code> seguindo alguns exemplos. Algo começou a me incomodar; que foi a grande quantidade de código, contida em um único arquivo. Pois, a medida que novas funcionalidades eram adicionadas, o código começava a mostrar cinais de que a longo prazo, iria ficar difícil de gerenciar.

Então, eu já imaginava a solução "ideal" para tal estrututura, e felizmente eu encontrei duas formas de poder solucionar essa questão, que são elas:

 - Trabalhar com dobramento de código
 - Dividir o .vimrc em vários arquivos, específicos por cada configuração

Utilizei ambas, porém, a segunda é a que eu mais gostei, porque ela segue uma estrutura limpa, e me fez lembrar do SOLID onde cada arquivo tem uma única reponsabilidade.

Para o nosso exemplo, eu irei trabalhar com as duas formas, mas eu recomendo fortemente que você crie o hábito de tentar aplicar a segunda opção _Dividir o .vimrc em vários arquivos, específicos por cada configuração_

No final do nosso curso, nos teremos a seguinte estrutura de arquivos:

 - Plugins de terceiros ().~/.vim/settings/plugins.vim
 - Configurações gerais ().~/.vim/settings/configs.vim
 - Funções personalizadas ().~/.vim/settings/functions.vim
 - Mapeamentos-chave () .~/.vim/settings/mappings.vim

### Criando os arquivos de configurações

Vamos criar os arquivos de configurações, na pasta *settings* que já foi criada nas etapas anteriores. O comando <code>:> file </code> tem a mesma funcionalidade que o comando <code>touch file</code>.

    :> ~/.vim/settings/plugins.vim
    :> ~/.vim/settings/configs.vim
    :> ~/.vim/settings/functions.vim
    :> ~/.vim/settings/mappings.vim

## Configurações básicas do Vim
<br>
Iremos realizar as configurações básicas no arquivo <code>.vimrc</code>. Caso você deseje acrescentar comentários, basta colocar uma aspas simples no início da frase. <code>"comentário aqui...</code>

<br>

Para facilitar a organização das nossas configurações, podemos trabalhar de duas formas:

 - 

No arquivo de configuração <code>.vimrc </code> crie a seguinte instrução:

    " CONFIGURAÇÕES BÁSICAS --------------------------------------------------------- {{{

    " }}}


    " PLUGINS ----------------------------------------------------------------------- {{{

    " }}}


    " MAPPINGS ---------------------------------------------------------------------- {{{

    " }}}


    " VIMSCRIPT --------------------------------------------------------------------- {{{

    " }}}


    " STATUS LINE ------------------------------------------------------------------- {{{

    " }}}

<br>

Feito isso, iniciar aplicando as configurações básicas, conforme exemplo abaixo. Lembrando que cada instrução, está com um comentário resumido, a respeito de suas funcionalidades.

<br>



    " CONFIGURAÇÕES BÁSICAS --------------------------------------------------------- {{{

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

---

### Configurações avançadas
Após a realização desses proce


--- 

## Comandos básicos do Vim

### Buffers

O que é umtampão?

Um buffer é um espaço na memória onde você pode escrever e editar algum texto. Quando você abre um arquivo em Vim, os dados são vinculados a um buffer. Quando você abre 3 arquivos em Vim, você tem 3 buffers.

Saindo do Vim
    
    q

    "sai e fecha todos os outros buffers
    qall 

--- 
## NERDTree
<br>
O NERDTree é um explorador de sistema de arquivos para o editor vim. Usando este plugin, os usuários podem navegar visualmente por hierarquias complexas de diretório, abrir rapidamente arquivos para leitura ou edição e executar operações básicas do sistema de arquivos.

NERDTree é um explorador de sistema de arquivos para o editor vim. Com este plug-in, os usuários podem navegar em visualizações de diretório complexas, abrir arquivos rapidamente para leitura ou edição e realizar operações básicas do sistema de arquivos.

Exemplo | Valor
--------| --------:
Carro   | R$ 45.304,22
Casa    | R$ 109.435,09

## Sessões no vim
Se uma exibição salvar as configurações de uma janela, uma sessão salvará as informações de todas as janelas (incluindo o layout).

criamos uma pasta com três arquivos de exemplo:

Cria split das telas

    :split file?
    :vsplit

Abrir um arquivo em uma determinada janela

    :open file.txt

Salvar uma sessão

    "salva no diretório atual
    :mksession

    " salva em um diretório especifíco
    :mksession path

    " sobrescreve um arquivo de sessão
    :mksession! file

Carregar um sessão

    " comanso do vim
    :source session.vim

    " pelo terminal
    vim -S session.vim

## Tabs (guias)

Cria uma nova guis/tab

    Para abrir em uma nova guia:file2.js
    :tabnew file2.js

    :tabnew file.txt    Open file.txt in a new tab
    :tabclose           Close the current tab
    :tabnext            Go to next tab
    :tabprevious        Go to previous tab
    :tablast            Go to last tab
    :tabfirst           Go to first tab

Para iniciar vim com várias guias, você pode fazer isso a partir do terminal:

    vim -p file1.js file2.js file3.js

desabilita as teclas direcionais do vim

hjkl

Tecla   | FUnção
--------| --------:
h       | Move para a direita
j       | Move para baixo
k       | Move para cima
l       | Move para a direita



    noremap <Up> <NOP>
    noremap <Down> <NOP>
    noremap <Left> <NOP>
    noremap <Right> <NOP>
https://github.com/neoclide/coc.vim/wiki/Language-servers
### Language Servers


### Instalar servidores para linguagens

    CocInstall coc-css coc-html  coc-jsondd