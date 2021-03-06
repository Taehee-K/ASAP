# ASAP: AI State Analysis of Pets πΎ
Analysis of Pets Using Keypoint Detection and Skeleton-Based Action Recognition.<br>
(2021.07.05~2021.08.23)

## Overview
ASAP(AI State Analysis of Pets)λ λ°λ €λλ¬Όμ νλμ λΆμν΄μ£Όλ μλΉμ€μλλ€. <br>

λ³Έ νλ‘μ νΈμ λͺ©νλ κ΅­λ΄μμ μμ‘λλ λ€μν κ°μ νμ’μ λν΄ νλμ λΆμνλ λ²μ©μ μΈ λͺ¨λΈμ μ μνκ³ , μ΅μ’μ μΌλ‘ μμ μ λ°λ €λλ¬Όμ λν΄ 10κ°μ§ νλ λΆμμ μ κ³΅νλ μλΉμ€λ₯Ό μ μνλ κ²μλλ€. νλ λΆμμ μν΄μλ λ¨Όμ  λ°λ €λλ¬Όμ μ΄¬μν μμ μ λ°λ €λλ¬Όμ κ΄μ  ν€ν¬μΈνΈλ₯Ό κ²μΆν ν, κ΄μ  ν€ν¬μΈνΈλ₯Ό κΈ°λ°μΌλ‘ νμν λ°λ €λλ¬Όμ λΌλλ₯Ό ν΅ν΄ νλ μ νμ λΆλ₯ν©λλ€.<br>

λ°λ €λλ¬Όμ λ΄μ μμμ μ¬λ¦΄ μ ν€ν¬μΈνΈ μΈμμ κΈ°λ°μΌλ‘ νλμ μλ €μ€λλ€. 

## Data
AI-Hubμμ μ κ³΅νλ [λ°λ €λλ¬Ό κ΅¬λΆμ μν λλ¬Ό μμ](https://aihub.or.kr/aidata/34146) λ°μ΄ν° μ€ κ°(λ°λ €κ²¬)μ λ°μ΄ν°λ§μ μ¬μ©νμ¬ λͺ¨λΈ νμ΅μ μ§ννμμ΅λλ€.<br>

Keypoint Detection λͺ¨λΈ νμ΅μ μμ λ°μ΄ν°(μμμ νλ μ λ³ μ΄λ―Έμ§)λ₯Ό, Action Recognition λͺ¨λΈ νμ΅μ λΌλ²¨ λ°μ΄ν°λ₯Ό μ¬μ©νμμΌλ©° κ° νμ΅ λ°μ΄ν°μ νμμ λ€μκ³Ό κ°μ΅λλ€.
* **Keypoint Detection** <br>
  | Original | Keypoint | Label |
  | :------: | :------: | :---- |
  | <img width="250" alt="data-img" src="https://user-images.githubusercontent.com/63901494/129929470-e2def238-963b-42c8-98b6-59bb0ad3b4c6.jpg"> | <img width="250" alt="data-keypoint" src="https://user-images.githubusercontent.com/63901494/129929529-235d5f39-1ec5-4452-8299-490c84702ebf.png"> | 0: μ½<br>1: μ΄λ§ μ  μ€μ<br>2: μκΌ¬λ¦¬(μλ)<br>3: μλ μμ  μ€μ<br>4: λͺ©<br>5: μλ€λ¦¬ μ€λ₯Έμͺ½ μμ<br>6: μλ€λ¦¬ μΌμͺ½ μμ<br>7: μλ€λ¦¬ μ€λ₯Έμͺ½ λ°λͺ©<br>8: μλ€λ¦¬ μΌμͺ½ λ°λͺ©<br>9: μ€λ₯Έμͺ½ λν΄κ³¨<br>10: μΌμͺ½ λν΄κ³¨<br>11: λ·λ€λ¦¬ μ€λ₯Έμͺ½ λ°λͺ©<br>12: λ·λ€λ¦¬ μΌμͺ½ λ§λͺ©<br>13: κΌ¬λ¦¬ μμ<br>14: κΌ¬λ¦¬ λ |

  ν€ν¬μΈνΈ κ°μ§ λͺ¨λΈ νμ΅μ μν΄μλ ν€ν¬μΈνΈ μ’ν λ°μ΄ν°κ° νμν©λλ€. λ€μκ³Ό κ°μ csv νμΌ νμμΌλ‘ μ΄λ―Έμ§μ κ²½λ‘μ ν€ν¬μΈνΈ μ λ³΄λ₯Ό κ΅¬μ±ν΄ μ£ΌμΈμ. <br>
  <img width="800" alt="data-csv" src="https://user-images.githubusercontent.com/63901494/129934622-ec6e8130-50de-4893-92d6-7d040220cac9.png">

* **Action Recognition** <br>
  νλ λΆλ₯ λͺ¨λΈμ νμ΅μ μν΄μλ ν€ν¬μΈνΈ μ’νκ°κ³Ό κ° ν¬μΈνΈμ λν confidence score, μμμ λΌλ²¨μΈ action class μ λ³΄κ° νμν©λλ€. λ€μκ³Ό κ°μ νμμ json νμΌμ κ° μμμ λν΄ κ΅¬μ±ν΄ μ£ΌμΈμ.
  ```
  {
    "data":[
      {"frame_index":1, "skeleton":[
        {"pose":[x.xxx, x.xxx, x.xxx, ...],   // keypoint
         "score":[x.xxx, x.xxx, x.xxx, ...]   // confidence score
        }]
      },
      {"frame_index":2, "skeleton":[
        {"pose":[x.xxx, x.xxx, x.xxx, ...],
         "score":[x.xxx, x.xxx, x.xxx, ...]
        }]
      },
      ...,]
      "label": "κ±·κ±°λ λ",
      "label_index": 5
    ...
  }
  ```
  μμμ κ° νλ μλ³ μ€μΌλ ν€ μ λ³΄λ‘λΆν° 'μκΈ°', 'λ μλ°μ λ€μ΄ μ¬λ¦Ό', 'μλ° νλλ₯Ό λ€μ΄ μ¬λ¦Ό', 'λͺΈμ ν΄λ€', 'μλλ¦¬κΈ°', 'κ±·κ±°λ λ', 'κΌ¬λ¦¬λ₯Ό μλ‘ μ¬λ¦¬κ³  νλ¦', 'λΉκΈλΉκΈ λλ€', 'λ§μ΄ν', 'κΌ¬λ¦¬κ° μλλ‘ ν₯ν¨' κ³Ό κ°μ νλ λΆλ₯λ₯Ό μ§ννμμ΅λλ€. 

## Models
* [Keypoint Detection] **Keypoint RCNN** - [Mask-RCNN, 2017 (Kaiming He, Georgia Gkioxari, Piotr DollΓ‘r, Ross Girshick)](https://arxiv.org/pdf/1703.06870v3.pdf)
* [Keypoint Detection] **HRNet** - [Deep High-Resolution Representation Learning for Visual Recognition, 2019 (Jingdong Wang, Ke Sun, Tianheng Cheng, Borui Jiang, Chaorui Deng, Yang Zhao, Dong Liu, Yadong Mu, Mingkui Tan, Xinggang Wang, Wenyu Liu, Bin Xiao)](https://arxiv.org/pdf/1908.07919.pdf)
* [Action Recognition] **ST-GCN** - [Spatial Temporal Graph Convolutional Networks for Skeleton-Based Action Recognition, 2018 (Sijie Yan, Yuanjun Xiong, Dahua Lin)](https://arxiv.org/pdf/1801.07455.pdf)

ν΄λΉ λͺ¨λΈλ€μ λͺ¨λ Pytorch νλ μμν¬λ₯Ό μ¬μ©νμ¬ νμ΅νμμ΅λλ€. 

<!--
**Flowchart** <br>
<img width="500" alt="tech stack" src="https://user-images.githubusercontent.com/63901494/129585982-4705c85e-c81b-4b97-87ef-20a37119d999.png"> 
-->

## Usage
νμ΅μ λͺ¨λΈμ μ©λ λ¬Έμ λ‘ μΈν΄ GPU νκ²½μμ μ€ννκΈ°λ₯Ό κΆμ₯ν©λλ€. <br>
Google Colabμ νμ©ν  μ [λ°νμ] - [λ°νμ μ ν λ³κ²½] - [GPU]λ‘ μ€μ μ λ°κΏμ£ΌμΈμ.
### 1. Installation
```
git clone https://github.com/Taehee-K/ASAP.git
cd ASAP
```
### 2. Train
[Keypoint RCNN](./KeypointRCNN)
```
cd KeypointRCNN
pip install -r requirements.txt
python train.py
```
[HRNet](./HRNet)
```
cd HRNet
pip install -r requirements.txt
python train.py
```
[ST-GCN](./ST-GCN)
```
cd ST-GCN
pip install -r requirements.txt
python torchlight/setup.py install
python main.py recognition -c config/st_gcn/kinetics-skeleton/train.yaml --device 0
```
### 3. Inference
```
cd demo
pip install -r requirements.txt
python torchlight/setup.py install

// Test
python test_final.py recognition -c work_dir/stgcn_demo.yaml

// Streamlit Demo
streamlit run app.py
```

## Result
Streamlit λΌμ΄λΈλ¬λ¦¬λ₯Ό ν΅ν΄ μλΉμ€ νλ‘ν νμμ μ μνμμ΅λλ€. <br>

<img width="600" alt="demo-streamlit" src="https://user-images.githubusercontent.com/63901494/130213347-a7735515-7440-4a09-8431-60786c1818ac.gif">

## Reference
* [pytorch/vision](https://github.com/pytorch/vision)
* [yysijie/st-gcn](https://github.com/yysijie/st-gcn)
* [leoxiaobin/deep-high-resolution-net.pytorch](https://github.com/leoxiaobin/deep-high-resolution-net.pytorch)
* [MaiHon/dacon-motion-keypoints](https://github.com/MaiHon/dacon-motion-keypoints)

## Contributors
<table>
  <tr>
    <td align="center"><a href="https://github.com/Taehee-K"><img src="https://user-images.githubusercontent.com/63901494/129619988-1a959834-313c-443c-84c2-4fc2db8ef8f6.jpg" width="100" height="100"><br /><sub><b>κΉνν¬</b></sub></td>
    <td align="center"><a href="https://github.com/wonjae-yang"><img src="https://user-images.githubusercontent.com/63901494/129583717-42d19759-7586-4de0-aea9-5e935295f4dd.png" width="100" height="100"><br /><sub><b>μμμ¬</b></sub></td>
    <td align="center"><a href="https://github.com/SK-jeong"><img src="https://user-images.githubusercontent.com/63901494/129582209-1d1d194e-cf3e-48d6-b097-35a7b855a683.jpg" width="100" height="100"><br /><sub><b>μ μ±κ²½</b></sub></td>
    <td align="center"><a href="https://github.com/miso-choi"><img src="https://user-images.githubusercontent.com/78155086/132087934-79862c4f-7076-4e2c-907b-a456d6980b90.jpeg" width="100" height="100"><br /><sub><b>μ΅λ―Έμ</b></sub></td>
    <td align="center"><a href="https://github.com/HwangChaewon"><img src="https://user-images.githubusercontent.com/63901494/129582279-430df734-43ae-451a-991d-7bb62a170eb0.png" width="100" height="100"><br /><sub><b>ν©μ±μ</b></sub></td>
    <td align="center"><a href="https://github.com/HyeJung-Hwang"><img src="https://user-images.githubusercontent.com/63901494/129582233-ccf2137f-89db-4559-9bc3-be23a133e2a3.png" width="100" height="100"><br /><sub><b>ν©νμ </b></sub></td>
  </tr>
</table>
