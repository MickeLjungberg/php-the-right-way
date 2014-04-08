---
isChild: true
anchor: basic_concept
---

## Grundläggande koncept {#basic_concept_title}

Vi kan demonstrera konceptet med ett enkelt exempel.

Här har vi klassen `Database` som kräver en adapter för att kommunicera med databasen. Vi kan skapa 
adaptern inuti konstruktorn och därmed hårdkoda behovet. Med det gör det svårt att tests och betyder 
dessutom att klassen `Database` är hårt kopplat till adaptern ifråga.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct()
    {
        $this->adapter = new MySqlAdapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

Den här koden kan skrivas om så att den använder behovsinjektion och därmed slipper vi dessa problem.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(MySqlAdapter $adapter)
    {
        $this->adapter = $adapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

Nu tilldelar vi klassen `Database` dess behov istället för att den själv skapar det direkt. Vi skulle också kunna skapa en metod
som tar emot behovskopplingen som ett argument och lösa det på så sätt, eller om egenskapen `$adapter` var deklarerad som `public` 
skulle vi kunna sätta den direkt.
