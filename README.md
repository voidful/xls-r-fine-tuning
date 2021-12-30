# xls-r-fine-tuning

xls-r fine-tuning script modify from https://huggingface.co/blog/fine-tune-xlsr-wav2vec2

- fix large memory usage during eval metric calculation
- add cer and wer for evaluation

## example usage

```bash
pip install -r requirements.txt

python -m torch.distributed.launch                          \
              --nproc_per_node=2                            \
    train.py                                                \
    --batch                   10                            \
    --max_input_length_in_sec 20                            \
    --common_voice_subset     zh-TW                         \
    --group_by_length                                       \
    --tokenize_config voidful/wav2vec2-large-xlsr-53-tw-gpt \
    --xlsr_config facebook/wav2vec2-xls-r-300m              
```

## sweep usage

```bash
python -m wandb sweep ./sweep_xxx.yaml
python -m wandb agent xxxxxxxxxxxxxx
```
