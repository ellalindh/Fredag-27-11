# Fredag-27-11
Presentation

**Översikt**  
Den här veckan har vi arbetat med grunderna i hur programmering och elektronik samverkar. Vi har lärt oss vad en mikroprocessor är och hur vi kan skriva, kompilera och ladda upp program till ett Arduino-kort. Vi har också gått igenom portinitialisering, alltså hur kortets anslutningar ställs in för att ta emot eller skicka ut signaler.  
<br><br>

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

Det finns även inställningen INPUT_PULLUP. Den aktiverar ett inbyggt motstånd som hjälper ingången att få ett stabilt värde när knappen inte är nedtryckt. Om knappen kopplas mellan ingångspinnen och jord, märkt GND på kortet så blir värdet HIGH när knappen är släppt och LOW när knappen är nedtryckt.  
<br><br>
**Kod med förklaringar**  
Nedan kommer jag ge ett exempel på en kod och ge en enkel förklaring till vad som kommer ske av koden.  

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

Här används instruktionerna pinMode(D5, OUTPUT), pinMode(D6, OUTPUT) OCH pinMode(D7, OUTPUT). De bestämmer att just de tre pinnarna på kortet ska vara utgångar. Det betyder att koertet kan skivka elektriska signaler genom dem för att styra lampan. Det här programmets portinitialisering.  

2. Upprepningen börjar i loop()  
När förberedelserna är klara går programmet vidare i loop(). instruktionerna där körs uppifrån och ned. När programmet når slutet börjar det om från början av loopen.

Det gör att bara behöver skriva förloppet en gång för att det ska upprepas så länge programmet körs.  

3. Utgångarna sätts på HIGH  
De tre följande instruktionerna använder digitalWrite() för att sätta D7, D6 och D5 på HIGH. Det betyder att utgångarna får en hög elektrisk signalnivå.  

Raderna körs efter varandra, men utan någon paus emellan dem. Alltså sker ändringarna väldigt snabbt. Alla tre utgångar är sedan kvar på HIGH tills programmet ändrar dem.  

4. Programmet väntar 1 sekund  
Instruktionen delay(1000) gör att programmet väntar i en sekund innan det fortsätter. Talet anges i millisekunder.

I det här programmet innebär detta att lampan lyser i en av färgerna i en sekund.  

5. Utgångarna sätts på LOW  
När det har gått en sekund så används digitalWrite() igen, men den här gången sätts D7, D6, D5 på LOW. Det betyder att utgångarna får en låg elektrisk signalnivå.

Alla tre ändras även här snabbt efter varandra.  

(Beroende på lampans koppling kan den höga signalnivån tända lampan och den låga släcka den, eller tvärt om.)  

6. Programmet väntar en tiondels sekund  
Instruktionen delay(100) gör en ny paus. den här gången är pausen 100 millisekunder, vilket är en tiondels sekund.

(Kommentaren bredvid den sista raden i koden säger att programmet väntar en sekund. men det stämmer inte med koden. Det är talet inne i parentesen som bestämmer pausen.)  

7. Förloppet börjar om  
Efter den sista pausen är instruktionerna i loop() klara. Programmet går då tillbaka till början av samma del och sätter återigen alla tre utgångar på HIGH.  
<br><br>
Alltså är det återkommande förloppet: hög signalnivå i en sekund, låg signalnivå i en tiondels sekund och sedan om från början. setup() körs inte igen under upprepningen, eftersom pinnarna redan har ställts in.

