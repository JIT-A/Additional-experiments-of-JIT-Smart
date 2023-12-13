# 🚀 Additional-experiments-of-JIT-Smart


## ⭐ (Reviewer1->Q2)
**Q: How does the model perform without any fine-tuning (e.g., with CodeBERT embedding)?**    

A: We freeze the entire CodeBERT weight (i.e. without fine-tuning), and all indicators are much lower than JIT-Smart. For example, model without fine-tuning achives the F1 of 0.109, which is 345.87% lower than JIT-Smart(F1 of 0.486). The results verified the importance of our fine-tuning.

|  | F1-Score ↑     | AUC ↑      | Recall@20%Effort ↑      |Effort@20%Recall ↓      |Popt ↑      |Top-5 Accuracy ↑      |Top-10 Accuracy ↑      |Recall@20%Effort_l ↑     |Effort@20%Recall_l ↓    |IFA_l ↓    | 
| -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- |
|$$JITSmart_{w/o-fine-tuning-CodeBERT}$$   | 0.109 |  0.733 |  0.6421 |  0.0196 | 0.8313  |  0.4897|  0.3345 | 0.6489  |  0.0802 |  0.6207 |
|$$JITSmart$$   | 0.486 |  0.885 | 0.823  | 0.01  | 0.942  | 0.552 | 0.41  |  0.74 | 0.081  |  0.098 |
> "↑" indicates the larger the better; "↓" indicates the smaller the better.

## ⭐ (Reviewer2->cost issue)
**Q: Cost issue: The questions here are, thereby, what are the costs associated with model training and prediction and localization, how much does data preprocessing cost, and how feasible is the approach?** 

A: Information about our model size, training and test costs can be seen in the link. Compared with the best model (i.e. JITFine), the model size, training cost and testing cost of our model are not much different, but our method achieves statistically significant improvement (shown in the results of RQ1, RQ2, and RQ3 in the paper). For example, in terms of the inference time of testset(5450 samples), JIT-Smart is 40s and JITFine is 36, but JIT-Smart perfoms more stably and statistically better than JITFine, such as improving JITFine by 19.89% and 174.79% in terms of F1 and Top-10 accuracy.



|      | Model Size     | Training Time     | Inference Time    | GPU Graphics Card for Training
| -------- | -------- | -------- | -------- | -------- |
| JITFine | 1.39 GB | 1h 46mins|  36s| 1 NVIDIA GeForce RTX 3090 |
| JITSmart | 1.44 GB | 2h 06mins | 40s | 1 NVIDIA GeForce RTX 3090 |
>(Numbers of test examples: 5480)

## ⭐ (Reviewer2->Ablation study of focal loss)
**Q: Since the primary focus of the paper is on the Defect Localization Model (DLN) and the simultaneous training of prediction and localization models, it is crucial to investigate the impact of the focal loss function on the performance to avoid making a wrong conclusion. For instance, it would be interesting to compare the performance of JIT-Smart with and without the focal loss function or modify
the baselines to incorporate the focal loss function instead of data sampling as a means to mitigate class imbalance.**  

A: We compared the performance of JIT-Smart and JITFine with or without focal-loss . Results show the advantages of JIT-Smart with focal-loss is better than JITFine under all tested conditions. For exmaple, focal-loss improved JITFine and JIT-Smart by 7.96% and 4.52% in terms of F1.


|  | F1-Score ↑     | AUC ↑      | Recall@20%Effort ↑      |Effort@20%Recall ↓      |Popt ↑      |Top-5 Accuracy ↑      |Top-10 Accuracy ↑      |Recall@20%Effort_l ↑     |Effort@20%Recall_l ↓    |IFA_l ↓    | 
| -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- |
|$$JITFine_{cross-entropy-loss}$$   |  0.402| 0.873  |  0.691 |  0.015 |  0.908 | 0.198 |  0.204 |  0.191 | 0.341  |  12.3523 |
|$$JITFine_{focal-loss}$$   | 0.434 |  0.891 |  0.808 |  0.01 | 0.9361  | 0.2298 | 0.2181  |  0.231 |  0.3182 | 11.124  |
|$$JITSmart_{cross-entropy-loss}$$   | 0.465 | 0.875  |  0.787 | 0.011  | 0.9289  | 0.551 | 0.406  |  0.74 | 0.079  |  0.107 |
|$$JITSmart_{focal-loss}$$   | 0.486 |  0.885 | 0.823  | 0.01  | 0.942  | 0.552 | 0.41  |  0.74 | 0.081  |  0.098 |

> "↑" indicates the larger the better; "↓" indicates the smaller the better.  





