# 1. Human Pose Estimation
Human pose estimation은 크게 2D와 3D로 나뉘는데 2D HPE는 2D 이미지에서 (x,y)같은 2차원 좌표들을 찾아내며 3D HPE는 (x,y,z)와 같은 3차원 좌표들을 찾아내는 기술이다. 사람의 몸은 3D 환경에서 나타내기에 제약이 있기 때문에 2D에서 3D 이미지로 복원을 한다.
이는 face landmark와 비슷하지만 face landmark는 물리적으로 거의 고정되어 있는 반면 human pose는 팔, 다리가 상대적으로 넓은 범위와 자유도를 갖는다는 차이가 있다. 자유도가 높기 때문에 데이터 분포를 특정하기 어려우며 학습에 굉장히 많은 데이터가 필요하고 복잡한 모델을 사용해야 한다. 

# 2. Human keypoint detection
HPE는 사람의 관절인 keypoint를 찾고 keypoint의 localization 문제를 푸는 것이다. 사람의 관절을 찾아 pose를 찾는 방법으로는 Top-down 방법과 Bottom-up 방법이 있다.
  1) Top-down 방법
    - 모든 사람의 keypoint를 정확하게 찾기 위해 object detection을 사용한다. detection한 이미지를 crop하여 검출한 객체 내에서 keypoint를 찾아내는 방법으로 detector가 선행되어야 하며 모든 사람마다 알고리즘이 적용되어야 하기 때문에 사람의 수가 많을 땐 다소 느리다는 단점이 있다.

  2) Bottom-up 방법
    - detector가 없으며 사람의 관절인 keypoint를 먼저 검출한 후에 해당 포인트들을 연결하여 자세를 추정하는 방법이다. 각 키 포인트들의 연결 가지수가 굉장히 많이 때문에 계산량이 많고 Top-down 방법에 비해 keypoint 검출 범위가 넓어서 성능이 떨어진다는 단점이 있다.