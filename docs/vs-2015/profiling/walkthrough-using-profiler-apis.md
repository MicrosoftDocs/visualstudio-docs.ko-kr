---
title: '연습: 프로파일러 API 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- profiling tools, walkthroughs
- performance tools, walkthroughs
ms.assetid: c2ae0b3e-a0ca-4967-b4df-e319008f520e
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: d5fc0f5a11d29fdb1ee570dc32066fdd492ed8db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68871545"
---
# <a name="walkthrough-using-profiler-apis"></a>연습: 프로파일러 API 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

연습에서는 C# 애플리케이션을 사용하여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로파일링 도구 API를 사용하는 방법을 보여 줍니다. 프로파일러 API를 사용하여 계측 프로파일링 동안 수집되는 데이터 양을 제한합니다.

 이 연습의 단계는 일반적으로 C/C++ 애플리케이션에 적용됩니다. 각 언어의 경우 빌드 환경을 적절하게 구성해야 합니다.

 일반적으로 샘플 프로파일링을 사용하여 애플리케이션 성능 분석을 시작합니다. 샘플 프로파일링에서 병목 상태를 파악할 수 있는 정보를 제공하지 않는 경우 계측 프로파일링은 더 높은 수준의 세부 정보를 제공할 수 있습니다. 계측 프로파일링은 스레드 상호 작용을 조사하는 데 매우 유용합니다.

 그러나 더 높은 수준의 세부 정보는 더 많은 데이터가 수집됨을 의미합니다. 계측 프로파일링에서 대용량 데이터 파일을 만드는 것을 알 수 있습니다. 또한 계측은 애플리케이션의 성능에 영향을 줄 가능성이 높습니다. 자세한 내용은 [계측 데이터 값 이해](../profiling/understanding-instrumentation-data-values.md) 및 [샘플링 데이터 값 이해](../profiling/understanding-sampling-data-values.md)를 참조하세요.

 Visual Studio 프로파일러를 사용하면 데이터의 수집을 제한할 수 있습니다. 이 연습에서는 프로파일러 API를 사용하여 데이터의 수집을 제한하는 방법의 예를 제공합니다. Visual Studio 프로파일러는 애플리케이션 내에서 데이터 수집 제어에 대한 API를 제공합니다.

 네이티브 코드의 경우 Visual Studio 프로파일러 API는 VSPerf.dll에 있습니다. 헤더 파일, VSPerf.h 및 가져오기 라이브러리, VSPerf.lib는 Microsoft Visual Studio 9\Team Tools\Performance Tools 디렉터리에 있습니다.

 관리되는 코드의 경우 프로파일러 API는 Microsoft.VisualStudio.Profiler.dll에 있습니다. 이 DLL은 Microsoft Visual Studio 9\Team Tools\Performance Tools 디렉터리에 있습니다. 자세한 내용은 [Profiler](/previous-versions/ms242704(v=vs.140))를 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습에서는 사용자가 선택한 개발 환경이 디버깅 및 샘플링을 지원하도록 구성되었다고 가정합니다. 다음 항목에서는 이러한 필수 구성 요소의 개요를 제공합니다.

 [방법: 수집 방법 선택](../profiling/how-to-choose-collection-methods.md)

 [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)

 기본적으로 프로파일러가 시작되면 프로파일러는 전역 수준에서 데이터를 수집합니다. 프로그램의 시작 부분에서 다음 코드는 전역 프로파일링을 해제합니다.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

 API 호출을 사용하지 않고 명령줄에서 데이터 수집을 해제할 수 있습니다. 다음 단계에서는 명령줄 빌드 환경이 프로파일링 도구를 실행하고 개발 도구로 구성되었다고 가정합니다. 여기에는 VSInstr 및 VSPerfCmd에 필요한 설정이 포함됩니다. 명령줄 프로파일링 도구를 참조하세요.

## <a name="limiting-data-collection-using-profiler-apis"></a>프로파일러 API를 사용하여 데이터 수집 제한

#### <a name="to-create-the-code-to-profile"></a>프로파일링할 코드를 만들려면

1. Visual Studio에서 새 C# 프로젝트를 만들거나 기본 설정에 따라 명령줄 빌드를 사용합니다.

    > [!NOTE]
    > 빌드는 Microsoft Visual Studio 9\Team Tools\Performance Tools 디렉터리에 있는 Microsoft.VisualStudio.Profiler.dll 라이브러리를 참조해야 합니다.

2. 다음 코드를 복사하여 프로젝트에 붙여넣습니다.

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.Text;
    using Microsoft.VisualStudio.Profiler;

    namespace ConsoleApplication2
    {
        class Program
        {
            public class A
            {
             private int _x;

             public A(int x)
             {
              _x = x;
             }

             public int DoNotProfileThis()
             {
              return _x * _x;
             }

             public int OnlyProfileThis()
             {
              return _x + _x;
             }

             public static void Main()
             {
            DataCollection.StopProfile(
            ProfileLevel.Global,
            DataCollection.CurrentId);
              A a;
              a = new A(2);
              int x;
              Console.WriteLine("2 square is {0}", a.DoNotProfileThis());
              DataCollection.StartProfile(
                  ProfileLevel.Global,
                  DataCollection.CurrentId);
              x = a.OnlyProfileThis();
              DataCollection.StopProfile(
                  ProfileLevel.Global,
                  DataCollection.CurrentId);
              Console.WriteLine("2 doubled is {0}", x);
             }
            }

        }
    }
    ```

#### <a name="to-collect-and-view-data-in-the-visual-studio-ide"></a>Visual Studio IDE에서 데이터를 수집하고 보려면

1. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE를 엽니다. **분석** 메뉴에서 **프로파일러**를 가리킨 다음 **새 성능 세션**을 선택합니다.

2. **성능 탐색기** 창의 **대상** 목록에 컴파일된 이진 파일을 추가합니다. **대상**을 마우스 오른쪽 단추로 클릭한 다음 **대상 이진 파일 추가**를 선택합니다. **대상 이진 파일 추가** 대화 상자에서 이진 파일을 찾은 다음 **열기**를 클릭합니다.

3. **성능 탐색기** 도구 모음의 **메서드** 목록에서 **계측**을 선택합니다.

4. **프로파일링 시작**을 클릭합니다.

    프로파일러는 이진 파일을 계측 및 실행하고 성능 보고서 파일을 만듭니다. 성능 보고서 파일은 **성능 탐색기**의 **보고서** 노드에 표시됩니다.

5. 결과 성능 보고서 파일을 엽니다.

   기본적으로 프로파일러가 시작되면 프로파일러는 전역 수준에서 데이터를 수집합니다. 프로그램의 시작 부분에서 다음 코드는 전역 프로파일링을 해제합니다.

```
DataCollection.StopProfile(
ProfileLevel.Global,
DataCollection.CurrentId);
```

#### <a name="to-collect-and-view-data-at-the-command-line"></a>명령줄에서 데이터를 수집하고 보려면

1. 이 연습 앞부분의 "프로파일링할 코드 만들기" 절차에서 만든 샘플 코드의 디버그 버전을 컴파일합니다.

2. 관리되는 애플리케이션을 프로파일링하려면 다음 명령을 입력하여 적절한 환경 변수를 설정합니다.

     **VsPefCLREnv /traceon**

3. 다음 명령을 입력 합니다.**VSInstr \<filename> **

4. 다음 명령을 입력 합니다.**VSPerfCmd/start: trace/output: \<filename> .vsp**

5. **VSPerfCmd /globaloff** 명령을 입력합니다.

6. 프로그램을 실행합니다.

7. **VSPerfCmd /shutdown** 명령을 입력합니다.

8. 다음 명령을 입력 합니다.**VSPerfReport/calltrace: \<filename> .vsp**

     결과 성능 데이터와 함께 현재 디렉터리에 .csv 파일이 만들어집니다.

## <a name="see-also"></a>추가 정보

- [Profiler](/previous-versions/ms242704(v=vs.140))
- [Visual Studio 프로파일러 API 참조 (네이티브)](../profiling/visual-studio-profiler-api-reference-native.md)
- [시작](../profiling/getting-started-with-performance-tools.md)
- [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)