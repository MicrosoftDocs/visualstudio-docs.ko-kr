---
title: 앱에서 메모리 사용량 측정
description: 디버거 통합 진단 도구를 사용하여 디버그하는 동안 메모리 누수 및 비효율적인 메모리를 찾습니다.
ms.custom: seodec18
ms.date: 04/25/2018
ms.topic: tutorial
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2876e1b25380719a4424c5828c8b37fb5bb72b41
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "75929241"
---
# <a name="measure-memory-usage-in-visual-studio"></a>Visual Studio에서 메모리 사용량 측정

디버거 통합 **메모리 사용량** 진단 도구를 사용하여 디버그하는 동안 메모리 누수 및 비효율적인 메모리를 찾습니다. 메모리 사용량 도구를 통해 관리되는 메모리 및 네이티브 메모리 힙의 *스냅샷*을 하나 이상 만들어 개체 유형이 메모리 사용에 미치는 영향을 이해할 수 있습니다. .NET, 네이티브 또는 혼합 모드(.NET 및 네이티브) 앱의 스냅샷을 수집할 수 있습니다.

다음 그림에서는 Visual Studio 2015 업데이트 1 이상 버전에서 사용할 수 있는 **진단 도구** 창을 보여 줍니다.

![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")

언제든지 **메모리 사용량** 도구에서 메모리 스냅샷을 수집할 수 있지만 Visual Studio 디버거를 사용하여 성능 문제를 조사하는 동안 애플리케이션이 실행되는 방식을 제어할 수 있습니다. 중단점 설정, 단계별 실행, 모두 중단 및 기타 디버거 작업은 가장 관련된 코드 경로를 중심으로 성능 조사를 수행하는 데 도움이 됩니다. 앱이 실행되는 동안 이러한 작업을 수행하면 불필요한 노이즈를 코드에서 제거하고, 문제 진단에 걸리는 시간을 크게 줄일 수 있습니다.

디버거 외부에서 메모리 도구를 사용할 수도 있습니다. [디버그하지 않는 경우의 메모리 사용](../profiling/memory-usage-without-debugging2.md)을 참조하세요. Windows 7 이상에서 연결된 디버거 없이 프로파일링 도구를 사용할 수 있습니다. Windows 8 이상에서는 디버거(**진단 도구** 창)를 포함한 프로파일링 도구를 실행해야 합니다.

> [!NOTE]
> **사용자 지정 할당자 지원** 기본 메모리 프로파일러는 런타임 시 내보낸 할당 [ETW](/windows-hardware/drivers/devtest/event-tracing-for-windows--etw-) 이벤트 데이터를 수집하여 작동합니다.  CRT 및 Windows SDK의 할당자가 해당 할당 데이터를 캡처할 수 있도록 원본 수준에서 주석이 추가되었습니다. 고유한 할당자를 작성하는 경우 myMalloc에 대한 다음 예제처럼 새로 할당된 힙 메모리에 대한 포인터를 반환하는 모든 함수를 [__declspec](/cpp/cpp/declspec)(allocator)로 데코레이트할 수 있습니다.
>
> `__declspec(allocator) void* myMalloc(size_t size)`

이 자습서에서는 다음을 수행합니다.

> [!div class="checklist"]
> * 메모리 스냅샷 생성
> * 메모리 사용량 데이터 분석

## <a name="collect-memory-usage-data"></a>메모리 사용량 데이터 수집

1. Visual Studio에서 디버그할 프로젝트를 열고 메모리 사용량 검사를 시작할 지점에서 앱에 중단점을 설정합니다.

    메모리 문제가 의심되는 영역이 있는 경우 메모리 문제가 발생하기 전에 첫 번째 중단점을 설정합니다.

    > [!TIP]
    > 앱이 메모리를 자주 할당 및 할당 취소하는 경우 관심 있는 작업의 메모리 프로필을 캡처하는 것이 어려울 수 있으므로, 작업의 시작 및 끝에 중단점을 설정하거나 작업을 단계별로 실행하여 메모리가 변경된 정확한 지점을 찾습니다.

2. 의심되는 메모리 문제가 발생한 후 또는 분석할 함수 또는 코드 영역 끝에 두 번째 중단점을 설정합니다.

3. 끄지 않았다면 **진단 도구** 가 자동으로 나타납니다. 창을 다시 표시하려면 **디버그** > **Windows** > **진단 도구 표시**를 클릭합니다.

4. 도구 모음의 **도구 선택** 설정에서 **메모리 사용량**을 선택합니다.

     ![진단 도구 표시](../profiling/media/diag-tools-select-tool-2.png "DiagToolsSelectTool")

5. **디버그/디버깅 시작**을 클릭합니다(또는 도구 모음에서 **시작** 또는 **F5** 누름).

     앱 로드가 완료되면 진단 도구의 요약 보기가 나타납니다.

     ![진단 도구 요약 탭](../profiling/media/diag-tools-summary-tab-2.png "DiagToolsSummaryTab")

     > [!NOTE]
     > 메모리 데이터를 수집할 경우 네이티브 또는 혼합 모드 앱의 디버깅 성능에 영향을 줄 수 있으므로 메모리 스냅샷은 기본적으로 사용되지 않습니다. 네이티브 또는 혼합 모드 앱에서 스냅샷을 사용하도록 설정하려면 디버깅 세션을 시작합니다(바로 가기 키: **F5** 키). **진단 도구** 창이 나타나면 **메모리 사용량** 탭을 선택한 다음, **힙 프로파일링**을 선택합니다.
     >
     >  ![스냅샷 사용](../profiling/media/dbgdiag_mem_mixedtoolbar_enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")
     >
     >  디버깅을 중지(바로 가기 키: **Shift**+**F5**)하고 다시 시작합니다.

6. 디버깅 세션의 시작 부분에 스냅샷을 만들려면 **메모리 사용량** 요약 도구 모음에서 **스냅샷 만들기**를 선택합니다. (이는 여기에 중단점을 설정하는 데도 도움이 될 수 있습니다.)

    ![스냅샷 만들기](../profiling/media/dbgdiag_mem_mixedtoolbar_takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")

     > [!TIP]
     > 메모리 비교 기준을 만들려면 디버깅 세션을 시작할 때 스냅샷을 만드는 것이 좋습니다.

6. 첫 번째 중단점이 발생할 시나리오를 실행합니다.

7. 디버거가 첫 번째 중단점에서 일시 중지하는 동안 **메모리 사용량** 요약 도구 모음에서 **스냅샷 만들기**를 선택합니다.

8. 두 번째 중단점까지 앱을 실행하려면 **F5** 키를 누릅니다.

9. 이제 다른 스냅샷을 만듭니다.

     이 시점에서 데이터 분석을 시작할 수 있습니다.

## <a name="analyze-memory-usage-data"></a>메모리 사용량 데이터 분석
메모리 사용량 요약 테이블의 행에는 디버깅 세션 중에 만든 스냅샷이 나열되고 더 자세한 보기에 대한 링크가 제공됩니다.

![메모리 요약 표](../profiling/media/dbgdiag_mem_summarytable.png "DBGDIAG_MEM_SummaryTable")

 열의 이름은 프로젝트 속성에서 선택한 디버깅 모드(.NET, 네이티브 또는 혼합(.NET 및 네이티브))에 따라 달라집니다.

- **개체(차이)** 및 **할당(차이)** 열에는 스냅샷을 만들 때 .NET 및 네이티브 메모리의 개체 수가 표시됩니다.

- **힙 크기(차이)** 열에는 .NET 및 네이티브 힙의 바이트 수가 표시됩니다.

여러 스냅샷을 만든 경우 요약 테이블의 셀에 행 스냅샷과 이전 스냅샷 간의 값 변경 내용이 포함됩니다.

메모리 사용량을 분석하려면 메모리 사용량에 대한 자세한 보고서를 여는 다음 링크 중 하나를 클릭합니다.

- 현재 스냅샷과 이전 스냅샷 간의 차이 정보를 보려면 화살표의 왼쪽에 있는 변경 링크(![메모리 사용량 증가](../profiling/media/prof-tour-mem-usage-up-arrow.png "메모리 사용량 증가"))를 선택합니다. 빨간색 화살표는 메모리 사용량 증가를 나타내고 녹색 화살표는 감소를 나타냅니다.

> [!TIP]
> 메모리 문제를 더 빠르게 확인하기 위해 차이 보고서는 전체 수에서 가장 많이 증가한 개체 형식(**개체(차이)** 열의 변경 링크 클릭) 또는 전체 힙 크기에서 가장 많이 증가한 개체 형식(**힙 크기(차이)** 열의 변경 링크 클릭)별로 정렬됩니다.

- 선택한 스냅샷의 세부 정보를 보려면 비변경 링크를 클릭합니다.

   보고서는 별도의 창에 나타납니다.

### <a name="managed-types-reports"></a>관리되는 형식 보고서
 메모리 사용량 요약 테이블에서 **개체(차이)** 또는 **할당(차이)** 셀의 현재 링크를 선택합니다.

 ![디버거 관리되는 형식 보고서 &#45; 루트 경로](../profiling/media/dbgdiag_mem_managedtypesreport_pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")

 위쪽 창에는 형식에서 참조되는 모든 개체의 크기(**포함 크기**)를 포함하여 스냅샷의 형식 개수 및 크기가 표시됩니다.

 아래쪽 창의 **루트 경로** 트리에는 위쪽 창에서 선택한 형식을 참조하는 개체가 표시됩니다. .NET Framework 가비지 수집기는 개체를 참조하는 마지막 형식이 해제된 경우에만 개체에 대한 메모리를 정리합니다.

 **참조된 개체** 트리에는 위쪽 창에서 선택한 형식이 보유하고 있는 참조가 표시됩니다.

 ![관리되는 참조된 개체 보고서 보기](../profiling/media/dbgdiag_mem_managedtypesreport_referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")

 위쪽 창에서 선택한 형식의 인스턴스를 표시하려면 ![인스턴스 아이콘](../profiling/media/dbgdiag_mem_instanceicon.png "DBGDIAG_MEM_InstanceIcon") 아이콘을 선택합니다.

 ![인스턴스 뷰](../profiling/media/dbgdiag_mem_managedtypesreport_instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")

 **인스턴스** 뷰에는 위쪽 창의 스냅샷에서 선택한 개체의 인스턴스가 표시됩니다. **루트 경로** 및 **참조된 개체** 창에는 선택한 인스턴스를 참조하는 개체 및 선택한 인스턴스가 참조하는 형식이 표시됩니다. 스냅샷이 만들어진 지점에서 디버거가 중지되면 **값** 셀을 마우스로 가리켜서 도구 설명에 개체 값을 표시할 수 있습니다.

### <a name="native-type-reports"></a>네이티브 형식 보고서
 **진단 도구** 창의 메모리 사용량 요약 테이블에서 **할당(차이)** 또는 **힙 크기(차이)** 셀의 현재 링크를 선택합니다.

 ![네이티브 형식 뷰](../profiling/media/dbgdiag_mem_native_typesview.png "DBGDIAG_MEM_Native_TypesView")

 **형식 뷰** 에는 스냅샷의 형식 수와 크기가 표시됩니다.

- 선택한 형식의 인스턴스 아이콘(![개체 형식 열의 인스턴스 아이콘](../profiling/media/dbg_mma_instancesicon.png "DBG_MMA_InstancesIcon"))을 선택하여 스냅샷에서 선택한 형식의 개체에 대한 정보를 표시합니다.

     **인스턴스** 뷰에는 선택한 형식의 각 인스턴스가 표시됩니다. 인스턴스를 선택하면 **할당 호출 스택** 창에 인스턴스를 만든 호출 스택이 표시됩니다.

     ![인스턴스 뷰](../profiling/media/dbgdiag_mem_native_instances.png "DBGDIAG_MEM_Native_Instances")

- **뷰 모드** 에서 **스택 뷰** 를 선택하여 선택한 형식에 대한 할당 스택을 확인합니다.

     ![뷰 모드](../profiling/media/dbgdiag_mem_native_stacksview.png "DBGDIAG_MEM_Native_StacksView")

### <a name="change-diff-reports"></a>변경(차이) 보고서

- **진단 도구** 창의 **메모리 사용량** 탭에서 요약 테이블 셀의 변경 링크를 선택합니다.

   ![변경&#40;diff&#41; 보고서 선택](../profiling/media/dbgdiag_mem_choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")

- 관리되는 보고서 또는 네이티브 보고서의 **비교 대상** 목록에서 스냅샷을 선택합니다.

   ![비교 목록에서 스냅샷 선택](../profiling/media/dbgdiag_mem_choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")

변경 보고서는 기본 스냅샷 값과 비교 스냅샷 간의 차이를 표시하는 열( **(차이)** 로 표시됨)을 기본 보고서에 추가합니다. 네이티브 형식 뷰 차이 보고서가 표시되는 모양은 다음과 같습니다.

![네이티브 형식 Diff 뷰](../profiling/media/dbgdiag_mem_native_typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")

## <a name="blogs-and-videos"></a>블로그 및 동영상

[디버깅하는 동안 CPU와 메모리 분석](https://devblogs.microsoft.com/visualstudio/analyze-cpu-memory-while-debugging/)

[Visual C++ 블로그: Visual C++ 2015의 메모리 프로파일링](https://devblogs.microsoft.com/cppblog/memory-profiling-in-visual-c-2015/)

## <a name="next-steps"></a>다음 단계

이 자습서에서는 메모리 사용량 데이터를 수집하고 분석하는 방법을 배웠습니다. 이미 [프로파일러 둘러보기](../profiling/profiling-feature-tour.md)를 완료한 경우 앱에서 CPU 사용량을 분석하는 방법을 빠르게 확인하는 것이 좋습니다.

> [!div class="nextstepaction"]
> [CPU 사용 분석](../profiling/beginners-guide-to-performance-profiling.md)
