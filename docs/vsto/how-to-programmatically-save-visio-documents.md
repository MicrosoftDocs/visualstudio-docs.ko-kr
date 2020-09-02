---
title: '방법: 프로그래밍 방식으로 Visio 문서 저장'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], saving Visio documents
- Visio [Office development in Visual Studio], saving Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 891a5c44159d10aacbb767cbc5376ae1d62252b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547058"
---
# <a name="how-to-programmatically-save-visio-documents"></a>방법: 프로그래밍 방식으로 Visio 문서 저장
  여러 가지 방법을 사용하여 Microsoft Office Visio 문서를 저장할 수 있습니다.

- 변경 내용을 기존 문서에 저장합니다.

- 새 문서를 저장하거나 새 이름으로 문서를 저장합니다.

- 지정된 인수와 함께 문서를 저장합니다.

  자세한 내용은 VBA 참조 설명서에서 [Microsoft.Office.Interop.Visio.Document.Save](/office/vba/api/Visio.Document.Save) 메서드, [Microsoft.Office.Interop.Visio.Document.SaveAs](/office/vba/api/Visio.Document.SaveAs) 메서드 및 [Microsoft.Office.Interop.Visio.Document.SaveAsEx](/office/vba/api/Visio.Document.SaveAsEx) 메서드를 참조하세요.

## <a name="save-an-existing-document"></a>기존 문서 저장

### <a name="to-save-a-document"></a>문서를 저장하려면

- 이전에 저장한 문서에서 `Microsoft.Office.Tools.Visio.Document` 클래스의 `Microsoft.Office.Interop.Visio.Document.Save` 메서드를 호출합니다.

     이 코드 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

    > [!NOTE]
    > 새 Visio 문서가 아직 저장되지 않은 경우 `Microsoft.Office.Interop.Visio.Document.Save` 메서드에서 예외를 throw합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#11)]

## <a name="save-a-document-with-a-new-name"></a>새 이름으로 문서 저장
 `Microsoft.Office.Interop.Visio.Document.SaveAs` 메서드를 사용하여 새 문서를 저장하거나 새 이름으로 문서를 저장합니다. 이 메서드를 사용하려면 새 파일 이름을 지정해야 합니다.

### <a name="to-save-the-active-visio-document-with-a-new-name"></a>활성 Visio 문서를 새 이름으로 저장하려면

- 파일 이름까지 포함한 정규화된 경로를 사용하여 저장하려는 `Microsoft.Office.Tools.Visio.Document`의 `Microsoft.Office.Interop.Visio.Document.SaveAs` 메서드를 호출합니다. 해당 이름의 파일이 폴더에 이미 있으면 자동으로 덮어씁니다.

     이 코드 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#10)]

## <a name="save-a-document-with-a-new-name-and-specified-arguments"></a>새 이름 및 지정 된 인수를 사용 하 여 문서 저장
 `Microsoft.Office.Interop.Visio.Document.SaveAsEx` 메서드를 사용하여 새 이름으로 문서를 저장하고 문서에 적용할 인수를 지정합니다.

### <a name="to-save-document-with-a-new-name-and-specified-arguments"></a>새 이름 및 지정된 인수를 사용하여 문서를 저장하려면

- 파일 이름까지 포함한 정규화된 경로를 사용하여 저장하려는 `Microsoft.Office.Tools.Visio.Document`의 `Microsoft.Office.Interop.Visio.Document.SaveAsEx` 메서드를 호출합니다. 해당 이름의 파일이 폴더에 이미 있으면 예외가 throw됩니다.

     다음 코드 예제에서는 활성 문서를 새 이름으로 저장하고 문서를 읽기 전용으로 표시하며 가장 최근에 사용됨 문서 목록에 문서를 표시합니다. 이 코드 예제를 사용하려면 프로젝트의 `ThisAddIn` 클래스에서 실행합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#12)]

## <a name="compile-the-code"></a>코드 컴파일
 이 코드 예제에는 다음이 필요합니다.

- 새 이름이 있는 문서를 저장 하려면 이름이 인 디렉터리가 `Test` *내 문서* 폴더 (windows XP 및 이전) 또는 *문서* 폴더 (windows Vista)에 있어야 합니다.

## <a name="see-also"></a>추가 정보
- [Visio 솔루션](../vsto/visio-solutions.md)
- [Visio 개체 모델 개요](../vsto/visio-object-model-overview.md)
- [방법: 프로그래밍 방식으로 새 Visio 문서 만들기](../vsto/how-to-programmatically-create-new-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 열기](../vsto/how-to-programmatically-open-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 닫기](../vsto/how-to-programmatically-close-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 인쇄](../vsto/how-to-programmatically-print-visio-documents.md)
