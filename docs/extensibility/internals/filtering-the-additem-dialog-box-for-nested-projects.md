---
title: 중첩 된 프로젝트에 대 한 추가 항목 대화 상자 필터링 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- filtering, nested projects
- nested projects, AddItem dialog box filtering
ms.assetid: 5b3e352e-7f18-4f66-be16-b0ad55637ce5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2bc97b6041f4844ff71fe1d38a7103e1219888be
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708379"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>중첩된 프로젝트에 대한 AddItem 대화 상자 필터링
중첩된 프로젝트에 대한 **AddItem** 대화 상자를 표시하면 상위 프로젝트에서 대화 상자에 표시되는 항목을 제어할 수 있습니다.

 인터페이스를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> 사용하면 **AddItem** 대화 상자에 있을 노드를 필터링할 수 있습니다. 자식 프로젝트에 **AddItem** 대화 상자가 표시되면 부모는 `IVsFilterAddProjectItemDlg` 자식 프로젝트에 표시될 인터페이스및 필터 항목을 구현할 수 있습니다.

 프로젝트가 특정 상위 프로젝트에서 함수별로 그룹화되면 `IVsFilterAddProjectItemDlg` 사용자가 중첩된 프로젝트의 바로 가기 메뉴에서 **프로젝트 항목 추가를** 선택할 때 구현할 수 있습니다. 해당 `IvsFilterAddProjectItemDlg displays` 그룹에 특정한 프로젝트 항목 또는 파일만 구현합니다. 다른 그룹에 대한 프로젝트 항목은 동일한 디렉터리에 저장된 경우에도 대화 상자에서 필터링됩니다.

 사용자가 자식에 대한 **AddItem** 대화 상자를 열면 상위 프로젝트의 `IVsFilterAddProjectItemDlg` 인터페이스 구현이 호출됩니다.

 인터페이스는 `IVsFilterAddProjectItemDlg` 범주별 필터링을 구현할 수도 있습니다. 자세한 내용은 [새 항목 추가 대화 상자에 항목 추가 상자](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) 및 프로젝트 및 항목 템플릿 [등록을](../../extensibility/internals/registering-project-and-item-templates.md)참조하십시오.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [네스트 프로젝트](../../extensibility/internals/nesting-projects.md)
