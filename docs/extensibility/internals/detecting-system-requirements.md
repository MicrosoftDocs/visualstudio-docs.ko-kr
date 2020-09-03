---
title: 시스템 요구 사항 검색 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- setup, VSPackages
- launch conditions
ms.assetid: 0ba94acf-bf0b-4bb3-8cca-aaac1b5d6737
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9ab254df5d53f379704128d8860b8d7fe5655bae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708729"
---
# <a name="detect-system-requirements"></a>시스템 요구 사항 검색
Visual Studio가 설치 되어 있지 않으면 VSPackage를 사용할 수 없습니다. Microsoft Windows Installer를 사용 하 여 VSPackage 설치를 관리 하는 경우 Visual Studio가 설치 되어 있는지 여부를 검색 하도록 설치 관리자를 구성할 수 있습니다. 또한 특정 버전의 Windows 또는 특정 RAM과 같은 다른 요구 사항이 있는지 시스템을 검사 하도록 구성할 수 있습니다.

## <a name="detect-visual-studio-editions"></a>Visual Studio 버전 검색
 Visual Studio 버전이 설치 되어 있는지 확인 하려면 다음 표에 나열 된 것과 같이 해당 폴더에서 **Install** 레지스트리 키의 값이 *(REG_DWORD) 1* 인지 확인 합니다. Visual Studio 버전의 계층 구조는 다음과 같습니다.

1. Enterprise

2. Professional

3. 커뮤니티

최신 버전을 설치 하면 이전 버전의 뿐만 아니라 해당 버전에 대 한 레지스트리 키도 추가 됩니다. 즉, Enterprise edition이 설치 되어 있는 경우 **설치** 키는 enterprise의 경우 1로, Professional 및 Community 버전의 경우 *1* 로 설정 됩니다. 따라서 필요한 최신 버전을 확인 해야 합니다.

> [!NOTE]
> 64 비트 버전의 레지스트리 편집기에서 32 비트 키는 **HKEY_LOCAL_MACHINE \software\wow6432node \\ **아래에 표시 됩니다. Visual Studio 키는 **HKEY_LOCAL_MACHINE \software\wow6432node\microsoft\devdiv\vs\servicing \\ **아래에 있습니다.

|제품|키|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\enterprise|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\professional|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\community|
|Visual Studio 2015 Shell (통합 및 격리)|HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\DevDiv\vs\Servicing\14.0\isoshell|

## <a name="detect-when-visual-studio-is-running"></a>Visual Studio가 실행 되는 경우 검색
 VSPackage가 설치 될 때 Visual Studio가 실행 중인 경우 VSPackage를 올바르게 등록할 수 없습니다. 설치 관리자에서 Visual Studio가 실행 중일 때를 검색 한 다음 프로그램 설치를 거부 해야 합니다. Windows Installer 테이블 항목을 사용 하 여 이러한 검색을 사용 하도록 설정할 수 없습니다. 대신, 다음과 같이 사용자 지정 작업을 만들어야 합니다. 함수를 사용 `EnumProcesses` 하 여 *devenv.exe* 프로세스를 검색 한 다음 시작 조건에 사용 되는 설치 관리자 속성을 설정 하거나 사용자에 게 Visual Studio를 닫으라는 메시지를 표시 하는 대화 상자를 조건부로 표시 합니다.

## <a name="see-also"></a>추가 정보
- [Windows Installer를 사용 하 여 Vspackage 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
