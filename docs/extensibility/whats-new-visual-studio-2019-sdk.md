---
title: Visual Studio 2019 SDK의 새로운 기능 | Microsoft Docs
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80740405"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Visual Studio 2019 SDK의 새로운 기능

Visual studio SDK에는 Visual Studio 2019에 대 한 다음과 같은 새롭고 업데이트 된 기능이 있습니다.

## <a name="synchronously-autoloaded-extensions-warning"></a>동기적으로 자동 로드 된 확장 경고

이제 설치 된 확장 중 하나라도 시작 시 동기적으로 자동 로드 되는 경우 사용자에 게 경고가 표시 됩니다. [동기적으로 자동 로드 된 확장](synchronously-autoloaded-extensions.md)에서 경고에 대해 자세히 알아볼 수 있습니다.

## <a name="single-unified-visual-studio-sdk"></a>단일 통합 Visual Studio SDK

이제 단일 NuGet 패키지 [VisualStudio](https://www.nuget.org/packages/microsoft.visualstudio.sdk)를 통해 모든 VISUAL Studio SDK 자산을 가져올 수 있습니다.

## <a name="editor-registration-enhancements"></a>편집기 등록 기능 향상

Visual Studio는 만든 사용자 지정 편집기 등록을 지원 하기 때문에 편집기에서 특정 확장명 (예: .xaml 및 .rc)에 대 한 선호도를 선언 하거나 확장 (. *)에 적합 한 사용자 지정 편집기를 등록할 수 있습니다. Visual Studio 2019 버전 16.1부터 편집기 등록에 대 한 지원이 확장 되었습니다.

### <a name="filenames"></a>파일 이름

편집기는 특정 파일 확장명에 대 한 지원을 등록 하거나 대신 새 `ProvideEditorFilename` 특성을 편집기의 패키지에 적용 하 여 특정 파일 이름을 지원 하도록 등록할 수 있습니다.

예를 들어 모든 json 파일을 지 원하는 편집기는 `ProvideEditorExtension` 해당 패키지에이 특성을 적용 합니다.

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

16.1부터 MyEditor는 잘 알려진 두 개의 json 파일만 지 원하는 경우 해당 패키지에 이러한 특성을 적용할 수 있습니다 `ProvideEditorFilename` .

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UIContexts

편집기는 사용 하도록 설정 된 경우를 나타내는 하나 이상의 UIContexts를 등록할 수 있습니다. UIContexts는 `ProvideEditorUIContextAttribute` 편집기를 등록 하는 패키지에 하나 이상의 인스턴스를 적용 하 여 등록 됩니다.

편집기에서 UIContexts를 등록 한 경우:

- 지정 된 확장명을 가진 파일을 열 때 등록 된 UIContexts 중 하나 이상이 활성화 되어 있으면 편집기 검색에 편집기가 포함 됩니다.
- 등록 된 UIContexts 활성화 되어 있지 않으면 편집기 검색에 편집기가 포함 되지 않습니다.

편집기에서 UIContexts를 등록 하지 않는 경우 해당 확장명에 대 한 편집기 검색에 항상 포함 됩니다.

예를 들어 c # 프로젝트를 열 때만 편집기를 사용할 수 있는 경우 특성을 적용 하 여이 선호도를 선언할 수 있습니다 `ProvideEditorUIContext` .

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
