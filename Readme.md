## Item/Session Embedding

1. 难点
   1. Item Embedding: modality interaction
      1. CONCAT + MLP/CNN/LSTM
   2. Session Embedding: item interaction
      1. RNN
2. Item Embedding
   1. BERT4Rec: 双向+只用Item_id
      1. How to use these embedding for next item prediction
3. Multi-modality
   1. Modality Interaction
      1. CONCAT + MLP/CNN/LSTM
      2. 其他的（没严格调研）
      3. Position Information注入到结点中
         1. 文本相似性，时间的相似性，类型的相似性等
         2. ![img](https://img-blog.csdnimg.cn/img_convert/c2a9a36f4da9c7ad663419eedad615a2.png)
         3. ![img](https://img-blog.csdnimg.cn/img_convert/7feef1e3f61abfd871fa9e90548f2f58.png)
         4. ![image-20230412160301900](C:\Users\86151\AppData\Roaming\Typora\typora-user-images\image-20230412160301900.png)
            1. graphor

​		

4. 难点

   1. input feature fusion/modality interaction: 

      1. transformer4rec的处理是在input之前就fusion起来了，通过concat或者element-wise manipulation处理；
      2. 通过graphormer的方式，在attention中以bias的方式注入【也有layerNorm的注入】
         1. id: attention_score
         2. bias: title(color), locale, 
            1. title/text: sbert/encoding(title)=embed1, 
               1. embed1, embed2, ..., embed5
               2. fine-tune sbert: xxx
         3. 

   2. how to construct self-learning

      1. MLM: xxx
      2. CLM: Teacher Force
      3. BART: xxx

   3. Phrase:

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
      3. bias 注入

      

   

   

   1. how to generate title

