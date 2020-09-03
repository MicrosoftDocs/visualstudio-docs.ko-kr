---
title: '방법: 문서 데이터에 보기 연결 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - attach views to document data
ms.assetid: f92c0838-45be-42b8-9c55-713e9bb8df07
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d5437e3a5d4fb0d6d33d570eb4d8923245cb287b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905899"
---
# <a name="how-to-attach-views-to-document-data"></a>방법: 문서 데이터에 보기 연결
새 문서 보기가 있는 경우 기존 문서 데이터 개체에 연결할 수 있습니다.

## <a name="to-determine-if-you-can-attach-a-view-to-an-existing-document-data-object"></a>뷰를 기존 문서 데이터 개체에 연결할 수 있는지 확인 하려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A>를 구현해야 합니다.

2. 구현에서 `IVsEditorFactory::CreateEditorInstance` `QueryInterface` IDE가 구현을 호출할 때 기존 문서 데이터 개체에 대해를 호출 합니다 `CreateEditorInstance` .

    를 호출 하면 `QueryInterface` 매개 변수에 지정 된 기존 문서 데이터 개체를 검사할 수 있습니다 `punkDocDataExisting` .

    그러나 반드시 쿼리해야 하는 정확한 인터페이스는 4 단계에 설명 된 대로 문서를 여는 편집기에 따라 달라 집니다.

3. 기존 문서 데이터 개체에서 적절 한 인터페이스를 찾지 못하는 경우 문서 데이터 개체가 편집기와 호환 되지 않음을 나타내는 오류 코드를 편집기에 반환 합니다.

    의 IDE 구현에서 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A> 메시지 상자는 문서가 다른 편집기에서 열려 있음을 알리고 사용자에 게 닫을지 묻는 메시지를 표시 합니다.

4. 이 문서를 닫으면 Visual Studio에서 편집기 팩터리를 두 번 호출 합니다. 이 호출에서 `DocDataExisting` 매개 변수는 NULL입니다. 그러면 편집기 팩터리 구현이 사용자의 편집기에서 문서 데이터 개체를 열 수 있습니다.

   > [!NOTE]
   > 기존 문서 데이터 개체를 사용 하 여 작업할 수 있는지 여부를 확인 하기 위해 개인 구현에 대 한 실제 클래스로 포인터를 캐스팅 하 여 인터페이스 구현에 대 한 개인 정보를 사용할 수도 있습니다 [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] . 예를 들어 모든 표준 편집기는 `IVsPersistFileFormat` 에서 상속 되는를 구현 <xref:Microsoft.VisualStudio.OLE.Interop.IPersist> 합니다. 따라서에 대해를 호출할 `QueryInterface` 수 <xref:Microsoft.VisualStudio.OLE.Interop.IPersist.GetClassID%2A> 있으며, 기존 문서 데이터 개체의 클래스 id가 구현의 클래스 id와 일치 하는 경우 문서 데이터 개체를 사용할 수 있습니다.

## <a name="robust-programming"></a>강력한 프로그래밍
 Visual Studio는 메서드의 구현을 호출할 때 <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> 매개 변수에서 기존 문서 데이터 개체에 대 한 포인터를 다시 전달 `punkDocDataExisting` 합니다 (있는 경우). 에서 반환 된 문서 데이터 개체를 검토 `punkDocDataExisting` 하 여이 항목에 설명 된 절차의 4 단계에 설명 된 대로 문서 데이터 개체가 편집기에 적합 한지 확인 합니다. 적절 한 경우 편집기 팩터리는 [다중 문서 뷰 지원](../extensibility/supporting-multiple-document-views.md)에 설명 된 대로 데이터에 대 한 두 번째 뷰를 제공 해야 합니다. 그렇지 않으면 적절 한 오류 메시지를 표시 해야 합니다.

## <a name="see-also"></a>추가 정보
- [다중 문서 뷰 지원](../extensibility/supporting-multiple-document-views.md)
- [사용자 지정 편집기의 문서 데이터 및 문서 보기](../extensibility/document-data-and-document-view-in-custom-editors.md)
