---
title: 쿼리 편집 쿼리 저장(소스 제어 VSPackage) | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705965"
---
# <a name="query-edit-query-save-source-control-vspackage"></a>쿼리 편집, 쿼리 저장(소스 제어 VSPackage)
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]편집자는 QEQS(쿼리 편집 쿼리 저장) 이벤트를 브로드캐스트할 수 있습니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]소스 제어 스텁은 QEQS 이벤트를 수신자가 되도록 QEQS 서비스를 구현합니다. 그런 다음 이러한 이벤트는 현재 활성 소스 제어 VSPackage에 위임됩니다. 활성 소스 제어 VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2> 및 해당 메서드를 구현 합니다. `IVsQueryEditQuerySave2` 인터페이스 의 메서드는 일반적으로 문서를 처음 편집하기 직전과 문서가 저장되기 직전에 호출됩니다.

## <a name="queryeditquerysave-events"></a>쿼리 편집쿼리 저장 이벤트
 소스 제어 VSPackage는 `IVsQueryEditQuerySave2` 인터페이스와 필요한 메서드를 구현하여 QEQS 이벤트를 처리해야 합니다. 다음은 VSPackage가 최소한 구현해야 하는 두 가지 방법에 대한 간략한 설명입니다. 실제 구현은 소스 제어 모델의 논리에 따라야 합니다.

### <a name="queryeditfiles-method"></a>쿼리 편집 파일 방법
 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QueryEditFiles%2A> 또는 편집기에서 파일을 수정하려고 할 때 호출됩니다. 이상적으로이 메서드는 파일을 수정 하기 *전에* 그리고 파일을 저장할 때 호출 됩니다. 호출할 때 `IVsQueryEditQuerySave2::QueryEditFiles` 메서드는 지정된 파일이 소스 제어하에 있는지 여부, 체크 아웃해야 하는지 여부 및 다시 로드할 수 있는지 여부를 확인합니다. 상황으로 인해 파일을 편집할 수 `IVsQueryEditQuerySave2::QueryEditFiles` 없는 경우 메서드는 호출 프로그램에 편집을 취소하도록 지시합니다. 호출자도 호출 모드를 지정할 수 있습니다. "자동" 모드에서이 메서드는 UI가 나타나지 않는 경우에만 작업을 수행합니다. UI가 불가피한 경우 문제를 나타내기 위해 플래그를 반환해야 합니다.

 메서드는 트랜잭션 방식으로 실행됩니다. 즉, 단일 파일에서 편집이 취소되면 모든 파일에 대해 편집이 취소됩니다. 반대로 편집이 허용되면 모든 파일에 대해 허용됩니다. 이 방법을 사용하면 지정된 파일 집합에 대해 한 번 편집할 수 있는 경우 항상 동일한 파일 집합에 대한 후속 호출을 편집할 수 있어야 합니다. 허용 편집 루프는 파일이 닫히고 저장되고 다시 로드될 때까지 계속됩니다. 속성(속성)이 변경될 때까지; 또는 소스 제어 패키지가 변경될 때까지. `IVsQueryEditQuerySave2::QueryEditFiles` 메서드를 구현할 때 고려해야 할 경우는 여러 파일, 특수 파일, 사용자 취소 및 메모리 내 편집을 포함합니다.

### <a name="querysavefiles-method"></a>쿼리 저장 파일 방법
 프로젝트 <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2.QuerySaveFiles%2A> 또는 편집기파일 집합을 저장해야 할 때 호출됩니다. 호출할 때 `IVsQueryEditQuerySave2::QuerySaveFiles` 메서드는 지정된 파일이 읽기 전용인지 여부와 소스 제어하에 있는지 여부를 확인합니다. 파일을 체크 아웃해야 하는 경우 호출이 소스 제어 패키지에 위임됩니다. 상황이 파일을 저장하지 못하는 경우 `IVsQueryEditQuerySave2::QuerySaveFiles` 메서드는 편집기에게 저장을 취소하도록 알려야 합니다. 메서드와 `IVsQueryEditQuerySave2::QueryEditFiles` 마찬가지로 호출 모드를 호출 모드를 지정할 수 있습니다. "자동" 모드에서이 메서드는 UI가 나타나지 않는 경우에만 작업을 수행합니다. UI가 불가피한 경우 문제를 나타내기 위해 플래그를 반환해야 합니다.

 이 메서드는 트랜잭션 방식으로 실행되어야 합니다. 즉, 단일 파일에서 저장이 취소되면 모든 파일에 대해 저장이 취소됩니다. 반대로 저장이 허용되는 경우 모든 파일에 대해 저장이 허용되어야 합니다. 메서드와 `IVsQueryEditQuerySave2::QueryEditFiles` 마찬가지로 `IVsQueryEditQuerySave2::QuerySaveFiles` 메서드를 구현할 때 고려해야 할 경우는 여러 파일, 특수 파일, 사용자 취소 및 메모리 내 편집을 포함합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsQueryEditQuerySave2>
