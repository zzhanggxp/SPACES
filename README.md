# SPACES
エンドツーエンドの長文要約モデル (2020 司法要約トラック)。

## Run

Env：tensorflow 1.14 + keras 2.3.1 + bert4keras 0.9.7

(Windows，bert4keras>=0.9.8)

まず、「snippets.py」内の該当するパスの設定を変更して、次のコードを実行してください。

Training code：
```bash
#! /bin/bash

python extract_convert.py
python extract_vectorize.py

for ((i=0; i<15; i++));
    do
        python extract_model.py $i
    done

python seq2seq_convert.py
python seq2seq_model.py
```

Predict code:
```python
from final import *
summary = predict(text, topk=3)
print(summary)
```
