---
isChild: true
anchor: vagrant
---

## Vagrant {#vagrant_title}

Att köra dina applikationer i olika miljöer mellan utveckling och produktion kan leda till underliga 
buggar när du lägger upp applikationen för allmänheten. Det är också trixigt att hålla olika 
utvecklingsmiljöer uppdaterade med samma versioner av bibliotek som används i grupper av 
utvecklare.

Om du jobbar i Windows och lägger upp resultatet på en Linuxmaskin (eller en icke-Windows-maskin), eller om du 
jobbar i en grupp, bör du fundera över att använda en virtuell maskin. Det låter trixigt, men med hjälp av 
[Vagrant][vagrant] kan du få igång en virtuell basmaskin med bara några få enkla steg. Du kan sen konfigurera 
dessa basmaskiner manuellt, eller använda "provisioning"-mjukvara som [Puppet][puppet] eller [Chef][chef] för att 
göra detta åt dig. Att använda sådan mjukvara skapar en trygghet att flera maskiner är konfigurerade på ett 
identiskt sätt och eliminerar behovet för komplicerade "manuellt konfigurerade" kommandolistor. Du kan också 
"förstöra" din basmaskin och återskapa den med ett fåtal manuella steg, vilket gör det enkelt att skapa en 
"fräsch" installation.

Vagrant skapar delade mappar som används för att dela koder mellan värdmaskinen och din virtuella maskin, 
vilket innebär att du kan skapa och redigera filer i din värdmaskin och sedan köra filerna i den 
virtuella maskinen.

### Lite hjälp

Om du behöver lite hjälp när du först börjar använda Vagrant finns det tre 
tjänster som kan vara användbara:

- [Rove][rove]: en tjänst som låter dig att på förhand generera vanliga Vagrantbyggen, med PHP bland alternativen. Konfigureringen utförs av Chef.
- [Puphpet][puphpet]: enkelt grafiskt gränssnitt för att skapa virtuella maskiner för PHP-utveckling. **Kraftigt fokuserad på PHP**. Förutom 
  lokala virtuella maskiner, kan tjänsten också användas för att lägga upp till molntjänster. Konfigurationen utförs av Puppet.
- [Protobox][protobox]: är ett lager ovanpå vagrant och ett webbaserat grafiskt gränssnitt för att skapa virtuella maskiner för webbutveckling. Ett enda YAML-dokument kontrollerar allting som installeras i maskinen.

[vagrant]: http://vagrantup.com/
[puppet]: http://www.puppetlabs.com/
[chef]: http://www.opscode.com/
[rove]: http://rove.io/
[puphpet]: https://puphpet.com/
[protobox]: http://getprotobox.com/
