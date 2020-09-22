---
title: '연습: Visual c # 프로젝트에서 VBA의 코드 호출'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Excel [Office development in Visual Studio], calling code from VBA
- Word [Office development in Visual Studio], calling code from VBA
- Visual C# [Office development in Visual Studio], calling code from VBA
- workbooks [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46f88b47e135331e5f1dc010aa4a73abed520f51
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841734"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-c-project"></a>연습: Visual c # 프로젝트에서 VBA의 코드 호출
  이 연습에서는 통합 문서의 VBA(Visual Basic for Applications) 코드에서 Microsoft Office Excel에 대한 문서 수준 사용자 지정의 메서드를 호출하는 방법을 보여 줍니다. 이 절차에는 세 가지 기본 단계( `Sheet1` 호스트 항목 클래스에 메서드 추가, 통합 문서의 VBA 코드에 메서드 노출, 통합 문서의 VBA 코드에서 메서드 호출)가 포함됩니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 이 연습에서는 Excel을 사용하지만 Word용 문서 수준 프로젝트에도 연습에서 설명하는 개념을 적용할 수 있습니다.

 이 연습에서는 다음 작업을 수행합니다.

- VBA 코드를 포함하는 통합 문서 만들기

- Excel의 보안 센터를 사용하여 통합 문서 위치 신뢰

- `Sheet1` 호스트 항목 클래스에 메서드 추가

- `Sheet1` 호스트 항목 클래스에 대한 인터페이스 추출

- VBA 코드에 메서드 노출

- VBA 코드에서 메서드 호출

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Excel

## <a name="create-a-workbook-that-contains-vba-code"></a>VBA 코드를 포함 하는 통합 문서 만들기
 첫 번째 단계는 간단한 VBA 매크로를 포함하는 매크로 사용 통합 문서를 만드는 것입니다. 사용자 지정의 코드를 VBA에 노출하려면 통합 문서에 VBA 코드가 이미 포함되어 있어야 합니다. 그렇지 않으면 Visual Studio가 VBA 코드에서 사용자 지정 어셈블리를 호출할 수 있도록 VBA 프로젝트를 수정할 수 없습니다.

 사용하려는 VBA 코드를 포함하는 통합 문서가 이미 있는 경우 이 단계를 건너뛸 수 있습니다.

### <a name="to-create-a-workbook-that-contains-vba-code"></a>VBA 코드를 포함하는 통합 문서를 만들려면

1. Excel을 시작합니다.

2. 활성 문서를 **Excel 매크로 사용 통합 문서 ( \* .xlsm)** 와 함께 통합 문서 이름 **vba**로 저장 합니다. 통합 문서를 바탕 화면과 같은 편리한 위치에 저장합니다.

3. 리본에서 **개발자** 탭을 클릭합니다.

    > [!NOTE]
    > **개발자** 탭이 표시되지 않는 경우 먼저 개발자 탭을 표시해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발자 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)를 참조 하세요.

4. **코드** 그룹에서 **Visual Basic**을 클릭합니다.

     Visual Basic Editor가 열립니다.

5. **프로젝트** 창에서 **ThisWorkbook**을 두 번 클릭합니다.

     `ThisWorkbook` 개체의 코드 파일이 열립니다.

6. 다음 VBA 코드를 코드 파일에 추가합니다. 이 코드는 아무 작업도 수행하지 않는 간단한 함수를 정의합니다. 이 함수의 유일한 목적은 VBA 프로젝트가 통합 문서에 있는지 확인하는 것입니다. 이 작업은 이 연습의 이후 단계에 필요합니다.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. 문서를 저장하고 Excel을 종료합니다.

## <a name="create-the-project"></a>프로젝트 만들기
 이제 이전에 만든 매크로 사용 통합 문서를 사용하는 Excel용 문서 수준 프로젝트를 만들 수 있습니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

3. 템플릿 창에서 **Visual C#** 을 확장한 다음 **Office/SharePoint**를 확장합니다.

4. **Office 추가 기능** 노드를 선택합니다.

5. 프로젝트 템플릿 목록에서 **Excel 2010 통합 문서** 또는 **Excel 2013 통합 문서** 프로젝트를 선택합니다.

6. **이름** 상자에 **CallingCodeFromVBA**를 입력합니다.

7. **확인**을 클릭합니다.

     **Visual Studio Tools for Office 프로젝트 마법사** 가 열립니다.

8. **기존 문서 복사**를 선택하고 **기존 문서의 전체 경로** 상자에서 이전에 만든 **WorkbookWithVBA** 통합 문서의 위치를 지정합니다. 사용자 고유의 매크로 사용 통합 문서를 사용하는 경우 대신 이 통합 문서의 위치를 지정합니다.

9. **마침**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 의 디자이너에 **WorkbookWithVBA** 통합 문서가 열리고 **CallingCodeFromVBA** 프로젝트가 **솔루션 탐색기**에 추가됩니다.

## <a name="trust-the-location-of-the-workbook"></a>통합 문서의 위치를 신뢰 합니다.
 통합 문서의 VBA 코드에 솔루션의 코드를 노출하려면 먼저 실행할 통합 문서의 VBA를 신뢰해야 합니다. 이 작업을 수행하는 데는 몇 가지 방법이 있습니다. 이 연습에서는 Excel의 **보안 센터** 에서 통합 문서의 위치를 신뢰하여 이 작업을 수행합니다.

### <a name="to-trust-the-location-of-the-workbook"></a>통합 문서의 위치를 신뢰하려면

1. Excel을 시작합니다.

2. **파일** 탭을 클릭합니다.

3. **Excel 옵션** 단추를 클릭합니다.

4. 범주 창에서 **보안 센터**를 클릭합니다.

5. 세부 정보 창에서 **보안 센터 설정**을 클릭합니다.

6. 범주 창에서 **신뢰할 수 있는 위치**를 클릭합니다.

7. 세부 정보 창에서 **새 위치 추가**를 클릭합니다.

8. **Microsoft Office 신뢰할 수 있는 위치** 대화 상자에서 **CallingCodeFromVBA** 프로젝트가 들어 있는 폴더를 찾습니다.

9. **이 위치의 하위 폴더도 신뢰할 수 있음**을 선택합니다.

10. **Microsoft Office 신뢰할 수 있는 위치** 대화 상자에서 **확인**을 클릭합니다.

11. **보안 센터** 대화 상자에서 **확인**을 클릭합니다.

12. **Excel 옵션** 대화 상자에서 **확인**을 클릭합니다.

13. **Excel**을 종료합니다.

## <a name="add-a-method-to-the-sheet1-class"></a>Sheet1 클래스에 메서드 추가
 이제 VBA 프로젝트가 설정되었으므로 VBA 코드에서 호출할 수 있는 `Sheet1` 호스트 항목 클래스에 공용 메서드를 추가합니다.

### <a name="to-add-a-method-to-the-sheet1-class"></a>Sheet1 클래스에 메서드를 추가하려면

1. **솔루션 탐색기**에서 **Sheet1.cs**를 마우스 오른쪽 단추로 클릭한 다음 **코드 보기**를 클릭합니다.

     **Sheet1.cs** 파일이 코드 편집기에서 열립니다.

2. `Sheet1` 클래스에 다음 코드를 추가합니다. `CreateVstoNamedRange` 메서드는 지정된 범위에 새로운 <xref:Microsoft.Office.Tools.Excel.NamedRange> 개체를 만듭니다. 이 메서드는 <xref:Microsoft.Office.Tools.Excel.NamedRange.Selected> 의 <xref:Microsoft.Office.Tools.Excel.NamedRange>이벤트에 대한 이벤트 처리기도 만듭니다. 이 연습의 뒷부분에서는 문서의 VBA 코드에서 `CreateVstoNamedRange` 메서드를 호출합니다.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#2](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#2)]

3. `Sheet1` 클래스에 다음 메서드를 추가합니다. 이 메서드는 <xref:Microsoft.Office.Tools.Excel.Worksheet.GetAutomationObject%2A> 메서드를 재정의하여 `Sheet1` 클래스의 현재 인스턴스를 반환합니다.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#3](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#3)]

4. `Sheet1` 클래스 선언의 첫째 줄 앞에 다음 특성을 적용합니다. 이러한 특성은 클래스가 COM에 표시되도록 하지만 클래스 인터페이스를 생성하지 않습니다.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#1](../vsto/codesnippet/CSharp/CallingCodeFromVBA/Sheet1.cs#1)]

## <a name="extract-an-interface-for-the-sheet1-class"></a>Sheet1 클래스에 대 한 인터페이스 추출
 `CreateVstoNamedRange` 메서드를 VBA 코드에 노출하려면 먼저 이 메서드를 정의하는 공용 인터페이스를 만든 후 이 인터페이스를 COM에 노출해야 합니다.

### <a name="to-extract-an-interface-for-the-sheet1-class"></a>Sheet1 클래스에 대한 인터페이스를 추출하려면

1. **Sheet1.cs** 코드 파일에서 `Sheet1` 클래스의 아무 곳이나 클릭합니다.

2. **리팩터링** 메뉴에서 **인터페이스 추출**을 클릭합니다.

3. **인터페이스 추출** 대화 상자의 **인터페이스를 구성할 공용 멤버 선택** 상자에서 `CreateVstoNamedRange` 메서드에 대한 항목을 클릭합니다.

4. **확인**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 에서 `ISheet1`이라는 새 인터페이스를 생성하고, `Sheet1` 인터페이스를 구현하도록 `ISheet1` 클래스의 정의를 수정합니다. 또한[!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 의 코드 편집기에서 **ISheet1.cs** 파일이 열립니다.

5. **ISheet1.cs** 파일에서 `ISheet1` 인터페이스 선언을 다음 코드로 바꿉니다. 이 코드는 `ISheet1` 인터페이스를 공용으로 설정하고 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 특성을 적용하여 인터페이스가 COM에 표시되도록 합니다.

     [!code-csharp[Trin_CallingCSCustomizationFromVBA#4](../vsto/codesnippet/CSharp/CallingCodeFromVBA/ISheet1.cs#4)]

6. 프로젝트를 빌드합니다.

## <a name="expose-the-method-to-vba-code"></a>VBA 코드에 메서드 노출
 통합 문서의 VBA 코드에 `CreateVstoNamedRange` 메서드를 노출하려면 **호스트 항목의** ReferenceAssemblyFromVbaProject `Sheet1` 속성을 **True**로 설정합니다.

### <a name="to-expose-the-method-to-vba-code"></a>VBA 코드에 메서드를 노출하려면

1. **솔루션 탐색기**에서 **Sheet1.cs**를 두 번 클릭합니다.

     **WorkbookWithVBA** 파일이 디자이너에서 열리고 Sheet1이 표시됩니다.

2. **속성** 창에서 **ReferenceAssemblyFromVbaProject** 속성을 선택하고 값을 **True**로 변경합니다.

3. 표시되는 메시지에서 **확인** 을 클릭합니다.

4. 프로젝트를 빌드합니다.

## <a name="call-the-method-from-vba-code"></a>VBA 코드에서 메서드 호출
 이제 통합 문서의 VBA 코드에서 `CreateVstoNamedRange` 메서드를 호출할 수 있습니다.

> [!NOTE]
> 이 연습에서는 프로젝트를 디버그하는 동안 통합 문서에 VBA 코드를 추가합니다. Visual Studio에서 빌드 출력 폴더의 문서를 주 프로젝트 폴더의 문서 복사본으로 바꾸기 때문에 이 문서에 추가하는 모든 VBA 코드는 다음번에 프로젝트를 빌드할 때 덮어쓰입니다. VBA 코드를 저장하려는 경우 프로젝트 폴더의 문서에 복사할 수 있습니다. 자세한 내용은 [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)을 참조 하세요.

### <a name="to-call-the-method-from-vba-code"></a>VBA 코드에서 메서드를 호출하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. **개발자** 탭의 **코드** 그룹에서 **Visual Basic**을 클릭합니다.

     Visual Basic Editor가 열립니다.

3. **삽입** 메뉴에서 **모듈**을 클릭합니다.

4. 새 모듈에 다음 코드를 추가합니다.

     이 코드는 사용자 지정 어셈블리의 `CreateTable` 메서드를 호출합니다. 매크로는 전역 `GetManagedClass` 메서드를 사용하여 VBA 코드에 노출한 `Sheet1` 호스트 항목 클래스에 액세스하여 이 메서드에 액세스합니다. `GetManagedClass` 메서드는 이 연습의 앞부분에서 **ReferenceAssemblyFromVbaProject** 속성을 설정할 때 자동으로 생성되었습니다.

    ```vb
    Sub CallVSTOMethod()
        Dim VSTOSheet1 As CallingCodeFromVBA.Sheet1
        Set VSTOSheet1 = GetManagedClass(Sheet1)
        Call VSTOSheet1.CreateVstoNamedRange(Sheet1.Range("A1"), "VstoNamedRange")
    End Sub
    ```

5. **F5**키를 누릅니다.

6. 열려 있는 통합 문서의 **Sheet1** 에서 **A1**셀을 클릭합니다. 메시지 상자가 표시되는지 확인합니다.

7. 변경 내용을 저장하지 않고 Excel을 종료합니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서는 VBA에서 Office 솔루션의 코드를 호출하는 방법에 대해 자세히 알아볼 수 있습니다.

- VBA에서 Visual Basic 사용자 지정의 호스트 항목에 포함된 코드를 호출합니다. 이 프로세스는 Visual C# 프로세스와 다릅니다. 자세한 내용은 [연습: Visual Basic 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)을 참조 하세요.

- VBA에서 VSTO 추가 기능의 코드를 호출합니다. 자세한 내용은 [연습: VBA에서 VSTO 추가 기능의 코드 호출](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)
- [문서 수준 사용자 지정 프로그램](../vsto/programming-document-level-customizations.md)
- [방법: Visual Basic 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [방법: Visual C&#35; 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [연습: Visual Basic 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
