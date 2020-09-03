---
title: 디버그하지 않는 경우의 메모리 사용량2 | Microsoft 문서
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: 24238fc0-40b8-4079-8579-698211db9a26
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ce7d30b66106b8d0d861fcf782a77ee7f461196b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85532043"
---
# <a name="memory-usage-without-debugging"></a>디버그하지 않는 경우의 메모리 사용량
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

디버그하지 않고 **메모리 사용량** 도구를 사용하여 다음을 수행할 수 있습니다.  
  
- 시나리오를 개발하는 동안 Visual Studio에서 직접 앱의 메모리 사용 권한을 모니터링합니다.  
  
- 앱의 메모리 상태에 대한 자세한 스냅샷을 만듭니다.  
  
- 스냅샷을 비교하여 메모리 문제의 근본 원인을 찾습니다.  
  
  이 항목에서는 메모리 사용량 도구를 사용하여 Windows 유니버설 XAML 앱을 분석하는 방법에 대해 설명합니다. JavaScript 및 HTML을 사용하는 Windows 유니버설 앱에서 메모리 사용을 분석하려는 경우 [메모리 사용 분석(JavaScript)](https://msdn.microsoft.com/library/windows/apps/jj819176.aspx)을 참조하세요.  
  
## <a name="start-a-memory-usage-diagnostic-session"></a><a name="BKMK_Start_a_Memory_Usage_diagnostic_session"></a> 메모리 사용량 진단 세션 시작  
  
1. Visual Studio에서 C# 유니버설 Windows 프로젝트를 엽니다.  
  
2. 메뉴 모음에서 **디버그 / 성능 프로파일러... **를 선택합니다.  
  
3. **메모리 사용량**을 선택한 다음 페이지 맨 아래에서 **시작** 단추를 선택합니다.  
  
     ![메모리 사용량 진단 세션 시작](../profiling/media/memuse-start-diagnosticssession.png "MEMUSE_Start_DiagnosticsSession")  
  
## <a name="monitor-memory-use"></a><a name="BKMK_Monitor_memory_use"></a> 메모리 사용 모니터링  
 **메모리 사용량** 도구로 문제를 찾아서 해결할 수 있는 상세 보고서를 생성할 수 있지만, 이 도구를 사용하여 적극적으로 개발 중인 시나리오에 대한 실시간 메모리 영향을 연구할 수도 있습니다.  
  
 진단 세션을 시작 하면 앱이 시작 되 고 **진단 도구** 창에 앱의 메모리 사용에 대 한 타임 라인 그래프가 표시 됩니다.  
  
 ![메모리 사용량 개요 페이지](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
 이 타임라인 그래프에는 앱을 실행할 때 앱의 메모리 변동 사항이 표시됩니다. 그래프에 스파이크가 있으면 일반적으로 일부 코드에서 데이터를 수집하거나 생성한 다음 처리가 완료되면 삭제함을 나타냅니다. 큰 스파이크는 최적화할 수 있는 영역을 나타냅니다. 비효율적인 메모리 사용량 또는 메모리 누수를 나타낼 수 있기 때문에 더욱 걱정스러운 점은 되돌릴 수 없는 메모리 사용량이 증가하는 문제입니다.  
  
### <a name="close-a-monitoring-session"></a><a name="BKMK_Close_a_monitoring_session"></a> 모니터링 세션 닫기  
 ![수집 중지](../profiling/media/memuse-stopcollection.png "MEMUSE__StopCollection")  
  
 보고서를 생성하지 않고 모니터링 세션을 중지하려면 진단 창을 닫기만 하면 됩니다. 메모리 스냅샷을 만들 때 보고서를 생성하려면 **중지**를 선택합니다.  
  
## <a name="take-snapshots-of-the-memory-state-of-your-app"></a><a name="BKMK_Take_snapshots_to_analyze_the_memory_state_of_your_app"></a> 앱의 메모리 상태 스냅샷 만들기  
 조사할 메모리 관련 문제를 발견하면 진단 세션이 진행되는 동안 스냅샷을 만들어서 특정 순간의 메모리 개체를 캡처할 수 있습니다. 앱에서 무수히 많은 개체 유형을 사용하므로 시나리오 하나에 대한 분석에 집중하려고 할 수 있습니다. 또한 메모리 문제가 나타나기 전 앱의 기본 스냅샷을 만들거나, 첫 번째 문제가 발생한 이후의 다른 스냅샷을 만들거나, 시나리오를 반복할 수 있는 경우 하나 이상의 추가 스냅샷을 만드는 것도 좋습니다.  
  
 스냅샷을 수집하려면 새로운 진단 세션을 시작합니다. 메모리 데이터를 캡처하려는 경우 **스냅샷 만들기**를 선택합니다. 보고서를 생성하려면 **중지**를 선택합니다.  
  
## <a name="memory-usage-overview-page"></a><a name="BKMK_Memory_Usage_overview_page"></a> 메모리 사용량 개요 페이지  
 데이터 컬렉션을 중지한 후 메모리 사용량 도구에서 앱을 중지하고 개요 보고서를 표시합니다.  
  
 ![메모리 사용량 개요 페이지](../profiling/media/memuse-reportoverview.png "MEMUSE__ReportOverview")  
  
### <a name="memory-usage-snapshot-views"></a><a name="BKMK_Memory_Usage_snapshot_views"></a> 메모리 사용량 스냅샷 뷰  
 스냅샷 뷰를 사용하여 새 Visual Studio 창에서 자세한 보고서를 엽니다. 다음과 같은 두 종류의 스냅샷 뷰가 있습니다.  
  
- [스냅샷 정보 보고서](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_details_reports)에서는 한 스냅샷의 형식 및 인스턴스를 보여 줍니다.  
  
- [스냅샷 차이(diff) 보고서](../profiling/memory-usage-without-debugging2.md#BKMK_Snapshot_difference__diff__reports)에서는 두 스냅샷의 형식 및 인스턴스를 비교합니다.  
  
  ![스냅샷 보기 링크](../profiling/media/memuse-snapshotview-numbered.png "MEMUSE__SnapshotView_Numbered")  
  
  스냅샷 뷰 그림에서 번호가 있는 항목은 메모리 사용량 보고서 뷰를 여는 링크입니다.  
  
|이미지|설명|  
|-|-|  
|![1단계](../profiling/media/procguid-1.png "ProcGuid_1")|링크 텍스트는 스냅샷을 만들 때 메모리의 총 바이트 수를 보여 줍니다.<br /><br /> 이 링크를 선택하면 유형 인스턴스의 총 크기별로 정렬된 스냅샷 정보 보고서가 표시됩니다.|  
|![2단계](../profiling/media/procguid-2.png "ProcGuid_2")|링크 텍스트는 스냅샷을 만들었을 때의 총 메모리 개체 수를 보여 줍니다.<br /><br /> 이 링크를 선택하면 유형 인스턴스의 개수별로 정렬된 스냅샷 정보 보고서가 표시됩니다.|  
|![3단계](../profiling/media/procguid-3.png "ProcGuid_3")|링크 텍스트는 현재 이 스냅샷의 총 메모리 개체 크기와 이전 스냅샷의 총 크기 간의 차이를 보여 줍니다.<br /><br /> 이 스냅샷의 메모리 크기가 이전 스냅샷보다 크면 링크 텍스트는 양수이고 작으면 음수입니다. 링크 텍스트 **기본**은 이 스냅샷이 진단 세션의 첫 번째 스냅샷임을 나타냅니다. **차이 없음**은 차이가 0임을 나타냅니다.<br /><br /> 이 링크를 선택하면 유형 인스턴스의 총 크기 차이별로 정렬된 스냅샷 차이 보고서가 표시됩니다.|  
|![4단계](../profiling/media/procguid-4.png "ProcGuid_4")|링크 텍스트는 이 스냅샷의 총 메모리 개체 수와 이전 스냅샷의 개체 수 간의 차이를 보여 줍니다.<br /><br /> 이 링크를 선택하면 유형 인스턴스의 총 개수 차이별로 정렬된 스냅샷 차이 보고서가 표시됩니다.|  
  
## <a name="snapshot-reports"></a><a name="BKMK_Snapshot_reports"></a> 스냅샷 보고서  
 ![메모리 사용량 스냅샷 보고서](../profiling/media/memuse-snapshotreport-all.png "MEMUSE_SnapshotReport_All")  
  
### <a name="snapshot-report-trees"></a><a name="BKMK_Snapshot_report_trees"></a> 스냅샷 보고서 트리  
  
#### <a name="managed-heap"></a><a name="BKMK_Managed_Heap"></a> 관리되는 힙  
 관리되는 힙 트리 [관리되는 힙 트리(스냅샷 정보)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_details_) 및 [관리되는 힙 트리(스냅샷 차이)](../profiling/memory-usage-without-debugging2.md#BKMK_Managed_Heap_tree__Snapshot_diff_)에서는 보고서의 형식 및 인스턴스를 보여 줍니다. 형식 또는 인스턴스를 선택하면 선택한 항목에 대한 **루트 경로** 및 **참조 개체** 트리가 표시됩니다.  
  
#### <a name="paths-to-root"></a><a name="BKMK_Paths_to_Root"></a> 루트 경로  
 [루트 경로 트리(스냅샷 정보)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_details_) 및 [루트 경로 트리(스냅샷 차이)](../profiling/memory-usage-without-debugging2.md#BKMK_Paths_to_Root_tree__Snapshot_diff_)에서는 형식 또는 인스턴스를 참조하는 개체의 체인을 보여 줍니다. .NET Framework 가비지 수집기는 개체에 대한 모든 참조가 해제된 경우에만 개체에 대한 메모리를 정리합니다.  
  
#### <a name="referenced-objects"></a><a name="BKMK_Referenced_Objects"></a> 참조된 개체  
 [참조된 개체 트리(스냅샷 정보)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_details_) 및 [참조된 개체 트리(스냅샷 차이)](../profiling/memory-usage-without-debugging2.md#BKMK_Referenced_Objects_tree__Snapshot_diff_)에서는 선택한 형식 또는 인스턴스가 참조하는 개체를 보여 줍니다.  
  
### <a name="object-type-and-instance-fields"></a><a name="BKMK_Object_Type_and_Instance_fields"></a> 개체 형식 및 인스턴스 필드  
 **개체 형식** 항목에 자식 항목이 있으면 화살표 아이콘을 선택하여 표시할 수 있습니다. **개체 형식** 텍스트의 색상이 파란색이면 해당 항목을 선택하여 소스 코드 파일에서 해당 개체로 이동할 수 있습니다. 소스 파일은 별도의 창에서 열립니다.  
  
 인스턴스 이름은 메모리 사용량 도구에서 생성하는 고유한 ID입니다.  
  
 쉽게 식별할 수 없는 형식이 있거나 이러한 형식이 코드와 어떻게 관련되는지 모르는 경우 개체의 소유권 체인과 관련되어 있기 때문에 메모리 사용량 도구에서 표시하는 .NET 프레임워크, 운영 체제 또는 컴파일러의 개체일 수 있습니다.  
  
### <a name="report-tree-filters"></a><a name="BKMK_Report_tree_filters_"></a> 보고서 트리 필터  
 대다수 앱에는 굉장히 다양한 유형이 있는데, 이 중 대부분의 유형에는 앱 개발자가 거의 관심을 두지 않습니다. **메모리 사용량** 도구는 **관리되는 힙**과 **루트 경로** 트리에서 이러한 형식을 대부분 숨기는 데 사용할 수 있는 필터 두 개를 정의합니다. 또한 유형 이름별로 트리를 필터링할 수도 있습니다.  
  
 ![옵션 정렬 및 필터링](../profiling/media/memuse-sortandfilter.png "MEMUSE_SortAndFilter")  
  
#### <a name="filter"></a><a name="BKMK_Filter"></a> 필터가  
 **필터** 상자에 문자열을 입력하여 지정한 텍스트가 포함된 형식으로 트리 표시를 제한합니다. 필터는 대/소문자를 구분하지 않고 유형 이름의 모든 부분에서 지정한 문자열을 인식합니다.  
  
#### <a name="collapse-small-objects"></a><a name="BKMK_Collapse_Small_Objects"></a> 작은 개체 축소  
 이 필터를 적용하면 **크기(바이트)** 가 총 스냅샷 메모리 크기의 0.5%보다 작은 형식이 **관리되는 힙** 목록에서 숨겨집니다.  
  
#### <a name="just-my-code"></a><a name="BKMK_Just_My_Code"></a> 내 코드만  
 **내 코드만** 필터는 외부 코드로 생성된 인스턴스를 대부분 숨깁니다. 외부 유형은 운영 체제 또는 프레임워크 구성 요소에서 소유하거나 컴파일러에서 생성합니다.  
  
## <a name="snapshot-details-reports"></a><a name="BKMK_Snapshot_details_reports"></a> 스냅숏 정보 보고서  
 스냅샷 정보 보고서를 사용하여 진단 세션에서 스냅샷 하나에만 집중합니다. 정보 보고서를 열려면 다음 그림과 같이 스냅샷 뷰에서 링크 중 하나를 선택합니다. 두 링크 모두 동일한 보고서를 열지만, 보고서에서 **관리되는 힙** 트리의 시작 정렬 순서만 다릅니다. 두 경우 모두 보고서를 열고 나서 정렬 순서를 변경할 수 있습니다.  
  
 ![스냅숏 뷰의 스냅숏 보고서 링크](../profiling/media/memuse-snapshotview-snapshotdetailslinks.png "MEMUSE_SnapshotView_SnapshotDetailsLinks")  
  
- **MB** 링크는 **포함 크기(바이트)** 열을 기준으로 보고서를 정렬합니다.  
  
- **개체** 링크는 **개수** 열을 기준으로 보고서를 정렬 합니다.  
  
### <a name="managed-heap-tree-snapshot-details"></a><a name="BKMK_Managed_Heap_tree__Snapshot_details_"></a> 관리되는 힙 트리(스냅샷 정보)  
 **관리되는 힙** 트리에는 메모리에 보관된 개체의 형식이 나열됩니다. 유형에서 가장 큰 인스턴스 10개를 크기별로 정렬해서 볼 수 있도록 유형 이름을 확장할 수 있습니다. 형식 또는 인스턴스를 선택하면 선택한 항목에 대한 **루트 경로** 및 **참조 개체** 트리가 표시됩니다.  
  
 ![관리되는 힙 트리](../profiling/media/memuse-snapshotdetails-managedheaptree.png "MEMUSE__SnapshotDetails_ManagedHeapTree")  
  
|Name|설명|  
|-|-|  
|**개체 형식**|유형 이름 또는 개체 인스턴스입니다.|  
|**Count**|유형의 개체 인스턴스 수입니다. 인스턴스의 경우 이 숫자는 항상 1입니다.|  
|**크기(바이트)**|유형의 경우 인스턴스에 포함된 개체 크기를 제외한 메모리 스냅샷 유형의 모든 인스턴스 크기입니다.<br /><br /> 인스턴스의 경우 인스턴스에 포함된 개체 크기를 제외한 개체 크기입니다.|  
|**포함 크기(바이트)**|포함된 개체 크기를 비롯한 유형의 인스턴스 크기 또는 단일 인스턴스 크기입니다.|  
  
### <a name="paths-to-root-tree-snapshot-details"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_details_"></a> 루트 경로 트리(스냅샷 정보)  
 **루트 경로 트리**는 형식 또는 인스턴스를 참조하는 개체의 체인을 보여 줍니다. .NET Framework 가비지 수집기는 개체에 대한 모든 참조가 해제된 경우에만 개체에 대한 메모리를 정리합니다.  
  
 ![형식에 대 한 루트 트리 경로](../profiling/media/memuse-snapshotdetails-type-pathstoroottree.png "MEMUSE_SnapshotDetails_Type_PathsToRootTree")  
  
 **루트 경로** 트리에서 형식을 보면 해당 형식을 참조하는 형식의 개체 수가 **참조 개수** 열에 표시됩니다. 인스턴스를 분석할 때에는 이 열이 나타나지 않습니다.  
  
### <a name="referenced-objects-tree-snapshot-details"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_details_"></a> 참조된 개체 트리(스냅샷 정보)  
 **참조된 개체** 트리는 선택한 형식 또는 인스턴스가 참조하는 개체를 보여 줍니다.  
  
 ![인스턴스에 대한 참조되는 개체 트리](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|Name|설명|  
|-|-|  
|**개체 형식/인스턴스**|유형 이름 또는 개체 인스턴스입니다.|  
|**크기(바이트)**|유형의 경우 유형에 포함된 개체 크기를 제외한 유형의 모든 인스턴스 크기입니다.<br /><br /> 인스턴스의 경우 개체에 포함된 개체 크기를 제외한 개체 크기입니다.|  
|**포함 크기(바이트)**|포함된 개체의 크기를 비롯한 유형의 총 인스턴스 크기 또는 단일 인스턴스 크기입니다.|  
  
## <a name="snapshot-difference-diff-reports"></a><a name="BKMK_Snapshot_difference__diff__reports"></a> 스냅숏 차이 (diff) 보고서  
 스냅샷 차이(diff) 보고서는 기본 스냅샷과 기본 스냅샷 바로 직전에 만든 스냅샷 간의 변경 사항을 보여 줍니다. 차이 보고서를 열려면 다음 그림과 같이 스냅샷 뷰에서 링크 중 하나를 선택합니다. 두 링크 모두 동일한 보고서를 열지만, 보고서에서 **관리되는 힙** 트리의 시작 정렬 순서만 다릅니다. 보고서를 연 후 정렬 순서를 변경할 수 있습니다.  
  
 ![스냅숏 뷰의 차이점 보고서 링크](../profiling/media/memuse-snapshotview-snapshotdifflinks.png "MEMUSE_SnapshotView_SnapshotDiffLinks")  
  
- **MB** 링크는 **포함 크기(바이트)** 열을 기준으로 보고서를 정렬합니다.  
  
- **개체** 링크는 **개수** 열을 기준으로 보고서를 정렬 합니다.  
  
### <a name="managed-heap-tree-snapshot-diff"></a><a name="BKMK_Managed_Heap_tree__Snapshot_diff_"></a> 관리되는 힙 트리(스냅샷 차이)  
 **관리되는 힙** 트리에는 메모리에 보관된 개체의 형식이 나열됩니다. 유형에서 가장 큰 인스턴스 10개를 크기별로 정렬해서 볼 수 있도록 유형 이름을 확장할 수 있습니다. 형식 또는 인스턴스를 선택하면 선택한 항목에 대한 **루트 경로** 및 **참조 개체** 트리가 표시됩니다.  
  
 ![차이 보고서의 유형에 대한 관리되는 힙 트리](../profiling/media/memuse-snapshotdiff-type-heap.png "MEMUSE_SnapshotDiff_Type_Heap")  
  
 그림에서 **개수**, **크기(바이트)** 및 **포함 크기(바이트)** 열은 축소되어 있습니다.  
  
|Name|설명|  
|-|-|  
|**개체 형식**|유형 이름 또는 개체 인스턴스입니다.|  
|**개수**|기본 스냅샷에 있는 유형의 인스턴스 수입니다. 인스턴스의 경우 **개수**는 항상 1입니다.|  
|**개수 차이**|유형의 경우 기본 스냅샷과 이전 스냅샷 간 유형의 인스턴스 수 차이입니다. 인스턴스의 경우 이 필드는 비어 있습니다.|  
|**크기(바이트)**|개체에 포함된 개체의 크기를 제외한 기본 스냅샷의 개체 크기입니다. 형식의 경우 **크기(바이트)** 및 **포함 크기(바이트)** 는 형식 인스턴스의 총 크기입니다.|  
|**총 크기 차이(바이트)**|유형의 경우 인스턴스에 포함된 개체 크기를 제외한 기본 스냅샷과 이전 스냅샷 간 유형의 총 인스턴스 크기의 차이를 나타냅니다. 인스턴스의 경우 이 필드는 비어 있습니다.|  
|**포함 크기(바이트)**|개체에 포함된 개체의 크기를 비롯한 기본 스냅샷의 개체 크기입니다.|  
|**포함 크기 차이(바이트)**|유형의 경우 개체에 포함된 개체 크기를 비롯한 기본 스냅샷과 이전 스냅샷 간 유형의 모든 인스턴스 크기 차이를 나타냅니다. 인스턴스의 경우 이 필드는 비어 있습니다.|  
  
### <a name="paths-to-root-tree-snapshot-diff"></a><a name="BKMK_Paths_to_Root_tree__Snapshot_diff_"></a> 루트 경로 트리(스냅샷 차이)  
 **루트 경로 트리**는 형식 또는 인스턴스를 참조하는 개체의 체인을 보여 줍니다. .NET Framework 가비지 수집기는 개체에 대한 모든 참조가 해제된 경우에만 개체에 대한 메모리를 정리합니다.  
  
 ![Diff 뷰의 인스턴스에 대한 루트 트리 경로](../profiling/media/memuse-snapshotdiff-pathstoroot-instance-all.png "MEMUSE_SnapshotDiff_PathsToRoot_Instance_All")  
  
### <a name="referenced-objects-tree-snapshot-diff"></a><a name="BKMK_Referenced_Objects_tree__Snapshot_diff_"></a> 참조된 개체 트리(스냅샷 차이)  
 **참조된 개체** 트리는 기본 형식 또는 인스턴스가 참조하는 개체를 보여 줍니다.  
  
 ![인스턴스에 대한 참조되는 개체 트리](../profiling/media/memuse-snapshotdetails-referencedobjects-instance.png "MEMUSE_SnapshotDetails_ReferencedObjects_Instance")  
  
|Name|설명|  
|-|-|  
|**개체 형식/인스턴스**|유형 이름 또는 개체 인스턴스입니다.|  
|**크기(바이트)**|인스턴스의 경우 인스턴스에 포함된 개체 크기를 제외한 기본 스냅샷의 개체 크기입니다.<br /><br /> 유형의 경우 인스턴스에 포함된 개체 크기를 제외한 기본 스냅샷에 있는 유형의 총 인스턴스 크기입니다.|  
|**포함 크기(바이트)**|개체에 포함된 개체의 크기를 비롯한 기본 스냅샷의 개체 크기입니다.|  
  
## <a name="see-also"></a>관련 항목  
 [JavaScript 메모리](../profiling/javascript-memory.md)   
 [앱 성능 분석](https://msdn.microsoft.com/library/58acb30b-8428-41a6-b195-b0fdedb89575)   
 [성능 및 진단 도구 실행](https://msdn.microsoft.com/library/788279d8-f56b-40a0-9bef-facc3dfba471)   
 [C + +, c # 및 Visual Basic를 사용 하는 Windows 스토어 앱에 대 한 성능 모범 사례](https://msdn.microsoft.com/library/windows/apps/hh750313.aspx)   
 [Visual Studio의 새 메모리 사용량 도구를 사용 하 여 메모리 문제 진단](https://devblogs.microsoft.com/devops/diagnosing-memory-issues-with-the-new-memory-usage-tool-in-visual-studio/)
