---
isChild: true
anchor: namespaces
---

## Namnutrymmen {#namespaces_title}

PHP-gemenskapen har som sagt många utvecklare som skriver mängder av koder. Det innebär att en klass 
i ett bibliotek kan använda samma namn som en klass i ett annat bibliotek. När båda biblioteken används 
i samma namnutrymme får man en namnkollision, vilket orsakar uppenbara problem.

_Namnutrymmen_ löser detta problem. Som det står PHP:s referensmanual kan namnutrymmen liknas vid 
kataloger i operativsystem som skapar olika _namnutrymmen_ för olika filer; två filer med samma namn 
kan samexistera om de sparas i två olika kataloger. På samma sätt kan två klasser med samma namn samexistera 
om de är tilldelade olika namnutrymmen. Det är så enkelt.

Det är viktigt att du använder namnutrymmen i dina koder så att de kan användas av andra utvecklare utan 
risk för namnkollisioner mellan bibliotek.

En rekommenderad användning av namnutrymmen ges i [PSR-0][psr0], vilken ämnar definiera en standardkonvention 
för filer, klasser och namnutrymmen som möjliggör att koderna används som plug-and-play.

I December 2013 skapade PHP-FIG en ny autoladdningsstandard: [PSR-4][psr4], som en dag 
förmodligen kommer att ersätta PSR-0. För tillfället är båda fortfarande godkända, eftersom PSR-4 
kräver PHP 5.3, och många PHP 5.2-projekt för närvarande använder sig av PSR-0. Om du tänker använda 
dig av en autoladdningsstandard i ett nytt projekt så vill du nog helt säkert använda dig av PSR-4.

* [Läs om namnutrymmen][namespaces]
* [Läs om PSR-0][psr0]
* [Läs om PSR-4][psr4]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md