---
isChild: true
anchor: windows_setup
---

## Installera i Windows {#windows_setup_title}

PHP för Windows finns tillgängligt på flera olika sätt. Du kan 
[ladda ner binärfilerna][php-downloads] och tills nyligen kunde du även använda 
en '.msi'-installationsfil. Installationsfilen stöds inte längre och upphörde 
med PHP 5.3.0.

För inlärning och lokal utveckling kan du använda den inbyggda webbservern som 
följer med PHP 5.4+, så du behöver inte oroa dig över konfigureringsalternativ.
Om du ändå vill ha en "allt i ett"-lösning (med en fullskalig webbserver och 
MySQL) så är verktyg som [Web Platform Installer][wpi], 
[Zend Server CE][zsce], [XAMPP][xampp] and [WAMP][wamp] användbara för att 
sätta upp en utvecklingsmiljö snabbt och effektivt. Med det sagt är det bra om 
du är medveten om att dessa miljöer kommer vara lite annorlunda från den 
webbserver du slutligen ska lägga upp dina koder på.

Om du vill lägga upp dina koder till en Windowsserver är IIS7 den mest stabila, 
och den med bäst prestanda. Du kan använda [phpmanager][phpmanager] (en plugin 
för IIS7 med grafiskt gränssnitt) för att underlätta konfiguration och hantering 
av PHP. IIS7 kommer med FastCGI inbyggt och redo att användas, du behöver bara 
konfigurera PHP som en hanterare. För hjälp och ytterligare resurser finns det 
en [del av iis.net dedikerad][php-iis] till PHP.

[php-downloads]: http://windows.php.net
[phpmanager]: http://phpmanager.codeplex.com/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[zsce]: http://www.zend.com/en/products/server-ce/
[xampp]: http://www.apachefriends.org/en/xampp.html
[wamp]: http://www.wampserver.com/
[php-iis]: http://php.iis.net/
