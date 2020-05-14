---
title: 기타 파일 프로젝트 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- files, adding existing files to solutions
- Miscellaneous Files project
- Solution Items folder
- files, opening with Miscellaneous Files project
ms.assetid: 93a278a8-d4f4-400b-8945-4f1b0a2b5bac
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 95cc1312fb7b381e1e20df834698480295fadcc8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707094"
---
# <a name="miscellaneous-files-project"></a>기타 파일 프로젝트
사용자가 프로젝트 항목을 열면 IDE는 솔루션의 프로젝트 구성원이 아닌 항목을 기타 파일에 할당합니다.

 프로젝트는 사용자가 프로젝트 항목을 열 때 사용되는 편집기를 결정하는 데 중요한 역할을 합니다. 프로젝트는 프로젝트별 편집기 또는 표준 편집기를 사용하여 특정 파일을 열도록 설계할 수 있습니다.

 프로젝트별 편집기는 일반적으로 사용자에게 특별한 지식을 갖거나 프로젝트의 특수 인터페이스를 사용해야 합니다. 자세한 내용은 [프로젝트별 편집기 열기 방법: 을](../../extensibility/how-to-open-project-specific-editors.md)참조하십시오.

 표준 편집기는 모든 프로젝트에서 특정 확장자의 파일을 열 수 있습니다. 사용자는 프로젝트에 대해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 텍스트 편집기와 같은 일부 표준 편집기에서 사용자 지정할 수 있지만 공개 문자를 계속 유지할 수 있습니다. 표준 편집기는 메서드를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 사용하여 만들어집니다.

 솔루션의 프로젝트가 프로젝트 항목을 열 수 있다고 응답하지 않으면 IDE는 파일을 여는 기타 파일 프로젝트라는 특수 프로젝트를 제공합니다.

 이 특수 프로젝트는 프로젝트의 컨텍스트 외부에서 파일을 여는 데 적합합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenDocumentViaProject%2A> 메서드를 처리하는 동안 기타 파일 프로젝트는 항상 매우 낮은 우선 순위로 응답합니다. 따라서 기타 파일 프로젝트는 항상 파일을 열 수 있는 우선 순위가 높은 프로젝트에 대한 결과를 얻을 수 있습니다.

 기타 파일 프로젝트는 사용자가 **새 프로젝트** 대화 상자를 사용하여 명시적으로 만들 필요가 없습니다. 또한 기타 파일 프로젝트는 프로젝트 멤버 목록을 영구적으로 관리하지 않습니다. 선택적 기능을 사용하여 각 사용자에 대해 가장 최근에 사용한 파일 목록을 기록합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument>
- <xref:Microsoft.VisualStudio.Shell.Interop.VSDOCUMENTPRIORITY>
- [방법: 프로젝트별 편집기 열기](../../extensibility/how-to-open-project-specific-editors.md)
- [방법: 표준 편집기 열기](../../extensibility/how-to-open-standard-editors.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
- [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
