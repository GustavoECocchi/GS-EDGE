# GS-EDGE

Integrantes:
- Gustavo Estevam Cocchi / RM562472
- José Henrique Escobar Rizzo / RM564419
- Arthur Pastorello Dias Temistocle / RM562345


==============================================================================================================================================================


Tesseract IoT – Monitoramento Inteligente de Demanda/Luminosidade (FIWARE + MQTT)

O Tesseract IoT é um módulo inteligente de monitoramento que envia leituras de luminosidade para um servidor FIWARE via MQTT utilizando o formato UltraLight 2.0.
Com base no valor (%) lido, o sistema classifica automaticamente o estado como:

LOW – abaixo de 50%

MID – entre 50% e 70%

CRITICAL – acima de 70%

Esse modelo pode ser aplicado para luminosidade, demanda operacional, uso de máquina, fluxo de trabalho ou qualquer dado que varie entre 0% e 100%.

O dispositivo também recebe comandos via MQTT (ex: ligar/desligar LED), simulando um ciclo completo de IoT: sensoriamento + atuação.


==============================================================================================================================================================

Descrição do Problema

Empresas de diversos setores precisam monitorar em tempo real indicadores que representam carga de trabalho, uso de recursos ou condições ambientais.
Quando o nível desses indicadores sobe demais e ninguém percebe, ocorrem:

- gargalos
- atrasos
- perda de produtividade
- falhas operacionais
- Da mesma forma, níveis muito baixos indicam ociosidade, falha em processos ou subutilização de recursos.


==============================================================================================================================================================


Solução Proposta

O Tesseract IoT funciona como um “sensor universal” capaz de transformar qualquer leitura em três estados operacionais:

Faixa	Status	Significado Operacional
0% – 49%	LOW	Nível saudável / Baixa complexidade
50% – 70%	MID	Carga moderada / Atenção
71% – 100%	CRITICAL	Alta carga / Risco de falha

A leitura é realizada por um sensor (LDR no Wokwi), processada no microcontrolador e enviada ao FIWARE através de MQTT.

O FIWARE armazena e disponibiliza esses dados para dashboards, bancos de dados e aplicações externas.


==============================================================================================================================================================

Fluxo de dados:

LDR → microcontrolador lê luminosidade

Código converte para %

Estado é calculado (LOW/MID/CRITICAL)

Publicação via MQTT no tópico /iot/ul

FIWARE IotAgent interpreta UltraLight 2.0

FIWARE Context Broker atualiza a entidade

Dashboard e APIs podem consumir os dados

FIWARE envia comandos MQTT de volta

Dispositivo aciona/desliga LED


==============================================================================================================================================================


<img width="1859" height="893" alt="image" src="https://github.com/user-attachments/assets/81e8f14a-3a47-4d5b-b46c-73772c97bccf" />



<img width="1861" height="895" alt="image" src="https://github.com/user-attachments/assets/cd9e015c-a2b9-4728-8091-c49e40804a2f" />



Link Wokwi: https://wokwi.com/projects/447631166141069313
Link apresentação Canva: https://www.canva.com/design/DAG5WM3x9ZU/CVZna63SRAqhD-BezJfdMA/edit?utm_content=DAG5WM3x9ZU&utm_campaign=designshare&utm_medium=link2&utm_source=sharebutton
LInk vídeo explicativo: https://youtu.be/MhZYPxy5cqI


