# SISSEJUHATUS 

Olete kunagi kuulnud kedagi ütlemas, see töötas minu arvutis. Olete te kunagi näinud roppu moodi vaeva, et saada enda arvutis käima arenduskeskkond mingile projektile. 
Olete kunagi teinud serveris mingeid muudatusi nii, et nendest muudatustest enam tagasi liikuda ei saa. Tänase praktikumi eesmärk on need probleemid elimineerida või vähemalt selliste probleemide hulka võimalikult palju vähendada. 

Tänase praktikumi teema on Docker, Visual Studio Code, Visual Studio Code devcontainers, ja Azures Container Instances. 



# SAMMUDE LOETELU 


1. Installime Visual Studio Code ja Docker Desktopi
2. Testime Dockerit
3. Loome oma Custom Dockeri image 
5. Testime Azure Container Instanceid
6. Proovime VSCode Devcontainereid



# INSTALLIMINE 

## VSCODE 


### WINDOWS

+ [Lae alla ja installi vscode Windowsis](https://code.visualstudio.com/)

![image](https://user-images.githubusercontent.com/21141607/199066212-7d612dd1-2674-4840-aeb7-9b6905cc49ee.png)

+ [Installige endale Visual Studio Code Remote Development Extension Pack](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)

![image](https://user-images.githubusercontent.com/21141607/199813413-330e585c-ec9c-4744-bcda-dd1f6316de94.png)



### WSL 

+ Ava WSLi terminal
+ Klooni endale WSLis kodukausta repo https://github.com/AndresNamm/dockertest.git
+ Mine kloonitud Githubi kausta 
+ Sisesta käsk 
~~~sh
code .
~~~
+ **PS** - kui viimane käsk hangub, siis lihtsalt sulgege terminal ja avage uuesti. 
+ Nüüd peaks avanema vscode aken. Võite selle akna sulgeda. 
+ Edaspidi saate samamoodi vscode avada. 

## DOCKER 

+ [Installida Docker desktop antud juhendi järgi](https://docs.docker.com/desktop/install/windows-install/)
+ Vaadake, et mõlemad linnukesed oleksid tehtud nagu alloleval pildil. **Eriti oluline on WSLi puudutav osa**
![image](https://user-images.githubusercontent.com/21141607/199082608-c1d0aca8-67ec-4394-8a2b-ae3f56344f86.png)
+ Käivitage Docker 


# TESTIME DOCKERIT 

+ Avage nüüd uuesti WSLi aken 
+ Sisestage käsk
~~~sh
docker ps
docker images 
~~~
+ Nüüd sisestage käsk
~~~sh
docker run -d -p 80:80 docker/getting-started
~~~~
+ Kontrollige jooksvaid dockeri konteinereid
~~~sh
docker ps
~~~
![image](https://user-images.githubusercontent.com/21141607/199088747-d6e543f0-e2fe-4838-a966-b27d96374002.png)
+ $\color{lightblue}{\textrm{Tehk screenshot oma käsu väljundist, nii, et oleks näha teie kasutajanimi}}$
+ Kontrollige oma alla laetu dockeri imagei'd 
~~~sh
docker images
~~~


+ Edasi Minge aadressile http://localhost/tutorial/
+ Järgige nüüd sealt avanenud tutorialit

## DOCKERI TUTORIALI TÄPSUSTAVAD SAMMUD 

## Getting Started

+ $\color{lightblue}{\textrm{Defineerige, mis on Dockerfile, Docker image, Docker container}}$

## Our Application

+ Laadige alla zip fail. 
![image](https://user-images.githubusercontent.com/21141607/199086224-ad1b694b-d794-4238-a28c-187a3c2f8f01.png)
+ Avage WSL ja kopeerige allalaetud app.zip kaust endale WSLi kodukausta 
+ Pakkige app.zip lahti ja minge kausta ning avage vscode

~~~sh
sudo apt install unzip
unzip app.zip
cd app/
code .
~~~
+ Avage terminal vscode aknas: Terminal -> New Terminal. Nagu näete, on WSL avanenud ka vscode sees.
+ Edasi järgige tutorialit nii nagu juhises kirjas. Tehke lõpuni sammud "Getting Started", "Our Application" ja "Updating our APP", "Sharing our App" ja "Persisting data". Soovitame soojalt teha läbi ka järgmised sammud, aga see ei ole kohustuslik

+ $\color{lightblue}{\textrm{Tehke enda VMist screenshot, kus on näha todo app ja terminal koos teie kasutajanimega}}$
 

![image](https://user-images.githubusercontent.com/21141607/199090984-6bba50ea-3b91-46aa-babd-38b71c15b72c.png)



## Sharing our app

+ Kui samm "Play with Docker" ei õnnestu, siis jätke see lihtsalt vahele
+ $\color{lightblue}{\textrm{Mis on antud sammu mõte? Mida see samm demonstreerib?}}$


## Persisting our DB

+ Tehke screenshot käsu 'docker volume inspect todo-db' väljundist.

# AZURE CONTAINER INSTANCES

+ Mäletatavasti tegite endale eelmises praktikumis Azure konto. Tänases praktikumis kasutame seda jälle. 


[Järgnevad sammud on pandud kirja selle tutoriali pinnalt. Kui kuskil jänni jääte, siis saate lisainfot juurde otsida.](https://docs.docker.com/cloud/aci-integration/)

## Logige oma Azure kontole Dockeriga sisse

~~~sh
docker login azure
~~~


## Tekitage endale Docker kontekst

+ Selgitage välja oma [Ülikooli Subscription ID selle juhendi järgi](https://learn.microsoft.com/en-us/azure/azure-portal/get-subscription-tenant-id)
+ Eelnevalt tuleb teil endal resource-group luua. Kasutame selleks azure cli-d. Selleks, et seda kasutada, tuleb ta **WSLi** installida [selle juhendi järgi](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux?source=recommendations&pivots=apt). 
+ Kui olete endal Azure CLI installinud, siis kõigpeale logige oma ülikooli kontoga enda Azure-sse sisse. Avaneb prompt, kus küsitakse teie parooli ja passwordi. 
~~~sh
az login
~~~
+ Valige endale active Azure Subscription. See, mis te enne üles otsisite.
~~~sh
AZURE_SUBSCRIPTION="xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx"
az account set --subscription $AZURE_SUBSCRIPTION
~~~~
+ Pärast sisselogimist saate endal luua uue resource groupi.
~~~sh
az group create --location norwayeast --name <perenimi>-ci
~~~


+ Logi dockeriga Azure sisse

~~~sh
docker login azure
~~~

+ Nüüd saate endal Dockeri konteksti luua. [Mis on Dockeri kontekst?](https://docs.docker.com/engine/context/working-with-contexts/)


~~~
RESOURCE_GROUP=perenimi>-ci
docker context create aci --subscription-id $AZURE_SUBSCRIPTION --resource-group $RESOURCE_GROUP --location norwayeast <perenimi>-aci
~~~


+ Jooksuta nüüd test dockeri imaget Azure pilves 

~~~sh
docker context use <perenimi>-aci
docker run -p 80:80 nginx
~~~

+ See Samm võtab nüüd aega. Ärge seda praegu ära canceldage.
+  $\color{lightblue}{\textrm{Edasi tuleb teil Azure portalis üles leida tekkinud Dockeri konteiner ja sellest Screenshot teha nagu praegune näide näitab}}$
 

![image](https://user-images.githubusercontent.com/21141607/199810779-70615428-8048-435e-ad1b-11992acad83f.png)

+ Antud lehel on kättesaadav ka docker konteineri Public IP. Minge oma veebibrauseriga sellele aadressile. Peaks avanema nginx veebiserveri "Hello world näide". Palju õnne, olete oma esimese Dockeri image laiale avalikusele deploynud.

+ Vaadake nüüd jooksvaid dockeri konteinereid

~~~sh
docker ps
~~~



+ Leidke väljundist CONTAINER ID ja 

~~~sh
docker stop <CONTAINER_ID>
docker rm <CONTAINER_ID>
~~~ 



# VISUAL STUDIO CODE CONTAINERS


Selle sammu eesmärk on teha teie arenduskeskkond 100 % reprodutseeritavaks mõne klikiga. Tavaliselt võtab uue ettevõtte/projektiga liitudes väga pikalt aega arenduskeskkonna üle seadmine. Visual Studio Code devcontainerid lubavad teil üles ehitada oma arenduskeskkonnad Dokcer konteineri põhjal. See tähendab, et arenduskeskkond on 


1. Alati reprodutseeritav
2. Lihtne üles seada
4. Võimalikult sarnane produktsioonikeskkonnaga. 





+ Sulgege nüüd VsCode
+ Avage uuesti Ubuntu WSL
+ Tekitage kodukausta uus repo nimega perenimi-devcontainer


~~~sh
cd <perenimi>-devcontainer
code . 
~~~

 
+ Avanenud vscode aknase vajutage klaviatuuril CTRL+SHIFT+P või valige View->Command Palette
+ Avanenud aknas kirjutage nagu allolevas screenshotis näidatud on



![image](https://user-images.githubusercontent.com/21141607/199813660-7a420feb-691f-49ad-8fde-c9328906b1ac.png)

 
+ Valige From a predefined container configuration definition.. ja Show all definitions
+ Valige menüüst "Go"


+ Avaneb devcontainer.json fail. 
![image](https://user-images.githubusercontent.com/21141607/199814509-cb136077-64a4-43de-9483-7028c66baff7.png)

+ Avage küljelt menüüs kaust ".devcontainer". Seal on ka Dockerfile, mis kirjeldab milliset arenduskeskkonda te dockeris tahata. Antud näide on GO-le suunatud. Seda on võimalik ka kohandada vastavalt vajadusele ning git-i commitida, et uus arendaja saaks endale täpselt sama arenduskeskkonna. 
+ Vajutage uuesti CTRL+SHIFT+P
+ Valige Dev Containers: Rebuild and Reopen in Container. Kui tuleb error, et Dokcer ei jookse, siis

![image](https://user-images.githubusercontent.com/21141607/199815834-bce07388-7750-4552-9955-2bbeb894403c.png)


+ Nüüd tõmmatakse alla kõik vajalikud Dockeri imaged. Natukes aja pärast peaks avanema teil GO arenduskeskkond. 

+ Kopeeriga endale nüüd siit GO keele näide alla https://gobyexample.com/hello-world ja tehke enda arenduskeskkonda uus fail hello-world.go ja jooksutage seda nagu näites näidatud
  
 
+ $\color{lightblue}{\textrm{Tehke screensho jooksnud GO programmist}}$

+ Go installiti ainult Dockeri konteineri sisse. See on täiesti isoleeritud teie ülejäänud VMist. 


# LÕPPSAMMUD 

+ Minge nüüd portal.azure.com. Otsige oma resource grupid üles ja eemaldage kõik loodud ressursid. 

+ Valige kõik ressursid. Ning eemaldage need. 
![image](https://user-images.githubusercontent.com/21141607/199819208-a6014b2d-20d4-4b4b-ade6-3d777ce70d75.png)
+ Vajutage mõlema resource groupi puhul"Delete Resource Group"
![image](https://user-images.githubusercontent.com/21141607/199819415-df2b9cac-b2d7-4c97-936a-7d7e60650fa0.png)
![image](https://user-images.githubusercontent.com/21141607/199819481-3b5721a5-9628-4d84-afd6-0fe7bf60481b.png)




