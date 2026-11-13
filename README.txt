=====================================================================
  LABORATÓRIO SECRETO — EXPERIMENTO 047
  Projeto de Linguagem e Técnicas de Programação
  Jogo de exploração feito SOMENTE com HTML e CSS (sem JavaScript)
=====================================================================

COMO ABRIR
----------
1. Descompacte o .zip numa pasta.
2. Abra o arquivo index.html no navegador (Chrome, Edge, Firefox ou Safari
   atualizados). Ou abra a pasta no VS Code e use o "Go Live".


O TEMA
------
Você acorda dentro de uma cápsula num laboratório subterrâneo, sem memória.
Para fugir, precisa encontrar 3 itens espalhados por 3 salas e usá-los na
porta de saída: o CARTÃO de acesso, a SENHA e uma BATERIA.
Durante a exploração, documentos secretos revelam que o "Experimento 047"
é... você.


AS PÁGINAS DO JOGO
------------------
  index.html          1. Início: título, introdução e botão "Iniciar missão"
  instrucoes.html        Regras, objetivo, passo a passo e legenda
  sala-controle.html  2. Sala de Controle  -> encontrar o CARTÃO
  laboratorio.html    3. Laboratório       -> descobrir a SENHA (enigma)
                                              e ler documentos secretos
  sala-energia.html   4. Sala de Energia   -> encontrar a BATERIA
  fuga.html           5. Fuga              -> usar os itens na porta
  vitoria.html        6. Final: vitória
  game-over.html      6. Final: derrota (uma página para os 9 tipos de derrota)


FLUXO DO JOGO
-------------
  Início -> Controle -> Laboratório -> Energia -> Fuga -> Vitória
               |            |            |         |
               v            v            v         v
            Game Over   Game Over    Game Over  Game Over
            #lockdown   #capsula     #choque    #ordem
            #terminal   #tubos       #cabos     #forca / #senha
               |
               v
            Recomeça do INÍCIO do jogo (index.html)

  - Cada sala tem uma porta TRANCADA que só abre quando o item é pego.
  - Cada fase tem pelo menos 2 escolhas erradas (armadilhas).
  - Todas as opções têm a MESMA cor: o jogador só descobre se a
    escolha era boa ou ruim depois de clicar.
  - Errou? Game over e o jogo recomeça do começo.
  - O rodapé de todas as páginas tem: Início, Como jogar e Reiniciar.


ORGANIZAÇÃO DOS ARQUIVOS
------------------------
  css/base.css         Variáveis de cor, fontes, fundo e layout (CSS Grid)
  css/componentes.css  Peças reutilizáveis: botões, painéis, inventário,
                       janelas de documento, teclado...
  css/jogo.css         A "lógica" do jogo feita com seletores CSS
  css/efeitos.css      Todas as animações (@keyframes)
  imagens/             Ilustrações em SVG feitas para o jogo


COMO O JOGO FUNCIONA SEM JAVASCRIPT
-----------------------------------
1. INVESTIGAR: cada objeto é um <label> ligado a um <input type="radio">
   escondido. Quando o radio é marcado, o CSS mostra o resultado que vem
   logo depois dele (seletor  .investigar:checked + .resultado).

2. PEGAR ITENS: o botão "Pegar" é um <label> de um checkbox escondido.
   O seletor :has() verifica se o checkbox está marcado e então
   atualiza a tabela de inventário e destranca a porta.

3. DOCUMENTOS e DERROTAS: usam o seletor :target. Um link para
   "#doc-prancheta" abre a janela do documento; um link para
   "game-over.html#choque" mostra a mensagem certa da derrota.

4. MEMÓRIA ENTRE PÁGINAS: só dá para sair de uma sala com o item.
   Por isso, cada página já "sabe" quais itens o jogador tem.


REQUISITOS DO PROFESSOR -> ONDE ESTÃO
-------------------------------------
  Página inicial ............. index.html
  Página de instruções ....... instrucoes.html
  3+ páginas de exploração ... sala-controle, laboratorio, sala-energia, fuga
  Página de conclusão ........ vitoria.html e game-over.html
  Layout responsivo .......... CSS Grid + media queries (base.css, seção 7)
  Navegação .................. botões de saída + rodapé em todas as páginas
  Imagens e ícones ........... pasta imagens/ (SVG) + emojis
  Tabela de inventário ....... em todas as salas (<table>)
  Listas ..................... opções (<ul>), passo a passo (<ol>), dicas
  Estilização avançada ....... variáveis CSS, degradês, sombras, neon,
                               position absolute/sticky, color-mix()
  Animações e transições ..... efeitos.css (entrada da página, item indo
                               para a mochila, glitch, digitação, sirene...)


SOLUÇÃO (não conte para ninguém!)
---------------------------------
  Controle: revistar a jaqueta e pegar o cartão.
            (armadilhas: botão vermelho, hackear o terminal)
  Laboratório: ler a prancheta (regra) e o computador (número 047).
            (armadilhas: abrir a cápsula, coletar o líquido dos tubos)
  Energia: pegar a bateria do DRONE.
            (armadilhas: bateria do gerador, puxar os cabos)
  Fuga: bateria -> cartão -> senha 740.
            (armadilhas: passar o cartão antes da bateria, arrombar,
             senhas erradas)
