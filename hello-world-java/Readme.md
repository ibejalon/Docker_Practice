# Hello world for Java file
- The docker file is a 2-stage build process:  Build for JAR file, and Image to run the jar file
* To create a jar file you need maven (similar to pip in python)
The the Jar file is used as input in the image by copying the buildfile into the image
- pom file which contains all the dependencies needed to run the java app.
