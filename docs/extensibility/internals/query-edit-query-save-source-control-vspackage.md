---
title: 쿼리 편집 쿼리 저장 (소스 제어 VSPackage) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- QEQS events
- Query Edit Query Save events
- source control packages, Query Edit Query Save events
ms.assetid: c360d2ad-fe42-4d65-899d-d1588cc8a322
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c09ac0cb4f51b8f2484b95d403ff6d0445631479
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705965"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>쿼리 편집, 쿼리 저장(소스 제어 VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 편집기는 쿼리 편집 쿼리 저장 (QEQS) 이벤트를 브로드캐스트할 수 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 원본 제어 스텁은 QEQS 서비스를 구현 하므로 QEQS 이벤트를 받는 사람입니다. 그런 다음 이러한 이벤트는 현재 활성 소스 제어 VSPackage 위임 됩니다. 활성 소스 제어 VSPackage는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 및 해당 메서드를 구현 합니다. 인터페이스의 메서드는 `IVsQueryEditQuerySave2` 일반적으로 문서를 처음 편집 하 고 문서를 저장 하기 직전에 호출 됩니다.

## <a name="queryeditquerysave-events"></a>QueryEditQuerySave 이벤트
 소스 제어 VSPackage는 `IVsQueryEditQuerySave2` 인터페이스 및 필요한 메서드를 구현 하 여 QEQS 이벤트를 처리 해야 합니다. 다음은 VSPackage가 최소한으로 구현 해야 하는 두 가지 방법에 대 한 간단한 설명입니다. 실제 구현은 원본 제어 모델의 논리에 따라 구현 되어야 합니다.

### <a name="queryeditfiles-method"></a>QueryEditFiles 메서드
 는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 프로젝트 또는 편집기에서 파일을 수정 하려고 할 때 호출 됩니다. 이 메서드는 파일이 수정 되 고 파일이 저장 될 때 *까지* 호출 하는 것이 가장 좋습니다. 이 메서드는 호출 되 면 `IVsQueryEditQuerySave2::QueryEditFiles` 지정 된 파일이 소스 제어에 있는지 여부, 체크 아웃 해야 하는지 여부 및 다시 로드할 수 있는지 여부를 확인 합니다. 환경에서 파일을 편집할 수 없는 경우 메서드는 `IVsQueryEditQuerySave2::QueryEditFiles` 호출 프로그램에 편집을 취소 하도록 지시 합니다. 호출자가 호출 모드를 지정 하는 것도 가능 합니다. "자동" 모드에서이 메서드는 UI가 표시 되지 않는 경우에만 작업을 수행 합니다. UI가 피할 수 없는 경우 문제를 나타내기 위해 플래그를 반환 해야 합니다.

 메서드는 트랜잭션 방식으로 동작 합니다. 즉, 단일 파일에 대해 편집이 취소 되 면 모든 파일에 대해 편집이 취소 됩니다. 반대로, 편집이 허용 되는 경우 모든 파일에 대해 허용 됩니다. 이 메서드가 지정 된 파일 집합에 대해 한 번 편집을 허용 하는 경우에는 동일한 파일 집합에 대 한 후속 호출에서 편집을 항상 허용 해야 합니다. 허용 편집 루프는 파일이 닫히고 저장 되 고 다시 로드 될 때까지 계속 됩니다. 특성 (속성)이 변경 될 때까지 또는 원본 제어 패키지가 변경 될 때까지. 메서드를 구현할 때 고려해 야 할 사례에는 `IVsQueryEditQuerySave2::QueryEditFiles` 여러 파일, 특수 파일, 사용자의 취소 및 메모리 내 편집이 포함 됩니다.

### <a name="querysavefiles-method"></a>QuerySaveFiles 메서드
 는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 프로젝트 또는 편집기에서 파일 집합을 저장 해야 할 때 호출 됩니다. 메서드는 호출 되 면 `IVsQueryEditQuerySave2::QuerySaveFiles` 지정 된 파일이 읽기 전용인 지, 소스 제어에서 사용할 수 있는지를 확인 합니다. 파일을 체크 아웃 해야 하는 경우 호출은 소스 제어 패키지에 위임 됩니다. 파일이 저장 되지 않는 상황이 발생 하면 `IVsQueryEditQuerySave2::QuerySaveFiles` 메서드에서 저장을 취소 하도록 편집기에 지시 해야 합니다. `IVsQueryEditQuerySave2::QueryEditFiles`메서드와 마찬가지로 호출자가 호출 모드를 지정할 수 있습니다. "자동" 모드에서이 메서드는 UI가 표시 되지 않는 경우에만 작업을 수행 합니다. UI가 피할 수 없는 경우 문제를 나타내기 위해 플래그를 반환 해야 합니다.

 이 메서드는 트랜잭션 방식으로 동작 해야 합니다. 즉, 단일 파일에서 저장이 취소 되 면 모든 파일에 대해 저장이 취소 됩니다. 반대로, 저장이 허용 되는 경우 모든 파일에 대해 허용 되어야 합니다. `IVsQueryEditQuerySave2::QueryEditFiles`메서드와 마찬가지로 메서드를 구현할 때 고려해 야 하는 사례에는 `IVsQueryEditQuerySave2::QuerySaveFiles` 여러 파일, 특수 파일, 사용자의 취소 및 메모리 내 편집이 포함 됩니다.

## <a name="see-also"></a>참고 항목
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
