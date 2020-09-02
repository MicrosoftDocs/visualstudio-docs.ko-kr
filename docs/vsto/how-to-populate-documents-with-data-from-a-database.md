---
title: '방법: 데이터베이스의 데이터로 문서 채우기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8470ec4acf686c016088c5f474539a1ab7ed85df
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547201"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>방법: 데이터베이스의 데이터로 문서 채우기

Windows Forms 프로젝트의 데이터에 액세스하는 것과 동일한 방식으로 Microsoft Office에 대한 문서 수준 프로젝트의 데이터에 액세스할 수 있습니다. 동일한 도구 및 코드를 사용하여 데이터베이스의 데이터를 솔루션으로 가져오며, Windows Forms 컨트롤을 사용하여 데이터를 표시할 수 있습니다.

또한 호스트 컨트롤을 사용하여 데이터를 표시할 수 있습니다. 호스트 컨트롤은 이벤트 및 데이터 바인딩 기능을 통해 향상된 Microsoft Office Word의 네이티브 개체입니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

다음 예제에서는 디자이너를 사용하여 문서 수준 프로젝트에 데이터 바인딩된 컨트롤을 추가하는 방법을 보여 줍니다. 런타임에 VSTO 추가 기능 프로젝트에서 데이터 바인딩된 컨트롤을 추가 하는 방법에 대 한 예제는 [연습: Vsto 추가 기능 프로젝트의 단순 데이터 바인딩](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)을 참조 하세요.

![비디오에 연결](../vsto/media/playvideo.gif "비디오에 링크") 관련 동영상 데모를 보려면 [Office 시스템에 대 한 Visual Studio Tools를 사용 하 여 Word 2007 콘텐츠 컨트롤에 데이터 바인딩 (3.0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12))을 참조 하세요.

## <a name="add-a-control-to-a-document-at-design-time"></a>디자인 타임에 문서에 컨트롤 추가

### <a name="to-populate-a-document-with-data-from-a-database"></a>데이터베이스의 데이터로 문서를 채우려면

1. 디자이너에서 문서를 열고 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 Word 문서 수준 프로젝트를 엽니다.

2. **데이터** 원본 창을 열고 데이터베이스에서 데이터 원본을 만듭니다. 자세한 내용은 [새 연결 추가](../data-tools/add-new-connections.md)를 참조 하세요.

3. 원하는 필드를 **데이터 소스** 창에서 문서로 끌어 옵니다.

콘텐츠 컨트롤이 문서에 추가됩니다. 콘텐츠 컨트롤의 형식은 선택한 필드의 데이터 형식에 따라 달라집니다. 자세한 내용은 [콘텐츠 컨트롤](../vsto/content-controls.md)을 참조 하세요.

**데이터 소스** 창에서 데이터 필드를 선택한 다음 드롭다운 목록에서 다른 컨트롤을 선택 하 여 다른 컨트롤을 추가할 수 있습니다.

## <a name="objects-in-the-project"></a>프로젝트의 개체

컨트롤 외에도 다음과 같은 데이터 관련 개체가 프로젝트에 자동으로 추가됩니다.

- 데이터베이스에서 연결된 데이터 테이블을 캡슐화하는 형식화된 데이터 세트. 자세한 내용은 [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)를 참조 하세요.

- 컨트롤을 형식화된 데이터 세트에 연결하는 <xref:System.Windows.Forms.BindingSource>. 자세한 내용은 [BindingSource 구성 요소 개요](/dotnet/framework/winforms/controls/bindingsource-component-overview)를 참조 하세요.

- 형식화 된 데이터 집합을 데이터베이스에 연결 하는 TableAdapter입니다. 자세한 내용은 [Tableadapter 만들기 및 구성](../data-tools/create-and-configure-tableadapters.md)을 참조 하세요.

- 데이터 집합의 테이블 어댑터를 조정 하 여 계층적 업데이트를 사용 하는 데 사용 되는 TableAdapterManager입니다. 자세한 내용은 [계층적 업데이트](../data-tools/hierarchical-update.md) 및 [TableAdapterManager reference](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)를 참조 하세요.

프로젝트를 실행하면 컨트롤이 데이터 소스의 첫 번째 레코드를 표시합니다. <xref:System.Windows.Forms.BindingSource>를 사용하여 사용자가 레코드를 스크롤할 수 있게 할 수 있습니다.

### <a name="to-scroll-through-the-records"></a>레코드를 스크롤하려면

- <xref:System.Windows.Forms.BindingSource.MoveNext%2A> 및 <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>와 같은 <xref:System.Windows.Forms.BindingSource> 메서드를 사용합니다.

형식화 된 데이터 집합 및 데이터베이스에 업데이트를 보내는 방법에 대 한 자세한 내용은 [방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [새 데이터 원본 추가](../data-tools/add-new-data-sources.md)
- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [방법: 개체의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office 솔루션에서 로컬 데이터베이스 파일 사용 개요](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource 구성 요소 개요](/dotnet/framework/winforms/controls/bindingsource-component-overview)