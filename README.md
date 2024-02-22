### main.py

#### color(message, color='red')

이 함수는 콘솔 출력에 색상을 추가하는데 사용됩니다. 기본적으로 빨간색으로 설정되어 있지만, 'green', 'orange', 'blue' 선택이 가능합니다.

#### main()

이 함수는 프로그램의 주 실행 함수입니다. argparse를 통해 다음의 인자들을 받습니다:

- '--crop': 이 옵션이 활성화되면  crop algorithm을 사용하여 입력 비디오를 자릅니다.
- '--sample': crop 옵션을 활성화했을때 프레임 샘플링 간격을 설정합니다. 기본값은 10입니다.
- '--save': 이 옵션이 활성화되면 자른 비디오 파일을 저장합니다.
- '--mode': 작동 모드를 설정합니다. 'video', 'eval' 중 하나를 선택해야 합니다.
- '--path': 'video' 모드에서 비디오 경로를 설정합니다.

입력받은 인자를 바탕으로 다음의 과정을 수행합니다.

- 'video' 모드가 선택되면, 'path' 인자로 지정된 비디오 경로에서 프레임을 추출합니다. 'path' 인자가 비어 있다면, 에러 메시지를 출력하고 프로그램을 종료합니다.

- 'crop' 옵션이 활성화된 경우, 'Frames Extracting with Crop' 메시지를 출력하고, 'loader.find_crop_area' 함수를 사용하여 비디오에서 자를 영역을 찾습니다. 이 때 'sample' 인자로 지정된 간격으로 프레임을 샘플링합니다. 찾아낸 영역을 기반으로 'loader.get_crop_frames' 함수를 사용하여 비디오를 자르고, 자른 프레임들과 비디오의 초당 프레임 수(fps)를 반환받습니다. 'save' 옵션이 활성화된 경우, 자른 비디오 파일을 저장합니다.

- 'crop' 옵션이 비활성화된 경우, 'Frames Extracting without Crop' 메시지를 출력하고, 'loader.get_frames' 함수를 사용하여 비디오에서 프레임을 추출합니다. 추출된 프레임들과 비디오의 초당 프레임 수(fps)를 반환받습니다.

반환받은 프레임 리스트에서 박수 치기, 머리 흔들기, 앉기/일어서기 동작들을 감지한 합니다.

- '[Hand-Clap Detecting ... ]' 메시지를 출력하고, 'handclap.model' 함수를 사용하여 입력된 프레임 리스트에서 손뼉치는 동작을 감지합니다. 감지 결과는 'handclap_detections'에 저장됩니다.

- '[Head-Banging Detecting ... ]' 메시지를 출력하고, 'headbanging.model' 함수를 사용하여 입력된 프레임 리스트에서 머리를 흔드는 동작을 감지합니다. 감지 결과는 'headbanging_detections'에 저장됩니다.

- '[Sit-Stand Detecting ... ]' 메시지를 출력하고, 'sitstand.model' 함수를 사용하여 입력된 프레임 리스트에서 앉았다 일어서는 동작을 감지합니다. 이 함수는 프레임과 초당 프레임 수(fps)를 인자로 받습니다. 감지 결과는 'sitstand_detections'에 저장됩니다.

감지된 동작들은 통합되어 하나의 데이터프레임으로 만들어지며, './unified.csv'로 저장됩니다.



