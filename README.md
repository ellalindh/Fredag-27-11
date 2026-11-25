# Fredag-27-11
Presentation

**Översikt**

**Mikroprocessor**  
En *mikroprocessor* är ett litet elektroniskt chip som utför instruktioner. Man kan tänka på den som hjärnan i en dator eller en elektronisk apparat. Genom att skriva ett program talar vi om vad den ska göra. Med hjälp av andra komponenter kan den till exempel reagera på en knapptryckning och tända en lampa.

Vi skriver programmet på en vanlig dator. Sedan använder vi ett verktyg som översätter koden till instruktioner som den lila datorn förstår. Det kallas att *kompilera*. Därefter laddar vi upp programmet till mikroprocessorn, där den kan köras.

Vi kan också använda ett *bibliotek*. Det är färdig kod som hjälper oss med vissa uppgifter, så att vi inte behöver skriva allt själva.  
<br><br>
**Arduino**  
För att arbeta praktiskt med programmering och elektronik kan vi använda *Arduino*. Det är en plattform som innehåller både programmerbara kretskort och verktyg för att skriva och ladda upp kod. På många Arduino-kort finns en *mikrokontroller*. Den innehåller en processor som utför instruktionerna, men också minne och funktioner för att ansluta andra komponenter.

Till kortet kan vi koppla exempelvis knappar, sensorer och lampor. Vi skriver programmet i ett verktyg som heter *Arduino IDE* på en vanlig dator. där väljer vi vilken kortmodell vi använder och vilken anslutning kortet är kopplat till. Sedan kan programmet kompileras och laddas upp till kortet.

Ett vanligt Arduino-program innehåller två basfunktioner: setup() och loop().  
I setup() skriver vi förberedelserna som ska göras en gång när programmet startar.  
I loop() skriver vi instruktionerna som ska upprepas.  
<br><br>
**Portinitialisering**  
När vi har kopplat komponenter till Arduino-kortet behöver vi bestämma hur anslutningarna ska användas. Det kallas i det här sammanhanget för *portinitialisering*. Kortets anslutningar kallas ofta för *pinnar*. En pinne kan användas som en ingång som tar emot en signal eller som en utgång som skickar ut en signal.  

Inställningen görs med pinMode(), vanligtvis i pragrammets setup(). Till exempel betyder pinMode(2, INPUT) att pinne 2 ska ta emot signaler, exempelvis från en knapp. pinMode(3, OUTPUT) betyder att pinne 3 ska skicka ut signaler, exempelvis för att styra en lampa.  

Det finns även inställningen INPUT_PULLUPP. Den aktiverar ett inbyggt motstånd som hjälper ingången att få ett stabilt värde när knappen inte är nedtryckt. Om knappen kopplas mellan ingångspinnen och jord, märkt GND på kortet så blir värdet HIGH när knappen är släppt och LOW när knappen är nedtryckt.  
<br><br>
**Kod med förklaringar**  
Nedan kommer jag ett exempel på en kod och ge en enkel förklaring till vad som kommer ske av koden.  

// the setup function runs once when you press reset or power the board  
void setup() {  
  pinMode(D5, OUTPUT);  
  pinMode(D6, OUTPUT);  
  pinMode(D7, OUTPUT);  
}  

// the loop function runs over and over again forever  
void loop() {  
  digitalWrite(D7, HIGH);  
   digitalWrite(D6, HIGH);  
    digitalWrite(D5, HIGH);  // change state of the LED by setting the pin to the HIGH voltage level
  delay(1000);                      // wait for a second  
  digitalWrite(D7, LOW);  
  digitalWrite(D6, LOW);  
  digitalWrite(D5, LOW);   // change state of the LED by setting the pin to the LOW voltage level
  delay(100);                      // wait for a second  
}    

Det här programmet styr tre anslutningar på kortet: D5, D6 och D7. Alla tre får först en hög elektrisk signalnivå i en sekund och sedan en låg signalnivå i en tiondels sekund. Detta upprepas hela tiden i en loop. Dessa anslutningar är till en lampa som kan lysa i rött, grönt och blått.  

Om anslutningarna styr de röda, gröna och blåa delarna i en lampa ändras alla färger tillsammans i den här koden. För att visa färgerna en i taget behöver de styras var för sig. När lampan tänds eller släcks beror på kopplingen.  

1. Förberedelser i setup()
Programmet börjar med setup(). Den delen körs en gång när kortet får ström eller när vi trycker på återställningsknappen.

