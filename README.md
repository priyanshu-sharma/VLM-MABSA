# Vision-Language Pre-Training for Multimodal Aspect-Based Sentiment Analysis(VLP-MABSA)
Codes and datasets for our ACL'2022 paper:[Vision-Language Pre-Training for Multimodal Aspect-Based Sentiment Analysis]()

Author

Yan Ling

ylin@njust.edu.cn

## Data Process
The pre-training dataset we use is MVSA-Multi. You can get from this [git](https://github.com/xunan0812/MultiSentiNet).
- For texts in MVSA-Multi dataset, we first use [twitter_nlp](https://github.com/aritter/twitter_nlp) to perform Named Entity Recognition in order to find the aspects. Then, we use the sentiment lexicon [sentiwordnet](https://github.com/zeeeyang/lexicon_rnn/tree/master/lexicons) to matching the opinion words.
- For images in MVSA-Multi dataset, we first perform [Faster-RCNN](https://github.com/jiasenlu/bottom-up-attention) to extract the region feature(only retain 36 regions with highest Confidence) as the input feature. Then we use [ANPs extractor](https://github.com/stephen-pilli/DeepSentiBank) to extract the ANPs distribution of each image.
## Data Download
Because the pre-training dataset after processing is very large, so we only provide the downstream datasets. You can download the downstream datasets and our pre-training model via the link [Baidu Netdist](https://pan.baidu.com/s/11INRcFpoBR-6iggukx1VtA) with code:d0tn.
## Downstream Task Training
To Train the downstream JMASA task on two twitter datasets, you can just run the following code. Note that you need to change all the file path in file **src\data\jsons\twitter15_info.json** and **src\data\jsons\twitter17_info.json** to your own path.
```
sh 15_pretrain_full.sh
sh 17_pretrain_full.sh
```
The following is the description of spome parameters of the above shell
```
--dataset           include dataset name and the path of info json file.
--checkpoint_dir    path to save your training model
--log_dir           path to save the training log
--checkpoint        path of the pre-training model
```
We also provide our training logs on two datasets in folder **./log**.  
## Acknowledgements
- Some codes are based on the codes of [BART-MABSA](https://github.com/yhcc/BARTABSA) and [KM-BART](https://github.com/FomalhautB/KM-BART).