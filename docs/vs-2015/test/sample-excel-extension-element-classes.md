---
title: '샘플 Excel 확장: Element 클래스 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 7c251098-00aa-49cf-9e37-5717c0c6b3f1
caps.latest.revision: 11
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 21c7777be710f0175708629eb9507b34f0d70be2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660445"
---
# <a name="sample-excel-extension-element-classes"></a>샘플 Excel 확장: 요소 클래스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

확장에서는 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement>에서 파생되며 [!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)]의 워크시트 컨트롤 및 셀 컨트롤을 나타내는 클래스를 사용합니다.

 이 확장의 기본 요소는 `ExcelElement`입니다. `ExcelWorksheetElement` 클래스 및 `ExcelCellElement` 클래스는 해당 요소에서 속성을 상속합니다.

## <a name="element-and-elementinformation-classes"></a>Element 및 ElementInformation 클래스
 `Element`는 Excel 확장의 모든 사용자 인터페이스 요소에 대한 기본 클래스이며 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement> 클래스에서 속성을 상속합니다. `ElementInformation`은 샘플의 요소 정보 클래스에 대한 기본 클래스이며 구성원은 포함하지 않습니다.

#### <a name="simple-properties-and-methods"></a>단순 속성 및 메서드
 이러한 구성원은 `Name` 속성의 값이나 `ClassName` 속성의 값과 같은 단순한 값을 반환하며, 코드는 명확하고 쉽게 읽을 수 있습니다. `Utility` 클래스를 사용하여 반환되는 값도 있습니다. 이 클래스에 대해서는 뒷부분에서 설명합니다. 그리고 이 샘플 확장과는 관련성이 없으므로 `null`을 반환하는 클래스도 있습니다. 특히 눈여겨볼 만한 두 멤버는 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> 속성과 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.CacheProperties%2A> 메서드입니다.

#### <a name="queryid-property"></a>QueryId 속성
 이 속성은 재생 중에 컨트롤을 고유하게 식별하는 속성 이름/값 쌍으로 구성된 조건을 반환합니다. 개발자는 파생된 각 컨트롤 클래스에 대해 프레임워크가 UI에서 컨트롤을 찾는 데 사용할 수 있는 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement> 개체를 반환하도록 이 속성을 재정의해야 합니다.

#### <a name="cacheproperties-method"></a>CacheProperties 메서드
 이 메서드는 기록 프로세스 중에 테스트 프레임워크에서 호출되어 중요 속성의 스냅샷을 저장하도록 요소에 지시합니다. 따라서 실제 UI 컨트롤이 화면에 더 이상 표시되어 있지 않아도 속성을 사용할 수 있습니다.

## <a name="worksheetelement-and-worksheetinformation-classes"></a>WorksheetElement 및 WorksheetInformation 클래스
 `WorksheetElement` 클래스는 테스트 프레임워크의 Excel 워크시트를 나타내며 `Element` 기본 클래스에서 속성을 상속합니다. Excel 워크시트 개체에 대한 특정 정보를 제공하기 위해 세 가지 속성(<xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ClassName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.ControlTypeName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.Name%2A>)이 재정의됩니다.

 이 클래스를 COM에 표시하기 위해 <xref:System.Runtime.InteropServices.ComVisibleAttribute>도 이 클래스에 적용됩니다.

 `WorksheetInformation` 클래스는 Excel 워크시트에 대한 정보를 나타냅니다. 이 클래스의 구성원은 `SheetName` 속성 하나뿐이며, 이 샘플에서는 해당 속성만 사용해도 충분합니다.

## <a name="cellelement-and-cellinformation-classes"></a>CellElement 및 CellInformation 클래스
 `CellElement` 클래스는 Excel 셀을 나타내며 `Element` 기본 클래스에서 속성을 상속합니다. 재정의되는 멤버는 `RowIndex` 및 `ColumnIndex` 속성을 사용하여 셀을 식별하는 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>를 반환하는 <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.UITechnologyElement.QueryId%2A> 속성뿐입니다.

## <a name="utilities-and-excelutilities-classes"></a>Utilities 및 ExcelUtilities 클래스
 내부 `ExcelUtilities` 클래스는 기술 이름과 같은 몇 가지 상수 값과, 제공된 창 핸들이 Excel 워크시트를 나타내는지 여부를 확인하는 메서드를 제공합니다.

 `Utilities` 클래스에는 UI에 대한 여러 정보를 반환하는 도우미 메서드가 있습니다. **USER32.DLL**, **OLEACC.DLL** 등의 외부 시스템 DLL을 직접 호출하여 UI에서 창 핸들을 가져오는 메서드도 있습니다<strong>.</strong>

## <a name="see-also"></a>관련 항목
 <xref:System.Runtime.InteropServices.ComVisibleAttribute> <xref:Microsoft.VisualStudio.TestTools.UITest.Extension.IQueryElement>
 [Microsoft Excel을 지원하도록 코딩된 UI 테스트 및 작업 기록 확장](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md)
