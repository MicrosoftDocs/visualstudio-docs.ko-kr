---
title: 중첩 프로젝트에 대 한 AddItem 대화 상자 필터링 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708379"
---
# <a name="filter-the-additem-dialog-box-for-nested-projects"></a>중첩 프로젝트에 대 한 AddItem 대화 상자 필터링
중첩 된 프로젝트에 대 한 **AddItem** 대화 상자를 표시 하면 부모 프로젝트가 대화 상자에 표시 되는 항목을 제어할 수 있습니다.

 인터페이스를 사용 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2> **AddItem** 대화 상자에 표시 되는 노드를 필터링 할 수 있습니다. 자식 프로젝트에 **AddItem** 대화 상자가 표시 되 면 부모는 인터페이스를 구현 하 `IVsFilterAddProjectItemDlg` 고 자식 프로젝트에 표시 되는 항목을 필터링 할 수 있습니다.

 프로젝트를 특정 부모 프로젝트에서 함수로 그룹화 할 때 `IVsFilterAddProjectItemDlg` 사용자가 중첩 된 프로젝트의 바로 가기 메뉴에서 **프로젝트 항목 추가** 를 선택 하면를 구현할 수 있습니다. `IvsFilterAddProjectItemDlg displays`프로젝트 항목 또는 해당 그룹과 관련 된 파일만 구현 합니다. 다른 그룹에 대 한 프로젝트 항목은 동일한 디렉터리에 저장 된 경우에도 대화 상자에서 필터링 됩니다.

 사용자가 자식에 대 한 **AddItem** 대화 상자를 열면 부모 프로젝트의 `IVsFilterAddProjectItemDlg` 인터페이스 구현이 호출 됩니다.

 `IVsFilterAddProjectItemDlg`인터페이스는 범주별 필터링을 구현할 수도 있습니다. 자세한 내용은 [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md) 및 [프로젝트 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)을 참조 하세요.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsFilterAddProjectItemDlg2>
- [새 항목 추가 대화 상자에 항목 추가](../../extensibility/internals/adding-items-to-the-add-new-item-dialog-boxes.md)
- [프로젝트 템플릿 및 항목 템플릿 등록](../../extensibility/internals/registering-project-and-item-templates.md)
- [프로젝트 중첩](../../extensibility/internals/nesting-projects.md)
