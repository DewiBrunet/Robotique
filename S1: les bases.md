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

Les sources de ces 5 séances sont en partie des MOOC, de l’enseignement de Jim et beaucoup de pratique.

![b6649669fed012ba3513717069567ad0](https://user-images.githubusercontent.com/25649502/36629625-7e30717a-1958-11e8-8aee-029d43c0d958.jpg)

# L'Arduino

Ok, c'est quoi ce truc?

![arduino_uno_test](https://user-images.githubusercontent.com/25649502/36629643-c7ed3974-1958-11e8-8ce9-7ef8a06f8592.jpg)

En somme L'Arduino (ici "Arduino UNO") est un "board" avec plein d'éléments dessus.   
Ce qui est important dessus c'est le **microcontrôleur**, la longue broche noire qui va contenir le code (ce qu'on veut dire de faire).     
- A gauche, les **broches d'alimentation analogique** (5V, 3,3V et Gnd) et les **entrées analogiques**.          
- A droite, les **entrées/sorties numériques**. 

Donc en gros on a un microcontroleur qui va recevoir des informations en code, ici un langage C++ et va les renvoyer pour effectuer des actions (allumer une led, faire fonctionner un moteur...).          
- Analogique correspond à une valeur multiple (exemple faire fonctionner des capteurs sonores)         
- Numérique correspond à une valeur binaire (exemple allumer une lampe)         

On retrouve aussi une prise d'alimentation USB, les LED TX et RX (témoins réception/émission) et un bouton reset.                     
Le reste n'est pas important pour l'instant.  


![arduino_explications](https://user-images.githubusercontent.com/25649502/36629678-7eff8324-1959-11e8-8a99-303a29cc5637.png)


Dans l'apprentissage d'Arduino, il y a donc deux parties : le code et les branchements.                
C'est parfois frustrant car le code prend une part importante au début mais c'est nécessaire pour comprendre la logique et l'alphabet du langage.             

# Le code

![c7105662eb2fb3885f460496f0724e881b8113cc8563e79806519a15c310a062](https://user-images.githubusercontent.com/25649502/36629886-071d6b6a-195d-11e8-9527-a4283ebfaae3.jpg)

Ouvrir le programme Arduino (installation sur : https://www.arduino.cc/en/Guide/HomePage )

![arduino software basic](https://user-images.githubusercontent.com/25649502/36629979-dbc2218e-195e-11e8-9cf5-5e45d24e3ff0.png)

La ça va c'est simple.
On vois deja 2 parties : voice setup et voice loop.
- Voice setup pour indiquer 1 action
- Voice loop pour indiquer une action en boucle

... et c'est quoi tout ces /{;)/(}?    
(  ) = rien écrire dedans         
{  } = permet de délimiter une action, d'organiser son code        
// = permet d'écrire des commentaires pour soi ou pour les autres         
; = marque la fin d'une commande           

Conseils : 
- toujours mettre les **{ }** sur une ligne à part/en décallé pour plus de visibilité
- toujours vérifier qu'il y a un **;** à la fin de chaque ligne

Les autres commandes de base seront :
pinMode() = "utiliser la pin n°.."       
digitalWrite() = "envoyer en sortie..."                     
delay() = "faire une pause de .."             

## Premier exercice : allumer une LED!
(après avoir vérifié dans Tool -> Board que le programme reconnait notre type d'Arduino)

void setup() {           
  pinMode(13, OUTPUT);    // reconnaitre la digital pin 13 comme output.               
}          

void loop() {          
}

## Deuxième exercice : clignoter une LED!
void setup() {          
  pinMode(13, OUTPUT);          
}          

void loop() {          
  digitalWrite(13, HIGH);            // Allumer LED          
  delay(1000);                       // Attendre 1 seconde          
  digitalWrite(13, LOW);             // Eteindre LED          
  delay(1000);                       // Attendre 1 seconde          
}

