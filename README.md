<div align="center">

# FreeV-official <!-- omit in toc -->
[![ColabBadge]][notebook]
[![PaperBadge]][paper]  

</div>

Clone of the [official FreeV][officialRepository], mel-to-wave vocoders with Pseudo Inversed Mel Filter.

![model](./figure/overall.png)

One liner code:
```python
model_input = mel_spec @ mel_filter.pinverse().abs().clamp_min(1e-5)
```

## Demo
Official [demo page]. 


## Requirements
```bash
git clone https://github.com/BakerBunker/FreeV.git
cd FreeV
pip install -r requirements.txt
```

## Configs

I tried using [PGHI(Phase Gradient Heap Integration)](https://ieeexplore.ieee.org/stamp/stamp.jsp?arnumber=7890450) as phase spec initialization. But sadly it didn't work.

| Model         | Config File       | Train Script  | 
| ------------- | ----------------- | ------------- |
| APNet2        | config.json       |train.py       |
| APNet2 w/pghi | config_pghi.json  |train_pghi.py  |
| FreeV         | config2.json      |train2.py      |
| FreeV w/pghi  | config2_pghi.json |train2_pghi.py |

## Training
**Model checkpoints** and **tensorboard training logs** available at: [huggingface](https://huggingface.co/Bakerbunker/FreeV_Model_Logs)

```
python <train-script>
```
Checkpoints and copy of the configuration file are saved in the `checkpoint_path` directory in `config.json`.

Modify the training and inference configuration by modifying the parameters in the `config.json`.

## Inference
Download pretrained model on LJSpeech dataset at [huggingface](https://huggingface.co/Bakerbunker/FreeV_Model_Logs).

Modify the `inference.py` to inference.

## References
### Original paper <!-- omit in toc -->
[![PaperBadge]][paper]  
<!-- Generated with the tool -> https://arxiv2bibtex.org/?q=2406.08196&format=bibtex -->
```
@misc{2406.08196,
Author = {Yuanjun Lv and Hai Li and Ying Yan and Junhui Liu and Danming Xie and Lei Xie},
Title = {FreeV: Free Lunch For Vocoders Through Pseudo Inversed Mel Filter},
Year = {2024},
Eprint = {arXiv:2406.08196},
}
```

### Acknowlegements
- [official APNet2](https://github.com/redmist328/APNet2)

See the code changes at this [commit](https://github.com/BakerBunker/FreeV/commit/95e1e5cb3fe2b0360a30f39167e3e3ffd8097980)


[ColabBadge]:https://colab.research.google.com/assets/colab-badge.svg

[paper]:https://arxiv.org/abs/2406.08196
[PaperBadge]:https://img.shields.io/badge/paper-arxiv.2406.08196-B31B1B.svg
[notebook]:https://colab.research.google.com/github/tarepan/FreeV-official/blob/main/freev.ipynb
[demo page]:https://bakerbunker.github.io/FreeV/
[officialRepository]:https://github.com/BakerBunker/FreeV