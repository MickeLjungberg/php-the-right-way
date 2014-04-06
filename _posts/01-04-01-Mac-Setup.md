---
isChild: true
anchor: mac_setup
---

## Installera i Mac  {#mac_setup_title}

PHP kommer förpacketerad i OSX, men ligger normalt något efter den senaste 
stabila versionen. Lion kommer med PHP 5.3.6, Mountain Lion använder 5.3.10, 
och Mavericks använder 5.4.17.

För att uppdatera PHP i OSX kan du använda en i mängden av [pakethanterare][mac-package-managers] 
för Mac, med [php-osx från Liip][php-osx-downloads] som den rekommenderade.

Ett annat alternativ är att [kompilera själv][mac-compile], i vilket fall du måste försäkra dig om att du har 
installerat antingen Xcode eller Apples substitut ["Kommandoradsprogram för Xcode"][apple-developer] som kan 
laddas ner från Apples Mac Developer Center.

För ett fullständigt "allt i ett"-paket med PHP, Apache (webbserver) och MySQL 
(databasserver), med ett snyggt grafiskts gränssnitt, testa 
[MAMP][mamp-downloads] eller [XAMPP][xampp].

[mac-package-managers]: http://www.php.net/manual/en/install.macosx.packages.php
[mac-compile]: http://www.php.net/manual/en/install.macosx.compile.php
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
[apple-developer]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/index.html
[php-osx-downloads]: http://php-osx.liip.ch/
[xampp]: http://www.apachefriends.org/en/xampp.html
