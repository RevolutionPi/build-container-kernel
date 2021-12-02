# Revolution Pi Kernel Build Container

This is a build container for Revolution Pi Kernel

## build container from Dockerfile

```
docker build -t kunbus-kernel-build .
```

## example usage

```
VERSION="5.10"
PREFIX="devel/"

mkdir build

git clone https://github.com/RevolutionPi/kernelbakery -b ${PREFIX}${VERSION} --depth 1 --single-branch build/kernelbakery
git clone https://github.com/RevolutionPi/piControl -b ${PREFIX}/revpi-${VERSION} --depth 1 --single-branch build/piControl
git clone https://github.com/RevolutionPi/linux -b ${PREFIX}revpi-${VERSION}  --depth 1 --single-branch build/linux

docker run -it --rm \
	-v $(PWD)/build:/build \
	-e 'NAME="Jane Doe"' \
	-e 'EMAIL="jane.doe@example.org"' \
	kunbus-kernel-build
```

## configuration options

```
NAME="Jane Doe"
EMAIL="jane.doe@example.org"
UPDATE_CHANGELOG=1	# Update changelog automatically (raspberrypi-kernel_9.20211026-5.10.74+revpi1~20211125215525-33e0c7e603b81_armhf.deb)
```
