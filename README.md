SISTEMA DE MONITORAMENTO DE LUMINOSIDADE DA VINHERIA AGNELLO



DESCRIÇÃO DO PROJETO:

A Vinheria Agnello nos contratou para criar um sistema de monitoramento à base do ATmega328P, capaz de acompanhar as condições de luminosidade do estoque, pois a qualidade do vinho é diretamente afetada pela luminosidade do ambiente.

O sistema sinaliza o estado do ambiente (Normal 🟢 / Alerta 🟡 / Anormal 🔴) através de LEDs, um display LCD e um buzzer sonoro.



DEPENDÊNCIAS:

Software: Arduino IDE — necessária para compilar e gravar o código no ATmega328P.

Bibliotecas: LiquidCrystal.h — usada para controlar o display LCD 16x2 que mostra o status da luminosidade. Já vem por padrão na Arduino IDE.




COMO FUNCIONA:

O LDR é um sensor sensível à luz: quanto mais claro está o ambiente, mais fácil a corrente elétrica passa por ele; quanto mais escuro, mais difícil. Essa variação é transformada em um sinal elétrico que o ATmega328P consegue ler pela entrada A0.

Só que esse sinal é analógico (varia de forma contínua), e o microcontrolador só entende números. É aí que entra o ADC: ele "traduz" o sinal do sensor em um número de 0 a 1023. Depois, esse número é convertido, com a função map(), para uma porcentagem de 0% a 100%, que é bem mais fácil de interpretar.

A partir dessa porcentagem, o sistema decide o que mostrar e como reagir:

Luminosidade normal (< 90%): acende o LED verde e o LCD mostra "Luminosidade Normal".
Nível de alerta (90% a 92%): acende o LED amarelo, o LCD mostra "Alerta na Luminosidade" e o buzzer apita por 3 segundos.
Nível anormal (>= 93%): acende o LED vermelho, o LCD mostra "Luminosidade Anormal" e o buzzer fica tocando como uma sirene enquanto o problema continuar.



COMO USAR: 

Monte o circuito (LDR, LEDs verde/amarelo/vermelho, buzzer e display LCD) conforme os pinos definidos no código.
Abra o arquivo na Arduino IDE. Selecione a placa (Arduino Uno/Nano) e a porta serial correspondente. 
Faça o upload do código para a placa. 
Acompanhe a leitura de luminosidade pelo Monitor Serial ou pelo próprio display LCD.
