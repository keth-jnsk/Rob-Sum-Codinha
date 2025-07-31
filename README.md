> If you're not a Portuguese reader, you can skip to the bottom of the page and you'll find an English version of this document! Hope it helps!

# Robô de Sumô
![blob](https://web.whatsapp.com/ada6d4c9-62db-4c92-9d84-43f6a6160315)

> Robô em Arduino programado para lutar em uma arena redonda preta, com os limites pintados de branco. 
- Dia da Luta e nosso Robô: https://www.instagram.com/p/DLAwvT4xAuQ/?img_index=5&igsh=Y3MxdnUzNWdwbW1s
- Nosso robô conquistou pela estética marcante inspirada na Hello Kitty e ficou exposto para visualização no laboratório de robótica da UniAmérica!
  
## Componentes
 - 1x Arduino Uno
 - Jumpers
 - 1x Sensor Ultra-Sônico HC_SR04
 - 2x Sensores de linha infra-vermelho TCRT5000
 - 1x Ponte H Dupla L298N
 - 2x Motores de redução e suas respectivas rodas
## Alimentação
 - 2x baterias 3000MAH 20A/3.7V ou similar
## Comportamento
> De acordo com as regras, 3 segundos depois de seu operador soltar o botão START, o robô irá começar a agir, em loop:
- Irá para frente, até encontrar seu oponente ou os limites da arena
- Se encontrar seu oponente, irá focar em persegui-lo e o empurrar para fora da arena 
- Se ao tentar empurrar o oponente para fora da arena, perceber que está em cima dos limites da arena, irá recuar
- Se encontrar os limites da arena, irá aplicar a estratégia "bailarina", girando incansávelmente a fim de desviar e dificultar o robô oponente de chegar ao seu encontro
## Dicas
### Esse repositório instrui apenas o circuito eletrônico e programação do robô e é independente da carcaça usada para suporte.
- Ou seja, use a imaginação para construir seu próprio chassi e robô! No nosso projeto, usamos ACM, e criatividades para desenhar.

### Use a ponte H apenas para controlar a direção das rodas
 - Pois o Arduino, mesmo ligado em baterias potentes, não irá fornecer muita energia para os motores ligados na ponte H. 
 - É possível ligar paralelamente: 
 > Baterias -> Arduino
 
 > Baterias -> VCC da Ponte H 

-------------------------------------------------------------------------------------------------------------------------------------------------------------------

If you’re not a Portuguese reader, you can skip to the bottom of the page and you’ll find an English version of this document! Hope it helps!

Sumo Robot

blob:https://web.whatsapp.com/ada6d4c9-62db-4c92-9d84-43f6a6160315

Arduino-powered robot programmed to fight in a black round arena with white-painted borders.

- Fight Day and Our Robot: https://www.instagram.com/p/DLAwvT4xAuQ/?img_index=5&igsh=Y3MxdnUzNWdwbW1s
- Our robot stood out for its striking Hello Kitty-inspired design and was displayed in the robotics lab at UniAmérica!

Components
	•	1x Arduino Uno
	•	Jumper wires
	•	1x HC-SR04 Ultrasonic Sensor
	•	2x TCRT5000 Infrared Line Sensors
	•	1x L298N Dual H-Bridge Motor Driver
	•	2x Gear Motors and their respective wheels

Power Supply
	•	2x 3000mAh 20A/3.7V batteries or similar

Behavior

According to the rules, 3 seconds after the operator releases the START button, the robot will begin acting in a loop:

  It will move forward until it finds its opponent or the arena boundaries
	If it detects the opponent, it will focus on chasing and pushing it out of the arena
	If, while pushing the opponent, it realizes it is on the arena border, it will back up
	If it detects the border, it will execute the “ballerina” strategy — spinning endlessly to dodge and make it difficult for the opponent to engage

Tips

This repository provides only the electronic circuit and programming of the robot. It is independent of the chassis used for support.
	•	In other words, use your imagination to build your own chassis and robot! In our project, we used ACM and creative ideas for the design.

Use the H-bridge only to control the wheel direction
	•	Because the Arduino, even when powered by strong batteries, will not supply much power to the motors connected to the H-bridge
	•	You can connect in parallel:

Batteries → Arduino

Batteries → H-Bridge VCC

## Contributors

<table>
  <tr>
    <td><img src="https://github.com/keth-jnsk.png?size=64" width="64"/></td>
    <td><img src="https://github.com/isabeliCnn.png?size=64" width="64"/></td>
    <td><img src="https://github.com/Aldryyn.png?size=64" width="64"/></td>
  </tr>
  <tr>
    <td><a href="https://github.com/keth-jnsk">Kethelyn Januskevicius</a></td>
    <td><a href="https://github.com/isabeliCnn">Isabeli Claumann</a></td>
    <td><a href="https://github.com/Aldryyn">Aldryn Maciel</a></td>
  </tr>
</table>
