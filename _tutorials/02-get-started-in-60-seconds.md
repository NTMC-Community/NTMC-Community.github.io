---
title: "Get Started in 60 Seconds"
permalink: /tutorials/get-started-in-60-seconds/
excerpt: "Get Started in 60 Seconds."
last_modified_at: 2020-07-27
redirect_from:
  - /theme-setup/
toc: true
---

Goal of this tutorial:
- Understand MatchZoo library and neural networks at a high level.
- Train a small neural network

To train a [Deep Semantic Structured Model](https://www.microsoft.com/en-us/research/project/dssm/), make use of MatchZoo customized loss functions and evaluation metrics to define a task:

```python
import torch
import matchzoo as mz

ranking_task = mz.tasks.Ranking(losses=mz.losses.RankCrossEntropyLoss(num_neg=4))
ranking_task.metrics = [
    mz.metrics.NormalizedDiscountedCumulativeGain(k=3),
    mz.metrics.MeanAveragePrecision()
]
```

Prepare input data:

```python
train_pack = mz.datasets.wiki_qa.load_data('train', task=ranking_task)
valid_pack = mz.datasets.wiki_qa.load_data('dev', task=ranking_task)
```

Preprocess your input data in three lines of code, keep track parameters to be passed into the model:

```python
preprocessor = mz.models.ArcI.get_default_preprocessor()
train_processed = preprocessor.fit_transform(train_pack)
valid_processed = preprocessor.transform(valid_pack)
```

Generate pair-wise training data on-the-fly:
```python
trainset = mz.dataloader.Dataset(
    data_pack=train_processed,
    mode='pair',
    num_dup=1,
    num_neg=4,
    batch_size=32
)
validset = mz.dataloader.Dataset(
    data_pack=valid_processed,
    mode='point',
    batch_size=32
)
```

Define padding callback and generate data loader:
```python
padding_callback = mz.models.ArcI.get_default_padding_callback()

trainloader = mz.dataloader.DataLoader(
    dataset=trainset,
    stage='train',
    callback=padding_callback
)
validloader = mz.dataloader.DataLoader(
    dataset=validset,
    stage='dev',
    callback=padding_callback
)
```

Initialize the model, fine-tune the hyper-parameters:

```python
model = mz.models.ArcI()
model.params['task'] = ranking_task
model.params['embedding_output_dim'] = 100
model.params['embedding_input_dim'] = preprocessor.context['embedding_input_dim']
model.guess_and_fill_missing_params()
model.build()
```

`Trainer` is used to control the training flow:

```python
optimizer = torch.optim.Adam(model.parameters())

trainer = mz.trainers.Trainer(
    model=model,
    optimizer=optimizer,
    trainloader=trainloader,
    validloader=validloader,
    epochs=10
)

trainer.run()
```