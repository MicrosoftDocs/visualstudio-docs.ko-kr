---
title: VSTO 추가 기능 프로그래밍 시작
description: VSTO 추가 기능을 사용하여 Microsoft Office 애플리케이션을 자동화하고, 애플리케이션의 기능을 확장하고, 애플리케이션의 사용자 인터페이스를 사용자 지정하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 04/28/2021
ms.topic: conceptual
f1_keywords:
- VST.ProjectItem.Outlook
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], getting started
- add-ins [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 1757dd6042536b6a042e67a8b3dcd9b12a2ea758
ms.sourcegitcommit: 9cb0097c33755a3e5cbadde3b0a6e9e76cee727d
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 05/13/2021
ms.locfileid: "109848294"
---
# <a name="get-started-programming-vsto-add-ins"></a>VSTO 추가 기능 프로그래밍 시작
> [!IMPORTANT]
> VSTO는 [.NET Framework](https://docs.microsoft.com/dotnet/framework/get-started/overview)를 기반으로 합니다. COM 추가 기능도 .NET Framework 작성할 수 있습니다. Office 추가 기능 은 최신 버전의 [.NET인 .NET Core 및 .NET 5+로](https://docs.microsoft.com/dotnet/core/dotnet-five)만들 수 없습니다. .NET Core/.NET 5 이상은 동일한 프로세스에서 .NET Framework 함께 작동할 수 없고 추가 기능 로드 오류가 발생할 수 있기 때문입니다. 계속해서 .NET Framework 사용하여 Office용 VSTO 및 COM 추가 기능 작성을 진행할 수 있습니다. Microsoft는 .NET Core 또는 .NET 5+를 사용하도록 VSTO 또는 COM 추가 기능 플랫폼을 업데이트하지 않습니다. ASP.NET Core를 포함하여 .NET Core 및 .NET 5+를 활용하여 Office 웹 추가 기능 의 서버 쪽을 만들 수 [있습니다.](https://docs.microsoft.com/office/dev/add-ins/overview/office-add-ins)

  VSTO 추가 기능을 사용하여 Microsoft Office 애플리케이션을 자동화하고 애플리케이션의 기능을 확장할 수 있으며 애플리케이션의 UI(사용자 인터페이스)를 사용자 지정할 수 있습니다. VSTO 추가 기능과 Visual Studio 사용하여 만들 수 있는 다른 유형의 Office 솔루션에 대한 자세한 내용은 VSTO&#41;[&#40;Office 솔루션 개발 개요를 ](../vsto/office-solutions-development-overview-vsto.md)참조하세요.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

## <a name="create-vsto-add-in-projects"></a>VSTO 추가 기능 프로젝트 만들기
 새 프로젝트 대화 상자의 VSTO 추가 기능 프로젝트 템플릿 중 하나를 사용하여 VSTO 추가 기능 **프로젝트를** 만듭니다. 이러한 템플릿에는 필요한 어셈블리 참조 및 프로젝트 파일이 포함되어 있습니다. Visual Studio에서는 대부분의 Office 애플리케이션용 VSTO 추가 기능 프로젝트 템플릿을 제공합니다.

 VSTO 추가 기능 프로젝트를 만드는 방법에 대한 자세한 내용은 [방법: Visual Studio Office 프로젝트 만들기를](../vsto/how-to-create-office-projects-in-visual-studio.md)참조하세요. 프로젝트 템플릿에 대한 자세한 내용은 [Office 프로젝트 템플릿 개요를 참조하세요.](../vsto/office-project-templates-overview.md)

## <a name="develop-vsto-add-in-projects"></a>VSTO 추가 기능 프로젝트 개발
 VSTO 추가 기능 프로젝트를 만들 때 Visual Studio *ThisAddIn.vb(의* [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] ) 또는 *ThisAddIn.cs(C#의)* 코드 파일을 자동으로 만듭니다. 이 파일에는 `ThisAddIn` VSTO 추가 기능의 기초를 제공하는 클래스가 포함되어 있습니다. 이 클래스의 멤버를 사용하여 VSTO 추가 기능이 로드되거나 언로드될 때 코드를 실행하고, 호스트 애플리케이션의 개체 모델에 액세스하고, 애플리케이션의 기능을 확장할 수 있습니다. 자세한 내용은 [프로그램 VSTO 추가 기능 를 참조하세요.](../vsto/programming-vsto-add-ins.md)

## <a name="automate-applications-by-using-the-object-models"></a>개체 모델을 사용하여 애플리케이션 자동화
 Microsoft Office 애플리케이션의 개체 모델은 VSTO 추가 기능에서 프로그래밍의 대상이 될 수 있는 많은 형식을 노출합니다. 이러한 형식을 사용하여 애플리케이션을 자동화할 수 있습니다. 예를 들어 프로그래밍 방식으로 Outlook에서 메일 메시지를 만들고 보내거나, 문서를 열고 Word에서 콘텐츠를 추가할 수 있습니다. 코드에서 호스트 응용 프로그램의 개체 모델에 액세스 하는 방법에 대 한 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

 특정 Microsoft Office 애플리케이션의 개체 모델에 대한 자세한 내용은 다음 항목을 참조하세요.

- [Excel 개체 모델 개요](../vsto/excel-object-model-overview.md)

- [Word 개체 모델 개요](../vsto/word-object-model-overview.md)

- [Outlook 개체 모델 개요](../vsto/outlook-object-model-overview.md)

- [InfoPath 솔루션](../vsto/infopath-solutions.md)

- [PowerPoint 솔루션](../vsto/powerpoint-solutions.md)

- [프로젝트 솔루션](../vsto/project-solutions.md)

- [Visio 개체 모델 개요](../vsto/visio-object-model-overview.md)

## <a name="customize-the-user-interface-of-applications"></a>응용 프로그램의 사용자 인터페이스 사용자 지정
 VSTO 추가 기능을 사용 하 여 호스트 응용 프로그램의 UI를 사용자 지정할 수 있는 여러 가지 방법이 있습니다.

- Excel과 Word의 경우 문서에 관리되는 컨트롤을 추가할 수 있습니다. 자세한 내용은 [런타임에 VSTO 추가 기능에서 Word 문서 및 Excel 통합 문서 확장](../vsto/extending-word-documents-and-excel-workbooks-in-vsto-add-ins-at-run-time.md)을 참조 하세요.

- 애플리케이션이 지원하는 경우 리본을 사용자 지정할 수 있습니다. 자세한 내용은 [리본 개요](../vsto/ribbon-overview.md)를 참조 하세요.

- 애플리케이션이 지원하는 경우 사용자 지정 작업창을 만들 수 있습니다. 자세한 내용은 [사용자 지정 작업 창](../vsto/custom-task-panes.md)을 참조 하세요.

- Outlook의 경우 사용자 지정 양식 영역을 만들 수 있습니다. 자세한 내용은 [Outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

- 모든 Microsoft Office 애플리케이션의 경우 VSTO 추가 기능에서 Windows Forms를 표시할 수 있습니다.

  Microsoft Office 응용 프로그램의 UI를 사용자 지정 하는 방법에 대 한 자세한 내용은 [OFFICE ui 사용자 지정](../vsto/office-ui-customization.md)을 참조 하세요.

## <a name="next-steps"></a>다음 단계
 VSTO 추가 기능을 만드는 방법을 알아보려면 다음 연습을 참조하세요.

- [연습: Excel 용 첫 VSTO 추가 기능 만들기](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)

- [연습: Outlook 용 첫 VSTO Add-In 만들기](../vsto/walkthrough-creating-your-first-vsto-add-in-for-outlook.md)

- [연습: PowerPoint 용 첫 VSTO 추가 기능 만들기](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)

- [연습: Project 용 첫 VSTO 추가 기능 만들기](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)

- [연습: Word 용 첫 VSTO 추가 기능 만들기](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)

  이러한 연습에서는 Visual Studio의 Office 개발 도구와 VSTO 추가 기능의 프로그래밍 모델을 소개합니다.

  Office 프로젝트의 일반적인 작업 중 일부를 안내하는 항목 목록은 Office [프로그래밍의 일반 작업을 참조하세요.](../vsto/common-tasks-in-office-programming.md)

## <a name="see-also"></a>추가 정보
- [방법: Visual Studio Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Visual Studio&#41;Office 개발 &#40;시작 ](../vsto/getting-started-office-development-in-visual-studio.md)
- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [프로그램 VSTO 추가 기능](../vsto/programming-vsto-add-ins.md)
