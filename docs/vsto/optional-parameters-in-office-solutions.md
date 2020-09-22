---
title: Office 솔루션의 선택적 매개 변수
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], optional parameters
- Visual C# [Office development in Visual Studio], optional parameters
- Visual Basic [Office development in Visual Studio], optional parameters
- application development [Office development in Visual Studio], optional parameters
- missing field [Office development in Visual Studio]
- optional parameters [Office development in Visual Studio]
- parameters [Office development in Visual Studio], optional
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: e8684ad4b9429a5499660ef4ad6fdd8133dccaa5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841998"
---
# <a name="optional-parameters-in-office-solutions"></a>Office 솔루션의 선택적 매개 변수
  Microsoft Office 애플리케이션의 개체 모델에 있는 메서드 중 상당수가 선택적 매개 변수를 허용합니다. Visual Studio에서 Visual Basic을 사용하여 Office 솔루션을 개발하는 경우 없는 매개 변수마다 기본값이 자동으로 사용되기 때문에 선택적 매개 변수의 값을 전달할 필요가 없습니다. 대부분의 경우 Visual C# 프로젝트에서도 선택적 매개 변수를 생략할 수 있습니다. 그러나 **ref** `ThisDocument` 문서 수준 Word 프로젝트에서는 클래스의 선택적 ref 매개 변수를 생략할 수 없습니다.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Visual c # 및 Visual Basic 프로젝트에서 선택적 매개 변수를 사용 하는 방법에 대 한 자세한 내용은 [명명 된 인수 및 선택적 인수 &#40;C&#35; 프로그래밍 가이드&#41;](/dotnet/csharp/programming-guide/classes-and-structs/named-and-optional-arguments) 및 [선택적 매개 변수 &#40;](/dotnet/visual-basic/programming-guide/language-features/procedures/optional-parameters)Visual Basic&#41;을 참조 하세요.

> [!NOTE]
> 이전 버전의 Visual Studio에서는 Visual C# 프로젝트에서 모든 선택적 매개 변수의 값을 전달해야 합니다. 편의를 위해 이러한 프로젝트에는 매개 변수의 기본값을 사용하려고 할 때 선택적 매개 변수에 전달할 수 있는 `missing`이라는 전역 변수가 포함되어 있습니다. Visual Studio의 Office 용 visual c # 프로젝트에는 여전히 변수가 포함 되어 `missing` 있지만 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] **ref** `ThisDocument` Word 용 문서 수준 프로젝트의 클래스에서 선택적 ref 매개 변수를 사용 하 여 메서드를 호출 하는 경우를 제외 하 고 일반적으로에서 office 솔루션을 개발할 때이 프로젝트를 사용할 필요가 없습니다.

## <a name="example-in-excel"></a>Excel의 예제
 <xref:Microsoft.Office.Tools.Excel.Worksheet.CheckSpelling%2A> 메서드에는 많은 선택적 매개 변수가 있습니다. 다음 코드 예제와 같이 일부 매개 변수에는 값을 지정하고 다른 매개 변수에는 기본값을 적용할 수 있습니다. 이 예제에는 `Sheet1`이라는 워크시트 클래스가 포함된 문서 수준 프로젝트가 필요합니다.

 [!code-csharp[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/CSharp/excelworkbook1/Sheet1.cs#1)]
 [!code-vb[Trin_VstrefGeneralExcel#1](../vsto/codesnippet/VisualBasic/excelworkbook1/Sheet1.vb#1)]

## <a name="example-in-word"></a>Word의 예제
 <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> 메서드에는 많은 선택적 매개 변수가 있습니다. 다음 코드 예제와 같이 일부 매개 변수에는 값을 지정하고 다른 매개 변수에는 기본값을 적용할 수 있습니다.

 [!code-vb[Trin_VstrefGeneralWord#1](../vsto/codesnippet/VisualBasic/worddocument1/ThisDocument.vb#1)]
 [!code-csharp[Trin_VstrefGeneralWord#1](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#1)]

## <a name="use-optional-parameters-of-methods-in-the-thisdocument-class-in-visual-c-document-level-projects-for-word"></a>Word 용 Visual c # 문서 수준 프로젝트의 ThisDocument 클래스에서 메서드의 선택적 매개 변수 사용
 Word 개체 모델에는 값을 허용 하는 선택적 **ref** 매개 변수가 있는 많은 메서드가 포함 되어 있습니다 <xref:System.Object> . 그러나 **ref** `ThisDocument` Word의 Visual c # 문서 수준 프로젝트에서 생성 된 클래스의 메서드에 대 한 선택적 ref 매개 변수는 생략할 수 없습니다. Visual c #에서는 클래스가 아닌 인터페이스 메서드에만 선택적 **ref** 매개 변수를 생략할 수 있습니다. 예를 들어 다음 코드 예제는 클래스의 메서드에 대 한 선택적 **ref** 매개 변수를 생략할 수 없기 때문에 컴파일되지 않습니다 <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> `ThisDocument` .

 [!code-csharp[Trin_VstrefGeneralWord#3](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#3)]

 `ThisDocument` 클래스의 메서드를 호출하는 경우 다음 지침을 따릅니다.

- 선택적 **ref** 매개 변수의 기본값을 적용 하려면 변수를 `missing` 매개 변수에 전달 합니다. `missing` 변수는 자동으로 Visual C# Office 프로젝트에서 정의되고 생성된 프로젝트 코드에서 <xref:System.Type.Missing> 값에 할당됩니다.

- 선택적 **ref** 매개 변수에 대 한 고유 값을 지정 하려면 지정 하려는 값에 할당 된 개체를 선언한 다음 개체를 매개 변수에 전달 합니다.

  다음 코드 예제에서는 <xref:Microsoft.Office.Tools.Word.DocumentBase.CheckSpelling%2A> *ignoreuppercase* 매개 변수의 값을 지정 하 고 다른 매개 변수에 대 한 기본값을 적용 하 여 메서드를 호출 하는 방법을 보여 줍니다.

  [!code-csharp[Trin_VstrefGeneralWord#4](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#4)]

  클래스에서 메서드의 선택적 **ref** 매개 변수를 생략 하는 코드를 작성 하려면 속성에서 반환 하는 `ThisDocument` 개체에 대해 동일한 메서드를 호출 하 <xref:Microsoft.Office.Interop.Word.Document> <xref:Microsoft.Office.Tools.Word.Document.InnerObject%2A> 고 해당 메서드에서 매개 변수를 생략할 수 있습니다. 이렇게 할 수 있는 이유는 <xref:Microsoft.Office.Interop.Word.Document>가 클래스가 아니라 인터페이스이기 때문입니다.

  [!code-csharp[Trin_VstrefGeneralWord#5](../vsto/codesnippet/CSharp/worddocument1/ThisDocument.cs#5)]

  값 및 참조 형식 매개 변수에 대 한 자세한 내용은 [값으로 인수 전달 및 참조로 인수 전달 &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference) (Visual Basic의 경우) 및 [전달 매개 변수 &#40;C&#35; 프로그래밍 가이드&#41;](/dotnet/csharp/programming-guide/classes-and-structs/passing-parameters)를 참조 하세요.

## <a name="see-also"></a>참고 항목
- [Office 솔루션 개발](../vsto/developing-office-solutions.md)
- [Office 솔루션에서 코드 작성](../vsto/writing-code-in-office-solutions.md)
