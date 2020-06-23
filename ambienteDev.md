# Ambiente para desenvolvimento

### Preparar ambiente virtual
https://github.com/muriloms/projetos-ciencia-de-dados/blob/master/ambienteDev.md

# TensorFlow
- Documentação: https://www.tensorflow.org/api_docs/python/tf
- Procedimentos para instalação: https://www.tensorflow.org/install

### Ambiente utilizando CPU
```
pip install tensorflow
```
por padrão o TF instala pacotes para CPU e GPU, retornando avisos quando não encontra pacotes para GPU. Abaixo uma forma de instalar para somente uso com CPU
```
pip uninstall tensorflow
pip install tensorflow-cpu
```
### Ambiente utilizando GPU
- Instalar CUDA Toolkit: </br>
https://developer.nvidia.com/cuda-downloads?target_os=Linux&target_arch=x86_64&target_distro=Ubuntu&target_version=1804&target_type=deblocal

- Instalar cuDNN:</br>
https://developer.nvidia.com/cudnn

### Caminho que segui
Para instalar o TensorFlow você precisa verificar a versão do seu driver e a compatibilidade com a instalação do CUDA e cuDnn.

No terminal:
nvidia-smi
nvcc --version

Verificar o "Driver Version"
Verificar no endereço abaixo a compatibilidade com o CUDA
https://docs.nvidia.com/deploy/cuda-compatibility/index.html#binary-compatibility__table-toolkit-driver

De acordo com a compatibilidade, instalar a versão do TF de acordo com a tabela:
https://www.tensorflow.org/install/source#tested_build_configurations

No meu caso: murilo 21/05/2019 - nvidia GeForce 940MX
instalei o drive do nvidia seguindo o tutorial:
https://www.linuxbabe.com/ubuntu/install-nvidia-driver-ubuntu-18-04

no comando:
sudo ubuntu-drivers devices

estava recomendado somente para instalar no driver 390. Assim meu Driver Version ficou de 390.116
criei o ambiente virtual com o conda (conda create tf-gpu) e instalei a versão 1.8 do TF
conda install tensorflow-gpu==1.8

Essa versão instala o CUDA 9.0 e cuDnn 7.3, compativel com minha versão do drive.

Testei e TF funcionando !!!

Entretanto, seguindo os códigos abaixo, surgiu novas versões de drive para instalar o nvidia. Agora vou testar, instalando o nvidia em drives mais recentes (e.g. nvidia-driver-418).
Isso permitirá instalar versão CUDA 10.0 e TF 1.12 ou 1.13

Comandos:
#### remover nvidia
sudo apt-get --purge remove nvidia-*

#### remover pacotes instalador e utilizados pelo nvidia
sudo apt-get autoremove

#### atualizar repositorio de versões de drives
sudo add-apt-repository ppa:graphics-drivers/ppa

#### atualizar 
sudo apt-get update

#### verificar versões 
sudo ubuntu-drivers devices

#### instalar no drive selecionado
sudo apt-get install nvidia-driver-XXX

#### reiniciar
sudo reboot
