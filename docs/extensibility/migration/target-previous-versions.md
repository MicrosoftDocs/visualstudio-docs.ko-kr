---
title: Visual Studio 2022 미리 보기에서 확장을 만들 때 대상 Visual Studio 2019
description: Visual Studio 2022 Preview를 사용하여 프로젝트를 만드는 경우 Visual Studio 확장이 Visual Studio 2019에서 작동하도록 하는 방법을 알아봅니다.
ms.date: 06/08/2021
ms.topic: conceptual
author: leslierichardson95
ms.author: lerich
manager: jmartens
monikerRange: vs-2022
ms.workload:
- vssdk
ms.openlocfilehash: dcf556e271e6a805110eac0c978a845f2195e28f
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308606"
---
# <a name="target-a-previous-version-when-creating-an-extension-in-visual-studio-2022-preview"></a>Visual Studio 2022 미리 보기에서 확장을 만들 때 이전 버전을 대상으로 지정

[!INCLUDE [preview-note](../includes/preview-note.md)]

Visual Studio 2022 미리 보기를 사용하여 새 VSIX 프로젝트를 만들면 Visual Studio 2022를 대상으로 하는 템플릿에서 프로젝트가 만들어집니다. Visual Studio 2019 또는 이전 버전을 대상으로 하려면 만든 프로젝트를 수정해야 합니다.

[확장에서](update-visual-studio-extension.md#use-shared-projects-for-multi-targeting) 대부분의 또는 모든 코드를 공유하면서 공유 프로젝트를 사용하여 Visual Studio 2019 및 Visual Studio 2022를 대상으로 하는 것이 좋습니다.

Visual Studio 2019를 대상으로 하는 VSIX 프로젝트에서 다음 단계를 수행합니다.

1. 파일을 `source.extension.vsixmanifest` 편집하여 `ProductArchitecture` 요소 및 버전 범위를 제거합니다.

    ```diff
    -<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[17.0,18.0)">
    +<InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[16.0,17.0)">
    -  <ProductArchitecture>amd64</ProductArchitecture>
     </InstallationTarget>
    ```

   또한 필수 구성요소도 업데이트합니다.

    ```diff
    -<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[17.0,18.0)" DisplayName="Visual Studio core editor" />
    +<Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[16.0,17.0)" DisplayName="Visual Studio core editor" />
    ```

    파일을 검토하여 필요할 수 있는 다른 업데이트를 확인합니다.

1. 프로젝트 파일에서 참조하는 VS SDK 패키지의 버전을 변경합니다.

    ```diff
    -<PackageReference Include="Microsoft.VisualStudio.SDK" Version="17.0.0-preview.1" />
    +<PackageReference Include="Microsoft.VisualStudio.SDK" Version="16.0.206" />
    -<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="17.0.63-preview.1" />
    +<PackageReference Include="Microsoft.VSSDK.BuildTools" Version="16.10.32" />
    ```
