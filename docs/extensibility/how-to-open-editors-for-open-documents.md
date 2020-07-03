---
title: '방법: 열려 있는 문서에 대 한 편집기 열기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], opening for open documents
ms.assetid: 1a0fa49c-efa4-4dcc-bdc0-299b7052acdc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0f67a7fad5944e82087f520508ef9f4a66b7109d
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905820"
---
# <a name="how-to-open-editors-for-open-documents"></a>방법: 열려 있는 문서에 대 한 편집기 열기
프로젝트가 문서 창을 열기 전에 먼저 프로젝트에서 다른 편집기의 문서 창에 파일이 이미 열려 있는지 여부를 확인 해야 합니다. 프로젝트 관련 편집기에서 파일을 열거나에 등록 된 표준 편집기 중 하나를 사용할 수 있습니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .

## <a name="open-a-project-specific-editor"></a>프로젝트별 편집기 열기
 이미 열려 있는 파일에 대 한 프로젝트 관련 편집기를 열려면 다음 절차를 따르십시오.

### <a name="to-open-a-project-specific-editor-for-an-open-file"></a>열려 있는 파일에 대 한 프로젝트 관련 편집기를 열려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 메서드를 호출합니다.

    이 호출은 해당 하는 경우 문서의 계층, 계층 항목 및 창 프레임에 대 한 포인터를 반환 합니다.

2. 문서가 열려 있는 경우 프로젝트는 문서 데이터 개체만 있는지 또는 문서 뷰 개체가 있는지도 확인 해야 합니다.

   - 문서 뷰 개체가 있고이 뷰가 다른 계층 구조 또는 계층 항목에 대 한 것 이면 프로젝트는 뷰의 창 프레임에 대 한 포인터를 사용 하 여 기존 창을 resurface.

   - 문서 뷰 개체가 있고이 뷰가 동일한 계층 구조 및 계층 구조 항목에 대 한 경우 프로젝트는 기본 문서 데이터 개체에 연결할 수 있는 경우 두 번째 뷰를 열 수 있습니다. 그렇지 않으면 프로젝트에서 뷰의 창 프레임에 대 한 포인터를 사용 하 여 기존 창을 resurface 합니다.

   - 문서 데이터 개체만 있는 경우 프로젝트는 해당 개체의 뷰에 문서 데이터 개체를 사용할 수 있는지 여부를 확인 해야 합니다. 문서 데이터 개체가 호환 되는 경우 [프로젝트 관련 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)에 설명 된 단계를 완료 합니다.

     문서 데이터 개체가 호환 되지 않으면 해당 파일이 현재 사용 중임을 나타내는 오류를 사용자에 게 표시 해야 합니다. 이 오류는 사용자가 핵심 텍스트 편집기 이외의 편집기를 사용 하 여 파일을 열려고 할 때와 같이 파일이 동시에 컴파일되는 경우와 같이 일시적인 경우에만 표시 되어야 합니다 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . 핵심 텍스트 편집기는 컴파일러와 문서 데이터 개체를 공유할 수 있습니다.

3. 문서 데이터 개체 또는 문서 뷰 개체가 없기 때문에 문서가 열려 있지 않은 경우 [프로젝트 관련 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)의 단계를 완료 합니다.

## <a name="open-a-standard-editor"></a>표준 편집기 열기
 이미 열려 있는 파일에 대 한 표준 편집기를 열려면 다음 절차를 따르십시오.

### <a name="to-open-a-standard-editor-for-an-open-file"></a>열려 있는 파일에 대 한 표준 편집기를 열려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>을 호출합니다.

     이 메서드는 먼저를 호출 하 여 문서가 아직 열려 있지 않은지 확인 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.IsDocumentOpen%2A> 합니다. 문서가 이미 열려 있는 경우에는 해당 편집기 창이 resurfaced 됩니다.

2. 문서가 열려 있지 않으면 [방법: 표준 편집기 열기](../extensibility/how-to-open-standard-editors.md)의 단계를 완료 합니다.

## <a name="see-also"></a>참조
- [프로젝트 항목 열기 및 저장](../extensibility/internals/opening-and-saving-project-items.md)
- [방법: 프로젝트 관련 편집기 열기](../extensibility/how-to-open-project-specific-editors.md)
- [방법: 표준 편집기 열기](../extensibility/how-to-open-standard-editors.md)
