# How to build
## Install dependencies
```bash
sudo apt install build-essential libncurses-dev zlib1g-dev gawk git gettext libssl-dev xsltproc rsync wget unzip python3 python3-distutils liblzma-dev python3-magic
```

## Download OpenWRT SDK for your platform
In our case, we use `ramips/mt76x8` platform.

```bash
wget -c https://downloads.openwrt.org/releases/23.05.3/targets/ramips/mt76x8/openwrt-sdk-23.05.3-ramips-mt76x8_gcc-12.3.0_musl.Linux-x86_64.tar.xz
```

## Unpack SDK
```bash
tar xJf openwrt-sdk-23.05.3-ramips-mt76x8_gcc-12.3.0_musl.Linux-x86_64.tar.xz
```

## Change directory
```bash
cd openwrt-sdk-23.05.3-ramips-mt76x8_gcc-12.3.0_musl.Linux-x86_64/
```

## Update OpenWRT feeds
```bash
./scripts/feeds update -a
```

## Clone git repo
```bash
git clone https://github.com/bakabtw/luci-theme-argon package/luci-theme-argon
```

## Build package
```bash  
make package/luci-theme-argon/compile
```

The built package will be located in `bin/packages/mipsel_24kc/base/`

```bash
bakabtw@DESKTOP-UA4ES0M:~/openwrt-sdk-23.05.3-ramips-mt76x8_gcc-12.3.0_musl.Linux-x86_64/$ ls -l bin/packages/mipsel_24kc/base/
total 404
-rw-r--r-- 1 bakabtw bakabtw    579 May 21 14:27 Packages
-rw-r--r-- 1 bakabtw bakabtw    342 May 21 14:27 Packages.gz
-rw-r--r-- 1 bakabtw bakabtw    831 May 21 14:27 Packages.manifest
-rw-r--r-- 1 bakabtw bakabtw     99 May 21 14:27 index.json
-rw-r--r-- 1 bakabtw bakabtw   3671 May 21 14:25 luci-app-vpn_1.0.0_all.ipk
-rw-r--r-- 1 bakabtw bakabtw 392988 May 21 14:23 luci-theme-argon_2.3.1_all.ipk

```

## Optional: build package index
```bash
make package/index
```