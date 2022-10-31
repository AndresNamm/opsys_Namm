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
+ Käivitage Docker uuesti 


+ 


# TESTIME DOCKERIT 

+ Avage nüüd uuesti WSLi aken 
+ Sisestage käsk
~~~sh
docker ps
docker images 

~~~
+ Minge localhost

# LOOME OMA CUSTOM DOCKER IMAGE 




