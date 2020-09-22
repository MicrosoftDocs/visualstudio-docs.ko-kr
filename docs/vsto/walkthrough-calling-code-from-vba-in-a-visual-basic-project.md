---
title: '연습: Visual Basic 프로젝트에서 VBA의 코드 호출'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- ThisDocument class
- Word [Office development in Visual Studio], calling code from VBA
- Visual Basic [Office development in Visual Studio], calling code from VBA
- VBA [Office development in Visual Studio], calling code in document-level customizations
- Office documents [Office development in Visual Studio, Visual Basic for Applications and
- calling code from VBA
- document-level customizations [Office development in Visual Studio], calling code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 46fa903b0025279fec3b33d3c14ce1661d076926
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842199"
---
# <a name="walkthrough-call-code-from-vba-in-a-visual-basic-project"></a>연습: Visual Basic 프로젝트에서 VBA의 코드 호출
  이 연습에서는 문서의 VBA(Visual Basic for Applications) 코드에서 Microsoft Office Word에 대한 문서 수준 사용자 지정의 메서드를 호출하는 방법을 보여 줍니다. 이 절차에는 세 가지 기본 단계( `ThisDocument` 호스트 항목 클래스에 메서드 추가, VBA 코드에 메서드 노출, 문서의 VBA 코드에서 메서드 호출)가 포함됩니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 이 연습에서는 Word를 사용하지만 Excel용 문서 수준 프로젝트에도 연습에서 설명하는 개념이 적용됩니다.

 이 연습에서는 다음 작업을 수행합니다.

- VBA 코드를 포함하는 문서 만들기

- Word의 보안 센터를 사용하여 문서 위치 신뢰

- `ThisDocument` 호스트 항목 클래스에 메서드 추가

- VBA 코드에 메서드 노출

- VBA 코드에서 메서드 호출

> [!NOTE]
> 일부 Visual Studio 사용자 인터페이스 요소의 경우 다음 지침에 설명된 것과 다른 이름 또는 위치가 시스템에 표시될 수 있습니다. 이러한 요소는 사용하는 Visual Studio 버전 및 설정에 따라 결정됩니다. 자세한 내용은 [Visual Studio IDE 개인 설정](../ide/personalizing-the-visual-studio-ide.md)을 참조하세요.

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word

## <a name="create-a-document-that-contains-vba-code"></a>VBA 코드를 포함 하는 문서 만들기
 첫 번째 단계는 간단한 VBA 매크로를 포함하는 매크로 사용 문서를 만드는 것입니다. 해당 문서를 기반으로 하는 Visual Studio 프로젝트를 만들기 전에 문서에 VBA 프로젝트가 포함되어야 합니다. 그렇지 않으면 Visual Studio가 VBA 코드에서 사용자 지정 어셈블리를 호출할 수 있도록 VBA 프로젝트를 수정할 수 없습니다.

 사용하려는 VBA 코드를 포함하는 문서가 이미 있는 경우 이 단계를 건너뛸 수 있습니다.

### <a name="to-create-a-document-that-contains-vba-code"></a>VBA 코드를 포함하는 문서를 만들려면

1. Word를 시작합니다.

2. 문서 이름이 **Documentwithvba**인 Word **매크로 사용 문서 ( \* .docm)** 로 활성 문서를 저장 합니다. 통합 문서를 바탕 화면과 같은 편리한 위치에 저장합니다.

3. 리본에서 **개발자** 탭을 클릭합니다.

    > [!NOTE]
    > **개발자** 탭이 표시되지 않는 경우 먼저 개발자 탭을 표시해야 합니다. 자세한 내용은 [방법: 리본 메뉴에 개발자 탭 표시](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)를 참조 하세요.

4. **코드** 그룹에서 **Visual Basic**을 클릭합니다.

     Visual Basic Editor가 열립니다.

5. **프로젝트** 창에서 **ThisDocument**를 두 번 클릭합니다.

     `ThisDocument` 개체의 코드 파일이 열립니다.

6. 다음 VBA 코드를 코드 파일에 추가합니다. 이 코드는 아무 작업도 수행하지 않는 간단한 함수를 정의합니다. 이 함수의 유일한 목적은 VBA 프로젝트가 문서에 있는지 확인하는 것입니다. 이 작업은 이 연습의 이후 단계에 필요합니다.

    ```vb
    Sub EmptySub()
    End Sub
    ```

7. 문서를 저장하고 Word를 종료합니다.

## <a name="create-the-project"></a>프로젝트 만들기
 이제 이전에 만든 매크로 사용 문서를 사용하는 Word용 문서 수준 프로젝트를 만들 수 있습니다.

### <a name="to-create-a-new-project"></a>새 프로젝트를 만들려면

1. [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다. IDE가 Visual Basic 개발 설정을 사용하도록 설정되면 **파일** 메뉴에서 **새 프로젝트**를 클릭합니다.

3. 템플릿 창에서 **Visual Basic**을 확장한 다음 **Office/SharePoint**를 확장합니다.

4. **Office 추가 기능** 노드를 선택합니다.

5. 프로젝트 템플릿 목록에서 **Word 2010 문서** 또는 **Word 2013 문서** 프로젝트를 선택합니다.

6. **이름** 상자에 **CallingCodeFromVBA**를 입력합니다.

7. **확인**을 클릭합니다.

     **Visual Studio Tools for Office 프로젝트 마법사** 가 열립니다.

8. **기존 문서 복사**를 선택하고 **기존 문서의 전체 경로** 상자에서 이전에 만든 **DocumentWithVBA** 문서의 위치를 지정합니다. 사용자 고유의 매크로 사용 문서를 사용하는 경우 대신 이 문서의 위치를 지정합니다.

9. **마침**을 클릭합니다.

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] 의 디자이너에 **DocumentWithVBA** 문서가 열리고 **CallingCodeFromVBA** 프로젝트가 **솔루션 탐색기**에 추가됩니다.

## <a name="trust-the-location-of-the-document"></a>문서 위치를 신뢰 합니다.
 문서의 VBA 코드에 솔루션의 코드를 노출하려면 먼저 실행할 문서의 VBA를 신뢰해야 합니다. 이 작업을 수행하는 데는 몇 가지 방법이 있습니다. 이 연습의 경우 Word의 **보안 센터** 에서 문서 위치를 신뢰합니다.

### <a name="to-trust-the-location-of-the-document"></a>문서 위치를 신뢰하려면

1. Word를 시작합니다.

2. **파일** 탭을 클릭합니다.

3. **Word 옵션** 단추를 클릭합니다.

4. 범주 창에서 **보안 센터**를 클릭합니다.

5. 세부 정보 창에서 **보안 센터 설정**을 클릭합니다.

6. 범주 창에서 **신뢰할 수 있는 위치**를 클릭합니다.

7. 세부 정보 창에서 **새 위치 추가**를 클릭합니다.

8. **Microsoft Office 신뢰할 수 있는 위치** 대화 상자에서 **CallingCodeFromVBA** 프로젝트가 들어 있는 폴더를 찾습니다.

9. **이 위치의 하위 폴더도 신뢰할 수 있음**을 선택합니다.

10. **Microsoft Office 신뢰할 수 있는 위치** 대화 상자에서 **확인**을 클릭합니다.

11. **보안 센터** 대화 상자에서 **확인**을 클릭합니다.

12. **Word 옵션** 대화 상자에서 **확인**을 클릭합니다.

13. Word를 종료합니다.

## <a name="add-a-method-to-the-thisdocument-class"></a>ThisDocument 클래스에 메서드 추가
 이제 VBA 프로젝트가 설정되었으므로 VBA 코드에서 호출할 수 있는 `ThisDocument` 호스트 항목 클래스에 메서드를 추가합니다.

### <a name="to-add-a-method-to-the-thisdocument-class"></a>ThisDocument 클래스에 메서드를 추가하려면

1. **솔루션 탐색기**에서 **ThisDocument.vb**를 마우스 오른쪽 단추로 클릭한 다음 **코드 보기**를 클릭합니다.

     **ThisDocument.vb** 파일이 코드 편집기에서 열립니다.

2. `ThisDocument` 클래스에 다음 메서드를 추가합니다. 이 메서드는 문서의 시작 부분에 두 행과 두 열이 있는 테이블을 만듭니다. 매개 변수는 첫 번째 행에 표시되는 텍스트를 지정합니다. 이 연습의 뒷부분에서는 문서의 VBA 코드에서 이 메서드를 호출합니다.

     [!code-vb[Trin_CallingVBCustomizationFromVBA#1](../vsto/codesnippet/VisualBasic/CallingCodeFromVBA/ThisDocument.vb#1)]

3. 프로젝트를 빌드합니다.

## <a name="expose-the-method-to-vba-code"></a>VBA 코드에 메서드 노출
 문서의 VBA 코드에 `CreateTable` 메서드를 노출하려면 **호스트 항목의** EnableVbaCallers `ThisDocument` 속성을 **True**로 설정합니다.

### <a name="to-expose-the-method-to-vba-code"></a>VBA 코드에 메서드를 노출하려면

1. **솔루션 탐색기**에서 **ThisDocument.vb**를 두 번 클릭합니다.

     **DocumentWithVBA** 파일이 디자이너에서 열립니다.

2. **속성** 창에서 **EnableVbaCallers** 속성을 선택하고 값을 **True**로 변경합니다.

3. 표시되는 메시지에서 **확인** 을 클릭합니다.

4. 프로젝트를 빌드합니다.

## <a name="call-the-method-from-vba-code"></a>VBA 코드에서 메서드 호출
 이제 문서의 VBA 코드에서 `CreateTable` 메서드를 호출할 수 있습니다.

> [!NOTE]
> 이 연습에서는 프로젝트를 디버그하는 동안 문서에 VBA 코드를 추가합니다. Visual Studio에서 빌드 출력 폴더의 문서를 주 프로젝트 폴더의 문서 복사본으로 바꾸기 때문에 이 문서에 추가하는 모든 VBA 코드는 다음번에 프로젝트를 빌드할 때 덮어쓰입니다. VBA 코드를 저장하려는 경우 프로젝트 폴더의 문서에 복사할 수 있습니다. 자세한 내용은 [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)을 참조 하세요.

### <a name="to-call-the-method-from-vba-code"></a>VBA 코드에서 메서드를 호출하려면

1. **F5** 키를 눌러 프로젝트를 실행 합니다.

2. **개발자** 탭의 **코드** 그룹에서 **Visual Basic**을 클릭합니다.

     Visual Basic Editor가 열립니다.

3. **삽입** 메뉴에서 **모듈**을 클릭합니다.

4. 새 모듈에 다음 코드를 추가합니다.

     이 코드는 사용자 지정 어셈블리의 `CreateTable` 메서드를 호출합니다. 매크로는 `CallVSTOAssembly` 개체의 `ThisDocument` 속성을 사용하여 이 메서드에 액세스합니다. 이 속성은 이 연습의 앞부분에서 **EnableVbaCallers** 속성을 설정할 때 자동으로 생성되었습니다.

    ```vb
    Sub CreateTable()
        Call ThisDocument.CallVSTOAssembly.CreateTable("Employee Name", "Start Date")
    End Sub
    ```

5. **F5**키를 누릅니다.

6. 문서에 새 테이블이 추가되었는지 확인합니다.

7. 변경 내용을 저장하지 않고 Word를 종료합니다.

## <a name="next-steps"></a>다음 단계
 다음 항목에서는 VBA에서 Office 솔루션의 코드를 호출하는 방법에 대해 자세히 알아볼 수 있습니다.

- VBA에서 Visual C# 사용자 지정의 코드를 호출합니다. 이 프로세스는 Visual Basic 프로세스와 다릅니다. 자세한 내용은 [연습: Visual C&#35; 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)을 참조 하세요.

- VBA에서 VSTO 추가 기능의 코드를 호출합니다. 자세한 내용은 [연습: VBA에서 VSTO 추가 기능의 코드 호출](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [VBA 및 문서 수준 사용자 지정 결합](../vsto/combining-vba-and-document-level-customizations.md)
- [문서 수준 사용자 지정 프로그램](../vsto/programming-document-level-customizations.md)
- [방법: Visual Basic 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [방법: Visual C&#35; 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [연습: Visual C&#35; 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
