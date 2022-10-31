# SISSEJUHATUS 

Tänase praktikumi teema on Docker, Visual Studio Code, Visual Studio Code devcontainers, ja Azures Container Instances. 


# SAMMUDE LOETELU 


1. Installime Visual Studio Code ja Docker Desktopi
2. Testime Dockerit
3. Loome oma Custom Dockeri image 
4. Proovime VSCode Devcontainereid
5. Testime Azure Container Instanceid


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

## GETTING STARTED

+ $\color{lightblue}{\textrm{Defineerige, mis on Dockerfile, Docker image, Docker container}}$

## OUR APPLICATION

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
+ Edasi järgige tutorialit nii nagu juhises kirjas. Tehke lõpuni sammud "Getting Started", "Our Application" ja "Updating our APP"




![image](https://user-images.githubusercontent.com/21141607/199090984-6bba50ea-3b91-46aa-babd-38b71c15b72c.png)



# LOOME OMA CUSTOM DOCKER IMAGE 

https://docs.docker.com/language/python/




