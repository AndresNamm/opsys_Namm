# SISSEJUHATUS 

Tänase praktikumi teemaks on Pilv, Azure, Azure keskkonnas Windows 11 virtuaalmasina loomine, sellega ühendumine ja sinna peale WSLi (Windows SubSystem for Linux) 
installimine. 

**Väga oluline on, et te lülitate oma pilves asuva virtuaalmasina välja iga kord pärast selle kasutamist. Vastasel juhul lõppeb teil endal tasuta kasutatav ressurss otsa ning ei ole võimalik praktikumi lõpuni teha**

# Sammude kokkuvõte


Sammud 1-4 saate teha ilma oma olemasoleva Windows 11 virtuaalmasinata.

1. Mis on Pilv?.
1. Tehke endale Azure'sse ülikooli kontoga kasutaja.
2. Azure Pilves Virtuaalmasina loomine.
3. Azure Pilves Virtuaalmasina seadistamine
4. Virtuaalmasinaga ühendamine.
5. WSLi installimine loodud virtuaalmasina peale.
6. WSLi katsetamine
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

+ Oluline oleks järgmisel sammul mitte praktikumi katkestada, sest vastasel juhul loob Azure VMi valmis ja paneb selle ka käima, mis põhjustab lisakulu. 
+ Virtuaalmasina loomine võtab aega kuskil 5-15 minutit. Võite nii kaua lugeda WSLi kohta https://en.wikipedia.org/wiki/Windows_Subsystem_for_Linux

# Virtuaalmasina käivitamine Azure pilves

+ Minge lingile https://portal.azure.com/#home

+ Vajutage nupule "Resource Groups"
+ Avanenud vaates vajutage resource grupile nimega &lt;perekonnaimini>-rg
+ Vajutage oma vm-i peale
  
  

$\color{lightblue}{\textrm{Otsige nüüd oma VMi üldvaade ülest ja tehke sellest Screenshot nagu alloval pildil näidatud}}$

![image](https://user-images.githubusercontent.com/21141607/196039626-da416317-6c88-48b5-b709-8e76ae112338.png)


+ Edasi otsige virtuaalmasina menüüst vasakult käelt üles "Auto-Shutdown" ja seadistage see "Enabled" olekusse. **Veenduga, et antud valik ka salvestuks**
![image](https://user-images.githubusercontent.com/21141607/196044658-ebc3bef9-66a3-450a-8981-469a6c36bdb4.png)

$\color{lightblue}{\textrm{Tehke salvestatud valikust ka Screenshot}}$



Veenduge, et teie loodud virtuaalmasin oleks käivitatud. Kui pole, siis käivitage see. 



# VIRTUAALMASINAGA ÜHENDUMINE

+ Kui virtuaalmasin on käivitatud, siis virtuaalmasina infovaates vajutage nupule "Connect" ja avanenud menüüst valige RDP.
+ Avaneb uus aken. Vajutage seal nupule "Download RDP File". Teile laetakse alla fail gt;perenimi>-vm.rdp. 
+ Nüüd on teil mitu võimalust ühenduda Remote Connectioniga pilves olevasse virtuaalmasinasse
+ Kui kasutate Windows 10, Windows 11 arvutit või Windows 11 lokaalselt virtuaalmasinta
   + Klõpsake alla laetud failile gt;perenimi>-vm.rdp. Aknas peaks avanema autentimisvaade. Klõpsake seal valikul "Use a different account" ja sisestaga oma varemloodud kasutajanimi ja parool. 
+ Kui kasutate mõnda muud operatsioonisüsteemi https://learn.microsoft.com/en-us/windows-server/remote/remote-desktop-services/clients/remote-desktop-clients
+ Voila, olete ühendanud oma pilves asuvasse virtuaalmasinasse. 
+ $\color{lightblue}{\textrm{Tehke enda arvutis System About vaatest Screenshot}}$

# WSLI INSTALLIMINE LOODUD VIRTUAALMASINA PEALE 

+ Installige antud juhendi järgi enda Virtuaalmasina peale [WSL](https://learn.microsoft.com/en-us/windows/wsl/install)
  + By default installitakse teile WSL koos Ubuntuga
+ Taaskäivitage arvuti 

# WSLI KATSETAMINE 

+ Pärast taaskäivitamist tuleb teil sisestada enda kasutajanimi. Pange selleks enda perekonnanimi
+ Käivitage WSL ja proovige teminalis sisestada mõned Linuxi käsud 

~~~sh
ls -la
pwd
uname -a
~~~
+ $\color{lightblue}{\textrm{Tehke tulemusest Screenshot}}$
+ $\color{lightblue}{\textrm{Mis kausta peate WSL-is minema, näha Windowsi kausta C:\Users\perenimi-admin\Documents kausta sisu?}}$


# VIRTUAALMASINA SULGEMINE

Minge https://portal.azure.com/#home kaudu end virtuaalmasina peale ja sulgge see. 

![image](https://user-images.githubusercontent.com/21141607/196045001-014b9723-7dff-484f-8b60-848b11372952.png)

![image](https://user-images.githubusercontent.com/21141607/196045075-a73ccbc8-f077-49f6-aa60-e4c389f991f9.png)

Veenduge, et teie Virtuaalmasinal oleks Status: Stopped (deallocated)


