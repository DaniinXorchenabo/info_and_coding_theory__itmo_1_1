# info_and_codingtheory__itmo_1_1


[original repo](https://ctlab.itmo.ru/gitlab/eabelyaev/cnnimagecodec)

```bash
docker build -f  ./docker/lighting.Dockerfile --build-arg REQUIREMENTS_FILE=cu_12_2.txt . -t daniinxorchenabo/itmo_dl_labs-env:lighting-cu122-latest
docker run --gpus all --ipc=host --ulimit memlock=-1 --ulimit stack=67108864  -p 0.0.0.0:8888:8888 -p 0.0.0.0:6006:6006 --rm -it -v .:/workspace/NN    daniinxorchenabo/itmo_dl_labs-env:lighting-cu122-latest 
```