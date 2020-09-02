---
title: 콘텐츠 컨트롤
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Toolbox.DropDownListContentControl
- VST.Toolbox.RichTextContentControl
- VST.Toolbox.PlainTextContentControl
- VST.Toolbox.ComboBoxContentControl
- VST.Toolbox.CCBuildingBlockGalleryContentControl
- VST.Toolbox.DatePickerContentControl
- VST.Toolbox.PictureContentControl
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- document building blocks [Office development in Visual Studio]
- restricted permissions [Office development in Visual Studio]
- ComboBoxContentControl class
- PictureContentControl class
- PlainTextContentControl class
- Office documents [Office development in Visual Studio], restricted permissions
- RichTextContentControl class
- content controls [Office development in Visual Studio]
- building block gallery [Office development in Visual Studio]
- controls [Office development in Visual Studio], content controls
- GroupContentControl class
- documents [Office development in Visual Studio], restricted permissions
- DropDownListContentControl class
- DatePickerContentControl class
- data binding [Office development in Visual Studio], content controls
- content controls [Office development in Visual Studio], about content controls
- custom XML parts, content controls
- templates [Office development in Visual Studio], content controls
- BuildingBlockGalleryContentControl class
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8683f5379aaa33446b150adf34f8a5aa57a83ff3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72986186"
---
# <a name="content-controls"></a>콘텐츠 컨트롤
  콘텐츠 컨트롤은 다음과 같은 기능이 있는 문서와 템플릿을 디자인하는 방법을 제공합니다.

- 양식과 같은 제어된 입력이 있는 UI(사용자 인터페이스).

- 사용자가 문서 또는 템플릿의 보호된 섹션을 편집하지 못하도록 하는 제한. 자세한 내용은 [콘텐츠 컨트롤을 사용 하 여 문서 부분 보호](#Protection)를 참조 하세요.

- 데이터 소스에 대한 데이터 바인딩. 자세한 내용은 [콘텐츠 컨트롤에 데이터 바인딩](#DataBinding)을 참조 하세요.

  [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]

  ![비디오에 연결](../vsto/media/playvideo.gif "비디오에 링크") 관련 동영상 데모를 보려면 [Office 시스템에 대 한 Visual Studio Tools를 사용 하 여 Word 2007 콘텐츠 컨트롤에 데이터 바인딩 (3.0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12))을 참조 하세요.

## <a name="overview-of-content-controls"></a>콘텐츠 컨트롤 개요
 콘텐츠 컨트롤은 사용자 입력 및 인쇄 둘 다에 최적화된 UI를 제공합니다. 문서에 콘텐츠 컨트롤을 추가하는 경우 컨트롤은 테두리, 제목 및 사용자에게 지침을 제공할 수 있는 임시 텍스트로 식별됩니다. 컨트롤의 테두리와 제목은 인쇄 버전의 문서에 표시되지 않습니다.

 예를 들어 사용자가 문서의 구역에 날짜를 입력하게 하려는 경우 문서에 날짜 선택 콘텐츠 컨트롤을 추가할 수 있습니다. 사용자가 컨트롤을 클릭하면 표준 날짜 선택 UI가 나타납니다. 컨트롤의 속성을 설정하여 표시되는 지역별 달력을 설정하고 날짜 형식을 지정할 수도 있습니다. 사용자가 날짜를 선택하면 컨트롤의 UI가 숨겨지고 사용자가 문서를 인쇄할 경우 날짜만 나타납니다.

 콘텐츠 컨트롤은 다음 작업을 수행하는 데에도 도움이 됩니다.

- 사용자가 문서의 일부를 편집 또는 삭제하지 못하도록 합니다. 이 기능은 사용자가 읽을 수 있지만 편집할 수 없어야 하는 정보가 문서 또는 템플릿에 있는 경우 또는 사용자가 콘텐츠 컨트롤을 편집할 수 있지만 삭제할 수 없도록 하려는 경우에 유용합니다.

- 문서 또는 템플릿 부분을 데이터에 바인딩합니다. 데이터베이스 필드, [!INCLUDE[dnprdnshort](../sharepoint/includes/dnprdnshort-md.md)]의 관리되는 개체, 문서에 저장된 XML 요소 및 기타 데이터 소스에 콘텐츠 컨트롤을 바인딩할 수 있습니다.

  문서 수준 프로젝트에서는 디자인 타임 또는 런타임에 콘텐츠 컨트롤을 문서에 추가할 수 있습니다. VSTO 추가 기능 프로젝트에서는 런타임에 열려 있는 임의 문서에 콘텐츠 컨트롤을 추가할 수 있습니다. 자세한 내용은 [방법: Word 문서에 콘텐츠 컨트롤 추가](../vsto/how-to-add-content-controls-to-word-documents.md)를 참조 하세요.

> [!NOTE]
> Open XML 형식으로 저장 된 문서 에서만 콘텐츠 컨트롤을 사용할 수 있습니다. Word 97-2003 문서 (*.doc*) 형식에 저장 된 문서에서 콘텐츠 컨트롤을 사용할 수 없습니다.

## <a name="types-of-content-controls"></a>콘텐츠 컨트롤의 형식
 문서에 추가할 수 있는 9가지 형식의 콘텐츠 컨트롤이 있습니다. 대부분의 콘텐츠 컨트롤은 <xref:Microsoft.Office.Tools.Word> 네임스페이스에 해당 형식이 있습니다. 사용 가능한 콘텐츠 컨트롤 중 하나를 나타낼 수 있는 제네릭 <xref:Microsoft.Office.Tools.Word.ContentControl>을 사용할 수도 있습니다. 사용 가능한 각 콘텐츠 컨트롤을 사용 하는 방법을 보여 주는 연습은 [연습: 콘텐츠 컨트롤을 사용 하 여 템플릿 만들기](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)를 참조 하세요.

### <a name="build-block-gallery"></a>빌드 블록 갤러리
 사용자는 문서 블록 갤러리를 사용 하 여 문서에 삽입할 *문서 블록* 목록에서 선택할 수 있습니다. 문서 블록은 일반적인 표지, 서식이 지정된 표 또는 머리글과 같이 여러 번 사용하기 위해 생성된 콘텐츠입니다. 자세한 내용은 유형을 참조 하세요 <xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl> . 구성 요소에 대 한 자세한 내용은 [Word 2007의 개발자를 위한 새로운 기능](/previous-versions/office/developer/office-2007/bb266218(v=office.12))을 참조 하세요.

### <a name="check-box"></a>확인란
 확인란은 이진 상태(선택됨 또는 선택 취소됨)를 나타내는 UI를 제공합니다.

 다른 형식의 콘텐츠 컨트롤과 달리 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]은 확인란 콘텐츠 컨트롤을 나타내는 특정 형식을 제공하지 않습니다. 즉, `CheckBoxContentControl` 형식이 없습니다. 그러나 프로그래밍 방식으로 문서에 제네릭 <xref:Microsoft.Office.Tools.Word.ContentControl>을 추가하여 확인란 콘텐츠 컨트롤을 만들 수 있습니다. 자세한 내용은 [Word 프로젝트의 확인란 콘텐츠 컨트롤](#checkbox)을 참조 하세요.

### <a name="combo-box"></a>콤보 상자
 콤보 상자에는 사용자가 선택할 수 있는 항목 목록이 표시됩니다. 드롭다운 목록과 달리 콤보 상자를 사용하면 사용자가 고유한 항목을 추가할 수 있습니다. 자세한 내용은 유형을 참조 하세요 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl> .

### <a name="date-picker"></a>날짜 선택기
 날짜 선택은 날짜를 선택하기 위한 달력 UI를 제공합니다. 최종 사용자가 컨트롤에서 드롭다운 화살표를 클릭하면 달력이 나타납니다. 지역별 달력 및 다른 날짜 형식을 사용할 수 있습니다. 자세한 내용은 유형을 참조 하세요 <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> .

### <a name="drop-down-list"></a>드롭다운 목록
 드롭다운 목록에는 사용자가 선택할 수 있는 항목 목록이 표시됩니다. 콤보 상자와 달리 드롭다운 목록에서는 사용자가 항목을 추가하거나 편집할 수 없습니다. 자세한 내용은 유형을 참조 하세요 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> .

### <a name="group"></a>그룹
 그룹 컨트롤은 사용자가 편집하거나 삭제할 수 없는 문서의 보호된 영역을 정의합니다. 그룹 컨트롤에는 텍스트, 표, 그래픽 및 기타 콘텐츠 컨트롤과 같은 모든 문서 항목이 포함될 수 있습니다. 자세한 내용은 유형을 참조 하세요 <xref:Microsoft.Office.Tools.Word.GroupContentControl> .

### <a name="picture"></a>Picture
 그림 컨트롤은 이미지를 표시합니다. 디자인 타임 또는 런타임에 이미지를 지정할 수 있거나, 사용자가 이 컨트롤을 클릭하여 문서에 삽입할 이미지를 선택할 수 있습니다. 자세한 내용은 유형을 참조 하세요 <xref:Microsoft.Office.Tools.Word.PictureContentControl> .

### <a name="rich-text"></a>서식 있는 텍스트
 서식 있는 텍스트 컨트롤에는 텍스트 또는 표, 그림, 기타 콘텐츠 컨트롤과 같은 항목이 포함됩니다. 자세한 내용은 유형을 참조 하세요 <xref:Microsoft.Office.Tools.Word.RichTextContentControl> .

### <a name="plain-text"></a>일반 텍스트
 일반 텍스트 컨트롤에는 텍스트가 포함됩니다. 일반 텍스트 컨트롤에는 표, 그림, 기타 콘텐츠 컨트롤과 같은 항목이 포함될 수 없습니다. 또한 일반 텍스트 컨트롤의 모든 텍스트는 동일한 서식을 갖습니다. 예를 들어 일반 텍스트 컨트롤에 있는 문장의 한 단어를 기울임꼴로 표시하는 경우 컨트롤 안의 모든 텍스트가 기울임꼴로 표시됩니다. 자세한 내용은 유형을 참조 하세요 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> .

### <a name="generic-content-control"></a>일반 콘텐츠 컨트롤
 제네릭 콘텐츠 컨트롤은 사용 가능한 콘텐츠 컨트롤 형식 중 하나를 나타낼 수 있는 <xref:Microsoft.Office.Tools.Word.ContentControl> 개체입니다. <xref:Microsoft.Office.Tools.Word.ContentControl.Type%2A> 속성을 사용하여 다른 콘텐츠 컨트롤 형식처럼 동작하도록 <xref:Microsoft.Office.Tools.Word.ContentControl> 개체를 변경할 수 있습니다. 예를 들어 일반 텍스트 컨트롤을 나타내는 <xref:Microsoft.Office.Tools.Word.ContentControl> 개체를 만드는 경우 콤보 상자처럼 동작하도록 런타임에 변경할 수 있습니다.

 <xref:Microsoft.Office.Tools.Word.ContentControl> 개체는 런타임에만 만들 수 있고 디자인 타임에는 만들 수 없습니다. 자세한 내용은 [방법: Word 문서에 콘텐츠 컨트롤 추가](../vsto/how-to-add-content-controls-to-word-documents.md)를 참조 하세요.

## <a name="common-features-of-content-controls"></a>콘텐츠 컨트롤의 일반적인 기능
 대부분의 콘텐츠 컨트롤은 일반적인 작업을 수행하는 데 사용할 수 있는 일련의 멤버를 공유합니다. 다음 표에서는 이러한 멤버를 사용하여 수행할 수 있는 일부 작업을 설명합니다.

|작업|방법:|
|--------------------|--------------|
|컨트롤에 표시되는 텍스트를 가져오거나 설정합니다.|**Text** 속성을 사용 합니다. **참고:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> 및 형식에는 <xref:Microsoft.Office.Tools.Word.ContentControl> 이 속성이 없습니다.|
|사용자가 컨트롤을 편집하거나, 컨트롤이 데이터 소스의 데이터로 채워지거나, 컨트롤의 내용이 삭제될 때까지 컨트롤에 표시되는 임시 텍스트를 가져오거나 설정합니다.|**PlaceholderText** 속성을 사용 합니다. **참고:**  <xref:Microsoft.Office.Tools.Word.PictureContentControl> 형식에이 속성이 없습니다.|
|사용자가 클릭할 때 콘텐츠 컨트롤의 테두리에 표시되는 제목을 가져오거나 설정합니다.|**Title** 속성을 사용 합니다.|
|사용자 컨트롤을 편집한 후 자동으로 문서에서 컨트롤을 제거합니다. 컨트롤의 텍스트는 문서에 남아 있습니다.|**임시** 속성을 사용 합니다.|
|사용자가 콘텐츠 컨트롤을 클릭하거나 커서가 프로그래밍 방식으로 콘텐츠 컨트롤로 이동할 때 코드를 실행합니다.|컨트롤의 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> 이벤트를 처리합니다.|
|사용자가 콘텐츠 컨트롤 바깥쪽을 클릭하거나 커서가 프로그래밍 방식으로 콘텐츠 컨트롤 바깥쪽으로 이동할 때 코드를 실행합니다.|컨트롤의 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Exiting> 이벤트를 처리합니다.|
|다시 실행 또는 실행 취소 작업의 결과로 콘텐츠 컨트롤이 문서에 추가된 후 코드를 실행합니다.|컨트롤의 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Added> 이벤트를 처리합니다.|
|문서에서 콘텐츠 컨트롤이 삭제되기 바로 전에 코드를 실행합니다.|컨트롤의 <xref:Microsoft.Office.Tools.Word.ContentControlBase.Deleting> 이벤트를 처리합니다.|

## <a name="protect-parts-of-documents-by-using-content-controls"></a><a name="Protection"></a> 콘텐츠 컨트롤을 사용 하 여 문서 부분 보호
 문서의 일부를 보호하는 경우 사용자가 문서의 해당 부분에서 내용을 변경하거나 삭제하지 못하도록 합니다. 콘텐츠 컨트롤을 사용하여 문서 부분을 보호할 수 있는 여러 가지 방법이 있습니다.

 보호하려는 영역이 콘텐츠 컨트롤 안에 있는 경우 콘텐츠 컨트롤의 속성을 사용하여 사용자가 컨트롤을 편집 또는 삭제하지 못하도록 할 수 있습니다.

- **Lockcontents** 속성은 사용자가 내용을 편집 하지 못하도록 합니다.

- **LockContentControl** 속성은 사용자가 컨트롤을 삭제 하지 못하도록 합니다.

  보호하려는 영역이 콘텐츠 컨트롤 안에 없거나 콘텐츠 컨트롤 및 다른 형식의 콘텐츠를 포함하는 영역을 보호하려는 경우 <xref:Microsoft.Office.Tools.Word.GroupContentControl>에 전체 영역을 넣을 수 있습니다. 다른 콘텐츠 컨트롤과 달리 <xref:Microsoft.Office.Tools.Word.GroupContentControl>은 사용자에게 표시되는 UI를 제공하지 않습니다. 사용자가 편집할 수 없는 영역을 정의하는 용도로만 사용됩니다.

> [!NOTE]
> 포함된 콘텐츠 컨트롤을 포함하는 <xref:Microsoft.Office.Tools.Word.GroupContentControl>을 만드는 경우 포함된 콘텐츠 컨트롤은 자동으로 보호되지 않습니다. 사용자가 내용을 편집 하지 못하도록 각 포함 된 컨트롤의 **Lockcontents** 속성을 사용 해야 합니다.

 콘텐츠 컨트롤을 사용 하 여 문서 부분을 보호 하는 방법에 대 한 자세한 내용은 [방법: 콘텐츠 컨트롤을 사용 하 여 문서 부분 보호](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)를 참조 하세요.

## <a name="bind-data-to-content-controls"></a><a name="DataBinding"></a> 콘텐츠 컨트롤에 데이터 바인딩
 데이터 소스에 콘텐츠 컨트롤을 바인딩하여 문서의 데이터를 표시할 수 있습니다. 데이터 소스가 업데이트되면 콘텐츠 컨트롤에 변경 내용이 반영됩니다. 변경 내용을 데이터 소스에 다시 저장할 수도 있습니다.

 콘텐츠 컨트롤은 다음과 같은 데이터 바인딩 옵션을 제공합니다.

- Windows Forms과 동일한 데이터 바인딩 모델을 사용하여 데이터베이스 필드 또는 관리되는 개체에 콘텐츠 컨트롤을 바인딩할 수 있습니다.

- 문서에 포함 된 XML 조각 ( *사용자 지정 xml 부분*)의 요소에 콘텐츠 컨트롤을 바인딩할 수 있습니다.

  Office 솔루션의 호스트 컨트롤을 데이터에 바인딩하는 방법에 대 한 개요는 [office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)을 참조 하세요.

### <a name="use-the-windows-forms-data-binding-model"></a>Windows Forms 데이터 바인딩 모델 사용
 대부분의 콘텐츠 컨트롤은 Windows Forms에서 사용하는 단순 데이터 바인딩 모델을 지원합니다. 단순 데이터 바인딩은 컨트롤이 데이터 테이블의 열 값과 같은 단일 데이터 요소에 바인딩됨을 의미합니다. 자세한 내용은 [데이터 바인딩 및 Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)을 참조 하세요.

 문서 수준 프로젝트에서의 **데이터 소스** 창을 사용 하 여 콘텐츠 컨트롤에 데이터를 바인딩할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 데이터 바인딩된 콘텐츠 컨트롤을 문서에 추가 하는 방법에 대 한 자세한 내용은 [방법: 데이터베이스의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-a-database.md) 및 [방법: 개체의 데이터로 문서 채우기](../vsto/how-to-populate-documents-with-data-from-objects.md)를 참조 하세요.

 다음 표에서는 **데이터 소스** 창에서 각 데이터 형식에 바인딩할 수 있는 콘텐츠 컨트롤을 보여 줍니다.

|데이터 형식|기본 콘텐츠 컨트롤|이 데이터 형식에 바인딩할 수 있는 기타 콘텐츠 컨트롤|
|---------------|-----------------------------|----------------------------------------------------------------|
|<xref:System.Boolean><br /><br /> <xref:System.Byte><br /><br /> <xref:System.Char><br /><br /> <xref:System.Double><br /><br /> <xref:System.Enum><br /><br /> <xref:System.Guid><br /><br /> <xref:System.Int16><br /><br /> <xref:System.Int32><br /><br /> <xref:System.Int64><br /><br /> <xref:System.SByte><br /><br /> <xref:System.Single><br /><br /> <xref:System.String><br /><br /> <xref:System.TimeSpan><br /><br /> <xref:System.UInt16><br /><br /> <xref:System.UInt32><br /><br /> <xref:System.UInt64>|<xref:Microsoft.Office.Tools.Word.PlainTextContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.DatePickerContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.DateTime>|<xref:Microsoft.Office.Tools.Word.DatePickerContentControl>|<xref:Microsoft.Office.Tools.Word.BuildingBlockGalleryContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.PlainTextContentControl><br /><br /> <xref:Microsoft.Office.Tools.Word.RichTextContentControl>|
|<xref:System.Drawing.Image><br /><br /> <xref:System.Byte> 배열|<xref:Microsoft.Office.Tools.Word.PictureContentControl>|없음|

 문서 수준 및 VSTO 추가 기능 프로젝트에서 컨트롤 <xref:System.Windows.Forms.IBindableComponent.DataBindings%2A> 속성의 <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> 메서드를 사용하여 프로그래밍 방식으로 콘텐츠 컨트롤을 데이터 소스에 바인딩할 수 있습니다. 이 작업을 수행 하는 경우 문자열 **텍스트** 를 메서드의 *propertyName* 매개 변수에 전달 <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> 합니다. **텍스트** 속성은 콘텐츠 컨트롤의 기본 데이터 바인딩 속성입니다.

 또한 콘텐츠 컨트롤은 컨트롤의 변경 내용이 데이터 소스에 업데이트되는 양방향 데이터 바인딩을 지원합니다. 자세한 내용은 [방법: 호스트 컨트롤의 데이터로 데이터 소스 업데이트](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)를 참조 하세요.

> [!NOTE]
> 콘텐츠 컨트롤은 복잡한 데이터 바인딩을 지원하지 않습니다. Windows Forms 데이터 모델을 사용하여 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 또는 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>을 데이터 소스에 바인딩하는 경우 사용자가 컨트롤을 클릭하면 단일 값만 표시됩니다. 사용자가 선택할 수 있는 데이터 값 집합에 이러한 컨트롤을 바인딩하려는 경우 사용자 지정 XML 부분의 요소에 해당 컨트롤을 바인딩할 수 있습니다.

### <a name="bind-content-controls-to-custom-xml-parts"></a>사용자 지정 XML 부분에 콘텐츠 컨트롤 바인딩
 문서에 포함된 사용자 지정 XML 부분의 요소에 일부 콘텐츠 컨트롤을 바인딩할 수 있습니다. 사용자 지정 XML 부분에 대 한 자세한 내용은 [사용자 지정 xml 부분 개요](../vsto/custom-xml-parts-overview.md)를 참조 하세요.

 사용자 지정 XML 부분의 요소에 콘텐츠 컨트롤을 바인딩하려면 컨트롤의 **Xmlmapping** 속성을 사용 합니다. 다음 코드 예제에서는 이미 문서에 추가된 사용자 지정 XML 부분에서 `Product` 노드 아래의 `Price` 요소에 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>을 바인딩하는 방법을 보여 줍니다.

```vb
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price")
```

```csharp
plainTextContentControl1.XMLMapping.SetMapping("/Product/Price", String.Empty, null);
```

 사용자 지정 XML 부분에 콘텐츠 컨트롤을 바인딩하는 방법을 자세히 보여 주는 연습은 [연습: 콘텐츠 컨트롤을 사용자 지정 xml 부분에 바인딩](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)을 참조 하세요.

 사용자 지정 XML 부분에 콘텐츠 컨트롤을 바인딩하는 경우 양방향 데이터 바인딩이 자동으로 사용됩니다. 사용자가 컨트롤의 텍스트를 편집하는 경우 해당 XML 요소가 자동으로 업데이트됩니다. 마찬가지로, 사용자 지정 XML 부분의 요소 값이 변경되는 경우 XML 요소에 바인딩된 콘텐츠 컨트롤에 새 데이터가 표시됩니다.

 사용자 지정 XML 부분에 다음과 같은 형식의 콘텐츠 컨트롤을 바인딩할 수 있습니다.

- <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>

- <xref:Microsoft.Office.Tools.Word.DatePickerContentControl>

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>

- <xref:Microsoft.Office.Tools.Word.PictureContentControl>

- <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>

### <a name="data-bind-events-for-content-controls"></a>콘텐츠 컨트롤에 대 한 데이터 바인딩 이벤트
 모든 콘텐츠 컨트롤은 데이터 소스가 업데이트되기 전에 컨트롤의 텍스트가 특정 조건을 충족하는지 확인하는 작업과 같은 데이터 관련 작업을 수행하기 위해 처리할 수 있는 이벤트 집합을 제공합니다. 다음 표에서는 데이터 바인딩과 관련된 콘텐츠 컨트롤 이벤트를 보여 줍니다.

|Task|이벤트|
|----------|-----------|
|Word에서 사용자 지정 XML 부분에 바인딩된 콘텐츠 컨트롤의 텍스트를 자동으로 업데이트하기 바로 전에 코드를 실행합니다.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.ContentUpdating>|
|Word에서 콘텐츠 컨트롤에 바인딩된 사용자 지정 XML 부분의 데이터를 자동으로 업데이트하기 바로 전, 즉 콘텐츠 컨트롤의 텍스트가 변경된 후에 코드를 실행합니다.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating>|
|사용자 지정 조건에 따라 컨트롤 내용의 유효성을 검사하는 사용자 고유의 코드를 실행합니다.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validating>|
|컨트롤 내용의 유효성 검사가 성공적으로 완료된 후에 코드를 실행합니다.|<xref:Microsoft.Office.Tools.Word.ContentControlBase.Validated>|

## <a name="limitations-of-content-controls"></a>콘텐츠 컨트롤의 제한 사항
 Office 프로젝트에서 콘텐츠 컨트롤을 사용하는 경우 다음과 같은 제한 사항에 주의하세요.

### <a name="behavior-differences-between-design-time-and-runtime"></a>디자인 타임 및 런타임 간의 동작 차이
 Microsoft Office Word에서 런타임에 콘텐츠 컨트롤에 적용하는 제한 사항은 대부분 디자인 타임에 적용되지 않습니다. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 문서 수준 솔루션의 UI를 디자인하는 경우 런타임에 지원되는 방식으로만 콘텐츠 컨트롤을 수정해야 합니다.

 런타임에 컨트롤이 지원하지 않는 방법으로 디자인 타임에 콘텐츠 컨트롤을 수정하는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 디자이너에서 지원되지 않는 변경 내용을 경고하지 않습니다. 그러나 프로젝트를 디버그 또는 실행하거나 프로젝트를 저장한 후 다시 여는 경우 Word에서 오류 메시지를 표시하고 문서를 복구할 수 있는 권한을 요청합니다. 문서를 복구하면 컨트롤에서 지원되지 않는 콘텐츠 및 서식이 모두 제거됩니다.

 예를 들어 Word에서 디자인 타임에 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl>에 표를 추가하지 못하도록 차단하지는 않습니다. 그러나 <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> 개체는 런타임에 표를 포함할 수 없으므로 Word에서 문서를 열 때 오류 메시지가 표시됩니다.

 또한 콘텐츠 컨트롤의 동작을 정의하는 많은 속성은 디자인 타임에 영향을 주지 않습니다. 예를 들어 디자인 타임에 콘텐츠 컨트롤의 **Lockcontents** 속성을 **True** 로 설정 하는 경우 디자이너에서 컨트롤의 텍스트를 편집할 수 있습니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] . 이 속성은 런타임에 사용자가 컨트롤을 편집하지 못하도록 하는 역할만 합니다.

### <a name="event-limitations"></a>이벤트 제한 사항
 콘텐츠 컨트롤은 사용자가 컨트롤의 텍스트 또는 기타 항목을 변경할 때 발생하는 이벤트를 제공하지 않습니다. 예를 들어 사용자가 <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> 또는 <xref:Microsoft.Office.Tools.Word.ComboBoxContentControl>에서 다른 항목을 선택할 때 발생하는 이벤트가 없습니다.

 사용자가 콘텐츠 컨트롤의 내용을 편집하는 시기를 확인하기 위해 사용자 지정 XML 부분에 컨트롤을 바인딩한 다음 <xref:Microsoft.Office.Tools.Word.ContentControlBase.StoreUpdating> 이벤트를 처리할 수 있습니다. 이 이벤트는 사용자가 사용자 지정 XML 부분에 바인딩된 컨트롤의 내용을 변경할 때 발생합니다. 사용자 지정 XML 부분에 콘텐츠 컨트롤을 바인딩하는 방법을 보여 주는 연습은 [연습: 콘텐츠 컨트롤을 사용자 지정 xml 부분에 바인딩](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)을 참조 하세요.

### <a name="check-box-content-controls-in-word-projects"></a><a name="checkbox"></a> Word 프로젝트의 확인란 콘텐츠 컨트롤
 Word 2010에서는 확인란을 나타내는 새로운 형식의 콘텐츠 컨트롤이 도입되었습니다. 그러나는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] Office 프로젝트에서 사용할 수 있는 해당 CheckBoxContentControl 형식을 제공 하지 않습니다. [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] 또는 Word 2010 프로젝트에서 확인란 콘텐츠 컨트롤을 만들려면 <xref:Microsoft.Office.Tools.Word.ControlCollection.AddContentControl%2A> 메서드를 사용하여 <xref:Microsoft.Office.Tools.Word.ContentControl> 개체를 만들고 <xref:Microsoft.Office.Interop.Word.WdContentControlType.wdContentControlCheckBox> 값을 메서드에 전달하여 확인란 콘텐츠 컨트롤을 지정합니다. 다음 코드 예제에서는 이 작업을 수행하는 방법을 보여 줍니다.

 [!code-vb[Trin_ContentControlReference#800](../vsto/codesnippet/VisualBasic/trin_contentcontrolreference/checkbox.vb#800)]
 [!code-csharp[Trin_ContentControlReference#800](../vsto/codesnippet/CSharp/trin_wordcontentcontrolreference/checkbox.cs#800)]

## <a name="see-also"></a>참조
- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)
- [방법: Word 문서에 콘텐츠 컨트롤 추가](../vsto/how-to-add-content-controls-to-word-documents.md)
- [연습: 콘텐츠 컨트롤을 사용 하 여 템플릿 만들기](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)
- [Office 솔루션의 데이터](../vsto/data-in-office-solutions.md)
- [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
