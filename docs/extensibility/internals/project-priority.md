---
title: 프로젝트 우선 순위 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: 9f707592-2fb6-4f75-9269-f6d4700a998e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a75c1c333d88e1bf5524281bee8b2a683ca6c98e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706415"
---
# <a name="project-priority"></a>프로젝트 우선 순위
프로젝트 항목은 일반적으로 솔루션에서 하나의 프로젝트의 멤버입니다. 따라서 IDE는 항목을 여는 데 사용되는 프로젝트를 쉽게 결정할 수 있습니다. 그러나 항목이 두 개 이상의 프로젝트의 구성원인 경우 IDE는 우선 순위 체계를 사용하여 항목을 여는 데 가장 적합한 프로젝트를 결정합니다.

 다음 목록은 프로젝트 우선 순위 체계를 보여 주며 있습니다.

- IDE는 솔루션의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> 각 프로젝트에 대한 메서드를 호출하여 문서가 해당 프로젝트의 멤버인지 여부를 확인합니다.

- 문서가 프로젝트의 구성원인 경우 프로젝트는 해당 문서의 처리에 따라 프로젝트가 할당하는 우선 순위로 응답합니다. 예를 들어 언어 프로젝트는 언어 원본 파일에 대해 우선 순위가 높은 것으로 응답하지만 빌드 프로세스의 일부로 사용되지 않는 인식되지 않는 파일 형식에 대해 낮은 우선 순위로 응답합니다.

- 문서에 대한 사용자 지정 프로젝트별 편집자 또는 디자이너를 제공하는 프로젝트도 높은 우선 순위를 받습니다.

- 열거형은 <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY> 문서 우선 순위 값을 제공합니다.

- 가장 높은 우선 순위를 지정하는 프로젝트에는 문서를 열 수 있는 컨텍스트가 지정됩니다. 두 프로젝트가 동일한 우선 순위 값을 반환하는 경우 활성 프로젝트가 선호됩니다. 솔루션의 프로젝트가 문서를 열 수 있다고 응답하지 않으면 IDE는 문서를 기타 파일 프로젝트에 넣습니다. 자세한 내용은 [기타 파일 프로젝트를](../../extensibility/internals/miscellaneous-files-project.md)참조하십시오.

## <a name="see-also"></a>참조
- [기타 파일 프로젝트](../../extensibility/internals/miscellaneous-files-project.md)
- [방법: 열린 문서에 대한 편집기 열기](../../extensibility/how-to-open-editors-for-open-documents.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
