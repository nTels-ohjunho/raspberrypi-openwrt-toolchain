# openwrt SDK for Raspberry-pi
## 소개
안녕하세요 엔텔스 오준호라고 합니다.
이 Git에 배포하는 openwrt SDK는 라즈베리파이용으로 제작되었으며
라우터를 위한 오픈 소스인 openwrt를 jvm등 기존의 glibc 환경에서 사용 가능하도록 재컴파일을 하여 배포하는 제품입니다.

툴체인을 비롯한 온전한 SDK를 모두 배포하며 기본 코드의 변경이 없기에 소스는 첨가하지 않습니다.

## SDK 사용 환경
* Raspberry-pi (brcm2708)
* linux-x86_64
* eglibc-2.15
* gcc-4.8-linaro

## 사용방법 

OpenWrt-SDK-brcm2708-for-linux-x86_64-gcc-4.8-linaro_eglibc-2.15.tar.bz2 파일의 압축을 해제합니다.
```
cat OpenWrt-SDK-brcm2708-for-linux-x86_64-gcc-4.8-linaro_eglibc-2.15.tar.gz* | gunzip | tar -xvf -
```
개발한 프로젝트에 툴체인 위치를 지정합니다. root 디렉토리를 git root로 지정하였을 경우입니다.
Makefile에 아래 구문 추가
```
GIT_ROOT = $(shell git rev-parse --show-toplevel)
TOOLCHAIN_DIR = $(GIT_ROOT)/OpenWrt-SDK-brcm2708-for-linux-x86_64-gcc-4.8-linaro_eglibc-2.15/staging_dir/toolchain-arm_arm1176jzf-s+vfp_gcc-4.8-linaro_eglibc-2.15_eabi/bin
CC = $(TOOLCHAIN_DIR)/arm-openwrt-linux-gcc
AR = $(TOOLCHAIN_DIR)/arm-openwrt-linux-ar
LD = $(TOOLCHAIN_DIR)/arm-openwrt-linux-ld
STRIP = $(TOOLCHAIN_DIR)/arm-openwrt-linux-strip
CONF = \
  --target=arm-openwrt-linux \
  --host=arm-openwrt-linux \
  --build=x86_64-linux-gnu

export CC
export AR
export LD
export STRIP
```


## 재배포자
엔텔스 porduct개발팀 

* 이상훈
* 오준호
* 김유성

## License

See [LICENSE](LICENSE) file.
 
## Package Guidelines

See [CONTRIBUTING.md](CONTRIBUTING.md) file.


