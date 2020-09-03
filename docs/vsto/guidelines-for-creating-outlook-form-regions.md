---
title: Outlook 양식 영역 만들기 지침
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- form regions [Office development in Visual Studio], guidelines
- icons [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: a962b1ae2bff7b9a954204485a6ee73a3b63eb7b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255948"
---
# <a name="guidelines-to-create-outlook-form-regions"></a>Outlook 양식 영역 만들기 지침
  다음 정보를 통해 양식 영역을 최적화하고 잠재적인 문제를 방지할 수 있습니다.

- [양식 영역 이름을 사용](#UsingFormRegions)합니다.

- [양식 영역 상속을 사용 하지 않습니다](#DisablingInheritance).

- [형식 및 메시지 클래스 이름을 이해](#ClassNames)합니다.

- [읽기 창의 인접 양식 영역을 디자인](#ReadingPane)합니다.

- [최적 아이콘 크기를 사용](#UsingOptimal)합니다.

  양식 영역에 대 한 자세한 내용은 [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

  [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="use-form-region-names"></a><a name="UsingFormRegions"></a> 양식 영역 이름 사용
 양식 영역을 설명하기 위해 사용하는 여러 가지 이름이 있습니다. 이러한 이름과 이들이 양식 영역에 영향을 미치는 방법 간의 차이점을 이해하는 것이 중요합니다. 다음 표에서는 각 이름에 대해 설명합니다.

|양식 영역 이름|설명|
|----------------------|-----------------|
|양식 영역 항목 이름|**새 항목 추가** 대화 상자에서 **Outlook 양식 영역** 항목에 대해 지정한 이름입니다. 이 이름은 **솔루션 탐색기**에 나타나는 양식 영역 코드의 이름입니다.|
|<xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> 속성|**새 Outlook 양식 영역** 마법사의 **설명 텍스트를 입력하고 디스플레이 기본 설정을 선택하세요.** 페이지에서 이 이름을 지정합니다. 이 이름은 **속성** 창에 **FormRegionName** 속성으로 나타납니다.<br /><br /> <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> 속성을 사용하여 Outlook UI(사용자 인터페이스)에서 양식 영역을 식별하는 레이블을 지정합니다. 별도 양식 영역의 경우 이 이름이 Outlook 항목의 리본에 단추로 나타납니다.<br /><br /> 인접한 양식 영역의 경우 이 이름이 양식 영역 위에 머리글 텍스트로 나타납니다.|
|`Microsoft.Office.Tools.Outlook.FormRegionName` 특성|**Outlook 양식 영역** 항목을 프로젝트에 추가하는 경우 Visual Studio는 이 속성을 양식 영역의 정규화된 이름으로 설정합니다. 기본 정규화된 이름은 VSTO 추가 기능 이름, 점, 양식 영역 이름이 차례로 연결된 이름입니다(예: `OutlookAddIn1.FormRegion1`).<br /><br /> 또한 이 정규화된 이름은 양식 영역 팩터리 클래스의 맨 위에 특성으로 나타납니다.<br /><br /> 특성을 사용 `Microsoft.Office.Tools.Outlook.FormRegionName` 하 여 모든 OUTLOOK VSTO 추가 기능에서 양식 영역을 고유 하 게 식별 합니다. `Microsoft.Office.Tools.Outlook.FormRegionName` 양식 영역 항목의 이름을 바꾸거나 속성을 변경 하 여 특성의 값을 변경할 수 없습니다 <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.FormRegionName%2A> . 이 이름을 변경하려면 양식 영역 코드 파일의 `Microsoft.Office.Tools.Outlook.FormRegionName` 특성을 수정해야 합니다.|

## <a name="disable-form-region-inheritance"></a><a name="DisablingInheritance"></a> 양식 영역 상속 사용 안 함
 기본적으로 사용자 지정 메시지 클래스는 기본 메시지 클래스의 모든 양식 영역 연결을 상속합니다. 예를 들어 `IPM.Task.Contoso`라는 메시지 클래스가 `IPM.Task`에서 파생됩니다. 따라서 `IPM.Task.Contoso`는 `IPM.Task`의 양식 영역 연결을 상속합니다.

 양식 영역을 파생된 메시지 클래스와 연결하지 않으려면 양식 영역의 <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> 속성을 **true**를 참조하세요. 예를 들어 인접 양식 영역을에 연결 하 `IPM.Task` 고 속성을 true로 설정 하는 경우 <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ExactMessageClass%2A> 양식 영역은 표준 작업 폼의 아래쪽에만 추가 됩니다. **true** 양식 영역이 사용자 지정된 버전의 표준 작업 양식 하단에는 추가되지 않습니다.

## <a name="understand-types-and-message-class-names"></a><a name="ClassNames"></a> 형식 및 메시지 클래스 이름 이해
 Outlook 항목의 형식 이름은 Outlook 항목의 메시지 클래스 이름과 다릅니다. 예를 들어 RSS 항목의 형식 이름은 `Microsoft.Office.Interop.Outlook.PostItem`입니다. RSS 항목의 메시지 클래스 이름은 `IPM.Post.RSS`입니다.

 형식 이름을 사용하여 코드의 Outlook 항목을 참조합니다. 형식 이름 목록은 [Outlook 메시지 클래스에 양식 영역 연결](../vsto/associating-a-form-region-with-an-outlook-message-class.md)을 참조 하세요.

 **새 Outlook 양식 영역** 마법사에서 Outlook 항목의 메시지 클래스 이름을 사용하여 항목을 양식 영역과 연결합니다. 유효한 메시지 클래스 이름 목록은 [Outlook 메시지 클래스에 양식 영역 연결](../vsto/associating-a-form-region-with-an-outlook-message-class.md)을 참조 하세요.

## <a name="design-adjoining-form-regions-for-the-reading-pane"></a><a name="ReadingPane"></a> 읽기 창의 인접 양식 영역 디자인
 Outlook 읽기 창을 사용하여 항목을 열지 않고도 Outlook 항목을 미리 볼 수 있습니다. 읽기 창은 읽기 전용으로 설계되어 있습니다. 따라서 항목 및 양식 영역이 읽기 창에서 열리는 경우 인접 양식 영역에 추가하는 입력 컨트롤(예: 텍스트 상자)이 예상대로 동작하지 않을 수 있습니다.

 예를 들어 인접 양식 영역을 가진 항목이 읽기 창에서 열려 있으면 다음과 같은 상황이 가능합니다.

1. 양식 영역에 있는 텍스트 상자에서 일부 텍스트를 선택합니다.

2. **Delete**키를 누릅니다.

3. 텍스트 상자의 텍스트 대신 전체 메일 항목이 삭제됩니다.

   입력 컨트롤을 포함하는 인접 양식 영역을 디자인하는 경우 읽기 창에서 컨트롤을 테스트하여 제대로 작동하는지 확인합니다. 예상대로 작동하지 않는 컨트롤을 사용하지 않도록 설정하는 사용자 지정 코드를 추가하는 것이 좋습니다.

   또는 양식 영역의 <xref:Microsoft.Office.Tools.Outlook.FormRegionManifest.ShowInspectorRead%2A> 속성을 **False**를 참조하세요. 이렇게 하면 읽기 창에서 양식 영역을 사용할 수 없습니다.

## <a name="use-optimal-icon-sizes"></a><a name="UsingOptimal"></a> 최적 아이콘 크기 사용
 **속성** 창의 **아이콘** 속성 그룹에서 아이콘 속성을 설정하여 양식 영역에 표시하려는 아이콘을 지정할 수 있습니다. 가장 좋은 시각적 품질을 달성하려면 다음 지침을 따릅니다.

- **페이지** 아이콘에 대해서는 PNG(이동식 네트워크 그래픽) 파일을 사용합니다.

- **창** 아이콘은 32X32 픽셀이어야 합니다.

- 다른 모든 아이콘은 16X16 픽셀이어야 합니다.

  별도, 대체 및 모두 대체 양식 영역을 포함하는 항목에 대해 검사기의 리본에 표시할 **페이지** 아이콘입니다.

  **창** 아이콘은 **Alt** + 바꾸기 또는 모두 바꾸기 양식 영역을 표시 하는 열려 있는 항목의 대체**탭** 대화 상자 및 알림 영역에 나타납니다.

## <a name="see-also"></a>참고 항목
- [런타임에 양식 영역 액세스](../vsto/accessing-a-form-region-at-run-time.md)
- [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)
- [연습: Outlook 양식 영역 디자인](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [방법: Outlook 추가 기능 프로젝트에 양식 영역 추가](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Outlook 메시지 클래스에 양식 영역 연결](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
