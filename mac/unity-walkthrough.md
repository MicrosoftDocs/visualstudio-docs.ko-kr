---
title: Unity로 게임 빌드 시작하기
description: Unity 및 Mac용 Visual Studio 시작하기
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/20/2019
ms.technology: vs-ide-general
ms.assetid: D07FA43B-9D18-4DFA-8343-CD538FAD84DB
ms.topic: how-to
ms.openlocfilehash: da9c8b3470fee406b577b136b6c55d76c9346e44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85950655"
---
# <a name="getting-started-building-games-with-unity-in-visual-studio-for-mac"></a>Mac용 Visual Studio에서 Unity로 게임 빌드 시작하기

Unity는 C#에서 게임 개발을 지원하는 게임 엔진입니다. 이 연습에서는 Unity 환경은 물론, Visual Studio Tools for Unity 확장과 Visual Studio for Mac을 사용하여 Unity 게임 개발 및 디버깅을 시작하는 방법을 보여줍니다.

Visual Studio for Mac Tools for Unity는 Mac용 Visual Studio와 함께 설치되는 무료 확장으로서, Unity 개발자가 탁월한 IntelliSense 지원, 디버깅 기능 등을 포함해 Mac용 Visual Studio의 생산성 기능을 활용할 수 있게 지원해 줍니다.

## <a name="objectives"></a>목표

> [!div class="checklist"]
> * Mac용 Visual Studio를 사용한 Unity 개발에 대해 알아보기

## <a name="prerequisites"></a>사전 요구 사항

- Mac용 Visual Studio([https://www.visualstudio.com/vs/mac](https://www.visualstudio.com/vs/visual-studio-mac))
- Unity 5.6.1 Personal Edition 이상([https://store.unity.com](https://store.unity.com/), 실행하려면 unity.com 계정 필요)

## <a name="intended-audience"></a>대상 독자

이 랩은 심층적인 경험이 요구되지는 않지만, C#에 능숙한 개발자를 대상으로 합니다.

## <a name="task-1-creating-a-basic-unity-project"></a>작업 1: 기본 Unity 프로젝트 만들기

1. **Unity**를 시작합니다. 요청된 경우 로그인합니다.

2. **새로 만들기**를 클릭합니다.

    ![Unity의 새로 만들기 단추](media/unity-image1.png)

3. **프로젝트 이름**을 **"UnityLab"** 으로 설정하고 **3D**를 선택합니다. **프로젝트 만들기**를 클릭합니다.

    ![새 프로젝트 만들기 화면](media/unity-image2.png)

4. 아래 보이는 화면은 기본 Unity 인터페이스입니다. 왼쪽에는 개임 개체, 중간에는 빈 장면의 3차원 뷰, 맨 아래에는 프로젝트 파일 창, 오른쪽에는 검사기와 서비스가 장면의 계층 구조를 이루고 있습니다. 물론, 이보다 훨씬 더 많이 있지만 보다 중요한 몇 가지 구성 요소를 대표적으로 보여주고 있습니다.

    ![빈 Unity 인터페이스](media/unity-image3.png)

5. Unity를 처음 사용하는 개발자를 위해 앱에서 실행되는 모든 것은 **장면**이라는 컨텍스트 내에 있게 됩니다. 장면 파일은 현재 장면과 해당 속성에 대해 프로젝트에서 사용되는 리소스에 대한 모든 종류의 메타데이터를 포함하는 단일 파일입니다. 플랫폼용 앱을 패키징하는 경우 결과 앱은 사용자가 추가하는 플랫폼 종속 코드와 함께, 하나 이상의 장면 컬렉션으로 마무리됩니다. 한 프로젝트에 원하는 만큼 많은 장면을 넣을 수 있습니다.

6. 새 장면에 방금 카메라와 방향성 광원이 생겼습니다. 장면에는 무엇이든 보이게 하는 **카메라**와 무엇이든 들리게 하는 **오디오 수신기**가 필요합니다. 이러한 구성 요소는 **GameObject**에 연결되어 있습니다.

7. **계층 구조** 창에서 **주 카메라** 개체를 선택합니다.

    ![계층 구조 창에 강조 표시된 주 카메라 개체](media/unity-image4.png)

8. 창 오른쪽에서 **검사기** 창을 선택하여 속성을 검토합니다. 카메라 속성에는 변환 정보, 백그라운드, 투사 유형, 시야각 등이 있습니다. 또한 오디오 수신기 구성 요소도 기본적으로 추가되어 있어 기본적으로 카메라에 연결된 가상 마이크에서 장면 오디오를 렌더링합니다.

    ![검사기 창](media/unity-image5.png)

9. **방향성 광원** 개체를 선택합니다. 이 셰이더와 같은 구성 요소가 개체를 렌더링하는 방법을 파악하도록 장면에 광원을 제공합니다.

    ![강조 표시된 방향성 광원 개체](media/unity-image6.png)

10. **검사기**를 사용하여 형식, 색, 강도, 섀도 형식 등을 포함해 일반적인 조명 속성을 포함하는지 확인합니다.

    ![속성 검사자 창에서 속성 보기](media/unity-image7.png)

11. Unity 프로젝트는 Mac용 Visual Studio 프로젝트와 약간 다르다는 것에 주목하는 것이 중요합니다. 맨 아래의 **프로젝트** 탭에서 **자산** 폴더를 마우스 오른쪽 단추로 클릭하고 **Finder에 표시**를 선택합니다.

    ![Finder에 표시 컨텍스트 작업](media/unity-image8.png)

12. 보이는 것처럼, 프로젝트에는 **Assets**, **Library**, **프ProjectSettings** 및 **Temp** 폴더가 있습니다. 그러나 인터페이스에는 **Assets** 폴더만 표시됩니다. **Library** 폴더는 가져온 자산을 위한 로컬 캐시로, 자산에 대한 모든 메타데이터를 포함합니다. **ProjectSettings** 폴더는 사용자가 구성할 수 있는 설정을 저장합니다. **Temp** 폴더는 빌드 프로세스 중 Mono 및 Unity의 임시 파일에 사용되며, Mac용 Visual Studio에서 열 수 있는 솔루션 파일도 있습니다(여기서는 **UnityLab.sln**).

    ![Finder에서의 자산](media/unity-image9.png)

13. **Finder** 창을 닫고 **Unity**로 돌아갑니다.

14. **Assets** 폴더는 자산-아트, 코드, 오디오 등을 모두 포함합니다. 지금은 비어 있지만, 프로젝트로 불러 오는 모든 단일 파일이 여기로 이동합니다. 이 폴더는 **Unity 편집기**에서 항상 최상위 레벨의 폴더입니다. 하지만 항상 바로 파일 시스템을 통해서가 아니라, Unity 인터페이스(또는 Mac용 Visual Studio)를 통해 파일을 추가하고 제거하세요.

    ![Unity의 자산 폴더](media/unity-image10.png)

15. **GameObject**는 거의 모든 것이 모델, 조명, 파티클 시스템 등을 포함해 이 유형에서 파생되므로 Unity에서의 개발에 중요합니다. **GameObject > 3차원 개체 > 큐브** 메뉴를 통해 장면에 새 **큐브** 개체를 추가합니다.

    ![장면의 큐브 개체](media/unity-image11.png)

16. 새로운 **GameObject**의 속성을 빠르게 살펴 보고 이름, 태그, 계층 및 변형이 있는지 확인합니다. 이러한 속성은 모든 **GameObject**에 공통됩니다. 또한 메시 필터, 박스 콜라이더 및 렌더러를 포함한 다양한 구성 요소가 필요한 기능을 제공하기 위해 **큐브**에 연결되어 있습니다.

    ![게임 개체 속성](media/unity-image12.png)

17. 기본 이름이 **"Cube"** 인 **큐브** 개체의 이름을 **"Enemy"** 로 변경합니다. 변경 사항을 저장하려면 반드시 **Enter** 키를 누르십시오. 그러면 간단한 게임에서 Enemy 큐브가 되는 것입니다.

    ![큐브 개체 이름 바꾸기 속성](media/unity-image13.png)

18. 위와 동일한 절차를 이용하여 장면에 **큐브** 개체를 하나 더 추가하고 **"Player"** 라는 이름을 지정합니다.

    ![두 번째 큐브 개체 이름 바꾸기](media/unity-image14.png)

19. 플레이어 개체에도 **"Player"** 로 태그를 지정합니다(이름 필드 바로 아래의 **태그** 드롭다운 컨트롤 참조). 플레이어 게임 개체를 찾을 수 있도록 Enemy 개체에서 이 플레이어를 사용할 것입니다.

    ![플레이어 개체 태그 지정](media/unity-image15.png)

20. **장면** 보기에서 마우스를 사용해 Z축을 따라 Enemy 개체에서 플레이어 개체를 멀리 이동합니다. 큐브의 **빨강** 패널을 선택하여 **파랑** 선을 향해 끌면 Z축을 따라 이동할 수 있습니다. 큐브는 3차원 공간에 있지만 매번 2차원에서만 끌 수 있으므로, 끄는 축이 특히 중요합니다.

    ![큐브를 보여주는 장면 뷰](media/unity-image16.png)

21. 큐브를 축을 따라 아래를 향하여 오른쪽으로 이동합니다. 그러면 **검사기**에서 **Transform.Position** 속성이 업데이트됩니다. 여기에 보이는 것과 비슷하게 위치로 끌어야 랩에서 이후 단계를 더 쉽게 진행할 수 있습니다.

    ![축을 따라 큐브 한 개 이동하기](media/unity-image17.png)

22. 이제 플레이어를 추적하도록 Enemy 논리를 구동하는 코드를 추가할 수 있습니다. **프로젝트** 패드에서 **Assets** 폴더를 마우스 오른쪽 단추로 클릭하고 **만들기 > C# 스크립트**를 선택합니다.

    ![C# 스크립트 컨텍스트 작업](media/unity-image18.png)

23. 새 C# 스크립트를 **"EnemyAI"** 로 이름을 지정합니다.

    ![C# 스크립트](media/unity-image19.png)

24. 게임 개체에 스크립트를 연결하려면 **계층 구조** 창에서 **Enemy** 개체로 새로 만든 스크립트를 끄세요. 이제 개체가 이 스크립트의 동작을 사용하게 됩니다.

    ![게임 개체로 스크립트 추가를 보여주는 강조 표시](media/unity-image20.png)

25. **파일 > 장면 저장**을 선택하여 현재 장면을 저장합니다. **"MyScene"** 으로 이름을 지정합니다.

## <a name="task-2-working-with-visual-studio-for-mac-tools-for-unity"></a>작업 2: Visual Studio for Mac Tools for Unity 작업

1. C# 코드를 편집하는 가장 좋은 방법은 Mac용 Visual Studio를 사용하는 것입니다. 기본 처리기로 Mac용 Visual Studio를 사용하도록 Unity를 구성할 수 있습니다. **Unity > 기본 설정**을 선택합니다.

2. **외부 도구** 탭을 선택합니다. **외부 스크립트 편집기** 드롭다운에서 **찾아보기**를 선택하고 **Applications/Visual Studio.app**을 선택합니다. 또는 이미 **Visual Studio** 옵션이 있는 경우에는 그냥 선택하세요.

    ![기본 설정의 외부 도구 탭](media/unity-image21.png)

3. 이제 Unity는 스크립트 편집에 **Mac용 Visual Studio**를 사용하도록 구성되었습니다. **Unity 기본 설정** 대화 상자를 닫습니다.

    ![기본 설정에서 선택된 Visual Studio](media/unity-image22.png)

4. **EnemyAI.cs**를 두 번 클릭하여 **Mac용 Visual Studio**에서 엽니다.

    ![Unity에서 선택된 Enemy 자산](media/unity-image23.png)

5. Visual Studio 솔루션은 간단합니다. 이전에 만든 **자산** 폴더(**Finder**와 같은 폴더)와 **EnemyAI.cs** 스크립트가 들어 있습니다. 보다 복잡한 프로젝트에서는 계층 구조가 Unity에서 보이는 것과는 다르게 보일 가능성이 높습니다.

    ![Mac용 Visual Studio의 솔루션 패드](media/unity-image24.png)

6. **EnemyAI.cs**가 편집기에서 열려 있습니다. 초기 스크립트에는 **Start** 및 **Update** 메서드에 대한 스텁만 들어 있습니다.

7. 초기 Enemy 코드를 아래 코드로 바꿉니다.

    ```csharp
    public class EnemyAI : MonoBehaviour
    {
        public float Speed = 50;
        private Transform _playerTransform;
        private Transform _myTransform;

        void Start()
        {
            var player = GameObject.FindGameObjectWithTag("Player");
            if (!player)
            {
                Debug.LogError(
                    "Could not find the main player. Ensure it has the player tag set.");
            }
            else
            {
                _playerTransform = player.transform;
            }
            _myTransform = this.transform;
        }

        void Update()
        {
            var moveAmount = Speed * Time.deltaTime;
            _myTransform.position = Vector3.MoveTowards(_myTransform.position,
                _playerTransform.position, moveAmount);

            if (_myTransform.position == _playerTransform.position)
            {
                _myTransform.position = Vector3.back * 10;
            }
        }
    }
    ```

8. 여기에 정의되어 있는 간단한 Enemy 동작을 빠르게 살펴 봅니다. **Start** 메서드에서 **변형**뿐만 아니라 플레이어 개체에 대한 참조를 가져옵니다. 프레임마다 호출되는 **Update** 메서드에서 Enemy는 플레이어 개체를 향해 이동합니다. 키워드와 이름에 색 코딩을 사용하여 Mac용 Visual Studio에서 코드베이스를 훨씬 쉽게 파악할 수 있습니다.

9. 변경 사항을 **Mac용 Visual Studio**의 Enemy 스크립트에 저장합니다.

## <a name="task-3-debugging-the-unity-project"></a>작업 3: Unity 프로젝트 디버깅

1. **Start** 메서드에서 코드 첫 줄에 중단점을 설정합니다. 대상 선에서 편집기 여백을 클릭하거나 줄에 커서를 놓고 **F9**를 누를 수 있습니다.

    ![Mac용 Visual Studio에서 중단점 설정](media/unity-image25.png)

2. **디버깅 시작** 단추를 클릭하거나 **F5**를 누릅니다. 그러면 프로젝트가 빌드되고 디버깅을 위해 Unity에 연결됩니다.

    ![Mac용 Visual Studio의 시작 단추](media/unity-image26.png)

3. **Unity**로 돌아가 **실행** 단추를 클릭하여 게임을 시작합니다.

    ![Unity의 실행 단추](media/unity-image27.png)

4. 중단점이 적중되며 이제 Mac용 Visual Studio 디버깅 도구를 사용할 수 있습니다.

    ![Mac용 Visual Studio에서 중단점 적중](media/unity-image28.png)

5. **로컬** 패드에서 **EnemyAI** 개체를 참조하는 **이** 포인터를 찾습니다. 참조를 확장하고 **속도**와 같은 연결된 멤버를 찾아볼 수 있는지 확인합니다.

    ![Mac용 Visual Studio에서 로컬 디버깅](media/unity-image29.png)

6. 여백을 클릭하거나 줄을 선택하고 **F9**를 눌러 추가한 것과 같은 방식으로 **Start** 메서드에서 중단점을 제거합니다.

    ![Mac용 Visual Studio에서 중단점 적중](media/unity-image30.png)

7. **F10**을 눌러 코드의 첫 줄로 이동하여 매개 변수로 태그를 사용하여 **플레이어** 게임 개체를 찾습니다.

8. 마우스 커서를 코드 편집기 창 내부의 **플레이어** 변수에 올려 놓고 연결된 멤버를 봅니다. 오버레이를 확장하면 자식 속성도 볼 수 있습니다.

    ![Mac용 Visual Studio 편집기의 디버깅 창](media/unity-image31.png)

9. **F5**를 누르거나 **실행** 단추를 눌러 실행을 계속합니다. Unity로 돌아가 Enemy 큐브가 반복해서 플레이어 큐브에 접근하는지 확인합니다. 보이지 않을 경우 카메라를 조정해야 할 수 있습니다.

    ![Unity에서 장면 재생](media/unity-image32.png)

10. **Mac용 Visual Studio**로 다시 돌아가 **Update** 메서드의 첫 줄에 중단점을 설정합니다. 즉시 적중되어야 합니다.

    ![Mac용 Visual Studio에서 중단점 설정](media/unity-image33.png)

11. 속도가 너무 빨라서 앱을 다시 시작하지 않고 변경 사항의 영향력을 테스트하고 싶어한다고 가정하겠습니다. **자동** 또는 **로컬** 창 내에서 **속도** 변수를 찾은 다음, **"10"** 으로 변경하고 **Enter** 키를 누릅니다.

    ![로컬 창에서 변수 조정](media/unity-image34.png)

12. 중단점을 제거하고 **F5** 키를 눌러 실행을 계속합니다.

13. **Unity**로 돌아가 실행 중인 애플리케이션을 봅니다. Enemy 큐브가 이제 원래 속도의 5분의 1로 움직입니다.

    ![애플리케이션일 실행 중인 Unity 창](media/unity-image35.png)

14. **재생** 단추를 다시 클릭하여 Unity 앱을 중지합니다.

    ![Unity 앱 중지](media/unity-image36.png)

15. **Mac용 Visual Studio**로 돌아갑니다. **중지** 단추를 클릭하여 디버깅 세션을 중지합니다.

    ![Mac용 Visual Studio에서 디버깅 세션 중지](media/unity-image37.png)

## <a name="task-4-exploring-unity-features-in-visual-studio-for-mac"></a>작업 4: Mac용 Visual Studio에서 Unity 기능 살펴보기

1. Mac용 Visual Studio는 코드 편집기 내 Unity 문서에 대한 빠른 액세스를 제공합니다. **Update** 메서드 내의 **Vector3** 기호 아무 곳에나 커서를 대고 **⌘ 명령 + '** 를 누릅니다.

    ![Mac용 Visual Studio 편집기에서 메서드 선택](media/unity-image38.png)

2. 새 브라우저 창에 **Vector3**에 대한 문서가 열립니다. 만족스러우면 브라우저 창을 닫습니다.

    ![문서로 열리는 브라우저 창](media/unity-image39.png)

3. 또한 Mac용 Visual Studio는 Unity 동작 클래스를 신속하게 만들 수 있도록 도우미를 제공하기도 합니다. **솔루션 탐색기**에서 **자산**을 마우스 오른쪽 단추로 클릭하고 **추가 > 새 MonoBehaviour**를 선택합니다.

    ![새 MonoBehaviour 컨텍스트 작업](media/unity-image40.png)

4. 새로 만든 클래스는 **Start** 및 **Update** 메서드에 대한 스텁을 제공합니다. **Update** 메서드의 닫는 중괄호 다음에 **"onmouseup"** 입력을 시작합니다. 입력할 때 구현하려는 메서드에 Visual Studio의 IntelliSense가 빠르게 영점화되는 것을 알 수 있습니다. 제공된 자동 완성 목록에서 선택합니다. 매개 변수를 포함해 사용자를 위해 메서드 스텁이 채워집니다.

    ![Mac용 Visual Studio의 IntelliSense](media/unity-image41.png)

5. **OnMouseUp** 메서드 내부에서 **"base."** 를 입력하고 호출에 사용 가능한 모든 베이스 메서드를 확인합니다. 또한 IntelliSense 플라이아웃의 오른쪽 위 모서리에서 페이징 옵션을 사용하여 각 함수의 다양한 오버로드를 살펴볼 수도 있습니다.

    ![Mac용 Visual Studio에서 오버로드 살펴보기](media/unity-image42.png)

6. 또한 Mac용 visual Studio를 사용하여 새 셰이더를 쉽게 정의할 수도 있습니다. **솔루션 탐색기**에서 **자산**을 마우스 오른쪽 단추로 클릭하고 **추가 > 새 셰이더**를 선택합니다.

    ![Mac용 visual Studio의 새 셰이더 작업](media/unity-image43.png)

7. 셰이더 파일 형식은 풀컬러와 글꼴 처리가 지원되어 훨씬 쉽게 읽고 이해할 수 있습니다.

    ![구문 강조](media/unity-image44.png)

8. **Unity**로 돌아갑니다. Mac용 Visual Studio는 동일한 프로젝트 시스템으로 작동하므로, 다른 위치에서 적용한 변경 사항도 서로 자동으로 동기화되어 있음을 알 수 있습니다. 이제 언제나 쉽게 작업에 최상의 도구를 사용할 수 있습니다.

    ![Unity 자산 패널](media/unity-image45.png)

## <a name="summary"></a>요약

이 랩에서는 Unity 및 Mac용 Visual Studio를 사용하여 게임 만들기를 시작하는 방법을 살펴보았습니다. Unity에 대한 자세한 내용은 [https://unity3d.com/learn](https://unity3d.com/learn)을 참조하십시오.
