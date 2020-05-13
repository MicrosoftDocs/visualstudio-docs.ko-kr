---
title: '방법: 열린 문서에 대한 오픈 에디터 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d0986573ac0d53427f6490370be2bfa1c4cbe7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710923"
---
# <a name="how-to-open-editors-for-open-documents"></a>방법: 열린 문서에 대한 편집기 열기
프로젝트가 문서 창을 열기 전에 프로젝트는 먼저 다른 편집기의 문서 창에서 파일이 이미 열려 있는지 확인해야 합니다. 파일은 프로젝트별 편집기에서 열거나 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에 등록된 표준 편집기 중 하나일 수 있습니다.

## <a name="open-a-project-specific-editor"></a>프로젝트별 편집기 열기
 다음 절차를 사용하여 이미 열려 있는 파일에 대한 프로젝트 별 편집기를 엽니다.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>열려 있는 파일에 대한 프로젝트 별 편집기를 열려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 메서드를 호출합니다.

    이 호출은 적절한 경우 문서의 계층 구조, 계층 항목 및 창 프레임에 대한 포인터를 반환합니다.

2. 문서가 열려 있는 경우 프로젝트는 문서 데이터 개체만 있는지 또는 문서 뷰 개체도 있는지 확인해야 합니다.

   - 문서 뷰 개체가 있고 이 뷰가 다른 계층 또는 계층 항목에 대한 경우 프로젝트는 뷰의 창 프레임에 대한 포인터를 사용하여 기존 창을 다시 표시합니다.

   - 문서 뷰 개체가 있고 이 뷰가 동일한 계층 및 계층 항목에 대한 경우 프로젝트는 기본 문서 데이터 개체에 연결할 수 있는 경우 두 번째 뷰를 열 수 있습니다. 그렇지 않으면 프로젝트에서 뷰의 창 프레임에 대한 포인터를 사용하여 기존 창을 다시 표시해야 합니다.

   - 문서 데이터 개체만 있는 경우 프로젝트는 해당 뷰에 문서 데이터 개체를 사용할 수 있는지 여부를 결정해야 합니다. 문서 데이터 개체가 호환되는 경우 [프로젝트별 편집기 열기에서](../extensibility/how-to-open-project-specific-editors.md)설명하는 단계를 완료합니다.

     문서 데이터 개체가 호환되지 않는 경우 파일이 현재 사용 중임을 나타내는 오류가 사용자에게 표시되어야 합니다. 이 오류는 사용자가 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 핵심 텍스트 편집기 이외의 편집기를 사용하여 파일을 열려고 하는 동시에 파일을 컴파일하는 경우와 같은 일시적인 경우에만 표시되어야 합니다. 핵심 텍스트 편집기는 문서 데이터 개체를 컴파일러와 공유할 수 있습니다.

3. 문서 데이터 개체 또는 문서 뷰 개체가 없기 때문에 문서가 열려 있지 않으면 [프로젝트별 편집기 열기에서](../extensibility/how-to-open-project-specific-editors.md)단계를 완료합니다.

## <a name="open-a-standard-editor"></a>표준 편집기 열기
 다음 절차를 사용하여 이미 열려 있는 파일에 대한 표준 편집기를 엽니다.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>열려 있는 파일에 대한 표준 편집기를 열려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>을 호출합니다.

     이 메서드는 먼저 를 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A>문서가 아직 열려 있지 않은지 확인합니다. 문서가 이미 열려 있으면 편집기 창이 다시 표시됩니다.

2. 문서가 열려 있지 않으면 표준 편집기 열기 방법: 의 단계를 [완료합니다.](../extensibility/how-to-open-standard-editors.md)

## <a name="see-also"></a>참조
- [프로젝트 항목 열기 및 저장](../extensibility/internals/opening-and-saving-project-items.md)
- [방법: 프로젝트별 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)
- [방법: 표준 편집기 열기](../extensibility/how-to-open-standard-editors.md)
