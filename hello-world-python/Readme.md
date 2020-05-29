# Docker image for Hello-world - Python

`Launch.py` contains the code for a simple hello world API. The API uses a Flask framework which is a dependency for the application.

Dockerfile: are the set of instructions to create a docker image. It contains the following:
1. Base image of Python 3:specifically, Alpine
2. State the work directory: `/app`
3. Copies all the files from the current directory (.) to the app directory `copy . /app`
4. To manage the python application , we need to download the Flask as it is stated in the requirements.txt file by running `RUN pip install -r requirements.txt`
5. Expose port 5000 to run the application to the outside world
6. Run the python application `CMD python ./launch.py`

## Create Docker image from the Docker file
- Run command prompt (I use a windows laptop) and cd into the project directory
- Run the docker build command `docker build -t ibtesting:0.0.1.RELEASE .`,
![](https://github.com/ibejalon/Docker_Practice/blob/master/hello-world-python/screen_shots/Docker_image%20file.JPG)
specify the tag (i.e the hello-world-python version ) and end with "." which is known as the build context.The build context are the files in the current directory needed to run the application to build the image.In this case the build context are Dockerfile, launch.py and requirements.txt

- Once installed run `docker run -p 5000:5000 -d ibtesting/hello-world-python:0.0.1.RELEASE` to create container. 
`-p 5000:5000` is to map the container port (5000) to the host port(5000) so the application can be accessed.
![](https://github.com/ibejalon/Docker_Practice/blob/master/hello-world-python/screen_shots/docker-container-create.JPG)

- Confirm that image is created using `docker images`
![](https://github.com/ibejalon/Docker_Practice/blob/master/hello-world-python/screen_shots/docker-image.JPG)

- start up the app using `docker logs -f container id` 

![](https://github.com/ibejalon/Docker_Practice/blob/master/hello-world-python/screen_shots/application_running.JPG)

## Push Python app to docker hub
Note: You can only push image into docker hub using your docker hub id. Hence, I had to build another image using my docker hub id as the repository name  `docker build -t ibudacity2020devops/hello-world-python:0.0.1.RELEASE .`
![](https://github.com/ibejalon/Docker_Practice/blob/master/hello-world-python/screen_shots/docker_image_push.JPG)

- Log in to docker hub using :`docker login`
- Push image to docker hub repository using : `docker push` 
![](https://github.com/ibejalon/Docker_Practice/blob/master/hello-world-python/screen_shots/dockerhub_repo.JPG)

