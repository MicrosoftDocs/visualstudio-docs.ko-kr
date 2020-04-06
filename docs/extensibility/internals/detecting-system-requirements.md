---
title: 시스템 요구 사항 감지 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708729"
---
# <a name="detect-system-requirements"></a>시스템 요구 사항 감지
비주얼 스튜디오를 설치하지 않으면 VSPackage가 작동하지 않습니다. Microsoft Windows 설치 관리자를 사용하여 VSPackage 설치를 관리하는 경우 설치 관리자를 구성하여 Visual Studio가 설치되었는지 여부를 감지할 수 있습니다. 특정 버전의 Windows 또는 특정 양의 RAM과 같은 다른 요구 사항이 있는지 시스템을 확인하도록 구성할 수도 있습니다.

## <a name="detect-visual-studio-editions"></a>비주얼 스튜디오 에디션 감지
 Visual Studio 에디션이 설치되어 있는지 확인하려면 다음 표에 나열된 대로 **설치** 레지스트리 키의 값이 적절한 폴더의 *(REG_DWORD) 1인지* 확인합니다. Visual Studio 버전에는 계층 구조가 있습니다.

1. Enterprise

2. Professional

3. 커뮤니티

최신 버전이 설치되면 해당 에디션의 레지스트리 키와 이전 버전이 추가됩니다. 즉, 엔터프라이즈 버전이 설치된 경우 **설치** 키는 엔터프라이즈 및 커뮤니티 버전에 대해 *1로* 설정됩니다. 따라서 필요한 최신 버전만 확인해야 합니다.

> [!NOTE]
> 레지스트리 편집기의 64비트 버전에서는 32비트 키가 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\\**로 표시됩니다. 비주얼 스튜디오 키는 **HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\마이크로소프트\DevDiv\vs\서비스\\**.

|Product|키|
|-------------|---------|
|Visual Studio Enterprise 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\서비스\14.0\엔터프라이즈|
|Visual Studio Professional 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\서비스\14.0\전문가|
|Visual Studio Community 2015|HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\DevDiv\vs\서비스\14.0\커뮤니티|
|비주얼 스튜디오 2015 쉘 (통합 및 격리)|HKEY_LOCAL_MACHINE\SOFTWARE\마이크로소프트\데브디브\vs\서비스\14.0\아이소쉘|

## <a name="detect-when-visual-studio-is-running"></a>Visual Studio가 실행 중일 때 감지
 VSPackage를 설치할 때 Visual Studio가 실행 중인 경우 VSPackage를 올바르게 등록할 수 없습니다. 설치 관리자는 Visual Studio가 실행 중인 시기를 감지한 다음 프로그램 설치를 거부해야 합니다. Windows 설치 관리자는 테이블 항목을 사용하여 이러한 검색을 활성화할 수 없습니다. 대신 다음과 같이 사용자 지정 작업을 만들어야 `EnumProcesses` 합니다. *devenv.exe*

## <a name="see-also"></a>참조
- [윈도우 설치 관리자와 VS패키지 설치](../../extensibility/internals/installing-vspackages-with-windows-installer.md)
