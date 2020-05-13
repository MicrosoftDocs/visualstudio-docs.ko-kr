---
title: 지시 파일을 사용하여 설치 자동화
description: Visual Studio 설치를 자동화하는 데 도움이 되는 JSON 지시 파일을 만드는 방법을 알아봅니다.
ms.date: 03/30/2019
ms.custom: seodec18
ms.topic: conceptual
helpviewer_keywords:
- response file
- automate
- installation
- command-line
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ecdda55bbe4e79af01f8fb9a9a2b77f775548b10
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76115240"
---
# <a name="how-to-define-settings-in-a-response-file"></a>지시 파일에서 설정을 정의하는 방법

Visual Studio를 배포하는 관리자는 다음 예제와 같이 `--in` 매개 변수를 사용하여 지시 파일을 지정할 수 있습니다.

```cmd
vs_enterprise.exe --in customInstall.json
```

지시 파일은 명령줄 인수를 미러링하는 콘텐츠가 포함된 [JSON](http://json-schema.org/) 파일입니다.  일반적으로 명령줄 매개 변수가 인수를 사용하지 않으면(예: `--quiet`, `--passive` 등) 지시 파일의 값은 true/false여야 합니다.  매개 변수가 인수를 사용하면(예: `--installPath <dir>`) 지시 파일의 값은 문자열이어야 합니다.  매개 변수가 인수를 사용하고 명령줄에 두 번 이상 나타날 수 있으면(예: `--add <id>`) 값은 문자열 배열이어야 합니다.

매개 변수가 여러 입력을 사용하는 경우(예: `--add`)를 제외하고 명령줄에 지정된 매개 변수는 지시 파일의 설정을 재정의합니다. 여러 입력을 사용하는 경우 명령줄에 지정한 입력이 지시 파일의 설정과 병합됩니다.

## <a name="setting-a-default-configuration-for-visual-studio"></a>Visual Studio에 대한 기본 구성 설정

`--layout`을 사용하여 네트워크 레이아웃 캐시를 만든 경우 초기 `response.json` 파일은 레이아웃에서 만들어집니다. 부분 레이아웃을 만드는 경우 이 지시 파일에는 레이아웃에 포함된 워크로드 및 언어가 포함됩니다.  이 레이아웃에서 설치를 실행하면 자동으로 response.json 파일이 사용되어 레이아웃에 포함된 워크로드 및 구성 요소가 선택됩니다.  그래도 사용자는 Visual Studio를 설치하기 전에 설치 UI에서 워크로드를 선택하거나 선택 취소할 수 있습니다.

레이아웃을 만드는 관리자는 레이아웃의 `response.json` 파일을 수정하여 레이아웃에서 Visual Studio를 설치할 때 사용자에게 표시되는 기본 설정을 제어할 수 있습니다.  예를 들어 관리자가 특정 워크로드 및 구성 요소가 기본적으로 설치되도록 하려면 해당 항목을 추가하도록 `response.json` 파일을 구성할 수 있습니다.

Visual Studio 설치 프로그램을 레이아웃 폴더에서 실행하면 _자동으로_ 레이아웃 폴더의 지시 파일을 사용합니다.  `--in` 옵션을 사용할 필요가 없습니다.

오프라인 레이아웃 폴더에 만들어진 `response.json` 파일을 업데이트하여 이 레이아웃에서 설치하는 사용자의 기본 설정을 정의할 수 있습니다.

> [!WARNING]
> 레이아웃이 만들어질 때 정의된 기존 속성은 그대로 유지해야 합니다.

레이아웃의 기본 `response.json` 파일은 다음 예제와 유사하며, 여기에 설치할 제품 및 채널에 대한 값이 더 포함됩니다.

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise"
}
```

::: moniker-end

레이아웃을 만들거나 업데이트하면 response.template.json 파일도 만들어집니다.  이 파일에는 사용할 수 있는 모든 워크로드, 구성 요소 및 언어 ID가 포함됩니다.  이 파일은 사용자 지정 설치에 포함할 수 있는 모든 항목에 대한 템플릿으로 제공됩니다.  관리자는 이 파일을 사용자 지정 지시 파일을 만들기 위한 기준으로 삼을 수 있습니다.  설치하지 않을 항목에 대한 ID를 제거하고 고유한 지시 파일로 저장하면 됩니다.  response.template.json 파일의 경우 레이아웃이 업데이트되면 변경 내용이 손실되므로 사용자 지정하지 마세요.

## <a name="example-layout-response-file-content"></a>레이아웃 지시 파일 콘텐츠의 예

다음 예제에서는 6개의 일반 워크로드 및 구성 요소가 포함되고 영어 및 프랑스어 UI 언어가 모두 포함된 Visual Studio Enterprise를 설치합니다. 이 예제를 템플릿으로 사용할 수 있고, 이 경우 워크로드 및 구성 요소를 설치할 항목으로 변경하면 됩니다.

::: moniker range="vs-2017"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/15/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.15.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2017",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

::: moniker range="vs-2019"

```json
{
  "installChannelUri": ".\\ChannelManifest.json",
  "channelUri": "https://aka.ms/vs/16/release/channel",
  "installCatalogUri": ".\\Catalog.json",
  "channelId": "VisualStudio.16.Release",
  "productId": "Microsoft.VisualStudio.Product.Enterprise",

  "installPath": "C:\\VS2019",
  "quiet": false,
  "passive": false,
  "includeRecommended": true,
  "norestart": false,

  "addProductLang": [
    "en-US",
    "fr-FR"
    ],

    "add": [
        "Microsoft.VisualStudio.Workload.ManagedDesktop",
        "Microsoft.VisualStudio.Workload.Data",
        "Microsoft.VisualStudio.Workload.NativeDesktop",
        "Microsoft.VisualStudio.Workload.NetWeb",
        "Microsoft.VisualStudio.Workload.Office",
        "Microsoft.VisualStudio.Workload.Universal",
        "Component.GitHub.VisualStudio"
    ]
}
```

::: moniker-end

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>참고 항목

* [Visual Studio 작업 및 구성 요소 ID](workload-and-component-ids.md)
* [Visual Studio 설치 또는 사용 시의 네트워크 관련 오류 문제 해결](troubleshooting-network-related-errors-in-visual-studio.md)
