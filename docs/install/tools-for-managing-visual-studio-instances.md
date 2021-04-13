---
title: Visual Studio 인스턴스 검색 및 관리 도구
titleSuffix: ''
description: 클라이언트 컴퓨터에서 Visual Studio 설치를 검색 및 관리하는 데 사용할 수 있는 도구에 대해 알아봅니다.
ms.date: 04/06/2021
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 85686707-14C0-4860-9B7A-66485D43D241
author: ornellaalt
ms.author: ornella
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2b6b641081c9b969cadd2c9517967adb8cc4cb1e
ms.sourcegitcommit: 56060e3186086541d9016d4185e6f1bf3471e958
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/07/2021
ms.locfileid: "106547442"
---
# <a name="tools-for-detecting-and-managing-visual-studio-instances"></a>Visual Studio 인스턴스 검색 및 관리 도구

클라이언트 컴퓨터에서 Visual Studio 설치를 검색하고 설치를 관리하는 데 사용할 수 있는 여러 도구가 있습니다.

## <a name="detecting-existing-visual-studio-instances"></a>기존 Visual Studio 인스턴스 검색

다음 도구 및 유틸리티는 클라이언트 컴퓨터에 설치된 Visual Studio 인스턴스를 검색 및 관리하는 데 도움이 됩니다.

* [**vswhere**](https://github.com/microsoft/vswhere): 실행 파일은 Visual Studio에 기본 설정되거나 별도 배포에 사용할 수 있습니다. 그러면 특정 머신에서 모든 Visual Studio 인스턴스의 위치를 확인할 수 있습니다.
* [**VSSetup.PowerShell**](https://github.com/microsoft/vssetup.powershell): 설치 구성 API를 사용하여 Visual Studio의 설치된 인스턴스를 식별하는 PowerShell 스크립트입니다.
* [**VS-Setup-Samples**](https://github.com/microsoft/vs-setup-samples): 설치 구성 API를 사용하여 기존 설치를 쿼리하는 방법을 보여 주는 C# 및 C++ 샘플입니다.
* [**WMI(Windows Management Instrumentation)** ](https://docs.microsoft.com/windows/win32/wmisdk/wmi-start-page): Visual Studio 클래스 MSFT_VSInstance를 통해 Visual Studio 인스턴스 정보를 쿼리할 수 있습니다. 
* [**설치 구성 API**](<xref:Microsoft.VisualStudio.Setup.Configuration>)는 Visual Studio 인스턴스를 조회하기 위해 자신의 유틸리티를 빌드하려는 개발자를 위한 인터페이스를 제공합니다.
* [**Microsoft Endpoint Configuration Manager 소프트웨어 인벤토리**](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory): 클라이언트 디바이스에서 Visual Studio 인스턴스에 대한 정보를 수집하는 데 사용할 수 있습니다. 

## <a name="using-vswhereexe"></a>vswhere.exe 사용

`vswhere.exe`는 Visual Studio 2017 이상에 자동으로 포함되어 있으며 [vswhere 릴리스 페이지](https://github.com/Microsoft/vswhere/releases)에서 다운로드할 수 있습니다. `vswhere -?`를 사용하여 도구에 대한 도움말 정보를 가져올 수 있습니다. 예를 들어, 이 명령은 이전 버전의 제품 및 시험판을 비롯한 Visual Studio의 모든 릴리스를 표시하고 결과를 JSON 형식으로 출력합니다.

```cmd
C:\Program Files (x86)\Microsoft Visual Studio\Installer> vswhere.exe -legacy -prerelease -format json
```

## <a name="using-windows-management-instrumentation-wmi"></a>WMI(Windows Management Instrumentation) 사용

컴퓨터에 Visual Studio 클라이언트 탐지기 유틸리티를 설치한 경우 WMI를 사용하여 Visual Studio 인스턴스 정보를 쿼리할 수 있습니다. Visual Studio 클라이언트 탐지기 유틸리티는 2020년 5월 12일 이후 릴리스된 모든 Visual Studio 2017 및 Visual Studio 2019 업데이트에서 기본적으로 설치됩니다. 독립적으로 설치하려는 경우 [Microsoft 업데이트 카탈로그](https://catalog.update.microsoft.com/)에서 사용할 수도 있습니다.  이 유틸리티를 사용하여 Visual Studio 인스턴스 정보를 반환하는 방법에 대한 예제를 보려면 클라이언트 컴퓨터에서 관리자 권한으로 PowerShell을 열고 다음 명령을 입력합니다.

```cmd
Get-CimInstance MSFT_VSInstance
```

## <a name="using-microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager 사용 

[Microsoft Endpoint Configuration Manager 소프트웨어 인벤토리](https://docs.microsoft.com/mem/configmgr/core/clients/manage/inventory/introduction-to-software-inventory) 기능은 클라이언트 디바이스에서 Visual Studio 인스턴스에 대한 정보를 쿼리하고 수집하는 데 사용할 수 있습니다. 예를 들어 다음 쿼리는 설치된 모든 Visual Studio 2017 및 2019 인스턴스에 대해 표시 이름, 버전 및 Visual Studio가 설치된 디바이스 이름을 반환합니다. 

```WQL 
select distinct SMS_G_System_COMPUTER_SYSTEM.Name, SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName, SMS_G_System_ADD_REMOVE_PROGRAMS.Version from SMS_R_System inner join SMS_G_System_COMPUTER_SYSTEM on SMS_G_System_COMPUTER_SYSTEM.ResourceID = SMS_R_System.ResourceId inner join SMS_G_System_ADD_REMOVE_PROGRAMS on SMS_G_System_ADD_REMOVE_PROGRAMS.ResourceID = SMS_R_System.ResourceId where SMS_G_System_ADD_REMOVE_PROGRAMS.DisplayName like "Visual Studio %[a-z]% 201[7,9]" 
``` 

::: moniker range="vs-2017"

> [!TIP]
> Visual Studio 2017 설치에 대한 자세한 내용은 [Visual Studio Setup Archives](https://devblogs.microsoft.com/setup/tag/vs2017/)를 참조하세요.

::: moniker-end

## <a name="editing-the-registry-for-a-visual-studio-instance"></a>Visual Studio 인스턴스의 레지스트리 편집

Visual Studio에서 레지스트리 설정은 전용 위치에 저장되므로 같은 머신에서 같은 버전의 Visual Studio에 대한 여러 side-by-side 인스턴스를 사용할 수 있습니다.

이러한 항목은 전역 레지스트리에 저장되지 않으므로 레지스트리 편집기를 사용하여 레지스트리 설정을 변경하기 위한 특별한 지침이 있습니다.

1. Visual Studio의 열린 인스턴스가 있으면 인스턴스를 닫으세요.

1. `regedit.exe`를 시작합니다.

1. `HKEY_LOCAL_MACHINE` 노드를 선택합니다.

1. Regedit 주 메뉴에서 **파일** > **하이브 로드...** 를 선택한 다음, **AppData\Local** 폴더에 저장된 전용 레지스트리 파일을 선택합니다. 예:

   ```
   %localappdata%\Microsoft\VisualStudio\<config>\privateregistry.bin
   ```

   > [!NOTE]
   > `<config>`는 찾아볼 Visual Studio의 인스턴스에 해당합니다.

하이브 이름을 입력하라는 메시지가 표시됩니다. 이 이름은 격리된 하이브의 이름이 됩니다. 이 작업을 한 후에는 직접 만든 격리된 하이브에서 레지스트리를 찾을 수 있습니다.

> [!IMPORTANT]
> Visual Studio를 다시 시작하기 전에 직접 만든 격리된 하이브를 언로드해야 합니다. 이 작업을 수행하려면 Regedit 주 메뉴에서 **파일** > **하이브 언로드** 를 선택합니다. 이렇게 하지 않으면 파일이 계속 잠겨 있고 Visual Studio가 시작되지 않습니다.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

* [Visual Studio 관리자 가이드](../install/visual-studio-administrator-guide.md)
