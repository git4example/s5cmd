
# Docker Multi Arch build and push
```
# clone s5cmd repo
git clone https://github.com/peak/s5cmd.git
cd s5cmd

# build images
docker build -t public.ecr.aws/parikshit/s5cmd:arm64 --build-arg ARCH=arm64/ .
docker build -t public.ecr.aws/parikshit/s5cmd:amd64 --build-arg ARCH=amd64/ .

# push images
docker push public.ecr.aws/parikshit/s5cmd:arm64d
docker push public.ecr.aws/parikshit/s5cmd:amd64

#b create menifest
docker manifest create public.ecr.aws/parikshit/s5cmd:latest \
 --amend public.ecr.aws/parikshit/s5cmd:arm64 \
 --amend public.ecr.aws/parikshit/s5cmd:amd64

# push menifest
docker manifest push public.ecr.aws/parikshit/s5cmd:latest
```
