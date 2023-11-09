Aggiungere nuove funzionalità o caratteristiche dinamicamente
Antipattern:
- gerarchia di classi, cioe creo una classe per ogni possibile combinazione di decorazioni
- unica classe (God class)

il decorator pattern attacca nuove responsabilità tramite l aggiunta di nuovi oggetti

creo una classe astratta Decorator che implementa la classe a cui ci vogliamo aggiungere cose in modo tale che overridiamo tutti i metodi cosicche le decorazioni che utilizzamo non dovrenno riscrivere i metodi che non cambiano
potrei aggiungere un metodo protected che rappresenta la azione specifica del decorator che verra ridefinito

...