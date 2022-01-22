# SmapModelsImporter
Blender addon to import models(building/terrain) from S-MAP: http://smap.seoul.go.kr/

## Original Code
https://github.com/eliemichel/MapsModelsImporter 의 코드를 참고 및 수정해서 만들었음. (구글맵, 구글어스 등에 적용)

+) https://github.com/minostauros/MapsModelsImporter/tree/seoulmap 코드도 참고함 <br>(s-map용으로 작성되었으나, 내 컴퓨터에서는 불러올 수 없었음)<br>


## Info
S-Map에만 적용됨. 구글맵, 구글 어스 등 다 적용 안됨<br>
<br>
__사용방법__
1. 사용 방법은 위 파일을 Blender에서 addon으로 불러옴 (Zip파일로)
2. Renderdoc을 이용하여 Chrome으로 S-MAP 캡쳐, .rdc파일 생성
3. blender에서 .rdc파일 import

https://github.com/eliemichel/MapsModelsImporter 과 동일하므로 자세한 사항은 참고 바람.<br>
! top-view로 움직이면서 캡쳐하지 않으면 지형 및 텍스쳐 맵핑이 이상하게 되는 오류가 있음. 주의
! z축 스케일링을 상수로 했는데 캡쳐마다 알맞는 경우도 있고 안맞는 경우도 있어서.. S-MAP과 비교하여 z축 스케일 조정 필요 

## Environment
! 다른 환경에서는 잘 작동하지 않을 수 있음

Renderdoc v1.9 (필수)<br>
Blender v2.83 (필수 - LTS는 안되는듯) <br>
Win64 Chrome
NVDIA Geforce mx150<br>

S-MAP - 2022.01.21 기준 renderdoc으로 캡쳐했을 때 Renderdoc 상에서 다음과 같이 그려지는 것으로 확인
```
* 지형-> 건물 순서대로 그림 (drawIndexed event)
 - 지형은 VSInput에서는 납작한 정사각형(x,y) 모양이나, vs[0]의 텍스쳐의 rgba로부터 각 vertex에 height(z)값을 부여
 - 건물은 건물 모음 그대로 VSInput으로 주어짐

* mesh viewer로 확인했을 때 VSInput이 다음과 같음
 - 지형은 TEXCOORD0(2개 데이터), TEXCOORD1(4개 데이터) (= x,y position 및 uv map / ???)
 - 건물은 TEXCOORD0(4개 데이터), TEXCOORD1(1개 데이터), TEXCOORD2(1개 데이터) (= x,y,z,w position / u / v map)

```
Mesh viewer상의 데이터 개수가 다를 경우 적용 불가.


## preview
![ewha](https://user-images.githubusercontent.com/71055964/150625647-12d6eada-d240-4850-8118-c47896faa739.png)
![광화문](https://user-images.githubusercontent.com/71055964/150625645-37dc811a-4d8b-4ae4-8a1a-bc45ea5728a3.png)
![peace](https://user-images.githubusercontent.com/71055964/150625643-025d121a-8c33-4317-9642-8ce92c11a7c0.png)
