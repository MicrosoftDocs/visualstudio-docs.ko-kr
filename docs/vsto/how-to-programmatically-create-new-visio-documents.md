---
title: '방법: 프로그래밍 방식으로 새 Visio 문서 만들기'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], creating Visio documents
- documents [Office development in Visual Studio], creating Visio documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 171ad93caf6b5c13d000073a0d7f7e82282b9b4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85541533"
---
# <a name="how-to-programmatically-create-new-visio-documents"></a>방법: 프로그래밍 방식으로 새 Visio 문서 만들기
  새 Microsoft Office Visio 드로잉 문서를 만들려면 열려 있는 Visio 문서의 `Microsoft.Office.Interop.Visio.Documents` 컬렉션에 추가합니다. 결과적으로 `Microsoft.Office.Interop.Visio.Documents.Add` 메서드는 새 Visio 드로잉 문서를 만듭니다. 자세한 내용은 VBA 참조 설명서에서 [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) 메서드를 참조하세요.

## <a name="create-new-blank-documents"></a>비어 있는 새 문서 만들기

### <a name="to-create-a-new-document"></a>새 문서를 만들려면

- 템플릿을 기반으로 하지 않는 빈 문서를 새로 만들려면 `Microsoft.Office.Interop.Visio.Documents.Add` 메서드를 사용합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#1)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#1](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#1)]

## <a name="create-documents-copied-from-existing-documents"></a>기존 문서에서 복사 되는 문서 만들기
 `Microsoft.Office.Interop.Visio.Documents.Add` 메서드를 사용하면 기존 Visio 문서의 복사본인 새 문서를 만들 수 있습니다. 다이어그램의 파일 이름 및 정규화된 경로를 제공해야 합니다.

### <a name="to-create-a-new-document-that-is-copied-from-an-existing-document"></a>기존 문서에서 복사된 새 문서를 만들려면

- `Microsoft.Office.Interop.Visio.Documents.Add` 메서드를 호출하고 Visio 다이어그램의 경로를 지정합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#2)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#2](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#2)]

## <a name="create-stencils-copied-from-existing-stencils"></a>기존 스텐실에서 복사 되는 스텐실 만들기
 [Microsoft.Office.Interop.Visio.Documents.Add](/office/vba/api/Visio.Documents.Add) 메서드는 기존 Visio 스텐실의 복사본인 새 스텐실을 만들 수 있습니다. 스텐실의 파일 이름 및 정규화된 경로를 제공해야 합니다.

### <a name="to-create-a-new-stencil-that-is-copied-from-an-existing-stencil"></a>기존 스텐실에서 복사된 새 스텐실을 만들려면

- `Microsoft.Office.Interop.Visio.Documents.Add` 메서드를 호출하고 스텐실의 경로를 지정합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#3](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#3)]

## <a name="create-documents-based-on-existing-templates"></a>기존 템플릿을 기반으로 문서 만들기
 `Microsoft.Office.Interop.Visio.Documents.Add`메서드는 기존 Visio 템플릿 ( *.vst* 파일)을 기반으로 하는 새 문서 ( *.vsd* 파일)를 만들 수 있습니다. 이 메서드는 템플릿 작업 영역의 일부인 스텐실, 스타일 및 설정을 복사합니다. 서식 파일의 파일 이름 및 정규화된 경로를 제공해야 합니다.

### <a name="to-create-a-new-document-that-is-based-on-an-existing-template"></a>기존 템플릿을 기반으로 새 문서를 만들려면

- `Microsoft.Office.Interop.Visio.Documents.Add` 메서드를 호출하고 템플릿의 경로를 지정합니다.

     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/CSharp/trin_vstcorevisioautomationaddin/ThisAddIn.cs#4)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#4](../vsto/codesnippet/VisualBasic/trin_vstcorevisioautomationaddin/ThisAddIn.vb#4)]

## <a name="compile-the-code"></a>코드 컴파일
 이 코드 예제에는 다음이 필요합니다.

- 이라는 Visio 문서는 `myDrawing.vsd` `Test` *내 문서* 폴더 (windows XP 및 이전 버전의 경우) 또는 *Documents* 폴더 (windows Vista의 경우)에서 이름이 지정 된 디렉터리에 있어야 합니다.

- 이라는 Visio 문서는 `myStencil.vss` `Test` *내 문서* 폴더 (windows XP 및 이전 버전의 경우) 또는 *Documents* 폴더 (windows Vista의 경우)에서 이름이 지정 된 디렉터리에 있어야 합니다.

- 이라는 Visio 문서는 `myTemplate.vst` `Test` *내 문서* 폴더 (windows XP 및 이전 버전의 경우) 또는 *Documents* 폴더 (windows Vista의 경우)에서 이름이 지정 된 디렉터리에 있어야 합니다.

## <a name="see-also"></a>추가 정보
- [Visio 솔루션](../vsto/visio-solutions.md)
- [Visio 개체 모델 개요](../vsto/visio-object-model-overview.md)
- [방법: 프로그래밍 방식으로 Visio 문서 열기](../vsto/how-to-programmatically-open-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 닫기](../vsto/how-to-programmatically-close-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 저장](../vsto/how-to-programmatically-save-visio-documents.md)
- [방법: 프로그래밍 방식으로 Visio 문서 인쇄](../vsto/how-to-programmatically-print-visio-documents.md)
