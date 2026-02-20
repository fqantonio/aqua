# Nicla Vision

## Sensors/Inputs onboard
- Câmara
- Time-of-flight long distance ranging sensor
- Microfone omnidireccional
- IMU de 6-eixos (*inertial measurment unit*) (3 eixos acelerómetro + 3
  eixos giroscópio)

## Comunicação
- USB
- Bluetooth LE
- Wifi

# Questões a resolver:

1. Como transmitir vídeo e dados de sensores de forma eficiente para terra
2. Como gravar vídeo e dados para análise posterior
3. Qual o tempo de "streaming" que a bateria aguenta
4. 

Location of Nicla Board libraries 
~/Library/Arduino15/packages/arduino/hardware/mbed_nicla

# LOG Testes


2026-02-19
¯¯¯¯¯¯¯¯¯¯
* Apesar de funcionar o streaming em formato MJPEG (movie jpeg) é muito lento.
  Os melhores resuntados são até o momento:

--- Resoluções
HVGA - 480x320 - transmite a aproximadamente 15 fps.

Resoluções mais altas resultam em erros. Talvez uma solução seja gravar os
vídeos localmente num cartão SD ou num raspberry pi.


2026-02-20
¯¯¯¯¯¯¯¯¯¯
A experiência com o openMV mostra que:

QVGA 320x240 - Funciona relativamente bem, aprox 25fps
HVGA 480x320 - Funciona mas mais lentamente, aprox 11-15fps
VGA 640x480 - Runtime Error Frame Buffer Overflow
SVGA 800x600 - Runtime Error Frame Buffer Overflow
HD 1280x720 - Runtime Error Frame Buffer Overflow

O problema parece ser que a Nicla Vision não tem memória interna suficiente para
guardar uma imagem maior. Ou seja, apesar do sensor da câmara ser de 2Mp não se
pode utilizar.

Acesso ao servidor AP 
Rede: OPENMV\_AP
Pass: 1234567890

XXX (Mudar mais tarde para algo mais personalizado)

Aceder a http://192.168.4.1:8080/ via Browser ou utilizando o VLC (para gravar
por exemplo, via File-\>Open Network)

### I2C

Scanning I2C bus 1
No I2C devices found
Scanning I2C bus 2
Found devices:
 - 0x08
 - 0x29
Scanning I2C bus 3
Found devices:
 - 0x3C

## SPI

### Battery

MAX17262REWL+T Fuel Gauge



```python
from machine import Pin
for p in dir(Pin.board):
    print(p)
```

A0
A1
A2
CIPO
COPI
CS
D0
D1
D2
D3
DAC1
DAC2
I2C1_SCL
I2C1_SDA
I2C2_SCL
I2C2_SDA
I2C3_SCL
I2C3_SDA
LEDB
LEDG
LEDR
LED_BLUE
LED_GREEN
LED_RED
LPIO0
LPIO1
LPIO2
LPIO3
OSCEN
PA0
PA1
PA10
PA11
PA12
PA13
PA14
PA15
PA2
PA3
PA4
PA5
PA6
PA7
PA8
PA9
PB0
PB1
PB10
PB11
PB12
PB13
PB14
PB15
PB2
PB3
PB4
PB5
PB6
PB7
PB8
PB9
PC0
PC1
PC10
PC11
PC12
PC13
PC14
PC15
PC2
PC3
PC4
PC5
PC6
PC7
PC8
PC9
PD0
PD1
PD10
PD11
PD12
PD13
PD14
PD15
PD2
PD3
PD4
PD5
PD6
PD7
PD8
PD9
PE0
PE1
PE10
PE11
PE12
PE13
PE14
PE15
PE2
PE3
PE4
PE5
PE6
PE7
PE8
PE9
PF0
PF1
PF10
PF11
PF12
PF13
PF14
PF15
PF2
PF3
PF4
PF5
PF6
PF7
PF8
PF9
PG0
PG1
PG10
PG11
PG12
PG13
PG14
PG15
PG2
PG3
PG4
PG5
PG6
PG7
PG8
PG9
PH0
PH1
PH10
PH11
PH12
PH13
PH14
PH15
PH2
PH3
PH4
PH5
PH6
PH7
PH8
PH9
PI0
PI1
PI10
PI11
PI12
PI13
PI14
PI15
PI2
PI3
PI4
PI5
PI6
PI7
PI8
PI9
PJ0
PJ1
PJ10
PJ11
PJ12
PJ13
PJ14
PJ15
PJ2
PJ3
PJ4
PJ5
PJ6
PJ7
PJ8
PJ9
PK0
PK1
PK2
PK3
PK4
PK5
PK6
PK7
SCKL
SCL
SDA
SE05X_EN
UART1_RX
UART1_TX
UART4_RX
UART4_TX
UART6_RX
UART6_TX
UART8_RX
UART8_TX
UART_RX
UART_TX
USB_DM
USB_DP

