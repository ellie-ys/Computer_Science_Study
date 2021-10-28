## Graph 정의

-   '정점의 모음'과 이 정점을 잇는 '간선의 모음'과의 결합입니다. 즉 연결의 집합을 모형화 한것.
-   수학적인 표현으로는 "정접의 집합을 V, 간선의 집합을 E, 그리고 그래프를 G라고 했을 때 G = (V,E)이다."
-   정점 몇 개 자체로는 아무것도 아니지만 이들이 간선으로 인해 서로 연결될 때는 '관계'가 형성되고 이로 인해 그래프가 형성됩니다.

## Graph의 중요성

-   위대한 수학자 오일러가 17세기에 개발한 이래, 그래프는 수많은 분야에서 도구로 사용되어 왔습니다.
-   서울 시청에서 버스노선을 정리할 때, 건축회사에서 시공 일정 계획을 할 때, 네이베기션이 경로를 탐색할 때 등 그래프의 응용 분야는 굉장히 다양합니다. 게다가 거의 모든 분야가 컴퓨터에 의존하고 있는 상황에서 프로그래머는 그래프를 반드시 이해해야 합니다.

## Graph 표현방법의 생각 과정

-   그래프는 정점의 집합과 간선의 집합의 결합이기 때문에, 이를 표현하는 문제는 '정점의 집합'과 '간선의 집합'의 표현 문제로 생각할 수 있습니다.
-   정점의 잡합은 배열이나 링크드 리스트, 어떤 자료구조를 사용하더라도 쉽게 표현이 가능합니다. 문제는 간선의 집합을 표현하는 방법입니다. 이유는 간선은 그냥 선이 아니기 때문입니다. 간선은 정점과 정점이 '인접'관계에 있음을 나타내는 존재입니다.
-   즉, 그래프의 표현은 "간선, 즉 정점과 정점의 인접 관게를 어덯게 나타내는가?"의 문제로 귀결됩니다.

## Graph의 표현 방법

-   Graph를 나타내는 정점 사이의 인접관계를 나타내는 방법에는 크게 두 가지가 있습니다. 하나는 행렬을 이용하는 것이고, 또 다른 하나는 리스트를 이용하는 것입니다.
-   행렬을 이용하는 방식은 인접행렬(Adjacency Matrix)이라 하고 리스트를 이용하는 방식은 인접 리스트(Adjacency List)라고 부릅니다.

## 인접행렬 표현방법

-   그래프의 정점의 수를 N이라고 한다면, N\*\\N 크기의 행렬을 만들고 행렬의 각 원소를, 한 정점과 또 다른 정점이 인접해 있는 경우(즉, 점점사이에 간선이 존재하는 경우)에는 1로 표시하고, 인접해 있지 않은 경우에는 0으로 표시하는 것입니다.

## 인접리스트 표현 방법

-   각 정점에 대해 자신과 인접해 있는 모든 정점의 목록을 리스트로 관리하도록 하는 것입니다.
-   먼저 모든 정점을 죽 늘어놓고, 각 정점의 인접 정접을 옆에 나열합니다.

[##_Image|kage@c9mJW5/btq2tlPF1ez/tC5oAgsgLqUoUE9NIOqwZ0/img.png|alignLeft|data-origin-width="685" data-origin-height="167" data-ke-mobilestyle="widthContent"|||_##]



## C++ vector 활용 인접리스트 형태로 그래프 표현

![image](https://user-images.githubusercontent.com/76929823/139233447-a03705e7-9c8e-405f-ae8b-dce5ac5174a8.png)
-   위 그래프를 인접리스트 형태로 표현
-   먼저 C++의 대괄호(\[\]) 연산자를 이용해 vector 5개를 선언
-   v1,v2가 연결되어 있다고 하면 아래와 같이 작성 가능
    -   map\[v1\].push\_back(v2);// map\[v1\] 벡터에 v2데이터 추가


```c++
#include<stdio.h>
#include<vector>
using namespace std;
int main() {

    vector<int> map[5];

    //v[0]은 사용 안함
    //vector map[1]은 노드 1에 연결된 노드정보 인접리스트형태로 저장
    map[1].push_back(2);//map[1][0]에 2라는 데이터가 저장
    map[1].push_back(3);//map[1][1]에 3이라는 데이터가 저장
    map[1].push_back(4);//map[1][2]에 4라는 데이터가 저장

    //vector map[2]은 노드2에 연결된 노드 정보를 인접리스트형태로 저장
    map[2].push_back(1);
    map[2].push_back(4);

    //vector map[3]은 노드3에 연결된 노드 정보를 인접리스트형태로 저장
    map[3].push_back(1);
    map[3].push_back(4);

    //vector map[4]은 노드4에 연결된 노드 정보를 인접리스트형태로 저장
    map[4].push_back(1);
    map[4].push_back(2);
    map[4].push_back(3);

    //각 노드에 연결된 길이만큼 for문으로 그래프 정보 출력
    for (int i = 1; i <= 4; ++i) {
        for (int j = 0; j < map[i].size(); ++j) {
            printf("(%d,%d)\n",i, map[i][j]);
        }
    }

    return 0;
}
```


## 연결리스트 표현

[##_Image|kage@1OpDd/btq6lnDuZt0/jW7p8GmpbIyqZsAtfvmXXk/img.png|alignCenter|data-origin-width="463" data-origin-height="306" data-ke-mobilestyle="widthOrigin"|||_##]

## 실제 저장 형태

[##_Image|kage@D8Dcz/btq6k9eqWGh/WUolKLZUY3wy4gFBzNlpvK/img.png|alignCenter|data-origin-width="419" data-origin-height="303" data-ke-mobilestyle="widthOrigin"|||_##]


\-------------------------------------------------------------------------------------------------------------

출처 : 뇌를 자극하는 알고리즘(한빛미디어, 박상현 저)