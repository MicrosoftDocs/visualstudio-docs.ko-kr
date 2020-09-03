---
title: VSTO 추가 기능에 대 한 레지스트리 항목
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- LoadBehavior entry
- add-ins [Office development in Visual Studio], registry entries
- registry keys [Office development in Visual Studio]
- application-level add-ins [Office development in Visual Studio], registry entries
- registry entries [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: b02b50c42692ec2fd455358df5157e0b8481562b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "79416525"
---
# <a name="registry-entries-for-vsto-add-ins"></a>VSTO 추가 기능에 대 한 레지스트리 항목
  Visual Studio를 사용하여 만든 VSTO 추가 기능을 배포할 때에는 특정 레지스트리 항목 집합을 만들어야 합니다. 이러한 레지스트리 항목은 Microsoft Office 애플리케이션에서 VSTO 추가 기능을 찾아 로드할 수 있는 정보를 제공합니다.

 [!INCLUDE[appliesto_allapp](../vsto/includes/appliesto-allapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 프로젝트를 빌드할 때 Visual Studio에서는 VSTO 추가 기능을 쉽게 실행하고 디버그할 수 있도록 개발 컴퓨터에서 이들 레지스트리 항목을 만듭니다. ClickOnce를 사용 하 여 VSTO 추가 기능을 배포 하는 경우 레지스트리 항목이 자동으로 최종 사용자 컴퓨터에 생성 됩니다. Windows Installer를 사용 하 여 VSTO 추가 기능을 배포 하는 경우 최종 사용자 컴퓨터에 레지스트리 항목을 만들도록 InstallShield 제한 된 버전 프로젝트를 구성 해야 합니다.

 VSTO 추가 기능에 대한 로드 프로세스 중 레지스트리 항목을 사용하는 방법에 대한 자세한 내용은 [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)를 참조하세요.

> [!NOTE]
> 이 항목에서 *추가 기능 ID* 텍스트는 VSTO 추가 기능의 고유한 ID를 나타냅니다. 기본적으로 ID는 VSTO 추가 기능 어셈블리의 이름입니다.

## <a name="register-vsto-add-ins-for-the-current-user-vs-all-users"></a>현재 사용자 및 모든 사용자에 대 한 VSTO 추가 기능 등록
 VSTO 추가 기능을 설치할 때 두 가지 방법으로 등록할 수 있습니다.

- 현재 사용자 전용 (즉, VSTO 추가 기능이 설치 될 때 컴퓨터에 로그온 한 사용자만 사용할 수 있음). 이 경우 레지스트리 항목은 **HKEY_CURRENT_USER**아래에 생성 됩니다.

- 모든 사용자에 대해 (즉, 컴퓨터에 로그온 하는 모든 사용자가 VSTO 추가 기능을 사용할 수 있음) 이 경우 레지스트리 항목은 **HKEY_LOCAL_MACHINE**아래에 생성 됩니다.

  Visual Studio를 사용하여 만드는 모든 VSTO 추가 기능은 현재 사용자용으로 등록할 수 있습니다. 그러나 특정 시나리오에서는 VSTO 추가 기능을 모든 사용자용으로만 등록할 수 있습니다. 이러한 시나리오는 컴퓨터의 Microsoft Office 버전과 VSTO 추가 기능이 배포된 방법에 따라 다릅니다.

### <a name="deployment-type"></a>배포 유형
 ClickOnce를 사용하여 VSTO 추가 기능을 배포하는 경우 VSTO 추가 기능을 현재 사용자 전용으로 등록할 수 있습니다. 이는 ClickOnce에서 **HKEY_CURRENT_USER**하는 키 생성만 지원 하기 때문입니다. 컴퓨터의 모든 사용자에 대해 VSTO 추가 기능을 등록하려면 Windows Installer를 사용하여 VSTO 추가 기능을 배포해야 합니다. 이러한 배포 유형에 대 한 자세한 내용은 ClickOnce를 [사용 하 여 office 솔루션 배포](../vsto/deploying-an-office-solution-by-using-clickonce.md) 및 [Windows Installer를 사용 하 여 office 솔루션 배포](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)를 참조 하세요.

## <a name="registry-entries"></a>레지스트리 항목
 필요한 VSTO 추가 기능 레지스트리 항목은 다음 레지스트리 키 아래에 있습니다. 여기서 *루트* 는 현재 사용자 또는 모든 사용자 용으로 설치 된 경우에 따라 **HKEY_CURRENT_USER** 또는 **HKEY_LOCAL_MACHINE** .

|Office 응용 프로그램|구성 경로|
|------------------|------------------|
|Visio|*Root*\Software\Microsoft \\ *Visio*\addins \\ *추가 기능 ID*|
|기타 모든|*Root*\Software\Microsoft\Office \\ *Office 응용 프로그램 이름*\addins \\ *추가 기능 ID*|

> [!NOTE]
> 설치 관리자가 64 비트 Windows의 모든 사용자를 대상으로 하는 경우 두 개의 레지스트리 항목을 포함 하는 것이 좋습니다. 하나는 HKEY_LOCAL_MACHINE \Software\Microsoft, 다른 하나는 HKEY_LOCAL_MACHINE \Software \\ **WOW6432Node**\Microsoft hive에 있습니다. 이는 사용자가 컴퓨터에서 32 비트 또는 64 비트 버전의 Office를 사용할 수 있기 때문입니다.
>
>설치 관리자가 현재 사용자를 대상으로 하는 경우에는 HKEY_CURRENT_USER \Software 경로를 공유 하므로 WOW6432Node에를 설치할 필요가 없습니다.
>
>자세한 내용은 [레지스트리에서 32 비트 및 64 비트 응용 프로그램 데이터](/windows/win32/sysinfo/32-bit-and-64-bit-application-data-in-the-registry) 를 참조 하세요.

 다음 테이블에는 이 레지스트리 키의 항목이 나열되어 있습니다.

|입력|형식|값|
|-----------|----------|-----------|
|**설명**|REG_SZ|필수 요소. VSTO 추가 기능에 대한 간략한 설명입니다.<br /><br /> 이 설명은 사용자가 Microsoft Office 애플리케이션의 **옵션** 대화 상자에 있는 **추가 기능** 창의 VSTO 추가 기능을 선택했을 때 표시됩니다.|
|**#B1**|REG_SZ|필수 요소. Microsoft Office 애플리케이션의 **COM 추가 기능** 대화 상자에 표시되는 VSTO 추가 기능에 대한 설명이 포함된 이름입니다. 기본값은 VSTO 추가 기능 ID입니다.|
|**LoadBehavior**|REG_DWORD|필수 요소. 애플리케이션에서 VSTO 추가 기능 및 VSTO 추가 기능의 현재 상태(로드 또는 언로드)를 로드하려고 할 때 지정하는 값입니다.<br /><br /> 기본적으로 이 항목은 시작 시 VSTO 추가 기능을 로드하도록 지정하는 3으로 설정됩니다. 자세한 내용은 [LoadBehavior values](#LoadBehavior)를 참조 하세요. **참고:**  사용자가 VSTO 추가 기능을 사용 하지 않도록 설정 하면 **HKEY_CURRENT_USER** 레지스트리 Hive에서 **LoadBehavior** 값이 수정 됩니다. 각 사용자에 대해 HKEY_CURRENT_USER hive의 **LoadBehavior** 값 값이 **HKEY_LOCAL_MACHINE** hive에 정의 된 기본 **LoadBehavior** 를 재정의 합니다.|
|**file:///**|REG_SZ|필수 요소. VSTO 추가 기능에 대한 배포 매니페스트의 전체 경로입니다. 경로는 로컬 컴퓨터, 네트워크 공유(UNC) 또는 웹 서버(HTTP)의 위치일 수 있습니다.<br /><br /> Windows Installer를 사용하여 솔루션을 배포하는 경우 **매니페스트** 경로에 접두사 **file:///** 을 추가해야 합니다. 또한이 경로 끝에 문자열 **&#124;vstolocal** (파이프 문자 **&#124;** 뒤에 **vstolocal**)를 추가 해야 합니다. 그러면 솔루션이 ClickOnce 캐시가 아니라 설치 폴더에서 로드됩니다. 자세한 내용은 [Windows Installer를 사용 하 여 Office 솔루션 배포](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md)를 참조 하세요. **참고:**  개발 컴퓨터에서 VSTO 추가 기능을 빌드할 때 Visual Studio에서 **&#124;vstolocal** 문자열을이 레지스트리 항목에 자동으로 추가 합니다.|

### <a name="registry-entries-for-outlook-form-regions"></a><a name="OutlookEntries"></a> Outlook 양식 영역에 대 한 레지스트리 항목
 Outlook용 VSTO 추가 기능에 사용자 지정 양식 영역을 만들 경우 추가 레지스트리 항목을 사용하여 Outlook에 양식 영역을 등록합니다. 이러한 항목은 양식 영역을 지원하는 각 메시지 클래스에 대한 다른 레지스트리 키 아래에 만들어집니다. 이러한 레지스트리 키는 다음 위치에 있습니다. 여기서 *Root* 는 **HKEY_CURRENT_USER** 또는 **HKEY_LOCAL_MACHINE**입니다.

 *Root*\Software\Microsoft\Office\Outlook\FormRegions \\ *message 클래스*

 모든 VSTO 추가 기능에서 다른 레지스트리 항목을 공유하는 것처럼, 프로젝트를 빌드할 때 Visual Studio는 개발 컴퓨터에 양식 영역 레지스트리 항목을 만듭니다. ClickOnce를 사용 하 여 VSTO 추가 기능을 배포 하는 경우 레지스트리 항목이 자동으로 최종 사용자 컴퓨터에 생성 됩니다. Windows Installer를 사용 하 여 VSTO 추가 기능을 배포 하는 경우 최종 사용자 컴퓨터에 레지스트리 항목을 만들도록 InstallShield 제한 된 버전 프로젝트를 구성 해야 합니다.

 양식 영역 레지스트리 항목에 대 한 자세한 내용은 [사용자 지정 양식에서 양식 영역의 위치 지정](/office/vba/outlook/Concepts/Creating-Form-Regions/specify-the-location-of-a-form-region-in-a-custom-form)을 참조 하세요. Outlook 양식 영역에 대 한 자세한 내용은 [outlook 양식 영역 만들기](../vsto/creating-outlook-form-regions.md)를 참조 하세요.

## <a name="loadbehavior-values"></a><a name="LoadBehavior"></a> LoadBehavior 값
 *Root*\Software\Microsoft\Office **LoadBehavior** \\ *응용 프로그램 이름*\Addins \\ *추가 기능 ID* 키 아래의 LoadBehavior 항목에는 VSTO 추가 기능의 런타임 동작을 지정 하는 값의 비트 조합이 포함 되어 있습니다. 가장 낮은 순서 비트(값 0과 1)는 VSTO 추가 기능이 현재 로드되었는지 여부를 나타냅니다. 다른 비트는 애플리케이션에서 VSTO 추가 기능을 로드하는 시기를 나타냅니다.

 일반적으로 **LoadBehavior** 항목은 VSTO 추가 기능이 최종 사용자 컴퓨터에 설치 된 경우 0, 3 또는 16 (10 진수)으로 설정 됩니다. VSTO 추가 기능을 빌드하거나 게시할 때, 기본적으로 Visual Studio는 VSTO 추가 기능의 **LoadBehavior** 항목을 3으로 설정합니다.

 다음 표에서는 **LoadBehavior** 항목의 가능한 모든 값을 모두 보여 줍니다. 이 표의 일부 설명은 VSTO 추가 기능 수동으로 또는 프로그래밍 방식으로 로드를 참조합니다. VSTO 추가 기능을 수동으로 로드하려면 애플리케이션의 **COM 추가 기능** 대화 상자에서 VSTO 추가 기능 옆에 있는 확인란을 선택합니다. VSTO 추가 기능을 프로그래밍 방식으로 로드하려면 <xref:Microsoft.Office.Core.COMAddIn.Connect%2A> 에 대한 VSTO 추가 기능을 나타내는 <xref:Microsoft.Office.Core.COMAddIn> 개체의 **P:Microsoft.Office.Core.COMAddIn.Connect**를 참조하세요.

|값(10 진수)|VSTO 추가 기능 상태|VSTO 추가 기능 로드 동작|설명|
|--------------------------|-------------------------|--------------------------------|-----------------|
|0|언로드됨|자동으로 로드하지 않음|애플리케이션이 VSTO 추가 기능을 자동으로 로드하지 않습니다. 사용자는 VSTO 추가 기능을 수동으로 로드하거나, VSTO 추가 기능을 프로그래밍 방식으로 로드할 수 있습니다.<br /><br /> VSTO 추가 기능이 성공적으로 로드되면 **LoadBehavior** 값은 0으로 유지되지만 **COM 추가 기능** 대화 상자의 VSTO 추가 기능 상태는 업데이트되어 VSTO 추가 기능이 로드된 것으로 나타납니다.|
|1|로드됨|자동으로 로드하지 않음|애플리케이션이 VSTO 추가 기능을 자동으로 로드하지 않습니다. 사용자는 VSTO 추가 기능을 수동으로 로드하거나, VSTO 추가 기능을 프로그래밍 방식으로 로드할 수 있습니다.<br /><br /> **COM 추가 기능** 대화 상자에 응용 프로그램이 시작 된 후 vsto 추가 기능이 로드 된 것으로 나타나지만, vsto 추가 기능은 수동으로 또는 프로그래밍 방식으로 로드 될 때까지 로드 되지 않습니다.<br /><br /> 애플리케이션에서 VSTO 추가 기능을 성공적으로 로드하면 **LoadBehavior** 값이 0으로 바뀌며, 애플리케이션을 종료하면 0으로 유지됩니다.|
|2|언로드됨|시작 시 로드|애플리케이션이 VSTO 추가 기능을 자동으로 로드하지 않습니다. 사용자는 VSTO 추가 기능을 수동으로 로드하거나, VSTO 추가 기능을 프로그래밍 방식으로 로드할 수 있습니다.<br /><br /> 애플리케이션에서 VSTO 추가 기능을 성공적으로 로드하면 **LoadBehavior** 값이 3으로 바뀌며, 애플리케이션을 종료하면 3으로 유지됩니다.|
|3|로드됨|시작 시 로드|애플리케이션을 시작하면 애플리케이션에서 VSTO 추가 기능을 로드합니다. Visual Studio에서 VSTO 추가 기능을 빌드하거나 게시할 때 기본값입니다.<br /><br /> 애플리케이션이 VSTO 추가 기능을 성공적으로 로드하면 **LoadBehavior** 값이 3으로 유지됩니다. VSTO 추가 기능을 로드할 때 오류가 발생하면 **LoadBehavior** 값이 2로 바뀌며, 애플리케이션을 종료하면 2로 유지됩니다.|
|8|언로드됨|요청 시 로드|애플리케이션이 VSTO 추가 기능을 자동으로 로드하지 않습니다. 사용자는 VSTO 추가 기능을 수동으로 로드하거나, VSTO 추가 기능을 프로그래밍 방식으로 로드할 수 있습니다.<br /><br /> 애플리케이션이 VSTO 추가 기능을 성공적으로 로드하면 **LoadBehavior** 값이 9로 바뀝니다.|
|9|로드됨|요청 시 로드|사용자가 VSTO 추가 기능의 기능을 사용하는 UI 요소를 클릭할 때처럼(예: 리본의 사용자 지정 단추), VSTO 추가 기능은 애플리케이션에서 필요로 하는 경우에만 로드됩니다.<br /><br /> 애플리케이션에서 VSTO 추가 기능을 성공적으로 로드하면 **LoadBehavior** 값은 9로 유지되지만 **COM 추가 기능** 대화 상자의 VSTO 추가 기능 상태는 업데이트되어 VSTO 추가 기능이 현재 로드된 것으로 나타납니다. VSTO 추가 기능을 로드할 때 오류가 발생하는 경우는 **LoadBehavior** 값이 8로 바뀝니다.|
|16|로드됨|처음으로 로드한 다음 요청 시 로드|VSTO 추가 기능이 요청 시 로드되도록 하려면 이 값을 설정합니다. 사용자가 애플리케이션을 처음으로 실행할 때 애플리케이션에서 VSTO 추가 기능을 로드합니다. 사용자가 다음에 애플리케이션을 실행하면 애플리케이션에서 VSTO 추가 기능에서 정의한 UI 요소를 로드합니다. 그러나 사용자가 VSTO 추가 기능과 연결된 UI 요소를 클릭할 때까지 VSTO 추가 기능은 로드되지 않습니다.<br /><br /> 애플리케이션에서 처음으로 VSTO 추가 기능을 로드할 때 VSTO 추가 기능이 로드되는 동안 **LoadBehavior** 값은 16으로 유지됩니다. 애플리케이션을 닫은 후에는 **LoadBehavior** 값이 9로 바뀝니다.|

## <a name="see-also"></a>참고 항목
- [Visual Studio의 Office 솔루션 아키텍처](../vsto/architecture-of-office-solutions-in-visual-studio.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Office 솔루션 빌드](../vsto/building-office-solutions.md)
- [Office 솔루션 배포](../vsto/deploying-an-office-solution.md)
 