# Unity_Project
Unity_Project on 2023 Summer Vacation.

## Unity 설치하기

[Unity Korea](https://unity.com/kr/download)
```
Windows 운영체제에 맞는 Unity를 다운
Personal(무료) 버전 2019.1.10f1, Unity Hub 2.0.4
```
## 씬에 물체 배치하기

![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/90c85383-7bb4-4a70-bfc5-c79773422621)
```
GameObject -> 3D Object -> Plane(평면), Cube(정육면체) 작성
```
## 시점 기본 조작
```
이동 : Ctrl + Alt 누르고 마우스 클릭&드래그
회전 : Alt 누르고 클릭&드래그
확대 및 축소 : 마우스 휠 스크롤 조작
```
## 컴포넌트 추가하기
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/b3c8982e-62fb-4981-9de9-2c8fa991c38a)
```
3D Object의 Capsule을 생성, 선택하고 compononent 탭에서 add를 누른다음
rigidbody 컴포넌트를 선택합니다.

재생 버튼을 누르면 캡슐이 중력을 받아 떨어지면서 지면과 충돌합니다.

rigidbody 컴포넌트 외에도 대표적인 컴포넌트들을 학습하였습니다.

Transform 컴포넌트 : 씬에서의 위치, 회전 스케일의 상태
Collider 컴포넌트, Mesh Filter 컴포넌트, Renderer/Mesh Renderer 컴포넌트, Camera컴포넌트
Light 컴포넌트, Audio Listener 컴포넌트, Audio Source 컴포넌트, Script 컴포넌트 등
다양한 컴포넌트가 있습니다.
```
## 프로젝트에 필요한 에셋 추가하기
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/c279690c-2e94-4914-bcfc-2fa7c4093058)
```
에셋스토어에서 다양한 에셋들을 선택 및 다운로드 하고 프로젝트에 import 하는 방법을 알아보았습니다.

VR Shooting 파일 밑으로 음성 관련한 에셋 Audio와 게임 오브젝트의 템플릿에 해당하는 Prefabs 파일
오브젝트의 표면 색상이나 요철 등의 외관의 표현을 목적으로 한 Textures 파일
오브젝트를 그릴 때의 렌더링 방법을 표현하는 Material 파일
캐릭터나 배경의 모델 데이터 Models 파일

크게 총 5종류의 에셋 파일을 프로젝트에 추가하였습니다.
```
## 지면 에셋을 프로젝트에 배치하기
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/562a8ea1-a9f2-4925-a681-af815639832c)
```
에셋 스토어에서 임포트한 에셋은 씬 뷰 또는 하이어라키 창에 드래그 앤 드롭하여 씬에 배치할 수 있습니다.

씬에 배치하고 Position을 수정(0, 25, 0)하였습니다.
```
## 카메라의 이동
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/3e2bc9e9-989d-485e-b5f3-ade1e9b1c7b4)
```
FPS 게임에서는 플레이어 캐릭터에서 본 시야가 화면에 비춰집니다. 따라서 카메라의 위치를 변경해
플레이어가 가지고 있는 무기가 보이도록 설정합니다.

Main Camera의 위치를 수정(0, 1.6, 0)합니다.
```
## PlayerGun 오브젝트 배치
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/cfb1c68b-6a38-43cb-a866-e79262b3e20a)
```
PlayerGun asset을 Main Camera의 자식 요소로 추가합니다.
PlayerGun asset의 position이 부모(Main Camera)의 position(0, 1.6, 0)을 상속받습니다. 
```
## 오브젝트 비활성화
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/9d1b48d5-7c2f-4d1d-bae7-b1c43e4006a5)
```
PlayerGun의 자식 요소인 Player를 선택하고 inspector 창에서 비활성화(오브젝트 명 옆 체크 해제)하면 총만 표시됩니다. 
```
## PlayGun의 이동
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/1c07e98d-5c6d-4118-8202-c40c05179694)
```
Game 뷰에서 총의 끝이 조금 보이는 듯한 시야로 설정하기 위해 PlayGun 오브젝트의 위치를 수정(-0.25, -0.7, 0.6)합니다.

게임 뷰에서 오브젝트의 위치를 봐가면서 수정함 
```
## 카메라를 회전시키는 C# 스크립트(CameraRotator.cs)의 작성
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/2c6f268f-344d-473e-a847-82608beeb887)
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/846af699-1537-4a0b-8ce7-6201096b201b)
```
오브젝트의 동작은 오브젝트에 적용된 컴포넌트에 의해 제어됩니다.
유니티는 다양한 컴포넌트를 제공하지만 이것만으로는 오브젝트를 생각한대로 제어할 수 없습니다.

따라서 유니티에서는 C# 스크립트를 기술하여 자체 기능을 가진 컴포넌트를 작성할 수 있습니다.
작성한 컴포넌트를 오브젝트에 추가하기만 하면 C# 스크립트에 기술된 대로 오브젝트가 동작되게 할 수 있습니다.

여기서는 Main Camera를 회전하는 C# 스크립트를 작성한 후 생성된 컴포넌트(CameraRotator.cs)를 Main Camera에 추가하였습니다.
```
## [C#] CameraRotator 스크립트 분석
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/482b3bbf-b35d-4d11-a517-2458f99867f8)
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/dc14059c-55bd-42dd-8df8-53cbf0e25cd4)
```
CameraRotator 클래스는 유니티가 제공하는 클래스인 MonoBehaviour 클래스를 상속받고 있으며 
MonoBehaviour 클래스의 멤버 변수인 이벤트 함수들을 구현하여 컴포넌트의 기능을 구현할 수 있게 되었습니다.

public 또는 [SerializeField] 속성이 붙은 멤버 변수(angularVelocity)는 유니티의 인스펙터 창에서 설정을 변경할 수 있습니다.
여기에서 정의한 angularVelocity가 인스펙터 창에서 [Angular Velocity]라는 이름의 프로퍼티로 표시되고 그 초깃값은 30f라는 
것을 알 수 있습니다. horizontalAngle과 verticalAngle은 회전량을 저장하기 위한 변수로 사용합니다.
```
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/8fb9b7d2-13f3-4e7e-8d24-6301c1618fff)
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/1a14da0b-e07d-436f-9fe1-7b285fceea23)
```
# if UNITY_EDITOR #endif 블록은 C#의 프리프로세스라는 것을 이용한 기술로, 이렇게 적어두면 둘러싸인 범위가 유니티 에디터에서만 유효
즉 휴대 단말에서 확인 시에는 무효되게 됩니다. 이는 휴대 단말에서 확인할 때 카메라의 제어를 VR 기능이 맡게 되기 때문에 
처리가 충돌되지 않게 한다는 의미가 있습니다.
```
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/9f311228-a92d-4ac3-9cbd-b3be55e05371)
```
Update 함수의 내부 로직의 첫 부분에서 키보드 입력을 통해 회전 속도와 프레임의 시간으로부터 회전량을 계산합니다.

horizontal (수평), vertical (수직) 두 축이 있으며 Input.GetAxis("horizontal or vertical")을 사용하여
화살표의 키 입력에 응해 -1부터 1의 값을 얻을 수 있습니다.

수평 : 왼쪽이 -1 오른쪽이 1 , 수직 : 아래쪽이 -1 위쪽이 1

Time.deltaTime은 앞 프레임으로부터의 경과 시간을 반환합니다. 이것을 회전 속도와 곱해서 회전량을 얻을 수 있습니다.

수직방향의 회전값 veritcal을 마이너스로 하는 것은 입력과 회전 방향을 맞추기 위함입니다.
(x축으로의 회전은 아래로 향하는 것이 정방향이기 때문에 입력을 반전시키기 위해 마이너스 값으로 변환)
```
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/c55c88fa-83e3-434c-a4cf-7e157c82438f)
```
입력에 따른 각 방향의 회전량을 얻은 다음 지금까지의 회전값에 그 값을 더합니다.

수직 방향으로 90도를 넘으면 좋지 않기 때문에 80도 이상이 되지 않도록 처리합니다.
Matf.Clamp는 값을 범위 내로 넣는 처리입니다.

마지막으로 회전량을 게임 오브젝트에 반영하고 있습니다.

MonoBehaviour의 transform 프로퍼티에서 'Transform' 컴포넌트를 취득하고 rotation에 회전 각도에 해당하는 쿼터니언을 설정합니다.
여기서는 Quaternion.Euler에 의한 오일러 각을 사용합니다. 
Transform 컴포넌트를 이용하여 스크립트로부터 게임 오브젝트의 위치나 회전을 갱신해서 움직일 수 있습니다.
```
## 총알 생성하기
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/bbc1b682-a5fa-479a-9c9d-825720e05c02)
```
3d object의 Sphere로 구를 생성한 후 이름을 Bullet으로 변경합니다.

오브젝트의 크기(scale)을 0.05, 0.05, 0.05로 수정합니다.
```
## 총알 Object를 프리팹화하기 (Prefab)
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/9c471bac-4eaa-4e29-a249-2b824b61ae1d)
```
프리팹은 게임 오프젝트의 템플릿에 해당하는 에셋입니다. 게임 중에 몇 번 나올 것 같은 게임 오브젝트를 
프리팹화해 두면 프리팹을 바탕으로 간단하게 게임 오브젝트를 씬상에 여러 개 계속 생성할 수 있습니다.

하이어라키 창의 Bullet을 프로젝트 창의 'Assets/VRShooting/Prefabs' 경로에 드래그 앤 드롭하여 
프리팹화 합니다.
```
## 총알을 발사하는 Shooter C# Script 작성
![image](https://github.com/chihyeonWON/Unity_VR/assets/58906858/63926e6a-8864-4801-aead-93ac954f1f36)
```
총알의 프리팹(GameObject형)와 총구의 Transform을 변수로 정의합니다.
게임 오브젝트와 컴포넌트의 형도 [SerializeField]로 지정하여 인스펙터 창에서 설정하게 할 수 있습니다.

Update 함수에서는 입력에 따라 Shoot 함수를 호출합니다. Input.GetButtonDown은 지정된 버튼이
눌린 순간에 true를 돌려주는 함수입니다. 또한 "Fire1"이라는 버튼명은 기본값으로 정의된 것으로,
마우스 왼쪽 버튼이나 왼쪽 I키의 입력을 받을 수 있습니다.

총알을 발사하는 Shoot함수안의 Instantiate 함수는 게임 오브젝트를 복사하는 함수로 첫 번째 인자로는 
복제할 프리팹을 두 번째 인자로는 총구의 위치(gunBarrelEnd.position)와 총구의 방향(gunBarrelEnd.rotation)을 지정해
총알을 생성하게끔 지정하였습니다.
```