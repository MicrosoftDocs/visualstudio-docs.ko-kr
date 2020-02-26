---
title: 완전 초보자를 위한 코드 디버깅
description: 처음으로 디버깅하는 경우 Visual Studio를 사용하여 디버깅 모드에서 앱을 실행하는 데 도움이 되는 몇 가지 원칙을 알아봅니다.
ms.date: 02/14/2020
ms.topic: tutorial
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c3cf9d5e4d72ed316344d1bda930d0416e9efe5
ms.sourcegitcommit: 6ef52c2030b37ea7a64fddb32f050ecfb77dd918
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416398"
---
# <a name="how-to-debug-for-absolute-beginners"></a>완전 초보자를 위한 디버깅하는 방법

틀림없이, 소프트웨어 개발자로서 작성하는 코드는 항상 예상한 대로 작업을 수행하지는 않습니다. 경우에 따라 완전히 다르게 작업을 수행할 때도 있습니다. 이 경우 다음 작업은 그 이유를 파악하는 것이며 몇 시간 동안 코드를 계속 살펴보고 싶더라도 디버깅 도구 또는 디버거를 사용하는 것이 훨씬 더 쉽고 효율적입니다.

아쉽게도 디버거는 마술처럼 코드의 모든 문제 또는 "버그"를 표시할 수 있는 것이 아닙니다. *디버깅*은 Visual Studio와 같은 디버깅 도구에서 단계별로 코드를 실행하여 프로그래밍 실수를 만든 정확한 지점을 찾는 것을 의미합니다. 그런 다음, 코드에서 변경해야 하는 수정 사항을 이해하고, 프로그램 실행을 계속할 수 있도록 디버깅 도구를 통해 종종 임시적인 변경 사항을 만들 수 있습니다.

디버거를 효과적으로 사용하는 것은 학습하는 데 시간 및 연습이 필요한 기술이지만 궁극적으로 모든 소프트웨어 개발자를 위한 기본 작업입니다. 이 문서에서는 디버깅의 핵심 원리를 소개하고 시작하기 위한 팁을 제공합니다.

## <a name="clarify-the-problem-by-asking-yourself-the-right-questions"></a>자신에게 직접 올바른 질문을 하여 문제를 명확히 합니다.

수정하려고 하기 전에 발생한 문제를 명확하게 하는 것이 좋습니다. 이미 코드에서 문제가 발생했다고 예상합니다. 그렇지 않으면 디버깅하는 방법을 파악하기 위해 여기에 있지 않을 것입니다. 따라서 디버깅을 시작하기 전에 해결하고자 하는 문제를 파악했는지 확인합니다.

* 코드에게서 어떤 동작을 기대하셨습니까?

* 그 대신 어떤 일이 발생하였나요?

    앱을 실행하는 동안 오류(예외)가 발생한 경우 이는 좋은 결과가 될 수 있습니다! 예외는 코드를 실행할 때 발생한 예기치 않은 이벤트이며 일반적으로 일종의 오류입니다. 디버깅 도구는 예외가 발생한 코드의 정확한 위치로 안내하고 가능한 수정 사항을 조사하는 데 도움이 됩니다.

    다른 문제가 발생한 경우 문제의 증상은 무엇인가요? 코드에서 이 문제가 발생한 위치를 이미 파악하고 있나요? 예를 들어 코드에서 일부 텍스트를 표시하지만 텍스트가 올바르지 않은 경우 데이터가 잘못되었거나 표시 텍스트를 설정한 코드에 버그가 있다는 것입니다. 디버거에서 코드를 단계별로 실행하여 변수에 대한 각각 및 모든 변경 내용을 검사하여 올바르지 않은 값이 할당된 위치와 방법을 정확하게 파악할 수 있습니다.

## <a name="examine-your-assumptions"></a>가정 검사

버그 또는 오류를 조사하기 전에 특정 결과를 예상하게 만든 가정을 생각해 봅니다. 디버거에서 문제의 원인을 보고 있는 경우에도 문제를 식별하는 과정에 숨겨진 또는 알 수 없는 가정이 방해가 될 수 있습니다. 가능한 가정의 긴 목록이 있을 수 있습니다. 다음은 가정이 올바른지 점검하기 위한 몇 가지 질문입니다.

* 올바른 API를 사용하고 있나요?(즉, 올바른 개체, 함수, 메서드 또는 속성) 사용 중인 API는 사용자가 생각하는 대로 작동하지 않을 수 있습니다. (디버거에서 API 호출을 검사한 후에 수정하려면 올바른 API를 식별할 수 있도록 설명서를 살펴봐야 합니다.)

* API를 올바르게 사용하고 있나요? 아마도 올바른 API를 사용했지만 올바른 방법으로 사용하지 않았을 것입니다.

* 코드에 오타가 포함되어 있나요? 변수 이름의 간단한 맞춤법 오류와 같은 몇 가지 오타는 사용되기 전에 변수를 선언할 필요가 없는 언어를 사용하는 경우에 특히 찾기 어려울 수 있습니다.

* 코드를 변경하고 표시되는 문제와 관련 없는 것으로 가정했나요?

* 개체 또는 변수에 실제로 발생한 것과 다른 특정 값(또는 특정 형식의 값)을 포함할 것으로 예상했나요?

* 코드의 의도를 알고 있나요? 다른 사람의 코드를 디버그하기가 종종 더욱 어렵습니다. 사용자의 코드가 아닌 경우 효과적으로 디버그하기 위해 코드가 수행하는 것을 정확하게 학습하는 데 시간을 소비해야 할 수 있습니다.

    > [!TIP]
    > 코드를 작성할 때 작은 것에서 시작하고, 작동하는 코드를 사용하여 시작합니다! (여기에서는 좋은 샘플 코드가 유용합니다.) 경우에 따라 달성하려는 핵심 작업을 보여주는 코드의 작은 부분부터 시작하여 대규모 또는 복잡한 코드 집합을 수정하는 것이 쉽습니다. 그런 다음, 오류의 각 지점에서 테스트하여 코드를 점진적으로 수정하거나 추가할 수 있습니다.

가정을 질문하여 코드에서 문제를 찾는 데 걸리는 시간을 줄일 수 있습니다. 또한 문제를 해결하는 데 걸리는 시간을 줄일 수 있습니다.

## <a name="step-through-your-code-in-debugging-mode-to-find-where-the-problem-occurred"></a>디버깅 모드에서 코드를 단계별로 실행하여 문제가 발생한 위치 찾기

일반적으로 앱을 실행하면 코드가 실행된 후에 오류 및 잘못된 결과가 표시됩니다. 프로그램 또한 원인을 표시하지 않고 예기치 않게 종료될 수 있습니다.

*디버깅 모드*라고도 하는 디버거 내의 앱 실행은 디버거가 프로그램이 실행될 때 발생하는 모든 것을 적극적으로 모니터링하는 것을 의미합니다. 또한 해당 상태를 검사하기 위해 언제든지 앱을 일시 중지한 다음, 코드를 줄 단위로 단계별로 실행하여 발생하는 모든 세부 사항을 살펴볼 수 있습니다.

Visual Studio에서 디버그 도구 모음의 **F5**(또는 **디버그** > **디버깅 시작** 메뉴 명령 또는 **디버깅 시작**  단추 ![디버깅 시작](../debugger/media/dbg-tour-start-debugging.png "디버깅 시작"))를 사용하여 디버깅 모드로 전환합니다. 예외가 발생하는 경우 Visual Studio의 예외 도우미는 예외가 발생한 정확한 지점으로 안내하고 기타 유용한 정보를 제공합니다. 코드의 예외를 처리하는 방법에 대한 자세한 내용은 [디버깅 기법 및 도구](../debugger/write-better-code-with-visual-studio.md)를 참조하세요.

예외가 발생하지 않은 경우 코드에서 문제를 찾을 수 있는 위치를 알고 있을 것입니다. 이는 코드를 더 신중하게 검사하는 기회를 제공하도록 디버거와 함께 ‘중단점’을 사용하는 위치입니다.  중단점은 신뢰할 수 있는 디버깅의 가장 기본적이고 필수적인 기능입니다. 중단점은 변수의 값, 메모리의 동작 또는 코드가 실행되는 시퀀스를 확인할 수 있도록 Visual Studio에서 실행 중인 코드를 일시 중단해야 하는 위치를 나타냅니다.

Visual Studio에서 코드 줄 옆의 왼쪽 여백을 클릭하여 중단점을 신속하게 설정할 수 있습니다. 또는 줄에 커서를 놓고 **F9** 키를 누릅니다.

이러한 개념을 설명하는 데 도움을 주기 위해 이미 몇 가지 버그를 가지고 있는 일부 예제 코드로 안내합니다. C#을 사용하지만 디버깅 기능은 Visual Basic, C++, JavaScript, Python 및 기타 지원되는 언어에 적용됩니다.

### <a name="create-a-sample-app-with-some-bugs"></a>샘플 앱 만들기(일부 버그를 사용하여)

다음으로 몇 가지 버그가 있는 애플리케이션을 만듭니다.

1. Visual Studio가 설치되어 있어야 하며 만들려는 앱 형식에 따라 **.NET 데스크톱 개발** 워크로드 또는 **.NET Core 플랫폼 간 개발** 워크로드가 설치되어 있어야 합니다.

    아직 Visual Studio를 설치하지 않은 경우  [Visual Studio 다운로드](https://visualstudio.microsoft.com/downloads/)  페이지로 이동하여 체험용으로 설치합니다.

    워크로드를 설치해야 하지만 이미 Visual Studio가 있는 경우 **도구** > **도구 및 기능 가져오기**를 클릭합니다. Visual Studio 설치 관리자가 시작됩니다. **.NET 데스크톱 개발**(또는 **.NET Core 플랫폼 간 개발**) 워크로드를 선택한 다음, **수정**을 선택합니다.

1. Visual Studio를 엽니다.

    ::: moniker range=">=vs-2019"
    시작 창에서 **새 프로젝트 만들기**를 선택합니다. 검색 창에 **콘솔**을 입력한 다음, **콘솔 앱(.NET Core)** 또는 **콘솔 앱(.NET Framework)** 을 선택합니다. **다음**을 선택합니다. **ConsoleApp-FirstApp**과 같은 프로젝트 이름을 입력하고 **만들기**를 클릭합니다.
    ::: moniker-end
    ::: moniker range="vs-2017"
    메뉴 모음에서 **파일** > **새로 만들기** > **프로젝트**를 차례대로 선택합니다. **새 프로젝트** 대화 상자의 왼쪽 창에서 **Visual C#** 아래에 **콘솔 앱**을 선택한 다음, 가운데 창에서 **콘솔 앱(.NET Framework)** 또는 **콘솔 앱(.NET Core)** 을 선택합니다. **ConsoleApp-FirstApp**과 같은 이름을 입력하고 **확인**을 클릭합니다.
    ::: moniker-end

    **콘솔 앱(.NET Framework)** 또는 **콘솔 앱(.NET Core)** 프로젝트 템플릿이 표시되지 않는 경우 **도구** > **도구 및 기능 가져오기**로 이동하면 Visual Studio 설치 관리자가 열립니다. **.NET Core 플랫폼 간 개발** 또는 **.NET 데스크톱 개발** 워크로드를 선택한 다음, **수정**을 선택합니다.

    Visual Studio에서 콘솔 프로젝트를 만들고 오른쪽 창의 솔루션 탐색기에 나타납니다.

1. *Program.cs*에서 모든 기본 코드를 다음 코드로 바꿉니다.

    ```csharp
    using System;
    using System.Collections.Generic;

    namespace ConsoleApp_FirstApp
    {
        class Program
        {
            static void Main(string[] args)
            {
                Console.WriteLine("Welcome to Galaxy News!");
                IterateThroughList();
                Console.ReadKey();
            }

            private static void IterateThroughList()
            {
                var theGalaxies = new List<Galaxy>
            {
                new Galaxy() { Name="Tadpole", MegaLightYears=400, GalaxyType=new GType('S')},
                new Galaxy() { Name="Pinwheel", MegaLightYears=25, GalaxyType=new GType('S')},
                new Galaxy() { Name="Cartwheel", MegaLightYears=500, GalaxyType=new GType('L')},
                new Galaxy() { Name="Small Magellanic Cloud", MegaLightYears=.2, GalaxyType=new GType('I')},
                new Galaxy() { Name="Andromeda", MegaLightYears=3, GalaxyType=new GType('S')},
                new Galaxy() { Name="Maffei 1", MegaLightYears=11, GalaxyType=new GType('E')}
            };

                foreach (Galaxy theGalaxy in theGalaxies)
                {
                    Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
                }

                // Expected Output:
                //  Tadpole  400,  Spiral
                //  Pinwheel  25,  Spiral
                //  Cartwheel, 500,  Lenticular
                //  Small Magellanic Cloud .2,  Irregular
                //  Andromeda  3,  Spiral
                //  Maffei 1,  11,  Elliptical
            }
        }

        public class Galaxy
        {
            public string Name { get; set; }

            public double MegaLightYears { get; set; }
            public object GalaxyType { get; set; }

        }

        public class GType
        {
            public GType(char type)
            {
                switch(type)
                {
                    case 'S':
                        MyGType = Type.Spiral;
                        break;
                    case 'E':
                        MyGType = Type.Elliptical;
                        break;
                    case 'l':
                        MyGType = Type.Irregular;
                        break;
                    case 'L':
                        MyGType = Type.Lenticular;
                        break;
                    default:
                        break;
                }
            }
            public object MyGType { get; set; }
            private enum Type { Spiral, Elliptical, Irregular, Lenticular}
        }
    }
    ```

    이 코드의 의도는 목록에 은하계 이름, 은하계의 거리 및 은하계 유형을 모두 표시하는 것입니다. 디버그하려면 코드의 의도를 이해하는 것이 중요합니다. 출력에 표시하려는 목록에서 한 줄의 형식은 다음과 같습니다.

    *은하계 이름*, *거리*, *은하계 유형*

### <a name="run-the-app"></a>앱 실행

1. **F5** 키 또는 코드 편집기의 위쪽에 있는 디버그 도구 모음에서 **디버깅 시작** 단추 ![디버깅 시작](../debugger/media/dbg-tour-start-debugging.png "디버깅 시작")를 누릅니다.

    앱이 시작되고 디버거에 의해 표시되는 예외가 없습니다. 그러나 콘솔 창에 표시되는 출력은 예상하는 것과 다릅니다. 예상되는 출력은 다음과 같습니다.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,  Irregular
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

    하지만 대신 다음이 표시됩니다.

    ```
    Tadpole  400,  ConsoleApp_FirstApp.GType
    Pinwheel  25,  ConsoleApp_FirstApp.GType
    Cartwheel, 500,  ConsoleApp_FirstApp.GType
    Small Magellanic Cloud .2,  ConsoleApp_FirstApp.GType
    Andromeda  3,  ConsoleApp_FirstApp.GType
    Maffei 1, 11,  ConsoleApp_FirstApp.GType
    ```

    출력 및 코드를 보면 `GType`이 은하계 유형을 저장하는 클래스의 이름인 것을 알 수 있습니다. 클래스 이름이 아닌 실제 은하계 유형(예: "Spiral")을 표시하려고 합니다.

### <a name="debug-the-app"></a>앱 디버그

1. 여전히 실행 중인 앱을 사용하여 이 코드 줄의 `Console.WriteLine` 메서드 호출 옆의 왼쪽 여백을 클릭하여 중단점을 설정합니다.

    ```csharp
    foreach (Galaxy theGalaxy in theGalaxies)
    {
        Console.WriteLine(theGalaxy.Name + "  " + theGalaxy.MegaLightYears + ",  " + theGalaxy.GalaxyType);
    }
    ```

    중단점을 설정하는 경우 왼쪽 여백에 빨간색 점이 나타납니다.

    출력에서 문제를 확인했으므로 디버거에서 출력을 설정하는 이전 코드를 확인하여 디버깅을 시작합니다.

1. 디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭합니다(**Ctrl** + **Shift** + **F5**).

    앱이 설정한 중단점에서 일시 중지됩니다. 노란색 강조 표시는 디버거가 일시 중지된 위치를 나타냅니다(노란색 코드 줄은 아직 실행되지 않음).

1. 오른쪽의 `GalaxyType` 변수를 마우스로 가리킨 다음, 렌치 아이콘의 왼쪽으로 `theGalaxy.GalaxyType`을 확장합니다. `GalaxyType`에 속성 `MyGType`이 포함되고 속성 값이 `Spiral`로 설정된 것을 확인할 수 있습니다.

    ![변수 검사](../debugger/media/beginners-inspect-variable.png)

    "Spiral"은 실제로 콘솔에 인쇄되도록 예상한 올바른 값입니다. 따라서 앱을 실행하는 동안 이 코드의 이 값에 액세스할 수 있는 것이 좋습니다. 이 시나리오에서는 잘못된 API를 사용합니다. 디버거에서 코드를 실행하는 동안 이를 수정할 수 있는지 살펴보겠습니다.

1. 동일한 코드에서 여전히 디버깅하는 동안 커서를 `theGalaxy.GalaxyType`의 끝에 놓고 `theGalaxy.GalaxyType.MyGType`으로 변경합니다. 이를 변경할 수 있지만 코드 편집기는 이 코드를 컴파일할 수 없음을 나타내는 오류를 보여줍니다.

    ![구문 오류](../debugger/media/beginners-edit.png)

1. **편집하며 계속하기** 메시지 상자에서 **편집**을 클릭합니다. 이제 **오류 목록** 창에서 오류 메시지가 표시됩니다. 오류는 `'object'`에 `MyGType`에 대한 정의가 포함되지 않음을 나타냅니다.

    ![구문 오류](../debugger/media/beginners-no-definition.png)

    `GType` 유형의 개체로 각 은하계를 설정하더라도(`MyGType` 속성이 있음) 디버거는 `theGalaxy` 개체를 `GType` 유형의 개체로 인식하지 않습니다. 왜 그럴까요? 은하계 유형을 설정하는 코드를 확인해야 합니다. 이렇게 하면 `GType` 클래스에 `MyGType`의 속성이 분명히 있지만 잘못된 항목이 있습니다. `object`에 대한 오류 메시지는 언어 인터프리터에 대한 단서로 확인되었습니다. 유형은 `GType` 유형의 개체 대신 `object` 유형의 개체로 보입니다.

1. 은하계 유형 설정과 관련된 코드를 확인하여 `Galaxy` 클래스의 `GalaxyType` 속성이 `GType` 대신 `object`로 지정된 것을 확인합니다.

    ```csharp
    public object GalaxyType { get; set; }
    ```

1. 이전 코드를 다음으로 변경합니다.

    ```csharp
    public GType GalaxyType { get; set; }
    ```

1. 디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭하여(**Ctrl** + **Shift** + **F5**) 코드를 다시 컴파일하고 다시 시작합니다.

    이제 디버거가 `Console.WriteLine`에서 일시 중지될 때 `theGalaxy.GalaxyType.MyGType`을 마우스로 가리키고, 값이 제대로 설정된 것을 확인할 수 있습니다.

1. 왼쪽 여백에서 중단점 원을 클릭하여 중단점을 제거한 다음(또는 마우스 오른쪽 단추로 클릭하고 **중단점** > **중단점 삭제** 선택), **F5** 키를 눌러 계속합니다.

    앱이 실행되고 출력을 표시합니다. 이제 괜찮아 보이지만 한 가지를 알 수 있습니다. 소규모 마젤란성운 은하계가 콘솔 출력에서 불규칙 은하계로 나타날 것으로 예상했지만 은하계 형식을 보여주지 않습니다.

    ```
    Tadpole  400,  Spiral
    Pinwheel  25,  Spiral
    Cartwheel, 500,  Lenticular
    Small Magellanic Cloud .2,
    Andromeda  3,  Spiral
    Maffei 1,  Elliptical
    ```

1. 이 코드 줄에 중단점을 설정합니다.

    ```csharp
    public GType(char type)
    ```

    이 코드는 은하계 유형이 설정된 위치이므로 이를 좀 더 자세히 살펴보고자 합니다.

1. 디버그 도구 모음에서 **다시 시작** ![앱 다시 시작](../debugger/media/dbg-tour-restart.png "RestartApp") 단추를 클릭하여(**Ctrl** + **Shift** + **F5**) 다시 시작합니다.

    디버거는 중단점을 설정한 코드 줄에서 일시 중지됩니다.

1. 마우스로 `type` 변수를 가리킵니다. `S`의 값이 표시됩니다(문자 코드 뒤에). 불규칙 은하계 유형임을 알고 있으므로 `I`의 값에 관심이 있습니다.

1. **F5** 키를 누르고 마우스로 `type` 변수를 다시 가리킵니다. `type` 변수에 `I`의 값이 표시될 때까지 이 단계를 반복합니다.

    ![변수 검사](../debugger/media/beginners-inspecting-data.png)

1. 이제 **F11** 키(디버그 도구 모음의 **디버그** > **한 단계씩 코드 실행** 또는 **한 단계씩 코드 실행** 단추)를 누릅니다.

    **F11** 키는 디버거를 한 번에 하나의 명령문씩 실행합니다(또한 코드 실행). **F10** 키(**프로시저 단위 실행**)는 유사한 명령이며, 디버거를 사용하는 방법을 학습하는 경우 둘 다 매우 유용합니다.

1. 'I'의 값에 대한 `switch` 문의 코드 줄에서 중지할 때까지 **F11** 키를 누릅니다. 여기에서 오타에서 발생하는 명백한 문제를 확인할 수 있습니다. 코드가 불규칙 은하계 유형으로 `MyGType`을 설정한 곳으로 이동할 것이라 예상했지만 대신 디버거는 이 코드를 완전히 건너뛰고 `switch` 명령문의 `default` 섹션에서 일시 중지합니다.

    ![오타 찾기](../debugger/media/beginners-typo.png)

    코드를 확인하여 `case 'l'` 명령문에서 오타를 확인합니다. `case 'I'`여야 합니다.

1. `case 'l'`에 대한 코드를 클릭하여 `case 'I'`로 바꿉니다.

1. 중단점을 제거한 다음, **다시 시작** 단추를 클릭하여 앱을 다시 시작합니다.

    이제 버그가 수정되었고 예상한 출력이 표시됩니다.

    앱을 완료하려면 아무 키나 누릅니다.

## <a name="summary"></a>요약

문제가 표시되는 경우 디버거 및 **F10** 및 **F11**과 같은 [단계 명령](../debugger/navigating-through-code-with-the-debugger.md)을 사용하여 문제가 있는 코드 영역을 찾습니다.

> [!NOTE]
> 문제가 발생하는 코드의 영역을 식별하기 어려운 경우 문제가 발생하기 전에 실행되는 코드에서 중단점을 설정한 다음, 문제 매니페스트가 표시될 때까지 단계 명령을 사용합니다. [추적점](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints)을 사용하여 **출력** 창에 메시지를 기록할 수도 있습니다. 기록된 메시지를 확인하여(또한 아직 기록되지 않은 메시지를 확인하여) 종종 문제가 있는 코드 영역을 격리할 수 있습니다. 범위를 좁히기 위해 이 프로세스를 여러 번 반복해야 할 수 있습니다.

문제가 있는 코드 영역을 찾으면 디버거를 사용하여 조사합니다. 문제의 원인을 찾으려면 디버거에서 앱을 실행하는 동안 문제 코드를 검사합니다.

* [변수를 검사](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)하고 포함해야 하는 값의 형식을 포함하는지 여부를 확인합니다. 잘못된 값을 찾는 경우 잘못된 값이 설정된 위치를 찾습니다(값이 설정된 위치를 찾으려면 디버거를 다시 시작하고, [호출 스택](../debugger/how-to-use-the-call-stack-window.md)을 살펴보거나 둘 다 수행해야 할 수 있음).

* 애플리케이션에서 예상하는 코드를 실행하고 있는지 여부를 확인합니다. (예를 들어 애플리케이션 예제에서 switch 문의 코드가 불규칙의 은하계 유형으로 설정될 것이라고 예상했지만 앱은 오타로 인해 코드를 건너뛰었습니다.)

> [!TIP]
> 디버거를 사용하면 버그를 찾는 데 도움이 됩니다. 디버깅 도구에서 코드의 의도를 아는 경우에만 *사용자를 위해* 버그를 찾을 수 있습니다. 도구는 개발자가 해당 의도를 표시하는 경우에만 코드의 의도를 알 수 있습니다. [단위 테스트](../test/improve-code-quality.md)를 작성하는 것이 해당 작업을 수행하는 방법입니다.

## <a name="next-steps"></a>다음 단계

이 문서에서는 몇 가지 일반적인 디버깅 개념을 알아보았습니다. 다음에는, 디버거에 대해 자세히 알아볼 수 있습니다.

> [!div class="nextstepaction"]
> [디버거 소개](../debugger/debugger-feature-tour.md)
