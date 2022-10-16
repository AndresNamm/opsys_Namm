# SISSEJUATUS 

Tänase praktikumi teemaks on Pilv, Azure, Azure keskkonnas Windows 11 virtuaalmasina loomine, sellega ühendumine ja sinna peale WSLi (Windows SubSystem for Linux) 
installimine. 
# Sammude kokkuvõte


Sammud 1-4 saate teha ilma oma olemasoleva Windows 11 virtuaalmasinata.

1. Mis on Pilv?.
1. Tehke endale Azure'sse ülikooli kontoga kasutaja.
2. Azure Pilves Virtuaalmasina loomine.
3. Azure Pilves Virtuaalmasina käivitamine.
4. Virtuaalmasinaga ühendamine.
5. WSLi installimine loodud virtuaalmasina peale.
6. Kasutusjuhud WSL-ile.
7. Virtuaalmasina sulgemine.

# Mis on Pilv?

## Pilv Üldiselt 

Googeldage internetis selle kohta, mis on arvutimaailmas laialt tuntuks saanud pilv ja vastake oma praktikumiaruandes järgnevatele küsimustele:

+ $\color{lightblue}{\textrm{Red Nimetaga 3 kõige suuremat pilveteenuste pakkujat}}$
+ $\color{lightblue}{\textrm{Nimetaga 5 eelist, mis on pilveteenustel võrreldes enda teenuste füüsilistel masinatel majutamisega?}}$
+ $\color{lightblue}{\textrm{Kas teate ka mõnda Eesti ettevõtet, kes pakub pilves hostimise teenust?}}$
+ $\color{lightblue}{\textrm{Mis on vahet IAAS ja SAAS ja PAAS tenustel?}}$


## Azure Pilv


Kasutades Googlit vastake nendele küsimustele. **PS, tehke endale vastused korralikult selgeks, sest neid läheb teil ka ülejäänud praktikumi jooksul vaja.**

+ $\color{lightblue}{\textrm{Mis on Azure Resource Group}}$
+ $\color{lightblue}{\textrm{Mis on Azure Subscription}}$
+ $\color{lightblue}{\textrm{Mis on Azure Resource}}$

# Ülikooli kasutajaga konto loomine 

+ [Link konto tegemiseks on siin olemas](https://azure.microsoft.com/en-us/free/students/)
+ Pange tähele, et te ülikooli kasutajaga peate te ainult kinnitama ära, et olete ülikooli tudeng. 
+ [Juhised inglise keeles konto tegemiseks](https://dev.to/esdanielgomez/creating-azure-for-students-account-48g)

## Sammud üldiselt

1. Vajutage "Start free"
2. Logige sisse oma olemasoleva Microsoti kontoga. Ei pea ilmtingimata oleme teie ülikooli konto. 
3. Kinnitaga oma isik telefoninumbriga 
4. Kinnitage oma õpilase staatus enda ülikooli kontoga. Teie ülikooli konto on <ut_kasutajanimi>@ut.ee.
5. Pärast enda õpilase staatuse kinnitamist juhatatakse teid edasi teie [Azure keskvaatesse](http://portal.azure.com/) (inglise k. "Azure Console","Azure Graphical User Interface")
6. Palju õnne! Nüüdseks on teil olemas oma Azure konto koos aastase 100 $ krediidiga. Lisaks saate kasutada ka mitmeid erinevaid teenuseid tasuta. [Lugege lähemalt siit](http://portal.azure.com/)

# Azure Pilves Virtuaalmasina loomine 


1. Minge aadressile https://portal.azure.com/ 
2. Avanenud vaates otsige üles sinine "Pluss" ikoon kirjaga "Create a resource" ja vajutage sellele
3. Avanenud vaates otsige üles kirje "Virtual machine" ja vajutage sellele 
![image](https://user-images.githubusercontent.com/21141607/196036889-eec37a7b-0751-4eaf-9288-dd10298287a0.png)
4. Avaneb virtuaalmasina loomise vaade. Seda täidame nüüd järgmises peatükise



## VIRTUAALMASINA LOOMINE 

Virtuaalmasina loomiseks täitke ära avanenud vaade nii nagu pildil näidatud. **Asendage nimi "namm" enda perekonnanimega.** $\color{lightblue}{\textrm{Enda perekonnanimega VM on oluline prakikumi lõpus enda VMi descriptionist screenshoti esitamisel}}$
**Väga oluline on, et jätata ka oma lisatud parooli ja kasutajanime meelde. Teil läheb seda vaja VMi sisselogimisel**

![image](https://user-images.githubusercontent.com/21141607/196038492-502d97d8-3500-41d8-b334-6f9efb40c54c.png)
![image](https://user-images.githubusercontent.com/21141607/196038509-00914b16-91fd-4f04-bfe4-dd2c428d2be3.png)

Edasi vajutaga nupule: "Next: Disks"


+ Valige OS diskiks "Standard HDD (locally-redundant storage)"
+ Tehke linnuke väljale "Delete with VM"

Edasi vajutaga nupule: "Next: Networking"

+ Kui seda juba tehtud pole, siis tehke linnuke väljale "Delete public IP and NIC when VM is deleted"

Edasi vajutage nupule "Review + create". Edasi peaks teile tekkima akna üles roheline tekst "Validation passed". Kui nii on, siis vajutage sinisele nupule "Create". 


+ Virtuaalmasina loomine võtab aega kuskil 5-15 minutit. Võite nii kaua lugeda WSLi kohta https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux

# Virtuaalmasina käivitamine Azure pilves

+ Minge lingile https://portal.azure.com/#home


@Alo Peets ja @Erkki Männiste kumb variant



$\color{red}{\textrm{Raskem variant}}$

+ Otsige nüüd oma loodud virtuaalmasin üles.

$\color{red}{\textrm{Lihtne variant}}$

+ Vajutage nupule "Resource Groups"
+ Avanenud vaates vajutage resource grupile nimega &lt;perekonnaimini>-rg
+ Vajutage oma vm-i peale
  


$\color{lightblue}{\textrm{Otsige nüüd oma VMi üldvaade ülest ja tehke sellest Screenshot nagu alloval pildil näidatud}}$

![image](https://user-images.githubusercontent.com/21141607/196039626-da416317-6c88-48b5-b709-8e76ae112338.png)


Veenduga, et teie loodud virtuaalmasin oleks käivitatud. Kui pole, siis käivitage see. 


# VIRTUAALMASINAGE ÜHENDUMINE

+ Kui virtuaalmasin on käivitatud, siis virtuaalmasina infovaates vajutage nupule "Connect" ja avanenud menüüst valige RDP.
+ Avaneb uus aken. Vajutage seal nupule "Download RDP File". Teile laetakse alla fail gt;perenimi>-vm.rdp. 
+ 
+ Klõpsake failile gt;perenimi>-vm.rdp. Aknas peaks avanema autentimisvaade. Klõpsake seal valikul "Use a different account" ja sisestaga oma varemloodud kasutajanimi ja parool. 
+ Voila, olete ühendanud oma pilves asuvasse virtuaalmasinasse. 
+ 




