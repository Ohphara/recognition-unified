### main.py

#### color(message, color='red')

이 함수는 콘솔 출력에 색상을 추가하는데 사용됩니다. 기본적으로 빨간색으로 설정되어 있지만, 'green', 'orange', 'blue' 선택이 가능합니다.

#### main()

이 함수는 프로그램의 주 실행 함수입니다. 다음의 인자들을 받습니다:

- '--crop': 이 옵션이 활성화되면 입력 비디오를 자릅니다.
- '--sample': 비디오를 자를 때 프레임 샘플링 간격을 설정합니다. 기본값은 10입니다.
- '--save': 이 옵션이 활성화되면 자른 비디오 파일을 저장합니다.
- '--mode': 작동 모드를 설정합니다. 'video', 'eval' 중 하나를 선택해야 합니다.
- '--path': 'video' 모드에서 비디오 경로를 설정합니다.

이 함수는 'video' 모드에서 비디오에서 프레임을 추출하고, 특정 동작들을 감지한 후, 감지된 동작들을 통합합니다.

- 'Hand-Clap' : 손뼉치는 동작을 감지합니다.
- 'Head-Banging' : 머리를 흔드는 동작을 감지합니다.
- 'Sit-Stand' : 앉았다 일어서는 동작을 감지합니다.

감지된 동작들은 통합되어 하나의 데이터프레임으로 만들어지며, './unified.csv'로 저장됩니다.



