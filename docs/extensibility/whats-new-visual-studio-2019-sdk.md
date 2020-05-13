---
title: 비주얼 스튜디오 2019 SDK의 새로운 내용 | 마이크로 소프트 문서
ms.date: 03/29/2019
ms.topic: conceptual
ms.assetid: 4a07607b-0c87-4866-acd8-6d68358d6a47
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 187d3df4b5bcefefc0135c010c7d98951e9b3af8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740405"
---
# <a name="whats-new-in-the-visual-studio-2019-sdk"></a>Visual Studio 2019 SDK의 새로운 기능

비주얼 스튜디오 SDK에는 Visual Studio 2019에 대한 다음과 같은 새롭고 업데이트된 기능이 있습니다.

## <a name="synchronously-autoloaded-extensions-warning"></a>동기적으로 자동 로드된 확장 경고

이제 설치된 확장 중 시작 시 동기적으로 자동 로드되는 경우 경고가 표시됩니다. 동기화 자동 로드 된 [확장에서](synchronously-autoloaded-extensions.md)경고에 대 한 자세한 내용을 확인할 수 있습니다.

## <a name="single-unified-visual-studio-sdk"></a>단일 통합 비주얼 스튜디오 SDK

이제 단일 NuGet 패키지 [Microsoft.VisualStudio.SDK를](https://www.nuget.org/packages/microsoft.visualstudio.sdk)통해 모든 Visual Studio SDK 자산을 얻을 수 있습니다.

## <a name="editor-registration-enhancements"></a>편집자 등록 개선 사항

Visual Studio는 생성 이후 편집기에서 특정 확장(예: .xaml 및 .rc)에 대한 선호도를 선언하거나 모든 확장(.*)에 적합한 사용자 지정 편집기 등록을 지원했습니다. Visual Studio 2019 버전 16.1부터 에디터 등록에 대한 지원을 확대합니다.

### <a name="filenames"></a>파일 이름

편집기는 특정 파일 확장명에 대한 지원을 등록하는 대신 편집기의 패키지에 새 `ProvideEditorFilename` 특성을 적용하여 특정 파일 이름을 지원한다고 등록할 수 있습니다.

예를 들어 모든 .json 파일을 지원하는 편집기는 이 `ProvideEditorExtension` 특성을 패키지에 적용합니다.

```cs
[ProvideEditorExtension(typeof(MyEditor), ".json", MyEditor.Priority)]
```

16.1부터 MyEditor가 잘 알려진 .json 파일 몇 개만 지원하는 경우 `ProvideEditorFilename` 대신 패키지에 이러한 특성을 적용할 수 있습니다.

```cs
[ProvideEditorFilename(typeof(MyEditor), "particular.json", MyEditor.Priority)]
[ProvideEditorFilename(typeof(MyEditor), "special.json",    MyEditor.Priority)]
```

### <a name="uicontexts"></a>UI컨텍스트

편집기는 활성화된 시기를 나타내는 하나 이상의 UIContexts를 등록할 수 있습니다. UIContexts는 편집기를 등록하는 패키지에 `ProvideEditorUIContextAttribute` 하나 이상의 인스턴스를 적용하여 등록됩니다.

편집기에서 UIContexts를 등록한 경우:

- 지정된 확장명이 있는 파일이 열릴 때 등록된 UIContext s 중 하나 이상이 활성 상태인 경우 편집기는 편집기 검색에 포함됩니다.
- 등록된 UIContexts가 활성 상태이지 않으면 편집기는 편집기 검색에 포함되지 않습니다.

편집기UIContexts를 등록 하지 않는 경우 해당 확장에 대 한 편집기 검색에 항상 포함 됩니다.

예를 들어 C# 프로젝트가 열려 있을 때만 편집기에서 사용할 수 있는 경우 특성을 적용하여 이 선호도를 `ProvideEditorUIContext` 선언할 수 있습니다.

```cs
[ProvideEditorUIContext(typeof(MyEditor), KnownUIContexts.CSharpProjectContext)]
```
