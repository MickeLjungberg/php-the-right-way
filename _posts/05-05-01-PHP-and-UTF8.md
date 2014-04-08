---
isChild: true
anchor: php_and_utf8
---

## PHP och UTF-8 {#php_and_utf8_title}

_Den här sektionen skrevs ursprungligen av [Alex Cabal](https://alexcabal.com/) hos 
[PHP Best Practices](https://phpbestpractices.org/#utf-8)_.

### Det finns inga enradskoder. Var försiktig, noggrann och detaljerad.

För tillfället finns inget lågnivåstöd för Unicode i PHP. Det finns metoder för försäkra sig om 
att UTF-8-strängar behandlas korrekt, men de är inte enkla, och det kräver att man jobbar med 
nästan alla nivåer i en webbapplikation, från HTML och SQL till PHP. Vi ämnar att ge en kortfattad, 
praktisk sammanfattning.

### UTF-8 på PHP-nivån

Grundläggande strängoperationer, som att sammanfoga två strängar och tilldela strängar till variabler, 
kräver inte att UTF-8-strängar behandlas på något speciellt sätt. Däremot kräver de flesta strängfunktioner 
(som `strpos()` och `strlen()`) speciell hänsyn. Dessa funktioner har ofta en motsvarighet i funktioner 
med prefixet `mb_*`: till exempel, `mb_strpos()` och `mb_strlen()`. Sammantaget kallas dessa motsvariga 
funktioner för flerbytesfunktioner för strängar. Dessa funktioner är utvecklare för att kunna hantera 
just Unicodesträngar.

Du måste använda dessa `mb_*`-funktioner när du hanterar Unicodesträngar. Om du till exempel använder 
`substr()` på en UTF-8-sträng, är chansen god att resultatet innehåller skräptecken. Den korrekta 
funktionen att använda för att utföra samma operation på en UTF-8-sträng skulle vara `mb_substr()`.

Det svåra är att alltid komma ihåg att använda `mb_*`-funktionerna. Om du glömmer det bara en enda 
gång, är risken stor att dina Unicodesträngar blir till skräpsträngar när de bearbetas.

Inte alla strängfunktioner har en motsvarighet med ett `mb_*`-prefix. Om en motsvarighet saknas för 
den operation du behöver utföra, kan det hända att du får leva med det.

Du bör också anropa funktionen `mb_internal_encoding()` överst i alla PHP-skript du skriver (eller 
överst i ditt globala skript), direkt följt av ett anrop till `mb_http_output()` om ditt skript skickar
utdata till en webbläsare. Att specifikt ange teckenkodningen i alla dina skript kan bespara dig 
mycket huvudvärk längre fram.

Slutligen har många PHP-funktioner som bearbetar strängar en valfri parameter via vilken du kan specificera 
teckenkodningen. Du bör alltid ange UTF-8 när du ges valet. Till exempel har `htmlentities()` ett 
alternativ för teckenkodning, och du bör alltid ange UTF-8 om du hanterar sådana strängar.

Värt att notera är att sedan version 5.4.0 av PHP är UTF-8 standardkodningen för 
`htmlentities()` och `htmlspecialchars()`.

### UTF-8 på databasnivån

Om ditt skript använder MySQL finns det en risk att dina strängar inte sparas som UTF-8 i databasen 
även om du följer alla råd ovan.

För att försäkra dig om att dina strängar förblir UTF-8 när de skickas från PHP till MySQL ska du försäkra dig om 
att din databas och dess tabeller alla är konfigurerade att använda teckenkodningen och kollationeringen `utf8mb4`, 
samt att du använder teckenkodningen `utf8mb4` i dina PDO-strängar. Se exemplet nedan. Det här är _av största vikt_.

Notera att du måste använda `utf8mb4`, och inte `utf8`, för fullständigt UTF-8-stöd. Läs vidare för en 
förklaring varför!

### UTF-8 på webbläsarnivån

Använd funktionen  `mb_http_output()` för att försäkra dig om att dina PHP-skript skickar iväg 
UTF-8-strängar till din webbläsare. I dina HTML-koders huvud (`<head>`) lägger du till [`<meta>`-taggen med charset-attributet](http://htmlpurifier.org/docs/enduser-utf8.html).

{% highlight php %}
<?php
// Berätta för PHP att vi använder UTF-8-strängar till skriptets slut
mb_internal_encoding('UTF-8');
 
// Berätta för PHP att vi tänker skicka iväg UTF-8 till webbläsaren
mb_http_output('UTF-8');
 
// Vår teststräng i UTF-8
$string = 'Êl síla erin lû e-govaned vîn.';

// Transformera strängen på något sätt med en av flerbytesfunktionerna
// Observera att vi klipper strängen vid ett tecken som inte är ASCII för demonstrationsändamål
$string = mb_substr($string, 0, 15);
 
// Koppla upp mot en databas för att spara den transformerade strängen
// Se PDO-exemplet i det här dokumentet för mer information
// Observera kommandot `set names utf8mb4`!
$link = new \PDO(   
                    'mysql:host=your-hostname;dbname=your-db;charset=utf8mb4',
                    'your-username',
                    'your-password',
                    array(
                        \PDO::ATTR_ERRMODE => \PDO::ERRMODE_EXCEPTION,
                        \PDO::ATTR_PERSISTENT => false
                    )
                );
 
// Spara den transformerade strängen som UTF-8 i vår databas
// Din databas och dess tabeller använder utf8mb4 som teckenkodning och kollationering, eller hur?
$handle = $link->prepare('insert into ElvishSentences (Id, Body) values (?, ?)');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->bindValue(2, $string);
$handle->execute();
 
// Läs in strängen vi just sparade för att bekräfta att den sparades korrekt
$handle = $link->prepare('select * from ElvishSentences where Id = ?');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->execute();
 
// Spara resultatet i ett objekt som vi skriver ut senare tillsammans med vår HTML
$result = $handle->fetchAll(\PDO::FETCH_OBJ);
?><!doctype html>
<html>
    <head>
        <meta charset="UTF-8" />
        <title>UTF-8 test page</title>
    </head>
    <body>
        <?php
        foreach($result as $row){
            print($row->Body);  // This should correctly output our transformed UTF-8 string to the browser
        }
        ?>
    </body>
</html>
{% endhighlight %}

### Vidare läsning

* [PHP-manualen: Strängoperationer](http://php.net/manual/en/language.operators.string.php)
* [PHP-manualen: Strängfunktioner](http://php.net/manual/en/ref.strings.php)
    * [`strpos()`](http://php.net/manual/en/function.strpos.php)
    * [`strlen()`](http://php.net/manual/en/function.strlen.php)
    * [`substr()`](http://php.net/manual/en/function.substr.php)
* [PHP-manualen: Flerbyte-strängfunktioner](http://php.net/manual/en/ref.mbstring.php)
    * [`mb_strpos()`](http://php.net/manual/en/function.mb-strpos.php)
    * [`mb_strlen()`](http://php.net/manual/en/function.mb-strlen.php)
    * [`mb_substr()`](http://php.net/manual/en/function.mb-substr.php)
    * [`mb_internal_encoding()`](http://php.net/manual/en/function.mb-internal-encoding.php)
    * [`mb_http_output()`](http://php.net/manual/en/function.mb-http-output.php)
    * [`htmlentities()`](http://php.net/manual/en/function.htmlentities.php)
    * [`htmlspecialchars()`](http://www.php.net/manual/en/function.htmlspecialchars.php)
* [PHP UTF-8 Fusklapp](http://blog.loftdigital.com/blog/php-utf-8-cheatsheet)
* [Stack Overflow: Vilka faktorer är det som gör PHP inkompatibelt med Unicode?](http://stackoverflow.com/questions/571694/what-factors-make-php-unicode-incompatible)
* [Stack Overflow: Hur man bäst jobbar med internationella strängar i PHP och MySQL](http://stackoverflow.com/questions/140728/best-practices-in-php-and-mysql-with-international-strings)
* [Hur man använder fullt stöd för UTF-8 i MySQL-databaser](http://mathiasbynens.be/notes/mysql-utf8mb4)
* [Använda Unicode i PHP med portabelt UTF-8](http://www.sitepoint.com/bringing-unicode-to-php-with-portable-utf8/)
