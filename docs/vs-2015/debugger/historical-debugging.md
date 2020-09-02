---
title: 기록 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7cc5ddf2-2f7c-4f83-b7ca-58e92e9bfdd2
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c7db175535e0eebdcf1974f0f85123959ba5a3ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68192163"
---
# <a name="historical-debugging"></a>기록 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

기록 디버깅은 IntelliTrace에서 수집된 정보에 의존하는 디버깅 모드입니다. 이 디버깅을 사용하면 애플리케이션 실행 도중 앞이나 뒤로 이동하며 상태를 검사할 수 있습니다.  
  
 Visual Studio Enterprise Edition(Professional 또는 Community Edition 아님)에서 IntelliTrace를 사용할 수 있습니다.  
  
## <a name="why-use-historical-debugging"></a>기록 디버깅을 사용하는 이유  
 버그를 찾는 중단점을 설정하는 것은 적중하느냐 누락하느냐의 문제입니다. 코드에서 버그가 있을 것으로 의심되는 위치 가까이에 중단점을 설정하면 디버거에서 애플리케이션을 실행할 때 중단점이 적중될 것으로 기대할 수 있고, 이에 따라 실행이 중단된 위치가 버그 소스를 노출할 수 있습니다. 그러지 않은 경우에는 코드 내의 다른 위치에 중단점을 설정한 후 디버거를 다시 실행해야 합니다. 즉, 문제를 발견할 때까지 테스트 단계를 반복적으로 실행하게 됩니다.  
  
 ![중단점 설정](../debugger/media/breakpointprocesa.png "가는")  
  
 IntelliTrace와 기록 디버깅을 사용하면 중단점을 설정하고 디버깅을 다시 시작하고 테스트 단계를 반복할 필요 없이 애플리케이션 내부를 이동하면서 상태(호출 스택 및 지역 변수)를 검사할 수 있습니다. 이렇게 하면 특히 버그가 테스트 시나리오의 깊은 수준에 있어서 실행하는 데 오래 걸리는 경우 많은 시간을 절약할 수 있습니다.  
  
## <a name="how-do-i-start-using-historical-debugging"></a>기록 디버깅을 사용하여 시작하는 방법  
 IntelliTrace는 기본적으로 설정되어 있습니다. 관심 있는 이벤트와 함수 호출을 결정하기만 하면 됩니다. 찾으려는 항목을 정의하는 방법에 대한 자세한 내용은 [IntelliTrace 기능](../debugger/intellitrace-features.md)을 참조하세요. IntelliTrace를 사용 하 여 디버깅 하는 단계별 계정에 대해서는 [연습: Intellitrace 사용](../debugger/walkthrough-using-intellitrace.md)을 참조 하세요.  
  
## <a name="navigating-your-code-with-historical-debugging"></a>기록 디버깅을 사용하여 코드 탐색  
 버그가 있는 간단한 프로그램부터 살펴보겠습니다. C# 콘솔 애플리케이션에서 다음 코드를 추가합니다.  
  
```csharp  
static void Main(string[] args)  
{  
    int testInt = 0;  
    int resultInt = AddAll(testInt);  
    Console.WriteLine(resultInt);  
}  
private static int AddAll(int j)  
{  
    for (int i = 0; i < 20; i++)  
    {  
        j = AddInt(j);  
    }  
    return j;  
}  
  
private static int AddInt(int add)  
{  
    if (add == 10)  
    {  
        return add += 25;  
    }  
    return ++add;  
}  
```  
  
 `AddAll()`을 호출한 후 `resultInt`의 예상 값을 20으로 가정하겠습니다(`testInt`를 20회 증분한 결과). (또한 `AddInt()`에서 버그를 볼 수 없다고 가정하겠습니다.) 그러나 결과는 실제로 44입니다. `AddAll()`을 단계적으로 10회 실행하지 않고도 버그를 찾으려면 어떻게 할까요? 기록 디버깅을 사용하여 더 빠르고 쉽게 버그를 찾을 수 있습니다. 방법을 알아보겠습니다.  
  
1. 도구 / 옵션 / IntelliTrace / 일반에서 IntelliTrace가 사용하도록 설정되어 있는지 확인하고 IntelliTrace 이벤트 및 호출 정보 옵션을 선택합니다. 이 옵션을 선택하지 않으면 탐색 여백(아래 설명)을 볼 수 없습니다.  
  
2. `Console.WriteLine(resultInt);` 줄에 중단점을 설정합니다.  
  
3. 디버깅을 시작합니다. 코드가 중단점까지 실행됩니다. **로컬** 창에서 `resultInt`의 값이 44임을 확인할 수 있습니다.  
  
4. **진단 도구** 창을 엽니다 (**디버그/진단 도구 표시**). 코드 창이 다음과 같이 나타납니다.  
  
    ![중단점의 코드 창](../debugger/media/historicaldebuggingbreakpoint.png "HistoricalDebuggingBreakpoint")  
  
5. 중단점 바로 위 왼쪽 여백 옆에 이중 화살표가 표시됩니다. 이 영역은 탐색 여백이라고 하며 기록 디버깅에 사용됩니다. 화살표를 클릭합니다.  
  
    코드 창에서 위 코드 줄(`int resultInt = AddIterative(testInt);`)에 분홍색이 지정된 것을 확인할 수 있습니다. 창 위에는 현재 기록 디버깅 중임을 알리는 메시지가 표시됩니다.  
  
    이제 코드 창의 모양은 다음과 같습니다.  
  
    ![기록 디버깅 모드의 코드 창](../debugger/media/historicaldebuggingback.png "HistoricalDebuggingBack")  
  
6. 이제 `AddAll()` 메서드를 단계별로 실행할 수 있습니다(**F11** 키 또는 탐색 여백의 **한 단계씩 코드 실행** 단추). 앞으로 이동합니다(**F10** 키 또는 탐색 여백의 **다음 호출로 이동**). 분홍색 줄이 `j = AddInt(j);` 줄에 표시됩니다. 이 경우에는 **F10** 키를 사용해도 다음 코드 줄로 진행되지 않습니다. 대신, 다음 함수 호출로 이동합니다. 기록 디버깅은 여러 호출을 탐색하며 함수 호출이 포함되지 않은 코드 줄을 건너뜁니다.  
  
7. 이제 `AddInt()` 메서드를 한 단계씩 실행합니다. 이 코드의 버그가 즉시 표시됩니다.  
  
   이 절차에서는 기록 디버깅으로 수행할 수 있는 작업을 기초적으로만 설명했습니다. 다양한 설정 및 탐색 여백에 있는 여러 단추의 효과에 대해 자세히 알아보려면 [IntelliTrace 기능](../debugger/intellitrace-features.md)을 참조하세요.
