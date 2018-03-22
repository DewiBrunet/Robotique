# Ou j’en suis?


En 2017, j’ai fait 5 séances ou j’ai appris :
-	La composition d’Arduino UNO
-	Les variables
-	Les constantes
-	Les conditions
-	Les boucles et calculs
-	La logique de circulation
-	La loi d’Ohm
-	La tension et intensité
-	Les calculs de résistance
-	A faire un chenillard

Je vais les réviser en les documentant ici.


![b6649669fed012ba3513717069567ad0](https://user-images.githubusercontent.com/25649502/36629625-7e30717a-1958-11e8-8aee-029d43c0d958.jpg)

# L'Arduino

Ok, c'est quoi ce truc?

![arduino_uno_test](https://user-images.githubusercontent.com/25649502/36629643-c7ed3974-1958-11e8-8ce9-7ef8a06f8592.jpg)

En somme L'Arduino (ici "Arduino UNO") est un "board" avec plein d'éléments dessus.   
Ce qui est important c'est 
- Le **microcontrôleur**, la longue broche noire qui va contenir le code (ce qu'on veut dire de faire).     
- A gauche, les **broches d'alimentation analogique** (5V, 3,3V et Gnd) et les **entrées analogiques**.          
- A droite, les **entrées/sorties numériques**. 

Donc en gros on a un microcontroleur qui va recevoir des informations en code, ici un langage C/C++ et va les renvoyer pour effectuer des actions (allumer une led, faire fonctionner un moteur...).          
- Analogique correspond à une valeur multiple (exemple faire fonctionner des capteurs sonores)         
- Numérique correspond à une valeur binaire (exemple allumer une lampe). Le signal sera donc LOW (0) ou HIGH (1)        

On retrouve aussi une prise d'alimentation USB, les LED TX et RX (témoins réception/émission) et un bouton reset.                     
Le reste n'est pas important pour l'instant.  

![arduino_explications](https://user-images.githubusercontent.com/25649502/36629678-7eff8324-1959-11e8-8a99-303a29cc5637.png)

Dans l'apprentissage d'Arduino, il y a deux parties : le code et les branchements.                
C'est parfois frustrant car le code prend une part importante au début mais c'est nécessaire pour comprendre la logique et l'alphabet du langage avant de se lancer sur la confection des circuits.            

# Le code

![c7105662eb2fb3885f460496f0724e881b8113cc8563e79806519a15c310a062](https://user-images.githubusercontent.com/25649502/36629886-071d6b6a-195d-11e8-9527-a4283ebfaae3.jpg)

Ouvrir le programme Arduino (installation sur : https://www.arduino.cc/en/Guide/HomePage )
Une fois ouvert, on peux clarifier 2 choses :
- Tool -> Board pour que le programme reconnaisse notre type d'Arduino
- Tool -> Port pour définir le port USB de lecture

![arduino software basic](https://user-images.githubusercontent.com/25649502/36629979-dbc2218e-195e-11e8-9cf5-5e45d24e3ff0.png)

La ça va c'est simple.
On vois 2 parties : voice setup et voice loop.
- Voice setup pour indiquer 1 action
- Voice loop pour indiquer une action en boucle

... et c'est quoi tout ces /{;)/(}?    
(  ) = rien écrire dedans         
{  } = permet de délimiter une action, d'organiser son code        
// = permet d'écrire des commentaires pour soi ou pour les autres         
; = marque la fin d'une instruction          

Conseils : 
- toujours mettre les **{ }** sur une ligne à part/en décallé pour plus de visibilité
- toujours vérifier qu'il y a un **;** à la fin de chaque ligne
- bien respecter les codes d'écriture (majuscule, espace...)
- ne pas chercher à apprendre par coeur le code, on peux facilement le copié collé. Le plus important c'est de comprendre la logique et comment désceller les erreurs.

Les autres commandes de base seront :
pinMode() = "utiliser la pin n°.."       
digitalWrite() = "envoyer en sortie..."                     
delay() = "faire une pause de .."             

## Petit rappel des cours de physique avant de s'y mettre                        

Le courant circule toujour du + vers le -                    
Le + c'est l'arrivée du courant (en général 5V).                   
Le - c'est la masse (noté Gnd pour Ground), c'est le point de référence 0 Volt.                   

### la loi d'Ohm

Si je savais que j'aurai eu besoin de mes cours de physique, j'aurai écouté en classe ><             
Normalement, il y a pas beaucoup de théories à apprendre mais celle la est essentielle.             
Pourquoi?             
Une fois qu'on a notre matériel, qu'on sait comment écrire un code reste à savoir comment choisir les composants et ou les brancher.     
C'est ici que la loi d'Ohm nous est utile pour :             
- calclculer la **tension** aux bornes (en Volts) - U            
- calculer l'intensité du **courant** qui traversse (en Ampères) - I            
- calculer la **résistance** (en Ohms) - R            

![loi_d ohm](https://user-images.githubusercontent.com/25649502/36675904-8d323b64-1b0a-11e8-8ee2-d557a6a2935b.png)

(U = RxI donc I = U/R donc R = U/I)                

DONC par exemple si j'ai une alimentation à 5 Volts et je veux faire fonctionner une LED de 0,02 Ampère, j'aurai besoin d'une résistance de 250Ω.

5 = R x 0,02         
R = 5/0,02         
R = 250Ω         

![ohms-law-cartoon-cropped](https://user-images.githubusercontent.com/25649502/36675842-646830ee-1b0a-11e8-9b82-0ea712af4eb5.jpg)



## C'est parti, premier exercice : allumer une LED!

Ok pour ça, j'ai besoin de mon Arduino, du cable d'alimentation, d'une LED, de la bonne résistance, de câble et d'une breadboard.

### Une LED

Bin oui, c'est quoi?
Composant semi conducteur qui brille si on le branche correctement.
Composé d'une anode pour connecter à l'arrivée du courant et d'une cathode pour connecter au Gnd.
Le - (cathode) a une branche plus petite et à un bord troncqué.

![led-anatomy-1024x455](https://user-images.githubusercontent.com/25649502/36680045-039d9e92-1b15-11e8-87d4-f7a4b336f4d6.png)

### Une breadboard

L'Arduino est tout petit et rapidement, il faut passer sur une breadboard pour faire un circuit.
Attention à bien saisir les connections de cet élément :

![basic_breadboard_layout](https://user-images.githubusercontent.com/25649502/36680195-5a772f12-1b15-11e8-9caf-96d5b9a8ea6a.png)


**Le code** 

void setup() {                
  pinMode(10, OUTPUT);// définir ledPin en temps que sortie
}

void loop() {
  digitalWrite(10, HIGH);//allumer la LED
}

**le circuit**

Quelques conseils utiles :
- Le courant circule toujours du + vers le - (Gnd)
- Toujours mettre une résistance au cas ou (ici n'importe quelle valeur Ohm car c'est qu'une LED)
- Toujours "Verify" le code sur le logiciel pour voir si il y a pas une erreur

Concrètement : 
1) je commence mon branchement à la broche 10, qui est défini en OUTPUT (donc il va envoyer du courant/des infos)
2) j'atteri sur la breadboard pour avoir plus de place
3) je place une résistance au cas ou
4) je place ma LED correctement (bou troncqué à la fin, vers Gnd)
5) je replace un cable pour joindre ma LED à la fin de mon circuit, sur Gnd

![untitled-1](https://user-images.githubusercontent.com/25649502/36681082-e42b273e-1b17-11e8-9e96-d6c728c93450.jpg)

## Deuxième exercice : clignoter une LED!
Même topo, rien à changer sur le branchement, jusque à rajouter quelques lignes de code :

void setup() {          
  pinMode(10, OUTPUT);          
}          

void loop() {          
  digitalWrite(10, HIGH);            // Allumer LED          
  delay(1000);                       // Attendre 1 seconde          
  digitalWrite(10, LOW);             // Eteindre LED          
  delay(1000);                       // Attendre 1 seconde          
}

![telechargement](https://user-images.githubusercontent.com/25649502/36681528-24e51a0e-1b19-11e8-93ba-ce7e0e33e6b1.jpg) 

**17 mars 2018**

Difficile de se motiver et se cadrer sans structure... Alors je décide de suivre "Arduino class" sur Instructables : https://www.instructables.com/class/Arduino-Class/

J'ai skip la première leçon pour passer direct aux expérimentations avec les leds. C'est très bien fait, simple et clair.

C'est parti pour un chenillard!!

![20180317_212857](https://user-images.githubusercontent.com/25649502/37779847-a954363a-2ded-11e8-8fa5-8aa528434508.jpg)

Petit problème : ma 4ème LED s'allume pas... est-ce parce qu'elle est bleue? (en inverssant + et - ça marche)


**21 mars 2018**

J'ai du mal à me concentrer sur la théorie, sur le code. Il y a beaucoup de nouvelles logiques, de vocabulaire et je suis frustré de pas en voir la finalité immédiate et surtout de commancer à faire fonctionner des moteurs et capteurs! Bref, j'apprends parfois mieux par la pratique...

Avec l'appli "Learn Arduino", il y a des tutos pour les moteurs, et si je testais celui sur les "moteur DC"?
DC Motor (Direct Current Motor), les plus courants on une borne + et une borne - (en fonction du sens de branchement, il tournera dans l'une ou l'autre direction).

Pour travailler avec mon DC motor 5V, j'ai besoin :
- Arduino
- Transistor PN2222
- Diode 1N4001
- Resistance 270

Petit montage et code rapide :
![screenshot_20180322-165832](https://user-images.githubusercontent.com/25649502/37783122-f4338b40-2df4-11e8-81d4-02f66e1e8371.png)
![screenshot_20180322-165850](https://user-images.githubusercontent.com/25649502/37783119-f4007912-2df4-11e8-949e-9f809afec406.png)

Arrg, ça marche pas...
Après mise à jour du logiciel (erreur "could not find member name...") et changement de direction du transistor (le mieux n'est pas tronqué mais à la place il y a une petite tige) ça fonctionne :)
Bon par contre ça tourne trop vite et ça s'arrête pas :(

Alors go pour la suite : gérer la vitesse.
Codage, branchement, ça fonctionne pas... alors allons cherche un autre tuto, sur dummies.com ;p en plus il y a un bouton régulateur dedans, on va pouvoir s'amuser!
http://www.dummies.com/computers/arduino/how-to-control-the-speed-of-a-dc-motor-with-the-arduino/

![381386 image0 1](https://user-images.githubusercontent.com/25649502/37782832-367e18b8-2df4-11e8-9769-8c773009bbfc.jpg)

et le code :

int potPin = A0;               
int motorPin = 9;               
int potValue = 0;               
int motorValue = 0;               
void setup() {               
 Serial.begin(9600);               
}               
void loop() {               
 potValue = analogRead(potPin);                 
 motorValue = map(potValue, 0, 1023, 0, 255);               
 analogWrite(motorPin, motorValue);                 
 Serial.print("potentiometer = " );                    
 Serial.print(potValue);               
 Serial.print("t motor = ");               
 Serial.println(motorValue);               
 delay(2);                   
}               

Ca marche :) par contre j'arrive pas encore à comprendre la logique de la régulation (c'est sur la ligne " motorValue = map(potValue, 0, 1023, 0, 255);"??)



