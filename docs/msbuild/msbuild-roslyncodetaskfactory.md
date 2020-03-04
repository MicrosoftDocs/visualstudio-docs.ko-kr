---
title: RoslynCodeTaskFactory를 사용한 MSBuild 인라인 작업 | Microsoft Docs
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ead738042b15c955aadb458c527253f3759b934e
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633228"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>RoslynCodeTaskFactory를 사용한 MSBuild 인라인 작업

[CodeTaskFactory](../msbuild/msbuild-inline-tasks.md)와 유사하게 RoslynCodeTaskFactory는 플랫폼 간 Roslyn 컴파일러를 사용하여 인라인 작업으로 사용하기 위한 메모리 내 작업 어셈블리를 생성합니다.  RoslynCodeTaskFactory 작업은 .NET Standard를 대상으로 하며 .NET Framework 및 .NET Core 런타임뿐만 아니라 Linux 및 Mac OS와 같은 다른 플랫폼에서도 작업할 수 있습니다.

>[!NOTE]
>RoslynCodeTaskFactory 작업은 MSBuild 15.8 이상에서만 사용할 수 있습니다.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>RoslynCodeTaskFactory를 사용한 인라인 작업의 구조

 RoslynCodeTaskFactory 인라인 작업은 [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md)와 동일한 방식으로 선언되며, 유일한 차이점은 .NET Standard를 대상으로 한다는 것입니다.  인라인 작업 및 이 작업을 포함하는 `UsingTask` 요소는 일반적으로 *.targets* 파일에 포함되며 필요할 때 다른 프로젝트 파일로 가져옵니다. 다음은 기본 인라인 작업입니다. 이 작업은 아무 것도 수행하지 않습니다.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 이 예제의 `UsingTask` 요소에는 작업 및 해당 작업을 컴파일하는 인라인 작업 팩터리를 설명하는 세 가지 특성이 있습니다.

- `TaskName` 특성은 작업의 이름을 지정합니다(이 경우 `DoNothing`).

- `TaskFactory` 특성은 인라인 작업 팩터리를 구현하는 클래스의 이름을 지정합니다.

- `AssemblyFile` 특성은 인라인 작업 팩터리를 위치를 지정합니다. 또는 `AssemblyName` 특성을 사용하여 일반적으로 GAC(전역 어셈블리 캐시)에 있는 인라인 작업 팩터리 클래스의 정규화된 이름을 지정할 수 있습니다.

`DoNothing` 작업의 나머지 요소는 비어 있으며 인라인 작업의 순서 및 구조를 보여 주기 위해 제공됩니다. 이 항목의 뒷부분에 보다 강력한 예제가 제공됩니다.

- `ParameterGroup` 요소는 선택적입니다. 이 요소를 지정하면 작업에 대한 매개 변수를 선언합니다. 입력 및 출력 매개 변수에 대한 자세한 내용은 이 항목 뒷부분에 나오는 [입력 및 출력 매개 변수](#input-and-output-parameters)를 참조하세요.

- `Task` 요소는 작업 소스 코드를 설명하고 포함합니다.

- `Reference` 요소는 코드에서 사용하는 .NET 어셈블리에 대한 참조를 지정합니다. 이 요소를 사용하는 것은 Visual Studio에서 프로젝트에 대한 참조를 추가하는 것과 같습니다. `Include` 특성은 참조된 어셈블리의 경로를 지정합니다.

- `Using` 요소는 액세스하려는 네임스페이스를 나열합니다. 이 요소는 Visual C#의 `Using` 문과 비슷합니다. `Namespace` 특성은 포함할 네임스페이스를 지정합니다.

`Reference` 및 `Using` 요소는 언어와 관련이 없습니다. 인라인 작업은 지원되는 .NET CodeDom 언어 중 하나(예: Visual Basic 또는 Visual C#)로 작성할 수 있습니다.

> [!NOTE]
> `Task` 요소에 의해 포함된 요소는 작업 팩터리(이 경우 코드 작업 팩터리)마다 고유합니다.

### <a name="code-element"></a>Code 요소

`Task` 요소 내에 마지막으로 나타나는 자식 요소는 `Code` 요소입니다. `Code` 요소는 작업으로 컴파일하려는 코드를 포함하거나 이러한 코드를 찾습니다. `Code` 요소에 포함하는 내용은 작업을 작성하려는 방법에 따라 다릅니다.

`Language` 특성은 코드가 작성된 언어를 지정합니다. 허용되는 값은 C#의 경우 `cs`, Visual Basic의 경우 `vb`입니다.

`Type` 특성은 `Code` 요소에서 발견되는 코드의 형식을 지정합니다.

- `Type` 값이 `Class`이면 `Code` 요소는 <xref:Microsoft.Build.Framework.ITask> 인터페이스에서 파생되는 클래스에 대한 코드를 포함합니다.

- `Type` 값이 `Method`이면 코드는 <xref:Microsoft.Build.Framework.ITask> 인터페이스의 `Execute` 메서드에 대한 재정의를 정의합니다.

- `Type` 값이 `Fragment`이면 코드는 서명 또는 `return` 문이 아니라 `Execute` 메서드의 내용을 정의합니다.

코드 자체는 일반적으로 `<![CDATA[` 표식 및 `]]>` 표식 사이에 나타납니다. 코드가 CDATA 섹션에 있으므로 "\<" 또는 ">"와 같은 예약 문자 이스케이프에 신경쓰지 않아도 됩니다.

또는 `Code` 요소의 `Source` 특성을 사용하여 작업에 대한 코드를 포함하는 파일의 위치를 지정할 수 있습니다. 소스 파일의 코드는 `Type` 특성으로 지정된 형식이어야 합니다. `Source` 특성이 있으면 `Type`의 기본값은 `Class`입니다. `Source`가 없으면 기본값은 `Fragment`입니다.

> [!NOTE]
> 소스 파일에서 클래스 이름을 정의할 때 클래스 이름은 [UsingTask](../msbuild/usingtask-element-msbuild.md) 요소의 `TaskName` 특성에 부합되어야 합니다.

## <a name="hello-world"></a>Hello World

 RoslynCodeTaskFactory를 사용한 보다 강력한 인라인 작업이 있습니다. HelloWorld 작업은 일반적으로 시스템 콘솔 또는 Visual Studio **출력** 창에 해당하는 기본 오류 로깅 디바이스에 "Hello, world!"를 표시합니다. 이 예제의 `Reference` 요소는 단지 설명을 위해 포함되었습니다.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

*HelloWorld.targets*라는 파일에 HelloWorld 작업을 저장한 다음, 다음과 같이 프로젝트에서 호출할 수 있습니다.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>입력 및 출력 매개 변수

 인라인 작업 매개 변수는 `ParameterGroup` 요소의 자식 요소입니다. 모든 매개 변수는 해당 매개 변수를 정의하는 요소의 이름을 사용합니다. 다음 코드는 매개 변수 `Text`를 정의합니다.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

매개 변수는 다음과 같은 특성을 하나 이상 포함할 수 있습니다.

- `Required`는 기본적으로 `false`인 선택적 특성입니다. `true`이면 매개 변수는 필수이며 작업을 호출하기 전에 값을 지정해야 합니다.

- `ParameterType`는 기본적으로 `System.String`인 선택적 특성입니다. System.Convert.ChangeType을 사용하여 특정 문자열로 변환되거나 이러한 문자열에서 변환될 수 있는 항목 또는 값에 해당하는 어떤 정규화된 형식으로도 설정될 수 있습니다. (즉, 외부 작업과 주고받을 수 있는 모든 형식을 나타냅니다.)

- `Output`는 기본적으로 `false`인 선택적 특성입니다. `true`이면 먼저 매개 변수에 값이 지정되어야 Execute 메서드에서 반환될 수 있습니다.

예를 들면 다음과 같습니다.

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

다음과 같은 세 개의 매개 변수를 정의합니다.

- `Expression`은 System.String 형식의 필수 입력 매개 변수입니다.

- `Files`는 필수 항목 목록 입력 매개 변수입니다.

- `Tally`는 System.Int32 형식의 출력 매개 변수입니다.

`Code` 요소에 `Fragment` 또는 `Method`의 `Type` 특성이 있는 경우 모든 매개 변수에 대해 자동으로 속성이 만들어집니다. 그렇지 않으면 작업 소스 코드에서 속성을 명시적으로 선언해야 하며 이러한 속성은 해당 매개 변수 정의와 정확히 일치해야 합니다.

## <a name="example"></a>예제

 다음 인라인 작업은 일부 메시지를 기록하고 문자열을 반환합니다.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>
</Project>
```

이러한 인라인 작업은 경로를 결합하고 파일 이름을 가져올 수 있습니다.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>
</Project>
```

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [연습: 인라인 작업 만들기](../msbuild/walkthrough-creating-an-inline-task.md)
