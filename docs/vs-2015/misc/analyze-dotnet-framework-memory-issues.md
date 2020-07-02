---
title: .NET Framework 메모리 문제 분석 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.diagnostics.managedmemoryanalysis
ms.assetid: 43341928-9930-48cf-a57f-ddcc3984b787
caps.latest.revision: 9
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e89b3f04a3e0e1dcd0cc29e57e09b1c71fbc2279
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545550"
---
# <a name="analyze-net-framework-memory-issues"></a>.NET Framework 메모리 문제 분석
관리되는 Visual Studio 메모리 분석기를 사용하여 .NET Framework 코드에서 메모리 누수 및 비효율적인 메모리 사용을 찾습니다. 대상 코드의 최소 .NET Framework 버전은 .NET Framework 4.5입니다.  
  
 메모리 분석 도구는 응용 프로그램의 메모리에 있는 개체의 복사본 *인 힙 데이터로 덤프 파일* 의 정보를 분석 합니다. Visual Studio IDE에서 또는 다른 시스템 도구를 사용해 덤프(.dmp) 파일을 수집할 수 있습니다.  
  
- 단일 스냅샷을 분석하여 메모리 사용에 대한 개체 형식의 상대적 영향을 파악하고 앱에서 메모리를 비효율적으로 사용하는 코드를 찾을 수 있습니다.  
  
- 앱의 두 스냅숏을 비교 (*diff*) 하 여 코드에서 시간에 따라 메모리 사용이 증가 하는 영역을 찾을 수도 있습니다.  
  
  관리 되는 메모리 분석기에 대 한 연습은 Visual Studio ALM + Team Foundation Server 블로그의 [프로덕션에서 Visual Studio 2013를 사용 하 여 .Net 메모리 문제 진단을](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/) 참조 하세요.  
  
## <a name="contents"></a><a name="BKMK_Contents"></a> 목차  
 [.NET Framework 앱에서 메모리 사용](#BKMK_Memory_use_in__NET_Framework_apps)  
  
 [앱의 메모리 문제 식별](#BKMK_Identify_a_memory_issue_in_an_app)  
  
 [메모리 스냅숏 수집](#BKMK_Collect_memory_snapshots)  
  
 [메모리 사용 분석](#BKMK_Analyze_memory_use)  
  
## <a name="memory-use-in-net-framework-apps"></a><a name="BKMK_Memory_use_in__NET_Framework_apps"></a>.NET Framework 앱에서 메모리 사용  
 .NET Framework는 가비지 수집 런타임이므로 대부분의 앱에서 메모리 사용은 문제가 되지 않습니다. 그러나 오래 실행되는 애플리케이션(예: 웹 서비스 및 애플리케이션)과 메모리의 양이 제한된 디바이스에서 메모리에 개체가 누적되면 앱이 실행되는 디바이스와 앱의 성능에 영향을 미칠 수 있습니다. 가비지 수집기가 너무 자주 실행되거나 운영 체제에서 강제로 RAM과 디스크 간에 메모리를 이동하는 경우 과도한 메모리 사용은 애플리케이션과 컴퓨터에 리소스 부족을 일으킬 수 있습니다. 최악의 경우 앱에서 "메모리 부족" 예외가 발생할 수 있습니다.  
  
 .NET *관리 되는 힙은* 앱에서 만든 참조 개체가 저장 되는 가상 메모리 영역입니다. 개체의 수명은 GC(가비지 수집기)가 관리합니다. 가비지 수집기에서는 참조를 사용하여 메모리 블록을 차지하는 개체를 추적합니다. 개체를 만들어 변수에 할당하면 참조가 생성됩니다. 단일 개체에는 참조가 여러 개 있을 수 있습니다. 예를 들어 개체를 클래스, 컬렉션 또는 기타 데이터 구조에 추가하거나 개체를 두 번째 변수에 할당하여 개체에 대한 추가 참조를 만들 수 있습니다. 참조를 만드는 덜 확실한 방법은 개체 하나가 다른 개체의 이벤트에 처리기를 추가하도록 하는 것입니다. 이 경우 처리기가 명시적으로 제거되거나 두 번째 개체가 제거될 때까지 두 번째 개체에는 첫 번째 개체에 대한 참조가 들어 있습니다.  
  
 각 애플리케이션의 경우 GC는 애플리케이션에서 참조하는 개체를 추적하는 참조 트리를 유지 관리합니다. *참조 트리에* 는 전역 및 정적 개체 뿐만 아니라 연결 된 스레드 스택과 동적으로 인스턴스화된 개체를 포함 하는 루트 집합이 있습니다. 개체에 자신에 대한 참조가 있는 부모 개체가 하나 이상 있는 경우 해당 개체는 루트로 지정됩니다. GC는 애플리케이션에 있는 다른 개체 또는 변수가 해당 개체를 참조하지 않는 경우에만 해당 개체의 메모리를 회수할 수 있습니다.  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="identify-a-memory-issue-in-an-app"></a><a name="BKMK_Identify_a_memory_issue_in_an_app"></a>앱의 메모리 문제 식별  
 메모리 문제의 가장 눈에 띄는 증상은 앱의 성능으로 특히 시간에 따라 성능이 저하되는 경우입니다. 앱 실행 중 다른 앱의 성능 저하 역시 메모리 문제를 나타낼 수 있습니다. 메모리 문제가 의심 되는 경우 작업 관리자 또는 [Windows 성능 모니터](https://technet.microsoft.com/library/cc749249.aspx) 와 같은 도구를 사용 하 여 추가로 조사 하십시오. 예를 들어 메모리 누수의 가능한 원인으로 설명할 수 없는 메모리의 총 크기 증가를 찾습니다.  
  
 ![리소스 모니터의 지속적인 메모리 증가](../misc/media/mngdmem-resourcemanagerconsistentgrowth.png "MNGDMEM_ResourceManagerConsistentGrowth")  
  
 또한 코드에 대한 지식으로 제안할 수 있는 것보다 더 큰 메모리 스파이크를 알아챌 수도 있습니다. 이는 프로시저에서 비효율적인 메모리 사용을 나타낼 수 있습니다.  
  
 ![리소스 관리자의 메모리 스파이크](../misc/media/mngdmem-resourcemanagerspikes.png "MNGDMEM_ResourceManagerSpikes")  
  
## <a name="collect-memory-snapshots"></a><a name="BKMK_Collect_memory_snapshots"></a>메모리 스냅숏 수집  
 메모리 분석 도구는 힙 정보를 포함 하는 *덤프 파일* 의 정보를 분석 합니다. Visual Studio에서 덤프 파일을 만들거나 [Windows Sysinternals](https://technet.microsoft.com/sysinternals)의 [procdump](https://technet.microsoft.com/sysinternals/dd996900.aspx) 와 같은 도구를 사용할 수 있습니다. Visual Studio Debugger 팀 블로그에서 [덤프 란 무엇 이며, 어떤 방법으로 만드시겠습니까?](https://blogs.msdn.microsoft.com/debugger/2009/12/30/what-is-a-dump-and-how-do-i-create-one/) 를 참조 하세요.  
  
> [!NOTE]
> 대부분의 도구는 전체 힙 메모리 데이터가 포함되거나 포함되지 않은 덤프 정보를 수집할 수 있습니다. Visual Studio 메모리 분석기는 전체 힙 정보가 필요합니다.  
  
 **Visual Studio에서 덤프를 수집하려면**  
  
1. Visual Studio 프로젝트에서 시작한 프로세스에 대한 덤프 파일을 생성하거나 디버거를 실행 중인 프로세스에 연결할 수 있습니다. [실행 중인 프로세스에 연결을](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)참조 하세요.  
  
2. 실행을 중지합니다. **디버그** 메뉴에서 **모두 중단** 을 선택 하거나 예외 또는 중단점에서 디버거를 중지 합니다.  
  
3. **디버그** 메뉴에서 다른 **이름으로 덤프 저장**을 선택 합니다. 다른 이름 **으로 덤프 저장** 대화 상자에서 위치를 지정 하 고 **파일 형식** 목록에서 **힙 사용 미니 덤프** (기본값)가 선택 되어 있는지 확인 합니다.  
  
   **메모리 스냅숏 두 개를 비교하려면**  
  
   앱의 메모리 사용 증가를 분석하려면 앱의 단일 인스턴스에서 덤프 파일 두 개를 수집합니다.  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="analyze-memory-use"></a><a name="BKMK_Analyze_memory_use"></a>메모리 사용 분석  
 [개체 목록을 필터링](#BKMK_Filter_the_list_of_objects) **하&#124;** [단일 스냅숏에서의 메모리 데이터를 분석 하](#BKMK_Analyze_memory_data_in_from_a_single_snapshot) **&#124;** [두 메모리 스냅숏을 비교](#BKMK_Compare_two_memory_snapshots) 합니다.  
  
 메모리 사용 문제에 대한 덤프 파일을 분석하려면:  
  
1. Visual Studio에서 **파일**, **열기** 를 차례로 선택 하 고 덤프 파일을 지정 합니다.  
  
2. **미니 덤프 파일 요약** 페이지에서 **관리 되는 메모리 디버깅**을 선택 합니다.  
  
    ![덤프 파일 요약 페이지](../misc/media/mngdmem-dumpfilesummary.png "MNGDMEM_DumpFileSummary")  
  
   메모리 분석기에서는 디버그 세션을 시작하여 파일을 분석하고 힙 보기 페이지에 결과를 표시합니다.  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
### <a name="filter-the-list-of-objects"></a><a name="BKMK_Filter_the_list_of_objects"></a>개체 목록 필터링  
 기본적으로 메모리 분석기는 메모리 스냅샷에서 개체 목록을 필터링하여 사용자 코드인 형식 및 인스턴스만 표시하고 총 포함 크기가 총 힙 크기의 임계값 비율을 초과하는 형식만 표시합니다. **보기 설정** 목록에서 다음 옵션을 변경할 수 있습니다.  
  
|Name|설명|  
|-|-|  
|**내 코드만 사용**|내 코드만은 대부분의 공통 시스템 개체를 숨기므로 사용자가 만든 형식만 목록에 표시됩니다.<br /><br /> Visual Studio **옵션** 대화 상자에서 내 코드만 옵션을 설정할 수도 있습니다. **디버그** 메뉴에서 **옵션 및 설정**을 선택합니다. **디버깅** / **일반** 탭에서 **내 코드만**를 선택 하거나 선택을 취소 합니다.|  
|**작은 개체 축소**|**작은 개체 축소** 는 총 포함 크기가 총 힙 크기의 0.5% 미만인 모든 형식을 숨깁니다.|  
  
 **검색** 상자에 문자열을 입력 하 여 형식 목록을 필터링 할 수도 있습니다. 목록에는 이름에 문자열이 포함된 형식만 표시됩니다.  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
### <a name="analyze-memory-data-in-from-a-single-snapshot"></a><a name="BKMK_Analyze_memory_data_in_from_a_single_snapshot"></a>단일 스냅숏에서의 메모리 데이터 분석  
 Visual Studio는 새 디버깅 세션을 시작하여 파일을 분석하고 힙 보기 창에 메모리 데이터를 표시합니다.  
  
 ![개체 형식 목록](../misc/media/dbg-mma-objecttypelist.png "DBG_MMA_ObjectTypeList")  
  
 ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
#### <a name="object-type-table"></a>개체 형식 테이블  
 상단 테이블에는 메모리에 저장된 개체 형식이 나열됩니다.  
  
- **Count** 는 스냅숏에서 형식의 인스턴스 수를 표시 합니다.  
  
- **크기 (바이트)** 는 참조를 보유 하는 개체의 크기를 제외 하 고 형식의 모든 인스턴스 크기입니다. Component  
  
- 포함 **크기 (바이트)** 에는 참조 된 개체의 크기가 포함 됩니다.  
  
  **개체** 형식 열에서 인스턴스 아이콘 (![개체 형식 열의 인스턴스 아이콘](../misc/media/dbg-mma-instancesicon.png "DBG_MMA_InstancesIcon"))을 선택 하 여 해당 형식의 인스턴스 목록을 볼 수 있습니다.  
  
#### <a name="instance-table"></a>인스턴스 테이블  
 ![인스턴스 테이블](../misc/media/dbg-mma-instancestable.png "DBG_MMA_InstancesTable")  
  
- **인스턴스** 는 개체의 개체 식별자 역할을 하는 개체의 메모리 위치입니다.  
  
- **값** 값 형식의 실제 값을 표시 합니다. 참조 형식의 이름을 가리키면 데이터 팁에서 해당 데이터 값을 볼 수 있습니다.  
  
   ![데이터 팁의 인스턴스 값](../misc/media/dbg-mma-instancevaluesindatatip.png "DBG_MMA_InstanceValuesInDataTip")  
  
- **크기 (바이트)** 는 개체에서 참조 하는 개체의 크기를 제외 하 고 개체의 크기입니다. Component  
  
- 포함 **크기 (바이트)** 에는 참조 된 개체의 크기가 포함 됩니다.  
  
  기본적으로 형식 및 인스턴스는 **포함 크기 (바이트)** 를 기준으로 정렬 됩니다. 정렬 순서를 변경하려면 목록에서 열 머리글을 선택합니다.  
  
#### <a name="paths-to-root"></a>루트 경로  
  
- **개체 형식** 테이블에서 선택한 형식의 경우 **루트 경로** 테이블에는 해당 형식의 모든 개체에 대 한 루트 개체로 이어지는 고유한 형식 계층 구조와 계층 구조에서 해당 형식의 상위 형식에 대 한 참조 수가 표시 됩니다.  
  
- 형식의 인스턴스에서 선택한 개체의 경우 **루트 경로** 는 인스턴스에 대 한 참조를 포함 하는 실제 개체의 그래프를 표시 합니다. 개체의 이름을 가리키면 데이터 팁에서 해당 데이터 값을 볼 수 있습니다.  
  
#### <a name="referenced-types--referenced-objects"></a>참조된 형식/참조된 개체  
  
- **개체 형식** 테이블에서 선택한 형식의 경우 **참조 되** 는 형식 탭에는 선택한 형식의 모든 개체가 보유 하 고 있는 참조 된 형식의 크기와 수가 표시 됩니다.  
  
- 선택한 형식의 인스턴스를 **참조** 하는 경우 선택한 인스턴스에서 보유 하 고 있는 개체를 표시 합니다. 이름을 가리키면 데이터 팁에서 해당 데이터 값을 볼 수 있습니다.  
  
  **순환 참조**  
  
  개체는 첫 번째 개체를 직접적 또는 간접적으로 참조하는 두 번째 개체를 참조할 수 있습니다. 이 상황이 발생 하면 메모리 분석기는 참조 경로 확장을 중지 하 고 첫 번째 개체의 목록에 **[Cycle 검색]** 주석을 추가 하 고 중지 합니다.  
  
  **루트 형식**  
  
  메모리 분석기에서는 보유 중인 참조의 종류를 설명하는 루트 개체에 다음과 같은 주석을 추가합니다.  
  
|주석|설명|  
|----------------|-----------------|  
|**정적 변수** `VariableName`|정적 변수. `VariableName`은 변수의 이름입니다.|  
|**종료 핸들**|종료자 큐의 참조입니다.|  
|**지역 변수**|지역 변수입니다.|  
|**강력한 핸들**|개체 참조 테이블의 강력한 참조에 대한 핸들입니다.|  
|**동기화. 고정 된 핸들**|개체 핸들 테이블의 비동기 고정된 개체입니다.|  
|**종속 핸들**|개체 핸들 테이블의 종속 개체입니다.|  
|**고정된 핸들**|개체 핸들 테이블의 고정된 강력한 참조입니다.|  
|**RefCount 핸들**|개체 핸들 테이블의 참조 횟수가 계산되는 개체입니다.|  
|**SizedRef 핸들**|가비지 컬렉션 시 모든 개체 및 개체 루트의 집합 클로저의 대략적인 크기를 유지하는 강력한 핸들입니다.|  
|**고정된 지역 변수**|고정된 지역 변수입니다.|  
  
### <a name="compare-two-memory-snapshots"></a><a name="BKMK_Compare_two_memory_snapshots"></a>두 메모리 스냅숏 비교  
 프로세서의 덤프 파일 두 개를 비교하여 메모리 누수의 원인이 될 수 있는 개체를 찾을 수 있습니다. 첫 번째(이전) 및 두 번째(이후) 파일 컬렉션 간의 간격은 누수된 개체 수 증가를 명백하게 확인하기에 충분할 정도로 커야 합니다. 두 파일을 비교하려면 다음 단계를 수행하세요.  
  
1. 두 번째 덤프 파일을 열고 **미니 덤프 파일 요약** 페이지에서 **관리 되는 메모리 디버깅** 을 선택 합니다.  
  
2. 메모리 분석 보고서 페이지에서 **기준 선택** 목록을 연 다음 **찾아보기** 를 선택 하 여 첫 번째 덤프 파일을 지정 합니다.  
  
   분석기는 보고서의 위쪽 창에 열을 추가 하 여 해당 형식의 **개수**, **크기**및 **포함 크기** 차이를 이전 스냅숏의 값과 비교 합니다.  
  
   ![형식 목록의 Diff 열](../misc/media/mngdmem-diffcolumns.png "MNGDMEM_DiffColumns")  
  
   **참조 개수 Diff** 열도 **루트 테이블 경로** 에 추가 됩니다.  
  
   ![맨 위로 이동](../debugger/media/pcs-backtotop.png "PCS_BackToTop") [목차](#BKMK_Contents)  
  
## <a name="see-also"></a>참고 항목  
 [VS ALM TFS 블로그: Visual Studio 2013을 사용 하 여 프로덕션에서 .NET 메모리 문제 진단](https://devblogs.microsoft.com/devops/using-visual-studio-2013-to-diagnose-net-memory-issues-in-production/)   
 [Channel 9 &#124; Visual Studio TV &#124; 관리 되는 메모리 분석](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Managed-Memory-Analysis)   
 [Channel 9 &#124; Visual Studio 도구 상자 &#124; 관리 되는 메모리 분석 Visual Studio 2013](https://channel9.msdn.com/Shows/Visual-Studio-Toolbox/Managed-Memory-Analysis-in-Visual-Studio-2013)