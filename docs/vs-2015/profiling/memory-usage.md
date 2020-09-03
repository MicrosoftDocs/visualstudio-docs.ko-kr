---
title: 메모리 사용량 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: bbb58d6c-3362-4ca3-8e87-64b2d4415bf6
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0feabad8dfa3b086c9ed5a1a58e231719774f9cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298362"
---
# <a name="memory-usage"></a>메모리 사용량
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

디버거 통합 **메모리 사용량** 진단 도구를 사용 하 여 디버깅 하는 동안 메모리 누수 및 비효율적인 메모리를 찾습니다. 메모리 사용량 도구를 통해 관리되는 메모리 및 네이티브 메모리 힙의 *스냅샷* 을 하나 이상 만들 수 있습니다. .NET, 네이티브 또는 혼합 모드(.NET 및 네이티브) 앱의 스냅샷을 수집할 수 있습니다.  
  
- 단일 스냅샷을 분석하여 메모리 사용에 대한 개체 형식의 상대적 영향을 파악하고 앱에서 메모리를 비효율적으로 사용하는 코드를 찾을 수 있습니다.  
  
- 또한 앱의 스냅샷 두 개를 비교(diff)하여 코드에서 시간에 따라 메모리 사용이 늘어나는 영역을 찾을 수 있습니다.  
  
  다음 그림은 Visual Studio 2015 업데이트 1의 **진단 도구** 창을 보여 줍니다.  
  
  ![DiagnosticTools&#45;Update1](../profiling/media/diagnostictools-update1.png "DiagnosticTools-Update1")  
  
  언제든지 **메모리 사용량** 도구에서 메모리 스냅샷을 수집할 수 있지만 Visual Studio 디버거를 사용하여 성능 문제를 조사하는 동안 애플리케이션이 실행되는 방식을 제어할 수 있습니다. 중단점 설정, 단계별 실행, 모두 중단 및 기타 디버거 작업은 가장 관련된 코드 경로를 중심으로 성능 조사를 수행하는 데 도움이 됩니다. 앱이 실행되는 동안 이러한 작업을 수행하면 불필요한 노이즈를 코드에서 제거하고 문제 진단에 걸리는 시간을 크게 줄일 수 있습니다.  
  
  디버거 외부에서 메모리 도구를 사용할 수도 있습니다. [디버깅 하지 않고 메모리 사용](https://msdn.microsoft.com/library/8883bc5f-df86-4f84-aa2b-a21150f499b0)을 참조 하세요.  
  
> [!NOTE]
> **사용자 지정 할당자 지원** 기본 메모리 프로파일러는 런타임 중 내보낸 할당 [ETW](https://msdn.microsoft.com/library/windows/desktop/bb968803\(v=vs.85\).aspx) 이벤트 데이터를 수집하여 작동합니다.  CRT 및 Windows SDK의 할당자가 해당 할당 데이터를 캡처할 수 있도록 원본 수준에서 주석이 추가되었습니다.  고유한 할당자를 작성하는 경우 myMalloc에 대한 다음 예제처럼 새로 할당된 힙 메모리에 대한 포인터를 반환하는 모든 함수를 [__declspec](https://msdn.microsoft.com/library/832db681-e8e1-41ca-b78c-cd9d265cdb87)(allocator)로 데코레이트할 수 있습니다.  
>   
> `__declspec(allocator) void* myMalloc(size_t size)`  
  
## <a name="analyze-memory-use-with-the-debugger"></a>디버거를 사용하여 메모리 사용 분석  
  
> [!NOTE]
> 메모리 데이터를 수집할 경우 네이티브 또는 혼합 모드 앱의 디버깅 성능에 영향을 줄 수 있으므로 메모리 스냅샷은 기본적으로 사용되지 않습니다. 스냅샷 네이티브 또는 혼합 모드 앱을 사용하도록 설정하려면 디버깅 세션을 시작합니다(바로 가기 키: **F5**). **진단 도구** 창이 나타나면 메모리 사용량 탭을 선택한 다음 **스냅샷 사용**을 선택합니다.  
>   
> ![스냅샷 사용](../profiling/media/dbgdiag-mem-mixedtoolbar-enablesnapshot.png "DBGDIAG_MEM_MixedToolbar_EnableSnapshot")  
>   
> 디버깅을 중지(바로 가기 키: **Shift + F5**)하고 다시 시작합니다.  
  
 메모리 상태를 캡처할 때마다 **메모리 사용량** 요약 도구 모음에서 **스냅샷 만들기** 를 선택합니다.  
  
 ![스냅샷 만들기](../profiling/media/dbgdiag-mem-mixedtoolbar-takesnapshot.png "DBGDIAG_MEM_MixedToolbar_TakeSnapshot")  
  
> [!TIP]
> - 메모리 비교 기준을 만들려면 디버깅 세션을 시작할 때 스냅샷을 만드는 것이 좋습니다.  
>   - 앱이 메모리를 자주 할당 및 할당 취소하는 경우 관심 있는 작업의 메모리 프로필을 캡처하는 것이 어려울 수 있으므로 작업의 시작 및 끝에 중단점을 설정하거나 작업을 단계별로 실행하여 메모리가 변경된 정확한 지점을 찾습니다.  
  
## <a name="viewing-memory-snapshot-details"></a>메모리 스냅샷 정보 보기  
 메모리 사용량 요약 테이블의 행에는 디버깅 세션 중에 만든 스냅샷이 나열됩니다.  
  
 행의 열은 프로젝트 속성에서 선택한 디버깅 모드(.NET, 네이티브 또는 혼합(.NET 및 네이티브))에 따라 달라집니다.  
  
- **관리되는 개체**및 **네이티브 할당** 열에는 스냅샷을 만들 때 .NET 및 네이티브 메모리의 개체 수가 표시됩니다.  
  
- **관리되는 힙 크기** 및 **네이티브 힙 크기** 열에는 .NET 및 네이티브 힙의 바이트 수가 표시됩니다.  
  
- 여러 스냅샷을 만든 경우 요약 테이블의 셀에 행 스냅샷과 이전 스냅샷 간의 값 변경 내용이 포함됩니다.  
  
   ![메모리 요약 표 셀](../profiling/media/dbgdiag-mem-summarytablecell.png "DBGDIAG_MEM_SummaryTableCell")  
  
  **세부 정보 보고서를 보려면**  
  
- 선택한 스냅샷의 세부 정보만 보려면 현재 링크를 선택합니다.  
  
- 현재 스냅샷과 이전 스냅샷 간의 차이 정보를 보려면 변경 링크를 선택합니다.  
  
  보고서는 별도의 창에 나타납니다.  
  
## <a name="memory-usage-details-reports"></a>메모리 사용량 정보 보고서  
  
### <a name="managed-types-reports"></a>관리되는 형식 보고서  
 메모리 사용량 요약 테이블에서 **관리되는 개체** 또는 **관리되는 힙 크기** 셀의 현재 링크를 선택합니다.  
  
 ![디버거 관리되는 형식 보고서 &#45; 루트 경로](../profiling/media/dbgdiag-mem-managedtypesreport-pathstoroot.png "DBGDIAG_MEM_ManagedTypesReport_PathsToRoot")  
  
 위쪽 창에는 형식에서 참조되는 모든 개체의 크기(**포함 크기**)를 포함하여 스냅샷의 형식 개수 및 크기가 표시됩니다.  
  
 아래쪽 창의 **루트 경로** 트리에는 위쪽 창에서 선택한 형식을 참조하는 개체가 표시됩니다. .NET Framework 가비지 수집기는 개체를 참조하는 마지막 형식이 해제된 경우에만 개체에 대한 메모리를 정리합니다.  
  
 **참조 된 형식** 트리에는 위쪽 창에서 선택한 형식이 보유하고 있는 참조가 표시됩니다.  
  
 ![관리되는 참조 형식 보고서 뷰](../profiling/media/dbgdiag-mem-managedtypesreport-referencedtypes.png "DBGDIAG_MEM_ManagedTypesReport_ReferencedTypes")  
  
 위쪽 창에서 선택한 형식의 인스턴스를 표시하려면 ![인스턴스 아이콘](../profiling/media/dbgdiag-mem-instanceicon.png "DBGDIAG_MEM_InstanceIcon") 아이콘을 선택합니다.  
  
 ![인스턴스 뷰](../profiling/media/dbgdiag-mem-managedtypesreport-instances.png "DBGDIAG_MEM_ManagedTypesReport_Instances")  
  
 **인스턴스** 뷰에는 위쪽 창의 스냅샷에서 선택한 개체의 인스턴스가 표시됩니다. 루트 경로 및 참조된 개체 창에는 선택한 인스턴스를 참조하는 개체 및 선택한 인스턴스가 참조하는 형식이 표시됩니다. 스냅샷이 만들어진 지점에서 디버거가 중지되면 값 셀을 마우스로 가리켜 도구 설명에 개체 값을 표시할 수 있습니다.  
  
### <a name="native-type-reports"></a>네이티브 형식 보고서  
 **진단 도구** 창의 메모리 사용량 요약 테이블에서 **네이티브 할당** 또는 **네이티브 힙 크기** 셀의 현재 링크를 선택합니다.  
  
 ![네이티브 형식 뷰](../profiling/media/dbgdiag-mem-native-typesview.png "DBGDIAG_MEM_Native_TypesView")  
  
 **형식 뷰** 에는 스냅샷의 형식 수와 크기가 표시됩니다.  
  
- 선택한 형식의 인스턴스 아이콘(![개체 형식 열의 인스턴스 아이콘](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon"))을 선택하여 스냅샷에서 선택한 형식의 개체에 대한 정보를 표시합니다.  
  
     **인스턴스** 뷰에는 선택한 형식의 각 인스턴스가 표시됩니다. 인스턴스를 선택하면 **할당 호출 스택** 창에 인스턴스를 만든 호출 스택이 표시됩니다.  
  
     ![인스턴스 뷰](../profiling/media/dbgdiag-mem-native-instances.png "DBGDIAG_MEM_Native_Instances")  
  
- **뷰 모드** 에서 **스택 뷰** 를 선택하여 선택한 형식에 대한 할당 스택을 확인합니다.  
  
     ![뷰 모드](../profiling/media/dbgdiag-mem-native-stacksview.png "DBGDIAG_MEM_Native_StacksView")  
  
### <a name="change-diff-reports"></a>변경(차이) 보고서  
  
- **진단 도구** 창의 **메모리 사용량** 탭에서 요약 테이블 셀의 변경 링크를 선택합니다.  
  
   ![변경 &#40;dif&#41;f 보고서를 선택 합니다.](../profiling/media/dbgdiag-mem-choosediffreport.png "DBGDIAG_MEM_ChooseDiffReport")  
  
- 관리되는 보고서 또는 네이티브 보고서의 **비교 대상** 목록에서 스냅샷을 선택합니다.  
  
   ![비교 목록에서 스냅샷 선택](../profiling/media/dbgdiag-mem-choosecompareto.png "DBGDIAG_MEM_ChooseCompareTo")  
  
  변경 보고서는 기본 스냅샷 값과 비교 스냅샷 간의 차이를 표시하는 열( **(차이)** 로 표시됨)을 기본 보고서에 추가합니다. 네이티브 형식 뷰 차이 보고서가 표시되는 모양은 다음과 같습니다.  
  
  ![네이티브 형식 Diff 뷰](../profiling/media/dbgdiag-mem-native-typesviewdiff.png "DBGDIAG_MEM_Native_TypesViewDiff")  
  
## <a name="blogs-and-videos"></a>블로그 및 동영상  
 [Visual Studio 2015의 진단 도구 디버거 창](https://devblogs.microsoft.com/devops/diagnostic-tools-debugger-window-in-visual-studio-2015/)  
  
 [블로그: Visual Studio 2015에서 디버그하는 동안 메모리 사용 도구](https://devblogs.microsoft.com/devops/memory-usage-tool-while-debugging-in-visual-studio-2015/)  
  
 [Visual C++ 블로그: VS2015 Preview의 기본 메모리 진단](https://devblogs.microsoft.com/cppblog/native-memory-diagnostics-in-vs2015-preview/)  
  
 [Visual C++ 블로그: Visual Studio 2015 CTP용 기본 메모리 진단 도구](https://devblogs.microsoft.com/cppblog/native-memory-diagnostic-tools-for-visual-studio-14-ctp/)
