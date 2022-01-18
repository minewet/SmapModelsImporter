# SmapModelsImporter
blender addon to import models from s-map(provided by Seoul)

https://github.com/eliemichel/MapsModelsImporter 의 코드를 수정해서 만들었음. 이 사람이 원작자임.
https://github.com/minostauros/MapsModelsImporter/tree/seoulmap 코드도 참고함 (s-map용으로 작성되었으나, 불러올 수 없었음)
구글맵, 구글 어스, MAPY CZ에는 적용 안됨. S-Map(서울시 제공)에만 적용됨.

위 파일을 Blender에서 addon으로 불러오고
Renderdoc을 이용하여 S-MAP 캡쳐, .rdc파일 만들고 blender에서 import
https://github.com/eliemichel/MapsModelsImporter 과 동일하므로 자세한 사항은 참고바람.

## 필수 조건
Renderdoc v1.9
Blender v2.83

S-MAP - 2022.01.18 기준 renderdoc으로 캡쳐했을 때 Renderdoc 상에서 다음과 같이 그려짐
```
- Event Viewer창에서 DrawIndexed() event를 확인했을 때 texture viewer 상에서 지형 -> 건물 순서대로 그림
 * 지형은 mesh viewer에서 대개 납작한 정사각형 모양이며, 건물은 mesh viewer에서 캡쳐한 곳에 있는 건물 모양임
- mesh viewer로 확인했을 때 VSInput이 다음과 같아야 함
 * 지형은 TEXCOORD0(2개 데이터), TEXCOORD1(4개 데이터)
 * 건물은 TEXCOORD0(2개 데이터), TEXCOORD1(1개 데이터), TEXCOORD2(1개 데이터) 

```
TEXCOORD가 아니라 다른 이름으로 나오는 거라면 괜찮으나, 순서대로 데이터 개수가 다를 경우 오류가 날 것임.


