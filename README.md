# Visual-SLAM
https://jjuke-brain.tistory.com/entry/Introduction-to-Visual-SLAM-SLAM-%EA%B0%9C%EC%9A%94
SLAM 설명
SLAM - Simultaneous Localization and Mapping, 동시적 위치추정 및 지도작성
●Visual SLAM: 카메라를 이용해서 SLAM
●단안, 스테레오, 뎁스 카메라를 사용
●Visual SLAM의 프레임워크 : Sensor input -> Visual odometry -> Backend optimaization -> Mapping 
                                                                 -> Loop closing   ->
●Visual Odometry(front end): 인접한 시점에서 이미지를 이용해서 카메라의 움직임을 예측
카메라의 회전 및 이동을 계산해야함
VO만 이용하면 drift error가 발생 
●drift error: 한바퀴돌아서 원래 자리왔는데도 같은 위치가 아니라고 판단, 루프클로징이 안되는 에러
●Backend optimaization: 센서에서 발생하는 노이즈 제거, drift error 제거, 칼만필터이용, 비선형 최적화 기반 사용
●Loop closure detection: 현재 위치가 이전에 방문한 곳인지를 판단, 이미지 간의 유사성을 판단
●Mapping: 포인트클라우드, Voxel 등으로 맵을 만듬, 응용 프로그램에 따라 다르게 구현(Sparse, dense, semi-dense map
------------------------------------------------------------------------------------------------------------------------------------
[23-09-06]
●SVO: Fast Semi-Direct Monocular Visual Odometry
논문 url: https://rpg.ifi.uzh.ch/docs/ICRA14_Forster.pdf
깃허브: https://github.com/uzh-rpg/rpg_svo.git 
●입문 VIsual SLAM 14강 번역 Ebook 
https://www.cv-learn.com/20210123-slam-book-translation/
https://github.com/gaoxiang12/slambook
●VIual Motion Estimation Methods
a)Feature-based Methods: SIFT로 특직정 추출, epipolar geometry로 카메라 자세를 추정,
reprojection error minimization으로 자세 개선
●SIFT(scale-Invariant-Feature transform): 이미지 크기, 회전에 불변하는 특징점을 추출하는 알고리즘
b)Direct Methods: intensity values in the image에서 직접 구한다는데 뭔 소리진 모르겠다
●PTAM(Parrel Tracking and Mapping): 키프레임을 이용한 V-SLAM,
tracking은 모든 프레임에서 진행하고, mapping은 주요 키프레임에만 적용해서 속도 높임(병렬)
최근의 monocular 알고리즘은 대부분 PTAM을 사용함
●키프레임: 비디오를 압축할 때 전체 이미지가 저장되는 프레임, 비디오의 모든 장면을 저장하면 용량이 너무 커지기 때문에
일정 시간 간격으로 전체이미지를 저장하고 그 사이는 변화된 값만 저장하는데 전체이미지를 저장하는 프레임을 
키프레임이라고 한다. 



그리고 Datasets으로는 [ UZH-FPV Drone Racing / RPG-event / Zurich Urban MAV / EuRoc / Solar-UAV / ASRL-Kagara-airborn ] 등이 있는데, Visual SLAM 의 테스트에는 EuRoc가 자주 사용됩니다. 아마 IMU, mono, stereo 정보 모두 가지고 있기 때문으로 보입니다.
"A Benchmark Comparison of Monocular Visual-Inertial Odometry Algorithms for Flying Robots" 논문을 참고하시면 드론에 어떠한 SLAM 방식을 적용해야 적합할지 결정하는데 도움이 되실 것 같습니다.
