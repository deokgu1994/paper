## Bag of Tricks for Image Classification with Convolutional Neural Networks
### Paper [Link](https://arxiv.org/pdf/1812.01187.pdf)
___
<br><br>

# start
[@https://openaccess.thecvf.com/content_CVPR_2019/papers/He_Bag_of_Tricks_for_Image_Classification_with_Convolutional_Neural_Networks_CVPR_2019_paper.pdf]



나동빈 <꼼꼼한 논문 읽기 - Bag of Tricks for Image Classification with Convolutional Neural Networks (CVPR 2019)>

- 모델 아키텍쳐의 선능 향상이 아닌 그외에 다른 파라미터를 변경해서 성능향상이 있다.

Algorithm 1:
 전체 이미지에서 batch사이즈 만큼 나누어서 학습하는 방법.
 
 일반적으로 train에서 rand aug를 사용하지 않는다.
 
 NAG (Optimizer)
 

1. efficient Training
    더욱 빠르게, batch size를 더욱 더 크게 작용했다.
 
    1) Large-batch training: 그만큼 사이즈를 키워서 사용했다.
        A. Linear scalling learning rate: learning rate를 키워서 사용한다.
        B. Learning rate warmup: 처움부터 큰 lr을 사용할때 불안정함, 천천히 감소하면서 증가한다.
        C. Zero y(감마):
        D. No dias decay: weight decay는 모든 decay를 향상,
    2) Low-precision training
    3) Experiment Results

2. Model Tweaks
    모델을 조금 변경했음에도 무시 못할정도로 증가했다.


3. Training Refinements
    1) Cosine Learning Rate Decay: 곡선을 따라서 매 스텝마다 천천히 증가를 함으로 곡선형의 선을 만든다.
    2) Label Smoothing: softmax,
    3) Knowledge Distillation: 서로다른 모델일때 좋은 성능이 나온다.
    4) Mixup Training: 많은 epoch의 값을 필요로 함.
    
4. Transfer Learning
    1) Object Detection
    2) Semantic Segmentation: 각각의 pix 레벨로 이미지를 확인한다. 


