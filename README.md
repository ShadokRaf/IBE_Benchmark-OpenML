[![DOI](https://zenodo.org/badge/65920602.svg)](https://zenodo.org/badge/latestdoi/65920602)

README

Instructions for setting up the benchmark

I) Installation
     1. Create an OpenML account, and generate an API key
     2. Install Docker
     3. Install Github

II) Launch the docker container from the console

     1. Download the appropriate docker image from dockerhub (around 2go)
        > docker pull shadoko/docker_java_packages:version3

     2. Create your docker machine and change its parameters
Change the default parameter for your docker machine and use the number of cpus and RAM that you desire. For example :
        > docker-machine create -d virtualbox --virtualbox-cpu-count=6 --virtualbox-memory=16000 --virtualbox-disk-size=50000 default

     3. Generate a rstudio instance that you can connect to
      > docker run --rm -p 8787:8787 -v /Users/myname/myFolder:/home/rstudio/Docker-Benchmark/ shadoko/docker_java_packages:version3

Note : for windows OS syntax is different, and the User Public is recommended for rights issues /c/Users/Public/MyFolder:/home/rstudio/Project shadoko/docker_java_packages:version3

        --rm indicates that the container will be deleted when stopped
        -p indicates the choice of port
        -v indicate linking a volume between the docker VM and your computer
        shadoko/docker_java_packages refers to the docker image used for the benchmark

III) Connect to your rstudio instance
     1. Check the IP of the docker container
     2. In the browser enter http://myContainerIP:8787

Enter login/mdp : rstudio/rstudio

IV) In your rstudio instance
     1. Open main.R, enter your API key and the number of cores you want tu use at the specified place in the file
     2. Get the data from OpenML and optionally compute an estimate of the training time (1-2 days)
     3. Do the benchmark (for 278 datasets, it takes around 8 hours with 7 cores and 8go RAM)
     4. Visualize the results
     5. Additional Simulations and computations

V) Stop the container from the console 
     > docker ps 
     > docker stop "YourContainerID"

