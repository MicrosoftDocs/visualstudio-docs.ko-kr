---
title: '방법: 응용 프로그램 페이지 만들기 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application pages [SharePoint development in Visual Studio], adding
- application pages [SharePoint development in Visual Studio], creating
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 32e6fbb7cece4c3b7513dfc1f5de3aca22f145ee
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: ko-KR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016944"
---
# <a name="how-to-create-an-application-page"></a>방법: 응용 프로그램 페이지 만들기
  하나 이상의 SharePoint 사이트에 대한 ASP.NET 웹 페이지를 만들 수 있습니다. SharePoint에서는 이러한 페이지를 응용 프로그램 페이지 라고 합니다. 사이트 페이지와 달리 응용 프로그램 페이지에는 페이지 뒤에 실행 되는 코드가 포함 되어 있습니다. 자세한 내용은 [SharePoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)를 참조 하세요.

### <a name="to-create-an-application-page"></a>응용 프로그램 페이지를 만들려면

1. Visual Studio에서 SharePoint 프로젝트를 열거나 만듭니다.

     자세한 내용은 [SharePoint 프로젝트 및 프로젝트 항목 템플릿](../sharepoint/sharepoint-project-and-project-item-templates.md)을 참조 하세요.

2. **솔루션 탐색기**에서 프로젝트 노드를 선택합니다.

3. 메뉴 모음에서 **프로젝트**  >  **새 항목 추가**를 선택 합니다.

4. **새 항목 추가** 대화 상자에서 **SharePoint** 노드를 확장 한 다음 **2010** 항목을 선택 합니다.

5. SharePoint 템플릿 목록에서 **응용 프로그램 페이지**를 선택 합니다.

6. **이름** 상자에서 응용 프로그램 페이지의 이름을 지정한 다음 **추가** 단추를 선택 합니다.

     Visual Studio는 프로젝트에 여러 폴더와 파일을 추가 합니다. 이러한 파일에 대 한 자세한 내용은 [SharePoint 용 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)를 참조 하세요.

     Visual Web Developer 디자이너의 **소스** 뷰에 ASP.NET 페이지 파일이 표시 됩니다. **도구 상자** 에서 컨트롤을 추가 하 고 콘텐츠 자리 표시자에 배치 하 여 페이지를 디자인할 수 있습니다. 자세한 내용은 [소스 뷰, 웹 페이지 디자이너를](/previous-versions/aspnet/ms178154\(v\=vs.100\))참조 하세요.

7. 컨트롤 이벤트를 처리하려면 애플리케이션 페이지의 코드 파일에 코드를 추가합니다.

     ASP.NET 페이지 파일에 대 한 노드를 확장 하 고 프로젝트의 언어에 따라 확장명이 *.cs* 또는 *.vb* 인 경우 코드 파일이 표시 됩니다. 응용 프로그램 페이지를 만드는 방법에 대 한 종단 간 예제는 [연습: SharePoint 응용 프로그램 만들기 페이지](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [SharePoint에 대 한 응용 프로그램 페이지 만들기](../sharepoint/creating-application-pages-for-sharepoint.md)
- [연습: SharePoint 응용 프로그램 페이지 만들기](../sharepoint/walkthrough-creating-a-sharepoint-application-page.md)
