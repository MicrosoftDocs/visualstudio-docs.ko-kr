---
title: .NET Framework를 대상으로 하는 Office 프로젝트의 변경 내용 디자인
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio 2010, what's new
- what's new [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 334344a2ffec5e084cb2e199a128b4583266af9f
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810512"
---
# <a name="changes-to-the-design-of-office-projects-that-target-the-net-framework-4-or-the-net-framework-45"></a>.NET Framework 4 또는 .NET Framework 4.5를 대상으로 하는 Office 프로젝트의 디자인 변경
  [!INCLUDE[vs_dev10_long](../sharepoint/includes/vs-dev10-long-md.md)]부터 Visual Studio에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 Office 프로젝트의 디자인에 몇 가지 변경 사항이 도입되었습니다. 이전 버전의 Visual Studio에서 Office 프로젝트를 사용하는 데 익숙한 경우 .NET Framework 4.0 이상의 버전을 대상으로 하는 Office 프로젝트를 개발하기 전에 이러한 변경 사항을 알고 있어야 합니다. 기본적으로 Visual Studio 2013 이상을 사용하여 만드는 모든 프로젝트는 .NET Framework 4.0 이상을 대상으로 합니다.

 다음 섹션에서는 이러한 Office 프로젝트 디자인 변경 사항에 대해 설명합니다.

## <a name="understand-the-interface-based-design-of-the-visual-studio-2010-tools-for-office-runtime"></a>Visual Studio 2010 Tools for Office runtime의 인터페이스 기반 디자인 이해
 이상을 대상으로 하는 Office 프로젝트를 개발 하는 경우 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] Visual Studio 2010 Tools For Office runtime에서 사용 하는 대부분의 형식은 인터페이스입니다. 이는 이러한 형식이 클래스인 이전 버전의 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]에서 크게 변경된 사항입니다. 예를 들어 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 경우 <xref:Microsoft.Office.Tools.Excel.Worksheet> 및 <xref:Microsoft.Office.Tools.Word.Document> 형식은 클래스가 아닌 인터페이스입니다. 자세한 내용은 [Visual Studio Tools for Office 런타임 개요](../vsto/visual-studio-tools-for-office-runtime-overview.md)를 참조 하세요.

 이전 버전의 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]에서 직접 인스턴스화할 수 있는 모든 형식의 경우 이제 `Globals.Factory` 개체의 메서드를 사용하여 이러한 형식의 인스턴스를 가져옵니다. 예를 들어 <xref:Microsoft.Office.Tools.Excel.SmartTag> 인터페이스를 구현하는 개체를 가져오려면 `Globals.Factory.CreateSmartTag` 메서드를 사용합니다. 자세한 내용은 다음 항목을 참조하세요.

- [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Excel 및 Word 프로젝트를 업데이트 합니다.](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Office 프로젝트에서 리본 메뉴 사용자 지정 업데이트](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Outlook 프로젝트에서 양식 영역 업데이트](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

### <a name="new-base-classes-in-office-projects"></a>Office 프로젝트의 새 기본 클래스
 Visual Studio 2010 Tools for Office runtime의 새로운 인터페이스 기반 디자인은 Office 프로젝트에서 생성 된 클래스 (예:, 및)에 영향을 줍니다 `ThisDocument` `ThisWorkbook` `ThisAddIn` . .NET Framework 3.5 및 이전 버전을 대상으로 하는 Office 프로젝트에서 이러한 생성된 클래스는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]에서 클래스(예: `Microsoft.Office.Tools.Word.Document`, `Microsoft.Office.Tools.Excel.Worksheet` 및 `Microsoft.Office.Tools.AddIn`)로부터 파생됩니다. [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 하는 프로젝트에서 이러한 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 클래스는 이제 인터페이스입니다. 따라서 Office 프로젝트에서 생성된 클래스는 더 이상 해당 클래스에서 구현을 파생시킬 수 없습니다. 대신 생성된 클래스는 <xref:Microsoft.Office.Tools.Word.DocumentBase>, <xref:Microsoft.Office.Tools.Excel.WorksheetBase>및 <xref:Microsoft.Office.Tools.AddInBase>와 같은 새 기본 클래스에서 파생됩니다. 자세한 내용은 [VSTO 추가 기능 프로그래밍](../vsto/programming-vsto-add-ins.md) 및 [문서 수준 사용자 지정 프로그래밍](../vsto/programming-document-level-customizations.md)을 참조 하세요.

 기본 클래스는 [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] 재배포 가능 패키지의 일부가 아닙니다. 대신 Visual Studio에 포함된 유틸리티 어셈블리에서 정의됩니다. 이러한 어셈블리는 Office 프로젝트를 빌드할 때 출력 폴더에 복사되고 솔루션과 함께 배포되어야 합니다. 유틸리티 어셈블리에 대 한 자세한 내용은 [Visual Studio Tools for Office 런타임의 어셈블리](../vsto/assemblies-in-the-visual-studio-tools-for-office-runtime.md)를 참조 하세요.

## <a name="breaking-changes-in-office-projects-that-are-retargeted-to-the-net-framework-4"></a>.NET Framework 4로 대상이 변경 되는 Office 프로젝트의 주요 변경 내용
 다음 표에는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상으로 대상이 변경되는 Office 프로젝트에서 경험할 수 있는 주요 변경 내용이 나와 있습니다. 자세한 내용은 [.NET Framework 4 이상으로 Office 솔루션 마이그레이션](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)을 참조 하세요.

|주요 변경 내용|결과|
|---------------------|-----------------|
|<xref:System.Security.SecurityTransparentAttribute> 는 Office 프로젝트에서 더 이상 사용되거나 지원되지 않습니다.|Visual Studio 2008에서 업그레이드하는 Office 프로젝트의 AssemblyInfo 코드 파일에서 이 특성을 제거해야 합니다. 자세한 내용은 [.NET Framework 4로 마이그레이션하는 Office 프로젝트를 실행 하는 데 필요한 변경 사항 또는 4.5 .NET Framework](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)를 참조 하세요.|
|**ExcelLocale1033Attribute** 는 더 이상 Excel 프로젝트에서 사용 되거나 지원 되지 않습니다.|Excel 프로젝트의 *AssemblyInfo* 코드 파일에서이 특성을 제거 해야 합니다. 자세한 내용은 [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Excel 및 Word 프로젝트 업데이트](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)를 참조 하세요.|
|**리본(비주얼 디자이너)** 프로젝트 항목의 프로그래밍 모델이 변경되었습니다.|프로젝트에서 모든 리본 항목에 대한 코드 숨김 파일을 수정해야 합니다. 또한 런타임에 리본 컨트롤을 인스턴스화하거나, 리본 이벤트를 처리하거나, 리본 구성 요소의 위치를 프로그래밍 방식으로 설정하는 모든 코드를 수정해야 합니다. 자세한 내용은 [.NET Framework 4로 마이그레이션하는 Office 프로젝트의 리본 사용자 지정 업데이트 또는 4.5 .NET Framework](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)를 참조 하세요.|
|Outlook 양식 영역의 프로그래밍 모델이 변경되었습니다.|프로젝트의 모든 양식 영역에 대한 코드 숨김 파일과 런타임에 특정 양식 영역 클래스를 인스턴스화하는 모든 코드를 수정해야 합니다. 자세한 내용은 [.NET Framework 4로 마이그레이션하는 Outlook 프로젝트에서 양식 영역 업데이트 또는 4.5 .NET Framework](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)를 참조 하세요.|
|Excel 및 Word 프로젝트에서 스마트 태그에 대한 프로그래밍 모델이 변경되었습니다. [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 및 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]에서는 스마트 태그가 사용되지 않습니다.|솔루션에서 스마트 태그를 사용하는 경우 프로젝트를 빌드할 때 오류가 발생합니다. 스마트 태그가 [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)] 및 [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)]에서 더 이상 사용되지 않기 때문에 [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] 이상에서 솔루션을 테스트하고 디버그하려면 태그를 제거해야 합니다.|
|`GetVstoObject` 및 `HasVstoObject` 메서드의 구문이 변경되었습니다.|PIA(주 Interop 어셈블리)로부터 네이티브 개체에서 이러한 메서드에 액세스할 때 `Globals.Factory` 개체를 이러한 메서드에 전달해야 합니다. 또는 프로젝트에서 `Globals.Factory` 속성에 의해 반환되는 개체에서 이러한 메서드에 액세스할 수 있습니다. 자세한 내용은 [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Excel 및 Word 프로젝트 업데이트](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)를 참조 하세요.|
|Word 콘텐츠 컨트롤의 이벤트가 새 대리자와 연결됩니다.|Word 콘텐츠 컨트롤의 이벤트를 처리하는 모든 코드를 수정하여 새 대리자를 지정해야 합니다. 자세한 내용은 [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Excel 및 Word 프로젝트 업데이트](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)를 참조 하세요.|
|`OLEObject` 및 `OLEControl` 클래스의 이름이 변경되었습니다.|이러한 클래스의 인스턴스를 사용하는 모든 코드를 수정하여 <xref:Microsoft.Office.Tools.Excel.ControlSite> 또는 <xref:Microsoft.Office.Tools.Word.ControlSite> 개체를 대신 사용해야 합니다. 자세한 내용은 [.NET Framework 4 또는 .NET Framework 4.5으로 마이그레이션하는 Excel 및 Word 프로젝트 업데이트](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)를 참조 하세요.|
|, N, 및과 같은 호스트 항목 클래스는 `ThisWorkbook` `Sheet` *n* `ThisDocument` `ThisAddIn` `Dispose` 재정의할 수 있는 메서드를 더 이상 제공 하지 않습니다.|`Dispose` 메서드 재정의의 모든 코드를 `ThisAddIn_Shutdown`과 같은 호스트 항목 클래스의 `Shutdown` 이벤트 처리기로 이동하고 호스트 항목 클래스에서 `Dispose` 메서드 재정의를 제거해야 합니다.|

## <a name="see-also"></a>추가 정보
- [.NET Framework 4 이상으로 Office 솔루션 마이그레이션](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [Office 개발의 새로운 기능](/previous-versions/86bkz018(v=vs.110))
- [Visual Studio Tools for Office 런타임 개요](../vsto/visual-studio-tools-for-office-runtime-overview.md)