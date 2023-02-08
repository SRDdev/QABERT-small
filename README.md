# <img src="https://static.thenounproject.com/png/2397931-200.png" style="height:30px;"> AnswerMind

QABERT is a Question Answering Language Model.This model is a lighter version of any of the question answering models out there.

| Feature          | Value                 |
| ---------------- | --------------------- |
| Datasets         | squad_v2             |
| Language         | en                    |
| Metrics          | accuracy              |
| Library          | transformers         |
| Pipeline         | question-answering    |
| Additional tags  | question-answering    |


## <img src="https://static.thenounproject.com/png/1759538-200.png" style="height:30px;"> Dataset
The Stanford Question Answering Dataset (SQuAD) is a widely used benchmark dataset for the task of machine reading comprehension. It consists of over 100,000 question-answer pairs based on a set of Wikipedia articles. The goal is to train models that can answer questions based on their understanding of the given text passages. SQuAD has played a significant role in advancing the state-of-the-art in this field and remains a popular choice for researchers and practitioners alike.
Due to GPU limitaions the this version is trained on `30k samples` from the Stanford Question Answering Dataset.

<details>
 <summary><i>Structure of the Data Dictonary</i></summary>
<!--All you need is a blank line-->

      {
      "data":[
          {
              "title":"Article Title",
              "paragraphs":[
                  {
                      "context":"The context text of the paragraph",
                      "qas":[
                          {
                              "question":"The question asked about the context",
                              "id":"A unique identifier for the question",
                              "answers":[
                                  {
                                      "text":"The answer to the question",
                                      "answer_start":"The starting index of the answer in the context"
                                  }
                              ]
                          }
                      ]
                  }
              ]
          }
      ],
      "version":"The version of the SQuAD dataset"
      }
</details>

## <img src="https://static.thenounproject.com/png/2921734-200.png" style="height:30px;"> Model

BERT (Bidirectional Encoder Representations from Transformers) is a pre-trained transformer-based model for natural language processing tasks such as question answering. BERT is fine-tuned for question answering by adding a linear layer on top of the pre-trained BERT representations to predict the start and end of the answer in the input context. BERT has achieved state-of-the-art results on multiple benchmark datasets, including the Stanford Question Answering Dataset (SQuAD). The fine-tuning process allows BERT to effectively capture the relationships between questions and answers and generate accurate answers.

1. QA-BERT-small : [Huggingface](https://huggingface.co/SRDdev/QABERT-small)
2. QA-BERT-normal : coming soon...

<img src="https://imgs.search.brave.com/F8m-nwp6EIG5vq--OmJLrCDpIkuX6tEQ_kyFKQjlUTs/rs:fit:1200:1200:1/g:ce/aHR0cHM6Ly9ibG9n/LmdyaWRkeW5hbWlj/cy5jb20vY29udGVu/dC9pbWFnZXMvMjAy/MC8xMC9TbGljZS0x/OC5wbmc">

For more detail about this read [Understanding QABERT](Understanding QABERT/readme.md)


## <img src="https://static.thenounproject.com/png/1703027-200.png" style="height:30px;"> Inference
_Load model_
```python
from transformers import AutoTokenizer, AutoModelForMaskedLM, 

tokenizer = AutoTokenizer.from_pretrained("SRDdev/")
model = AutoModelForMaskedLM.from_pretrained("SRDdev/")
```

_context_
```text
Extractive Question Answering is the task of extracting an answer from a text given a question. 
An example of a question answering dataset is the SQuAD dataset, which is entirely based on that task. 
If you would like to fine-tune a model on a SQuAD task, you may leverage the examples/pytorch/question-answering/run_squad.py.
```


_Build Pipeline_
```python
from transformers import pipeline

ask = pipeline("question-answering", model='')

result = ask(question="What is a good example of a question answering dataset?", context=context)

print(f"Answer: '{result['answer']}'")
```

## <img src="https://static.thenounproject.com/png/2119838-200.png" style="height:30px;"> Contributing

Pull requests are welcome. For major changes, please open an issue first
to discuss what you would like to change.
Please make sure to update tests as appropriate.

## <img src="https://static.thenounproject.com/png/5497984-200.png" style="height:30px;"> Citations
```
@citation{ QABERT,
  author = {Shreyas Dixit},
  year = {2023},
  url = {https://huggingface.co/SRDdev/QABERT}
}
```
