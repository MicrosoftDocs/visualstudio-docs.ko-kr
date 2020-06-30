---
title: '방법: Visual Basic 프로젝트에서 VBA로 코드 노출'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- Visual Basic [Office development in Visual Studio], exposing code to VBA
- exposing code to VBA
- host items [Office development in Visual Studio], exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8aa29fca9905c9f1ed056949eec64ad967323462
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544848"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-basic-project"></a>방법: Visual Basic 프로젝트에서 VBA로 코드 노출
  [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]두 형식의 코드가 서로 상호 작용 하도록 하려면 프로젝트의 코드를 VBA (Visual Basic for Applications) 코드에 노출할 수 있습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Visual Basic 프로세스는 Visual c # 프로세스와 다릅니다. 자세한 내용은 [방법: Visual C&#35; 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)을 참조 하세요.

 호스트 항목 클래스의 코드에 대 한 프로세스는 다른 클래스의 코드에 대 한 프로세스와 다릅니다.

- [호스트 항목 클래스의 코드 노출](#HostItemCode)

- [호스트 항목 클래스에 없는 코드 노출](#NonHostItem)

## <a name="expose-code-in-a-host-item-class"></a><a name="HostItemCode"></a>호스트 항목 클래스의 코드 노출
 VBA 코드에서 호스트 항목 클래스의 Visual Basic 코드를 호출 하도록 하려면 호스트 항목의 **EnableVbaCallers** 속성을 **True**로 설정 합니다.

 호스트 항목 클래스의 메서드를 노출 한 다음 VBA에서 호출 하는 방법을 보여 주는 연습은 [연습: Visual Basic 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)을 참조 하세요. 호스트 항목에 대 한 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

#### <a name="to-expose-code-in-a-host-item-to-vba"></a>호스트 항목의 코드를 VBA에 노출 하려면

1. [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]매크로를 지원 하 고 이미 VBA 코드를 포함 하는 Word 문서, excel 통합 문서 또는 excel 서식 파일을 기반으로 하는 문서 수준 프로젝트를 열거나 만듭니다.

     매크로를 지 원하는 문서 파일 형식에 대 한 자세한 내용은 [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)을 참조 하세요.

    > [!NOTE]
    > 이 기능은 Word 서식 파일 프로젝트에서 사용할 수 없습니다.

2. 사용자에 게 매크로를 설정 하 라는 메시지를 표시 하지 않고 문서의 VBA 코드를 실행할 수 있는지 확인 합니다. Word 또는 Excel의 보안 센터 설정에서 신뢰할 수 있는 위치 목록에 Office 프로젝트의 위치를 추가하여 VBA 코드를 실행하도록 신뢰할 수 있습니다.

3. VBA에 노출할 속성, 메서드 또는 이벤트를 프로젝트의 호스트 항목 클래스 중 하나에 추가 하 고 새 멤버를 **Public**으로 선언 합니다. 클래스의 이름은 응용 프로그램에 따라 달라 집니다.

    - Word 프로젝트에서 호스트 항목 클래스의 이름은 `ThisDocument` 기본적으로입니다.

    - Excel 프로젝트에서 호스트 항목 클래스의 이름은 `ThisWorkbook` 기본적으로,, `Sheet1` `Sheet2` 및 `Sheet3` 입니다.

4. 호스트 항목의 **EnableVbaCallers** 속성을 **True**로 설정 합니다. 이 속성은 디자이너에서 호스트 항목을 열 때 **속성** 창에서 사용할 수 있습니다.

     이 속성을 설정 하면 Visual Studio에서 자동으로 **ReferenceAssemblyFromVbaProject** 속성을 **True**로 설정 합니다.

    > [!NOTE]
    > 통합 문서나 문서에 VBA 코드가 이미 포함 되어 있지 않거나 문서의 VBA 코드를 실행 하도록 신뢰할 수 없는 경우 **EnableVbaCallers** 속성을 **True**로 설정 하면 오류 메시지가 표시 됩니다. 그 이유는 이러한 경우 Visual Studio에서 문서의 VBA 프로젝트를 수정할 수 없기 때문입니다.

5. 표시되는 메시지에서 **확인** 을 클릭합니다. 이 메시지는에서 프로젝트를 실행 하는 동안 통합 문서나 문서에 VBA 코드를 추가 하는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음에 프로젝트를 빌드할 때 vba 코드가 손실 됨을 알려 줍니다. 프로젝트를 빌드할 때마다 빌드 출력 폴더의 문서를 덮어쓰므로이는입니다.

     이 시점에서 Visual Studio는 VBA 프로젝트가 어셈블리를 호출할 수 있도록 프로젝트를 구성 합니다. 또한 Visual Studio는 `CallVSTOAssembly` `ThisDocument` `ThisWorkbook` `Sheet1` `Sheet2` VBA 프로젝트의,,, 또는 `Sheet3` 모듈에 라는 속성을 추가 합니다. 이 속성을 사용 하 여 VBA에 노출 한 클래스의 공용 멤버에 액세스할 수 있습니다.

6. 프로젝트를 빌드합니다.

## <a name="expose-code-that-is-not-in-a-host-item-class"></a><a name="NonHostItem"></a>호스트 항목 클래스에 없는 코드 노출
 VBA 코드에서 호스트 항목 클래스에 없는 Visual Basic 코드를 호출 하도록 하려면 VBA에 표시 되도록 코드를 수정 합니다.

### <a name="to-expose-code-that-is-not-in-a-host-item-class-to-vba"></a>호스트 항목 클래스에 없는 코드를 VBA에 노출 하려면

1. [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]매크로를 지원 하 고 이미 VBA 코드를 포함 하는 Word 문서, excel 통합 문서 또는 excel 서식 파일을 기반으로 하는 문서 수준 프로젝트를 열거나 만듭니다.

     매크로를 지 원하는 문서 파일 형식에 대 한 자세한 내용은 [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)을 참조 하세요.

    > [!NOTE]
    > 이 기능은 Word 서식 파일 프로젝트에서 사용할 수 없습니다.

2. 사용자에 게 매크로를 설정 하 라는 메시지를 표시 하지 않고 문서의 VBA 코드를 실행할 수 있는지 확인 합니다. Word 또는 Excel의 보안 센터 설정에서 신뢰할 수 있는 위치 목록에 Office 프로젝트의 위치를 추가하여 VBA 코드를 실행하도록 신뢰할 수 있습니다.

3. VBA에 노출할 멤버를 프로젝트의 공용 클래스에 추가 하 고 새 멤버를 **public**으로 선언 합니다.

4. <xref:System.Runtime.InteropServices.ComVisibleAttribute>VBA에 노출 하는 클래스에 다음 및 특성을 적용 합니다 <xref:Microsoft.VisualBasic.ComClassAttribute> . 이러한 특성은 VBA에 클래스를 표시 하도록 합니다.

    ```vb
    <Microsoft.VisualBasic.ComClass()> _
    <System.Runtime.InteropServices.ComVisibleAttribute(True)> _
    ```

5. VBA에 노출할 클래스의 인스턴스를 반환하도록 프로젝트에서 호스트 항목 클래스의 **GetAutomationObject** 메서드를 재정의합니다. 다음 코드 예제에서는 라는 클래스를 VBA에 노출 하는 것으로 가정 합니다 `DocumentUtilities` .

    ```vb
    Protected Overrides Function GetAutomationObject() As Object
        Return New DocumentUtilities()
    End Function
    ```

6. 에서 문서 (Word의 경우) 또는 워크시트 (Excel의 경우) 디자이너를 엽니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

7. **속성** 창에서 **ReferenceAssemblyFromVbaProject** 속성을 선택하고 값을 **True**로 변경합니다.

    > [!NOTE]
    > 통합 문서나 문서에 VBA 코드가 이미 포함 되어 있지 않거나 문서의 VBA 코드를 실행 하도록 신뢰할 수 없는 경우 **ReferenceAssemblyFromVbaProject** 속성을 **True**로 설정 하면 오류 메시지가 표시 됩니다. 그 이유는 이러한 경우 Visual Studio에서 문서의 VBA 프로젝트를 수정할 수 없기 때문입니다.

8. 표시되는 메시지에서 **확인** 을 클릭합니다. 이 메시지는에서 프로젝트를 실행 하는 동안 통합 문서나 문서에 VBA 코드를 추가 하는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음에 프로젝트를 빌드할 때 vba 코드가 손실 됨을 알려 줍니다. 프로젝트를 빌드할 때마다 빌드 출력 폴더의 문서를 덮어쓰므로이는입니다.

     이 시점에서 Visual Studio는 VBA 프로젝트가 어셈블리를 호출할 수 있도록 프로젝트를 구성 합니다. 또한 Visual Studio는 라는 메서드를 `GetManagedClass` VBA 프로젝트에 추가 합니다. Vba 프로젝트의 어디에서 나이 메서드를 호출 하 여 VBA에 노출 한 클래스에 액세스할 수 있습니다.

9. 프로젝트를 빌드합니다.

## <a name="see-also"></a>참고 항목
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)
- [연습: Visual Basic 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [방법: Visual C&#35; 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
