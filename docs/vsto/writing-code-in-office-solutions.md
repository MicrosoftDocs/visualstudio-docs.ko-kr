---
title: Office 솔루션에서 코드 작성
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.RefactoringCancelled
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], writing code
- managed code [Office development in Visual Studio]
- Office development in Visual Studio, programming languages supported
- Office applications [Office development in Visual Studio], automating
- Office applications [Office development in Visual Studio], writing code
- writing code for Office solutions
- programming [Office development in Visual Studio], model
- Automation [Office development in Visual Studio], managed code
- application development [Office development in Visual Studio], programming model
- Office solutions [Office development in Visual Studio], writing code
- automating Office applications
- application development [Office development in Visual Studio], writing code
- application development [Office development in Visual Studio], automating
- Office projects [Office development in Visual Studio], changing namespaces
- solutions [Office development in Visual Studio], programming model
- programming [Office development in Visual Studio]
- namespaces [Office developmentin Visual Studio], changing in Office solutions
- projects [Office development in Visual Studio], writing code
- Office applications [Office development in Visual Studio], programming model
- managed code extensions [Office development in Visual Studio], writing code
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cead0569ae067fcc503f7f2074807c609e6eed75
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71255039"
---
# <a name="write-code-in-office-solutions"></a>Office 솔루션에서 코드 작성
  Visual Studio의 Office 프로젝트에는 기타 유형의 프로젝트와 다른 코드 작성의 몇 가지 측면이 있습니다. 이러한 차이점 중 상당수는 Office 개체 모델이 관리 코드에 노출되는 방식과 관련되어 있으며, 다른 차이점은 Office 프로젝트의 디자인과 관련되어 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="managed-code-and-office-programming"></a>관리 코드와 Office 프로그래밍
 통합된 Microsoft Office 솔루션을 만들 수 있도록 하는 핵심 기술은 COM(구성 요소 개체 모델) 기술의 일부인 자동화입니다. 자동화를 사용하면 적절한 프로그래밍 인터페이스를 지원하는 모든 애플리케이션, DLL 또는 ActiveX 컨트롤이 노출하는 소프트웨어 개체를 코드를 통해 만들고 제어할 수 있습니다.

### <a name="understand-primary-interop-assemblies"></a>주 interop 어셈블리 이해
 Microsoft Office 애플리케이션은 기능의 상당 부분을 자동화에 노출합니다. 그러나 Visual Basic 또는 C#과 같은 관리 코드를 직접 사용하여 Office 애플리케이션을 자동화할 수 없습니다. 관리 코드를 사용하여 Office 애플리케이션을 자동화하려면 Office PIA(주 interop 어셈블리)를 사용해야 합니다. 주 interop 어셈블리를 사용하면 관리 코드가 Office 애플리케이션의 COM 기반 개체 모델과 상호 작용할 수 있습니다.

 모든 Microsoft Office 애플리케이션에는 PIA가 있습니다. Visual Studio에서 Office 프로젝트를 만들 때 적절한 PIA에 대한 참조가 프로젝트에 자동으로 추가됩니다. 프로젝트에서 다른 Office 애플리케이션의 기능을 자동화하려면 적절한 PIA에 대한 참조를 수동으로 추가해야 합니다. 자세한 내용은 [방법: 주 interop 어셈블리를 통한 Office 응용 프로그램 대상](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)을 참조 하세요.

### <a name="use-primary-interop-assemblies-at-design-time-and-runtime"></a>디자인 타임 및 런타임에 주 interop 어셈블리 사용
 대부분의 개발 작업을 수행하려면 개발 컴퓨터의 전역 어셈블리 캐시에서 Office PIA를 설치하고 등록해야 합니다. 자세한 내용은 [Office 솔루션을 개발할 수 있도록 컴퓨터 구성](../vsto/configuring-a-computer-to-develop-office-solutions.md)을 참조 하세요.

 최종 사용자 컴퓨터에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 Office 솔루션을 실행하는 데 Office PIA가 필요하지 않습니다. 자세한 내용은 [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)를 참조 하세요.

### <a name="use-types-in-primary-interop-assemblies"></a>주 interop 어셈블리에서 형식 사용
 Office PIA에는 Office 애플리케이션의 개체 모델을 노출하는 형식과 코드에서 직접 사용되지 않을 추가 인프라 형식의 조합이 포함되어 있습니다. Office Pia의 형식에 대 한 개요는 [office 주 interop 어셈블리의 클래스 및 인터페이스 개요](/previous-versions/office/office-12/ms247299\(v\=office.12\))를 참조 하세요.

 Office PIA의 형식이 COM 기반 개체 모델의 형식에 해당하기 때문에 이러한 형식을 사용하는 방식은 다른 관리되는 형식과 다른 경우가 많습니다. 예를 들어 Office 주 interop 어셈블리에서 선택적 매개 변수가 있는 메서드를 호출하는 방식은 프로젝트에서 사용하고 있는 프로그래밍 언어에 따라 달라집니다. 자세한 내용은 다음 항목을 참조하세요.

- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)

- [Office 솔루션의 런타임에 바인딩](../vsto/late-binding-in-office-solutions.md)

## <a name="program-model-of-office-projects"></a>Office 프로젝트의 프로그램 모델
 모든 Office 프로젝트에는 코드에 대한 진입점을 제공하는 생성된 클래스가 하나 이상 포함되어 있습니다. 이러한 클래스를 사용하면 호스트 애플리케이션의 개체 모델과 작업창 및 사용자 지정 작업창과 같은 기능에도 액세스할 수 있습니다.

### <a name="understand-the-generated-classes"></a>생성 된 클래스 이해
 Excel 및 Word의 문서 수준 프로젝트에서 생성된 클래스는 애플리케이션 개체 모델의 최상위 개체와 유사합니다. 예를 들어 Word 문서 프로젝트의 생성된 `ThisDocument` 클래스는 Word 개체 모델의 <xref:Microsoft.Office.Interop.Word.Document> 클래스와 동일한 멤버를 제공합니다. 문서 수준 프로젝트에서 생성 된 클래스에 대 한 자세한 내용은 [문서 수준 사용자 지정 프로그래밍](../vsto/programming-document-level-customizations.md)을 참조 하세요.

 VSTO 추가 기능 프로젝트는 `ThisAddIn`이라는 생성된 클래스를 제공합니다. 이 클래스는 호스트 애플리케이션의 개체 모델에 있는 클래스와 유사하지 않습니다. 대신이 클래스는 VSTO 추가 기능 자체를 나타내며, 호스트 응용 프로그램의 개체 모델에 액세스 하 고 VSTO 추가 기능에 사용할 수 있는 다른 기능에 액세스 하는 데 사용할 수 있는 멤버를 제공 합니다. 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md)을 참조 하세요.

 Office 프로젝트의 모든 생성된 클래스에는 `Startup` 및 `Shutdown` 이벤트 처리기가 포함되어 있습니다. 코드 작성을 시작하려면 일반적으로 이러한 이벤트 처리기에 코드를 추가합니다. VSTO 추가 기능을 초기화하기 위해 `Startup` 이벤트 처리기에 코드를 추가할 수 있습니다. VSTO 추가 기능에서 사용하는 리소스를 정리하기 위해 `Shutdown` 이벤트 처리기에 코드를 추가할 수 있습니다. 자세한 내용은 [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)를 참조 하세요.

### <a name="access-the-generated-classes-at-run-time"></a>런타임에 생성 된 클래스에 액세스
 Office 솔루션이 로드될 때 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 은 프로젝트에서 각각의 생성된 클래스를 인스턴스화합니다. `Globals` 클래스를 사용하여 프로젝트의 모든 코드에서 이러한 개체에 액세스할 수 있습니다. 예를 들어 클래스를 사용 `Globals` 하 여 `ThisAddIn` VSTO 추가 기능에 있는 리본 단추의 이벤트 처리기에서 클래스의 코드를 호출할 수 있습니다.

 자세한 내용은 [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)를 참조 하세요.

### <a name="namespace-considerations-in-office-solutions"></a>Office 솔루션의 네임 스페이스 고려 사항
 Office 프로젝트를 만든 후 프로젝트의 *기본 네임스페이스* (또는 Visual Basic에서는 *루트 네임스페이스* )를 변경할 수 없습니다. 기본 네임스페이스는 프로젝트를 만들 때 지정한 프로젝트 이름과 항상 일치합니다. 프로젝트의 이름을 변경하는 경우 기본 네임스페이스는 변경되지 않습니다. 프로젝트의 기본 네임 스페이스에 대 한 자세한 내용은 [응용 프로그램 페이지, 프로젝트 디자이너 &#40;C&#35;&#41;](../ide/reference/application-page-project-designer-csharp.md) 및 [응용 프로그램 페이지, 프로젝트 디자이너 &#40;Visual Basic&#41;](../ide/reference/application-page-project-designer-visual-basic.md)를 참조 하세요.

### <a name="change-the-namespace-of-host-item-classes-in-c-projects"></a>C # 프로젝트에서 호스트 항목 클래스의 네임 스페이스 변경
 Visual C# Office 프로젝트에서 호스트 항목 클래스(예: `ThisAddIn`, `ThisWorkbook`또는 `ThisDocument` 클래스)에는 고유한 네임스페이스가 있습니다. 기본적으로 프로젝트에서 호스트 항목의 네임스페이스는 프로젝트를 만들 때 지정한 프로젝트 이름과 일치합니다.

 Visual C# Office 프로젝트에서 호스트 항목의 네임스페이스를 변경하려면 **호스트 항목의 네임스페이스** 속성을 사용합니다. 자세한 내용은 [Office 프로젝트의 속성](../vsto/properties-in-office-projects.md)을 참조 하세요.

## <a name="supported-programming-languages-in-office-projects"></a>Office 프로젝트에서 지원 되는 프로그래밍 언어
 Visual Studio에서 Office 프로젝트 템플릿은 Visual Basic 및 Visual C# 프로그래밍 언어만 지원합니다. 따라서 이러한 프로젝트 템플릿은 **에서** 새 프로젝트 **대화 상자의** Visual Basic **및** Visual C# [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]노드에서만 사용할 수 있습니다. 자세한 내용은 [방법: Visual Studio에서 Office 프로젝트 만들기](../vsto/how-to-create-office-projects-in-visual-studio.md)를 참조 하세요.

## <a name="language-choice-and-office-programming"></a>언어 선택 및 Office 프로그래밍
 Microsoft Office 및 VBA(Visual Basic for Applications)는 애플리케이션 사용자 지정의 워크플로를 최적화하기 위해 함께 작동하도록 개발되었습니다. Visual Basic은 이러한 개발 중 일부를 상속했습니다. 예를 들어 Visual Basic에서는 선택적 매개 변수를 지원하므로 Visual C#을 사용하는 경우보다 Microsoft Office 주 interop 어셈블리의 일부 메서드를 호출할 때 적은 코드를 작성할 수 있습니다.

## <a name="program-with-visual-basic-vs-visual-c-in-office-solutions"></a>Office 솔루션의 Visual Basic 및 Visual c #을 사용한 프로그램
 Visual Basic 또는 Visual C#을 사용하여 Office 솔루션을 만들 수 있습니다. Microsoft Office 개체 모델이 Microsoft VBA(Visual Basic for Applications)와 함께 사용하도록 설계되었기 때문에 Visual Basic 개발자는 Microsoft Office 애플리케이션이 노출하는 개체로 편안하게 작업할 수 있습니다. Visual C# 개발자는 Visual Basic 개발자와 거의 동일한 기능을 사용할 수 있지만 Office 개체 모델을 사용하기 위해 추가 코드를 작성해야 하는 경우가 있습니다. 또한 Office 개발의 기본 프로그래밍 기능과 Visual Basic 및 C#으로 작성된 관리 코드 간에는 몇 가지 차이점이 있습니다.

<!-- markdownlint-disable MD003 MD020 -->
## <a name="key-differences-between-visual-basic-and-visual-c"></a>Visual Basic와 Visual C의 주요 차이점 #
<!-- markdownlint-enable MD003 MD020 -->

다음 표에서는 Office 개발에서 Visual Basic과 Visual C#의 주요 차이점을 보여 줍니다.

|기능|설명|Visual Basic 지원|Visual C# 지원|
|-------------|-----------------|--------------------------|------------------------|
|선택적 매개 변수|많은 Microsoft Office 메서드에는 메서드를 호출할 때 필요하지 않은 매개 변수가 있습니다. 매개 변수의 값이 전달되지 않는 경우 기본값이 사용됩니다.|Visual Basic에서는 선택적 매개 변수를 지원합니다.|Visual C#에서는 대부분의 경우 선택적 매개 변수를 지원합니다. 자세한 내용은 [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)를 참조 하세요.|
|참조로 매개 변수 전달|대부분의 Microsoft Office 주 interop 어셈블리에서 선택적 매개 변수는 값으로 전달할 수 있습니다. 그러나 일부 주 interop 어셈블리에서 참조 형식을 사용하는 선택적 매개 변수는 참조로 전달해야 합니다.<br /><br /> 값 및 참조 형식 매개 변수에 대 한 자세한 내용은 [값으로 인수 전달 및 참조로 인수 전달 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic의 경우) 및 [전달 매개 변수 &#40;C&#35; 프로그래밍 가이드&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)를 참조 하세요.|참조로 매개 변수를 전달하는 데는 추가 작업이 필요하지 않습니다. Visual Basic 컴파일러는 필요한 경우 자동으로 매개 변수를 참조로 전달합니다.|대부분의 경우 Visual C# 컴파일러는 필요한 경우 자동으로 매개 변수를 참조로 전달합니다. 자세한 내용은 [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)를 참조 하세요.|
|매개 변수가 있는 속성|일부 속성은 매개 변수를 받아들이고 읽기 전용 함수로 작동합니다.|Visual Basic에서는 매개 변수를 받아들이는 속성을 지원합니다.|Visual C#에서는 매개 변수를 받아들이는 속성을 지원합니다.|
|런타임에 바인딩|런타임에 바인딩에서는 디자인 타임에 변수를 개체 형식으로 캐스팅하는 대신 런타임에 개체의 속성을 결정합니다.|Visual Basic에서는 **Option Strict** 가 off일 때 런타임에 바인딩을 수행합니다. **Option Strict** 가 on으로 설정 된 경우 명시적으로 개체를 변환 하 고 네임 스페이스의 형식을 사용 <xref:System.Reflection> 하 여 런타임에 바인딩된 멤버에 액세스 해야 합니다. 자세한 내용은 [Office 솔루션의 런타임에 바인딩](../vsto/late-binding-in-office-solutions.md)을 참조 하세요.|Visual C#에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]을 대상으로 하는 프로젝트에서 런타임에 바인딩을 수행합니다. 자세한 내용은 [Office 솔루션의 런타임에 바인딩](../vsto/late-binding-in-office-solutions.md)을 참조 하세요.|

## <a name="key-differences-between-office-development-and-managed-code"></a>Office 개발과 관리 코드의 주요 차이점
 다음 표에서는 Visual Basic 또는 Visual C#으로 작성된 관리 코드와 Office 개발의 주요 차이점을 보여 줍니다.

|기능|설명|Visual Basic 및 Visual C# 지원|
|-------------|-----------------|-----------------------------------------|
|배열 인덱스|Microsoft Office 애플리케이션에서 컬렉션의 배열 하한은 1부터 시작합니다. Visual Basic 및 Visual C#에서는 0부터 시작하는 배열을 사용합니다. 자세한 내용은 [배열 &#40;C&#35; 프로그래밍 가이드&#41;](/dotnet/csharp/programming-guide/arrays/index) 및 [Visual Basic에서 배열](/dotnet/visual-basic/programming-guide/language-features/arrays/index)을 참조 하세요.|Microsoft Office 애플리케이션의 개체 모델에서 컬렉션의 첫 번째 항목에 액세스하려면 인덱스 0 대신 1을 사용합니다.|

## <a name="see-also"></a>추가 정보

- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](../vsto/global-access-to-objects-in-office-projects.md)
- [Office 프로젝트의 이벤트](../vsto/events-in-office-projects.md)
- [방법: 주 interop 어셈블리를 통한 Office 응용 프로그램 대상](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md)
- [방법: Office 프로젝트에서 이벤트 처리기 만들기](../vsto/how-to-create-event-handlers-in-office-projects.md)
- [Office 솔루션의 런타임에 바인딩](../vsto/late-binding-in-office-solutions.md)
- [Office 솔루션 공동 개발](../vsto/collaborative-development-of-office-solutions.md)
