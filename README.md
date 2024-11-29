
# Docker Multi Arch build and push
```
git clone https://github.com/peak/s5cmd.git
cd s5cmd
docker build -t public.ecr.aws/parikshit/s5cmd:arm64 --build-arg ARCH=arm64/ .
docker build -t public.ecr.aws/parikshit/s5cmd:arm64 --build-arg ARCH=amd64/ .
docker push public.ecr.aws/parikshit/s5cmd:arm64
docker push public.ecr.aws/parikshit/s5cmd:amd64
docker manifest create public.ecr.aws/parikshit/s5cmd:latest \
 --amend public.ecr.aws/parikshit/s5cmd:arm64 \
 --amend public.ecr.aws/parikshit/s5cmd:amd64

docker manifest push public.ecr.aws/parikshit/s5cmd:latest
```