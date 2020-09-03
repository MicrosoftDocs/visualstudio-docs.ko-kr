---
title: '방법: SharePoint 웹 파트 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Web Parts [SharePoint development in Visual Studio], adding
- Web Parts [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 2a8c02cce2f55374b4d62ba5663e8b3fe85b55b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86016445"
---
# <a name="how-to-create-a-sharepoint-web-part"></a>방법: SharePoint 웹 파트 만들기
  SharePoint 프로젝트에 **웹 파트** 항목을 추가 하 고 웹 파트에 대 한 코드 파일을 편집 하거나 디자이너를 사용 하 여 웹 파트를 만들고 사용자 지정할 수 있습니다. 자세한 내용은 [방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)를 참조 하세요.

### <a name="to-create-a-sharepoint-web-part"></a>SharePoint 웹 파트를 만들려면

1. SharePoint 프로젝트를 만들거나 엽니다.

     자세한 내용은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)을 참조 하세요.

2. **솔루션 탐색기** 에서 SharePoint 프로젝트 노드를 선택한 다음 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

3. **새 항목 추가** 대화 상자에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

4. SharePoint 템플릿 목록에서 **웹 파트**를 선택 합니다.

5. **이름** 상자에서 웹 파트의 이름을 지정한 다음 **추가** 단추를 선택 합니다.

     웹 파트는 **솔루션 탐색기**표시 됩니다. 웹 파트에 포함 된 파일에 대 한 자세한 내용은 [SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)를 참조 하세요.

6. **솔루션 탐색기**에서 방금 만든 웹 파트에 대 한 코드 파일을 엽니다.

     예를 들어 웹 파트의 이름이 *WebPart1*인 경우 *WebPart1* (Visual Basic) 또는 *WebPart1.cs* (c #)를 엽니다.

7. 코드 파일에서 <xref:System.Web.UI.Control.CreateChildControls%2A> 메서드에 컨트롤을 추가합니다.

     예제는 [연습: SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)
- [방법: 디자이너를 사용 하 여 SharePoint 웹 파트 만들기](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)
- [연습: SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)
- [연습: 디자이너를 사용 하 여 SharePoint 용 웹 파트 만들기](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)
