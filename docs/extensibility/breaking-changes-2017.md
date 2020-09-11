---
title: Visual Studio 2017 확장성의 주요 변경 내용
titleSuffix: ''
ms.date: 11/09/2016
ms.topic: conceptual
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d872003b319773401ef4da72c1fac8dc177ecbdb
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90011790"
---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Visual Studio 2017 확장성의 변경 내용

Visual Studio 2017은 사용자가 설치 된 작업 및 기능에 대 한 더 많은 옵션을 제공 하는 동시에 Visual Studio가 사용자 시스템에 미치는 영향을 줄이는 [더 빠르고 가벼운 Visual studio 설치 환경을](https://devblogs.microsoft.com/visualstudio/faster-leaner-visual-studio-installer) 제공 합니다. 이러한 향상 된 기능을 지원 하기 위해 몇 가지 주요 변경 내용을 포함 하 여 확장성 모델을 변경 했습니다. 이 문서에서는 이러한 변경 내용에 대 한 기술 세부 정보 및 해결을 위해 수행할 수 있는 작업을 설명 합니다.

> [!NOTE]
> 일부 정보는 지정 시간 구현 세부 정보 이며 나중에 변경 될 수 있습니다.

## <a name="changes-affecting-vsix-format-and-installation"></a>VSIX 형식 및 설치에 영향을 주는 변경 내용

Visual Studio 2017는 경량 설치 환경을 지원 하기 위해 VSIX v3 (버전 3) 형식을 도입 했습니다.

VSIX 형식에 대 한 변경 내용은 다음과 같습니다.

* 설치 필수 조건 선언입니다. Visual Studio를 빠르게 설치 하는 간단한 기능을 제공 하기 위해 이제 설치 관리자는 사용자에 게 더 많은 구성 옵션을 제공 합니다. 따라서 확장에 필요한 기능 및 구성 요소가 설치 되도록 하려면 확장에서 해당 종속성을 선언 해야 합니다.

  * Visual Studio 2017 설치 관리자는 확장을 설치 하는 과정에서 사용자에 대 한 필수 구성 요소를 얻고 설치 하도록 자동으로 제공 합니다.
  * 또한 사용자는 새 VSIX v3 형식을 사용 하 여 빌드되지 않은 확장을 설치 하려고 할 때 경고를 대상 버전 15.0으로 표시 된 경우에도 경고를 표시 합니다.

* VSIX 형식의 향상 된 기능. Side-by-side 설치를 지 원하는 Visual Studio의 [낮은 설치](https://devblogs.microsoft.com/visualstudio/anatomy-of-a-low-impact-visual-studio-install) 를 제공 하기 위해 더 이상 대부분의 구성 데이터를 시스템 레지스트리에 저장 하지 않고 visual studio 특정 어셈블리를 GAC에서 이동 했습니다. 또한 VSIX 형식 및 VSIX 설치 엔진의 기능을 사용 하 여 일부 설치 형식에 대 한 확장을 설치 하는 데 MSI 또는 EXE 대신 사용할 수 있습니다.

새로운 기능은 다음과 같습니다.

* 지정 된 Visual Studio 인스턴스에 등록 합니다.
* [Extensions 폴더](set-install-root.md)외부에 설치 합니다.
* 프로세서 아키텍처를 검색 합니다.
* 언어에 따라 구분 된 언어 팩에 종속 됩니다.
* 설치에서 [NGEN을 지원](ngen-support.md)합니다.

## <a name="build-an-extension-for-visual-studio-2017"></a>Visual Studio 2017에 대 한 확장 빌드

새 VSIX v3 매니페스트 형식을 작성 하기 위한 디자이너 도구는 Visual Studio 2017에서 사용할 수 있습니다. 디자이너 도구를 사용 하거나 프로젝트 및 매니페스트를 수동으로 업데이트 하 여 VSIX v3 확장을 개발 하는 방법에 대 한 자세한 내용은 함께 제공 되 [는 문서 방법: 확장성 프로젝트를 Visual Studio 2017로 마이그레이션](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) 을 참조 하세요.

## <a name="change-visual-studio-user-data-path"></a>변경: Visual Studio 사용자 데이터 경로

이전에는 각 컴퓨터에 Visual Studio의 각 주요 릴리스를 하나만 설치할 수 있었습니다. Visual Studio 2017의 side-by-side 설치를 지원 하기 위해 Visual Studio에 대 한 여러 사용자 데이터 경로가 사용자의 컴퓨터에 있을 수 있습니다.

Visual studio 프로세스 내에서 실행 되는 코드는 Visual Studio 설정 관리자를 사용 하도록 업데이트 되어야 합니다. Visual Studio 프로세스 외부에서 실행 되는 코드는 [여기 지침에](locating-visual-studio.md)따라 특정 visual studio 설치의 사용자 경로를 찾을 수 있습니다.

## <a name="change-global-assembly-cache-gac"></a>변경: GAC (전역 어셈블리 캐시)

대부분의 Visual Studio core 어셈블리는 더 이상 GAC에 설치 되지 않습니다. Visual Studio 프로세스에서 실행 되는 코드가 런타임에 필요한 어셈블리를 찾을 수 있도록 다음과 같이 변경 되었습니다.

> [!NOTE]
> 아래 [INSTALLDIR]는 Visual Studio의 설치 루트 디렉터리를 나타냅니다. *VSIXInstaller.exe* 는이를 자동으로 채우지만 사용자 지정 배포 코드를 작성 하려면 [Visual Studio 찾기](locating-visual-studio.md)를 참조 하세요.

* GAC에 설치 된 어셈블리는 다음과 같습니다.

  이러한 어셈블리는 이제 <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> 또는 *[INSTALLDIR] \Common7\IDE\PrivateAssemblies*아래에 설치 됩니다. 이러한 폴더는 Visual Studio 프로세스의 검색 경로에 포함 되어 있습니다.

* 비 검색 경로에 설치 된 어셈블리를 GAC에 설치 합니다.

  * GAC의 복사본이 설치 프로그램에서 제거 되었습니다.
  * *.Pkgdef* 파일이 추가 되어 어셈블리에 대 한 코드 베이스 항목을 지정 했습니다.

    예를 들면 다음과 같습니다.

    ```
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```

    Visual Studio .pkgdef 하위 시스템은 런타임에 이러한 항목을 Visual Studio 프로세스의 런타임 구성 파일 ( *[VSAPPDATA] \devenv.exe.config*)에 요소로 병합 합니다 [`<codeBase>`](/dotnet/framework/configure-apps/file-schema/runtime/codebase-element) . 이 방법은 검색 경로를 통한 검색을 방지 하기 때문에 Visual Studio 프로세스에서 어셈블리를 찾을 수 있도록 하는 데 권장 되는 방법입니다.

### <a name="reacting-to-this-breaking-change"></a>이 주요 변경 사항에 대응

* 확장이 Visual Studio 프로세스 내에서 실행 되는 경우:

  * 코드에서 Visual Studio 핵심 어셈블리를 찾을 수 있습니다.
  * 필요한 경우 *.pkgdef* 파일을 사용 하 여 어셈블리 경로를 지정 하는 것이 좋습니다.

* 확장이 Visual Studio 프로세스 외부에서 실행 되는 경우:

  구성 파일 또는 어셈블리 확인자를 사용 하 여 <em>[INSTALLDIR] \Common7\IDE \* , * [INSTALLDIR] \Common7\IDE\PublicAssemblies</em> 또는 *[INSTALLDIR] \Common7\IDE\PrivateAssemblies* 에서 Visual Studio 핵심 어셈블리를 검색 하십시오.

## <a name="change-reduce-registry-impact"></a>변경: 레지스트리 영향 감소

### <a name="global-com-registration"></a>전역 COM 등록

* 이전에는 Visual Studio가 네이티브 COM 등록을 지원 하기 위해 HKEY_CLASSES_ROOT 및 HKEY_LOCAL_MACHINE hive에 많은 레지스트리 키를 설치 했습니다. 이러한 영향을 제거 하기 위해 Visual Studio에서는 이제 [COM 구성 요소에 대해 등록이 필요 없는 활성화](/previous-versions/dotnet/articles/ms973913(v=msdn.10))를 사용 합니다.
* 결과적 으로% ProgramFiles (x86)% \ Common Files\Microsoft Shared\MSEnv 아래의 대부분의 TLB/DTE.OLB/DLL 파일은 Visual Studio에 의해 더 이상 기본적으로 설치 되지 않습니다. 이제 이러한 파일은 Visual Studio 호스트 프로세스에서 사용 하는 해당 등록이 필요 없는 COM 매니페스트가 있는 [INSTALLDIR] 아래에 설치 됩니다.
* 결과적으로, Visual Studio COM 인터페이스에 대 한 전역 COM 등록을 사용 하는 외부 코드는 이러한 등록을 더 이상 찾을 수 없습니다. Visual Studio 프로세스 내에서 실행 되는 코드에는 차이점이 표시 되지 않습니다.

### <a name="visual-studio-registry"></a>Visual Studio 레지스트리

* 이전에는 Visual Studio가 시스템의 **HKEY_LOCAL_MACHINE** 에 많은 레지스트리 키를 설치 하 고 visual studio 별 키로 **HKEY_CURRENT_USER** hive를 설치 했습니다.

  * **HKLM\Software\Microsoft\VisualStudio \{ Version}**: MSI 설치 관리자 및 컴퓨터별 확장에 의해 생성 된 레지스트리 키입니다.
  * **HKCU\Software\Microsoft\VisualStudio \{ Version}**: 사용자 특정 설정을 저장 하기 위해 Visual Studio에서 만든 레지스트리 키입니다.
  * **HKCU\Software\Microsoft\VisualStudio \{ 버전} _Config**: 위의 Visual STUDIO HKLM 키 복사본과 *.pkgdef* 파일에서 확장명으로 병합 된 레지스트리 키가 있습니다.

* 레지스트리에 대 한 영향을 줄이기 위해 Visual Studio는 이제 [Regloadappkey](/windows/desktop/api/winreg/nf-winreg-regloadappkeya) 함수를 사용 하 여 레지스트리 키를 *[VSAPPDATA] \privateregistry.bin*의 전용 이진 파일에 저장 합니다. 매우 적은 수의 Visual Studio 관련 키만 시스템 레지스트리에 남아 있습니다.
* Visual Studio 프로세스 내에서 실행 되는 기존 코드는 영향을 받지 않습니다. Visual Studio는 HKCU Visual Studio 별 키 아래의 모든 레지스트리 작업을 개인 레지스트리로 리디렉션합니다. 다른 레지스트리 위치에 대 한 읽기 및 쓰기는 시스템 레지스트리를 계속 사용 합니다.
* Visual Studio 레지스트리 항목에 대해이 파일에서 외부 코드를 로드 하 고 읽어야 합니다.

### <a name="react-to-this-breaking-change"></a>이 주요 변경 사항에 대응

* 외부 코드는 COM 구성 요소에 대 한 등록이 필요 없는 활성화를 사용 하도록 변환 해야 합니다.
* 외부 구성 요소는 여기서 설명 하는 [지침에 따라](https://devblogs.microsoft.com/setup/changes-to-visual-studio-15-setup)Visual Studio 위치를 찾을 수 있습니다.
* 외부 구성 요소는 Visual Studio 레지스트리 키에 직접 읽기/쓰기 대신 [외부 설정 관리자](/dotnet/api/microsoft.visualstudio.settings.externalsettingsmanager) 를 사용 하는 것이 좋습니다.
* 확장에서 사용 하는 구성 요소가 등록을 위한 다른 기술을 구현 했을 수 있는지 확인 합니다. 예를 들어 디버거 확장은 새로운 [MSVSMON JSON 파일 COM 등록](migrate-debugger-COM-registration.md)을 활용할 수 있습니다.