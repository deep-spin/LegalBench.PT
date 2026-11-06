# LegalBench.PT

LegalBench.PT is the first comprehensive legal benchmark specifically designed for the European Portuguese context. It assesses large language models' legal knowledge and reasoning abilities across key areas of the Portuguese law.

📄 Paper: https://aclanthology.org/2026.nllp-1.30/

🤗 Dataset: https://huggingface.co/datasets/BeatrizCanaverde/LegalBench.PT


## Updates

**LegalBench.PT** was accepted at the [NLLP](https://nllpw.org/workshop/) (Natural Legal Language Processing) Workshop 2026 🎉🎉


## About

LegalBench.PT provides a rigorous evaluation framework that:

- **Covers 31 fields of law**, grouped into 5 main/broader areas
- **Includes 6 diverse question types** that allow for an automated evaluation:
  - **Multiple-Choice**: Questions with only one correct option
  - **Cloze Tasks**: Fill-in-the-blank exercises formulated as multiple-choice
  - **Case Analysis**: Multiple-choice questions. The difference from the former type is solely related to the exam questions used to create them. Case analysis questions were created from theoretical exercises, while multiple-choice were created from practical problems.
  - **True/False**: Classification of statements as either "True" or "False"
  - **Multiple Selection**: Multiple-choice questions where more than one option can be correct
  - **Matching Questions**: Require respondents to pair items from two columns


## Installation

Install the required dependencies:

```
pip install -r requirements.txt
```


## Usage

### 1. Generate Model Predictions

Run your model on LegalBench.PT to generate predictions:

```
python generation.py \
    --model_path <path_to_your_model> \
    --max_len 1000 \
    --temperature 0.001 \
    --output_path <path_to_save_predictions.jsonl> \
    --seed 42
```

`max_len`, `temperature`, and `seed` can be omitted above.


### 2. Evaluate Model Answers

Evaluate the generated predictions against the ground truth:

```
python evaluation.py evaluate_model_answers \
    --input_path <folder_path_with_predictions> \
    --output_path <folder_path_to_save_evaluations>
```

### 3. Compute Model Scores

Calculate aggregate scores across all evaluations:

```
python evaluation.py compute_model_scores \
    --input_path <folder_path_to_save_evaluations> \
    --output_path <folder_path_to_save_aggregated_scores>
```

## Citation

Please cite the following paper if you use LegalBench.PT in your work:
```bibtex
@inproceedings{canaverde-etal-2026-legalbench,
    title = "{L}egal{B}ench.{PT}: A Benchmark for {P}ortuguese Law",
    author = "Canaverde, Beatriz  and
      Pires, Telmo  and
      Martins, Andre",
    editor = "Aletras, Nikolaos  and
      Chalkidis, Ilias  and
      Barrett, Leslie  and
      Goanț{\u{a}}, C{\u{a}}t{\u{a}}lina  and
      Preoțiuc-Pietro, Daniel  and
      Spanakis, Gerasimos  and
      Xu, Shanshan",
    booktitle = "Proceedings of the Natural Legal Language Processing Workshop 2026",
    month = oct,
    year = "2026",
    address = "Budapest, Hungary",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2026.nllp-1.30/",
    doi = "10.18653/2026.nllp-1.30",
    pages = "334--349",
    ISBN = "979-8-89176-494-1",
    abstract = "The growing use of LLMs in the legal field has spurred the creation of benchmarks across various jurisdictions and languages, yet none specifically focused on the Portuguese legal system. We present LegalBench.PT, the first comprehensive benchmark for Portuguese law. To develop it, we first collect long-form questions and answers from real law exams, and then use GPT-4o to convert them into multiple-choice, true/false, and matching formats. Once generated, the questions are filtered and processed to improve the quality of the dataset. To ensure accuracy and relevance, we validate our approach by having a legal professional review a sample of the generated questions. Although synthetically generated, we show that their basis in human-created exams and our rigorous filtering and processing methods applied result in a reliable benchmark for assessing LLMs' legal knowledge and reasoning abilities. Finally, we evaluate the performance of leading LLMs on LegalBench.PT and investigate potential biases in GPT-4o{'}s responses. We also assess the performance of Portuguese lawyers on a sample of questions to establish a baseline for model comparison and validate the benchmark."
}
```
