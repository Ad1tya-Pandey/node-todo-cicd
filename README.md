
# Implementation of Containersation and CI/CD pipeline

This project is a Implementation of Docker containers and Jenkins pipeline on a simple Nodejs To-do web app.


## Documentation

In order to build and execute this project using Docker and Jenkins follow the below steps :

### Requirements
- Docker  (20.10.23 or above)
- Jenkins (2.375.2  or above)
- Dockerhub account

Follow the below steps for creating a CI/CD pipeline using Jenkins.( it is recommended to have this setup and required softwares installed on a virtual machine in cloud to have a industry like real-time project which can be accessed from anywhere across the world)

### Steps :
- fork this repository 

- start Jenkins ( `sudo systemctl start jenkins` )

- [setup Jenkins](https://www.jenkins.io/doc/book/installing/linux/) and create administrative user if you are running it for the first time.

- From Jenkins Dashboard add `+ New item` , Enter the name of your pipeline and in sub-options select pipeline .

- Configure your pipeline as shown below:

        1) Enter the description of your choice in the  description dialogbox.
    
        2) Check Github project checkbox and provide the HTTPS URL for your forked Github repository.
    
        3) Under next section of Build triggers select option 'github hook trigger for GITscm polling'
    
        4) Then after in the pipeline section select 'Pipeline script from SCM'
    
        5) Apply and Save

- Adding Dockerhub credentials to Jenkins
you can add your dockerhub credentials using the built-in plugin by going to `Dashboard` and from there to `manage Jenkins` under which you will see security scection select `manage credentials` 
  - add new global credentials with id `Dockerhub`
  with your respective Dockerhub credentials.

- Changing the parameters in Forked Github  repository :

       1) In docker-compose file replace the field 'image' with 'yourdockerhubusername/node-todo-test:latest'
      
       2) In Jenkinsfile under `code stage` replace the `URL parameter` with HTTPS URL of your forked repository.
       
       3) In Jenkinsfile under `build` stage replace `ad1tyapandey` with your Dockerhub username.

- Add webhook :
    from your github repository go to `settings` select `webhooks` and create a webhook with `payload URL` as `http://youripaddress:8080/github-webhook/`
   ,  'content type': application/json
    select the option `just the push event` and create webhook. 

Now you are all set to test this pipeline , just make a commit in your forked repository after following the above mentioned steps and you should see your Jenkins pipeline getting triggered automatically form it which would then ultimately result in automated deployment of app through a multistage declarative pipeline with the help of docker containers and docker-compose.

    
    


    







