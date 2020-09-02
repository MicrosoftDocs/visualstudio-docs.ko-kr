---
title: Office 솔루션의 런타임에 바인딩
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- objects [Office development in Visual Studio], casting
- types [Office development in Visual Studio], casting
- automation [Office development in Visual Studio], casting objects
- casting, object to specific type
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 62224006d04e0a1e7447053e868dd9946f00c97e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62583948"
---
# <a name="late-binding-in-office-solutions"></a>Office 솔루션의 런타임에 바인딩
  Office 응용 프로그램의 개체 모델에 있는 일부 형식은 런타임에 바인딩 기능을 통해 사용할 수 있는 기능을 제공 합니다. 예를 들어, 일부 메서드 및 속성은 Office 응용 프로그램의 컨텍스트에 따라 다른 형식의 개체를 반환할 수 있으며, 일부 형식은 다른 컨텍스트에서 다른 메서드나 속성을 노출할 수 있습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 **Option Strict** 가 off 인 프로젝트와 또는를 대상으로 하는 Visual c # 프로젝트가 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 이러한 런타임에 바인딩 기능을 사용 하는 형식에서 직접 작업할 수 있는 Visual Basic 프로젝트입니다.

## <a name="implicit-and-explicit-casting-of-object-return-values"></a>개체 반환 값의 암시적 및 명시적 캐스팅
 Microsoft Office Pia (주 interop 어셈블리)의 여러 메서드 및 속성은 여러 가지 <xref:System.Object> 형식의 개체를 반환할 수 있기 때문에 값을 반환 합니다. 예를 들어 속성은의 <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> <xref:System.Object> 반환 값 <xref:Microsoft.Office.Interop.Excel.Worksheet> <xref:Microsoft.Office.Interop.Excel.Chart> 은 활성 시트가 무엇 인지에 따라 또는 개체 일 수 있기 때문에를 반환 합니다.

 메서드나 속성이을 반환 하는 경우 <xref:System.Object> **Option Strict** 가 on 인 Visual Basic 프로젝트에서 개체를 올바른 형식으로 명시적으로 변환 해야 합니다 (Visual Basic). <xref:System.Object> **Option Strict** 가 off 인 Visual Basic 프로젝트에서 반환 값을 명시적으로 캐스팅할 필요가 없습니다.

 대부분의 경우 참조 설명서에는를 반환 하는 멤버에 대 한 반환 값의 가능한 형식이 나열 <xref:System.Object> 됩니다. 개체를 변환 하거나 캐스팅 하면 코드 편집기의 개체에 대해 IntelliSense를 사용할 수 있습니다.

 Visual Basic 변환에 대 한 자세한 내용은 [암시적 변환과 명시적 변환 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) 및 [CType 함수 &#40;](/dotnet/visual-basic/language-reference/functions/ctype-function)Visual Basic&#41;을 참조 하세요.

### <a name="examples"></a>예제
 다음 코드 예제에서는 **Option Strict** 가 on 인 Visual Basic 프로젝트에서 개체를 특정 형식으로 캐스팅 하는 방법을 보여 줍니다. 이 형식의 프로젝트에서는 속성을로 명시적으로 캐스팅 해야 합니다 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> <xref:Microsoft.Office.Interop.Excel.Range> . 이 예제에는 라는 워크시트 클래스가 포함 된 문서 수준 Excel 프로젝트가 필요 `Sheet1` 합니다.

 [!code-vb[Trin_VstcoreProgramming#9](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#9)]

 다음 코드 예제에서는 **Option Strict** 가 off 인 Visual Basic 프로젝트에서 또는를 대상으로 하는 Visual c # 프로젝트에서 개체를 특정 형식으로 암시적으로 캐스팅 하는 방법을 보여 줍니다 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . 이러한 형식의 프로젝트에서 <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> 속성은 암시적으로로 캐스팅 됩니다 <xref:Microsoft.Office.Interop.Excel.Range> . 이 예제에는 라는 워크시트 클래스가 포함 된 문서 수준 Excel 프로젝트가 필요 `Sheet1` 합니다.

 [!code-vb[Trin_VstcoreProgramming#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreProgrammingExcelVB/Sheet1.vb#10)]
 [!code-csharp[Trin_VstcoreProgramming#10](../vsto/codesnippet/CSharp/Trin_VstcoreProgrammingExcelCS/Sheet1.cs#10)]

## <a name="access-members-that-are-available-only-through-late-binding"></a>런타임에 바인딩을 통해서만 사용할 수 있는 멤버에 액세스 합니다.
 Office Pia의 일부 속성 및 메서드는 런타임에 바인딩을 통해서만 사용할 수 있습니다. **Option Strict** 가 off 인 경우 또는를 대상으로 하는 Visual c # 프로젝트의 Visual Basic 프로젝트에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 이러한 언어의 런타임에 바인딩 기능을 사용 하 여 런타임에 바인딩된 멤버에 액세스할 수 있습니다. **Option Strict** 가 on 인 Visual Basic 프로젝트에서 리플렉션을 사용 하 여 이러한 멤버에 액세스 해야 합니다.

### <a name="examples"></a>예제
 다음 코드 예제에서는 **Option Strict** 가 off 인 Visual Basic 프로젝트에서 또는를 대상으로 하는 Visual c # 프로젝트에서 런타임에 바인딩된 멤버에 액세스 하는 방법을 보여 줍니다 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] . 이 예제에서는 Word에서 **파일 열기** 대화 상자의 런타임에 바인딩된 **이름** 속성에 액세스 합니다. 이 예제를 사용 하려면 `ThisDocument` `ThisAddIn` Word 프로젝트의 또는 클래스에서 실행 합니다.

 [!code-vb[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#122)]
 [!code-csharp[Trin_VstcoreWordAutomation#122](../vsto/codesnippet/CSharp/Trin_VstcoreWordAutomationCS/ThisDocument.cs#122)]

 다음 코드 예제에서는 리플렉션을 사용 하 여 **Option Strict** 가 on 인 Visual Basic 프로젝트에서 동일한 작업을 수행 하는 방법을 보여 줍니다.

 [!code-vb[Trin_VstcoreWordAutomation#102](../vsto/codesnippet/VisualBasic/Trin_VstcoreWordAutomationVB/ThisDocument.vb#102)]

## <a name="see-also"></a>추가 정보
- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)
- [Office 솔루션의 선택적 매개 변수](../vsto/optional-parameters-in-office-solutions.md)
- [Type dynamic &#40;C&#35; 프로그래밍 가이드를 사용&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)
- [Option Strict 문](/dotnet/visual-basic/language-reference/statements/option-strict-statement)
- [리플렉션(C#)](/dotnet/csharp/programming-guide/concepts/reflection)
- [리플렉션(Visual Basic)](/dotnet/visual-basic/programming-guide/concepts/reflection)
- [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)
