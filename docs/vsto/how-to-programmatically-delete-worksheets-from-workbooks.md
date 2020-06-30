---
title: '방법: 프로그래밍 방식으로 통합 문서에서 워크시트 삭제'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- workbooks, deleting worksheets
- worksheets, deleting
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 38aa92ae1c320ae9eb5ad4bdb1e43b761048661f
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547136"
---
# <a name="how-to-programmatically-delete-worksheets-from-workbooks"></a>방법: 프로그래밍 방식으로 통합 문서에서 워크시트 삭제
  통합 문서의 모든 워크시트를 삭제할 수 있습니다. 워크시트를 삭제하려면 워크시트 호스트 항목을 사용하거나 통합 문서의 시트 컬렉션을 통해 워크시트에 액세스합니다.

 [!INCLUDE[appliesto_xlalldocapp](includes/appliesto-xlalldocapp-md.md)]

## <a name="use-the-worksheet-host-item"></a>워크시트 호스트 항목 사용
 문서 수준 사용자 지정에서 디자인 타임에 워크시트가 추가된 경우 <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> 메서드를 사용하여 지정된 워크시트를 삭제합니다. 다음 코드는 워크시트 호스트 항목을 직접 참조하여 통합 문서에서 워크시트를 삭제합니다.

> [!IMPORTANT]
> 이 코드는 다음 프로젝트 템플릿 중 하나를 사용하여 만든 프로젝트에서만 실행됩니다.
>
> - Excel 2013 통합 문서
> - Excel 2013 서식 파일
> - Excel 2010 통합 문서
> - Excel 2010 템플릿
>
>   다른 형식의 프로젝트에서이 작업을 수행 하려는 경우에는 **Microsoft** 의 프로젝트에 대 한 참조를 추가 해야 합니다. 그런 다음 해당 어셈블리의 클래스를 사용 하 여 통합 문서를 열고 워크시트를 삭제 해야 합니다. 자세한 내용은 [방법: 주 interop 어셈블리를 통한 Office 응용 프로그램 대상](how-to-target-office-applications-through-primary-interop-assemblies.md) 및 [Excel 2010 주 interop 어셈블리 참조](office-primary-interop-assemblies.md)를 참조 하세요.

### <a name="to-delete-a-worksheet-by-using-a-worksheet-host-item"></a>워크시트 호스트 항목을 사용하여 워크시트를 삭제하려면

1. <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> 의 `Sheet1`메서드를 호출합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#17](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#17)]

## <a name="use-the-sheets-collection-of-the-excel-workbook"></a>Excel 통합 문서의 시트 컬렉션 사용
 다음과 같은 경우 Microsoft Office Excel <xref:Microsoft.Office.Interop.Excel.Sheets> 컬렉션을 통해 워크시트에 액세스합니다.

- VSTO 추가 기능에서 워크시트를 삭제하려고 합니다.

- 삭제하려는 워크시트는 문서 수준 사용자 지정에서 런타임에 생성되었습니다.

  다음 코드는 시트 컬렉션의 인덱스 번호를 **통해 시트를** 참조 하 여 통합 문서에서 워크시트를 삭제 합니다. 이 코드에서는 새 워크시트가 프로그래밍 방식으로 생성되었다고 가정합니다.

> [!IMPORTANT]
> 다른 형식의 프로젝트에서이 작업을 수행 하려는 경우에는 **Microsoft** 의 프로젝트에 대 한 참조를 추가 해야 합니다. 그런 다음 해당 어셈블리의 클래스를 사용 하 여 통합 문서를 열고 워크시트를 삭제 해야 합니다. 자세한 내용은 [방법: 주 interop 어셈블리를 통한 Office 응용 프로그램 대상](how-to-target-office-applications-through-primary-interop-assemblies.md) 및 [Excel 2010 주 interop 어셈블리 참조](office-primary-interop-assemblies.md)를 참조 하세요.

### <a name="to-delete-a-worksheet-by-using-the-sheets-collection-of-the-excel-workbook"></a>Excel 통합 문서의 시트 컬렉션을 사용하여 워크시트를 삭제하려면

1. <xref:Microsoft.Office.Interop.Excel.Sheets> 컬렉션의 <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> 메서드를 호출합니다.

     [!code-csharp[Trin_VstcoreExcelAutomation#18](codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#18)]

## <a name="see-also"></a>참고 항목
- [워크시트 작업](working-with-worksheets.md)
- [방법: 프로그래밍 방식으로 워크시트 숨기기](how-to-programmatically-hide-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서 내에서 워크시트 이동](how-to-programmatically-move-worksheets-within-workbooks.md)
- [방법: 프로그래밍 방식으로 워크시트 선택](how-to-programmatically-select-worksheets.md)
- [방법: 프로그래밍 방식으로 통합 문서에 새 워크시트 추가](how-to-programmatically-add-new-worksheets-to-workbooks.md)
- [워크시트 호스트 항목](worksheet-host-item.md)
- [Office 프로젝트의 개체에 대 한 전역 액세스](global-access-to-objects-in-office-projects.md)
- [호스트 항목 및 호스트 컨트롤의 프로그래밍에 대 한 제한 사항](programmatic-limitations-of-host-items-and-host-controls.md)
