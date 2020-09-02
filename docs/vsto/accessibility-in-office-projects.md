---
title: Office 프로젝트의 내게 필요한 옵션
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8bd74f4d61c74a4dc348f7a615e103b283a15fc0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "73189628"
---
# <a name="accessibility-in-office-projects"></a>Office 프로젝트의 내게 필요한 옵션

Microsoft Visual Studio 및 Microsoft Office에는 표준 접근성 요구 사항을 충족 하는 사용자 지정 솔루션을 빌드할 수 있는 많은 내게 필요한 옵션 기능이 포함 되어 있습니다. Microsoft는 웹에서 내게 필요한 옵션에 대 한 지침을 게시 합니다. 자세한 내용은 [내게 필요한 옵션 웹 사이트](https://www.microsoft.com/accessibility/)를 참조 하세요.

대부분의 경우 Visual Studio의 Office 프로젝트는 접근성 표준을 충족 하거나 솔루션에 액세스할 수 있도록 설정할 수 있는 속성을 노출 합니다. 그러나 액세스 가능성이 제한 된 일부 기능이 있습니다.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>디자인 타임에 접근성

### <a name="use-shortcut-keys-in-document-level-projects"></a>문서 수준 프로젝트에서 바로 가기 키 사용
 Visual Studio에서 Microsoft Office Word 문서 또는 Microsoft Office Excel 통합 문서가 열려 있는 경우 한 번에 한 응용 프로그램만 바로 가기 키 명령을 받습니다. 기본적으로 Visual Studio는 모든 바로 가기 키 명령을 받지만 **옵션** 대화 상자의 **키보드 설정** 페이지에서 **동적 키보드 구성표** 를 선택 하 여 문서에 포커스가 있을 때 Word 또는 Excel에서이를 받도록 할 수 있습니다. 자세한 내용은 [Microsoft Office Word 키보드, Microsoft Office 키보드 설정, 옵션 대화 상자](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) 및 [Microsoft Office Excel 키보드 Microsoft Office 키보드 설정, 옵션 대화 상자](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)를 참조 하세요.

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>문서 수준 프로젝트의 리본 메뉴에 대 한 바로 가기 키 표시
 Visual Studio에서 Word 문서 또는 Excel 통합 문서가 열려 있는 경우 **Alt** 키를 눌러 리본의 탭과 컨트롤에 대 한 바로 가기 키를 볼 수 없습니다. 디자이너에서 문서 또는 통합 문서가 열려 있는 동안 바로 가기 키를 보려면 다음 단계를 수행 합니다.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>디자이너에서 리본 탭 및 컨트롤에 대 한 바로 가기 키를 보려면

1. Visual Studio의 **도구** 메뉴에서 **옵션**을 클릭 합니다.

2. **Office 도구** 노드를 확장 하 고 **Microsoft Office Excel 키보드** 또는 **Microsoft Office Word 키보드**를 적절히 선택 합니다.

3. **동적 키보드 구성표**를 선택 합니다.

     변경 내용을 적용 하려면 Visual Studio를 다시 시작 해야 한다는 내용의 메시지가 표시 됩니다.

4. **확인**을 클릭합니다.

5. Visual Studio를 다시 시작 하 고 프로젝트를 다시 엽니다.

6. 프로젝트에 대 한 문서 또는 통합 문서 디자이너를 엽니다.

7. **F6** 키를 눌러 리본 메뉴에 대 한 바로 가기 키를 표시 합니다.

## <a name="accessibility-at-run-time"></a>런타임에 접근성

### <a name="windows-forms-controls-on-office-documents"></a>Office 문서의 Windows Forms 컨트롤
 Windows Forms 컨트롤은 화면 판독기와 같은 내게 필요한 옵션 지원 기능에 컨트롤에 대 한 정보를 제공 하는 내게 필요한 옵션 속성을 노출 합니다. 문서 수준 사용자 지정에서 컨트롤이 Office 문서에 있는 경우 이러한 내게 필요한 옵션 속성을 활용할 수 있습니다. 자세한 내용은 [Windows Form의 컨트롤에 내게 필요한 옵션 정보 제공](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form)을 참조 하세요.

 그러나 Windows Forms 컨트롤이 Excel 통합 문서 또는 Word 문서에서 호스팅될 때 런타임에는 다음과 같은 몇 가지 접근성 제한이 있습니다.

- 한 컨트롤에서 다른 컨트롤로 tab 키를 누르면 됩니다.

- 문서의 확대/축소 설정을 100% 이외의 값으로 변경 하면 문서의 컨트롤을 사용할 수 없습니다.

  문서에서 Windows Forms 컨트롤의 제한에 대 한 자세한 내용은 [Office 문서에서 Windows Forms 컨트롤의 제한 사항](../vsto/limitations-of-windows-forms-controls-on-office-documents.md)을 참조 하세요.

### <a name="actions-panes-and-custom-task-panes"></a>작업 창 및 사용자 지정 작업창
 작업 창 또는 사용자 지정 작업창에 포커스가 있는 경우 Windows Forms 응용 프로그램에서 컨트롤에 액세스 하는 것과 동일한 방식으로 컨트롤에 액세스 합니다. 작업 창과 문서 사이에서 커서를 이동 하려면 **F6**키를 누를 수 있습니다.

 작업 창 및 사용자 지정 작업창에 대 한 자세한 내용은 [작업 창 개요](../vsto/actions-pane-overview.md) 및 [사용자 지정 작업창](../vsto/custom-task-panes.md)을 참조 하세요.

### <a name="display-modes"></a>디스플레이 모드

Visual Studio에는 디스플레이 모드와 관련 된 다음과 같은 제한 사항이 있습니다.

- 문서의 확대/축소 설정을 100% 이외의 값으로 변경 하면 Word 문서 또는 Excel 워크시트의 컨트롤이 사용 하지 않도록 설정 됩니다.

- 사용자가 **고대비 사용**을 위해 컴퓨터의 접근성 옵션을 변경 하면 **새 프로젝트** 대화 상자에 컨트롤이 올바르게 표시 되지 않습니다.

돋보기를 사용 하 여 이러한 제한을 극복할 수 있습니다. 돋보기는 화면의 확대 된 부분을 표시 하는 별도의 창을 만드는 창에 표시 되는 유틸리티입니다.

## <a name="see-also"></a>추가 정보

- [Office 솔루션 개발](../vsto/developing-office-solutions.md)
- [Office 문서의 컨트롤](../vsto/controls-on-office-documents.md)
- [장애가 있는 사용자를 위한 내게 필요한 옵션](../ide/reference/accessibility-features-of-visual-studio.md)
- [Visual Studio의 내게 필요한 옵션 기능](../ide/reference/accessibility-features-of-visual-studio.md)