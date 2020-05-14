---
title: '방법: 뷰를 문서 데이터에 첨부 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1d8bd586a9d67996389f3cb6a2b0f13f0afec3bd
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711087"
---
# <a name="how-to-attach-views-to-document-data"></a>방법: 뷰를 문서에 첨부하여 데이터를 문서화합니다.
새 문서 보기가 있는 경우 기존 문서 데이터 개체에 첨부할 수 있습니다.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>기존 문서 데이터 개체에 뷰를 첨부할 수 있는지 확인하려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>를 구현해야 합니다.

2. `IVsEditorFactory::CreateEditorInstance`구현에서 IDE가 구현을 호출할 때 기존 문서 데이터 개체를 호출합니다. `QueryInterface` `CreateEditorInstance`

    호출을 `QueryInterface` 사용하면 매개 변수에 지정된 기존 문서 `punkDocDataExisting` 데이터 개체를 검사할 수 있습니다.

    그러나 쿼리해야 하는 정확한 인터페이스는 4단계에서 설명한 대로 문서를 여는 편집기에 따라 다릅니다.

3. 기존 문서 데이터 개체에서 적절한 인터페이스를 찾지 못하면 문서 데이터 개체가 편집기와 호환되지 않음을 나타내는 오류 코드를 편집기로 반환합니다.

    IDE의 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>메시지 상자는 문서가 다른 편집기에서 열려 있음을 알리고 닫을지 묻습니다.

4. 이 문서를 닫으면 Visual Studio에서 편집기 팩터리를 두 번째로 호출합니다. 이 호출에서 `DocDataExisting` 매개 변수는 NULL과 같습니다. 그런 다음 에디터 팩터리 구현에서 문서 데이터 개체를 자신의 편집기에서 열 수 있습니다.

   > [!NOTE]
   > 기존 문서 데이터 개체로 작업할 수 있는지 여부를 확인하려면 개인 구현의 실제 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] 클래스에 포인터를 캐스팅하여 인터페이스 구현에 대한 개인 지식을 사용할 수도 있습니다. 예를 들어 모든 표준 `IVsPersistFileFormat`편집기는 에서 <xref:Microsoft.VisualStudio.OLE.Interop.IPersist>상속되는 을 구현합니다. 따라서 `QueryInterface` <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A>을 호출할 수 있으며 기존 문서 데이터 개체의 클래스 ID가 구현의 클래스 ID와 일치하는 경우 문서 데이터 개체로 작업할 수 있습니다.

## <a name="robust-programming"></a>강력한 프로그래밍
 Visual Studio에서 메서드의 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 구현을 호출하면 매개 변수의 기존 문서 `punkDocDataExisting` 데이터 개체에 대한 포인터(있는 경우)에 대한 포인터를 다시 전달합니다. 반환된 문서 데이터 `punkDocDataExisting` 개체를 검사하여 이 항목의 절차 4단계에서 설명된 대로 문서 데이터 개체가 편집기에 적합한지 확인합니다. 적절한 경우 편집기 팩터리는 [지원 여러 문서](../extensibility/supporting-multiple-document-views.md)보기에 설명된 대로 데이터에 대한 두 번째 보기를 제공해야 합니다. 그렇지 않으면 적절한 오류 메시지가 표시되어야 합니다.

## <a name="see-also"></a>참조
- [여러 문서 보기 지원](../extensibility/supporting-multiple-document-views.md)
- [사용자 지정 편집기의 문서 데이터 및 문서 보기](../extensibility/document-data-and-document-view-in-custom-editors.md)
