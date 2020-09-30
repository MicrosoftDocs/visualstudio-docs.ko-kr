---
title: Word 용 문서 수준 사용자 지정 프로그래밍 시작
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Word solutions in Visual Studio
- Word projects [Office development in Visual Studio], getting started
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: f4cf54dcdd08e7c44e8318973a3653dbe9c5ea1b
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585669"
---
# <a name="get-started-programming-document-level-customizations-for-word"></a>Word 용 문서 수준 사용자 지정 프로그래밍 시작
  Visual Studio를 사용 하 여 Microsoft Office Word에 대 한 문서 수준 사용자 지정을 만들기 시작 하는 경우 알아야 할 사항은 다음과 같습니다.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

## <a name="understand-how-document-level-customizations-for-word-work"></a>Word 작업의 문서 수준 사용자 지정 방법 이해
 만든 각 단어 사용자 지정은 단일 문서를 기반으로 합니다. 사용자 지정 사용을 시작 하기 위해 최종 사용자가 문서를 열거나 Word 서식 파일에서 문서를 만듭니다. 문서의 이벤트 (예: 커서를 특정 영역으로 이동 하거나 단추 및 메뉴 항목 클릭)는 어셈블리에서 이벤트 처리 메서드를 호출할 수 있습니다. 문서를 닫으면 사용자 지정에서 제공 하는 기능을 Word에서 더 이상 사용할 수 없습니다.

 자세한 내용은 [문서 수준 사용자 지정의 아키텍처](../vsto/architecture-of-document-level-customizations.md)를 참조 하세요.

## <a name="create-document-level-projects-for-word"></a>Word 용 문서 수준 프로젝트 만들기
 Word 용 문서 수준 사용자 지정을 만들려면 **새 프로젝트** 대화 상자에서 word 문서 또는 word 서식 파일 프로젝트 템플릿을 사용 합니다. 이러한 템플릿에는 필요한 어셈블리 참조 및 프로젝트 파일이 포함되어 있습니다.

 Word 용 문서 수준 프로젝트를 만드는 방법에 대 한 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요. 프로젝트 템플릿에 대 한 자세한 내용은 [Office 프로젝트 템플릿 개요](../vsto/office-project-templates-overview.md)를 참조 하세요.

## <a name="program-word-documents-by-using-host-items-host-controls"></a>호스트 항목 호스트 컨트롤을 사용 하 여 Word 문서 프로그램
 *호스트 항목* 및 *호스트 컨트롤* 은 문서 수준 사용자 지정을 위한 프로그래밍 모델을 제공 하는 클래스입니다.

 호스트 항목은 코드에 대 한 진입점을 제공 하며 호스트 컨트롤 및 Windows Forms 컨트롤의 컨테이너 역할을 할 수도 있습니다. Word 용 문서 수준 프로젝트에서 호스트 항목은 클래스로 표현 됩니다 `ThisDocument` .

 호스트 컨트롤은 콘텐츠 컨트롤, 책갈피 및 XML 노드와 같은 네이티브 Word 개체를 기반으로 합니다. 호스트 컨트롤은 네이티브 Word 개체와 유사한 기능을 제공 하지만 새 이벤트, 디자이너 지원 및 데이터 바인딩 기능도 있습니다. 이러한 개체는 프로젝트 코드 및 IntelliSense에 첫 번째 클래스 개체로 나타나므로 Word 개체 모델을 탐색 하지 않고도 코드에서 직접 특정 개체를 쉽게 참조할 수 있습니다.

 자세한 내용은 다음 항목을 참조하세요.

- [문서 수준 사용자 지정 프로그램](../vsto/programming-document-level-customizations.md)

- [확장 된 개체를 사용 하 여 Word 자동화](../vsto/automating-word-by-using-extended-objects.md)

- [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)

## <a name="customize-the-user-interface-of-word"></a>Word의 사용자 인터페이스 사용자 지정
 대부분의 Microsoft Office 솔루션은 Office 응용 프로그램의 UI (사용자 인터페이스)를 수정 하 여 사용자가 솔루션과 상호 작용할 수 있는 몇 가지 방법을 제공 합니다. 문서 수준 사용자 지정을 사용 하 여 Word의 UI를 수정할 수 있는 여러 가지 방법이 있습니다. 예를 들어 리본 메뉴에 컨트롤을 추가 하 고 작업 창을 표시할 수 있습니다. 자세한 내용은 [OFFICE UI 사용자 지정](../vsto/office-ui-customization.md)을 참조 하세요.

 Visual Studio에서 직접 프로젝트와 연결 된 문서를 열 수도 있습니다. Visual Studio에서 문서를 열면 Word 사용자 인터페이스를 사용 하 여 문서를 수정할 수 있습니다. 또한 문서를 디자인 화면으로 사용 하 여 컨트롤을 끌어 놓을 수 있습니다. 자세한 내용은 [Visual Studio 환경의 Office 프로젝트](../vsto/office-projects-in-the-visual-studio-environment.md)를 참조 하세요.

## <a name="bind-controls-to-data"></a>데이터에 컨트롤 바인딩
 콘텐츠 컨트롤 및 컨트롤은 <xref:Microsoft.Office.Tools.Word.Bookmark> **데이터 소스** 창에서 끌어올 수 있는 컨트롤 목록에 있습니다. 이러한 방식으로 콘텐츠 컨트롤 및 책갈피를 추가 하면 창을 사용 하 여 설정한 데이터 원본에 자동으로 바인딩됩니다. 코드를 작성 하지 않고도 데이터베이스, 서비스 및 비즈니스 개체의 데이터를 표시할 수 있습니다. 자세한 내용은 [Office 솔루션의 컨트롤에 데이터 바인딩](../vsto/binding-data-to-controls-in-office-solutions.md)을 참조 하세요.

## <a name="next-steps"></a>다음 단계
 Word 용 문서 수준 사용자 지정을 만드는 방법을 알아보려면 [연습: word 용 첫 문서 수준 사용자 지정 만들기](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)를 참조 하세요. 이 연습에서는 Visual Studio에서 Office 개발 도구를 소개 하 고 Word 문서 수준 사용자 지정을 위한 프로그래밍 모델을 소개 합니다.

 Word 프로젝트의 일반적인 작업 중 일부를 안내 하는 항목의 목록은 [Office 프로그래밍의 일반적인 작업](../vsto/common-tasks-in-office-programming.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [문서 수준 사용자 지정 프로그램](../vsto/programming-document-level-customizations.md)
- [Word 솔루션](../vsto/word-solutions.md)
- [연습: Word 용 첫 문서 수준 사용자 지정 만들기](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)
- [Word를 사용한 연습](../vsto/walkthroughs-using-word.md)
- [Word 개체 모델 개요](../vsto/word-object-model-overview.md)
- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)
