---
title: CPU 사용량 분석 | Microsoft Docs
ms.custom: seodec18
ms.date: 04/02/2020
ms.topic: how-to
ms.assetid: 7501a20d-04a1-480f-a69c-201524aa709d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e5ab97f3db8e5d44aa649455c313a5681ed93c8c
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543392"
---
# <a name="analyze-cpu-usage"></a>CPU 사용량 분석

앱의 성능 문제를 조사하기 위한 좋은 방법은 CPU 사용량을 이해하는 것입니다. **CPU 사용량** 성능 도구는 C++, C#/Visual Basic 및 JavaScript 앱에서 코드 실행에 소요된 CPU 시간 및 백분율을 보여줍니다.

**CPU 사용량** 도구는 열려 있는 Visual Studio 프로젝트, 설치된 Microsoft Store 앱에서 실행하거나 실행 중인 앱 또는 프로세스에 연결할 수 있습니다. 자세한 내용은 [디버거를 사용하거나 사용하지 않고 프로파일링 도구 실행](../profiling/running-profiling-tools-with-or-without-the-debugger.md)을 참조하세요.

디버깅을 사용하거나 사용하지 않고 **CPU 사용량** 도구를 실행할 수 있습니다. 디버거에서 CPU 프로파일링을 설정하거나 해제할 수 있으며 CPU 사용량에 대한 함수별 분석을 볼 수 있습니다. 실행이 일시 중지된 경우 CPU 사용량 결과를 볼 수 있습니다(예: 중단점에서).

다음 지침은 Visual Studio **성능 프로파일러**를 사용하여 디버거 없이 **CPU 사용량** 도구를 사용하는 방법을 보여줍니다. 이 예제에서는 로컬 머신에서 릴리스 빌드를 사용합니다. 릴리스 빌드는 실제 앱 성능을 가장 잘 보여줍니다. 디버그 빌드를 사용하여 CPU 사용량을 분석하려면 [초보자를 위한 성능 프로파일링 지침](../profiling/beginners-guide-to-performance-profiling.md)을 참조하세요.

일반적으로 로컬 머신은 설치된 앱 실행을 가장 잘 복제합니다. Windows Phone 앱의 경우 디바이스에서 직접 데이터를 수집하면 가장 정확한 데이터가 제공됩니다. 원격 디바이스에서 데이터를 수집하려면 원격 데스크톱 연결을 통하지 않고 디바이스에서 직접 앱을 실행합니다.

>[!NOTE]
>[성능 프로파일러](../profiling/profiling-feature-tour.md)를 사용하려면 Windows 7 이상이 필요합니다.

## <a name="collect-cpu-usage-data"></a>CPU 사용량 데이터 수집

1. Visual Studio 프로젝트에서 솔루션 구성을 **릴리스**로 설정하고 **로컬 Windows 디버거**(또는 **로컬 머신**)를 배포 대상으로 선택합니다.

    ![릴리스 및 로컬 컴퓨터 선택](../profiling/media/cpuuse_selectreleaselocalmachine.png "릴리스 및 로컬 컴퓨터 선택")

1. **디버그** > **성능 프로파일러**를 선택합니다.

1. **사용 가능한 도구**에서 **CPU 사용량**을 선택한 다음, **시작**을 선택합니다.

    ![CPU 사용량 선택](../profiling/media/cpuuse_lib_choosecpuusage.png "CPU 사용량 선택")

4. 앱이 시작되면 진단 세션이 시작되고 CPU 사용량 데이터가 표시됩니다. 데이터 수집이 완료되면 **컬렉션 중지**를 선택합니다.

   ![CPU 사용량 데이터 수집 중지](../profiling/media/cpu_use_wt_stopcollection.png "CPU 사용량 데이터 수집 중지")

   CPU 사용량 도구에서 데이터를 분석하고 보고서를 표시합니다.

   ![CPU 사용량 보고서](../profiling/media/cpu_use_wt_report.png "CPU 사용량 보고서")

## <a name="analyze-the-cpu-usage-report"></a>CPU 사용량 보고서 분석

진단 보고서는 **총 CPU**를 기준으로 가장 높은 CPU에서 가장 낮은 CPU로 정렬됩니다. 열 머리글을 선택하여 정렬 순서 또는 정렬 열을 변경합니다. **필터** 드롭다운을 사용하여 표시할 스레드를 선택하거나 선택 취소하고, **검색** 상자를 사용하여 특정 스레드 또는 노드를 검색합니다.

::: moniker range=">=vs-2019"
Visual Studio 2019부터 **실행 부하 과다 경로 확장** 및 **실행 부하 과다 경로 표시** 단추를 클릭하여 호출 트리 뷰에서 CPU 사용률이 가장 높은 함수 호출을 볼 수 있습니다.
::: moniker-end

### <a name="cpu-usage-data-columns"></a><a name="BKMK_Call_tree_data_columns"></a> CPU 사용량 데이터 열

|이름|설명|
|-|-|
|**총 CPU [단위, %]**|![총 % 데이터 수식](../profiling/media/cpu_use_wt_totalpercentequation.png "CPU_USE_WT_TotalPercentEquation")<br /><br /> 선택한 시간 범위에서 함수 호출 및 함수가 호출한 함수에 의해 사용되는 밀리초 및 CPU 백분율입니다. 이 값은 시간 범위의 총 CPU 활동을 사용 가능한 총 CPU와 비교하는 **CPU 사용률** 타임라인 그래프와 다릅니다.|
|**셀프 CPU [단위, %]**|![자체 % 수식](../profiling/media/cpu_use_wt_selflpercentequation.png "CPU_USE_WT_SelflPercentEquation")<br /><br /> 함수에 의해 호출되는 함수를 제외하고 선택한 시간 범위에서 함수를 호출하는 데 사용되는 밀리초 및 CPU 백분율입니다.|
|**모듈**|함수를 포함하는 모듈의 이름입니다.

### <a name="the-cpu-usage-call-tree"></a><a name="BKMK_The_CPU_Usage_call_tree"></a> CPU 사용량 호출 트리

호출 트리를 보려면 보고서에서 부모 노드를 선택합니다. **CPU 사용량** 페이지가 **호출자/호출 수신자** 보기에 열립니다. **현재 보기** 드롭다운 목록에서 **호출 트리**를 선택합니다.

#### <a name="call-tree-structure"></a><a name="BKMK_Call_tree_structure"></a> 호출 트리 구조

::: moniker range=">=vs-2019"
![호출 트리 구조](../profiling/media/vs-2019/cpu-use-wt-getmaxnumbercalltree-annotated.png "호출 트리 구조")
::: moniker-end
::: moniker range="vs-2017"
![호출 트리 구조](../profiling/media/cpu_use_wt_getmaxnumbercalltree_annotated.png "호출 트리 구조")
::: moniker-end

|이미지|설명|
|-|-|
|![1단계](../profiling/media/procguid_1.png "ProcGuid_1")|CPU 사용량 호출 트리의 최상위 노드는 의사 노드입니다.|
|![2단계](../profiling/media/procguid_2.png "ProcGuid_2")|대다수의 앱에서 **외부 코드 표시** 옵션을 사용하지 않도록 설정한 경우 두 번째 수준 노드가 **[External Code]** 노드입니다. 노드에는 앱 시작 및 중지, UI 그리기, 스레드 일정 제어 및 앱에 기타 낮은 수준 서비스를 제공하는 시스템과 프레임워크 코드가 포함되어 있습니다.|
|![3단계](../profiling/media/procguid_3.png "ProcGuid_3")|두 번째 수준 노드의 자식은 두 번째 수준 시스템과 프레임워크 코드가 호출하거나 만드는 사용자 코드 메서드 및 비동기 루틴입니다.|
|![4단계](../profiling/media/procguid_4.png "ProcGuid_4")|메서드의 자식 노드에는 부모 메서드 호출에 대한 데이터만 있습니다. **외부 코드 표시** 가 사용하지 않도록 설정되어 있으면 앱 메서드에 **[External Code]** 노드를 포함할 수 있습니다.|

#### <a name="external-code"></a><a name="BKMK_External_Code"></a> 외부 코드

코드로 실행되는 시스템과 프레임워크 함수를 *외부 코드*라고 합니다. 외부 코드 함수는 앱 시작 및 중지, UI 그리기, 스레딩 제어, 기타 낮은 수준 서비스를 앱에 제공합니다. 대부분의 경우 외부 코드에 관심이 없으므로 CPU 사용량 호출 트리에서 사용자 메서드의 외부 함수를 하나의 **[External Code]** 노드로 수집합니다.

외부 코드의 호출 경로를 보려면 기본 진단 보고서 페이지(오른쪽 창)의 **필터** 드롭다운에서 **외부 코드 표시**를 선택한 다음, **적용**을 선택합니다. **CPU 사용량** 페이지의 **호출 트리** 보기와 외부 코드 호출을 확장합니다. (**필터** 드롭다운은 자세한 보기가 아닌 기본 진단 페이지에서 사용할 수 있습니다.)

![외부 코드 표시](../profiling/media/cpu_use_wt_filterview.png "외부 코드 표시")

여러 외부 코드 호출 체인은 깊이 중첩되어 있으므로 체인 너비가 **함수 이름** 열의 표시 너비를 초과할 수 있습니다. 그러면 함수 이름이 **...** 로 나타납니다.

![호출 트리에 중첩된 외부 코드](../profiling/media/cpu_use_wt_showexternalcodetoowide.png "호출 트리에 중첩된 외부 코드")

찾고자 하는 함수 이름을 찾으려면 검색 상자를 사용합니다. 선택한 줄 위로 마우스를 가져가거나 가로 스크롤 막대를 사용하여 데이터를 봅니다.

::: moniker range=">=vs-2019"
![중첩된 외부 코드 검색](../profiling/media/vs-2019/cpu-use-wt-showexternalcodetoowide-found.png "중첩된 외부 코드 검색")
::: moniker-end
::: moniker range="vs-2017"
![중첩된 외부 코드 검색](../profiling/media/cpu_use_wt_showexternalcodetoowide_found.png "중첩된 외부 코드 검색")
::: moniker-end

### <a name="asynchronous-functions-in-the-cpu-usage-call-tree"></a><a name="BKMK_Asynchronous_functions_in_the_CPU_Usage_call_tree"></a> CPU 사용량 호출 트리의 비동기 함수

 컴파일러에서 비동기 메서드가 발생하면 메서드 실행을 제어하는 숨겨진 클래스를 만듭니다. 개념적으로 클래스는 상태 머신입니다. 클래스에 원래 메서드를 비동기식으로 호출하는 컴파일러 생성 함수와 이를 실행하는 데 필요한 콜백, 스케줄러 및 반복기가 있습니다. 부모 메서드가 원래 메서드를 호출하면 컴파일러는 부모의 실행 컨텍스트에서 메서드를 제거하고, 앱 실행을 제어하는 시스템과 프레임워크 코드의 컨텍스트에서 숨겨진 클래스 메서드를 실행합니다. 비동기 메서드는 일반적으로 하나 이상의 서로 다른 스레드에서 실행되지만 항상 그렇지는 않습니다. 이 코드는 트리의 상단 노드 바로 아래의 **[External Code]** 노드의 자식으로 **CPU 사용량** 호출 트리에 나타납니다.

다음 예제에서 **[External Code]** 아래에 있는 처음 두 노드는 상태 시스템 클래스의 컴파일러 생성 메서드입니다. 세 번째 노드는 원래 메서드에 대한 호출입니다.

![비동기 노드](media/cpu_use_wt_getmaxnumberasync_selected.png "비동기 노드")

생성된 메서드를 확장하면 진행 상황이 표시됩니다.

![확장된 비동기 노드](media/cpu_use_wt_getmaxnumberasync_expandedcalltree.png "확장된 비동기 노드")

- `MainPage::GetMaxNumberAsyncButton_Click`은 작업 값 목록을 관리하고, 결과의 최댓값을 계산하고, 출력을 표시합니다.

- `MainPage+<GetMaxNumberAsyncButton_Click>d__3::MoveNext` 는 `GetNumberAsync`에 대한 호출을 래핑하는 48개 작업을 예약 및 시작하는 데 필요한 활동을 보여 줍니다.

- `MainPage::<GetNumberAsync>b__b`는 `GetNumber`를 호출하는 작업의 활동을 보여줍니다.
