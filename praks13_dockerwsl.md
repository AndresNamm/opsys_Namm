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
+ [Lugege läbi antud tutorial. Teeme need sammud praktikumis läbi](https://docs.docker.com/cloud/aci-integration/)


## Logige oma Azure kontole Dockeriga sisse

~~~sh
docker login azure
~~~


## Tekitage endale Docker kontekst

+ Selgitage välja oma [Ülikooli Subscription ID selle juhendi järgi](https://learn.microsoft.com/en-us/azure/azure-portal/get-subscription-tenant-id)
+ Eelnevalt tuleb teil endal resource-group luua. Kasutame selleks azure cli-d. Selleks, et seda kasutada, tuleb ta installida [selle juhendi järgi](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli-linux?source=recommendations&pivots=apt). 

~~~sh
az group create --location --name
~~~


~~~sh 
az 
~~~

+ Nüüd saate endal Dockeri konteksti luua. 
~~~
docker context create aci --subscription-id  <Teie Subscriptioni ID> --resource-group  <Teie Resource Group> --location  eu-west
~~~

##




