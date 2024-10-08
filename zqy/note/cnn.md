# 论文阅读

## Classification of Brain Disorders in rs-fMRI via Local-to-Global Graph Neural Networks

<https://ieeexplore.ieee.org/document/9936686/authors#authors>

[](../reading/Classification_of_Brain_Disorders_in_rs-fMRI_via_Local-to-Global_Graph_Neural_Networks.pdf)

# Brain MRI Analysis for Alzheimer’s Disease Diagnosis Using CNN-Based Feature Extraction and Machine Learning

<https://www.proquest.com/docview/2653031657?accountid=16210&sourcetype=Scholarly%20Journals>

MRI图进行cnn

# A CNN based framework for classification of Alzheimer’s disease

<https://link.springer.com/article/10.1007/s00521-021-05799-w>

用MRI图， 创新点是

- Applying adaptive thresholding in the second layer.
- Performing data augmentation in the second layer. 这个就是把图像反转，旋转同一个图，得到很多图(看可不可以用满足旋转不变性的模型，如Oriented R-CNN做， convolution本身有平移不变性)
- Initializing the network weights using Glorot Uniform weight initializer in the fifth layer.

