https://www.tensorflow.org/install/gpu

## Requirment
1. nvidia driver (CUDA® 11.2 requires 450.80.02 or higher)
2. CUDA Toolkit - TensorFlow supports CUDA® 11.2 (TensorFlow >= 2.5.0)
3. cuDNN

# remove all nvidia package


```
sudo apt-get remove --purge '^nvidia-.*'
sudo apt-get remove --purge '^libnvidia-.*'
sudo apt autoremove
sudo apt autoclean
```
check if nvidia still exist
```
dpkg -l | grep -i nvidia
```

# nvidia driver(470) installment 
add nvidia source
```
sudo add-apt-repository ppa:graphics-drivers/ppa
```

check nvidia-driver version
```
apt search nvidia-driver
```

install nvidia-driver-470
```
sudo apt install nvidia-driver-470
```

reboot and check if installment
```
sudo reboot now
nvidia-smi
```

# nvidia Toolkit
download the runfile
https://developer.nvidia.com/cuda-11-4-4-download-archive?target_os=Linux&target_arch=x86_64&Distribution=Ubuntu&target_version=18.04&target_type=runfile_local
tip: this download version matches 470. If you install the nvidia-driver with other version, find the proper one. But make sure to select cuda 11, as tf support cuda 11 rather than 10.

```
wget https://developer.download.nvidia.com/compute/cuda/11.4.4/local_installers/cuda_11.4.4_470.82.01_linux.run

sudo sh cuda_11.4.4_470.82.01_linux.run
```
make sure do not select the driver(\*)



# cuDNN
https://developer.nvidia.com/rdp/cudnn-download
download the right file

```
tar -xf cudnn-linux-x86_64-8.4.0.27_cuda11.6-archive.tar.xz
cd cudnn-linux-x86_64-8.4.0.27_cuda11.6-archive
sudo cp ./include/cudnn* /usr/local/cuda-11.4/include
sudo cp ./lib/libcudnn* /usr/local/cuda-11.4/lib64
sudo chmod a+r /usr/local/cuda-11.4/include/cudnn* /usr/local/cuda-11.4/lib64/libcudnn*
```

## tensorflow (2.7.0)
```
python 3.9
tensorflow 2.7.0
```
Do not install tensorflow-gpu,or early version of tensorflow, it will has all kinds of error.
```
conda install -c conda-forge/label/broken tensorflow 
```


