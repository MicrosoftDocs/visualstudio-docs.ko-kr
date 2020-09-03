---
title: 프로젝트 디자이너, 빌드 이벤트 페이지(C#)
ms.date: 10/17/2019
ms.technology: vs-ide-compile
ms.topic: reference
f1_keywords:
- cs.ProjectPropertiesBuildEvents
helpviewer_keywords:
- build events
- Project Designer, Build Events page
- pre-build events
- post-build events
ms.assetid: 3fff9ae5-213c-46ea-a660-1d70acb6c922
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: a56093ab14b9be72f99e36b03eefe7abb895183f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85419057"
---
# <a name="build-events-page-project-designer-c"></a>프로젝트 디자이너, 빌드 이벤트 페이지(C#)

**프로젝트 디자이너**의 **빌드 이벤트** 페이지를 사용하여 빌드 구성 지침을 지정합니다. 또한 빌드 후 이벤트를 실행할 조건을 지정할 수 있습니다. 자세한 내용은 [방법: 빌드 이벤트 지정(C#)](../../ide/how-to-specify-build-events-csharp.md) 및 [방법: 빌드 이벤트 지정(Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)을 참조하세요.

## <a name="uielement-list"></a>UI 요소 목록

**구성**

이 컨트롤은 이 페이지에서 편집할 수 없습니다. 이 컨트롤에 대한 설명은 [프로젝트 디자이너, 빌드 페이지(C#)](../../ide/reference/build-page-project-designer-csharp.md)를 참조하세요.

**플랫폼**

이 컨트롤은 이 페이지에서 편집할 수 없습니다. 이 컨트롤에 대한 설명은 [프로젝트 디자이너, 빌드 페이지(C#)](../../ide/reference/build-page-project-designer-csharp.md)를 참조하세요.

**빌드 전 이벤트 명령줄**

빌드를 시작하기 전에 실행할 명령을 지정합니다. 긴 명령을 입력하려면 **빌드 전 편집**을 클릭하여 [빌드 전 이벤트/빌드 후 이벤트 명령줄](../../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md) 대화 상자를 표시합니다.

> [!NOTE]
> 프로젝트가 최신 상태이고 빌드가 트리거되지 않으면 빌드 전 이벤트가 실행되지 않습니다.

**빌드 후 이벤트 명령줄**

빌드가 끝난 후 실행할 명령을 지정합니다. 긴 명령을 입력하려면 **빌드 후 편집**을 클릭하여 **빌드 전 이벤트/빌드 후 이벤트 명령줄** 대화 상자를 표시합니다.

> [!NOTE]
> .bat 파일을 실행하는 모든 빌드 후 이벤트 명령 앞에 `call` 문을 추가합니다. 예를 들어 `call C:\MyFile.bat` 또는 `call C:\MyFile.bat call C:\MyFile2.bat`로 이름을 지정할 수 있습니다.

**빌드 후 이벤트 실행**

다음 표에 나와 있는 것처럼 실행할 빌드 후 이벤트에 대한 다음 조건을 지정합니다.

|옵션|결과|
|------------|------------|
|**항상**|빌드의 성공 여부에 관계 없이 빌드 후 이벤트가 실행됩니다.|
|**빌드가 성공한 경우**|빌드에 성공하면 빌드 후 이벤트가 실행됩니다. 따라서 이벤트는 빌드가 성공하는 한 최신 프로젝트에도 실행됩니다.|
|**빌드에서 프로젝트 출력을 업데이트한 경우**|컴파일러의 출력 파일(.exe 또는.dll)이 이전 컴파일러 출력 파일과 다른 경우에만 빌드 후 이벤트가 실행됩니다. 따라서 프로젝트가 최신 상태이면 빌드 후 이벤트가 실행되지 않습니다.|

## <a name="in-the-project-file"></a>프로젝트 파일에서:

이전 버전의 Visual Studio에서는 IDE의 **PreBuildEvent** 또는 **PostBuildEvent** 설정을 변경할 때 Visual Studio가 프로젝트 파일에 `PreBuildEvent` 또는 `PostBuildEvent` 속성을 추가합니다. 따라서 예를 들어 IDE의 **PreBuildEvent** 명령줄 설정이 다음과 같은 경우,

```input
"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)"
```

프로젝트 파일 설정은 다음과 같습니다.

```xml
<PropertyGroup>
    <PreBuildEvent>"$(ProjectDir)PreBuildEvent.bat" "$(ProjectDir)..\" "$(ProjectDir)" "$(TargetDir)" />
</PropertyGroup>
```

.NET Core 프로젝트의 경우 Visual Studio 2019 및 최신 업데이트 Visual Studio 2017은 **PreBuildEvent** 및 **PostBuildEvent** 설정에 대해 `PreBuild` 또는 `PostBuild`라는 MSBuild 대상을 추가합니다. 이러한 대상은 MSBuild에서 인식하는 **BeforeTargets** 및 **AfterTargets** 특성을 사용합니다. 예를 들어 앞의 예에서 Visual Studio는 이제 다음 코드를 생성합니다.

```xml
<Target Name="PreBuild" BeforeTargets="PreBuildEvent">
    <Exec Command="&quot;$(ProjectDir)PreBuildEvent.bat&quot; &quot;$(ProjectDir)..\&quot; &quot;$(ProjectDir)&quot; &quot;$(TargetDir)&quot;" />
</Target>
```

빌드 후 이벤트의 경우 이름 `PostBuild`를 사용하고 `AfterTargets` 특성을 `PostBuildEvent`로 설정합니다.

```xml
<Target Name="PostBuild" AfterTargets="PostBuildEvent">
   <Exec Command="echo Output written to $(TargetDir)" />
</Target>
```

> [!NOTE]
> SDK 스타일 프로젝트를 지원하기 위해 프로젝트 파일을 변경했습니다. 이전 형식에서 SDK 스타일 형식으로 프로젝트 파일을 수동으로 마이그레이션하는 경우, 앞의 코드에 나온 것처럼 `PreBuildEvent` 및 `PostBuildEvent` 속성을 삭제하고 `PreBuild` 및 `PostBuild` 대상으로 바꿔야 합니다. 프로젝트가 SDK 스타일 프로젝트인지 확인하는 방법을 알아보려면 [프로젝트 형식 확인](/nuget/resources/check-project-format)을 참조하세요.

## <a name="see-also"></a>참조

- [방법: 빌드 이벤트 지정(Visual Basic)](../../ide/how-to-specify-build-events-visual-basic.md)
- [방법: 빌드 이벤트 지정(C#)](../../ide/how-to-specify-build-events-csharp.md)
- [프로젝트 속성 참조](../../ide/reference/project-properties-reference.md)
- [컴파일 및 빌드](../../ide/compiling-and-building-in-visual-studio.md)
