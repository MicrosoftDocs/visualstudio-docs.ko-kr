---
title: 다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- VBA [Office development in Visual Studio], calling code in application-level add-ins
- application-level add-ins [Office development in Visual Studio], calling code from other solutions
- calling add-in code
- add-ins [Office development in Visual Studio], calling code from other solutions
- interoperability [Office development in Visual Studio]
- calling code from VBA
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 584406098f058c17b3dd215dda9c8c4e9498cf46
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255324"
---
# <a name="call-code-in-vsto-add-ins-from-other-office-solutions"></a>다른 Office 솔루션에서 VSTO 추가 기능의 코드 호출
  VSTO 추가 기능의 개체를 다른 Microsoft Office 솔루션을 비롯한 다른 솔루션에 노출할 수 있습니다. 이는 해당 VSTO 추가 기능이 다른 솔루션에서 사용하도록 하려는 서비스를 제공하는 경우에 유용합니다. 예를 들어 웹 서비스의 재무 데이터에 대해 계산을 수행 하는 Microsoft Office Excel 용 VSTO 추가 기능이 있는 경우 다른 솔루션은 런타임에 Excel VSTO 추가 기능을 호출 하 여 이러한 계산을 수행할 수 있습니다.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

 이 프로세스는 크게 다음과 같은 두 가지 단계로 구성되어 있습니다.

- VSTO 추가 기능에서 개체를 다른 솔루션에 노출합니다.

- 다른 솔루션에서 VSTO 추가 기능을 통해 노출된 개체에 액세스하고 개체의 멤버를 호출합니다.

## <a name="types-of-solutions-that-can-call-code-in-an-add-in"></a>추가 기능에서 코드를 호출할 수 있는 솔루션의 유형
 VSTO 추가 기능의 개체를 다음 유형의 솔루션에 노출할 수 있습니다.

- VSTO 추가 기능과 동일한 애플리케이션 프로세스에서 로드되는 문서의 VBA(Visual Basic for Applications) 코드

- VSTO 추가 기능과 동일한 애플리케이션 프로세스에서 로드되는 문서 수준 사용자 지정

- Visual Studio의 Office 프로젝트 템플릿을 사용하여 만든 다른 VSTO 추가 기능

- COM VSTO 추가 기능(즉, <xref:Extensibility.IDTExtensibility2> 인터페이스를 직접 구현하는 VSTO 추가 기능)

- VSTO 추가 기능과 다른 프로세스에서 실행되는 솔루션(이러한 유형의 솔루션을 *OOP(Out-of-Process) 클라이언트*라고도 함). 여기에는 Windows Forms 또는 콘솔 애플리케이션 같은 Office 애플리케이션을 자동화하는 애플리케이션, 그리고 다른 프로세스에서 로드되는 VSTO 추가 기능이 포함됩니다.

## <a name="expose-objects-to-other-solutions"></a>다른 솔루션에 개체 노출
 VSTO 추가 기능의 개체를 다른 솔루션에 노출하려면 VSTO 추가 기능에서 다음 단계를 수행합니다.

1. 다른 솔루션에 노출하려는 클래스를 정의합니다.

2. <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 클래스에서 `ThisAddIn` 메서드를 재정의합니다. 다른 솔루션에 노출하려는 클래스의 인스턴스를 반환합니다.

### <a name="define-the-class-you-want-to-expose-to-other-solutions"></a>다른 솔루션에 노출 하려는 클래스를 정의 합니다.
 최소한, 노출하려는 클래스는 public 클래스여야 하며, <xref:System.Runtime.InteropServices.ComVisibleAttribute> 특성이 **true**로 설정되어 있어야 하고, [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 인터페이스를 노출해야 합니다.

 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) 인터페이스를 노출하는 데 권장되는 방식은 다음 단계를 수행하는 것입니다.

1. 다른 솔루션에 노출하려는 멤버를 선언하는 인터페이스를 정의합니다. 이 인터페이스를 VSTO 추가 기능 프로젝트에 정의할 수 있습니다. 하지만 클래스를 비VBA 솔루션에 노출하려는 경우에는 이 인터페이스를 별도의 클래스 라이브러리 프로젝트에 정의해야 할 수 있습니다. 이렇게 해야 VSTO 추가 기능을 호출하는 솔루션이 VSTO 추가 기능 프로젝트를 참조하지 않고 인터페이스를 참조할 수 있기 때문입니다.

2. <xref:System.Runtime.InteropServices.ComVisibleAttribute>이 인터페이스에 특성을 적용 하 고이 특성을 **true**로 설정 합니다.

3. 이 인터페이스에 구현할 클래스를 수정합니다.

4. 특성을 <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 클래스에 적용 하 고이 특성을 열거형의 **None** 값으로 설정 합니다 <xref:System.Runtime.InteropServices.ClassInterfaceType> .

5. 이 클래스를 out-of-process 클라이언트에 노출 하려면 다음을 수행 해야 할 수도 있습니다.

   - <xref:System.Runtime.InteropServices.StandardOleMarshalObject>에서 클래스를 파생합니다. 자세한 내용은 out-of-process [클라이언트에 클래스 노출](#outofproc)을 참조 하세요.

   - 인터페이스를 정의하는 프로젝트에서 **COM Interop 등록** 속성을 설정합니다. 클라이언트에서 초기 바인딩을 사용 하 여 VSTO 추가 기능을 호출 하도록 하려는 경우에만이 속성이 필요 합니다.

   다음 코드 예제에서는 다른 솔루션에서 호출할 수 있는 `AddInUtilities` 메서드와 `ImportData` 클래스를 보여 줍니다. 큰 연습의 컨텍스트에서이 코드를 보려면 [연습: VBA에서 VSTO 추가 기능의 코드 호출](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)을 참조 하세요.

   [!code-csharp[Trin_AddInInteropWalkthrough #3](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/AddInUtilities.cs#3)]
   [!code-vb[Trin_AddInInteropWalkthrough#3](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/AddInUtilities.vb#3)]

### <a name="expose-classes-to-vba"></a>VBA에 클래스 노출
 위에 나와 있는 단계를 수행하는 경우 VBA 코드는 인터페이스에서 선언하는 메서드만 호출할 수 있습니다. VBA 코드는 클래스가 <xref:System.Object>같은 기본 클래스에서 가져오는 메서드를 비롯해 클래스의 다른 모든 메서드를 호출할 수 없습니다.

 또는 특성을 [IDispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> 열거형의 Autodispatch 또는 autodispatch 값으로 설정 하 여 IDispatch 인터페이스를 노출할 수도 있습니다 <xref:System.Runtime.InteropServices.ClassInterfaceType> . 인터페이스를 노출 하는 경우 별도의 인터페이스에서 메서드를 선언할 필요가 없습니다. 하지만 VBA 코드는 <xref:System.Object>같은 기본 클래스에서 가져오는 메서드를 포함하여 클래스의 모든 public 및 비정적 메서드를 호출할 수 있습니다. 하지만 초기 바인딩을 사용하는 OOP(Out-of-Process) 클라이언트는 클래스를 호출할 수 없습니다.

### <a name="expose-classes-to-out-of-process-clients"></a><a name="outofproc"></a> Out-of-process 클라이언트에 클래스 노출
 OOP(Out-of-Process) 클라이언트에 VSTO 추가 기능의 클래스를 노출하려면 <xref:System.Runtime.InteropServices.StandardOleMarshalObject> 에서 클래스를 파생시켜 OOP 클라이언트가 노출된 VSTO 추가 기능 개체를 호출할 수 있도록 해야 합니다. 그렇지 않은 상태에서 OOP(Out-of-Process) 클라이언트에서 노출된 개체 인스턴스를 가져오려고 하면 예기치 않게 실패할 수 있습니다.

 이 오류는 Office 응용 프로그램의 개체 모델에 대 한 모든 호출은 주 UI 스레드에서 수행 되어야 하지만 out-of-process 클라이언트에서 개체로의 호출은 임의의 RPC (원격 프로시저 호출) 스레드에 도착 하기 때문입니다. .NET Framework의 COM 마샬링 메커니즘은 스레드를 전환하지 않으며 대신 주 UI 스레드 대신 들어오는 RPC 스레드에서 개체에 대한 호출을 마샬링하려고 합니다. 개체가 <xref:System.Runtime.InteropServices.StandardOleMarshalObject>에서 파생되는 클래스의 인스턴스인 경우 개체에 대한 들어오는 호출은 노출된 개체가 만들어진 스레드에 대해 자동으로 마샬링되며, 이 스레드는 호스트 애플리케이션의 주 UI 스레드가 됩니다.

 Office 솔루션에서 스레드를 사용 하는 방법에 대 한 자세한 내용은 [office의 스레딩 지원](../vsto/threading-support-in-office.md)을 참조 하세요.

### <a name="override-the-requestcomaddinautomationservice-method"></a>RequestComAddInAutomationService 메서드를 재정의 합니다.
 다음 코드 예제에서는 VSTO 추가 기능의 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 클래스에서 `ThisAddIn` 를 재정의하는 방법을 보여 줍니다. 이 예제에서는 `AddInUtilities` 다른 솔루션에 노출 하려는 라는 클래스를 정의 했다고 가정 합니다. 큰 연습의 컨텍스트에서이 코드를 보려면 [연습: VBA에서 VSTO 추가 기능의 코드 호출](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)을 참조 하세요.

 [!code-csharp[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/CSharp/Trin_AddInInteropWalkthrough/ThisAddIn.cs#1)]
 [!code-vb[Trin_AddInInteropWalkthrough#1](../vsto/codesnippet/VisualBasic/Trin_AddInInteropWalkthrough/ThisAddIn.vb#1)]

 VSTO 추가 기능이 로드되면 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 에서 <xref:Microsoft.Office.Tools.AddInBase.RequestComAddInAutomationService%2A> 메서드를 호출합니다. 런타임에서는 <xref:Microsoft.Office.Core.COMAddIn> VSTO 추가 기능을 나타내는 개체의 COMAddIn 속성에 반환 된 개체를 할당 합니다. 이 <xref:Microsoft.Office.Core.COMAddIn> 개체는 다른 Office 솔루션은 물론, Office를 자동화하는 솔루션에서 사용할 수 있습니다.

## <a name="access-objects-from-other-solutions"></a>다른 솔루션에서 개체 액세스
 VSTO 추가 기능에서 노출된 개체를 호출하려면 클라이언트 솔루션에서 다음을 수행합니다.

1. 노출된 VSTO 추가 기능을 나타내는 <xref:Microsoft.Office.Core.COMAddIn> 개체를 가져옵니다. 클라이언트는 호스트 Office 애플리케이션의 개체 모델에서 `Application.COMAddIns` 속성을 활용하여 사용 가능한 모든 VSTO 추가 기능에 액세스할 수 있습니다.

2. 개체의 COMAddIn 속성에 액세스 합니다 <xref:Microsoft.Office.Core.COMAddIn> . 이 속성은 VSTO 추가 기능에서 노출된 개체를 반환합니다.

3. 노출된 개체의 멤버를 호출합니다.

   COMAddIn 속성의 반환 값을 사용 하는 방법은 VBA 클라이언트와 비 VBA 클라이언트에 따라 다릅니다. OOP(Out-of-Process) 클라이언트의 경우 가능한 경합 상태가 발생하지 않도록 하기 위해 추가 코드가 필요합니다.

### <a name="access-objects-from-vba-solutions"></a>VBA 솔루션에서 개체 액세스
 다음 코드 예제에서는 VBA를 사용 하 여 VSTO 추가 기능에 의해 노출 되는 메서드를 호출 하는 방법을 보여 줍니다. 이 VBA 매크로는 `ImportData` **EXCELIMPORTDATA**라는 VSTO 추가 기능에 정의 된 라는 메서드를 호출 합니다. 큰 연습의 컨텍스트에서이 코드를 보려면 [연습: VBA에서 VSTO 추가 기능의 코드 호출](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)을 참조 하세요.

```vb
Sub CallVSTOMethod()
    Dim addIn As COMAddIn
    Dim automationObject As Object
    Set addIn = Application.COMAddIns("ExcelImportData")
    Set automationObject = addIn.Object
    automationObject.ImportData
End Sub
```

### <a name="access-objects-from-non-vba-solutions"></a>비 VBA 솔루션에서 개체 액세스
 비 VBA 솔루션에서는 COMAddIn 속성 값을 구현 하는 인터페이스로 캐스팅 해야 합니다. 그런 다음 인터페이스 개체에서 노출 된 메서드를 호출할 수 있습니다. 다음 코드 예제에서는 Visual Studio에서 Office 개발자 도구를 사용하여 만든 다른 VSTO 추가 기능에서 `ImportData` 메서드를 호출하는 방법을 보여 줍니다.

```vb
Dim addIn As Office.COMAddIn = Globals.ThisAddIn.Application.COMAddIns.Item("ExcelImportData")
Dim utilities As ExcelImportData.IAddInUtilities = TryCast( _
    addIn.Object, ExcelImportData.IAddInUtilities)
utilities.ImportData()
```

```csharp
object addInName = "ExcelImportData";
Office.COMAddIn addIn = Globals.ThisAddIn.Application.COMAddIns.Item(ref addInName);
ExcelImportData.IAddInUtilities utilities = (ExcelImportData.IAddInUtilities)addIn.Object;
utilities.ImportData();
```

 이 예제에서 COMAddIn 속성의 값을 인터페이스가 아닌 클래스로 캐스팅 하려고 하면 `AddInUtilities` `IAddInUtilities` 코드에서이 throw 됩니다 <xref:System.InvalidCastException> .

## <a name="see-also"></a>참고 항목
- [VSTO 추가 기능 프로그램](../vsto/programming-vsto-add-ins.md)
- [연습: VBA에서 VSTO 추가 기능의 코드 호출](../vsto/walkthrough-calling-code-in-a-vsto-add-in-from-vba.md)
- [Office 솔루션 개발](../vsto/developing-office-solutions.md)
- [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [확장성 인터페이스를 사용 하 여 UI 기능 사용자 지정](../vsto/customizing-ui-features-by-using-extensibility-interfaces.md)
