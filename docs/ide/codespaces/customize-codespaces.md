---
title: codespace 사용자 지정(미리 보기)
description: codespace를 사용자 지정하는 방법을 자세히 알아봅니다.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: f63dc4989a59256a0a3ad59491b2290912ffd2f8
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90862359"
---
# <a name="how-to-customize-a-codespace-preview"></a>codespace를 사용자 지정하는 방법(미리 보기)

GitHub Codespaces는 클라우드에서 완전한 개발 환경을 제공합니다. Visual Studio 2019를 사용한 Windows 기반 개발의 경우 GitHub Codespaces 기본 인스턴스로 시작하는 것도 좋지만 특정 프로젝트의 환경을 사용자 지정할 수도 있습니다.

## <a name="installed-software"></a>설치된 소프트웨어

Windows codespace에는 많은 프레임워크 및 도구가 이미 설치되어 있으므로 바로 시작할 수 있습니다. 아래 표에는 모든 Windows codespace 환경에서 사용할 수 있는 애플리케이션 및 기능이 나와 있습니다.

| 앱                                         | 경로 별칭 | 버전            |
|---------------------------------------------|------------|--------------------|
| .NET                                        | 해당 없음        | 4.8                |
| .NET Core 런타임                           | dotnet     | 2.1, 3.1           |
| .NET Core SDK                               | dotnet     | 2.1, 3.1.3, 3.1.4  |
| Azure CLI                                   | az         | 2.5                |
| Chocolatey                                  | choco      | 0.10.15            |
| CMake                                       | cmake      | 3.17               |
| Git                                         | git        | 2.26               |
| Microsoft Build                             | msbuild    | 16.7               |
| Microsoft SQL Server Express Edition 2019   | 해당 없음        | 15.0               |
| Ninja                                       | ninja      | 1.8.2              |
| Node.js                                     | node       | 12.16              |
| NPM                                         | npm        | 6.14               |
| Python                                      | python     | 3.7                |
| VC 패키지 관리자                          | vcpkg      | 2020.02            |
| Windows SDK                                 | 해당 없음        | 10.0.18362         |

위 목록은 전체 목록이 아니며 Visual Studio가 설치하는 많은 도구(예: IISExpress)가 제외되어 있습니다. 구성 요소에는 위에서 위에 언급한 것과 다른 부 버전이나 패치 버전이 있을 수도 있습니다.

사전 설치된 프레임워크 및 도구에 대한 자세한 내용은 아래 [설치된 소프트웨어 세부 정보](#installed-software-specifics) 섹션을 참조하세요.

## <a name="modifications-to-a-codespace"></a>codespace 수정
 
codespace를 만든 후에는 GitHub Codespaces에서 codespace 인스턴스가 제공되는 동안 해당 codespace의 모든 변경 내용이 유지됩니다. 추가 리포지토리를 복제하고, 도구 및 애플리케이션 생성기를 설치하고, 기타 개발 자산을 추가할 수 있으며, 해당 수정 내용은 codespace가 일시 중단된 경우에도 유지됩니다. 그러나 codespace를 삭제하면 모든 수정 내용이 사라집니다.

> [!NOTE]
> codespace를 삭제하면 codespace에 있는 로컬 리포지토리의 모든 변경 내용(보류 중 또는 커밋됨)이 손실됩니다. codespace를 삭제하기 전에 리포지토리 변경 내용을 원격 위치에 푸시해야 합니다.

Visual Studio를 사용하여 codespace에 연결된 동안 명령줄 도구 실행을 위해 Visual Studio 터미널을 사용할 수 있습니다. 둘 다 로컬 관리자 계정으로 권한이 상승된 PowerShell 또는 Windows 명령 프롬프트를 사용할 수 있습니다. Visual Studio 터미널에 관해 자세히 알아보려면 [Visual Studio 터미널 알림 블로그](https://devblogs.microsoft.com/visualstudio/say-hello-to-the-new-visual-studio-terminal/)를 참조하세요.

## <a name="customize-a-codespace"></a>codespace 사용자 지정

GitHub Codespaces의 진정한 가치는 팀 작업뿐 아니라 고유한 개인 작업에 맞게 조정된 클라우드의 반복 가능한 고유 개발 환경을 만들 수 있을 때 나타납니다. 기본 GitHub Codespaces 인스턴스를 빌드하면 새 codespace를 만들 때 설치 및 구성되는 항목을 사용자 지정할 수 있습니다.

다음 섹션에서는 *.devcontainer.json* 및 *.devinit.json* 파일을 사용하는 두 가지 codespace 구성 방법을 설명합니다. 해당 파일을 사용하여 codespace용으로 설치 프레임워크 및 도구를 구성할 수 있으며, 리포지토리에 추가되면 리포지토리를 기반으로 하는 codespace를 만드는 모든 사용자가 동일한 원격 개발 환경을 사용합니다.

## <a name="customize-with-devcontainerjson"></a>devcontainer.json을 사용하여 사용자 지정

codespace를 만들 때 GitHub Codespaces는 리포지토리의 루트에서 [*devcontainers.json*](https://code.visualstudio.com/docs/remote/devcontainerjson-reference) 파일을 검색하고, 파일 내 설정을 사용하여 codespace 또는 연결된 클라이언트 인스턴스를 사용자 지정합니다(브라우저 기반 편집기, Visual Studio 또는 Visual Studio Code). *devcontainer.json* 설정은 대부분 Linux 기반 codespace 또는 다른 두 클라이언트에 적용되지만 일부는 Windows codespace 및 Visual Studio에서 사용할 수 있습니다.

*devcontainer.json* 파일은 리포지토리의 두 위치 중 하나에 배치될 수 있습니다.

1. *{repository-root}/.devcontainer.json*
2. *{repository-root}/.devcontainer/devcontainer.json*

GitHub Codespaces는 다음 *devcontainer.json* 속성을 지원합니다. Visual Studio 외에 다른 클라이언트를 사용하여 codespace에 연결해야 하는 경우 Visual Studio Code 관련 속성을 설정하는 것이 유용합니다. 

* `extensions` - 설치해야 하는 [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/vscode) 확장의 배열입니다.
* `settings`  - 적용할 [Visual Studio Code 설정](https://code.visualstudio.com/docs/getstarted/settings) 세트입니다.
* `forwardPorts` - codespace가 실행 중일 때 로컬로 자동으로 전달해야 하는 포트 또는 포트 배열입니다.
* `postCreateCommand` - codespace를 만든 후 실행할 명령 문자열 또는 명령 인수 목록입니다.

> [!NOTE]
> **devcontainer.json** 파일은 Visual Studio Code [원격 개발](https://code.visualstudio.com/docs/remote/remote-overview)을 지원하는 데 사용되며 이 문서에서 다루지 않는 추가 속성을 포함합니다. 해당 추가 속성은 파일에 안전하게 추가할 수 있지만 Codespaces에서 무시됩니다. 자세한 내용은 code.visualstudio.com에서 [devcontainer.json 참조](https://code.visualstudio.com/docs/remote/devcontainerjson-reference)를 참조하세요.

## <a name="customize-with-devinit"></a>devinit를 사용하여 사용자 지정

[devinit](../../devinit/getting-started-with-devinit.md)는 프레임워크 및 도구를 환경에 설치하도록 해주는 Windows codespace에 포함된 명령줄 도구입니다. 명령 프롬프트(`devinit -t require-dotnetcoresdk`)에서 수동으로 실행할 수 있지만 실제 기능은 사용자 지정 [ *.devinit.json*](../../devinit/devinit-json.md) 파일을 만들어 만들 때마다 codespace를 균일하게 구성하는 작업을 기반으로 합니다.

`devinit`에는 SQL Server 및 Azure CLI 같은 특정 항목을 설치하고 chocolatey, npm, vcpkg 등의 일반 패키지 관리자도 실행하는 도구 집합이 포함됩니다. `devinit` 도구의 전체 목록은 [사용 가능한 도구](../../devinit/devinit-tool-list.md) 설명서에서 찾을 수 있습니다.

### <a name="devinitjson"></a>devinit.json

`devinit` 명령줄을 직접 실행할 수 있지만 실행할`devinit` 도구 집합을 설명하는 [*devinit.json*](../../devinit/devinit-json.md) 구성 파일을 만드는 것이 좋습니다. 

예를 들어 [.NET Core SDK](https://docs.microsoft.com/dotnet/core/sdk)를 설치하기 위한 *.devinit.json*은 다음과 같이 표시됩니다.

```json
{
    "run": [
        {
            "comments": "We need the .NET Core SDK."
            "tool": "require-dotnetcoresdk"
        }
    ]
}
```

프로젝트 루트에서 *.devinit.json* 파일을 작성하면 `devinit init`를 실행할 때 해당 파일이 사용됩니다. 기본적으로 `devinit.exe`는 다음 위치에서 파일을 검색합니다.

1. *{current-directory}\\.devinit.json*
2. *{current-directory}\\.devinit\devinit.json*

### <a name="running-devinit-when-creating-a-codespace"></a>codespace를 만들 때 devinit 실행

*devcontainers.json* 파일의 `postCreateCommand` 속성을 사용하여 codespace를 만든 후 `devinit`를 실행하도록 GitHub Codespaces에 지시할 수 있습니다. 위에 언급한 대로 GitHub Codespaces는 codespace 또는 클라이언트 인스턴스를 사용자 지정하기 위해 복제된 리포지토리에서 *devcontainer.json* 파일을 검색하고 `postCreateCommand` 속성에 설명된 모든 명령을 실행합니다.

`devinit init`를 지정하면 `devinit`는 *devinit.json* 구성을 사용하여 실행됩니다.

```json
{
  "postCreateCommand": "devinit init"
}
```

### <a name="an-example"></a>예제

.NET Core Entity Framework 명령줄 도구인 `dotnet-ef`를 설치하는 간단한 예제는 다음과 같습니다.

**devcontainer.json**

리포 루트에 있는 *.devcontainer.json* 파일의 콘텐츠입니다. 

```json
{
  "postCreateCommand": "devinit init"
}
```

**devinit.json**

*.devinit.json* 파일의 콘텐츠입니다. 해당 파일은 *.devcontainer.json*과 동일한 폴더에 있어야 합니다.

```json
{
    "run": [
        {
            "comments": "Install the Entity Framework tools",
            "tool": "dotnet-toolinstall",
            "input": "dotnet-ef",
        }
     ]
}
```

`devinit` [샘플 목록](../../devinit/sample-readme.md)에서 더 많은 `devinit` 예제를 찾을 수 있습니다.

## <a name="port-forwarding"></a>포트 전달

GitHub Codespaces는 포트 전달을 통해 원격 환경에서 실행되는 애플리케이션 및 서비스에 대한 액세스를 제공합니다. 기본적으로 보안상 이유로 포트는 전달되지 않습니다. 그러나 codespace에서 열려는 특정 포트를 지정할 수 있습니다.

### <a name="configure-port-forwarding"></a>포트 전달 구성

지정된 리포지토리에 대해 기본적으로 전달해야 하는 포트가 하나 이상 있는 경우 *devcontainer.json*에서 `forwardPorts` 속성을 사용하여 구성할 수 있습니다.

* `forwardPorts` - 환경이 실행 중일 때 로컬로 자동으로 전달해야 하는 포트 또는 포트 배열입니다.

## <a name="installed-software-specifics"></a>설치된 소프트웨어 세부 정보

### <a name="microsoft-sql-server"></a>Microsoft SQL Server

Microsoft SQL Server 2019 Express Edition이 Windows Codespace 환경에서 제공되며 로컬 서비스(localdb)로 실행됩니다. 앱과 Visual Studio 터미널을 실행하는 현재 사용자는 SQL Server에 대한 SQL 관리자 권한을 가집니다. 서버를 관리하려면 Visual Studio 터미널에서 PowerShell을 사용하거나 `dotnet-ef`와 같은 기타 명령줄 도구를 사용해야 합니다. 현재는 SQL Server Management Studio 및 기타 원격 관리 도구를 사용할 수 없습니다.

#### <a name="example-connection-string"></a>연결 문자열 예제

로컬 MS SQL Server에 연결하기 위한 연결 문자열의 예제는 다음과 같습니다.

```csharp
"Server=(LocalDB);Integrated Security=true;"
```

### <a name="azure-cli"></a>Azure CLI

Azure CLI는 모든 Windows Codespace 환경에 설치되며 경로에서 `az`로 사용할 수 있습니다.

#### <a name="using-azure-resources"></a>Azure 리소스 사용

Azure Active Directory ID를 사용하여 Azure 리소스에 대해 애플리케이션을 인증하는 경우 먼저 Visual Studio 터미널에서 Azure에 로그인해야 합니다. 로그인하려면 아래 예제와 같이 디바이스 로그인 흐름에서 Azure CLI `login` 명령을 사용합니다. 로그인되면 애플리케이션 및 터미널 세션에서 해당 ID를 사용할 수 있습니다.

```powershell
> az login --use-device-code
```

Azure CLI [설명서](/cli/azure/reference-index#az_login)에서 `az login` 명령에 관해 자세히 알아볼 수 있습니다.

## <a name="see-also"></a>추가 정보

- [GitHub Codespaces란?](codespaces-overview.md)
- [codespace와 함께 Visual Studio를 사용하는 방법](use-visual-studio-with-codespaces.md)