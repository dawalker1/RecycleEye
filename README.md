Containerize mock detection app

This project seeks to containerize the mock detection app in this github repo:

1. Starting with the Dockerfile, the necessary dependencies are set to be installed into the working directory of the base image.

2. I then export TMPDIR='/var/tmp' to avoid running out of space when installing the requirements.

3. Next pip is used to install the packages in the requirements.txt, to allow for iterative development and to ensure that the build doesn't re-download and re-install the dependencies every time there is a change to the source code, Docker's layer caching is used which skips installing requirements if the requirements.txt file does not change.

4. Multistage builds are also utilised as the dependencies are built in a base image and then imported into the application image, further slimming down the final docker image

5. Finally github actions are used to both download and replace the current saved model with the coco model and subsequently build the docker image using persistent workflow techniques.

