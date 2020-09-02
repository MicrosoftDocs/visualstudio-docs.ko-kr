---
title: Outlook 솔루션
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Outlook
- Office projects [Office development in Visual Studio], Outlook
- Office solutions [Office development in Visual Studio], Outlook
- templates [Office development in Visual Studio], Outlook
- projects [Office development in Visual Studio], Outlook
- Outlook [Office development in Visual Studio]
- e-mail [Office development in Visual Studio], Outlook solutions
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21e6478bb0f02383066a2c63dad1bdaf980a0b5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985681"
---
# <a name="outlook-solutions"></a>Outlook 솔루션
  Visual Studio에서는 Microsoft Office Outlook용 VSTO 추가 기능을 만드는 데 사용할 수 있는 프로젝트 템플릿을 제공합니다. VSTO 추가 기능을 사용하여 Outlook을 자동화하거나, Outlook 기능을 확장하거나, Outlook UI(사용자 인터페이스)를 사용자 지정할 수 있습니다. VSTO 추가 기능에 대한 자세한 내용은 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)를 참조하세요.

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="create-an-outlook-vsto-add-in-project"></a>Outlook VSTO 추가 기능 프로젝트 만들기
 **새 프로젝트** 대화 상자에서 **Outlook 추가 기능** 프로젝트 템플릿을 사용하여 Outlook 프로젝트를 만듭니다. 이 템플릿에는 필요한 어셈블리 참조 및 프로젝트 파일이 포함되어 있습니다.

 VSTO 추가 기능 프로젝트를 만드는 방법에 대 한 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요. 프로젝트 템플릿에 대 한 자세한 내용은 [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)를 참조 하세요.

## <a name="outlook-vsto-add-in-programming-model"></a>Outlook VSTO 추가 기능 프로그래밍 모델
 Outlook VSTO 추가 기능 프로젝트를 만드는 경우 Visual Studio는 솔루션의 기초가 되는 `ThisAddIn`인이라는 클래스를 생성합니다. 이 클래스는 코드를 작성하기 위한 시작점을 제공하고 VSTO 추가 기능에 Outlook의 개체 모델도 노출합니다.

 `ThisAddIn`클래스 및 Vsto 추가 기능에서 사용할 수 있는 기타 기능에 대 한 자세한 내용은 [vsto 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

## <a name="automate-outlook-by-using-the-outlook-object-model"></a>Outlook 개체 모델을 사용 하 여 Outlook 자동화
 Outlook 개체 모델은 Outlook 자동화에 사용할 수 있는 다양한 형식을 노출합니다. 이러한 형식을 사용하여 일반적인 작업을 수행하는 코드를 작성할 수 있습니다.

- 프로그래밍 방식으로 메일 메시지를 만들고 보냅니다.

- 새 모임 요청을 보냅니다.

- Outlook 폴더에서 항목을 검색합니다.

  자세한 내용은 [Outlook 개체 모델 개요](../vsto/outlook-object-model-overview.md)를 참조 하세요.

## <a name="customize-the-user-interface-of-an-outlook-application"></a>Outlook 응용 프로그램의 사용자 인터페이스 사용자 지정

|Task|참조 항목|
|----------|--------------------------|
|Outlook 검사기의 리본 메뉴에 사용자 지정 탭을 추가합니다.|[리본 개요](../vsto/ribbon-overview.md)|
|Outlook 검사기의 기본 제공 탭에 사용자 지정 그룹을 추가합니다.|[방법: 기본 제공 탭 사용자 지정](../vsto/how-to-customize-a-built-in-tab.md)|
|Outlook 검사기에 나타나는 사용자 지정 작업창을 추가합니다.|[사용자 지정 작업창](../vsto/custom-task-panes.md).|
|기존 Outlook 양식을 확장하거나 바꾸는 양식 영역을 추가합니다.|[Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)|

 Outlook 및 기타 Microsoft Office 응용 프로그램의 UI를 사용자 지정 하는 방법에 대 한 자세한 내용은 [OFFICE ui 사용자 지정](../vsto/office-ui-customization.md)을 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[Outlook 개체 모델 개요](../vsto/outlook-object-model-overview.md)|Outlook 개체 모델에서 제공하는 개체에 대해 설명합니다.|
|[Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)|양식 영역을 쉽게 디자인, 개발 및 디버그할 수 있도록 Visual Studio에서 제공하는 도구에 대해 설명합니다.|
|[연습: Outlook 용 첫 VSTO 추가 기능 만들기](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)|Microsoft Office Outlook용 VSTO 추가 기능을 만드는 방법을 보여 줍니다.|
|[Office 개발의 Outlook 2010](/previous-versions/office/developer/office-2010/ff458122(v=office.14))|Visual Studio를 사용한 Office 개발에 국한되지 않고 Outlook 솔루션을 개발하는 방법에 대한 문서와 참조 설명서를 찾을 수 있는 MSDN 라이브러리 영역입니다.|
