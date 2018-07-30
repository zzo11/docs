# NEO Smart Contract Introductie

## Wat is een Smart Contract?

Een smart contract is een reeks afspraken die zijn vastgelegd in digitale vorm, inclusief de overeenkomst hoe de deelnemers aan dit contract deze afspraken zullen vervullen. Blockchaintechnologie dient hierbij als een gedecentraliseerd, betrouwbaar en niet-bemoeiend systeem; eigenschappen die essentieel zijn voor smart contracts. Het feit dat smart contracts zo goed passen bij blockchaintechnologie is een van de belangrijkste eigenschappen van een blockchain, en de reden dat blockchains als revolutionair worden gezien. Het gebruik van smart contracts vergroot de efficiëntie van de maatschappij.

## Wat zijn de kenmerken van NEO Smart Contracts?

Een NEO Smart Contract 2.0 omvat de volgende kenmerken: zekerheid, hooggraads functioneren en uitbreidingsmogelijkheden. De contracttypen die hieronder vallen zijn onder andere: validatiecontracten, functiecontracten en applicatiecontracten.

NEO gebruikt het lichtgewicht NeoVM (NEO Virtual Machine) als smart contract uitvoerplatform, bedoeld om de prestaties van smart contracts te optimaliseren. Het start snel op en verbruikt slechts een kleine hoeveelheid middelen om smart contracts uit te voeren. Het statisch compilen en cachen van hotspot-contracten kan significant verbeterd worden door JIT(live)-compilertechnologie. Bij het opzetten van de NeoVM wordt een reeks cryptografische instructies gegeven om de uitvoering van cryptografische algoritmes in smart contracts zo efficiënt mogelijk te laten verlopen. Hiernaast maken instructies voor datamanipulatie het mogelijk om direct arrays en complexe datastructuren te ondersteunen. Alle bovenstaande kenmerken zorgen ervoor dat het presteren van NEO Smart Contract 2.0 optimaal is.

NEO Smart Contract 2.0 maakt het mogelijk om projecten uitbreidingsmogelijkheden te geven door middel van hoge concurrency en dynamische partitionering, gecombineerd met een laag-coupling ontwerp. De laag-coupling contractprocedure wordt uitgevoerd in een virtuele machine (NeoVM) en communiceert met de buitenwereld d.m.v. een interactieve serverlaag. Hierdoor kunnen de meeste verbeteringen en aanvullingen van smart contract functies behaald worden door simpele API's van de interactieve serverlaag.

## Schrijf Smart Contracts in elke programmeertaal

Vergeleken met Ethereum is het programmeren van NEO Smart Contract 2.0 intuïtiever: in tegenstelling tot de originele Solidity programmeertaal in Ethereum kan een NEO smart contract worden geschreven in bijna elke geavanceerde programmeertaal. De eerste talen die worden ondersteund ​​zijn C#, VB.Net, F#, Java en Kotlin. NEO biedt compilers en plug-ins voor deze talen, welke de geavanceerde programmeertalen omzetten in instructies die compatibel zijn met NeoVM. De eerste compiler zal voor MSIL (Microsoft intermediate language) zijn, zodat vrijwel elk type .Net-taal gelijk ondersteund zal zijn, evenals elke taal die direct kan worden vertaald naar MSIL.

De talen die op dit moment worden ondersteund, zijn:

1) C#, VB.Net, F#
2) Java, Kotlin

De talen die op de planning staan om ondersteuning te krijgen, zijn:

1) C, C++, Golang
2) Python, JavaScript

Met ondersteuning voor meerdere programmeertalen kan meer dan 90% van de ontwikkelaars direct deelnemen aan het ontwikkelen van een NEO smart contract, zonder dat hiervoor een nieuwe programmeertaal geleerd hoeft te worden. Het kan zelfs mogelijk zijn al in werking zijnde code van bedrijven direct in te voeren in de blockchian. Door deze functionaliteit denken wij dat de populariteit van NEO sterk zal toenemen.

Hiernaast kan het lastig zijn om smart contracts te debuggen en testen bij gebrek aan hulpmiddelen of duidelijke instructies. Bij NEO wordt echter significante hulp geboden voor debuggen in de NeoVM, waardoor het ontwikkelen van NEO Smart Contract 2.0 makkelijker en sneller verloopt. Voor TestNet GAS kunt u contact opnemen met mede-ontwikkelaars; dit wordt graag afgestaan om te helpen bij de ontwikkeling.

## Smart contract triggers

Er zijn twee manieren om smart contracts te triggeren:

1. Contract User Authentication: hierbij is het smart contract een contract-account. Wanneer de gebruiker aanvraagt om de contract-account te gebruiken bij een asset, dan wordt het smart-contract getriggerd.
2. Stuur handmatig een transaction call Smart contract: hierbij stuurt de gebruiker een transactie (*Invocation Transaction*) om de implementatie van een smart contract te triggeren.

## NeoVM

**NeoVM** is de virtual machine die de NEO smart contract-code uitvoert. Dit is niet een volledige VM zoals Vmware of Hypter-V, maar een die puur op smart contracts is gericht.

Bijvoorbeeld: in de Java JVM of .NET CLR wordt de broncode gecompileerd tot de bijbehorende bytecode, en vervolgens uitgevoerd op de juiste virtual machine. JVM of CLR voert de bytecode uit, wat lijkt op het uitvoeren van instructies op een fysieke machine (de bijbehorende binaire instructies worden uiteraard nog steeds uitgevoerd op een fysieke machine). De fysieke machine haalt informatie uit de opslag, verplaatst het naar de CPU via de geheugenbus, waarna de data gedecodeerd en uitgevoerd wordt en het resultaat wordt opgeslagen.

### Virtual machine Opbouw

   ![](C:/neo-project/docfx/docs/nl-nl/sc/assets/neo-vm.jpg)

Het bovenstaande diagram is de systeemarchitectuur van de Neo Virtual Machine (NeoVM), waarbij het middelste omlijnde gebied de kern van de virtual machine is.

#### Execution engine

Het groene gebied aan de linkerkant is de virtual machine execution engine (de 'CPU' van het systeem). Deze voert veelvoorkomende instructies uit zoals flow control, stack operations, bit operations, arithmetische operations, logical operations, cryptographische methodes et cetera. Deze vereist een service layer waarmee interactie kan worden aangegaan (zie hieronder).

#### Evaluation Stack

Het middelste, grijze gedeelte is de virtual machine computing stack (het 'geheugen' van het systeem). Dit kan op basis van de stack of op basis van het register; beide manieren hebben voor- en nadelen. Op de stack-gebaseerde virtual machines kunnen werken met JVM, Python en .NET CLR. Op het register-gebaseerde VM's bestaan ook, zoals Dalvik en Lua5.0. Op de stack-gebaseerde VM's maken het mogelijk om direct aanpassingen te maken in de blockchain tijdens het uitvoeren van opdrachten.

Aangezien de standaard methode is om data vanuit de operand stack uit te voeren, is het niet nodig om een operand te definiëren. Bijvoorbeeld: Normaal gesproken moet je bij x86 assembly "ADD EAX, EBX" aangeven ....... Bij op de stack-gebaseerde VM-instructies is het echter niet nodig deze parameters te specificeren. 

<!--NL: vertaald a.d.h.v. onderstaande stuk, erg gebroken Engels. Kan iemand anders hier wijs uit worden?
    EN: translated from the bit below; it's unclear to me what exactly is meant with this, can someone take a look at this?
The middle part of the gray is the virtual machine computing stack (equivalent to memory), and now the virtual machine to achieve two ways, based on the stack and based on the register, the two ways to achieve their own advantages and disadvantages, but also have the iconic product. Stack-based virtual machines with JVM, CPython, and .Net CLR. Register-based VMs also exist such as Dalvik and Lua5.0. Stack-based virtual machines have a stack stack concept that allows virtual machines to interact directly with the stack when performing real operations.
-
Since the default is to fetch data from the operand stack, there is no need to specify an operand. For example, x86 assembly "ADD EAX, EBX", you need to specify where the operation from the need to take the operation, where the results stored in the implementation. But stack-based virtual machine instructions do not need to specify these parameters. For example, to add a simple operation the default operands are stored in the operand stack, and we can pop out two data directly from the stack to do addition.
-->

#### Interoperable service layer

Het blauwe gedeelte aan de rechterzijde is de interoperable service layer van de VM (de 'randapparatuur' van de VM). Momenteel geeft de interoperable service layer (ISL) enkele API's om de blockchaindata van een smart contract te beheren, welke blockchain-informatie, transactie-informatie, contractinformatie, asset-informatie et cetera kan beheren.

Daarnaast maakt de ISL ook langdurige opslag voor elk contract mogelijk. Elk smart contract kan optioneel worden opgeslagen op eigen opslag door een key en waarde op te slaan. 

<!--NL: ook dit stuk is vaag.
    EN: this part is unclear as well
In addition, the interoperable service layer also provides a persistent storage area for each contract. Each of the smart contracts is optionally created with private storage, which is in the form of a key-value object determined by the callee of the contract, rather than the context of the persistent store. Of course, the caller needs to pass their own storage context to the callee (that is, to complete the authorization), the caller can perform read and write operations.
-->

### Servicekosten

Om een smart contract op de blockchain te plaatsen, moeten er deployment-kosten worden betaald (momenteel 500 GAS). Bij het uitvoeren van de smart contract moet de gebruiker eventueel servicekosten betalen (momenteel gratis).

## Een eenvoudige smart contract

Hieronder volgt de eenvoudige code van het smart contract voor VerificationCode:

```c#
public static bool Verify ()
{
    return true;
}
```

Hier is het resultaat altijd `true`, wat betekent dat iedereen het contract-adres van de assets kan uitgeven (vergelijkbaar met het uitgeven van geld).

<!--NL: idem dito
    EN: this part as well
There is a function of deleting an asset in the client's e-wallet client. When you delete an asset, the asset is sent to a specified address, which is the contract address generated by the above smart contract, and anyone can spend the address In the assets, of course, the address of the assets are other people do not want the assets.
-->

```c#
public static bool Verify ()
{
    return false
}
```

Hier is het resultaat altijd `false`, wat betekent dat de assets van dit contract niet gebruikt kunnen worden, bijvoorbeeld wanneer een hoeveelheid van een asset is vernietigd door een bedrijf.

<!--same
The return value of the contract is always false, indicating that the assets of this contract can not be used (can be understood as burn or destroy an asset), such as which can store some of the shares of the company has been canceled.
-->

Bekijk voor meer voorbeelden:

[Hello World](tutorial/HelloWorld.md)

[Lock (lock)](tutorial/lock.md)

[Domain (Domain Name System)](tutorial/Domain.md)