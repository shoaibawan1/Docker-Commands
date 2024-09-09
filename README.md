Docker-Commands

Here’s a step-by-step guide with the detailed commands to achieve each step in Kali Linux:

1. Install Docker

First, make sure Docker is installed on your Kali Linux system. Run these commands:

bash
sudo apt update
sudo apt install docker.io

After installing Docker, start and enable the Docker service:

bash
sudo systemctl start docker
sudo systemctl enable docker


To verify if Docker is installed correctly, run:

bash
docker --version

2. Create a Container

To create a container from an image (e.g., `ubuntu`), use the following command:

bash
docker run -it --name my_container ubuntu /bin/bash


This creates a container called `my_container` and starts a bash shell in it.

3. Access Your Container

You can access the container you just created by using:

bash
docker exec -it my_container /bin/bash


This will drop you into the shell of your running container.

4. Clone Your Code into Container from GitHub

Inside the container shell, make sure `git` is installed, and clone your repository from GitHub:

bash
apt update
apt install git
git clone https://github.com/your_username/your_repo.git


Make sure to replace `your_username` and `your_repo` with the actual repository details.

5. Create an Image from Container

Once you’ve cloned your code into the container, exit the container shell and create an image from the container:

bash
docker commit my_container my_dockerhub_username/my_image_name


This will create an image with your code inside it. Replace `my_dockerhub_username` and `my_image_name` as per your requirement.

6. Push to Docker Hub

First, log in to Docker Hub:

bash
docker login

Then, push the image to your Docker Hub account:

bash
docker push my_dockerhub_username/my_image_name

7. Delete Container and Local Images

To delete the container:

bash
docker rm -f my_container


To delete the local image:

bash
docker rmi my_dockerhub_username/my_image_name

8. Pull Your Image from Docker Hub

To pull your image back from Docker Hub:

bash

docker pull my_dockerhub_username/my_image_name

9. Create a Container and Start It on Port 80:80

To create and run a container from the pulled image and expose it on port `80:80`, use:

bash
docker run -d -p 80:80 my_dockerhub_username/my_image_name

This will map your host’s port `80` to the container’s port `80` and run the container in detached mode (`-d`).

10. Access Your Website

Now, open a browser and access your website by going to:

http://localhost

If you’re accessing it remotely, replace `localhost` with your server’s IP address.
