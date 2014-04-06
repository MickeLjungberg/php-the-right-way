---
isChild: true
anchor: command_line_interface
---

## Kommandoradsgränsnitt {#command_line_interface_title}

PHP skapades ursprungligen för att bygga webbapplikationer, men det är också användbart för att skriva program för kommandoraden (CLI). 
Kommandoradsprogram skrivna i PHP kan hjälpa dig att automatisera vanliga uppgifter som testning, publicering och administration av applikationer.

Kommandoradsprogram i PHP är kraftfulla eftersom du kan använda dina applikationskoder direkt utan att behöva skapa och säkra ett webbgränssnitt. 
Försäkra dig bara om att du inte sparar dina PHP-koder för kommandoradsprogrammen i webrootskatalogen!

Försök att köra PHP från kommandoprompten:

{% highlight bash %}
> php -i
{% endhighlight %}

Alternativet `-i` skriver ut din PHP-konfiguration precis som [`phpinfo`][phpinfo]-funktionen.

Alternativet `-a` skapar ett interaktivt skal, liknande Rubys IRB eller pythons interaktiva skal. 
Det finns ett flertal andra användbara [alternativ för kommandoraden][cli-options] också.

Låt oss skriva ett enkelt "Hallå, $name"-program för kommandoraden. Skapa en fil vid namn `hello.php`, med följande innehåll:

{% highlight php %}
<?php
if ($argc != 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hallå, $name\n";
{% endhighlight %}

PHP skapar två speciella variabler som innehåller argumenten ditt skript anropas med. [`$argc`][argc] 
är en heltalsvariabel som innehåller argumentet *count* och [`$argv`][argv] är en vektorvariabel som 
innehåller alla argumentens *värden*. Det första argumentet är alltid namnet på PHP-skriptet, som i 
det här fallet är `hello.php`.

Uttrycket `exit()` anropas med talet noll för att indikera för skalet att kommandot misslyckades. Vanliga avslutningskoder 
hittar du [här][exit-codes]

Skriv in följande i kommandoraden för att köra vårat skript:

{% highlight bash %}
> php hello.php
Usage: php hello.php [name]
> php hello.php världen
Hallå, världen
{% endhighlight %}


 * [Lär dig om hur du kör PHP från kommandoraden][php-cli]
 * [Lär dig konfigurera Windows så att du kan köra PHP från kommandoraden][php-cli-windows]

[phpinfo]: http://php.net/manual/en/function.phpinfo.php
[cli-options]: http://www.php.net/manual/en/features.commandline.options.php
[argc]: http://php.net/manual/en/reserved.variables.argc.php
[argv]: http://php.net/manual/en/reserved.variables.argv.php
[php-cli]: http://php.net/manual/en/features.commandline.php
[php-cli-windows]: http://www.php.net/manual/en/install.windows.commandline.php
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&topic=sysexits
