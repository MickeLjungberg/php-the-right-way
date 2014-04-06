---
anchor: dependency_management
---

# Beroendehantering {#dependency_management_title}

Det finns mängder av PHP-bibliotek, ramverk och komponenter att välja mellan. 
Ditt projekt kommer troligtvis att använda flera av dessa - vilket innebär att ditt projekt är beroende av dem. 
Tills nyligen fanns det inget bra sätt i PHP att hantera projektberoenden. Även om du hanterade dem manuellt, 
fanns det alltid problem med autoladdningar. Inte längre.

För tillfället finns det två huvudsakliga pakethanteringssystem för PHP - Composer och PEAR.
Vilket är rätt för dig? Svaret är båda.

 * Använd **Composer** när du hanterar beroenden för ett projekt.
 * Använd **PEAR** när du hanterar beroenden för PHP som helhet i ditt system.

Generellt sett är Composer-paket bara tillgängliga i de projekt du specifikt anger, medans PEAR-paket 
finns tillgängliga för alla dina PHP-projekt. Även om PEAR kan verka som den enklare lösningen vid en 
första anblick, så finns det ändå fördelar med att hantera beroenden på projektbasis.
