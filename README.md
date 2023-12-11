# 🚀 Additional-experiments-of-JIT-Smart


## ⭐ (Reviewer1->Q2)
We froze the entire CodeBERT weight (i.e. without fine-tuning), and the results show that all indicators were much lower than JIT-Smart, which further verified the importance of our fine-tuning.

|  | F1-Score ↑     | AUC ↑      | Recall@20%Effort ↑      |Effort@20%Recall ↓      |Popt ↑      |Top-5 Accuracy ↑      |Top-10 Accuracy ↑      |Recall@20%Effort_l ↑     |Effort@20%Recall_l ↓    |IFA_l ↓    | 
| -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- |
|$$JITSmart_{w/o-fine-tuning-CodeBERT}$$   | 0.109 |  0.733 |  0.6421 |  0.0196 | 0.8313  |  0.4897|  0.3345 | 0.6489  |  0.0802 |  0.6207 |
|$$JITSmart$$   | 0.486 |  0.885 | 0.823  | 0.01  | 0.942  | 0.552 | 0.41  |  0.74 | 0.081  |  0.098 |
> "↑" indicates the larger the better; "↓" indicates the smaller the better.

## ⭐ (Reviewer2->cost issue)
Information about our model size, training, and test costs can be seen in the link. Compared with the best model (i.e. JITFine), the model size, training cost and testing cost of our model are not much different, but our method achieves significant statistical improvement(shown in the results of RQ1, RQ2, and RQ3 in the paper).



|      | Model Size     | Training Time     | Inference Time    | GPU Graphics Card for Training
| -------- | -------- | -------- | -------- | -------- |
| JITFine | 1.39 GB | 1h 46mins|  36s| 1 NVIDIA GeForce RTX 3090 |
| JITSmart | 1.44 GB | 2h 06mins | 40s | 1 NVIDIA GeForce RTX 3090 |
>(Numbers of test examples: 5480)

## ⭐ (Reviewer2->Ablation study of focal loss)
In the experiment, we compared the performance of JIT-Smart and JITFine with or without focal-loss (compared with cross-entropy-loss which is the most common loss in classification tasks). Results show the advantages of focal-loss and JIT-Smart is better than JITFine under any conditions.

|  | F1-Score ↑     | AUC ↑      | Recall@20%Effort ↑      |Effort@20%Recall ↓      |Popt ↑      |Top-5 Accuracy ↑      |Top-10 Accuracy ↑      |Recall@20%Effort_l ↑     |Effort@20%Recall_l ↓    |IFA_l ↓    | 
| -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- | -------- |
|$$JITFine_{cross-entropy-loss}$$   |  0.402| 0.873  |  0.691 |  0.015 |  0.908 | 0.198 |  0.204 |  0.191 | 0.341  |  12.3523 |
|$$JITFine_{focal-loss}$$   | 0.434 |  0.891 |  0.808 |  0.01 | 0.9361  | 0.2298 | 0.2181  |  0.231 |  0.3182 | 11.124  |
|$$JITSmart_{cross-entropy-loss}$$   | 0.465 | 0.875  |  0.787 | 0.011  | 0.9289  | 0.551 | 0.406  |  0.74 | 0.079  |  0.107 |
|$$JITSmart_{focal-loss}$$   | 0.486 |  0.885 | 0.823  | 0.01  | 0.942  | 0.552 | 0.41  |  0.74 | 0.081  |  0.098 |

> "↑" indicates the larger the better; "↓" indicates the smaller the better.




