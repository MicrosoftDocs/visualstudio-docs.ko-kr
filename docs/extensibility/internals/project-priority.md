---
title: 프로젝트 우선 순위 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80706415"
---
# <a name="project-priority"></a>프로젝트 우선 순위
프로젝트 항목은 일반적으로 솔루션에 있는 하나의 프로젝트의 멤버입니다. 따라서 IDE는 항목을 여는 데 사용 되는 프로젝트를 쉽게 확인할 수 있습니다. 그러나 항목이 둘 이상의 프로젝트의 멤버인 경우 IDE는 우선 순위 체계를 사용 하 여 항목을 여는 데 가장 적합 한 프로젝트를 결정 합니다.

 다음 목록에서는 프로젝트 우선 순위 스키마를 보여 줍니다.

- IDE는 솔루션의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject2.IsDocumentInProject%2A> 각 프로젝트에 대해 메서드를 호출 하 여 문서가 해당 프로젝트의 멤버 인지 여부를 확인 합니다.

- 문서가 프로젝트의 멤버인 경우 프로젝트는 해당 문서 처리에 따라 프로젝트가 할당 하는 우선 순위를 사용 하 여 응답 합니다. 예를 들어 언어 프로젝트는 언어 소스 파일에 대해 높은 우선 순위로 응답 하지만 해당 빌드 프로세스의 일부로 사용 되지 않는 인식 되지 않는 파일 형식에 대해 낮은 우선 순위로 응답 합니다.

- 문서에 대 한 사용자 지정, 프로젝트 관련 편집기 또는 디자이너를 제공 하는 프로젝트도 높은 우선 순위를 받습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>열거형은 문서 우선 순위 값을 제공 합니다.

- 가장 높은 우선 순위를 지정 하는 프로젝트는 문서를 여는 컨텍스트를 제공 합니다. 두 프로젝트가 동일한 우선 순위 값을 반환 하는 경우 활성 프로젝트를 선호 합니다. 솔루션에 문서를 열 수 있는 것으로 응답 하는 프로젝트가 없으면 IDE는 기타 파일 프로젝트에 문서를 넣습니다. 자세한 내용은 [기타 파일 프로젝트](../../extensibility/internals/miscellaneous-files-project.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [기타 파일 프로젝트](../../extensibility/internals/miscellaneous-files-project.md)
- [방법: 열린 문서에 대한 편집기 열기](../../extensibility/how-to-open-editors-for-open-documents.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
