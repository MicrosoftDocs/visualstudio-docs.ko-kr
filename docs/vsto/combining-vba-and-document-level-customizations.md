---
title: VBA 및 문서 수준 사용자 지정 결합
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.VBAInterop.InvalidAssemblyVersion
- VST.VBAInterop.ProjectLoadFailure
- VST.VBAInterop.MissingGUID
- VST.VBAInterop.EnableComCallers
- VST.VBAInterop.PersistVBACode
- VST.VBAInterop.ReferenceAssemblyFromVBA
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio]
- Office documents [Office development in Visual Studio], Visual Basic for Applications and
- VBA [Office development in Visual Studio], about VBA and document-level customizations
- managed code [Office development in Visual Studio], Visual Basic for Applications and
- document-level customizations [Office development in Visual Studio], Visual Basic for Applications and
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b3bab9c132439c6efa53842f1e13c6c5be31db00
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "70977598"
---
# <a name="combine-vba-and-document-level-customizations"></a>VBA 및 문서 수준 사용자 지정 결합
  Microsoft Office Word 또는 Microsoft Office Excel의 문서 수준 사용자 지정의 일부인 문서에서 VBA(Visual Basic for Applications) 코드를 사용할 수 있습니다. 사용자 지정 어셈블리에서 문서의 VBA 코드를 호출하거나, 문서의 VBA 코드에서 사용자 지정 어셈블리의 코드를 호출할 수 있도록 프로젝트를 구성할 수 있습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

## <a name="behavior-of-vba-code-in-a-document-level-customization"></a>문서 수준 사용자 지정에서 VBA 코드의 동작
 Visual Studio에서 프로젝트를 열 때 문서가 디자인 모드에서 열립니다. VBA 코드는 문서가 디자인 모드에 있을 때 실행되지 않으므로 VBA 코드를 실행하지 않고 문서와 코드에서 작업할 수 있습니다.

 솔루션을 실행할 때 VBA와 사용자 지정 어셈블리의 이벤트 처리기는 문서에서 발생하는 이벤트를 선택하며, 두 코드 집합이 모두 실행됩니다. 코드가 실행되는 순서를 사전에 결정할 수는 없습니다. 각 개별 사례에서 테스트를 통해 이를 결정해야 합니다. 두 코드 집합이 신중하게 조정되고 테스트되지 않은 경우 예기치 않은 결과를 얻을 수 있습니다.

## <a name="call-vba-code-from-the-customization-assembly"></a>사용자 지정 어셈블리에서 VBA 코드 호출
 Word 문서에서 매크로를 호출할 수 있으며 Excel 통합 문서에서 매크로와 함수를 호출할 수 있습니다. 이 작업을 수행하려면 다음 방법 중 하나를 사용합니다.

- Word의 경우 <xref:Microsoft.Office.Interop.Word._Application.Run%2A> 클래스의 메서드를 호출 합니다 <xref:Microsoft.Office.Interop.Word.Application> .

- Excel의 경우 <xref:Microsoft.Office.Interop.Excel._Application.Run%2A> 클래스의 <xref:Microsoft.Office.Interop.Excel.Application> 메서드를 호출합니다.

  각 메서드의 경우 첫 번째 매개 변수는 호출하려는 매크로나 함수의 이름을 식별하고 나머지 선택적 매개 변수는 매크로나 함수에 전달할 매개 변수를 지정합니다. 첫 번째 매개 변수에는 Word 및 Excel에 대한 다양한 형식이 포함될 수 있습니다.

- Word의 경우 첫 번째 매개 변수는 서식 파일, 모듈 및 매크로 이름의 조합일 수 있는 문자열입니다. 문서 이름을 지정하는 경우 코드에서는 임의의 문서의 임의의 매크로가 아니라 현재 컨텍스트와 관련된 문서의 매크로만 실행할 수 있습니다.

- Excel의 경우 첫 번째 매개 변수는 매크로 이름, 함수의 위치를 나타내는 <xref:Microsoft.Office.Interop.Excel.Range> 또는 등록된 DLL(XLL) 함수의 레지스터 ID를 지정하는 문자열일 수 있습니다. 문자열을 전달하는 경우 문자열이 활성 시트의 컨텍스트에서 평가됩니다.

  다음 코드 예제에서는 Excel의 문서 수준 프로젝트에서 `MyMacro` 라는 매크로를 호출하는 방법을 보여 줍니다. 이 예제에서는 `MyMacro` 가 `Sheet1`에서 정의되어 있다고 가정합니다.

```vb
Globals.Sheet1.Application.Run("MyMacro")
```

```csharp
Globals.Sheet1.Application.Run("MyMacro", missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing, missing,
    missing, missing, missing, missing, missing, missing);
```

> [!NOTE]
> Visual c #에서 선택적 매개 변수 대신 전역 변수를 사용 하는 방법에 대 한 자세한 내용은 `missing` [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)을 참조 하세요.

## <a name="call-code-in-document-level-customizations-from-vba"></a>VBA에서 문서 수준 사용자 지정의 코드 호출
 문서의 VBA(Visual Basic for Applications) 코드에서 사용자 지정 어셈블리의 코드를 호출할 수 있도록 Word 또는 Excel의 문서 수준 프로젝트를 구성할 수 있습니다. 이는 다음과 같은 시나리오에서 유용합니다.

- 동일한 문서와 연결된 문서 수준 사용자 지정의 기능을 사용하여 문서에서 기존 VBA 코드를 확장하려는 경우

- 문서에서 VBA 코드를 작성하여 문서 수준 사용자 지정에서 개발하는 서비스를 서비스에 액세스할 수 있는 최종 사용자가 사용할 수 있도록 하려는 경우

  Visual Studio의 Office 개발 도구는 VSTO 추가 기능에 대해 유사한 기능을 제공 합니다. VSTO 추가 기능을 개발 하는 경우 다른 Microsoft Office 솔루션에서 VSTO 추가 기능의 코드를 호출할 수 있습니다. 자세한 내용은 [다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출](../vsto/calling-code-in-vsto-add-ins-from-other-office-solutions.md)을 참조 하세요.

> [!NOTE]
> 이 기능은 Word 서식 파일 프로젝트에서 사용할 수 없습니다. 이 기능은 Word 문서, Excel 통합 문서 또는 Excel 서식 파일 프로젝트에서만 사용할 수 있습니다.

## <a name="requirements"></a>요구 사항
 VBA 코드에서 사용자 지정 어셈블리를 호출할 수 있도록 하기 전에 프로젝트는 다음 요구 사항을 충족해야 합니다.

- 문서에 다음 파일 이름 확장명 중 하나가 있어야 합니다.

  - Word의 경우: *.docm* 또는 *.doc*

  - Excel: *.xlsm*, *. xltm*, *.xls*또는 *.xlt*

- 문서에 VBA 코드가 포함된 VBA 프로젝트가 이미 있어야 합니다.

- 문서의 VBA 코드는 매크로를 사용하도록 설정하라는 메시지를 사용자에게 표시하지 않고 실행될 수 있어야 합니다. Word 또는 Excel의 보안 센터 설정에서 신뢰할 수 있는 위치 목록에 Office 프로젝트의 위치를 추가하여 VBA 코드를 실행하도록 신뢰할 수 있습니다.

- Office 프로젝트에는 VBA에 노출할 공용 멤버가 하나 이상 포함된 공용 클래스가 적어도 하나 포함되어 있어야 합니다.

     메서드, 속성 및 이벤트를 VBA에 노출할 수 있습니다. 노출하는 클래스는 호스트 항목 클래스(예: Word의 경우 `ThisDocument` 또는 Excel의 경우 `ThisWorkbook` 및 `Sheet1` )이거나 프로젝트에서 정의하는 다른 클래스일 수 있습니다. 호스트 항목에 대 한 자세한 내용은 [호스트 항목 및 호스트 컨트롤 개요](../vsto/host-items-and-host-controls-overview.md)를 참조 하세요.

## <a name="enable-vba-code-to-call-into-the-customization-assembly"></a>VBA 코드에서 사용자 지정 어셈블리를 호출할 수 있도록 설정
 사용자 지정 어셈블리의 멤버를 문서의 VBA 코드에 노출할 수 있는 두 가지 방법이 있습니다.

- [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 프로젝트의 호스트 항목 클래스 멤버를 VBA에 노출할 수 있습니다. 이렇게 하려면 호스트 항목(즉, 문서, 워크시트 또는 통합 문서)이 디자이너에 열려 있는 동안 **속성** 창에서 호스트 항목의 **EnableVbaCallers** 속성을 **True** 로 설정합니다. Visual Studio에서는 VBA 코드에서 클래스의 멤버를 호출할 수 있도록 하는 데 필요한 모든 작업을 자동으로 수행합니다.

- Visual C# 프로젝트의 모든 공용 클래스 멤버 또는 [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] 프로젝트의 비 호스트 항목 클래스 멤버를 VBA에 노출할 수 있습니다. 이 옵션을 사용하는 경우 VBA에 노출하는 클래스를 좀더 자유롭게 선택할 수 있지만 더 많은 수동 단계가 필요하기도 합니다.

   이렇게 하려면 다음 주요 단계를 수행해야 합니다.

  1. COM에 클래스를 노출합니다.

  2. VBA에 노출할 클래스의 인스턴스를 반환하도록 프로젝트에서 호스트 항목 클래스의 **GetAutomationObject** 메서드를 재정의합니다.

  3. 프로젝트에서 호스트 항목 클래스의 **ReferenceAssemblyFromVbaProject** 속성을 **True**로 설정합니다. 이렇게 하면 사용자 지정 어셈블리의 형식 라이브러리가 어셈블리에 포함되고 형식 라이브러리에 대한 참조가 문서의 VBA 프로젝트에 추가됩니다.

  자세한 내용은 [방법: Visual Basic 프로젝트에서 vba로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md) 및 [방법: Visual C&#35; 프로젝트에서 Vba로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)을 참조 하세요.

  **EnableVbaCallers** 및 **ReferenceAssemblyFromVbaProject** 속성은 디자인 타임에만 **속성** 창에서 사용할 수 있으며 런타임에는 사용할 수 없습니다. 속성을 보려면 [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]에서 호스트 항목에 대한 디자이너를 엽니다. 이러한 속성을 설정할 때 Visual Studio에서 수행 하는 특정 작업에 대 한 자세한 내용은 [호스트 항목 속성에 의해 수행](#PropertyTasks)되는 작업을 참조 하세요.

> [!NOTE]
> 통합 문서나 문서에 VBA 코드가 이미 포함되어 있지 않거나 문서의 VBA 코드를 실행하도록 신뢰할 수 없는 경우 **EnableVbaCallers** 또는 **ReferenceAssemblyFromVbaProject** 속성을 **True**로 설정하면 오류 메시지가 표시됩니다. 그 이유는 이러한 경우 Visual Studio에서 문서의 VBA 프로젝트를 수정할 수 없기 때문입니다.

## <a name="use-members-in-vba-code-to-call-into-the-customization-assembly"></a>VBA 코드의 멤버를 사용 하 여 사용자 지정 어셈블리 호출
 VBA 코드에서 사용자 지정 어셈블리를 호출할 수 있도록 프로젝트를 구성한 후 Visual Studio에서는 다음 멤버를 문서의 VBA 프로젝트에 추가합니다.

- 모든 프로젝트에 대해 Visual Studio에서는 `GetManagedClass`라는 전역 메서드를 추가합니다.

- [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)] **EnableVbaCallers** 속성을 사용 하 여 호스트 항목 클래스의 멤버를 노출 하는 프로젝트의 경우 Visual Studio는 `CallVSTOAssembly` `ThisDocument` `ThisWorkbook` `Sheet1` `Sheet2` VBA 프로젝트의,,, 또는 `Sheet3` 모듈에 이라는 속성을 추가 합니다.

  `CallVSTOAssembly` 속성이나 `GetManagedClass` 메서드를 사용하여 프로젝트의 VBA 코드에 노출한 클래스의 공용 멤버에 액세스할 수 있습니다.

> [!NOTE]
> 솔루션을 개발하고 배포하는 동안 VBA 코드를 추가할 수 있는 문서의 복사본이 몇 가지 있습니다. 자세한 내용은 [문서에 VBA 코드를 추가 하기 위한 지침](#Guidelines)을 참조 하세요.

### <a name="use-the-callvstoassembly-property-in-a-visual-basic-project"></a>Visual Basic 프로젝트에서 CallVSTOAssembly 속성 사용
 `CallVSTOAssembly` 속성을 사용하여 호스트 항목 클래스에 추가한 공용 멤버에 액세스할 수 있습니다. 예를 들어 다음 VBA 매크로는 Excel 통합 문서 프로젝트에서 `MyVSTOMethod` 클래스에 정의된 `Sheet1` 라는 메서드를 호출합니다.

```vb
Sub MyMacro()
    Sheet1.CallVSTOAssembly.MyVSTOMethod()
End Sub
```

 이 속성을 사용하면 `GetManagedClass` 메서드를 직접 사용하는 것보다 간편하게 사용자 지정 어셈블리를 호출할 수 있습니다. `CallVSTOAssembly` 는 VBA에 노출한 호스트 항목 클래스를 나타내는 개체를 반환합니다. 반환된 개체의 멤버와 메서드 매개 변수가 IntelliSense에서 표시됩니다.

 `CallVSTOAssembly` 속성에는 다음 코드와 유사한 선언이 있습니다. 이 코드에서는 `Sheet1` 이라는 Excel 통합 문서 프로젝트의 `ExcelWorkbook1` 호스트 항목 클래스를 VBA에 노출했다고 가정합니다.

```vb
Property Get CallVSTOAssembly() As ExcelWorkbook1.Sheet1
    Set CallVSTOAssembly = GetManagedClass(Me)
End Property
```

### <a name="use-the-getmanagedclass-method"></a>GetManagedClass 메서드 사용
 전역 `GetManagedClass` 메서드를 사용하려면 **GetAutomationObject** 메서드의 재정의가 포함된 호스트 항목 클래스에 해당하는 VBA 개체를 전달합니다. 그런 다음 반환된 개체를 사용하여 VBA에 노출한 클래스에 액세스합니다.

 예를 들어 다음 VBA 매크로는 `MyVSTOMethod` 이라는 Excel 통합 문서 프로젝트에서 `Sheet1` 호스트 항목 클래스에 정의된 `ExcelWorkbook1`메서드를 호출합니다.

```vb
Sub CallVSTOMethod
    Dim VSTOSheet1 As ExcelWorkbook1.Sheet1
    Set VSTOSheet1 = GetManagedClass(Sheet1)
    VSTOSheet1.MyVSTOMethod
End Sub
```

 `GetManagedClass` 메서드에는 다음과 같은 선언이 있습니다.

```vb
GetManagedClass(pdispInteropObject Object) As Object
```

 이 메서드는 VBA에 노출한 클래스를 나타내는 개체를 반환합니다. 반환된 개체의 멤버와 메서드 매개 변수가 IntelliSense에서 표시됩니다.

## <a name="guidelines-for-adding-vba-code-to-the-document"></a><a name="Guidelines"></a> 문서에 VBA 코드를 추가 하기 위한 지침
 문서 수준 사용자 지정을 호출하는 VBA 코드를 추가할 수 있는 문서의 복사본이 몇 가지 있습니다.

 솔루션을 개발하고 테스트하면서 Visual Studio에서 프로젝트를 디버그하거나 실행하는 동안 열려 있는 문서(즉, 빌드 출력 폴더의 문서)에서 VBA 코드를 작성할 수 있습니다. 그러나 Visual Studio에서 빌드 출력 폴더의 문서를 주 프로젝트 폴더의 문서 복사본으로 바꾸기 때문에 이 문서에 추가하는 모든 VBA 코드는 다음번에 프로젝트를 빌드할 때 덮어쓰입니다.

 솔루션을 디버그하거나 실행하는 동안 문서에 추가하는 VBA 코드를 저장하려면 프로젝트 폴더의 문서에 VBA 코드를 복사합니다. 빌드 프로세스에 대 한 자세한 내용은 [office 솔루션 빌드](../vsto/building-office-solutions.md)를 참조 하세요.

 솔루션을 배포할 준비가 된 경우 VBA 코드를 추가할 수 있는 세 가지 주요 문서 위치가 있습니다.

### <a name="in-the-project-folder-on-the-development-computer"></a>개발 컴퓨터의 프로젝트 폴더
 이 위치는 문서의 VBA 코드와 사용자 지정 코드를 모두 완전히 제어할 수 있는 경우에 편리합니다. 문서가 개발 컴퓨터에 있기 때문에 사용자 지정 코드를 변경하는 경우 VBA 코드를 쉽게 수정할 수 있습니다. 이 문서 복사본에 추가하는 VBA 코드는 솔루션을 빌드하고 디버그하고 게시할 때 문서에 남아 있습니다.

 문서가 디자이너에서 열려 있는 동안 문서에 VBA 코드를 추가할 수 없습니다. 먼저 디자이너에서 문서를 닫은 후 Word나 Excel에서 직접 문서를 열어야 합니다.

> [!CAUTION]
> 문서가 열려 있을 때 실행되는 VBA 코드를 추가하면 이 코드로 인해 문서가 손상되거나 디자이너에서 열리지 못하는 경우가 드물게 발생합니다.

### <a name="in-the-publish-or-installation-folder"></a>게시 또는 설치 폴더
 게시 또는 설치 폴더에서 문서에 VBA 코드를 추가하는 것이 적합한 경우도 있습니다. 예를 들어 Visual Studio가 설치되지 않은 컴퓨터에서 다른 개발자가 VBA 코드를 작성하고 테스트하는 경우 이 옵션을 선택할 수 있습니다.

 사용자가 게시 폴더에서 직접 솔루션을 설치하는 경우 솔루션을 게시할 때마다 문서에 VBA 코드를 추가해야 합니다. Visual Studio에서는 솔루션을 게시할 때 게시 위치의 문서를 덮어씁니다.

 사용자가 게시 폴더와 다른 설치 폴더에서 솔루션을 설치하는 경우 솔루션을 게시할 때마다 문서에서 VBA 코드를 추가하는 것을 방지할 수 있습니다. 게시 업데이트가 게시 폴더에서 설치 폴더로 이동할 준비가 되면 문서를 제외한 모든 파일을 설치 폴더에 복사합니다.

### <a name="on-the-end-user-computer"></a>최종 사용자 컴퓨터
 최종 사용자가 문서 수준 사용자 지정에서 제공하는 서비스를 호출하는 VBA 개발자인 경우 문서의 복사본에서 `CallVSTOAssembly` 속성이나 `GetManagedClass` 메서드를 사용하여 코드를 호출하는 방법을 최종 사용자에게 알려줄 수 있습니다. 솔루션에 업데이트를 게시할 때 문서는 업데이트를 게시 하 여 수정 되지 않으므로 최종 사용자 컴퓨터의 문서에서 VBA 코드를 덮어쓰지 않습니다.

## <a name="tasks-performed-by-the-host-item-properties"></a><a name="PropertyTasks"></a> 호스트 항목 속성에 의해 수행 되는 작업
 **EnableVbaCallers** 및 **ReferenceAssemblyFromVbaProject** 속성을 사용하는 경우 Visual Studio에서는 다른 작업 집합을 수행합니다.

### <a name="enablevbacallers"></a>속성
 Visual Basic 프로젝트에서 호스트 항목의 **EnableVbaCallers** 속성을 **True** 로 설정하면 Visual Studio에서는 다음 작업을 수행합니다.

1. <xref:Microsoft.VisualBasic.ComClassAttribute> 및 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 특성을 호스트 항목 클래스에 추가합니다.

2. 호스트 항목 클래스의 **GetAutomationObject** 메서드를 재정의합니다.

3. 호스트 항목의 **ReferenceAssemblyFromVbaProject** 속성을 **True**로 설정합니다.

   **EnableVbaCallers** 속성을 다시 **False**로 설정하면 Visual Studio에서는 다음 작업을 수행합니다.

4. <xref:Microsoft.VisualBasic.ComClassAttribute> 클래스에서 <xref:System.Runtime.InteropServices.ComVisibleAttribute> 및 `ThisDocument` 특성을 제거합니다.

5. 호스트 항목 클래스에서 **GetAutomationObject** 메서드를 제거합니다.

   > [!NOTE]
   > Visual Studio에서는 자동으로 **ReferenceAssemblyFromVbaProject** 속성을 다시 **False**로 설정하지 않습니다. **속성** 창을 사용하여 수동으로 이 속성을 **False** 로 설정할 수 있습니다.

### <a name="referenceassemblyfromvbaproject"></a>ReferenceAssemblyFromVbaProject
 Visual Basic 또는 Visual C# 프로젝트에서 호스트 항목의 **ReferenceAssemblyFromVbaProject** 속성이 **True**로 설정되면 Visual Studio에서는 다음 작업을 수행합니다.

1. 사용자 지정 어셈블리에 대한 형식 라이브러리를 생성하고 어셈블리에 형식 라이브러리를 포함합니다.

2. 문서에서 VBA 프로젝트의 다음 형식 라이브러리에 대한 참조를 추가합니다.

   - 사용자 지정 어셈블리에 대한 형식 라이브러리.

   - Microsoft Visual Studio Tools for Office Execution Engine 9.0 형식 라이브러리. 이 형식 라이브러리는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]에 포함되어 있습니다.

   **ReferenceAssemblyFromVbaProject** 속성이 다시 **False**로 설정되면 Visual Studio에서는 다음 작업을 수행합니다.

3. 문서의 VBA 프로젝트에서 형식 라이브러리 참조를 제거합니다.

4. 어셈블리에서 포함된 형식 라이브러리를 제거합니다.

## <a name="troubleshoot"></a>문제 해결
 다음 표에는 몇 가지 일반적인 오류와 해당 오류를 해결하기 위한 제안 사항이 나와 있습니다.

|오류|제안 해결 방법|
|-----------|----------------|
|**EnableVbaCallers** 또는 **ReferenceAssemblyFromVbaProject** 속성을 설정한 후 문서에 VBA 프로젝트가 포함되어 있지 않다는 오류 메시지가 표시되거나 문서에서 VBA 프로젝트에 액세스할 수 있는 권한이 없습니다.|프로젝트의 문서에 VBA 매크로가 하나 이상 포함되어 있고, VBA 프로젝트를 실행하는 데 충분한 신뢰가 있으며, VBA 프로젝트가 암호로 보호되지 않는지 확인합니다.|
|**EnableVbaCallers** 또는 **ReferenceAssemblyFromVbaProject** 속성을 설정 하 고 나면 선언이 없거나 손상 되었다는 오류 메시지가 표시 됩니다 <xref:System.Runtime.InteropServices.GuidAttribute> .|<xref:System.Runtime.InteropServices.GuidAttribute>선언이 프로젝트의 *AssemblyInfo.cs* 또는 *AssemblyInfo* 파일에 있으며이 특성이 유효한 GUID로 설정 되어 있는지 확인 합니다.|
|**EnableVbaCallers** 또는 **ReferenceAssemblyFromVbaProject** 속성을 설정한 후에는에 지정 된 버전 번호가 잘못 되었음을 나타내는 오류 메시지가 표시 <xref:System.Reflection.AssemblyVersionAttribute> 됩니다.|<xref:System.Reflection.AssemblyVersionAttribute>프로젝트의 *AssemblyInfo.cs* 또는 *AssemblyInfo* 파일에서 선언이 유효한 어셈블리 버전 번호로 설정 되어 있는지 확인 합니다. 유효한 어셈블리 버전 번호에 대한 자세한 내용은 <xref:System.Reflection.AssemblyVersionAttribute> 클래스를 참조하세요.|
|사용자 지정 어셈블리의 이름을 변경한 후 사용자 지정 어셈블리를 호출하는 VBA 코드의 작동이 중지됩니다.|사용자 지정 어셈블리를 VBA 코드에 노출한 후 사용자 지정 어셈블리의 이름을 변경하면 문서의 VBA 프로젝트와 사용자 지정 어셈블리 간의 연결이 끊어집니다. 이 문제를 해결하려면 프로젝트에서 **ReferenceFromVbaAssembly** 속성을 **False** 로 변경했다가 다시 **True**로 변경한 후 VBA 코드에서 이전 어셈블리 이름에 대한 모든 참조를 새 어셈블리 이름으로 바꿉니다.|

## <a name="see-also"></a>추가 정보
- [방법: Visual Basic 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-basic-project.md)
- [방법: Visual C&#35; 프로젝트에서 VBA로 코드 노출](../vsto/how-to-expose-code-to-vba-in-a-visual-csharp-project.md)
- [연습: Visual Basic 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-basic-project.md)
- [연습: Visual C&#35; 프로젝트에서 VBA의 코드 호출](../vsto/walkthrough-calling-code-from-vba-in-a-visual-csharp-project.md)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
- [Visual Studio의 VBA 및 Office 솔루션 비교](../vsto/vba-and-office-solutions-in-visual-studio-compared.md)
- [문서 수준 사용자 지정 프로그램](../vsto/programming-document-level-customizations.md)
