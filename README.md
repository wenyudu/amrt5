# AMRT5

This repository contains the official implementation of experiments conducted in
- On Enhancing NL2SQL Semantics \[Scalable Data Science\] (VLDB 2024 Submission)

<img src="casestudy.png">

### Repo structure:
- `configs`: Json files for various running configurtions
- `seq2seq`: Codebase for **NL2SQL** experiments, which is adapted from [Picard](https://github.com/ServiceNow/picard) for the file structure.
  - `datasets`: Dataset related python files
  - `metrics`: Metrics related python files
  - `utils`: Folder with python utility files
- `T5`: A modified T5 architecture with AMR augmented, which is derived from [Huggingface Transformers](https://github.com/huggingface/transformers).
- `run_seq2seq_internal.py`: A python file for training main experiments.

### Dependencies
 - python3.7 or above
   
Install python packages

```bash
pip install -r requirements.txt
```

### Basic Usage

Train AMRT5-large (LN) model
```bash
python run_seq2seq_internal.py --config_files=configs/train_amr.json
```

Train AMRT5-large (SC) model
```bash
python run_seq2seq_internal.py --config_files=configs/train_amr_sc.json
```

Train AMRT5-3B model
```bash
python run_seq2seq_internal.py --config_files=configs/train_amr_3B.json
```

Eval the model A 
```bash
python run_seq2seq_internal_eval.py --model_path=path/to/ckpt_A
```

### NL2SQL datasets

| Dataset         | Link |
|------------------|-----------------|
| Spider        |  https://drive.usercontent.google.com/download?id=1iRDVHLr4mX2wQKSgA9J8Pire73Jahh0m&export=download&authuser=0           | 
| SYN | https://github.com/ygan/Spider-Syn            |
| DK        | https://github.com/ygan/Spider-DK            |
| REALISTIC | https://zenodo.org/records/5205322            |

## AMR

<img src="AMR.png"> 

AMR is a comprehensive semantic graph representation of a sentence. It utilizes a directed acyclic graph structure with a root node and represents important concepts as nodes and semantic relationships as edges.

AMR can help PLM to augment their semantics to strive a better trade off between efficiency and effectiveness.

### AMR parser

The parser we choose is orginal from [here](https://github.com/goodbai-nlp/AMRBART). We modified this to be suitable for Natural Language Questions (NLQs) by retraining it using [a corpus of NLQ-AMR pairs](https://github.com/IBM/AMR-annotations).

## License

MIT
