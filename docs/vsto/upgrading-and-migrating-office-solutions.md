---
title: Office 솔루션 업그레이드 및 마이그레이션
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office applications [Office development in Visual Studio], upgrading
- Office projects [Office development in Visual Studio], upgrading
- upgrading applications [Office development in Visual Studio]
- upgrading Office solutions in Visual Studio
- migrating Office solutions in Visual Studio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 5e421d6e4ee94d9974c0a0583db1fb495c72593e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79416538"
---
# <a name="upgrade-and-migrate-office-solutions"></a>Office 솔루션 업그레이드 및 마이그레이션
  Microsoft Office 프로젝트를 이전 버전 Visual Studio에서 만든 경우 현재 버전의 Visual Studio에서 사용하려면 프로젝트를 업그레이드해야 합니다. Microsoft Office 프로젝트를 업그레이드하려면 Microsoft Office 개발자 도구가 포함된 Visual Studio 버전에서 프로젝트를 엽니다. Microsoft Office 개발자 도구를 포함 하는 Visual Studio 버전에 대 한 자세한 내용은 [Office 솔루션을 개발할 수 있도록 컴퓨터 구성](../vsto/configuring-a-computer-to-develop-office-solutions.md)을 참조 하세요.

[!include[Add-ins note](includes/addinsnote.md)]

> [!NOTE]
> Visual Studio에서는 이전 버전 Visual Studio에서 만든 InfoPath 양식 템플릿 프로젝트를 업그레이드할 수 없습니다. 이러한 형식의 프로젝트는 현재 Visual Studio 릴리스에서 지원되지 않습니다.

## <a name="changes-to-upgraded-projects"></a>업그레이드 된 프로젝트의 변경 내용
 Microsoft Office 프로젝트를 업그레이드하면 Visual Studio에서는 다음 항목을 대상으로 지정하도록 프로젝트를 수정합니다.

- Visual Studio 2010 Tools for Office runtime. 자세한 내용은 [Visual Studio Tools for Office 런타임 개요](../vsto/visual-studio-tools-for-office-runtime-overview.md)를 참조 하세요.

- 현재 어셈블리 참조.

- 프로젝트 형식에서 지원되는 .NET Framework 버전(Visual Studio 2013으로만 업그레이드하는 경우)

- 프로젝트 형식에서 지원되는 Microsoft Office 버전(Visual Studio 2013으로만 업그레이드하는 경우)

## <a name="assembly-references"></a>어셈블리 참조
 Visual Studio에서는 프로젝트에서 다음 어셈블리 참조를 업그레이드합니다.

- Microsoft Office PIA(주 Interop 어셈블리)

- [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]의 어셈블리. 이러한 어셈블리에 대 한 자세한 내용은 [Visual Studio Tools for Office 런타임 개요](../vsto/visual-studio-tools-for-office-runtime-overview.md)를 참조 하세요.

- 종속 어셈블리의 새 버전 또는 업데이트 버전.

## <a name="targeted-net-framework"></a>대상 .NET Framework
 프로젝트를 Visual Studio 2013으로 업그레이드하는 경우 Visual Studio에서 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] 또는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]를 대상으로 하도록 프로젝트를 수정합니다. 프로젝트 대상으로 지정된 .NET Framework 버전은 컴퓨터에 설치된 Office 버전에 따라 다릅니다. [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 이(가) 설치되어 있으면 Visual Studio에서는 [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]을(를) 대상으로 지정하도록 프로젝트를 수정합니다. 이외의 경우에는 Visual Studio에서는 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)]을(를) 대상으로 지정하도록 프로젝트를 수정합니다.

> [!NOTE]
> 개발 및 최종 사용자 컴퓨터에서 대상이 변경된 솔루션을 실행하려면 몇몇 추가 단계를 수행해야 할 수 있고 프로젝트가 특정 기능을 사용할 경우 프로젝트는 더 이상 컴파일되지 않습니다. 자세한 내용은 [.NET Framework 4 이상으로 Office 솔루션 마이그레이션](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)을 참조 하세요.

 Office 프로젝트에서 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] 이상을 대상으로 지정하면 .NET Framework 3.5를 대상으로 지정할 때는 사용할 수 없는 일부 기능을 사용할 수 있습니다. 자세한 내용은 [Office 솔루션 디자인 및 만들기](../vsto/designing-and-creating-office-solutions.md)를 참조 하세요.

## <a name="targeted-office-application"></a>대상 Office 응용 프로그램
 Office 프로젝트를 Visual Studio 2013으로 업그레이드하는 경우 Visual Studio에서 문서 수준 사용자 지정 프로젝트 또는 VSTO 추가 기능 프로젝트와 같은 프로젝트 형식에서 지원되는 Microsoft Office 버전을 대상으로 지정하도록 프로젝트를 수정합니다.

 Visual Studio 2013의 Office 프로젝트는 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] 및 [!INCLUDE[office14_long](../vsto/includes/office14-long-md.md)] 애플리케이션을 대상으로 할 수 있습니다. Visual Studio에서 설치된 최신 버전의 Office를 대상으로 하도록 프로젝트를 수정합니다. 해당 버전의 Office가 설치되어 있지 않으면 Visual Studio에서 프로젝트를 업그레이드하지 않습니다.

> [!NOTE]
> 이상 버전으로 VSTO 추가 기능 프로젝트를 업그레이드 하는 경우 [!INCLUDE[Office_15_short](../vsto/includes/office-15-short-md.md)] `ThisAddIn_Startup` vsto 추가 기능의 이벤트 처리기에 응용 프로그램의 문서에 액세스 하는 코드가 포함 되어 있지 않은지 확인 합니다. 자세한 내용은 [Office 응용 프로그램이 시작 될 때 문서 액세스](../vsto/programming-vsto-add-ins.md#AccessingDocuments)를 참조 하세요.

 문서 수준 사용자 지정의 경우는 [!INCLUDE[vs_current_short](../sharepoint/includes/vs-current-short-md.md)] 프로젝트에서 확장명이 *.xls* 또는 *.doc* 인 문서와 같은 이진 형식 문서를 Office Open XML 형식으로 변환 합니다. Open XML에 대 한 자세한 내용은 [새 파일 이름 확장명 및 OPEN xml 형식 소개](https://support.office.com/en-nz/article/Introduction-to-new-file-name-extensions-eca81dcb-5626-4e5b-8362-524d13ae4ec1)를 참조 하세요.

> [!NOTE]
> 스마트 태그는 Excel 2010 및 Word 2010에서 더 이상 사용되지 않습니다. 따라서 솔루션에 스마트 태그가 사용되는 경우 Visual Studio 2013 또는 Visual Studio 2015에서 솔루션을 테스트 및 디버그하기 전에 스마트 태그를 제거해야 합니다.

## <a name="upgrade-microsoft-office-2003-projects"></a>Microsoft Office 2003 프로젝트 업그레이드
 Microsoft Office 2003을 대상으로 하는 문서 수준 사용자 지정 및 VSTO 추가 기능을 업그레이드하려면 몇 가지 사항을 추가로 고려해야 합니다.

### <a name="document-level-projects"></a>문서 수준 프로젝트
 프로젝트의 문서에 Windows Forms 컨트롤이 있으면 프로젝트를 업그레이드하기 전에 Visual Studio 2005 Tools for Office Second Edition Runtime도 설치해야 합니다. 프로젝트를 업그레이드하기 전에 이 런타임 버전이 개발 컴퓨터에 설치되어 있지 않으면 업그레이드된 프로젝트에 컴파일 또는 런타임 오류가 포함될 수 있습니다. 프로젝트 업그레이드를 완료한 후 다른 Office 솔루션에서 사용되고 있지 않으면 개발 컴퓨터에서 Visual Studio 2005 Tools for Office Second Edition Runtime을 제거할 수 있습니다. 이 런타임 버전은 Microsoft 다운로드 센터의 [Microsoft Visual Studio 2005 Tools for Office Second Edition Runtime(VSTO 2005 SE)(x86)](https://www.microsoft.com/download/details.aspx?id=2392)에서 재배포 가능 패키지로 다운로드할 수 있습니다.

### <a name="vsto-add-in-projects"></a>VSTO 추가 기능 프로젝트
 원래 프로젝트에 대한 솔루션 파일에 VSTO 추가 기능을 설치하도록 구성된 설치 프로그램 또는 InstallShield Limited Edition 프로젝트가 포함된 경우 Visual Studio에서 프로젝트를 업그레이드하지만 프로젝트를 추가로 변경하지 않습니다. 계속해서 Windows Installer 파일을 사용하여 VSTO 추가 기능을 배포하려면 [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)], Visual Studio 2010 Tools for Office Runtime 및 선택적으로 VSTO 추가 기능에서 참조되는 주 Interop 어셈블리와 같은 새로운 필수 조건을 설치하도록 설치 프로그램 또는 InstallShield Limited Edition 프로젝트를 수정해야 합니다. 자세한 내용은 [Windows Installer를 사용 하 여 Office 솔루션 배포](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)를 참조 하세요.

 ClickOnce를 사용하여 VSTO 추가 기능을 배포하려면 설치 프로그램 또는 InstallShield Limited Edition 프로젝트를 완전히 삭제할 수 있습니다. ClickOnce를 사용 하 여 VSTO 추가 기능을 배포 하는 방법에 대 한 자세한 내용은 [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)를 참조 하세요.

## <a name="see-also"></a>참조
- [방법: Office 솔루션 업그레이드](https://msdn.microsoft.com/a269e539-b717-4680-a568-2152b070347e)
- [.NET Framework 4 이상으로 Office 솔루션 마이그레이션](../vsto/migrating-office-solutions-to-the-dotnet-framework-4-or-later.md)
- [옵션 대화 상자, 프로젝트 업그레이드](../vsto/project-upgrade-options-dialog-box.md)
