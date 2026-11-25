# Fredag-27-11
Presentation

**Översikt**

**Mikroprocessor**  
En *mikroprocessor* är ett litet elektroniskt chip som utför instruktioner. Man kan tänka på den som hjärnan i en dator eller en elektronisk apparat. Genom att skriva ett program talar vi om vad den ska göra. Med hjälp av andra komponenter kan den till exempel reagera på en knapptryckning och tända en lampa.

Vi skriver programmet på en vanlig dator. Sedan använder vi ett verktyg som översätter koden till instruktioner som den lila datorn förstår. Det kallas att *kompilera*. Därefter laddar vi upp programmet till mikroprocessorn, där den kan köras.

Vi kan också använda ett *bibliotek*. Det är färdig kod som hjälper oss med vissa uppgifter, så att vi inte behöver skriva allt själva.

**Arduino**  
För att arbeta praktiskt med programmering och elektronik kan vi använda *Arduino*. Det är en plattform som innehåller både programmerbara kretskort och verktyg för att skriva och ladda upp kod. På många Arduino-kort finns en *mikrokontroller*. Den innehåller en processor som utför instruktionerna, men också minne och funktioner för att ansluta andra komponenter.

Till kortet kan vi koppla exempelvis knappar, sensorer och lampor. Vi skriver programmet i ett verktyg som heter *Arduino IDE* på en vanlig dator. där väljer vi vilken kortmodell vi använder och vilken anslutning kortet är kopplat till. Sedan kan programmet kompileras och laddas upp till kortet.  
Ett vanligt Arduino-program innehåller två basfunktioner: setup() och loop().  
I setup() skriver vi förberedelserna som ska göras en gång när programmet startar.  
I loop() skriver vi instruktionerna som ska upprepas.  

**Portinitialisering**
