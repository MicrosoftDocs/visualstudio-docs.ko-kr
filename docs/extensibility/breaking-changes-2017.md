---
title: 비주얼 스튜디오 2017 확장성의 주요 변경 사항
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b3a04c925ef897171de51c73c90973a12c3b17d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739977"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>비주얼 스튜디오 2017 확장성의 변경 사항

Visual Studio 2017은 사용자 시스템에 대한 Visual Studio의 영향을 줄이는 동시에 설치된 워크로드 및 기능에 대한 선택의 폭을 넓게 하는 [더 빠르고 가벼운 Visual Studio 설치 환경을](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) 제공합니다. 이러한 개선 사항을 지원하기 위해 몇 가지 주요 변경 사항을 포함하여 확장성 모델을 변경했습니다. 이 문서에서는 이러한 변경 사항에 대한 기술적 세부 사항과 이러한 변경 사항을 해결하기 위해 수행할 수 있는 작업에 대해 설명합니다.

> [!NOTE]
> 일부 정보는 시점 구현 세부 정보이며 나중에 변경될 수 있습니다.

## <a name="changes-affecting-vsix-format-and-installation"></a>VSIX 형식 및 설치에 영향을 미치는 변경 사항

Visual Studio 2017은 경량 설치 환경을 지원하기 위해 VSIX v3(버전 3) 형식을 도입했습니다.

VSIX 형식의 변경 사항은 다음과 같습니다.

* 설정 전제 조건 선언입니다. 가볍고 빠르게 설치되는 Visual Studio를 제공하기 위해 설치 관리자는 이제 사용자에게 더 많은 구성 옵션을 제공합니다. 따라서 확장에 필요한 기능 및 구성 요소를 설치하려면 확장이 종속성을 선언해야 합니다.

  * Visual Studio 2017 설치 프로그램은 확장 설치의 일부로 사용자에게 필요한 구성 요소를 자동으로 획득하고 설치합니다.
  * 새 VSIX v3 형식을 사용하여 빌드되지 않은 확장을 설치하려고 할 때 매니페스트에서 대상 버전 15.0으로 표시된 경우에도 사용자에게 경고가 표시됩니다.

* VSIX 형식에 대한 향상된 기능. 나란히 설치를 지원하는 Visual Studio의 [영향이 적은 설치를](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) 제공하기 위해 대부분의 구성 데이터를 시스템 레지스트리에 저장하지 않고 Visual Studio 관련 어셈블리를 GAC 밖으로 이동했습니다. 또한 VSIX 포맷과 VSIX 설치 엔진의 기능을 향상시켜 MSI 나 EXE대신 사용할 수 있도록 하여 일부 설치 유형에 대한 확장을 설치할 수 있습니다.

새로운 기능은 다음과 같습니다.

* 지정된 Visual Studio 인스턴스에 등록합니다.
* 확장 폴더 외부에 [설치합니다.](set-install-root.md)
* 프로세서 아키텍처 의 검색.
* 언어 구분 언어 팩에 대한 의존성.
* [NGEN 지원](ngen-support.md)설치.

## <a name="build-an-extension-for-visual-studio-2017"></a>비주얼 스튜디오 2017에 대 한 확장을 구축

새로운 VSIX v3 매니페스트 형식의 작성을 위한 디자이너 도구는 Visual Studio 2017에서 사용할 수 있습니다. 함께 제공되는 [문서: 확장성 프로젝트를 Visual Studio 2017로 마이그레이션하여](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) 디자이너 도구를 사용하거나 프로젝트에 대한 수동 업데이트를 수행하고 VSIX v3 확장을 개발하기 위해 매니페스트하는 방법에 대한 자세한 내용을 확인하십시오.

## <a name="change-visual-studio-user-data-path"></a>변경: 비주얼 스튜디오 사용자 데이터 경로

이전에는 Visual Studio의 각 주요 릴리스에 대한 설치가 각 컴퓨터에 하나만 존재할 수 있었습니다. Visual Studio 2017의 병렬 설치를 지원하기 위해 Visual Studio에 대한 여러 사용자 데이터 경로가 사용자의 컴퓨터에 있을 수 있습니다.

Visual Studio 프로세스 내에서 실행되는 코드는 Visual Studio 설정 관리자를 사용하도록 업데이트해야 합니다. Visual Studio 프로세스 외부에서 실행되는 코드는 다음 의 지침을 따라 특정 Visual Studio 설치의 사용자 경로를 찾을 수 [있습니다.](locating-visual-studio.md)

## <a name="change-global-assembly-cache-gac"></a>변경: 전역 어셈블리 캐시(GAC)

대부분의 Visual Studio 코어 어셈블리는 더 이상 GAC에 설치되지 않습니다. Visual Studio 프로세스에서 실행되는 코드가 런타임에 필요한 어셈블리를 계속 찾을 수 있도록 다음 변경 사항이 변경되었습니다.

> [!NOTE]
> [INSTALLDIR] 아래는 Visual Studio의 설치 루트 디렉토리를 나타냅니다. *VSIXInstaller.exe는* 자동으로 이 것을 채우지만 사용자 지정 배포 코드를 작성하려면 [Visual Studio 를 찾는 것을](locating-visual-studio.md)읽으십시오.

* GAC에만 설치된 어셈블리:

  이러한 어셈블리는 이제 <em>[INSTALLDIR]\Common7\IDE,\**[INSTALLDIR]\Common7\IDE\Public 어셈블리</em> 또는 *[INSTALLDIR]\Common7\IDE\Private 어셈블리 아래에 설치됩니다.* 이러한 폴더는 Visual Studio 프로세스의 검색 경로의 일부입니다.

* 비프로빙 경로와 GAC에 설치된 어셈블리:

  * GAC의 복사본이 설정에서 제거되었습니다.
  * 어셈블리에 대한 코드 베이스 항목을 지정하기 위해 *.pkgdef* 파일이 추가되었습니다.

    다음은 그 예입니다.

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    런타임에 Visual Studio pkgdef 하위 시스템은 이러한 항목을 *[VSAPPDATA]\devenv.exe.config*아래의 Visual Studio 프로세스의 [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) 런타임 구성 파일로 요소로 병합합니다. 이는 검색 경로를 통해 검색하지 않도록 하기 때문에 Visual Studio 프로세스에서 어셈블리를 찾을 수 있도록 하는 데 권장되는 방법입니다.

### <a name="reacting-to-this-breaking-change"></a>이러한 주요 변경에 대응

* 확장이 Visual Studio 프로세스 내에서 실행 중인 경우:

  * 코드에서 Visual Studio 코어 어셈블리를 찾을 수 있습니다.
  * 필요한 경우 *.pkgdef* 파일을 사용하여 어셈블리에 대한 경로를 지정하는 것이 좋습니다.

* 확장이 Visual Studio 프로세스 외부에서 실행중인 경우:

  <em>[INSTALLDIR]\Common7\IDE\*, *[INSTALLDIR]\Common7\IDE\Public 어셈블리</em> 또는 *[INSTALLDIR]\Common7\IDE\Private 어셈블리* 구성 파일 또는 어셈블리 확인자를 사용하여 Visual Studio 코어 어셈블리를 찾는 것이 좋습니다.

## <a name="change-reduce-registry-impact"></a>변경: 레지스트리 영향 감소

### <a name="global-com-registration"></a>글로벌 COM 등록

* 이전에 Visual Studio는 HKEY_CLASSES_ROOT 많은 레지스트리 키를 설치하고 기본 COM 등록을 지원하기 위해 두드러기를 HKEY_LOCAL_MACHINE. 이러한 영향을 없애기 위해 Visual Studio는 이제 [COM 구성 요소에 등록 없는 정품 인증을](https://msdn.microsoft.com/library/ms973913.aspx)사용합니다.
* 결과적으로, 대부분의 TLB / OLB / DLL 파일 %ProgramFiles (x86)%%\일반 파일\마이크로 소프트 공유 \MSEnv는 더 이상 비주얼 스튜디오에 의해 기본적으로 설치되지 않습니다. 이러한 파일은 이제 [INSTALLDIR] 아래에 설치되며 Visual Studio 호스트 프로세스에서 사용하는 해당 등록 없는 COM 매니페스트가 있습니다.
* 따라서 Visual Studio COM 인터페이스에 대한 전역 COM 등록에 의존하는 외부 코드는 더 이상 이러한 등록을 찾을 수 없습니다. Visual Studio 프로세스 내에서 실행되는 코드는 차이가 없습니다.

### <a name="visual-studio-registry"></a>비주얼 스튜디오 레지스트리

* 이전에 Visual Studio는 시스템의 **HKEY_LOCAL_MACHINE** 많은 레지스트리 키를 설치하고 Visual Studio 관련 키 아래에 **HKEY_CURRENT_USER.**

  * **HKLM\소프트웨어\Microsoft\VisualStudio\{버전}**: MSI 설치 프로그램 및 시스템별 확장에 의해 생성된 레지스트리 키.
  * **HKCU\소프트웨어\Microsoft\VisualStudio\{버전}**: Visual Studio에서 만든 레지스트리 키로 사용자별 설정을 저장합니다.
  * **HKCU\Software\Microsoft\VisualStudio\{버전}_Config**: 위의 Visual Studio HKLM 키 사본과 *확장명으로 .pkgdef* 파일에서 병합된 레지스트리 키.

* 레지스트리에 미치는 영향을 줄이기 위해 Visual Studio는 이제 [RegLoadAppKey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) 함수를 사용하여 *[VSAPPDATA]\privateregistry.bin*아래의 개인 바이너리 파일에 레지스트리 키를 저장합니다. 매우 적은 수의 Visual Studio 관련 키만 시스템 레지스트리에 남아 있습니다.
* Visual Studio 프로세스 내에서 실행되는 기존 코드는 영향을 받지 않습니다. Visual Studio는 HKCU Visual Studio 전용 키아래의 모든 레지스트리 작업을 개인 레지스트리로 리디렉션합니다. 다른 레지스트리 위치에 읽고 쓰는 것은 시스템 레지스트리를 계속 사용합니다.
* 외부 코드는 Visual Studio 레지스트리 항목에 대해 이 파일을 로드하고 읽어야 합니다.

### <a name="react-to-this-breaking-change"></a>이 주요 변경에 대응

* 외부 코드는 COM 구성 요소에 대해서도 등록 이없는 활성화를 사용하도록 변환되어야 합니다.
* 외부 구성 요소는 다음 [의 지침을 따라](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)Visual Studio 위치를 찾을 수 있습니다.
* 외부 구성 요소는 Visual Studio 레지스트리 키를 직접 읽거나 쓰는 대신 [외부 설정 관리자를](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) 사용하는 것이 좋습니다.
* 확장 프로그램이 사용하는 구성 요소가 등록을 위한 다른 기술을 구현했는지 확인합니다. 예를 들어 디버거 확장은 새 [msvsmon JSON 파일 COM 등록을](migrate-debugger-COM-registration.md)활용할 수 있습니다.
