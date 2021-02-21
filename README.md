JDK Installation

1.Update the repositories:

        $ sudo apt-get update

2.Install OpenJDK 

        $ sudo apt-get install openjdk-8-jdk -y

3.Verify the version of the JDK 

        $ java -version
        openjdk version "1.8.0_252" OpenJDK Runtime Environment (build 1.8.0_252-8u252-b09-1~16.04-b09) OpenJDK 64-Bit Server VM (build 25.252-b09, mixed mode)

4.If you have multiple Java installations to change the default version, use the update-alternatives tool as shown below:

        $ sudo update-alternatives --config java

        Output:- There is only one alternative in link group java (providing /usr/bin/java): /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java Nothing to configure.

5.Set the JAVA_HOME Environment Variable 

   OpenJDK 8 is located at /usr/lib/jvm/java-8-openjdk-amd64/jre/bin/java
  
  Copy the installation path of your Java installation proceeding till /bin/java 
  
  Edit the /etc/environment file

        $ sudo vi /etc/environment

        Add the following line, at the end of the file JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64/jre"

6.Apply the Changes to environment File 
    
        $ source /etc/environment
    
7.Verify the Changes applied 
   
        $ echo $JAVA_HOME
    
    
Maven Installation

1.Update the repositories: 
     
     $ sudo apt-get update

2.Install Apache Maven 
   This example shows version 3.6.3. Substitute the download URL for the most recent version of Apache Maven from the official website. Choose the "Binary tar.gz archive".          Official Website :- https://maven.apache.org/download.cgi

    $ cd /opt/ 
    $ wget http://apache.mirrors.pair.com/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz

   Once the download has completed, extract the downloaded archive. 
   
    $ sudo tar -xvzf apache-maven-3.6.3-bin.tar.gz

   Next, rename the extracted directory 
    
    $ sudo mv apache-maven-3.6.3 maven

3.Set Up Environment Variables

   Set up the environment variables M2_HOME and PATH by creating mavenenv.sh in /etc/profile.d/. 
    
    $ sudo vi /etc/profile.d/mavenenv.sh
    
   Add the following lines in maven.sh file: 
    
    export M2_HOME=/opt/maven 
    export PATH=${M2_HOME}/bin:${PATH}

   Save and close the file, update its permissions, then load the environment. 
        
    $ sudo chmod +x /etc/profile.d/mavenenv.sh 
    $ source /etc/profile.d/mavenenv.sh

4.Verify installation Check the version of the Apache Maven. 
    
    $ mvn --version
       
   The output will be similar to this, depending on your version. 
        
    Apache Maven 3.6.3 (cecedd343002696d0abb50b32b541b8a6ba2883f) 
    Maven home: /opt/maven 
    Java version:         1.8.0_252, vendor: Private Build, runtime: /usr/lib/jvm/java-8-openjdk-amd64/jre 
    Default locale: en_US, platform encoding: UTF-8 OS name: "linux",version: "4.4.0-1109-aws", arch: "amd64", family: "unix"

Jenkins Installation
        
1.Add the repository key to the system
        wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
2.Append the Debian package repository address to the server’s sources.list
        sudo sh -c 'echo deb https://pkg.jenkins.io/debian-stable binary/ > \
        /etc/apt/sources.list.d/jenkins.list'
        
3.Update using Package Manager & Install Jenkins and its dependencies
        sudo apt-get update
        sudo apt-get install jenkins
        systemctl status jenkins
        cat /var/lib/jenkins/secrets/initialAdminPassword

