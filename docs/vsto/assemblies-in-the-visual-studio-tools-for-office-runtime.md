---
title: Visual Studio Tools for Office 런타임의 어셈블리
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio Tools for Office runtime, assemblies
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b2fc47aa917fa9c9d5351fd313ec46ae4aaa0664
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918790"
---
# <a name="assemblies-in-the-visual-studio-tools-for-office-runtime"></a>Visual Studio Tools for Office 런타임의 어셈블리
  Office 프로젝트를 만들면 Visual Studio에서 프로젝트 형식 및 프로젝트의 대상 .NET Framework에 사용되는 [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] 어셈블리에 자동으로 참조를 추가합니다. .NET Framework 3.5, [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]및 [!INCLUDE[net_v45](includes/net-v45-md.md)]용 Office 확장에는 각각 다른 어셈블리가 있습니다. Office 확장에 대 한 자세한 내용은 [Visual Studio Tools for Office 런타임 개요](visual-studio-tools-for-office-runtime-overview.md)를 참조 하세요.

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-4-and-the-net_v45"></a>.NET Framework 4 및 용 Office 확장의 어셈블리 [!INCLUDE[net_v45](includes/net-v45-md.md)]
 다음 표에는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 및 [!INCLUDE[net_v45](includes/net-v45-md.md)]용 Office 확장에 포함된 어셈블리가 나열되어 있습니다. 이러한 어셈블리의 네임 스페이스 및 형식에 대 한 설명서는 [Visual Studio&#41;에서 관리 되는 참조 &#40;Office 개발 ](managed-reference-office-development-in-visual-studio.md)을 참조 하세요.

|어셈블리 이름|설명|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.dll|다음과 같은 형식을 제공합니다.<br /><br /> -리본 사용자 지정 및 스마트 태그를 만들기 위한 형식입니다. **참고:**      스마트 태그는 및에서 더 이상 사용 되지 않습니다 [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-문서 수준 사용자 지정 및 VSTO 추가 기능의 사용자 지정 작업창에서 작업 창을 만들기 위한 형식입니다.|
|Microsoft.Office.Tools.Excel.dll|Excel 프로젝트에 대한 호스트 항목 및 호스트 컨트롤을 나타내는 인터페이스 및 지원 형식을 제공합니다. 자세한 내용은 [확장 개체를 사용 하 여 Excel 자동화](automating-excel-by-using-extended-objects.md)를 참조 하세요.|
|Microsoft.Office.Tools.Outlook.dll|Outlook VSTO 추가 기능에서 사용자 지정 양식 영역을 만드는 데 사용할 수 있는 형식을 제공합니다.|
|Microsoft.Office.Tools.Word.dll|Word 프로젝트에 대한 호스트 항목 및 호스트 컨트롤을 나타내는 인터페이스 및 지원 형식을 제공합니다. 자세한 내용은 [확장 개체를 사용 하 여 Word 자동화](automating-word-by-using-extended-objects.md)를 참조 하세요.|
|Microsoft.Office.Tools.v4.0.Framework.dll|다음과 같은 형식을 제공합니다.<br /><br /> -Visual Studio Tools for Office 런타임에 의해 throw 될 수 있는 예외입니다.<br />-Outlook 양식 영역을 만들 때 사용할 수 있는 특성입니다.|
|Microsoft.Office.Tools.dll|Visual Studio Tools for Office 런타임 인프라의 일부이며 코드에서 직접 사용할 수 없도록 되어 있는 형식을 제공합니다.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.dll|다음과 같은 형식을 제공합니다.<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 문서 수준 사용자 지정에서 데이터 개체를 캐시 하는 데 사용할 수 있는 특성 및 인터페이스입니다. 자세한 내용은 [데이터 캐시](caching-data.md)를 참조 하세요.<br />- <xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> Office 솔루션에 대 한 ClickOnce 설치 관리자의 최종 단계로 추가 설치 단계를 실행 하기 위해 구현할 수 있는 인터페이스입니다. 자세한 내용은 [ClickOnce를 사용 하 여 Office 솔루션 배포](deploying-an-office-solution-by-using-clickonce.md)를 참조 하세요.<br />-Visual Studio Tools for Office 런타임에 의해 throw 될 수 있는 예외입니다.<br />-Visual Studio Tools for Office 런타임 인프라의 일부 이며 코드에서 직접 사용 하기 위한 것이 아닙니다.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.dll|다음과 같은 형식을 제공합니다.<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 사용자 지정 어셈블리를 문서에 연결 하 고 문서에서 캐시 된 데이터에 액세스 하는 데 사용할 수 있는 클래스입니다. 자세한 내용은 [ServerDocument 클래스를 사용 하 여 서버에서 문서 관리](managing-documents-on-a-server-by-using-the-serverdocument-class.md)를 참조 하세요.<br />-문서 수준 사용자 지정에서 캐시 된 데이터의 계층 구조를 나타내는 여러 클래스입니다. 자세한 내용은 [서버에 있는 문서의 데이터 액세스](accessing-data-in-documents-on-the-server.md)를 참조 하세요.|

 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 또는 [!INCLUDE[net_v45](includes/net-v45-md.md)] 를 대상으로 하는 프로젝트도 다음과 같은 어셈블리를 참조합니다. 이러한 어셈블리는 [!INCLUDE[vsto_runtime](includes/vsto-runtime-md.md)] 재배포 가능 패키지의 일부가 아닙니다. 대신 솔루션과 함께 배포되어야 하는 종속 어셈블리입니다. 기본적으로 프로젝트에 대한 빌드 출력 폴더에 복사되며, 이러한 어셈블리의 **로컬 복사** 속성은 **True**로 설정됩니다. ClickOnce를 사용하여 프로젝트를 배포하는 경우 이러한 어셈블리는 생성된 패키지에 포함 됩니다.

|어셈블리 이름|설명|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v4.0.Utilities.dll|VSTO 추가 기능 프로젝트에서 생성된 `ThisAddIn` 클래스 및 모든 프로젝트에서 생성된 리본 클래스에 대해 기본 클래스를 제공합니다.|
|Microsoft.Office.Tools.Excel.v4.0.Utilities.dll|다음과 같은 형식을 제공합니다.<br /><br /> - `ThisWorkbook` `Sheet` Excel 용 문서 수준 프로젝트에서 생성 된 및 클래스의 기본 클래스입니다.<br />-Excel 프로젝트의 워크시트에서 사용할 수 있는 컨트롤을 Windows Forms 합니다.|
|Microsoft.Office.Tools.Outlook.v4.0.Utilities.dll|Outlook 프로젝트에서 생성된 `ThisAddIn` 및 양식 영역 클래스에 대해 기본 클래스를 제공합니다.|
|Microsoft.Office.Tools.Word.v4.0.Utilities.dll|다음과 같은 형식을 제공합니다.<br /><br /> - `ThisDocument` Word에 대 한 문서 수준 프로젝트에서 생성 된 클래스의 기본 클래스입니다.<br />-Word 프로젝트의 문서에서 사용할 수 있는 컨트롤을 Windows Forms 합니다.|

## <a name="assemblies-in-the-office-extensions-for-the-net-framework-35"></a>.NET Framework 3.5 용 Office 확장의 어셈블리
 다음 표에는 .NET Framework 3.5용 Office 확장에 포함된 어셈블리가 나열되어 있습니다. 이러한 어셈블리의 네임 스페이스 및 클래스에 대 한 설명서는 Visual Studio 2008 설명서의 다음 참조 섹션을 참조 하세요 [http://go.microsoft.com/fwlink/?LinkId=160658](managed-reference-office-development-in-visual-studio.md) .

|어셈블리 이름|설명|
|-------------------|-----------------|
|Microsoft.Office.Tools.Common.v9.0.dll|다음과 같은 형식을 제공합니다.<br /><br /> -VSTO 추가 기능에 대 한 Microsoft.<br />-리본 사용자 지정 및 스마트 태그를 만들기 위한 클래스입니다. **참고:**      스마트 태그는 및에서 더 이상 사용 되지 않습니다 [!INCLUDE[Excel_14_short](includes/excel-14-short-md.md)] [!INCLUDE[Word_14_short](includes/word-14-short-md.md)] .<br />-문서 수준 사용자 지정에서 작업 창을 만들기 위한 클래스 및 VSTO 추가 기능의 사용자 지정 작업창|
|Microsoft.Office.Tools.Excel.v9.0.dll|Excel 솔루션에 대한 호스트 항목 및 호스트 컨트롤을 제공합니다. 자세한 내용은 [확장 개체를 사용 하 여 Excel 자동화](automating-excel-by-using-extended-objects.md)를 참조 하세요.|
|Microsoft.Office.Tools.Outlook.v9.0.dll|Outlook VSTO 추가 기능에서 사용자 지정 양식 영역을 만드는 데 사용할 수 있는 클래스를 제공합니다.|
|Microsoft.Office.Tools.Word.v9.0.dll|Word 솔루션에 대한 호스트 항목 및 호스트 컨트롤을 제공합니다. 자세한 내용은 [확장 개체를 사용 하 여 Word 자동화](automating-word-by-using-extended-objects.md)를 참조 하세요.|
|Microsoft.Office.Tools.v9.0.dll|다음과 같은 형식을 제공합니다.<br /><br /> -문서 수준 사용자 지정의 호스트 컨트롤에 대 한 데이터 바인딩 기능을 제공 하는 [RemoteBindableComponent](/previous-versions/visualstudio/visual-studio-2008/bb546360(v=vs.90)) 클래스입니다.<br />-Visual Studio Tools for Office 런타임 인프라의 일부 이며 코드에서 직접 사용 하기 위한 것이 아닙니다.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v9.0.dll|다음과 같은 형식을 제공합니다.<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> 문서 수준 사용자 지정에서 데이터 개체를 캐시 하는 데 사용할 수 있는 특성 및 인터페이스입니다. 자세한 내용은 [데이터 캐시](caching-data.md)를 참조 하세요.<br />-Visual Studio Tools for Office 런타임에 의해 throw 될 수 있는 예외입니다.<br />-Visual Studio Tools for Office 런타임 인프라의 일부 이며 코드에서 직접 사용 하기 위한 것이 아닙니다.|
|Microsoft.VisualStudio.Tools.Applications.Runtime.v10.0.dll|<xref:Microsoft.VisualStudio.Tools.Applications.Deployment.IAddInPostDeploymentAction> 인터페이스로, Office 솔루션에 대한 ClickOnce 설치 관리자의 최종 단계로 추가 설치 단계를 실행하기 위해 구현할 수 있습니다. 자세한 내용은 [고급 Office 솔루션 배포](/previous-versions/visualstudio/visual-studio-2010/dd234217(v=vs.100))를 참조 하세요.|
|Microsoft.VisualStudio.Tools.Applications.ServerDocument.v10.0.dll|다음과 같은 형식을 제공합니다.<br /><br /> - <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> 프로그래밍 방식으로 문서에 사용자 지정 어셈블리를 연결 하 고 문서에서 캐시 된 데이터에 액세스 하는 데 사용할 수 있는 클래스입니다. 자세한 내용은 [ServerDocument 클래스를 사용 하 여 서버에서 문서 관리](managing-documents-on-a-server-by-using-the-serverdocument-class.md)를 참조 하세요.<br />-문서 수준 사용자 지정에서 캐시 된 데이터의 계층 구조를 나타내는 여러 클래스입니다. 자세한 내용은 [서버에 있는 문서의 데이터 액세스](accessing-data-in-documents-on-the-server.md)를 참조 하세요.|
|Microsoft.VisualStudio.Tools.Office.Runtime.v10.0.dll|다음과 같은 형식을 제공합니다.<br /><br /> -.NET Framework 3.5를 대상으로 하는 Office 솔루션에 신뢰를 부여 하는 사용자 포함 목록 항목을 만드는 데 사용할 수 있는 VisualStudio 및 UserInclusionList 클래스입니다 .이 클래스를 사용할 수 있습니다.<br />-Visual Studio Tools for Office 런타임 인프라의 일부 이며 코드에서 직접 사용 하기 위한 것이 아닙니다.|

## <a name="see-also"></a>참조
- [Visual Studio Tools for Office 런타임 개요](visual-studio-tools-for-office-runtime-overview.md)
- [Visual Studio Tools for Office 런타임 설치 시나리오](visual-studio-tools-for-office-runtime-installation-scenarios.md)
