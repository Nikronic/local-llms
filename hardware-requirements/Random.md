[[D] Choosing Cloud vs local hardware for training LLMs. What's best for a small research group? : MachineLearning (reddit.com)](https://www.reddit.com/r/MachineLearning/comments/11rnppe/d_choosing_cloud_vs_local_hardware_for_training/)

>[https://fullstackdeeplearning.com/cloud-gpus/](https://fullstackdeeplearning.com/cloud-gpus/)
Your best bet to reach 256Gb in the cloud would be Azure with 4x80GB A100 instances, however your 40k budget will only buy you 3000 hours of compute at best on demand, with spot instances stretching that a bit further.
>
If that's not enough for you then you will have to figure out how to make a server with RTX A6000 Adas with 48GB each. RTX4090 would be cheaper but there may be legal issues due to the gaming driver license, you would need to use multiple servers due to power usage or strongly limit the power limit, and Nvidia dropped P2P that may o may not matter depending on how much communication you need between the GPUs ([https://discuss.pytorch.org/t/ddp-training-on-rtx-4090-ada-cu118/168366](https://discuss.pytorch.org/t/ddp-training-on-rtx-4090-ada-cu118/168366))

---
[Standard nVidia CUDA tests fail with dual RTX 4090 Linux box - Graphics / Linux / Linux - NVIDIA Developer Forums](https://forums.developer.nvidia.com/t/standard-nvidia-cuda-tests-fail-with-dual-rtx-4090-linux-box/233202/43)

> https://forums.developer.nvidia.com/t/standard-nvidia-cuda-tests-fail-with-dual-rtx-4090-linux-box/233202/40
> 
>From the tone of the discussion it seems 4090s will have P2P locked. In my case, it renders the 4090 worthless.
I ended up having an internal debate between A100 40G / A5500 24G x2 + opted for 2x A5500. It is in the ballpark of a pair of 4090s + it packs the performance of the A100 40G that, I have a feeling we both may have been aiming for.
A consideration if you are able to make the hardware switch.
For HPC we’re stuck with using appropriate hardware. Not necessarily a bad thing. Tools tend to be more functional than toys.

> https://forums.developer.nvidia.com/t/standard-nvidia-cuda-tests-fail-with-dual-rtx-4090-linux-box/233202/42
That’s nice and all, but it’s useless. 24G of ram is nothing. 5500 has P2P/SLI 3090 has neither.
With the poor capabilities of the 4090 it’s worthless as anything but a toy. I returned 2 of them. At least I can use 100% of an A5500. P2P performance probably hinders scaling with more than two RTX 4090 because of bad all gather and all reduce performance

---

