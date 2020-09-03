---
title: 프로젝트 형식을 만들어야 하는 경우 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703425"
---
# <a name="when-to-create-project-types"></a>프로젝트 형식을 만들어야 하는 경우
새 프로젝트 형식을 만들면 사용자를 사용자 지정 하기 위한 기초를 제공 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 합니다. 그러나 모든 사용자 지정에는 새 프로젝트 형식을 만들 필요가 없습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 다음 지침은 시나리오에 새 프로젝트 형식이 필요한 지 여부를 확인 하는 데 도움이 됩니다.

## <a name="create-a-new-project-type"></a>새 프로젝트 형식 만들기
 다음 방법 중 하나 이상을 수행 하도록 사용자 지정 하려는 경우 프로젝트 형식을 만들어야 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- 빌드, 배포, 구성 및 소스 제어에 참여 합니다.

- 디버깅 지원을 제공 합니다.

- **솔루션 탐색기**에 프로젝트 항목을 표시 합니다.

- **프로젝트 열기** 또는 **새 프로젝트** 대화 상자를 사용 합니다.

- 프로젝트 중첩을 지원 합니다.

## <a name="extend-an-existing-project-type"></a>기존 프로젝트 형식 확장
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]기존 프로젝트 형식의 동작을 수정 하거나 확장 하기 위해 다음과 같은 방법으로 사용할 수 있는 새 프로젝트 형식을 만들 수 있습니다. 예를 들어, 프로젝트의 빌드 프로세스를 수정 합니다 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] .

- 여러 파일을 단일 단위로 사용 합니다.

- 단일 파일을 하위 항목의 계층 구조로 표시 합니다.

- 편집기 주위에 명령 컨텍스트를 표시 합니다.

- 편집기에 대 한 서비스 컨텍스트를 표시 합니다.

## <a name="use-an-existing-project-type"></a>기존 프로젝트 형식 사용
 경우에 따라 새 프로젝트를 만들 필요가 없습니다. 다음 표에서는에 대 한 프로젝트 형식을 만들 필요가 없는 태스크를 보여 줍니다.

|Task|설명|
|----------|-----------------|
|명령 처리|모든 VSPackage은 명령을 처리할 수 있습니다.|
|편집기 빌드|사용자 지정 편집기를 등록할 수 있습니다. 자세한 내용은 [Windows 및 편집기 문서](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)를 참조 하세요.|
|소유 창|새 프로젝트 형식을 추가 하지 않고 도구와 문서 창을 모두 만들 수 있습니다.|
|속성 창 속성 노출|모든 개체는 속성을 노출할 수 있습니다.|

## <a name="create-a-project-subtype"></a>프로젝트 하위 형식 만들기
 프로젝트 하위 형식을 사용 하 여 새 프로젝트 형식을 만들지 않고도 관리 되는 프로젝트 형식을 확장할 수 있습니다. 프로젝트 하위 유형은 COM 집계를 사용 하 여 Microsoft 또는에서 작성 된 관리 되는 프로젝트를 확장 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] 합니다. COM 집계를 사용 하면 대부분의 관리 되는 프로젝트 시스템 구현을 다시 사용 하 고 집계 및 지원 인터페이스를 사용 하 여 특정 시나리오에 대 한 사용자 지정을 계속할 수 있습니다. 프로젝트 하위 형식에 대 한 자세한 내용은 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [문서 창 및 편집기](https://msdn.microsoft.com/library/603625e1-62b6-413a-bc44-089346e166bc)
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [Visual Studio의 계층 구조](../../extensibility/internals/hierarchies-in-visual-studio.md)
