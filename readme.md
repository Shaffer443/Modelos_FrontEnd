# Código JavaScript com os efeitos:


### Movimentação:

- https://micku7zu.github.io/vanilla-tilt.js/

**sintaxe**

 <script type="text/javascript" src="vanilla-tilt.js"></script>
    <script type="text/javascript">
        VanillaTilt.init(document.querySelector(".your-element"), {
            max: 25,
            speed: 400
        });
        
        //It also supports NodeList
        VanillaTilt.init(document.querySelectorAll(".your-element"));
    </script>

**Espelhamento**

Opções para configuração


{
    reverse:                false,  // reverse the tilt direction
    max:                    35,     // max tilt rotation (degrees)
    startX:                 0,      // the starting tilt on the X axis, in degrees.
    startY:                 0,      // the starting tilt on the Y axis, in degrees.
    perspective:            1000,   // Transform perspective, the lower the more extreme the tilt gets.
    scale:                  1,      // 2 = 200%, 1.5 = 150%, etc..
    speed:                  300,    // Speed of the enter/exit transition
    transition:             true,   // Set a transition on enter/exit.
    axis:                   null,   // What axis should be enabled. Can be "x" or "y"
    reset:                  true,   // If the tilt effect has to be reset on exit.
    "reset-to-start":       true,   // Whether the exit reset will go to [0,0] (default) or [startX, startY]
    easing:                 "cubic-bezier(.03,.98,.52,.99)",    // Easing on enter/exit.
    glare:                  false,  // if it should have a "glare" effect
    "max-glare":            1,      // the maximum "glare" opacity (1 = 100%, 0.5 = 50%)
    "glare-prerender":      false,  // false = VanillaTilt creates the glare elements for you, otherwise
                                    // you need to add .js-tilt-glare>.js-tilt-glare-inner by yourself
    "mouse-event-element":  null,   // css-selector or link to HTML-element what will be listen mouse events
    gyroscope:              true,   // Boolean to enable/disable device orientation detection,
    gyroscopeMinAngleX:     -45,    // This is the bottom limit of the device angle on X axis, meaning that a device rotated at this angle would tilt the element as if the mouse was on the left border of the element;
    gyroscopeMaxAngleX:     45,     // This is the top limit of the device angle on X axis, meaning that a device rotated at this angle would tilt the element as if the mouse was on the right border of the element;
    gyroscopeMinAngleY:     -45,    // This is the bottom limit of the device angle on Y axis, meaning that a device rotated at this angle would tilt the element as if the mouse was on the top border of the element;
    gyroscopeMaxAngleY:     45,     // This is the top limit of the device angle on Y axis, meaning that a device rotated at this angle would tilt the element as if the mouse was on the bottom border of the element;
}




# Informação:

Onde o código JavaScript deve ser colocado em um documento HTML: no elemento <head> ou <body>? No início ou no final de cada um? Existe alguma diferença de performance ou qualquer outra relacionada a isso?



Depende do que o script faz, e do quanto ele faz falta. Todo JavaScript inserido numa página (seja onde for) executa de modo síncrono por padrão*. Isso significa que quando a tag <script> é encontrada o browser não renderiza mais nada enquanto esse script não for carregado e executado.

Colocar um <script> no head garante que ele seja executado antes de qualquer elemento ser colocado no body. Isso significa que ele garantidamente estará presente quando a página for "montada", ou seja, qualquer código que precise estar presente na hora de processar o body com certeza já estará pronto para agir. A desvantagem é que o usuário só vai ver uma página em branco até que o script termine de executar.

Colocar um <script> no final do body, por outro lado, permite que o conteúdo antes dele já apareça para o usuário sem ter de esperar sua execução. Isso passa a impressão de um site mais rápido, o usuário não precisa esperar cada mínimo detalhe estar pronto antes de ler o conteúdo da página. A desvantagem é que - se o seu script modifica significativamente o conteúdo e/ou sua apresentação e funcionalidade - o usuário verá uma página "estranha" e "mal formatada" antes que o script a "corrija". Da mesma forma, se um script muda o comportamento de um link ou botão, por exemplo, clicar nos mesmos antes do script executar causará um comportamento incorreto.

Cabe então a você determinar, caso a caso, onde é o melhor lugar para se colocar o script. Se fizer pouca diferença, a recomendação mais comum é o final do body, pela questão da performance principalmente. Se somente estiver interessado em browsers modernos, entretanto, colocá-lo no head com o atributo defer pode ser ainda melhor.

* Nota: também é possível tornar o script assíncrono, caso isso seja possível (i.e. não existam dependências complexas entre os diferentes scripts e/ou entre o script e os elementos da página), através dos atributos async e defer do HTML5. Mais detalhes nessa resposta. Ambos fazem a carga paralelamente à renderização, a diferença é que o async para a renderização (em um ponto arbitrário) no momento em que a carga for concluída para executá-lo, enquanto o defer somente o executa ao final da renderização, mesmo que a carga seja concluída antes. Tal como no caso síncrono, o uso mais indicado depende do seu propósito.
