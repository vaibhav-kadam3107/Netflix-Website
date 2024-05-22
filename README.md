### How to Run


1. Create an AWS account if you don't have one, or visit https://aws.amazon.com/console/.
2. Navigate to the EC2 Service section and create two servers, namely Netflix Server 1 and Netflix Server.
3. Log in to the server using SSH and paste the code below.


    sudo apt update -y
    
    git clone https://github.com/vaibhav-kadam3107/Netflix-Website.git
    
    cd Netflix-Website
    

Install Docker 


    sudo apt-get update
    sudo apt-get install docker.io -y
    sudo usermod -aG docker $USER  # Replace with your system's username, e.g., 'ubuntu'
    newgrp docker
    sudo chmod 777 /var/run/docker.sock
    

Run the docker image. Paste the TMDB API key here.


    docker build --build-arg TMDB_V3_API_KEY= -t netflix .
    
    docker run -d --name netflix -p 8081:80 netflix:latest
    

If you want to add the security you can use Trivey. To insatll pase this command.


    sudo apt-get install wget apt-transport-https gnupg lsb-release
    wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
    echo deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main | sudo tee -a /etc/apt/sources.list.d/trivy.list
    sudo apt-get update
    sudo apt-get install trivy        
    


To scan :  trivy image Netflix

To scan all files : trivey fs .

Please remember the following instructions:

- Follow the same steps in the Netflix server. Now your servers are ready.
- The next step is to add a load balancer for these servers. You can do this in the load balancer section of EC2.
- Then, you can add an autoscaling feature so that if network traffic increases, the number of servers increases accordingly.
- Finally, you can assign a domain name for this using the Route 53 service.
