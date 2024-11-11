# Assignment Repo

Download the file from this link https://www.gyan.dev/ffmpeg/builds/
ffmpeg-release-essentials.7z

extract, rename the folder to ffmpeg
place the folder in c drive C:/

Advanced System Settings
Environment Variables
Under System Variables, search for path 
Key this "C:\ffmpeg\bin"

Exit all existing command prompts if any) and open a new command prompt.
Type "ffmpeg -version" you should see a response


Specify the full path
curl -F "file=@C:/Users/danie/Documents/Machine Learning/HTX/myrepo/common_voice/cv-valid-dev/sample-000000.mp3" http://localhost:8001/asr
E.g. {"transcription":"BE CAREFUL WITH YOUR PROGNOSTICATIONS SAID THE STRANGER","duration":"5.1"}


Setting up Docker

Download Docker Desktop and install
https://www.docker.com/products/docker-desktop/

Setup GPU support
Install WSL follow the link
https://learn.microsoft.com/en-us/windows/wsl/install
Must install via Powershell as an admin.
type "wsl --unregister ubuntu"
type "wsl --install" and follow through all the instructions.

Install Nvidia Container Toolkit.
Follow this link for instructions https://docs.nvidia.com/datacenter/cloud-native/container-toolkit/latest/install-guide.html

Docker pull a cuda image from the Docker hub repo and run it to check for GPU support.

C:\Users\danie\Documents\Machine Learning\HTX\myrepo>docker run --rm --gpus all nvidia/cuda:11.8.0-cudnn8-devel-ubuntu22.04 nvidia-smi

==========
== CUDA ==
==========

CUDA Version 11.8.0

Container image Copyright (c) 2016-2023, NVIDIA CORPORATION & AFFILIATES. All rights reserved.

This container image and its contents are governed by the NVIDIA Deep Learning Container License.
By pulling and using the container, you accept the terms and conditions of this license:
https://developer.nvidia.com/ngc/nvidia-deep-learning-container-license

A copy of this license is made available in this container at /NGC-DL-CONTAINER-LICENSE for your convenience.

Mon Nov 11 15:25:32 2024
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 555.59                 Driver Version: 556.13         CUDA Version: 12.5     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 3070 ...    On  |   00000000:01:00.0 Off |                  N/A |
| N/A   67C    P8             13W /   80W |       0MiB /   8192MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+

+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI        PID   Type   Process name                              GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|  No running processes found                                                             |
+-----------------------------------------------------------------------------------------+


Build Docker image
docker build -t asr-api .

After build, run Docker image
docker run -p 8001:8001 asr-api

use another terminal and check for the ping and start running some samples
curl -F "file=@C:/Users/danie/Documents/Machine Learning/HTX/myrepo/harvard.mp3" http://localhost:8001/asr

