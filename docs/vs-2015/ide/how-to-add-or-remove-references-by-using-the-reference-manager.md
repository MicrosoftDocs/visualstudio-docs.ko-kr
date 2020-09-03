---
title: '방법: 참조 관리자를 사용하여 참조 추가 또는 제거 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- VS.ReferenceManager
helpviewer_keywords:
- Visual C# projects, references
- references [Visual Studio], adding
- assemblies [Visual Studio], references
- Visual Basic projects, references
- project references, adding
- referencing components, adding references
- project references, removing
- referencing assemblies
- referencing components, removing references
- references [Visual Studio], removing
- referencing components, assemblies not listed
ms.assetid: 1aabb520-99b0-46c6-9368-21b4d84793eb
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d0763f2cf86d94f96f6f9c907ee306c731994f22
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852083"
---
# <a name="how-to-add-or-remove-references-by-using-the-reference-manager"></a>방법: 참조 관리자를 사용하여 참조 추가 또는 제거
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**참조 관리자** 대화 상자를 사용 하 여 Microsoft 또는 다른 회사에서 개발한 구성 요소에 대 한 참조를 추가 하 고 관리할 수 있습니다. 유니버설 Windows 앱을 개발하는 경우 프로젝트에서 올바른 모든 Windows SDK DLL을 자동으로 참조합니다. .NET 애플리케이션을 개발하는 경우 프로젝트에서 자동으로 mscorlib.dll을 참조합니다. 일부 .NET API는 수동으로 추가해야 하는 구성 요소에서 노출됩니다. COM 구성 요소 또는 사용자 지정 구성 요소에 대한 참조를 수동으로 추가해야 합니다.

## <a name="adding-and-removing-a-reference"></a>참조 추가 및 제거

#### <a name="to-add-a-reference"></a>참조를 추가하려면

1. **솔루션 탐색기**에서 참조 노드를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

2. 추가할 참조를 지정한 다음 **확인** 단추를 선택합니다.

   **참조 관리자**가 열리고 사용 가능한 참조 목록이 그룹별로 나열됩니다. 프로젝트 형식에 따라 표시되는 다음 그룹이 결정됩니다.

- 어셈블리, 프레임워크 및 확장 하위 그룹 포함

- 솔루션, 프로젝트 하위 그룹 포함

- Windows, 핵심 및 확장명 하위 그룹 포함. **개체 브라우저**를 사용하여 Windows SDK 또는 확장명 SDK에서 참조를 탐색할 수 있습니다.

- 찾아보기, 최근 항목 하위 그룹 포함

## <a name="assemblies-tab"></a>어셈블리 탭
 **어셈블리** 탭은 참조에 사용할 수 있는 .NET Framework 어셈블리를 모두 나열합니다. GAC의 어셈블리는 런타임 환경의 일부 이므로 **어셈블리** 탭에는 gac (전역 어셈블리 캐시)의 어셈블리가 나열 되지 않습니다. GAC에 등록된 어셈블리에 대한 참조가 포함된 애플리케이션을 배포하거나 복사하는 경우, 이 어셈블리는 로컬 복사 설정과 관계없이 애플리케이션과 함께 배포되거나 복사되지 않습니다. 자세한 내용은 [프로젝트의 참조 관리](https://msdn.microsoft.com/library/ez524kew.aspx)를 참조하세요.

 EnvDTE 네임스페이스(EnvDTE, EnvDTE80, EnvDTE90, EnvDTE90a 또는 EnvDTE100)에 대한 참조를 수동으로 추가할 때는 속성 창에서 참조의 Interop 형식 포함 속성을 False로 설정합니다. 이 속성을 True로 설정하면 포함할 수 없는 특정 EnvDTE 속성으로 인해 빌드 문제가 발생할 수 있습니다.

 모든 데스크톱 프로젝트에는 mscorlib에 대한 암시적 참조가 포함되어 있습니다. [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 프로젝트에는 Microsoft.VisualBasic에 대한 암시적 참조가 포함되어 있습니다. [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서는 System.Core가 참조 목록에서 제거된 경우에도 모든 프로젝트에 System.Core에 대한 암시적 참조가 포함되어 있습니다.

 프로젝트 형식이 어셈블리를 지원 하지 않으면 **참조 관리자** 대화 상자에이 탭이 나타나지 않습니다.

 어셈블리 탭은 다음 두 개의 하위 탭으로 구성됩니다.

1. 프레임워크 하위 탭은 대상 프레임워크를 구성하는 모든 어셈블리를 나열합니다.

   - 보급된 어셈블리는 전체 프레임워크에 있으며 프로젝트가 대상 프레임워크의 프로필을 대상으로 지정하는 경우 프레임워크 목록에 열거됩니다. 보급된 어셈블리는 프로젝트의 대상 프레임워크 프로필에 있는 어셈블리와 구분하기 위해 회색으로 표시됩니다. 예를 들어, 프로젝트가 .NET Framework 4 클라이언트를 대상으로 지정하는 경우 프레임워크 목록에는 .NET Framework 4에서 보급된 어셈블리가 표시됩니다. 사용자가 보급된 어셈블리를 추가하면 사용자는 **참조 관리자** 대화 상자가 닫힌 후에 프로젝트의 대상이 .NET Framework 4로 변경되고 보급된 어셈블리가 추가되었음을 알게 됩니다.

   - [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱용 프로젝트에는 프로젝트 생성 시 기본적으로 대상 [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)]의 모든 어셈블리에 대한 참조가 포함됩니다. 관리 되는 프로젝트에서 **솔루션 탐색기** 의 참조 폴더 아래에 있는 읽기 전용 노드는 전체 프레임 워크에 대 한 참조를 나타냅니다. 따라서 프레임워크 탭은 프레임워크의 어떠한 어셈블리도 열거하지 않고 대신 다음과 같은 메시지를 표시합니다. "모든 Framework 어셈블리가 이미 참조되었습니다. [개체 브라우저]를 사용하여 Framework에서 참조를 탐색하십시오." 데스크톱 프로젝트의 경우, 프레임워크 탭은 대상 프레임워크의 어셈블리를 열거하고 사용자는 애플리케이션에 필요한 참조를 추가해야 합니다.

2. 확장 하위 탭은 구성 요소 및 컨트롤의 외부 공급업체가 개발하고 대상 프레임워크를 확장한 모든 어셈블리를 나열합니다. 사용자 애플리케이션의 목적에 따라 이러한 어셈블리가 필요할 수 있습니다.

   - 확장명 하위 탭은 다음 위치에 등록된 어셈블리를 열거하여 채워집니다.

       ```
       32-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       64-bit machine:
       HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\[Target Framework Identifier]\v[Target Framework Version]\AssemblyFoldersEx\[UserComponentName]\@default=[Disk location of assemblies]
       And older versions of the [Target Framework Identifier]
       ```

        예를 들어, 프로젝트가 32비트 컴퓨터에서 .NET Framework 4를 대상으로 지정하는 경우, 확장명 하위 탭은 \Microsoft\\.NETFramework\v4.0\AssemblyFoldersEx\\, \Microsoft\\.NETFramework\v3.5\AssemblyFoldersEx\\, \Microsoft\\.NETFramework\v3.0\AssemblyFoldersEx\\ 및 \Microsoft\\.NETFramework\v2.0\AssemblyFoldersEx\\에서 등록된 어셈블리를 열거합니다.

   프로젝트의 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 버전에 따라 목록의 일부 구성 요소는 표시되지 않을 수 있습니다. 이 비동기화는 다음과 같은 경우에 발생할 수 있습니다.

- 최신 버전의 .NET Framework를 사용하는 구성 요소는 이전 버전의 .NET Framework를 대상으로 하는 프로젝트와 호환되지 않습니다.

     프로젝트의 대상 .NET Framework 버전을 변경하는 방법에 대한 자세한 내용은 [방법: 한 버전의 .NET Framework를 대상으로 지정](../ide/how-to-target-a-version-of-the-dotnet-framework.md)을 참조하세요.

- [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]를 사용하는 구성 요소는 [!INCLUDE[net_v45](../includes/net-v45-md.md)]을 대상으로 하는 프로젝트와 호환되지 않습니다.

     새 애플리케이션을 만들면 기본적으로 일부 프로젝트가 [!INCLUDE[net_v45](../includes/net-v45-md.md)]을 대상으로 합니다. 자세한 내용은 [.NET Framework Client Profile](https://msdn.microsoft.com/library/f0219919-1f02-4588-8704-327a62fd91f1)을 참조하세요.

- 동일한 솔루션에 있는 다른 프로젝트의 출력에 대한 파일 참조를 추가하면 컴파일 오류가 발생할 수 있으므로 이 방법은 사용하지 않는 것이 좋습니다. 대신 **참조 추가** 대화 상자의 **프로젝트** 탭을 사용하여 프로젝트 간 참조를 만듭니다. 이렇게 하면 프로젝트에서 만드는 클래스 라이브러리를 보다 효율적으로 관리할 수 있으므로 개발 팀이 작업하기가 간편해집니다. 자세한 내용은 [끊어진 참조 문제 해결](../ide/troubleshooting-broken-references.md)을 참조하세요.

- > [!NOTE]
    > Visual Studio 2015에서는 한 프로젝트의 대상 .NET Framework 버전이 버전 4.5이고 다른 프로젝트의 대상 버전이 버전 2, 3, 3.5 또는 4.0인 경우 프로젝트 참조 대신 파일 참조가 만들어집니다.

#### <a name="to-display-an-assembly-in-the-add-reference-dialog-box"></a>참조 추가 대화 상자에서 어셈블리를 표시하려면

- 다음 위치 중 하나로 어셈블리를 이동하거나 복사합니다.

  - 현재 프로젝트 디렉터리. 이 어셈블리는 **찾아보기** 탭을 통해 찾을 수 있습니다.

  - 같은 솔루션에 있는 다른 프로젝트 디렉터리. 이 어셈블리는 **프로젝트** 탭을 통해 찾을 수 있습니다.

    \- 또는 -

- 표시할 어셈블리의 위치를 지정하는 레지스트리 키를 설정합니다.

   32비트 운영 체제의 경우 다음 레지스트리 키 중 하나를 추가합니다.

  - [HKEY_CURRENT_USER\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

    64비트 운영 체제의 경우에는 32비트 레지스트리 하이브에 포함된 다음 레지스트리 키 중 하나를 추가합니다.

  - [HKEY_CURRENT_USER\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

  - [HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\\.NETFramework\\*VersionMinimum*\AssemblyFoldersEx\MyAssemblies]@="*AssemblyLocation*"

    *VersionMinimum*은 적용되는 최하위 .NET Framework 버전입니다. *VersionMinimum*이 v3.0인 경우 AssemblyFoldersEx에 지정된 폴더는 .NET Framework 3.0 이상을 대상으로 하는 프로젝트에 적용됩니다.

    *AssemblyLocation*은 **참조 추가** 대화 상자에 표시하려는 어셈블리의 디렉터리(예: C:\MyAssemblies\\)입니다.

    HKEY_LOCAL_MACHINE 노드 아래에 레지스트리 키를 만들면 모든 사용자가 **참조 추가** 대화 상자에서 지정된 위치의 어셈블리를 볼 수 있습니다. HKEY_CURRENT_USER 노드 아래에 레지스트리 키를 만들면 현재 사용자에 대한 설정에만 영향을 줍니다.

    **참조 추가** 대화 상자를 다시 엽니다. 어셈블리가 **.NET** 탭에 나타나야 합니다. 어셈블리가 나타나지 않으면 지정된 *AssemblyLocation* 디렉터리에 어셈블리가 있는지 확인하고 Visual Studio를 다시 시작한 후 다시 시도합니다.

## <a name="com-tab"></a>COM 탭
 COM 탭은 참조에 사용할 수 있는 COM 구성 요소를 모두 나열합니다. 내부 매니페스트가 포함된 등록 COM DLL에 참조를 추가하려는 경우 해당 DLL의 등록을 먼저 해제합니다. 그렇지 않으면 네이티브 DLL 대신 ActiveX 컨트롤 같은 어셈블리 참조가 추가됩니다.

 프로젝트 형식이 COM을 지원하지 않으면 **참조 관리자** 대화 상자에 이 탭이 나타나지 않습니다.

## <a name="solution-tab"></a>솔루션 탭
 솔루션 탭은 프로젝트 하위 탭에 현재 솔루션 내 모든 호환 가능한 프로젝트를 나열합니다.

 프로젝트는 다른 버전의 .NET Framework를 대상으로 하는 다른 프로젝트를 참조할 수 있습니다. 예를 들어, [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]를 대상으로 하지만 .NET Framework 2용으로 빌드된 어셈블리를 참조하는 프로젝트를 만들 수 있습니다. 그러나 .NET Framework 2 프로젝트는 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)] 프로젝트를 참조할 수 없습니다. 자세한 내용은 [특정 대상 .NET Framework 버전 지정](../ide/targeting-a-specific-dotnet-framework-version.md)을 참조하세요.

 [!INCLUDE[net_v40_short](../includes/net-v40-short-md.md)]를 대상으로 하는 프로젝트는 [!INCLUDE[net_client_v40_long](../includes/net-client-v40-long-md.md)]을 대상으로 하는 프로젝트와 호환되지 않습니다.

 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]에서 하나의 프로젝트가 .NET Framework 4를 대상으로 지정하고 다른 프로젝트가 이전 버전을 대상으로 지정하는 경우, 프로젝트 참조 대신 파일 참조가 만들어집니다.

 [!INCLUDE[net_win8_profile](../includes/net-win8-profile-md.md)]을 대상으로 하는 프로젝트는 .NET Framework를 대상으로 하는 프로젝트에 프로젝트 참조를 추가할 수 없으며 그 반대의 경우도 마찬가지입니다.

## <a name="windows-tab"></a>Windows 탭
 Windows 탭은 Windows 운영 체제를 실행하는 플랫폼에 관련된 모든 SDK를 나열합니다.

 다음 두 가지 방법으로 Visual Studio의 WinMD 파일을 생성할 수 있습니다.

- ** [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱 관리 프로젝트**: [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱 프로젝트는 출력 형식 = Winmd 파일 &#124; 프로젝트 속성을 설정 하 여 winmd 이진 파일을 출력할 수 있습니다. WinMD 파일 이름은 안에 있는 모든 네임스페이스의 상위 네임스페이스여야 합니다. 예를 들어, 프로젝트가 네임스페이스 A.B 및 A.B.C로 구성된 경우 해당 출력 WinMD의 가능한 이름은 A.winmd 및 A.B.winmd입니다. 사용자가 프로젝트의 네임스페이스 집합과 연결되지 않은 "프로젝트 속성 &#124; 어셈블리 이름" 또는 "프로젝트 속성 &#124; 네임스페이스" 값을 입력하거나, 프로젝트 내에 상위 네임스페이스가 없는 경우, 다음과 같은 빌드 경고가 발생합니다. 'A.winmd'은(는) 이 어셈블리에 올바른 .winmd 파일 이름이 아닙니다. Windows 메타데이터 파일 내의 모든 형식은 파일 이름의 하위 네임스페이스에 있어야 합니다. 파일 이름의 하위 네임스페이스에 없는 형식은 런타임에 찾을 수 없습니다. 이 어셈블리에서 가장 작은 공통 네임스페이스는 'CSWSClassLibrary1'입니다. Visual Basic 또는 Visual C# 데스크톱 프로젝트는 자사 WinMD로 알려진 [!INCLUDE[win8](../includes/win8-md.md)] SDK를 사용하여 생성된 WinMD만 사용할 수 있으며, WinMD를 생성할 수 없습니다.

- ** [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱 네이티브 프로젝트**: 네이티브 WinMD 파일은 메타 데이터만으로 구성 됩니다. 해당 구현은 별도 DLL 파일에 있습니다. **새 프로젝트** 대화 상자의 Windows 런타임 구성 요소 프로젝트 템플릿을 선택하거나, 빈 프로젝트에서 시작해 프로젝트 속성을 수정하여 WinMD 파일을 생성함으로써 네이티브 이진 파일을 만들 수 있습니다. 프로젝트가 연결되지 않은 네임스페이스로 구성된 경우, 빌드 오류로부터 그러한 네임스페이스를 결합하거나 MSMerge 도구를 실행하는 사용자를 확인할 수 있습니다.

  Windows 탭은 다음 두 개의 하위 그룹으로 구성됩니다.

### <a name="core-subgroup"></a>핵심 하위 그룹
 핵심 하위 그룹은 대상 버전의 Windows용 SDK에 있는 WinMD(Windows 런타임 요소용)를 모두 나열합니다.

 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱 프로젝트에는 프로젝트 생성 시 기본적으로 [!INCLUDE[win8](../includes/win8-md.md)]의 모든 WinMD에 대한 참조가 포함됩니다. 관리 프로젝트에서 **솔루션 탐색기**의 참조 폴더 아래에 있는 읽기 전용 노드는 전체 [!INCLUDE[win8](../includes/win8-md.md)] SDK에 대한 참조를 나타냅니다. 따라서 참조 관리자의 핵심 하위 그룹은 [!INCLUDE[win8](../includes/win8-md.md)] SDK의 어떠한 어셈블리도 열거하지 않고 대신 다음과 같은 메시지를 표시합니다. "Windows SDK가 이미 참조되었습니다. [개체 탐색기]를 사용하여 Windows SDK에서 참조를 탐색하십시오."

 데스크톱 프로젝트에서 핵심 하위 그룹은 기본적으로 표시되지 않습니다. 프로젝트 노드에 대한 바로 가기 메뉴를 열고, **프로젝트 언로드**를 선택하고, 다음 코드 조각을 추가하고, 프로젝트를 다시 열어(프로젝트 노드에서 **프로젝트 다시 로드** 선택) Windows 런타임을 추가할 수 있습니다. **참조 관리자** 대화 상자를 호출하면 핵심 하위 그룹이 나타납니다.

```
<PropertyGroup>
  <TargetPlatformVersion>8.0</TargetPlatformVersion>
</PropertyGroup>
```

 이 하위 그룹의 **Windows** 확인란이 선택되어 있는지 확인합니다. 이 경우 Windows 런타임 요소를 사용할 수 있어야 합니다. 그러나, Windows 런타임 라이브러리에서 사용되는 IEnumerable과 같은 일부 표준 클래스 및 인터페이스를 Windows 런타임에서 정의하는 경우, System.Runtime도 추가하려 할 수 있습니다. System.Runtime을 추가하는 방법은 [관리되는 데스크톱 앱 및 Windows 런타임](https://msdn.microsoft.com/library/windows/apps/jj856306.aspx#consuming_standard_windows_runtime_types)을 참조하세요.

### <a name="extensions-subgroup"></a>확장명 하위 그룹
 확장 하위 그룹은 대상 Windows 플랫폼을 확장하는 사용자 SDK를 나열합니다. 이 탭은 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱 프로젝트의 경우에만 나타납니다. 데스크톱 프로젝트의 경우 자사 .winmd 파일만 사용할 수 있으므로 이 탭이 표시되지 않습니다.

 SDK는 Visual Studio에서 단일 구성 요소로 처리하는 파일의 컬렉션입니다. 확장 탭에서, **참조 관리자** 대화 상자가 호출 된 프로젝트에 적용 되는 sdk는 단일 항목으로 나열 됩니다. SDK 콘텐츠는 프로젝트에 추가되면 모두 Visual Studio에서 사용되므로 IntelliSense, 도구 상자, 디자이너, 개체 브라우저, 빌드, 배포, 디버깅, 패키지의 SDK 콘텐츠를 활용하기 위해 사용자가 어떠한 추가 작업도 수행할 필요가 없습니다. 확장 탭에서 SDK를 표시하는 방법은 [방법: 소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)를 참조하세요.

> [!NOTE]
> 프로젝트가 다른 SDK에 종속적인 SDK를 참조하는 경우, Visual Studio에서는 사용자가 수동으로 두 번째 SDK에 대한 참조를 추가하지 않는 한 두 번째 SDK가 사용되지 않습니다. 사용자가 **확장명** 탭에서 SDK를 선택하면, **참조 관리자** 대화 상자를 통해 사용자는 SDK의 이름 및 버전뿐만 아니라 세부 정보 창에서 SDK 종속성의 이름을 나열하여 SDK 종속성을 식별할 수 있습니다. 사용자가 종속성을 알리지 않고 해당 SDK를 추가하는 경우, MSBuild에서는 사용자에게 종속성을 추가하라는 메시지를 표시합니다.

 프로젝트 형식이 **확장명**을 지원하지 않으면 **참조 관리자** 대화 상자에 이 탭이 나타나지 않습니다.

## <a name="browse-button"></a>찾아보기 단추
 **찾아보기** 단추를 사용하여 파일 시스템의 구성 요소를 찾아볼 수 있습니다.

 프로젝트는 다른 버전의 .NET Framework를 대상으로 하는 구성 요소를 참조할 수 있습니다. 예를 들어, .NET Framework 2를 대상으로 하는 구성 요소를 참조하는 .NET Framework 4 Client Profile을 대상으로 하는 애플리케이션을 만들 수 있습니다. 자세한 내용은 [특정 대상 .NET Framework 버전 지정](../ide/targeting-a-specific-dotnet-framework-version.md)을 참조하세요.

 동일한 솔루션에 있는 다른 프로젝트의 출력에 대한 파일 참조를 추가하면 컴파일 오류가 발생할 수 있으므로 이 방법은 사용하지 않는 것이 좋습니다. 대신 **참조 관리자** 대화 상자의 **솔루션** 탭을 사용 하 여 프로젝트 간 참조를 만들 수 있습니다. 이 방법을 통해 프로젝트에서 만드는 클래스 라이브러리를 보다 효율적으로 관리할 수 있으므로 팀 개발이 쉬워집니다. 자세한 내용은 [끊어진 참조 문제 해결](../ide/troubleshooting-broken-references.md)을 참조하세요.

 SDK를 찾아 프로젝트에 추가할 수는 없습니다. 파일(예: 어셈블리 또는 .winmd)만 찾아 프로젝트에 추가할 수 있습니다.

 WinMD에 대한 파일 참조를 수행하는 경우, 예상되는 레이아웃은 *FileName*.winmd, *FileName*.dll 및 *FileName*.pri 파일이 모두 나란히 배치되는 것입니다. 다음과 같은 시나리오에서 WinMD를 참조하는 경우, 불완전한 파일 집합이 프로젝트 출력 디렉터리에 복사되고, 그에 따라 빌드 및 런타임 오류가 발생합니다.

- **기본 구성 요소**: 네이티브 프로젝트에서는 연결되지 않은 네임스페이스 집합 각각에 대한 하나의 WinMD 및 그 구현으로 구성된 하나의 DLL을 만듭니다. WinMD는 서로 다른 이름을 갖게 됩니다. 이 기본 구성 요소 파일을 참조하는 경우, MSBuild에서는 서로 다른 이름을 가진 WinMD에서 하나의 구성 요소를 만드는 것을 인식하지 못합니다. 따라서 동일한 이름의 *FileName*.dll 및 *FileName*.winmd만 복사되어 런타임 오류가 발생합니다. 이 문제를 해결하기 위해서는 확장명 SDK를 만듭니다. 자세한 내용은 [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)를 참조하세요.

- **컨트롤 사용**: XAML 컨트롤은 최소한 *FileName*.winmd, *FileName*.dll, *FileName*.pri, *XamlName*.xaml 및 *ImageName*.jpg로 구성됩니다. 프로젝트를 빌드할 때 파일 참조와 연관된 리소스 파일은 프로젝트의 출력 디렉터리에 복사되지 않고 *FileName*.winmd, *FileName*.dll 및 *FileName*.pri만 복사됩니다. 빌드 오류가 기록되어 사용자에게 리소스 *XamlName*.xaml 및 *ImageName*.jpg가 누락되었음을 알려줍니다. 성공적으로 빌드하려면 사용자는 이러한 리소스 파일을 수동으로 빌드 및 디버깅/런타임용 프로젝트 출력 디렉터리에 복사해야 합니다. 이 문제를 해결하려면 [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)의 단계에 따라 확장명 SDK를 만들거나, 프로젝트 파일을 편집하여 다음 속성을 추가합니다.

    ```
    <PropertyGroup>
    <GenerateLibraryOutput>True</GenerateLibraryOutput>
    </PropertyGroup>
    ```

    > [!NOTE]
    > 이 속성을 추가하면 빌드 실행이 느려질 수 있습니다.

## <a name="recent"></a>최근 항목
 어셈블리, COM, Windows 및 찾아보기 탭 각각은 최근에 프로젝트에 추가된 구성 요소의 목록을 열거하는 최근 항목 탭을 지원합니다.

## <a name="search"></a>검색
 **참조 관리자** 대화 상자의 검색 모음은 포커스가 있는 탭에 대해 작동 합니다. 예를 들어, 사용자가 **솔루션** 탭에 포커스가 있을 때 검색 창에 "system"을 입력 하면 솔루션이 "system"을 포함 하는 프로젝트 이름으로 구성 되어 있지 않으면 검색 결과가 반환 되지 않습니다.

## <a name="see-also"></a>관련 항목
 [NIB 방법: 참조 추가 대화 상자를 사용 하 여 참조 추가 또는 제거](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9) [프로젝트에서 참조 관리](../ide/managing-references-in-a-project.md)
