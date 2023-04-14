## Task
1. (MLM + BERT) +
   1. fusion: concat + element-wise + TransformerBlock
   2. feature selection: title(price, description, ) + model
      1. DataLoader: 
         1. filter:  划分成两个file
         2. x: item_id, title(bert/xxx.tokenizer(input_id, embedding/text)), price, locale, ..., xxx
         3. y: random masked (15%)
         4. preprocess: 缺失值处理
      2. Model (运行时间、算力)
         1. Input: concat/merge/transformerBlock
         2. Encoder: Transformer Block
      3. Loss Function
         1. MLM: 交叉熵
2.  (CLM + GPT)
3. bias 注入【graphormer】
   
