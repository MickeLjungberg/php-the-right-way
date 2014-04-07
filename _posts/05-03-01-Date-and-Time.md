---
isChild: true
anchor: date_and_time
---

## Datum och tid{#date_and_time_title}

I PHP finns klassen DateTime som hjälper dig när du ska läsa, skriva, jämföra eller 
utföra beräkningar med datum och tider. Det finns många datum och tidsrelaterade funktioner 
i PHP förutom DateTime, men den här klassen ger dig ett trevligt objektorienterat gränssnitt
för de vanligaste uppgifterna. Den kan hantera tidszoner, men det är bortom den här korta 
introduktionen att ta upp.

För att skapa ett DateTime-objekt kan du skicka datum och tid i råa strängformat till 
fabriksmetoden `createFromFormat()` eller anropa `new \DateTime` för att få det aktuella 
datumet och tiden. Använd metoden `format()` för att konvertera DateTime-objektet till 
en utdatasträng.

{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = \DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start date: ' . $start->format('m/d/Y') . "\n";
{% endhighlight %}

Att utföra beräkningar med DateTime är möjligt med hjälp av klassen DateInterval.
DateTime har metoder som `add()` och `sub()` som tar ett DateInterval-objekt som 
argument. Skriv inte kod som förlitar sig på samma antal sekunder per dag, eftersom 
både sommartid och tidzonändringar kommer att bryta såna koder. Använd istället 
datumintervaller. För att beräkna skillnader använder du metoden `diff()`. Den 
returnerar ett nytt DateInterval-objekt, som är superenkelt att visa.

{% highlight php %}
<?php
// create a copy of $start and add one month and 6 days
$end = clone $start;
$end->add(new \DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Difference: ' . $diff->format('%m month, %d days (total: %a days)') . "\n";
// Difference: 1 month, 6 days (total: 37 days)
{% endhighlight %}

On DateTime objects you can use standard comparison:
{% highlight php %}
<?php
if ($start < $end) {
    echo "Start is before end!\n";
}
{% endhighlight %}

Här är ett sista exempel för att demonstrera DatePeriod-klassen. Den används för att vandra genom 
återkommande händelser. Den kan ta två DateTime-objekt, start och slut (end), och returnerar 
alla händelser i det intervallet.

{% highlight php %}
<?php
// output all thursdays between $start and $end
$periodInterval = \DateInterval::createFromDateString('first thursday');
$periodIterator = new \DatePeriod($start, $periodInterval, $end, \DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // output each date in the period
    echo $date->format('m/d/Y') . ' ';
}
{% endhighlight %}

* [Läs om DateTime][datetime]
* [Läs om datumformatering][dateformat] (giltiga strängformat för datum)

[datetime]: http://www.php.net/manual/book.datetime.php
[dateformat]: http://www.php.net/manual/function.date.php
