---
title: Mac용 Visual Studio 확장
description: 확장 패키지라는 모듈을 사용하여 Mac용 Visual Studio의 기능을 확장할 수 있습니다. 이 가이드의 첫 번째 부분에서는 간단한 Mac용 Visual Studio 확장 패키지를 만들어 문서에 날짜와 시간을 삽입합니다. 이 가이드의 두 번째 부분에서는 확장 패키지 시스템의 기본 사항 및 Mac용 Visual Studio의 기초를 형성하는 몇 가지 핵심 API를 소개합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/20/2019
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: dd4db2502c65e9330bde5f475fc97b2e86a49e4a
ms.sourcegitcommit: 054815dc9821c3ea219ae6f31ebd9cd2dc8f6af5
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80544023"
---
# <a name="extending-visual-studio-for-mac"></a>Mac용 Visual Studio 확장

Mac용 Visual Studio는 *확장 패키지*라는 모듈 집합으로 구성됩니다. 확장 패키지를 사용하여 추가 언어 또는 새 프로젝트 템플릿 지원과 같은 새로운 기능을 Mac용 Visual Studio에 추가할 수 있습니다.

확장 패키지는 다른 확장 패키지의 *확장* 지점에서 빌드됩니다. 확장 지점은 메뉴, IDE 명령 목록 등 확장할 수 있는 영역에 대한 자리 표시자입니다. 새 메뉴 항목, 새 명령 등 확장이라는 구조화된 데이터 노드를 등록하여 확장 지점에서 확장 패키지를 빌드할 수 있습니다. 각 확장 지점은 *명령*, *패드*, *FileTemplate* 등 특정 형식의 확장을 허용합니다. 확장 지점을 포함하는 모듈은 다른 확장 패키지에 의해 확장될 수 있으므로 *추가 기능 호스트*라고 합니다.

Mac용 Visual Studio를 사용자 지정하려면 다음 다이어그램과 같이 Mac용 Visual Studio에서 기존 라이브러리 내의 추가 기능 호스트에 포함된 확장 지점을 통해 빌드되는 확장 패키지를 만듭니다.

![추가 기능 아키텍처](media/extending-visual-studio-mac-addin1.png)

Mac용 Visual Studio에서 확장 패키지를 빌드하려면 Mac용 Visual Studio IDE 내에 기존 확장 지점에서 빌드되는 확장이 있어야 합니다. 확장 패키지가 추가 기능 호스트에서 정의된 확장 지점을 사용하는 경우 해당 확장 패키지에 대한  _종속성_ 이 있다고 합니다.

이 모듈식 디자인의 이점은 Mac용 Visual Studio를 확장할 수 있다는 것입니다. 사용자 지정 확장 패키지로 빌드할 수 있는 많은 확장 지점이 있습니다. 현재 확장 패키지의 예로 C# 및 F# 지원, 디버거 도구, 프로젝트 템플릿 등이 있습니다.

> [!NOTE]
> Add-in Maker 1.2 이전에 만든 Add-in Maker 프로젝트가 있는 경우 [여기](https://mhut.ch/addinmaker/1.2)에 나와 있는 단계에 따라 프로젝트를 마이그레이션해야 합니다.

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

이 섹션에서는 Add-in Maker를 통해 생성되는 다양한 파일과 명령 확장에 필요한 데이터를 살펴보겠습니다.

## <a name="attribute-files"></a>특성 파일

확장 패키지는 이름, 버전, 종속성, 기타 정보에 대한 메타데이터를 C# 특성에 저장합니다. Add-in Maker는 `AddinInfo.cs` 및 `AssemblyInfo.cs`라는 두 개의 파일을 만들어 이 정보를 저장하고 구성합니다. 확장 패키지의 ‘ *특성’에 고유 ID와 네임스페이스가 지정되어 있어야 합니다.`Addin`*

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

또한 확장 패키지에서 연결되는 확장 지점을 소유한 확장 패키지에 대한 종속성을 선언해야 합니다. 이 종속성은 빌드 시간에 자동으로 참조됩니다.

또한 다음 이미지와 같이 프로젝트에 대한 Solution Pad의 추가 기능 참조 노드를 통해 참조를 더 추가할 수 있습니다.

![날짜 삽입 스크린샷](media/extending-visual-studio-mac-addin13.png)

해당 `assembly:AddinDependency` 특성도 빌드 시간에 추가됩니다. 메타데이터 및 종속성 선언이 구현되고 나면 확장 패키지의 필수 구성 요소에 집중할 수 있습니다.

## <a name="extensions-and-extension-points"></a>확장 및 확장 지점

확장 지점은 데이터 구조(형식)를 정의하는 자리 표시자인 반면, 확장은 특정 확장 지점에서 지정된 구조에 맞는 데이터를 정의합니다. 확장 지점은 해당 선언에서 허용할 수 있는 확장 형식을 지정합니다. 확장은 형식 이름 또는 확장 경로를 사용하여 선언됩니다. 필요한 확장 지점을 만드는 방법에 대한 자세한 내용은 [확장 지점 참조](https://github.com/mono/mono-addins/wiki/Extension-Points)를 참조하세요.

확장/확장 지점 아키텍처를 통해 Mac용 Visual Studio 개발이 신속한 모듈식 개발로 유지됩니다.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>명령 확장

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

명령 확장은 실행할 때마다 호출되는 메서드를 가리키는 확장입니다.

명령 확장은 `/MonoDevelop/Ide/Commands` 확장 지점에 항목을 추가하여 정의합니다. 다음 코드를 사용하여 `Manifest.addin.xml`에서 확장을 정의했습니다.

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <Command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaultHandler="DateInserter.InsertDateHandler" />
</Extension>
```

확장 노드에는 연결되는 확장 지점(이 경우 `/MonoDevelop/Ide/Commands/Edit`)을 지정하는 경로 특성이 있습니다. 또한 명령에 대한 부모 노드로 동작합니다. 명령 노드에는 다음과 같은 특성이 있습니다.

* `id` - 이 명령의 식별자를 지정합니다. 명령 식별자는 열거형 멤버로 선언되어야 하며 Commands를 CommandItems에 연결하는 데 사용됩니다.
* `_label` - 메뉴에 표시할 텍스트입니다.
* `_description` - 도구 모음 단추의 도구 설명으로 표시할 텍스트입니다.
* `defaultHandler` - 명령을 구동하는 `CommandHandler` 클래스를 지정합니다.

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

`/MonoDevelop/Ide/MainMenu/Edit` 확장 지점에 연결되는 CommandItem 확장은 다음 코드 조각에 나와 있습니다.

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

CommandItem은 해당 `id` 특성에 지정된 명령을 메뉴에 배치합니다. 이 CommandItem은 명령의 레이블을 `/MonoDevelop/Ide/MainMenu/Edit`편집 메뉴**에 표시하는**  확장 지점을 확장합니다. CommandItem의 ID는 명령 노드의 ID인 `InsertDate`에 해당합니다. CommandItem을 제거하면 **날짜 삽입** 옵션이 편집 메뉴에서 사라집니다.

### <a name="command-handlers"></a>명령 처리기

`InsertDateHandler`는 `CommandHandler` 클래스의 확장입니다. 두 가지 메서드 `Update` 및 `Run`을 재정의합니다. 명령이 메뉴에 표시되거나 키 바인딩을 통해 실행될 때마다 `Update` 메서드가 쿼리됩니다. 정보 개체를 변경하여 명령을 사용하지 않거나 보이지 않도록 설정하고, 배열 명령을 채우고, 기타 작업을 수행할 수 있습니다. 이 `Update` 메서드는 텍스트를 삽입할 *TextEditor*가 있는 활성 *문서*를 찾을 수 없는 경우 명령을 사용하지 않도록 설정합니다.

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

명령을 사용하도록 설정하거나 숨기기 위한 특수 논리가 있는 경우에만 `Update` 메서드를 재정의해야 합니다. `Run` 메서드는 사용자가 명령을 실행할 때마다 실행되며, 이 경우 사용자가 편집 메뉴에서 명령을 선택할 때 발생합니다. 이 메서드는 텍스트 편집기의 캐럿에 날짜와 시간을 삽입합니다.

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

`DateInserterCommands` 내에서 명령 형식을 열거형 멤버로 선언합니다.

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

이제 Command와 CommandItem이 연결되었습니다. **편집 메뉴**에서 CommandItem을 선택하면 CommandItem이 Command를 호출합니다.

## <a name="ide-apis"></a>IDE API

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

개발에 사용할 수 있는 영역의 범위에 대한 자세한 내용은 [확장 트리 참조](https://www.monodevelop.com/developers/articles/extension-tree-reference/) 및 [API 개요](https://www.monodevelop.com/developers/articles/api-overview/)를 참조하세요. 고급 확장 패키지를 빌드하는 경우 [개발자 문서](https://www.monodevelop.com/developers/articles/)도 참조하세요. 다음은 사용자 지정이 가능한 영역의 부분 목록입니다.

* 패드
* 키 바인딩 구성표
* 정책
* 코드 포맷터
* 프로젝트 파일 형식
* 기본 설정 패널
* 옵션 패널
* 디버거 프로토콜
* 디버거 시각화 도우미
* 작업 영역 레이아웃
* Solution Pad 트리 노드
* 소스 편집기 여백
* 단위 테스트 엔진
* 코드 생성기
* 코드 조각
* 대상 프레임워크
* 대상 런타임
* VCS 백 엔드
* 리팩터링
* 실행 처리기
* 구문 강조 표시

## <a name="extending-the-new-editor"></a>새 편집기 확장

Mac용 Visual Studio에서 [새로 도입된 네이티브 Cocoa 텍스트 편집기 UI](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes)는 Windows용 Visual Studio의 동일한 편집기 계층을 기반으로 해서 구축되었습니다.

Visual Studio와 Mac용 Visual Studio 간에 편집기를 공유할 경우의 많은 이점 중 하나는 Visual Studio 편집기를 대상으로 하는 코드를 Mac용 Visual Studio에서 실행되도록 조정할 수 있다는 것입니다.

> [!NOTE]
> 현재 새 편집기는 C# 파일만 지원합니다. 다른 언어 및 파일 형식은 레거시 편집기에서 열립니다. 하지만 레거시 편집기도 아래에 설명된 Visual Studio 편집기 API 중 일부를 구현합니다.

### <a name="visual-studio-editor-overview"></a>Visual Studio 편집기 개요

![Visual Studio 편집기 아키텍처](media/vs-editor-architecture.png)

Mac용 Visual Studio와 관련된 확장 정보를 살펴보기 전에 공유 편집기 자체를 자세히 파악하는 것이 도움이 됩니다. 공유 편집기를 깊이 이해하는 데 유용할 수 있는 몇 가지 리소스는 다음과 같습니다.

* [Managed Extensibility Framework](/dotnet/framework/mef/index)
* [편집기의 MEF](/visualstudio/extensibility/managed-extensibility-framework-in-the-editor)
* [편집기 기본 사항](/visualstudio/extensibility/inside-the-editor)
* [언어 서비스 및 편집기 확장 지점](/visualstudio/extensibility/language-service-and-editor-extension-points)
* [편집기 아키텍처 소개 비디오](https://www.youtube.com/watch?v=PkYVztKjO9A)

이러한 리소스에서 숙지해야 하는 기본 개념은 [`ITextBuffer`](/dotnet/api/microsoft.visualstudio.text.itextbuffer) 및 [`ITextView`](/dotnet/api/microsoft.visualstudio.text.editor.itextview)입니다.

* `ITextBuffer`는 시간이 지남에 따라 변경될 수 있는 텍스트의 메모리 내 표현입니다. `CurrentSnapshot`의 `ITextBuffer` 속성은 현재 버퍼 내용의 ‘변경이 불가능한’ 표현인  *인스턴스를 반환합니다.* `ITextSnapshot` 버퍼를 편집하면 CurrentSnapshot 속성이 최신 버전으로 업데이트됩니다. 분석기는 모든 스레드의 텍스트 스냅샷 및 해당 콘텐츠가 변경되지 않았는지 검사할 수 있습니다.

* `ITextView`는 화면의 편집기 컨트롤에서 `ITextBuffer`가 렌더링되는 방식의 UI 표현입니다. 해당 텍스트 버퍼에 대한 참조와 `Caret`, `Selection` 및 기타 UI 관련 개념이 있습니다.

지정된 [`MonoDevelop.Ide.Gui.Document`](http://source.monodevelop.com/#MonoDevelop.Ide/MonoDevelop.Ide.Gui/Document.cs,4e960d4735f089b5)에 연결된 기본 `ITextBuffer` 및 `ITextView`는 각각 `Document.GetContent<ITextBuffer>()` 및 `Document.GetContent<ITextView>()`를 통해 검색할 수 있습니다.

## <a name="additional-information"></a>추가 정보

> [!NOTE]
> Mac용 Visual Studio용 확장 시나리오 개선을 위해 현재 작업 중입니다. 확장을 만들고 있으며 추가 도움 또는 정보가 필요하거나 피드백을 제공하려는 경우 [Mac용 Visual Studio 확장 제작](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u) 양식을 작성해 주세요.

## <a name="see-also"></a>참고 항목

- [Visual Studio 확장 개발(Windows에서)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)
