Projet Physique avancée 

# Rapport de projet : Système de Surveillance de Température avec ESP32, MQTT et Node-RED

Realiser par : Téo BARATHIER et Flora GOICOECHEA
Encadrant: 


## Sommaire 



## Introduction

L'objectif est de concevoir un système de surveillance de température en utilisant un capteur LM35, un
ESP32, un Raspberry Pi, et le protocole MQTT. Les données seront transmises au Raspberry Pi
via Mosquitto, stockées dans une base de données SQLite, et affichées en temps réel via Node-
RED. 

### 1. Schéma d’architecture



##2. Acquisition et Transmission des Données

La température est mesurée à l’aide du capteur analogique LM35, connecté à une entrée analogique 33 de l’ESP32. Le capteur fournit une tension proportionnelle à la température ambiante.

<p align="center">
	<img src="photo montage.jpg" width="360" height="360">
</p>

L’ESP32 convertit cette tension en valeur numérique, puis calcule la température en degrés Celsius

Voici le script Arduino pour lire la temperature du capteur LM35 sur ESP 32


```bash
void setup()
{
Serial.begin(9600); // initialise sortie console
}
void loop()
{
int raw = analogRead(26); // entrée analog 2 de l’ESP (need PinMap)
Serial.print("raw : ");
Serial.println(raw);
float volts = (float)raw*5/4095; // il faut forcer volt a être un float sinon la division renvoie un int (donc 0 au lieu de 0.2)
Serial.print("volts : ");
Serial.println(volts);
float degres;
degres = volts/0.01;
Serial.print("degres : ");
Serial.println(degres);
delay(2000);
}
```

##3. Stockage et Exploitation des Données

```bash
void setup()
{
Serial.begin(9600); // initialise sortie console
}
void loop()
{
int raw = analogRead(26); // entrée analog 2 de l’ESP (need PinMap)
Serial.print("raw : ");
Serial.println(raw);
float volts = (float)raw*5/4095; // il faut forcer volt a être un float sinon la division renvoie un int (donc 0 au lieu de 0.2)
Serial.print("volts : ");
Serial.println(volts);
float degres;
degres = volts/0.01;
Serial.print("degres : ");
Serial.println(degres);
delay(2000);
}
```























## Technologies utilisées


## Organisation du travail
Description des étapes.

## Résultats
Ce qui a été réalisé.

## Conclusion
Bilan du projet