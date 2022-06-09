Procedure of first construct a pytorch virtual env on cluster 20220501

# CUDA Version

`cd /usr/local/cuda && cat version.txt`

In our case we have CUDA 10.1.243

# Correct Version for Pytorch

On official website - get started

No suitable version -> find previous version -> in our case pytorch 1.7

i.e.
```
pip install torch==1.7.1+cu101 torchvision==0.8.2+cu101 torchaudio==0.7.2 -f https://download.pytorch.org/whl/torch_stable.html
```

#