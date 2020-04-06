---
title: 프로젝트 유형을 작성하는 경우 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project types, conditions for creating
ms.assetid: 26adc860-ee4a-4f5c-95e1-e41b207dd7e6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 861250dac25288f353cbd5c57f510bf67dadce70
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703425"
---
# <a name="when-to-create-project-types"></a>프로젝트 형식을 만들어야 하는 경우
새 프로젝트 형식을 만들면 사용자에 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 대한 사용자 지정의 기반이 됩니다. 그러나 모든 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 사용자 지정에 새 프로젝트 형식을 만드는 데 필요한 것은 아닙니다. 다음 지침은 시나리오에 새 프로젝트 유형이 필요한지 여부를 결정하는 데 도움이 됩니다.

## <a name="create-a-new-project-type"></a>새 프로젝트 유형 만들기
 다음 방법 중 하나 이상에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 작동하도록 사용자 지정하려면 프로젝트 유형을 만들어야 합니다.

- 빌드, 배포, 구성 및 소스 제어에 참여합니다.

- 디버깅 지원을 제공합니다.

- **솔루션 탐색기에서**프로젝트 항목을 표시합니다.

- 프로젝트 **열기** 또는 **새 프로젝트** 대화 상자를 사용합니다.

- 프로젝트 중첩을 지원합니다.

## <a name="extend-an-existing-project-type"></a>기존 프로젝트 유형 확장
 다음과 같은 방법으로 기존 프로젝트 유형의 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 동작을 수정하거나 확장하는 데 사용할 수 있는 새 프로젝트 형식을 만들 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 수 있습니다(예: 프로젝트의 빌드 프로세스 수정)

- 여러 파일을 단일 단위로 작업합니다.

- 단일 파일을 하위 항목의 계층구조로 표시합니다.

- 편집기 주위에 명령 컨텍스트를 표시합니다.

- 편집자에 대한 서비스 컨텍스트를 표시합니다.

## <a name="use-an-existing-project-type"></a>기존 프로젝트 유형 사용
 새 프로젝트를 만들 필요가 없는 경우가 있습니다. 다음 표에서는 프로젝트 형식을 만들 필요가 없는 작업을 보여 주며 있습니다.

|Task|설명|
|----------|-----------------|
|명령 처리|모든 VSPackage는 명령을 처리할 수 있습니다.|
|편집기 작성|사용자 지정 편집기는 등록할 수 있습니다. 자세한 내용은 [문서 Windows 및 편집기](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)를 참조하십시오.|
|창 소유|새 프로젝트 유형을 추가하지 않고 도구 및 문서 창을 모두 만들 수 있습니다.|
|속성 창에서 속성 노출|모든 개체는 속성을 노출할 수 있습니다.|

## <a name="create-a-project-subtype"></a>프로젝트 하위 유형 만들기
 프로젝트 하위 유형을 사용하여 새 프로젝트 형식을 만들지 않고도 관리되는 프로젝트 유형을 확장할 수 있습니다. 프로젝트 하위 유형은 COM 집계를 사용하여 Microsoft [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]또는 에서 작성된 관리되는 프로젝트를 확장합니다. COM 집계를 사용하면 관리되는 프로젝트 시스템 구현의 대부분을 다시 사용하고 집계 및 지원 인터페이스 사용을 통해 특정 시나리오에 맞게 사용자 지정할 수 있습니다. 프로젝트 하위 유형에 대한 자세한 내용은 [프로젝트 하위 유형을](../../extensibility/internals/project-subtypes.md)참조하십시오.

## <a name="see-also"></a>참조
- [문서 윈도우 및 편집자](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)
