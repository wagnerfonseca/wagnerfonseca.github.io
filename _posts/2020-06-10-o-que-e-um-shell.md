---
layout: post
title:  "O que é um Shell"
date:   2020-06-10 19:45:46 -0300
categories: linux
tags: linux shell article
type: article
---

Quando nós falamos em *linha de comando* raramente referimos ao *shell*. O *shell* é um programa que pega os comandos digitados nele e passa para o sistema operacional tomar conta. O *shell* é um processador de macros que executa comandos. O termo processador de macros significa funcionalidade em que textos e símbolos são expandidos para criar expressões maiores.

O *shell* é um interpretador de comandos que interage e executa comandos em nome do usuário. O *shell* é a interface entre o usuário e o kernel. 

![user-and-kernel]({{ site.url }}/{{ site.baseurl }}images/posts/2020/2020-06-10-o-que-e-um-shell-01.png){:class="post-image-small-center"}

A sua função é ler uma linha de comando, interpretar o seu significado, executar e devolver o resultado pelas saídas.
Em um *shell* Unix ele é tanto um interpretador de comando e uma linguagem de programação.
*Shells* podem ser usados de forma *interativa* ou *não-interativa*. No modo interativo, ele aceita a entrada digitada através de um teclado. Quando executado de forma não-interativa, executam comandos lendo um arquivo.
Shells também podem executar comandos, ambos síncronos e assíncronos.

Quase todas as distribuições Linux fornecem um programa *shell* do projeto GNU chamado `bash`, um acrônimo de *b*ourne-*a*gain *sh*ell. 

Existem vários shells, sendo os mais comuns o *sh* (chamado de Bourne Shell), e seus derivados, *bash* (Bourne shell again), o *csh* (C Shell), o *Tcsh*(Tenex C Shell), o *ksh* (Korn shell), *zsh* (Zero shell).

Cada usuário tem um shell padrão, ele é definido no arquivo de configuração `/etc/passwd`. E através do comando `chsh` você pode listar as opções de shell instalados em sua máquina e alterar o shell padrão por usuário.

{% highlight stout %}
$ chsh -l 
/bin/sh
/bin/bash
/usr/bin/tmux
/bin/zsh
{% endhighlight %}

### *Builtin* Shell

Shells proporciona um pequeno conjunto de comandos internos (*builtins*) esses *builtins* são implementados internamente pelo próprio shell, em vez de um programa executável, ou um binário no sistema de arquivos. Esses *builtins* implementam funcionalidades impossíveis ou inconvenientes para se obter via utilitários separados.

Esses comandos foram herdados do *sh*, são implementados como uma especificação do padrão POSIX(Uma família de padrões de sistemas abertos baseados no Unix)
**pwd**, **cd**, **exit**, **times**, **exec**, **export**, **alias**, **echo**, **source**, etc

### Um pouco de história

Por volta de 1964 e 1965, três organizações (**GE**, **AT&T** e **MIT**) se juntam com desejo de desenvolver um sistema operacional multi tarefa e multi usuários e outras inovações computacionais, para rodar em imensos computadores e serem acessados por milhares de pessoas através de terminais burros espalhados pelo planeta.

Em 1969 a divisão da **AT&T** chamada, **Bell labs**, abandonam o projeto alegando que os recursos computacionais à época revelaram-se insuficientes, e projetos experimentais haviam sido excluídos do projeto Multics.

Em 1969, *Ken Thompson* e *Dennis Ritchie* reescrevem o Multics com um conceito menos ambicioso e batizado com Unics, que foi rebatizado de UNIX.

Em 1971, *Ken Thompson*, escreve a primeira shell, chamada shell v6, aliás era um dos conceitos herdado do Multics, onde o sistema operacional era dividido em responsabilidades, ou melhor, em camadas, onde o kernel ficava responsável por interagir com a camada mais baixa da arquitetura de um computador, e o shell fazia a interação com o kernel, ou seja, rodava fora dele.

Nesta primeira versão já foi introduzido uma sintaxe compacta para realizar redirecionamento (< > e \>\>) e canalização (\| ou ^) de comandos, ou seja, o reaproveitamento da saída de um comando, para a entrada de outro que sobrevive ainda nas shells modernas.

{% highlight bash %}
$ ls | grep bin
{% endhighlight %}

Também existia suporte para chamar comandos executados de forma sequencial (com ;) e assíncronos (com &).

{% highlight bash %}
$ rm -rf my_dir && mkdir my_new_dir
{% endhighlight %}

O que faltava nesta primeira versão era a capacidade de ler script. O único proposito nesta primeira versão era modo imperativo, ou seja, ler um comando executar e exibir uma saída.

Em 1975, *Stephen Bourne* do **AT&T Bell Labs**, desenvolve o *bourne shell*. O *sh* (bourne shell) tinha objetivos primários: servir como um interpretador de comandos para executar de forma interativa e não-iterativo, rodando scripts reutilizáveis. O *sh* substitui a shell Thompson na versão UNIX v7.
Bourne introduziu fluxos de controle, loops e variáveis nos scripts. O *sh* permitia o uso de scripts como filtros, mas ainda não tinha capacidade de criar funções.


### *Shell* não é um terminal

Um shell e um terminal são distintos apesar de terem uma relação muito próxima.

Um emulador de terminal, também mais conhecido como terminal, é um programa que interage com o shell em um ambiente de interface gráfica(GUI). No KDE usa o Konsole, e no GNOME o gnome-terminal. Existe uma variedade de emuladores de terminais, como Tilix, Terminator, Guake, xterm e tantos outros, mas todos eles basicamente fazem a mesma coisa: conceder acesso ao shell.

### Conclusão

Sistemas operacionais modermos oferecem um shell para comunicar com kernel, e um terminal para lidar com o shell. Essa banda de três componentes trás acessibilidade e produtividade no dia-a-dia.

##### Fonts:

The Linux Command Line, 2nd Edition: A Complete Introduction 2nd Edition, Shotts, William

[What is a shell, GNU manual](https://www.gnu.org/savannah-checkouts/gnu/bash/manual/bash.html#What-is-a-shell_003f){:target="_blank"}

[Unix](https://en.wikipedia.org/wiki/Unix){:target="_blank"}
