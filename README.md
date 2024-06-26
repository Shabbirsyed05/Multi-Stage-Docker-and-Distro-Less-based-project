# Multi Stage Docker Build

The main purpose of choosing a golang based applciation to demostrate this example is golang is a statically-typed programming language that does not require a runtime in the traditional sense. Unlike dynamically-typed languages like Python, Ruby, and JavaScript, which rely on a runtime environment to execute their code, Go compiles directly to machine code, which can then be executed directly by the operating system.

So the real advantage of multi stage docker build and distro less images can be understand with a drastic decrease in the Image size.

#
![image](https://github.com/Shabbirsyed05/Multi-Stage-Docker-and-Distro-Less-based-project/assets/119849465/22edc0a7-033f-42bf-a0eb-ebe1fb8c57dc)

Here it is single docker file but it has 2 stages.
Stage 1: From ubutu as base image it will run the instructions and it will pass the binary to stage 2
Stage 2: In stage 2 it will take the binary from stage 1 . It will be having only the runtime based on stage 1 not the total base image by this it saves more space

![image](https://github.com/Shabbirsyed05/Multi-Stage-Docker-and-Distro-Less-based-project/assets/119849465/37fa5a64-bcaa-4a9f-a941-19b3ee8b593d)

From the above pic it can refered. 
 Stage 1 : By combining all its going upto 1.4 GB
 Stage 2: Here we are using runtime or whatever we requied .So that size is getting decresed a lot


![image](https://github.com/Shabbirsyed05/Multi-Stage-Docker-and-Distro-Less-based-project/assets/119849465/cfc6c41f-65b7-4509-9efd-0b01cb91dc00)

 For Golang => it doesnot require runtime .So the size will be appri 10 to 15 mb

 # Advantages of Distroless:
 It prevents hackers from accessing it . It will be having very less chances of exposing to security threats

 # Working on Git
 ```
 git init
 git clone https://github.com/Shabbirsyed05/Multi-Stage-Docker-and-Distro-Less-based-project.git
 ls
 go run calculator.go

 vim dockerfile-without-multistage/calculator.go
 cd dockerfile-without-multistage
ls

docker build -t simplecalculator .
docker images
```
It will be creating an image of size 861 mb

```
cd ..
ls
vim Dockerfile
```
scratch is the minimialistic image (Golang does not require runtime . So we can use this)
```
docker build -t simplecalculator-multistage .
docker images
```
Now the size will be approx 2 mb
 
`
