## Annotation 관련 매뉴얼
- Multi Class Object Detection 모델 학습을 위해서는 <br> 학습 영상 및 해당 영상 내 객체에 대한 bounding box 정보와 class 정보가 필요합니다. 
- 데이터에 모델 학습에 사용할 label 정보를 추가하는 행위를 annotation이라고 하며 <br> 아래 글은 LabelImage Tool을 통해 annotation 하는 방법이 작성되어 있습니다.

## LabelImage Tool 활용
1. 먼저 해당 [링크](https://drive.google.com/uc?id=1cTv2dx52tXmLw0R8xFIQ4_uWD2bJQeBA&export=download)를 클릭하여 LabelImage Tool 프로그램을 다운받습니다.
   - 참고로 링크를 통해 제공된 Tool은 Window용이기 때문에 MacOS 혹은 Linux를 활용하시는 분들이라면 실행이 안될 수 있습니다. (테스트를 하지 못함.) 
    -  최대한 Window 환경을 활용해주시거나 LabelImage [공식 홈페이지](https://github.com/heartexlabs/labelImg)를 참고하셔서 본인의 환경에 맞게 프로그램을 실행시켜주세요.
 
2. 다운받은 압축 파일의 압축을 해제하면 다음과 같은 경로로 폴더들이 구성되어 있습니다.
```
LabelImage_for_window
|── windows_v1.6.0
|     |─data
|     |   |─predefined_classes.txt
|     |
|     |─labelImg.exe
```
   - 여기서 먼저 data 폴더 안에 predefined_classes.txt는 labelImg Tool에서 bounding box의 class를 지정해줄 때 활용되는 class category를 의미합니다.
   - 현재 다운받은 폴더 속 txt 파일 안에는 dog, person, cat 등 15개의 class가 명시되어있으며, 본인의 검출기가 학습시킬 class에 맞게 내용을 변경해주면 됩니다.
   - 해당 예제에서는 페트병과 알루미늄 캔에 대한 간단한 검출기를 학습시킬 것이기에, 카테고리를 pet와 aluminum_can으로 변경하였습니다.

![image](https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image1.png)



3. 올바르게 저장을 했다면 labelImg.exe 파일을 실행시킵니다.
   - labelImg 프로그램을 실행시켰다면 아래와 같은 UI가 나타나게 됩니다. 각 버튼의 기능은 다음과 같습니다.
   
![image](https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image2.png)

4. 영상을 읽어온 후 annotation 과정을 수행합니다. (아래 그림 참고)
     - 경로에 한글이 포함된 경우 데이터 읽어오는 과정이 수행되지 않을 수 있습니다.
     - 경로를 영어로 지정해주세요.

![image]((https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image3.png)


5. Drag 하여 Bounding Box를 선택하면 아래 그림과 같이 작은 창이 뜨게됩니다. <br> 해당 창은 방금 친 box에 대하여 class label을 부여하는 것으로, 2번 단계에서  txt 파일에 카테고리를 어떻게 설정했느냐에 따라서 보여지는 것이 달라집니다.
![image]((https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image4.png)

6. Save 버튼을 눌러 annotation 정보를 저장합니다.
![image]((https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image5.png)

- 한 장의 영상에 대해 annotation 수행 후 save 버튼을 누르고 다음 영상으로 넘어갑니다. 

7. 5~6 과정을 train image 전체에 대해서 반복적으로 수행하여 annotation을 모두 마무리합니다.
![image]((https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image6.png)

8. 이후 제공해드린 [ROS2_Detection_Code](https://kaggle.com/datasets/ec2b4415401c4c9a560ee5e32b3e24d4c0900b497b7a37af086eeb92384f89d4) 에 직접 취득 및 annotation한 train_image를 업로드 후, 모델을 학습시켜 최종 checkpoint 파일을 생성하시면 됩니다.  업로드 과정은 아래와 같습니다.

![image]((https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image7.png)

----
-  한가지 팁을 드리면 labelImg에는 단축키가 존재합니다. 이는 아래와 같습니다.
![image]((https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image8.png)

- 또한 save 버튼을 매번 누르지 않고 자동으로 저장하는 기능을 키기 위해서는 좌측 상단 View - Auto Saving 항목을 체크해주시면 됩니다.
![image]((https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image9.png)

- 만약 에러가 발생하신다면, 좌측 상단의 ResetALL 버튼을 클릭한 후 다시 tool을 실행해보세요.
![image]((https://github.com/sejongresearch/2024.DeepLearningSystem/blob/main/images/image10.png)
