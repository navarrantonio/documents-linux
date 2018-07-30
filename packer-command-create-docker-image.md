#### Using Packer to create a Docker image

Using Packer to create a Docker image
Packer is a HashiCorp tool that is capable of creating identical images for different platforms from a template. For example, from a template you can create images for Amazon EC2, VMWare, VirtualBox and DigitalOcean. One of those platforms is Docker.

The following template shows three stages. In the first, the builder is indicated; which in this case is Docker, as well as the image to use ubuntu: 14.04. The second defines the provisioning stage, a simple shell. And finally, the steps of post-processing.
````bash
{
"builders": [
  {
    "type": "docker",
    "image": "ubuntu: 14.04",
    "commit": "true"}],
"provisioners": [
  {
    "type": "shell",
    "script": "bootstrap.sh"
  }
],
"post-processors": [
   {
     "type": "docker-tag",
     "repository": "how2dock / packer",
     "tag": "latest"
   }
]
}
````
We can check this template and execute it to build the image with two commands:
````bash
$ packer validate template.json
$ packer build template.json
````
#### Publish images in Docker Hub
Once we have generated an image of some usefulness for other Docker users, we have at our disposal Docker Hub, where we can upload it and make it accessible, or not, for the rest of the Docker community.

To be able to use the Docker Hub service, we must complete the following actions:

Create an account in Docker Hub
Log in from our host with Docker
Upload our image (push)
Once we have created our Docker Hub account, we access our system with Docker, select an image and publish it in our public repository:

We start session with docker login. We will have to enter the credentials.
We tag one of our images with the Docker Hub username.
We push towards the repository.
The first step (login) saves the credentials in ~ / .docker / config.json. Once consulted the available images, we make use of one of them, for example:
````bash
$ docker tar packer [user] / packer
$ docker images
````
Once the label has been modified with the format required by Docker Hub, we are ready to make the upload:
````bash
$ docker push [user] / packer
````
When the upload is complete, any user can download the image with the docker pull [user] / packer command.

In case of not knowing the exact name of an image, we can perform a search with the command docker search:
````bash
$ docker search postgres
````
Among the results we can see the official image (first), and the rest will be created by Docker Hub users.

http://recetas-docker.readthedocs.io/es/latest/capitulo_1.html#introduccion
http://recetas-docker.readthedocs.io/es/latest/capitulo_2.html
