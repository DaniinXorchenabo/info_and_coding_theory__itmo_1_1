# Теория информации и кодирования. ИТМО 1_1
## Итоговый проект

[original repo](https://ctlab.itmo.ru/gitlab/eabelyaev/cnnimagecodec)

Отчёт: [gh_Отчет_по_финальному_проекту.pdf](https://github.com/user-attachments/files/18052633/gh_._._._._.pdf)

## Results

![image](https://github.com/user-attachments/assets/ead76ad0-ae41-4a4a-8a46-ba06c2979fab)

![image](https://github.com/user-attachments/assets/86d8c23f-5fac-4b47-a9b4-c892f00eb455)

![image](https://github.com/user-attachments/assets/564046fc-3632-4212-8ae4-03ece2493603)

---
Результаты работы модель с шумом при 7 битах на один параметр в скрытом представлении
![image](https://github.com/user-attachments/assets/8a9a377f-fb83-4246-935e-27f902b149cf)
---

Результаты работы модель с шумом при 2 битах на один параметр в скрытом представлении
![image](https://github.com/user-attachments/assets/b919155a-daed-44f9-a277-1785acf85366)
---

Результаты работы модель без шума при 7 битах на один вес
![image](https://github.com/user-attachments/assets/a6cc694c-1855-4d35-8662-b7b85e753695)
---

Результаты работы модель без шума при 2 битах на один вес
![image](https://github.com/user-attachments/assets/268fadfd-b842-4471-a3dd-de91894ad018)
---

## Run and build

1. Copy [entrypoint.d](https://gitlab.com/nvidia/container-images/cuda/-/tree/master/entrypoint.d) to `<project_root>/docker/source`
2. Copy [NGC-DL-CONTAINER-LICENSE](https://gitlab.com/nvidia/container-images/cuda/-/blob/master/NGC-DL-CONTAINER-LICENSE) to `<project_root>/docker/source`
3. Copy [nvidia_entrypoint.sh](https://gitlab.com/nvidia/container-images/cuda/-/blob/master/nvidia_entrypoint.sh) to `<project_root>/docker/source`
4. (Optional) Enable `docker` [Buildkit](https://docs.docker.com/build/buildkit/#:~:text=To%20use%20Docker%20BuildKit%20by,the%20following%20to%20the%20file)

5.
```bash
docker build -f  ./docker/lighting.Dockerfile --build-arg REQUIREMENTS_FILE=cu_12_2.txt . -t daniinxorchenabo/itmo_dl_labs-env:lighting-cu122-latest
```

6.
```bash
cp ./env/example.env ./env/.env
```

7. Input your token
```bash
nano ./env/.env
```

8. Run docker image

In windows console:
```bash
docker run --gpus all --ipc=host --ulimit memlock=-1 --ulimit stack=67108864  -p 0.0.0.0:8888:8888 -p 0.0.0.0:6007:6006 --rm -it --env-file ./env/.env -v .:/workspace/NN --mount type=bind,src=%cd%/docker/jupyter_config,dst=/root/.jupyter/   daniinxorchenabo/itmo_dl_labs-env:lighting-cu122-latest jupyter lab --config=/root/.jupyter/jupyter_lab_config.py --allow-root --ip=0.0.0.0
```

In linux console:
```bash
docker run --gpus all --ipc=host --ulimit memlock=-1 --ulimit stack=67108864  -p 0.0.0.0:8888:8888 -p 0.0.0.0:6007:6006 --rm -it --env-file ./env/.env -v .:/workspace/NN --mount type=bind,src=$(PWD)/docker/jupyter_config,dst=/root/.jupyter/   daniinxorchenabo/itmo_dl_labs-env:lighting-cu122-latest jupyter lab --config=/root/.jupyter/jupyter_lab_config.py --allow-root --ip=0.0.0.0
```


9. Build codec

   Для сборки кодека необходимо выполнить ноутбук `./notebooks/build_cpp_codec.ipynb`


