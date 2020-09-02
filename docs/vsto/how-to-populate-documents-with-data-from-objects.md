---
title: '방법: 개체의 데이터로 문서 채우기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38461fc30f71a811033ea70bfe560a6492f56e12
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547175"
---
# <a name="how-to-populate-documents-with-data-from-objects"></a>방법: 개체의 데이터로 문서 채우기

Windows Forms 프로젝트에서와 동일한 방식으로 Microsoft Office에 대한 문서 수준 프로젝트에서 데이터 개체의 데이터에 액세스할 수 있습니다. 동일한 도구 및 코드를 사용하여 개체의 데이터를 솔루션으로 가져오며, Windows Forms 컨트롤을 사용하여 데이터를 표시할 수 있습니다. 또한 호스트 컨트롤을 사용하여 데이터를 표시할 수 있습니다. 호스트 컨트롤은 이벤트 및 데이터 바인딩 기능을 통해 향상된 Microsoft Office Word의 네이티브 개체입니다. 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

[!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

개체의 데이터로 문서를 채우려면 세 가지 기본 단계를 완료해야 합니다.

- 데이터에 바인딩할 수 있는 문서에 컨트롤을 추가합니다.

- 문서에 데이터 개체를 추가합니다.

- BindingSource에 데이터 개체를 연결합니다.

## <a name="to-add-a-data-object"></a>데이터 개체를 추가하려면

데이터 개체를 추가 하려면 **데이터 소스** 창을 열고 개체에서 데이터 원본을 만듭니다. 자세한 내용은 [새 데이터 소스 추가](../data-tools/add-new-data-sources.md)를 참조하세요.

## <a name="connect-the-data-object-to-the-bindingsource"></a>BindingSource에 데이터 개체 연결

문서 수준 프로젝트에서 문서에 컨트롤을 추가하고 디자인 타임에 데이터에 바인딩합니다.

VSTO 추가 기능 프로젝트에서 컨트롤을 만들고 런타임에 바인딩합니다.

### <a name="document-level-projects"></a>문서 수준 프로젝트

데이터 개체를 BindingSource에 연결 하려면 다음을 수행 합니다.

1. **데이터 원본** 창에서 원하는 데이터 필드를 문서로 끌어옵니다. 그러면 자동으로 컨트롤을 만듭니다.

2. 코드에서 데이터 원본에 대해 선택한 개체 유형의 인스턴스를 만듭니다.

3. 인스턴스를 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 의 <xref:System.Windows.Forms.BindingSource>속성에 할당합니다.

### <a name="application-level-projects"></a>응용 프로그램 수준 프로젝트

데이터 개체를 BindingSource에 연결 하려면 다음을 수행 합니다.

1. 코드에서 데이터 원본과 연결되는 개체 유형의 인스턴스를 만듭니다.

2. <xref:System.Windows.Forms.BindingSource>의 인스턴스를 만듭니다.

3. 데이터 원본 인스턴스를 <xref:System.Windows.Forms.BindingSource.DataSource%2A> 의 <xref:System.Windows.Forms.BindingSource>속성에 할당합니다.

4. 데이터 원본을 데이터 바인딩으로 컨트롤에 추가합니다.

## <a name="see-also"></a>추가 정보

- [새 데이터 원본 추가](../data-tools/add-new-data-sources.md)
- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [방법: 데이터베이스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [BindingSource 구성 요소 개요](/dotnet/framework/winforms/controls/bindingsource-component-overview)