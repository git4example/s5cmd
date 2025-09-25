
# Docker Multi Arch build and push

We are overriting Dockerfile from this repo as we have updated GOLANG and Alpine images to latest. 

```
# clone s5cmd repo
git clone https://github.com/peak/s5cmd.git
cd s5cmd

curl -o Dockerfile https://raw.githubusercontent.com/git4example/s5cmd/main/Dockerfile

# build images
docker build -t public.ecr.aws/parikshit/s5cmd:arm64 --build-arg ARCH=arm64/ .
docker build -t public.ecr.aws/parikshit/s5cmd:amd64 --build-arg ARCH=amd64/ .

# push images
docker push public.ecr.aws/parikshit/s5cmd:arm64
docker push public.ecr.aws/parikshit/s5cmd:amd64

#b create menifest
docker manifest create public.ecr.aws/parikshit/s5cmd:latest \
 --amend public.ecr.aws/parikshit/s5cmd:arm64 \
 --amend public.ecr.aws/parikshit/s5cmd:amd64

# push menifest
docker manifest push public.ecr.aws/parikshit/s5cmd:latest
```
