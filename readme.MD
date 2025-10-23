Creatig the CI/CD Pipeline using open source tool called JENKINS.


1. using AWS ec2 instance for setup (ubuntu).
2. install java before install jenkins.
   "sudo apt install fontconfig openjdk-17-jre"
   "java -version"
3. install the jenkins using DOC.
4. Start the service- using enable to strat it on boot as well.
5. now check the in browser if it installed or not (port: 8080).
6. unlock it by specifying given path and paste the key.
7. create the fist admin creds and now your jenkins is ready.
##################################################################3
8. you can create additional node and use it as agent.
9. you can set as "agent label lable_name" with managing jenkins entering agent host ip and ssh keys.


#############################
USED a SHARED LIBRARY stored in repo: "jenkins-shared-lib"