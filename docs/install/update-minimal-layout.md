---
title: 최소 오프라인 레이아웃을 사용하여 Visual Studio 업데이트
description: 최소 오프라인 레이아웃을 사용하여 Visual Studio를 업데이트하는 방법을 알아봅니다.
ms.date: 07/21/2020
ms.custom: seodec18
ms.topic: how-to
ms.assetid: ''
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2b9c86c17b89258145613e867ba6a91b2219fe0d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "88168751"
---
# <a name="update-visual-studio-using-a-minimal-offline-layout"></a>최소 오프라인 레이아웃을 사용하여 Visual Studio 업데이트

인터넷에 연결되지 않은 컴퓨터의 경우 최소 레이아웃을 만드는 것이 오프라인 Visual Studio 인스턴스를 업데이트하는 가장 쉽고 빠른 방법입니다.

최소 레이아웃 도구는 팀 요구 사항에 맞게 특별히 조정된 레이아웃을 생성합니다. 엔터프라이즈 관리자는 이 도구를 사용하여 대부분의 Visual Studio 2017 및 2019 버전의 업데이트 레이아웃을 만들 수 있습니다. 전체 Visual Studio 레이아웃과 달리 최소 레이아웃에는 업데이트된 패키지만 포함되므로 항상 더 작고 빠르게 생성하고 배포할 수 있습니다. 원하는 언어, 워크로드, 구성 요소만 지정하여 업데이트 레이아웃의 크기를 더욱 최소화할 수 있습니다.

## <a name="how-to-generate-a-minimal-layout"></a>최소 레이아웃을 생성하는 방법

> [!IMPORTANT]
> 이 지침에서는 이전에 레이아웃을 만들고 사용했다고 가정합니다. 해당 작업을 수행하는 방법에 대한 자세한 내용은 [네트워크 기반의 Visual Studio 설치 업데이트](update-a-network-installation-of-visual-studio.md) 페이지를 참조하세요.
>
> Visual Studio 수명 주기에 대한 자세한 내용은 [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing) 페이지를 참조하세요.
>

이 도구는 Visual Studio 2017(15.9) 이상의 업데이트 레이아웃을 만듭니다. 레이아웃을 네트워크/오프라인 머신에 배포하여 Visual Studio 인스턴스를 업데이트할 수 있습니다. [일반 레이아웃 생성](update-a-network-installation-of-visual-studio.md) 과정에서는 해당 릴리스의 모든 패키지가 다운로드됩니다. Visual Studio 인스턴스에서 복구, 제거 및 기타 표준 작업을 수행하려면 일반 레이아웃을 만들어야 합니다. 최소 레이아웃은 업데이트된 패키지만 다운로드하므로 더 작고 편리하게 오프라인 머신에 복사할 수 있습니다.

### <a name="installing-the-minimal-layout-tool"></a>최소 레이아웃 도구 설치
 
 1. 먼저 [여기](https://aka.ms/vs/installer/minimallayout)에 있는 최소 레이아웃 도구를 다운로드합니다. 메시지가 표시되면 **저장**을 선택한 후 **실행**을 선택해야 합니다.

     ![최소 레이아웃 도구 저장](media/save-minimal-layout.png)

 2. **예**를 클릭하여 사용자 계정 컨트롤 프롬프트를 수락합니다.

     ![사용자 계정 컨트롤 수락](media/accept-user-account-control.png)

 3. 최소 레이아웃 도구가 `C:\Program Files (x86)\Microsoft Visual Studio\MinimalLayout`에 설치됩니다.

### <a name="how-to-use-the-minimal-layout-tool"></a>최소 레이아웃 도구를 사용하는 방법

`MinimalLayout.exe`에서는 다음 명령과 옵션을 사용하여 레이아웃을 생성합니다. 도구를 실행하려면 하나 이상의 명령이 필요합니다. 도구를 실행하는 방법은 다음과 같습니다.

```MinimalLayout.exe [command] <options>...```

#### <a name="commands"></a>명령
* **미리 보기**: 이 명령을 사용하면 다운로드하는 패키지 수와 이 레이아웃을 만드는 데 사용하는 총 공간을 미리 볼 수 있습니다. 
* **Generate**: 이 명령을 사용하면 Visual Studio를 업데이트하기 위한 최소 레이아웃을 생성할 수 있습니다.
* **Regenerate**: 이 명령을 사용하면 기존의 최소 레이아웃 지시 파일로 레이아웃을 다시 생성할 수 있습니다. 모든 최소 레이아웃은 원본 최소 레이아웃 입력 매개 변수가 포함된 `MinimalLayout.json` 지시 파일을 생성합니다. **Regenerate** 명령과 `MinimalLayout.json` 지시 파일을 사용하여 최소 레이아웃을 다시 생성할 수 있습니다. 이 명령은 이전의 최소 레이아웃 지시 파일을 기준으로 새 Visual Studio 업데이트의 최소 레이아웃을 만들려는 경우에 유용합니다.

   이 명령을 사용하려면 이미 생성된 레이아웃의 `MinimalLayout.json` 파일 경로가 필요합니다. 

    ```cmd
    MinimalLayout.exe regenerate --filePath C:\MinimalLayout\MinimalLayout.json
    ```

* **Verify**: 이 명령을 사용하면 레이아웃 폴더가 손상되었는지 여부를 확인할 수 있습니다.
* **Fix**: 이 명령을 사용하면 레이아웃 폴더에서 누락된 패키지를 다시 배치하는 등 손상된 레이아웃 폴더를 수정할 수 있습니다.

#### <a name="options"></a>옵션 

|옵션    |Description    |필수/선택 |예제 |
|:----------|:-----------|:------------|:--------------|
|--targetLocation &lt;dir&gt; |최소 오프라인 레이아웃을 만들 디렉터리를 지정합니다.       |필요한 공간        |--targetLocation c:\VSLayout\ |
|--baseVersion &lt;버전&gt;|이 버전부터 최소 오프라인 레이아웃이 생성됩니다.   |필요한 공간|--baseVersion 16.4.0 |
|--targetVersion &lt;버전&gt;|이 버전까지 최소 오프라인 레이아웃이 생성됩니다.|필요한 공간|--targetVersion 16.4.4|
|--languages    |최소 오프라인 레이아웃에 포함할 언어를 지정합니다. 여러 값을 공백으로 구분하여 지정할 수 있습니다.    |필요한 공간    |--languages en-US fr-FR |
|--productId &lt;id&gt;    |최소 오프라인 레이아웃을 생성할 제품의 ID입니다. <br> <ul><li>Microsoft.VisualStudio.Product.Enterprise</li><li>Microsoft.VisualStudio.Product.Professional</li><li>Microsoft.VisualStudio.Product.BuildTools</li><li>Microsoft.VisualStudio.Product.TestAgent</li><li>Microsoft.VisualStudio.Product.TestController</li><li>Microsoft.VisualStudio.Product.TeamExplorer</li></ul>|필요한 공간|--productId Microsoft.VisualStudio.Product.Enterprise |
|--filePath    |이미 생성된 레이아웃에 속한 MinimalLayout.json 파일의 파일 경로입니다. 이 옵션은 Regenerate 명령에서만 사용됩니다.     |Regenerate 명령의 경우 필수    |--filePath C:\VSLayout\minimalLayout.json <br><br> **Regenerate 명령만 --filePath를 옵션으로 사용합니다.** |
|--add &lt;하나 이상의 워크로드 또는 구성 요소 ID&gt;    |추가할 워크로드 또는 구성 요소 ID를 하나 이상 지정합니다. --IncludeRecommended 및/또는 <br> –-includeOptional을 사용하여 추가 구성 요소를 전역적으로 추가할 수 있습니다. 여러 워크로드 또는 구성 요소 ID를 공백으로 구분하여 지정할 수 있습니다.    |Optional    |--add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb Component.GitHub.VisualStudio |
|--includeRecommended    |설치된 모든 워크로드에 대한 권장 구성 요소를 포함하지만, 선택적 구성 요소는 포함하지 않습니다.    |Optional    |특정 워크로드에 적용하려는 경우: <br> --add Microsoft.VisualStudio.Workload. ManagedDesktop;includeRecommended <br><br> 모든 워크로드에 적용하려는 경우: --includeRecommended |
|--includeOptional |권장 구성 요소를 비롯하여 설치된 모든 워크로드의 선택적 구성 요소를 포함합니다.    |Optional    |특정 워크로드에 적용하려는 경우: <br>--add Microsoft.VisualStudio.Workload. ManagedDesktop;includeOptional <br><br> 모든 워크로드에 적용하려는 경우: --includeOptional |

### <a name="generating-a-minimal-layout"></a>최소 레이아웃 생성

> [!IMPORTANT]
>  이 지침에서는 네트워크 설치 레이아웃을 이전에 만든 것으로 가정합니다. 이 작업을 수행하는 방법에 대한 자세한 내용은 [Visual Studio의 네트워크 설치 만들기](create-a-network-installation-of-visual-studio.md) 페이지를 참조하세요.

지정한 버전 범위에 대해 **generate** 명령을 사용하여 최소 레이아웃을 만듭니다. 또한 productId, 언어, 필요한 모든 특정 워크로드를 알고 있어야 합니다. 이 최소 레이아웃은 기본 버전부터 대상 버전까지 모든 Visual Studio 인스턴스를 업데이트합니다.

레이아웃을 만들기 전에 **preview** 명령을 사용하여 다운로드 전체 크기와 포함되는 패키지 수를 확인할 수 있습니다. 이 명령은 **generate** 명령과 동일한 옵션을 사용하며, 콘솔에 세부 정보가 기록됩니다.

최소 레이아웃을 미리 보고, 생성하고, 다시 생성하는 방법의 몇 가지 예를 살펴봅시다.

- 먼저 다음은 Visual Studio Enterprise 버전 16.4.0부터 16.4.4까지의 영어 전용 레이아웃을 미리 보는 방법의 예제입니다.

    ```cmd
    MinimalLayout.exe preview --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --languages en-US
    ```

- 다음은 단일 워크로드를 사용하여 동일한 레이아웃을 생성하는 방법입니다.

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US
    ```

- 다음은 기존 지시 파일을 사용하여 최소 오프라인 레이아웃을 다시 생성하는 방법입니다. 

    ```cmd
    MinimalLayout.exe regenerate -filepath c:\VSLayout\MinimalLayout.json
    ```

**generate** 명령을 사용하는 다른 몇 가지 예제는 다음과 같습니다.

- 다음은 워크로드를 더 추가하고 권장 패키지만 포함하는 방법입니다. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Professional --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop Microsoft.VisualStudio.Workload.NetWeb;includeRecommended --languages en-US
    ```

- 마지막으로, 다음은 최소 레이아웃에 여러 언어를 포함하는 방법입니다. 

    ```cmd
    MinimalLayout.exe generate --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeOptional --languages en-US fr-FR
    ```

### <a name="how-to-maintain-a-minimal-layout"></a>최소 레이아웃을 유지 관리하는 방법

**verify** 및 **fix** 명령을 사용하여 생성된 최소 레이아웃을 유지 관리할 수 있습니다. **verify** 명령은 최소 레이아웃에 손상되었거나 누락된 패키지가 있는지 여부를 확인합니다. **verify** 명령을 실행한 후 문제가 발견되면 **fix** 명령을 사용하여 누락되었거나 손상된 패키지를 수정합니다.

- 다음은 레이아웃에 손상되었거나 누락된 패키지가 있는지 여부를 확인하는 방법입니다. 

    ```cmd
    MinimalLayout.exe Verify --targetLocation c:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop --includeRecommended --languages en-US
    ```

- 다음은 해당 레이아웃을 수정하는 방법입니다.

    ```cmd
    MinimalLayout.exe fix --targetLocation C:\VSLayout\ --productId Microsoft.VisualStudio.Product.Enterprise --baseVersion 16.4.0 --targetVersion 16.4.4 --add Microsoft.VisualStudio.Workload.ManagedDesktop;includeRecommended --languages en-US
    ```

>[!NOTE] 
> 이 레이아웃을 사용하여 Visual Studio 설치를 복구할 수는 없습니다. 기존 Visual Studio 인스턴스를 복구하려면 [Visual Studio 복구](repair-visual-studio.md)를 참조하세요.
>

### <a name="how-to-use-a-minimal-offline-layout-to-update-an-existing-installation-of-visual-studio"></a>최소 오프라인 레이아웃을 사용하여 기존 Visual Studio 설치를 업데이트하는 방법

최소 레이아웃을 생성한 후 최소 레이아웃 폴더 전체를 클라이언트 머신에 복사할 수 있습니다. 이 작업은 컴퓨터가 원래 위치의 최소 레이아웃 폴더에 액세스할 수 없는 경우에 필요합니다.

폴더로 이동하여 부트스트래퍼 애플리케이션 이름을 확인합니다. 부트스트래퍼 애플리케이션 이름은 최소 레이아웃을 생성하는 동안 지정된 ProductId 값에 따라 다릅니다. 일반적인 예는 아래 표를 참조하세요.

|ProductId 값    |애플리케이션 이름|
|:-----------|:------------|
|Microsoft.VisualStudio.Product.Enterprise    |vs_enterprise.exe|
|Microsoft.VisualStudio.Product.Professional    |vs_professional.exe|
|Microsoft.VisualStudio.Product.BuildTools    |vs_buildtools.exe|

업데이트는 두 단계로 Visual Studio 인스턴스에 적용됩니다. 먼저 Visual Studio 설치 관리자를 업데이트한 다음, Visual Studio를 업데이트합니다.

1. **Visual Studio 설치 관리자 업데이트** 

    필요한 경우 `vs_enterprise.exe`를 올바른 부트스트래퍼 애플리케이션 이름으로 대체하여 다음 명령을 실행합니다. 

    ```cmd
    vs_enterprise.exe --quiet --update --offline C:\VSLayout\vs_installer.opc
    ```

2. **Visual Studio 애플리케이션 업데이트**

    Visual Studio를 업데이트하려면 업데이트할 Visual Studio 인스턴스의 installPath를 지정해야 합니다. 여러 개의 Visual Studio 인스턴스가 설치되어 있을 경우 각 인스턴스를 별도로 업데이트해야 합니다. 최소 레이아웃에 포함되지 않은 구성 요소가 설치되지 않도록 update 명령에 `–noWeb` 옵션을 지정하는 것이 좋습니다. 이렇게 하면 Visual Studio가 사용할 수 없는 상태로 방치되지 않습니다.

    installPath 명령줄 매개 변수를 적절하게 대체하여 다음 명령을 실행합니다. 올바른 부트스트래퍼 애플리케이션 이름도 사용해야 합니다.

    ```cmd
    vs_enterprise.exe update --noWeb --quiet --installpath "C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise"
    ```

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참조

* [Visual Studio 설치](install-visual-studio.md)
* [Visual Studio 관리자 가이드](visual-studio-administrator-guide.md)
* [명령줄 매개 변수를 사용하여 Visual Studio 설치](use-command-line-parameters-to-install-visual-studio.md)
* [Visual Studio 인스턴스 검색 및 관리 도구](tools-for-managing-visual-studio-instances.md)
* [지시 파일에서 설정을 정의하는 방법](automated-installation-with-response-file.md)
* [네트워크 기반 Visual Studio 배포에 대한 업데이트 제어](controlling-updates-to-visual-studio-deployments.md)
* [Visual Studio 제품 수명 주기 및 서비스](/visualstudio/releases/2019/servicing/)
