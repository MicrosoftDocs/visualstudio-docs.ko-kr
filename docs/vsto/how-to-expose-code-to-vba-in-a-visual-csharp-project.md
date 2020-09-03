---
title: '방법: c # 프로젝트에서 VBA로 코드 노출'
ms.custom: seodec18
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual C# [Office development in Visual Studio], exposing code to VBA
- VBA [Office development in Visual Studio], exposing code in document-level customizations
- document-level customizations [Office development in Visual Studio], exposing code
- exposing code to VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 21d7672d3c08012e75d73ee8bf4d9816b850eb2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544835"
---
# <a name="how-to-expose-code-to-vba-in-a-visual-c-project"></a>방법: Visual c # 프로젝트에서 VBA로 코드 노출
  두 가지 코드 형식이 서로 상호 작용 하도록 하려면 Visual c # 프로젝트의 코드를 VBA (Visual Basic for Applications) 코드에 노출할 수 있습니다.

 Visual c # 프로세스는 Visual Basic 프로세스와 다릅니다. 자세한 내용은 [방법: Visual Basic 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)을 참조 하세요.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="expose-code-in-a-visual-c-project"></a>Visual c # 프로젝트에서 코드 노출
 VBA 코드에서 Visual c # 프로젝트의 코드를 호출할 수 있도록 하려면 COM에 표시 되도록 코드를 수정 하 고 디자이너에서 **ReferenceAssemblyFromVbaProject** 속성을 **True** 로 설정 합니다.

 VBA에서 Visual c # 프로젝트의 메서드를 호출 하는 방법을 보여 주는 연습은 [연습: Visual c&#35; 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)을 참조 하세요.

### <a name="to-expose-code-in-a-visual-c-project-to-vba"></a>Visual c # 프로젝트의 코드를 VBA에 노출 하려면

1. 매크로를 지원 하 고 이미 VBA 코드를 포함 하는 Word 문서, Excel 통합 문서 또는 Excel 서식 파일을 기반으로 하는 문서 수준 프로젝트를 열거나 만듭니다.

    매크로를 지 원하는 문서 파일 형식에 대 한 자세한 내용은 [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)을 참조 하세요.

   > [!NOTE]
   > 이 기능은 Word 서식 파일 프로젝트에서 사용할 수 없습니다.

2. 사용자에 게 매크로를 설정 하 라는 메시지를 표시 하지 않고 문서의 VBA 코드를 실행할 수 있는지 확인 합니다. Word 또는 Excel의 보안 센터 설정에서 신뢰할 수 있는 위치 목록에 Office 프로젝트의 위치를 추가하여 VBA 코드를 실행하도록 신뢰할 수 있습니다.

3. VBA에 노출할 멤버를 프로젝트의 공용 클래스에 추가 하 고 새 멤버를 **public**으로 선언 합니다.

4. <xref:System.Runtime.InteropServices.ComVisibleAttribute>VBA에 노출 하는 클래스에 다음 및 특성을 적용 합니다 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> . 이러한 특성은 클래스가 COM에 표시되도록 하지만 클래스 인터페이스를 생성하지 않습니다.

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   [System.Runtime.InteropServices.ClassInterface(
       System.Runtime.InteropServices.ClassInterfaceType.None)]
   ```

5. VBA에 노출할 클래스의 인스턴스를 반환 하도록 프로젝트에서 호스트 항목 클래스의 **Getautomationobject** 메서드를 재정의 합니다.

   - 호스트 항목 클래스를 VBA에 노출 하는 경우이 클래스에 속하는 **Getautomationobject** 메서드를 재정의 하 고 클래스의 현재 인스턴스를 반환 합니다.

     ```csharp
     protected override object GetAutomationObject()
     {
         return this;
     }
     ```

   - 호스트 항목이 아닌 클래스를 VBA에 노출 하는 경우 프로젝트에 있는 모든 호스트 항목의 **Getautomationobject** 메서드를 재정의 하 고 비 호스트 항목 클래스의 인스턴스를 반환 합니다. 예를 들어 다음 코드에서는 라는 클래스를 VBA에 노출 하는 것으로 가정 합니다 `DocumentUtilities` .

     ```csharp
     protected override object GetAutomationObject()
     {
         return new DocumentUtilities();
     }
     ```

     호스트 항목에 대 한 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

6. VBA에 노출 하는 클래스에서 인터페이스를 추출 합니다. **인터페이스 추출** 대화 상자에서 인터페이스 선언에 포함 하려는 public 멤버를 선택 합니다. 자세한 내용은 [Extract interface 리팩터링](../ide/reference/extract-interface.md)을 참조 하세요.

7. **Public** 키워드를 인터페이스 선언에 추가 합니다.

8. 인터페이스에 다음 특성을 추가 하 여 인터페이스가 COM에 표시 되도록 합니다 <xref:System.Runtime.InteropServices.ComVisibleAttribute> .

   ```csharp
   [System.Runtime.InteropServices.ComVisible(true)]
   ```

9. 의 디자이너에서 문서 (Word의 경우) 또는 워크시트 (Excel의 경우)를 엽니다 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .

10. **속성** 창에서 **ReferenceAssemblyFromVbaProject** 속성을 선택하고 값을 **True**로 변경합니다.

    > [!NOTE]
    > 통합 문서나 문서에 VBA 코드가 이미 포함 되어 있지 않거나 문서의 VBA 코드를 실행 하도록 신뢰할 수 없는 경우 **ReferenceAssemblyFromVbaProject** 속성을 **True**로 설정 하면 오류 메시지가 표시 됩니다. 그 이유는 이러한 경우 Visual Studio에서 문서의 VBA 프로젝트를 수정할 수 없기 때문입니다.

11. 표시되는 메시지에서 **확인** 을 클릭합니다. 이 메시지는에서 프로젝트를 실행할 때 통합 문서나 문서에 VBA 코드를 추가 하는 경우 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 다음에 프로젝트를 빌드할 때 vba 코드가 손실 됨을 알려 줍니다. 프로젝트를 빌드할 때마다 빌드 출력 폴더의 문서를 덮어쓰므로이는입니다.

     이 시점에서 Visual Studio는 VBA 프로젝트가 어셈블리를 호출할 수 있도록 프로젝트를 구성 합니다. 또한 Visual Studio는 라는 메서드를 `GetManagedClass` VBA 프로젝트에 추가 합니다. Vba 프로젝트의 어디에서 나이 메서드를 호출 하 여 VBA에 노출 한 클래스에 액세스할 수 있습니다.

12. 프로젝트를 빌드합니다.

## <a name="see-also"></a>참조
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)
- [연습: Visual C&#35; 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [방법: Visual Basic 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
