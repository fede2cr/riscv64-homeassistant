# riscv64-homeassistant
Home assistant built for running in riscv64 inside a container

## Usage

If you want to run home assistant inside a container on riscv64 hardware, run:

```
podman run -p 8123:8123 -it docker.io/fede2/riscv64-homeassistant:latest /bin/bash
```

## Dev

To rebuild home assistant on riscv64 hardware, run:

```
git clone https://github.com/fede2cr/riscv64-homeassistant.git
cd riscv64-homeassistant
podman build .
```


