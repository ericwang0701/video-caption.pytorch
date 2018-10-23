# S2VT + Attention

This is a re-tooled fork of a [discontinued repo by Sundrops](https://github.com/Sundrops/video-caption.pytorch).

The goal is to have something basic for quick video captioning experiments in PyTorch, while still implementing encoder-decoder framework and attention mechanism, on top of being somewhat updated (having CUDA 9 support, for starters).



## Data processing

Borrowed some scripts from [VideoToTextDNN](https://github.com/OSUPCVLab/VideoToTextDNN).

First process frames of MSVD:

```bash
python process_frames.py /path/to/videos /path/to/write/frames/directories 0 n
```

`n = size of dataset`

Next process features, this will take awhile depending on how many GPUs you have (nasnet-large shown):

```bash
python process_features.py /path/to/written/frames /path/to/write/features --type nasnetalarge
```

Batch size parameter `-bs` can be used to adjust batch size in case you run out of memory. The default of 8 uses around 10gb. Smaller batch size = less memory, but will take longer. 

