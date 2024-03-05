<style>
  section {
    background-color: #dbdccf;
    background-size: cover;
  }

  .transparent {
    background-color: transparent!important;
  }

  section.transparent img {
    background-color: transparent!important;
  }

  .transparent-table-tr-td-th {
    background-color: rgba(0, 0, 0, 0.0) !important;
  }

  .cabecalho {
    position: absolute;
    top: 10%;
    margin-left: 5%;
    margin-right: 10%;
    font-size: 48px;
    font-weight: bold;
  }

  .conteudo {
    top: 30%;
    margin-top: 7.5vh;
    margin-left: 5%;
    margin-right: 5%;
    font-size: 28px;
    text-align: justify;
  }

  .conteudo-absoluto {
    position: absolute;
    top: 30%;
    margin-left: 5%;
    margin-right: 5%;
    font-size: 28px;
    text-align: justify;
  }
  .huge {
    font-size: 32px;
  }
  .large {
    font-size: 24px;
  }
  .normal {
    font-size: 22px;
  }
  .regular {
    font-size: 18px;
  }
  .small {
    font-size: 16px;
  }
  .footnotesize {
    font-size: 14px;
  }
  .scriptsize {
    font-size: 12px;
  }
  .tiny {
    font-size: 10px;
  }
  .bold {
    font-weight: bold;
  }
  section.centered table {
    margin-left: auto;
    margin-right: auto;
  }
  section.lead p {
    text-align: justify;
    font-size: 18px;
  }
  section.lead h1, h2, h3, h4 {
    text-align: center;
  }
  
  .grid-50-50 {
    display: grid;
    grid-template-columns: 1fr 1fr;
    text-align: justify;
  }

  .grid-66-33 {
    display: grid;
    grid-template-columns: 2fr 1fr;
    text-align: justify;
  }

  .grid-75-25 {
    display: grid;
    grid-template-columns: 3fr 1fr;
    text-align: justify;
  }

  .grid-80-20 {
    display: grid;
    grid-template-columns: 4fr 1fr;
    text-align: justify;
  }

  .grid-33-66 {
    display: grid;
    grid-template-columns: 1fr 2fr;
    text-align: justify;
  }

  .grid-element {
    margin-left: 5%;
    margin-right: 5%;
    padding-left: 2.5%;
    padding-right: 2.5%;
  }
  img[alt=grid-img] {
    display: block;
    width: 100%;
  }

  img[alt=grid-img-35] {
    display: block;
    margin: auto;
    width: 35%;
  }

  img[alt=grid-img-50] {
    display: block;
    margin: auto;
    width: 50%;
  }

  img[alt=grid-img-75] {
    display: block;
    margin: auto;
    width: 75%;
  }


  img[alt=centered-img] {
    display: block;
    margin: auto;
  }

  img[alt=arquitetura-microprocessador] {
    display: block;
    margin: auto;
    width: 45%;
  }

  .mid-aligned-container {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 100%;
  }

  .flex-container {
    display: flex;
  }

  .column-container {
    flex: 1;
    padding: 5px;
  }

  .column-row-container {
    display: flex;
    flex-direction: column;
  }

  .quarter-row {
    flex: 1;
  }

  .three-quarter-row {
    flex: 3;
  }

</style>

<script src="https://polyfill.io/v3/polyfill.min.js?features=es6"></script>
<script id="MathJax-script" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML"></script>


# Microcontroladores e Microprocessadores

## Aula 02

### Introdução ao Arduino
### Entradas e Saídas Digitais

Prof. M.Sc. [Diego Ascânio Santos](mailto:ascanio@cefetmg.br)

Aula baseada nas apostilas do Prof. Dr. [Ricardo Kerschbaumer — IFC, Campus Luzerna](https://lattes.cnpq.br/5304374284779760)

CEFET-MG DECOMDV — Divinópolis, 2024


---

## Objetivos

- Mostrar como funciona o Arduino e seus componentes principais;
- Apresentar o ATMEGA328P;
- Apresentar o ambiente de desenvolvimento do Arduino;
- Apresentar entradas e saídas digitais do Arduino;
- Apresentar os circuitos de conexão de componentes externos ao Arduino;


---

## Roteiro

<div class="regular" markdown="1">

1. Introdução ao Arduino;
    1. ATMega328P;
    2. Alimentação do Arduino;
    3. Entradas e saídas do Arduino;
    4. Ambiente de desenvolvimento do Arduino;
2. Entradas e saídas digitais;
    1. Entradas digitais no Arduino;
    2. Saídas digitais no Arduino;
        1. Conexão de relés;
        2. Conexão de um motor utilizando transistor;
        3. Conexão de lâmpada de sinalização;
        4. Conexão de pequenos motores;
        5. Conexão de motores de passo;
        6. Conexão de motores CC com reversão;
        7. Conexão de displays de LED;
        8. Circuitos especializados de saída;
3. Shields.

</div>


---

<!-- _class: lead -->
# Introdução ao Arduino


---

## Introdução ao Arduino

<div class="regular">

- Arduino é uma placa de prototipagem eletrônica de código aberto — *hardware* livre — que permite a criação de projetos interativos e autônomos.
    - Inicialmente baseado em microcontroladores AVR da Atmel, o arduino pode ser programado em C/C++.
    - Por ser *hardware* livre ele permite a construção de projetos **faça você mesmo** (DIY) de baixo custo, flexíveis e fáceis de se usar.
    - A quantidade de placas que compõem a família Arduino é muito extensa. Por isso, a disciplina se concentrará nas placas Arduino construídas em torno do microcontrolador ATMEGA328P / ATMEGA168P (Arduino Uno, Nano, Pro Mini, etc). Um Arduino UNO, principal expoente dos arduinos construídos em torno do ATMEGA328P, é mostrado na figura 1.

<figure>

<!-- _class: transparent -->
![centered-img](./img/arduino-uno.png)

<figcaption>Figura 1 — Arduino UNO</figcaption>
</figure>

</div>


---

## Introdução ao Arduino
<div class="regular">

- O arduino é composto por um microcontrolador, entradas e saídas (digitais e analógicas) uma entrada de alimentação, uma interface serial ou USB para comunicação (e programação) com o computador, botão de Reset, LEDs de indicação, saídas de alimentação de periféricos em nível lógico TTL (+5V) e CMOS (+3.3V) e referências comuns (GND) como mostrado na Figura 2.

<figure>

<!-- _class: transparent -->
![centered-img](./img/componentes-arduino.png)

<figcaption style="text-align: center;">Figura 2 — Componentes de um Arduino</figcaption>
</figure>
</div>


---

## Introdução ao Arduino
<div class="regular">

- A programação do arduino é feita a partir de um computador conectado ao arduino pela porta USB, como mostrado na Figura 3.

- Um aspecto muito importante das placas Arduino é a capacidade de serem expandidas através de *shields* (escudos, tradução literal) que são placas que se encaixam na placa principal e adicionam funcionalidades como GPS, Bluetooth, Ethernet, entre outros. A Figura 4 mostra um Arduino com um shield Ethernet que possibilita sua conexão à internet.

</div>
<div class="grid-50-50 small">
<div class="grid-element">
<figure>

<!-- _class: transparent -->
![centered-img](./img/programacao-arduino-computador.png)

<figcaption style="text-align: center;">Figura 3 — Conexão do arduino a um computador</figcaption>
</figure>
</div>
<div class="grid-element">
<figure>

<!-- _class: transparent -->
![centered-img](./img/shield.png)

<figcaption style="text-align: center;">

Figura 4 — Arduino extendido com um *shield* Ethernet

</figcaption>
</figure>
</div>
</div>


---

## Introdução ao Arduino — Microcontrolador ATmega328P

<div class="regular">

- De todos os componentes do Arduino, o mais importante é o microcontrolador.
    - Ele é o cérebro do Arduino e é responsável por todas as operações.
- Como dito anteriormente, existem vários modelos de Arduino, cada qual com um microcontrolador específico.
    - Os adotados neste curso são os microcontroladores ATmega168 e ATmega328P, presente no Arduino UNO.
    - A pinagem do microcontrolador ATmega328P é mostrada pela Figura 5, enquanto as características do microcontrolador são apresentadas a seguir:

<!-- _class: lead -->
### Principais características do ATmega328P

<div class="grid-50-50">
<div class="grid-element small">

- CPU RISC de 8 bits;
- Capacidade de processamento de 20 milhões de instruções por segundo (MIPS) em 20 MHz;
- Memória Flash de programa de 32 KB;
- Memória SRAM de 2 KB;
- Memória EEPROM de 1 KB;
- Programável no circuito;
- 2 temporizadores/contadores de 8 bits;

</div>
<div class="grid-element">

- 1 temporizador/contador de 16 bits;
- 6 entradas analógicas (ADC) de 10 bits;
- Contador de tempo real (RTC);
- 23 pinos de entrada/saída digitais;
- 6 canais PWM;
- Comunicação UART, SPI e I2C;
- Operação em 1,8 V a 5,5 V.

</div>
</div>

</div>


---

## Introdução ao Arduino — Microcontrolador ATmega328P

<figure>

<!-- _class: transparent -->
![centered-img](./img/pinagem-atmega328p.png)

<figcaption class="regular" style="text-align: center;">Figura 5 — Pinagem do microcontrolador ATmega328P</figcaption>
</figure>


---

## Introdução ao Arduino — Alimentação

<div class="grid-50-50 regular">
<div class="grid-element">

- O arduino pode receber alimentação de duas formas: USB ou por uma fonte externa como ilustrado pela Figura 6.
- Quando a alimentação é realizada por fonte externa, a tensão de alimentação deve ser de 7 a 12V.
    - Reguladores de tensão internos do Arduino reduzem a tensão para os níveis lógicos necessários aos componentes (TTL ou CMOS).
    - *Hoaxes* dizem que o Arduino aguenta até 20V, mas, não é bom pagar para ver.
- O consumo total de corrente no Arduino não deve ultrapassar \\(500mA\\).
- A comutação entre alimentação USB e externa é feita automaticamente pelo Arduino.

</div>
<div class="grid-element mid-aligned-container">
<figure>

<!-- _class: transparent -->
![](./img/alimentacao-arduino.png)

<figcaption style="text-align: center;">Figura 6 — Alimentação do Arduino.</figcaption>
</figure>
</div>
</div>


---

## Introdução ao Arduino — Alimentação

<div class="flex-container regular">
<div class="column-container">

- O Arduino também fornece conexões de alimentação para periféricos ou *shields* conectados a ele.
    - A Figura 7 mostra a disposição destes conectores de alimentação no Arduino Uno.
- Nestes conectores, o pino `IOREF` fornece uma tensão de referência para os *shields* e periféricos conectados ao Arduino.
    - Assim, o *shield* ou periférico pode reconhecer se o nível lógico de tensão é CMOS (3.3V) ou TTL (5V).
- O pino `RESET` é conectado ao botão de reset do Arduino e permite que periféricos ou *shields* conectados ao Arduino possam reiniciar o microcontrolador.
- O pino `3.3V` fornece uma tensão de 3.3V para alimentar periféricos ou *shields* que operam em CMOS.
- O pino `5V` fornece uma tensão de 5V para alimentar periféricos ou *shields* que operam em TTL.

</div>
<div class="column-container column-row-container">
<div class="three-quarter-row">

- Os pinos `GND` são conectados ao terra do Arduino e fornecem uma referência de tensão para os periféricos ou *shields* conectados.
- O pino `VIN` permite alimentar o Arduino através de algum circuito externo, sem a nacessiade de utilizar a porta USB ou a fonte de alimentação do Arduino.
    - Este pino também é conectado ao regulador de tensão do Arduino.
    - Os níveis operacionais de tensão permanecem entre 7V e 12V.

</div>
<div class="quarter-row small">
<figure>
<div class="mid-aligned-container">

<!-- _class: transparent -->
![](./img/shield-power-connectors.png)

</div>
<figcaption style="text-align: center;">

Figura 7 - Conectores de alimentação de *shields* e periféricos do Arduino Uno.

</figcaption>
</figure>
</div>
</div>
</div>


---

## Introdução ao Arduino — Entradas e Saídas

<div class="small">

- Como visto nos conteúdos anteriores, o arduino possui entradas e saídas dos tipos digitais e analógicas.
    - Em relação aos tipos digitais são 14 pinos que podem enviar ou receber sinais digitais de nível lógico TTL (0V e 5V), ou seja, 0 ou 1.
        - Alguns destes pinos digitais também podem ser utilizados em outras funções:
            - 6 pinos (pinos 3, 5, 6, 9, 10 e 11) podem ser utilizados como saídas PWM (Pulse Width Modulation), que com devidas adaptações, simula saídas analógicas, como veremos mais adiante.
            - Os pinos 0 e 1 podem ser utilizados para comunicação serial (RX e TX).
            - Os pinos 2 e 3 podem ser utilizados para interrupções externas.
    - Já os pinos analógicos do Arduino (A0 - A5, que correspondem respectivamente aos pinos 14 - 19) só podem ser utilizados como entradas analógicas.
        - As entradas analógicas são implementadas no arduino através de um conversor analógico-digital (ADC) compartilhado entre elas, que converte uma tensão analógica (entre 0 a 5V) em um valor digital de 10 bits (0 a 1023) para cada entrada.
        - Como apenas um único ADC está disponível para todas as entradas analógicas, apenas uma entrada analógica pode ser lida por vez.
- A Figura 8 ilustra as entradas e saídas do Arduino UNO com suas principais funções.

</div>


---

## Introdução ao Arduino — Entradas e Saídas

<figure>

<!-- _class: transparent -->
![centered-img](./img/arduino-inout-shared-functions.png)

<figcaption class="regular" style="text-align: center;">
Figura 8 — Entradas e saídas do Arduino UNO com suas principais funções.
</figcaption>
</figure>


---

## Introdução ao Arduino — Ambiente de Desenvolvimento

<div class="small">

- Para se programar o Arduino são necessárias ferramentas de desenvolvimento apropriadas para tal.
    - Existem diversas formas de se programar o Arduino, tais quais:
        1. Plugins para configuração no VSCode;
        2. Interfaces de linha de comando para compilação e upload de código;
        3. O ambiente de desenvolvimento integrado oficial do Arduino, o Arduino IDE, ilustrado pelas Figuras 10 e 11.

<div class="flex-container footnotesize">
<div class="column-container">
<figure style="padding: 10px;">

![](./img/arduino-ide-loading.png)

<figcaption style="text-align: center;">Figura 10 — Tela de Carregamento do Arduino IDE</figcaption>
</figure>
</div>
<div class="column-container">
<figure style="padding: 10px;">

![](./img/arduino-ide-loaded.png)

<figcaption style="text-align: center;">Figura 11 — Arduino IDE carregado em sua tela inicial</figcaption>
</figure>
</div>
</div>
</div>


---

## Introdução ao Arduino — Ambiente de Desenvolvimento

<div class="normal">

- É recomendado na disciplina utilizar a IDE oficial do Arduino para a programação dos microcontroladores — Apenas UPLOAD dos códigos. Esta IDE está disponível no container de aulas do professor da disciplina. 
    - Utilizar este container permite garantir que todos os alunos estão utilizando a mesma versão do ambiente de desenvolvimento, evitando problemas de compatibilidade entre diferentes versões do software e portanto, garantindo a reprodutibilidade dos experimentos.
        - As instruções apropriadas para execução deste container estão disponíveis em seu [repositório](https://github.com/diegoascanio/container-aulas-cefetmg).
    - Caso o aluno deseje apenas instalar a IDE do Arduino em seu computador, acesse o [site oficial](https://www.arduino.cc/en/software) e siga as instruções de instalação para o seu sistema operacional.
    - Também é facultado ao aluno utilizar outras ferramentas de sua preferência, entretanto, não é garantido nenhum suporte para problemas de compatibilidade que possam surgir.

</div>


---

## Introdução ao Arduino — Ambiente de Desenvolvimento

<div class="regular flex-container">
<div class="column-container">

- A IDE oficial do Arduino dispõe de um editor de texto, um compilador, um gravador de firmware, monitor serial, gerenciador de bibliotecas, ferramentas de depuração, exemplos de código e muitos outros recursos.
- O upload do firmware para a placa é feito através de um cabo USB, que também é usado para alimentar a placa. Além disso, pelo mesmo cabo é possível monitorar o funcionamento da placa através de comunicação serial, bem como, construir gráficos de dados numéricos enviados pela placa em tempo real.
- A Figura 12 mostra um código de exemplo carregado no Arduino IDE que faz a placa enviar sequencialmente e em loop, todos os caracteres da tabela ASCII pela comunicação serial.

</div>
<div class="column-container">
<figure>

<!-- _class: transparent -->
![grid-img-75](./img/arduino-ide-ascii.png)

<figcaption style="text-align: center;">Figura 12 - Arduino IDE com o programa ASCIITable</figcaption>
</figure>
</div>
</div>


---

## Introdução ao Arduino — Uso da IDE
### Pré requisitos

<div class="small">

1. No linux, além de ter a IDE do Arduino instalada, é necessário adicionar o usuário ao grupo `dialout` e / ou `tty` (a depender da distro) para que o usuário tenha permissão de acesso à porta serial. Para isso, execute o comando `sudo usermod -a -G [GRUPO] $USER` e faça logout e login novamente, onde `[GRUPO]` é o nome do respectivo grupo (`tty` ou `dialout`) que permite o acesso à porta serial na sua distro.

2. Feito isso, conecte o Arduino UNO à porta USB do computador e verifique se o sistema reconheceu a placa. Para isso, execute o comando `dmesg | grep tty` e verifique se a placa foi reconhecida. Se sim, a saída do comando será algo como `/dev/ttyACM0` ou `/dev/ttyUSB0`.

3. Se utilizar o container da disciplina — o que torna dispensável a instalação do Arduino IDE em seu Host — adicione também seu usuário ao grupo `docker` para que o usuário tenha permissão de acesso à porta serial. Para isso, execute o comando `sudo usermod -a -G docker $USER` e faça logout e login novamente.

4. Inicie o container da disciplina com o comando `docker run -it --rm -p 6080:6080 -v ~/container-aulas-cefetmg:/container-aulas-cefetmg --ulimit nofile=65536:65536 --device /dev/ttyUSB0:/dev/ttyUSB0 diegoascanio/cefetmg:container-aulas`. Se a placa estiver identificada como `/dev/ttyACM0`, substitua as ocorrências de `/dev/ttyUSB0` por `/dev/ttyACM0` no comando.

</div>


---

## Introdução ao Arduino — Uso da IDE
### Pré requisitos

<div class="normal">

<div class="grid-75-25">
<div class="grid-element">

5. Iniciado o container da disciplina, abra o endereço [http://localhost:6080](http://localhost:6080) no navegador de sua preferência para acessar a interface gráfica do container e clique em `Connect` como mostra a Figura 13.
6. Em seguida, clique com o botão direito do mouse em qualquer parte da tela preta para abrir o menu de aplicativos do container. Em seguida, navegue até `Development` e clique em `Arduino IDE` para abrir a IDE do Arduino, como mostra a Figura 14.

</div>
<div class="grid-element">
<figure>

![](./img/novnc.png)

<figcaption class="footnotesize" style="text-align: center;">Figura 13 — Tela Inicial do Container</figcaption>
</figure>
<figure>

<!-- _class: transparent -->
![](./img/openbox.png)

<figcaption class="footnotesize" style="text-align: center;">Figura 14 — Acesso ao Arduino IDE</figcaption>
</figure>

</div>
</div>
</div>


---

## Introdução ao Arduino — Uso da IDE
### Pré requisitos

<div class="grid-50-50">
<div class="grid-element normal">

7. Se você estiver usando o Arduino UNO, pode passar diretamente ao passo 8. Se for o Arduino nano ATmega168 (Arduino nano vermelho) siga os passos a seguir:
    1. No Arduino IDE clique em `Tools`, depois em `Board` e selecione `Arduino Nano`, como mostra a Figura 15.
    2. Em seguida, clique novamente em `Tools`, depois em `Processor` e selecione `ATmega168`, como mostra a Figura 16.

</div>
<div class="grid-element footnotesize">
<figure>

<!-- _class: transparent -->
![](./img/select-nano-168.png)

<figcaption style="text-align: center;">Figura 15 - Seleção do Arduino Nano</figcaption>
</figure>
<figure>

<!-- _class: transparent -->
![](./img/nano-168-processor.png)

<figcaption style="text-align: center;">Figura 16 - Seleção do Processador ATmega168</figcaption>
</figure>
</div>
</div>


---

## Introdução ao Arduino — Uso da IDE
### Pré requisitos

<div class="grid-50-50">
<div class="grid-element normal">

8. Agora é necessário selecionar a porta USB que o Arduino está conectado. Para isso, vá em `Tools -> Port` e clique na porta onde o Arduino está conectado— `/dev/ttyUSB0` ou `/dev/ttyACM0` no Linux — como mostra a Figura 17.

</div>
<div class="grid-element footnotesize">
<figure>

<!-- _class: transparent -->
![](./img/arduino-port.png)

<figcaption style="text-align: center;">Figura 17 - Seleção da porta do Arduino</figcaption>
</figure>
</div>
</div>


---

## Introdução ao Arduino — Uso da IDE
### Carregando um programa de exemplo no Arduino

<div class="grid-50-50">
<div class="grid-element regular">

Agora que você já configurou a IDE do Arduino, vamos carregar um programa de exemplo no Arduino. Para isso, siga os passos a seguir:

1. Clique no menu `File -> Examples -> 01.Basics -> Blink` para abrir o programa de exemplo Blink, como mostrado na Figura 18.
2. Uma nova janela será aberta com o código do programa Blink. Agora, clique no botão `Upload` para carregar o programa no Arduino, como mostrado pela Figura 19.
3. Aguarde o término do carregamento do programa. Se não houver nenhum erro de configuração ou edição acidental de código, o LED do Arduino deverá piscar a cada segundo.

</div>
<div class="grid-element footnotesize">
<figure>

<!-- _class: transparent -->
![centered-img](./img/blink.png)

<figcaption style="text-align: center;">Figura 18 — Localização do exemplo Blink</figcaption>
</figure>
<figure>

<!-- _class: transparent -->
![centered-img](./img/upload.png)

<figcaption style="text-align: center;">

Figura 19 — Botão `Upload`

</figcaption>
</figure>

</div>
</div>


---


## Introdução ao Arduino — Estrutura básica de um programa

<style scoped>
#codigo-container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 80vh;
  text-align: left; /* Para garantir alinhamento do texto à esquerda */
}

#codigo-container pre,
#codigo-container code {
  width: 100%; /* Ocupa a largura total da `div` */
  max-width: 650px; /* Um valor máximo de largura pode ser útil */
  font-size: 16px; /* Ou qualquer tamanho que prefira */
  padding: 20px; /* Ajuste conforme necessário */
  box-sizing: border-box; /* Inclui o padding no cálculo da largura */
}
</style>

<div class="flex-container">
<div class="column-container footnotesize">

A estrutura básica de um programa Arduino, também conhecida como *sketch*, é composta por duas funções principais: `setup()` e `loop()`. Aqui está um breve resumo de cada uma:

1. **Função `setup()`**:
    - É chamada uma única vez quando o programa inicia.
    - Utilizada para inicializar configurações ou preparar o estado inicial do programa.
    - Comum para configurar a velocidade de comunicação serial, definir modos de pinos (entrada, saída), iniciar bibliotecas, etc.

2. **Função `loop()`**:
    - É chamada repetidamente enquanto o Arduino estiver ligado após a execução da função `setup()`.
    - Este é o coração do programa, onde a maior parte do código é executada.
    - Utilizada para ler sensores, controlar atuadores, atualizar o estado do programa, etc.

Além dessas duas funções, um programa Arduino pode conter outras funções e variáveis globais, de acordo com a necessidade de cada projeto.

Um exemplo simples de um programa Arduino que pisca um LED a cada segundo é mostrado ao lado:

</div>
<div class="column-container">
<div id="codigo-container">

```c

// Define o pino do LED
int ledPin = 13;

// A função setup() é chamada uma vez quando o sketch inicia
void setup() {
  // Configura o pino do LED como saída
  pinMode(ledPin, OUTPUT);
}

// A função loop() é chamada repetidamente
void loop() {
  digitalWrite(ledPin, HIGH);   // Acende o LED
  delay(1000);                  // Espera por um segundo
  digitalWrite(ledPin, LOW);    // Apaga o LED
  delay(1000);                  // Espera por um segundo
}
```

</div>
</div>
</div>


---

## Introdução ao Arduino — Wokwi

<div class="small">

<!-- _class: transparent -->
![centered-img](./img/wokwi.png)

- "Wokwi é um simulador de eletrônica online. Você pode usá-lo para simular Arduino, ESP32 e muitas outras placas, componentes e sensores populares." [(LTD., 2024)](#referencias)

### Porque usar Wokwi?

- Não é necessário se preocupar com a aquisição de componentes ou downloads de softwares grandes, pois, o Wokwi apresenta os principiais recursos para simular projetos com microcontroladores.

- A preocupação com danificação de componentes é eliminada, pois, o Wokwi é um simulador online e não é possível queimar *hardware* virtual.

- *Hardware* virtual ilimitado com possibilidade de criação de seus próprios componentes.

- Separação de papéis entre *hardware* e *software* para facilitar a compreensão do funcionamento do sistema.

- Comunidade ativa, amigável com bom suporte para dúvidas.

Maiores informações disponíveis em [https://docs.wokwi.com/pt-BR/](https://docs.wokwi.com/pt-BR/).

</div>


---

## Simulação de Um Circuito no Wokwi

<div class="regular" style="text-align: center;">
Circuito com entradas e saídas digitais com desvios condicionais para controle das saídas.
</div>
<iframe src="https://wokwi.com/projects/391440053861806081" width="100%" height="100%"></iframe>


---

## Simulação de Um Circuito no Wokwi

<div class="regular" style="text-align: center;">
Jogo Simon Says (GENIUS Estrela) simulado com Arduino UNO no Wokwi.
</div>
<iframe src="https://wokwi.com/projects/328451800839488084" width="100%" height="100%"></iframe>


---

<!-- _class: lead -->
# Entradas e Saídas Digitais
## Estruturas de *Hardware* para fazer as conexões de periféricos de entrada e saída digitais no Arduino


---

## Entradas e Saídas Digitais

<style scoped>
    .figure-container {
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .image-caption {
        text-align: center;
        margin: 10px;
    }
    img {
        height: auto;
    }
    .image-caption > img {
        width: auto;
    }
</style>
<div class="small">

Serão apresentados os circuitos necessários para conectar periféricos de entrada e saída digitais ao microcontrolador, pois, ao lidar com periféricos distintos, cada qual possui suas especificações que demandam adaptações para seu correto funcionamento.

### Entradas Digitais no Arduino

- Preparadas para receber sinais digitais em nível lógico TTL (0V a 5V).
    - Nem todos os circuitos digitais operam com nível lógico TTL, assim, são necessárias algumas adaptações.
    - É impossível abordar todos os tipos de entrada digital existentes, pois, muitos ainda nem foram inventados. Entretanto, ao abordar os mais comuns — botões ou chaves — é possível generalizar para compreender os demais. As generalizações que servem para os demais são mostradas pelos dois circuitos da Figura 20.

<figure>
<div class="figure-container">
<div class="image-caption">

<!-- _class: transparent -->
![](./img/NO-contact.png)

<figcaption>(a) Modelo para ligação de um contato (chave, botão) normalmente aberto no Arduino</figcaption>
</div>
<div class="image-caption">

<!-- _class: transparent -->
![](./img/NC-contact.png)

<figcaption>(a) Modelo para ligação de um contato (chave, botão) normalmente fechado no Arduino</figcaption>
</div>
</div>
<figcaption style="text-align: center;">Figura 20 — Modelos genéricos de conexão para botões e / ou chaves no Arduino</figcaption>
</figure>

</div>


---

## Entradas e Saídas Digitais

<div class="small">

### Entradas Digitais no Arduino

- Porque os modelos da Figura 20 generalizam para os demais tipos de chave?
    - Na aula passada vimos os transistores que são como chaves digitais, ou analogamente, como torneiras que controlam o fluxo de água, como mostra a Figura 21.
    - Se os transistores são chaves digitais, logo, quaisquer outros tipos de contatos podem ser modelados por eles. Destarte, as generalizações implicadas pela Figura 20.

<figure>

<!-- _class: transparent -->
![centered-img](./img/torneira.png)

<figcaption style="text-align: center;">Figura 21 — Funcionamento da torneira onde seu registro controla o fluxo da água que sai do cano para a pia</figcaption>
</figure>

</div>


---

## Entradas e Saídas Digitais

<div class="small">

### Entradas Digitais no Arduino

<div class="flex-container">
<div class="column-container">

Retomando as discussões sobre a Figura 20, temos na Figura 20 (a) a representação de um contato normalmente aberto:

<figure>

<!-- _class: transparent -->
![centered-img](./img/NO-contact.png)

<figcaption class="scriptsize" style="text-align: center;">Figura 20 (a)</figcaption>
</figure>

Esse contato recebe esse nome porque seu estado padrão é em nível lógico baixo (0V) que representa a alta impedância, o estado de desligado. Quando acionado, ele fecha o circuito e passa a conduzir, representando o nível lógico alto (5V) que representa o estado de ligado.

</div>
<div class="column-container">

Já na Figura 20 (b) temos a representação de um contato normalmente fechado, que recebe este nome porquê seu estado padrão é em nível lógico alto (5V) que representa o estado de ligado. Quando acionado, ele abre o circuito e passa a não conduzir, representando o nível lógico baixo (0V) que representa o estado de desligado.

<figure>

<!-- _class: transparent -->
![centered-img](./img/NC-contact.png)

<figcaption class="scriptsize" style="text-align: center;">Figura 20 (b)</figcaption>
</figure>

Porquê a entrada Pin 0 passa a não receber corrente? Porquê quando o botão é fechado, a corrente elétrica encontra um caminho sem impedância para circular e não passa em nenhuma fração pelo resistor de \\(1 k\\Omega\\) e, consequentemente, na entrada Pin 0.

</div>
</div>

</div>


---

## Entradas e Saídas Digitais

<div class="small">

### Entradas Digitais no Arduino

A comutação de chaves mecânicas pode ocasionar o aparecimento de ruídos que fazem com que o microcontrolador interprete erroneamente os sinais de entrada. Para contornar este problema podem ser adotadas algumas técnicas:

- ***Debounce***: consiste em aguardar um tempo após a detecção de uma transição de estado para verificar se a chave continua no mesmo estado. Se sim, a transição é considerada válida. Se não, a transição é ignorada. O tempo de espera pode ser implementado por meio de um temporizador ou por meio de um laço que aguarde um tempo fixo.
- ***Pull-up e Pull-down***: consiste em conectar um resistor de valor elevado entre a entrada digital e a alimentação (pull-up) ou entre a entrada digital e o terra (pull-down). 
- **Filtro Capacitivo**: consiste em conectar um capacitor entre a entrada digital e o terra. O capacitor armazena energia e, quando a chave é acionada, a energia armazenada no capacitor é transferida para a entrada digital, evitando que ruídos sejam interpretados como transições de estado, como mostrado pela Figura 21.

<figure>

<!-- _class: transparent -->
![centered-img](img/filtro-rc.png)

<figcaption style="text-align: center;">Figura 21 — Filtro capacitivo para remover ruídos de uma entrada digital</figcaption>
</figure>

</div>


---

## Entradas e Saídas Digitais

<div class="normal">

### Entradas Digitais no Arduino — Exercício manuscrito valendo 1 ponto extra para a AV1

1. Explique o que são e para que servem os resistores de pull-up e pull-down.
2. Explique como usar os resistores pull-up internos do Arduino.
3. Explique os problemas que podem ser ocasionados por uma entrada digital flutuante.
4. Explique se é necessário ou não considerar os sinais de entrada invertidos ao usar resistores pull-up internos do Arduino.
5. Explique como construir uma proteção contra ruídos externa à entrada digital com resistores pull-down.

A entrega deverá ser efetuada digitalizada e em formato PDF no [Ambiente Virtual de Aprendizado](https://ava.cefetmg.br) da disciplina até a data limite lá estabelecida.

</div>


---

## Entradas e Saídas Digitais

<div class="regular">

### Saídas Digitais no Arduino

- As saídas digitais do Arduino podem, virtualmente, controlar quaisquer tipos de dispositivos atuadores, cada qual com suas particularidades.
- Se a corrente necessária para acionamento do atuador for baixa, o Arduino pode controlá-lo diretamente.
    - Uma gama muito restrita de atuadores — elementos de carga — podem ser controlados diretamente, como LEDs, *shields* e módulos periféricos do arduino. A Figura 22 mostra um diagrama genérico para controle de elementos de carga de baixa corrente pelo Arduino.

<figure>

<!-- _class: transparent -->
![centered-img](./img/generic_low_load_element.png)

<figcaption style="text-align: center;">Figura 22 - Diagrama genérico para controle de elementos de carga de baixa corrente pelo Arduino.</figcaption>
</figure>

- Ao observar a Figura 22, verifica-se que a conexão do pino do Arduino, passando pelo resistor de proteção de \\(330 \\Omega\\) e pelo elemento de carga, é conectada ao terra. O que isso implica?
    - Isso implica que para acionar o elemento de carga deve-se escrever o nível lógico alto no pino do Arduino. Isso é feito com a função `digitalWrite(pino, HIGH);`.
</div>


---

## Entradas e Saídas Digitais

<div class="regular">

### Saídas Digitais no Arduino

Se for necessário acionar um elemento de carga ou qualquer outro periférico conectado ao Arduino com um nível lógico BAIXO, como proceder? A Figura 23 mostra como realizar:

<figure>

<!-- _class: transparent -->
![centered-img](./img/generic_low_load_element_low_level.png)

<figcaption style="text-align: center;">Figura 23 - Acionamento de um LED atravérs do nível lógico BAIXO.</figcaption>
</figure>

Ao ver a Figura 23 é possível observar que existe uma conexão de um elemento de nível lógico ALTO (+5V) passando por um resistor de proteção de \\(330 \\Omega\\) e um LED até chegar à porta de saída `PIN 1` do Arduino.

- Se for escrito na porta de saída `PIN 1` o nível lógico ALTO (+5V), então, não existirá diferencial de potencial entre `PIN 1` e o terminal `5V`. Se não existe diferencial de potencial, logo, não existirá corrente elétrica circulando pelo circuito. Portanto, o LED não acenderá.
- Agora, se for escrito na porta de saída `PIN 1` o nível lógico BAIXO (0V), então, existirá um diferencial de potencial de \\(5V\\) entre `PIN 1` e o terminal `5V` fazendo com que a corrente elétrica circule pelo circuito e, portanto, acendendo o LED.

</div>


---

## Entradas e Saídas Digitais

<div class="regular">

### Saídas Digitais no Arduino - LEDs

- LEDs são diodos emissores de luz que emitem luz quando uma corrente elétrica circula entre seu ânodo (A) e cátodo (K).
    - Diodos são componentes eletrônicos que permitem a passagem de corrente elétrica em um único sentido, do ânodo para o cátodo.
    - O ânodo é o terminal positivo e o cátodo é o terminal negativo de um LED e por consequência, de um diodo.
- Por serem dispositivos fundamentais em eletrônica, os LEDs são muito utilizados em circuitos eletrônicos para indicar o estado de um sistema, como por exemplo, se um dispositivo está ligado ou desligado e se necessitamos conhecer os estados de determinado sistema, os LEDs são escolhas naturais para esta tarefa.
- O ânodo de um LED, seu polo positivo, é seu terminal (perna) mais longo(a) e o cátodo, seu polo negativo, é seu terminal (perna) mais curto(a), como ilustrado pela figura 24:

<figure>

<!-- _class: transparent -->
![centered-img](./img/led.png)

<figcaption class="footnotesize" style="text-align: center;">Figura 24 — Cátodo (terminal negativo) de um LED, representado pela letra K e Ânodo (terminal positivo) de um LED representado pela letra A</figcaption>
</figure>

</div>


---

## Entradas e Saídas Digitais

<div class="regular">

### Saídas Digitais no Arduino - Acionamento de cargas genéricas de correntes intermediárias e elevadas.

- Para todas as cargas que demandam correntes maiores do que o microcontrolador pode fornecer, é necessário usar um circuito auxiliar composto de fonte de alimentação para a carga, resistor limitador de corrente para a base do transistor, diodo para proteção do circuito contra descargas, transistor (para atuar como chave digital) e referencial comum de tensão (GND), como ilustrado pela Figura 25.


<figure>

<!-- _class: transparent -->
![centered-img](./img/acionamento-generico.png)

<figcaption class="footnotesize" style="text-align: center;">Figura 25 — Circuito genérico para acionamento de cargas que demandem correntes maiores do que o microcontrolador consegue fornecer</figcaption>
</figure>

A corrente da carga determina quais tipos de resistor e transistor devem ser utilizados. Nos próximos *slides* serão apresentados circuitos para acionamento de cargas elevadas construídos sobre o modelo genérico da Figura 25.

</div>


---

## Entradas e Saídas Digitais

<div class="regular">

### Saídas Digitais no Arduino - Acionamento de cargas genéricas de correntes intermediárias e elevadas.

<div class="flex-container scriptsize">
<div class="column-container">

#### Acionamento de relés.

<figure>

<!-- _class: transparent -->
![grid-img-35](./img/reles.png)

<figcaption style="text-align: center;">Figura 26 — Acionamento de Relé com transistor BC548</figcaption>
</figure>
</div>
<div class="column-container">

#### Acionamento de motor CC

<figure>

<!-- _class: transparent -->
![grid-img-35](./img/motor-mosfet.png)

<figcaption style="text-align: center;">Figura 27 — Acionamento de Motor CC com mosfet IRF530</figcaption>
</figure>
</div>
</div>
<div class="flex-container scriptsize">
<div class="column-container">

#### Acionamento de motores de corrente contínua com reversão de direção.

<figure>

<!-- _class: transparent -->
![grid-img-35](./img/motor-cc-com-reversao.png)

<figcaption style="text-align: center;">Figura 28 — Conexão de motores CC com reversão</figcaption>
</figure>
</div>
<div class="column-container">

#### Acionamento de Lâmpadas
<div class="mid-aligned-container">
<figure>

<!-- _class: transparent -->
![grid-img-35](./img/lampada.png)

<figcaption style="text-align: center;">Figura 29 — Acionamento de Lâmpadas de Sinalização</figcaption>
</figure>
</div>
</div>
</div>
</div>


---

## Entradas e Saídas Digitais

<div class="regular">

### Saídas Digitais no Arduino - Acionamento de cargas genéricas de correntes intermediárias e elevadas.
#### Acionamento de Pequenos Motores

O acionamento de pequenos motores, como mostrado pela Figura 29, exige certos cuidados especiais, como a adição de um capacitor de \\(220nF\\) em paralelo ao motor para filtrar ruídos emitidos pelo motor que interferem no circuito, como mostrado pela Figura 30.

<figure>

<!-- _class: transparent -->
![centered-img](./img/pequeno-motor.png)

<figcaption style="text-align: center;">Figura 29 — Circuito para acionamento de pequenos motores</figcaption>
</figure>
<figure>

<!-- _class: transparent -->
![centered-img](./img/pequeno-motor-capacitor.png)

<figcaption style="text-align: center;">

Figura 30 — Capacitor cerâmico de \\(220nF\\) em parelelo ao pequeno motor.

</figcaption>
</figure>
</div>


---

## Referências Bibliográficas

<a name="referencias"></a>

1. [KERSCHBAUMER, R. Programação Aplicada a Microcontroladores. Luzerna: IFC - Instituto Federal de Educação, Ciência e Tecnologia Catarinense, 2018. ](https://professor.luzerna.ifc.edu.br/ricardo-kerschbaumer/wp-content/uploads/sites/43/2019/11/Apostila-Programa%C3%A7%C3%A3o-Aplicada-a-Microcontroladores-2018-2.pdf)

2. LTD., C. Bem vindo ao Wokwi! | Wokwi Docs. Disponível em: [https://docs.wokwi.com/pt-BR/](https://docs.wokwi.com/pt-BR/). Acesso em: 4 mar. 2024. 


---

![centered-img](./img/thatsallfolks.webp)
