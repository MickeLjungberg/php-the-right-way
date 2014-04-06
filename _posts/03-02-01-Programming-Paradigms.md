---
isChild: true
anchor: programming_paradigms
---

## Programmeringsparadigmer {#programming_paradigms_title}

PHP är ett flexibelt, dynamiskt språk som stödjer en mängd olika programmeringstekniker. Det har utvecklats dramatiskt 
genom åren, genom att bland annat lägga till en solid objektorienterad modell i PHP 5.0 (2004), anonyma funktioner och 
namnutrymmen i PHP 5.3 (2009), och drag i PHP 5.4 (2012).

### Objektorienterad programmering

I PHP finns en väldigt komplett uppsättning objektorienterade funktioner vilka inkluderar stöd för klasser, 
abstrakta klasser, gränssnitt, arv, konstruktorer, kloner, undantag, och mer.

* [Läs om objektorienterad PHP][oop]
* [Läs om drag][traits]

### Funktionell programmering

PHP har stöd för förstklassiga funktioner, vilket innebär att en funktion kan tilldelas en variabel. Såväl användardefinierade som 
inbyggda funktioner kan refereras av en variabel och köras dynamiskt. Funktioner kan skickas som argument till andra 
funktioner (överordnade funktioner) och funktioner kan returnera andra funktioner.

Det är möjligt att använda rekursion i PHP, vilket gör det möjligt för en funktion att anropa sig själv, men oftast 
fokuserar PHP-koder på iteration.

Nya anonyma funktioner (med stöd för inslutning) finns tillgängliga sen PHP 5.3 (2009).

PHP 5.4 lade till möjligheten att binda inslutningar till ett objekts omfång och förbättrade även stödet för 
anropare så att de kan användas växelvis med anonyma funktioner i alla situationer.

* Fortsätt läsa om [funktionell programmering i PHP](/pages/Functional-Programming.html)
* [Läs om anonyma funktioner][anonymous-functions]
* [Läs om inslutningsklassen][closure-class]
* [Mer detaljer i inslutnings-RFC:n][closures-rfc]
* [Läs om anropare][callables]
* [Läs om hur man kan anropa funktioner dynamiskt med `call_user_func_array`][call-user-func-array]

### Metaprogrammering

PHP har stöd för olika former av metaprogrammering genom mekanismer som reflektions-API:t och magiska metoder. Det finns 
många magiska metoder tillgängliga som `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()`, o.s.v. som låter 
utvecklare koppla in sig i klassbeteenden. Rubyutvecklare påstår ofta att PHP saknar `method_missing`, men den finns 
tillgänglig som `__call()` och `__callStatic()`.

* [Läs om magiska metoder][magic-methods]
* [Läs om reflektion][reflection]

[namespaces]: http://php.net/manual/en/language.namespaces.php
[overloading]: http://php.net/manual/en/language.oop5.overloading.php
[oop]: http://www.php.net/manual/en/language.oop5.php
[anonymous-functions]: http://www.php.net/manual/en/functions.anonymous.php
[closure-class]: http://php.net/manual/en/class.closure.php
[callables]: http://php.net/manual/en/language.types.callable.php
[magic-methods]: http://php.net/manual/en/language.oop5.magic.php
[reflection]: http://www.php.net/manual/en/intro.reflection.php
[traits]: http://www.php.net/traits
[call-user-func-array]: http://php.net/manual/en/function.call-user-func-array.php
[closures-rfc]: https://wiki.php.net/rfc/closures
