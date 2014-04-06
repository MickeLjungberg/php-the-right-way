---
isChild: true
anchor: composer_and_packagist
---

## Composer och Packagist {#composer_and_packagist_title}

Composer är en **briljant** beroendehanterare för PHP. Lista bara ditt projekts beroenden i filen `composer.json` och, 
med några enkla kommandon kommer Composer att automatiskt ladda ner ditt projekts beroenden och ställa in autoladdning åt dig.

Det finns redan en mängd PHP-bibliotek som är kompatibla med Composer, redo att användas i dina egna projekt.
Dessa "paket" finns listade i [Packagist][1], det officiella arkivet för Composer-kompatibla PHP-bibliotek.

### Hur man installerar Composer

Du kan installera Composer lokalt (i din arbetskatalog; ej rekommenderat) eller globalt (d.v.s. i /usr/local/bin). 
Låt oss anta att du vill installera Composer lokalt. Från ditt projekts rootkatalog:

    curl -s https://getcomposer.org/installer | php

Det kommandot kommer att ladda hem `composer.phar` (ett binärt PHP-arkiv). Du kan 
köra detta med `php` för att hantera ditt projekts beroenden. <strong>Notera:</strong> 
Om du skickar in nedladded kod direkt i tolken (som ovan), försäkra dig först om att koden är säker genom att läsa den på nätet.

#### Installation i Windows

För Windowsanvändare är det enklast att använda installationsprogrammet [ComposerSetup][6], 
som installerar Composer globalt och ställer in `$PATH` så att du kan anropa `composer` från 
kommandoraden i vilken katalog som helst.

### Hur man installerar Composer (manuellt)

Att installera Composer manuellt är avancerat; dock finns det olika orsaker till varför en utvecklare kan tänkas föredra denna metod
framför en interaktiv installationsrutin. Den interaktiva installationen undersöker PHP-installationen för att säkra följande:

- att en lämplig version av PHP används
- att `.phar`-filer kan köras korrekt
- att tillräckliga åtkomsträttigheter är satta för vissa kataloger
- att vissa problematiska tillägg inte är laddade
- att vissa inställningar är gjorda i `php.ini`

Då en manuell installation inte gör något av detta måste du bestämma dig om det är värt det för dig.
Om du vill installera manuellt, gör du enligt följande:

    curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
    chmod +x $HOME/local/bin/composer

Sökvägen `$HOME/local/bin` (eller en katalog du själv väljer) bör finnas med i 
miljövariabeln `$PATH`. Det gör att kommandot `composer` är tillgängligt från 
vilken katalog som helst.

När du hittar dokumentation som säger åt dig att köra Composer som `php composer.phar install`, 
kan du ersätta det med:

    composer install
    
Under förutsättning att du installerat Composer globalt.

### Hur man definierar och installerar beroenden

Composer håller reda på ditt projekts beroenden med hjälp av filen `composer.json`. 
Du kan redigera filen för hand om du vill, eller använda Composer. Kommandot 
`composer require` lägger till ett projektberoende och om du inte då redan skapat 
filen `composer.json`, kommer den att skapas åt dig. Här är ett exempel som 
lägger till [Twig][2] som ett beroende till ditt projekt:

	composer require twig/twig:~1.8

Alternativt kan du använda kommandot `composer init` för att skapa en komplett 
`composer.json`-fil för ditt projekt. Oavsett hur du gör, så kan du efter att 
filen skapats kommendera Composer att ladda hem och installera dina beroenden 
till katalogen `vendors/`. Det här gäller även för projekt du laddat hem som 
redan har filen `composer.json`:

    composer install

Lägg sedan till denna rad i din applikations huvudsakliga PHP-fil; det här berättar för PHP att den ska använda
Composers autoladdning för dina projektberoenden:

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Nu kan du använda dina projektberoenden, och de autoladdas vid behov.

### Uppdatera dina beroenden

Composer skapar filen `composer.lock` som sparar information om exakt vilka versioner 
av de olika paketen som laddades ner när du först körde `php composer.phar install`. 
Om du delar dina projekt med andra utvecklare och filen `composer.lock` finns med 
som en del i din distribution, kommer de att få samma versioner som du när de kör 
`php composer.phar install`. För att uppdatera dina beroenden, kör du
`php composer.phar update`.

Det här är användbart när du definierar versionskraven flexibelt. Till exempel 
betyder versionskravet ~1.8 "allting efter version 1.8, men innan 2.0.x-dev". 
Du kan också använda uttrycket `*` som till exempel `1.8.*`. Nu uppgraderar 
kommandot `php composer.phar update` alla dina beroenden till den senaste versionen 
som matchar de begränsningar du definierar.

### Uppdateringsmeddelanden

För att ta emot meddelanden om nya versioner kan du registrera dig hos [VersionEye][3], 
en webbtjänst som kan övervaka dina GitHub och BitBucket-kontons `composer.json`-filer 
och skicka e-postmeddelanden med nya paketutgåvor.

### Övervaka säkerhetsproblem i dina beroenden

[Security Advisories Checker][4] finns som en webbtjänst och ett kommandoradsverktyg, och båda 
undersöker filen `composer.lock` och meddelar dig om du behöver uppdatera några av dina 
beroenden.

* [Lär dig om Composer][5]

[1]: http://packagist.org/
[2]: http://twig.sensiolabs.org
[3]: https://www.versioneye.com/
[4]: https://security.sensiolabs.org/
[5]: http://getcomposer.org/doc/00-intro.md
[6]: https://getcomposer.org/Composer-Setup.exe

