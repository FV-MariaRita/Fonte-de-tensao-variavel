# Fonte de tensão variável
Projeto construído como o Trabalho 1 da disciplina de Eletrônica para Computação do curso de Ciência da Computação do 1° semestre no ICMC-USP.

## Descrição do projeto
O projeto consiste na construção de uma fonte de tensão capaz de retificar a corrente alternada de tensão eficaz 127V (aproximada 179,6V de pico) da tomada em uma corrente contínua, com tensão ajustável, por meio de um potenciômetro, entre 3V e 12V. 

A partir da tomada, teremos uma tensão eficaz de 127V, com corrente alternada e frequência de 60Hz. 

## Alunos
* Julia Barbosa Nogueira - 17901347 - [Github Julia Nogueira](https://github.com/juliab2nogueira)
* Carolina Goulart Kowalczuk - 13854629 - [Github Carolina Kowalczuk](https://github.com/kowalczukcarolina)
* Maria Rita Fagundes Vargas - 17912857 -  [Github Maria Rita Vargas](https://github.com/FV-MariaRita)
* Victor Hugo Adão de Oliveira - 17969072 - [Github Victor Adão](https://github.com/VihAdao)



## Componentes utilizados 
| Componentes        | Quantidade           | Valores  |
| ------------- |:-------------:| -----|
| Capacitor ELCO 470µF x 35V 105 C 10X16     | 2 | R$2,80 |
| Capacitor ELCO 330µF x 25V 105 C 10X12.5 | 1 | R$3,30 |
| Diodo Retificador 1N4007 LGE = 1N4004      | 10      | R$0,20 |
| Diodo Zenner 1N4743 13V 1W | 2      |    R$0,50 |
| LED 5MM Azul Difuso EVERLIGHT | 3 | R$0,50 |
| Potenciômetro 1W B10K B-16,5 x E-20-XR-7MM| 2   | R$7,00 |
| Transistor 2N2222A NPN 60V 0,8A TO-92 | 2  |  R$2,60 |
| Resistor CR25 120R Carvão | 10   | R$0,07 |
| Resistor CR25 100R Carvão ROHS | 10  | R$0,07 |
| Resistor CR25 5K1 Carvão TL | 10 | R$0,07 |
| Resistor CR25 3K3 Carvão | 10 | R$0,07 |
| Resistor CR25 4K7 Carvão ROHA | 10 | R$0,07 |
| Jumper Macho x Macho (Kit com 10 peças) | 2 | R$7,00 |
| **Total** | | **R$50,10** |
  
## Descrição dos componentes utilizados

**Transformador (AC = 18,1 Vrms / Capacitor = 24,2V):** Reduz a tensão da tomada (127V) para alimentar o circuito em uma tensão menor, proporcional ao seu número de espiras em cada um dos lados.

**Ponte de Diodos:** Retifica (converte) a corrente alternada (AC) para corrente contínua (DC). Ela é formada por 4 diodos, cada um com 0,7V de tensão.

**Capacitor:** Armazena a energia elétrica temporariamente para liberá-la quando necessária, fazendo com que a tensão retificada seja filtrada para reduzir o ripple.

**Diodo Zener:** Estabiliza e regula a tensão do circuito, travando a tensão de referência em 13V.

**Resistor de Polarização:** Limita a corrente que passa pelo diodo zener para que ele não queime.

**Potenciômetro Linear:** Permite o ajuste manual da tensão de saída entre os valores de 3V e 12V exigidos pelo projeto.

**Transistor de Passagem:** Transistor de passagem funciona como um "copiador" de tensão. A tensão na saída (no emissor) será sempre a tensão do braço do potenciômetro menos a queda de tensão base-emissor do transistor(=0,7V). Ele funciona com 3 pinos, sendo eles: Coletor C, Base B e Emissor E.

Imagem do manual do Transistor de passagem 2N2222: 

<img width="400" height="200" alt="image" src="https://github.com/user-attachments/assets/15de184b-7182-4960-82c7-a5a10c2eba9a" />


**LED Azul:** Utilizado como indicador visual de que a fonte está ligada e em funcionamento.

**Resistores de Apoio:** 
1. Resistor de 3.3kΩ (em série com o LED): Limita a corrente que passa pelo LED indicador para não queimá-lo.
2. Resistor de 820Ω: Posicionado logo antes do diodo zener para polarizar o zener de forma segura.
3. Resistor de 5.1kΩ: Limita o mínimo de tensão a 3V, para que mesmo ao girar o potenciômetro para o mínimo a tensão não zere.
4. Resistores de 100Ω e 120Ω: Estabilizam as correntes de base e emissor do transistor. 

## Cálculos


* **Tensão de Pico da Tomada:** A tensão $V_{rms}$ da rede elétrica é calculada em seu valor máximo de pico pela equação:
$$V_{\text{pico tomada}} = V_{rms} \times \sqrt{2} = 127 \times \sqrt{2} \approx 179,6\text{ V}$$


* **Tensão de pico no Transformador:** Após passar pelo transformador, a tensão sofre uma modificação e é preciso calcular a tensão de pico na saída do transformador. Para isso, utiliza-se a tensão AC do transformador, pois ela representa o valor da tensão RMS de saída do transformador. O transformador escolhido reduz a tensão para $18,1\text{ Vrms}$ no secundário, resultando na seguinte tensão de pico de saída:
$$V_{\text{pico transformador}} = V_{rms} \times \sqrt{2} = 18,1 \times \sqrt{2} \approx 25,59\text{ V}$$


* **Queda de tensão na Ponte de Diodos:** A corrente contínua atravessa dois diodos simultaneamente na retificação da Ponte de Diodos. Considerando uma queda típica de $0,7\text{ V}$ por diodo, a tensão máxima retificada é:

  $$V_{\text{pico diodos}} = V_{\text{pico transformador}} - (0,7 \times 2)$$

  $$V_{\text{pico diodos}} = 25,59 - 1,4 = 24,19\text{ V} \approx 24,2\text{ V}$$

* **Relação de Espiras do Transformador:** A relação de espiras é dada pela razão da quantidade de espiras no primário (entrada) e no secundário (saída). Essa razão é proporcional à razão entre a tensão primária e a tensão secundária. Por isso:

  $$\text{Relação de espiras} = \frac{V_{rms\text{ tomada}}}{V_{rms\text{ transformador}}} = \frac{127}{18,1} \approx 7,016$$

* **Cálculo do Ripple:** O Ripple é o componente de corrente alternada que se sobrepõe ao valor médio da tensão de uma fonte de corrente contínua. A origem da ondulação normalmente está associada à utilização de carregadores baseados em retificadores. Normalmente é um valor residual e periódico obtido de uma fonte de tensão que é alimentada por uma corrente alternada. Para o projeto da fonte,
o ripple deve ser de **no máximo 10%** sobre a tensão retificada:

   $Ripple = 10/100 * 24,19 = 2,419V$

    Como a oscilação máxima permitida é de $2,419V$, a tensão no capacitor deve oscilar entre $24,2\text{ V}$ (máximo) e $21,78\text{ V}$ (mínimo).

* **Cálculo da Capacitância:** A capacitância mínima representa a menor capacidade de armazenamento de energia que o capacitor deve ter para conseguir "sustentar" a tensão da fonte firme, sem deixar que ela caia além do permitido enquanto a carga puxa a corrente máxima.

    $C = \frac{I_{carga}}{f \cdot \Delta v}$

    $I_{carga} = 0,1\text{ A}$ (capacidade da fonte)

    $f = 120\text{Hz}$ (frequência de rede retificada em onda completa)

    $\Delta v = 2,42\text{V}$ (Ripple máx)

    $C = \frac{I_{carga}}{f \cdot \Delta v} = \frac{0,1}{120 \cdot 2,419} = \frac{0,1}{290,28} = 3,444949 \cdot 10^{-4} = 344\mu\text{F}$

    Valor comercial superior mais próximo a 344µF : 470µF

* **Resistor de Polarização do Zener ($R_z$):** O Zener precisa de um resistor em série para limitar a corrente que passa por ele, vinda dos 24,2V do capacitor. A tensão sobre esse resistor será:


## Circuito no Falstad

## Esquemático no EasyEDA 

## PCB no EasyEDA

## Fotos da Protoboard

## Explicação em vídeo do projeto 
