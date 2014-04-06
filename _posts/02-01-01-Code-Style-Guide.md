---
anchor: code_style_guide
---

# Kodstilmall  {#code_style_guide_title}

PHP-gemenskapen är stor och varierad, med oräkneligt antal bibliotek, ramverk och komponenter. Det är vanligt bland 
PHP-utvecklare att välja och vraka mellan dessa och kombinera dem i egna projekt. Det är därför viktigt att PHP-koder 
följer (så troget som möjligt) vanliga kodstilar för att underlätta för utvecklare när de mixar och parar ihop bibliotek 
i sina egna projekt.

[Framework Interop Group][fig] har föreslagit och godkänt en serie rekommendationer. Inte alla relaterar till 
kodstilar, men följande rekommendationer gör det: [PSR-0][psr0], [PSR-1][psr1], [PSR-2][psr2] och [PSR-4][psr4]. 
Dessa rekommendationer är bara en uppsättning regler som projekt som Drupal, Zend, Symfony, CakePHP, phpBB, AWS 
SDK, FuelPHP, Lithium, o.s.v. har börjar använda sig av. Du kan använda dem i dina egna projekt, eller fortsätta 
använda din egen personliga stil.

Idealet är att du skriver PHP-koder som följer en känd standard. Det kan vara en kombination av PSR, eller en 
av kodstandarderna för PEAR eller Zend. Om du gör det så kan andra utvecklare enkelt läsa och arbeta med dina 
koder, och applikationer som implementerar komponenter förblir konsekventa även när de använder många tredjepartskoder.

* [Läs om PSR-0][psr0]
* [Läs om PSR-1][psr1]
* [Läs om PSR-2][psr2]
* [Läs om PSR-4][psr4]
* [Läs om kodstandarderna i PEAR][pear-cs]
* [Läs om kodstandarderna i Zend][zend-cs]
* [Läs om kodstandarderna i Symfony][symfony-cs]

Du kan använda [PHP_CodeSniffer][phpcs] för att validera koder gentemot vilken 
som helst av dessa rekommendationer, och det finns tillägg till textverktyg som 
[Sublime Text 2][st-cs] som ger respons i realtid.

Använd Fabien Potenciers [PHP Coding Standards Fixer][phpcsfixer] för att automatiskt
ändra din kodsyntax så att den följer dessa standarder, så behöver du inte fixa varenda
problem på egen hand.

Engelska är föredraget för alla symbolnamn och kodstrukturer. Kommentarer kan skrivas i vilket språk som nu är 
lättläst för alla nuvarande och framtida parter som kan tänkas arbeta med koderna.

[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[zend-cs]: http://framework.zend.com/wiki/display/ZFDEV2/Coding+Standards
[symfony-cs]: http://symfony.com/doc/current/contributing/code/standards.html
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
