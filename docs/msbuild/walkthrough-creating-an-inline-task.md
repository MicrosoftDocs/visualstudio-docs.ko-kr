---
title: '연습: 인라인 작업 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70ce19a6dcd9c61b0e14d0d88c52072f59f87fb9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77631161"
---
# <a name="walkthrough-create-an-inline-task"></a>연습: 인라인 작업 만들기

MSBuild 작업은 일반적으로 <xref:Microsoft.Build.Framework.ITask> 인터페이스를 구현하는 클래스를 컴파일하여 생성됩니다. .NET Framework 버전 4부터 프로젝트 파일에서 인라인으로 작업을 만들 수 있습니다. 작업을 호스트할 별도의 어셈블리를 만들 필요가 없습니다. 자세한 내용은 [인라인 작업](../msbuild/msbuild-inline-tasks.md)을 참조하세요.

 이 연습에서는 이러한 인라인 작업을 만들고 실행하는 방법을 보여 줍니다.

- 입력 또는 출력 매개 변수가 없는 작업입니다.

- 입력 매개 변수는 1개 있고 출력 매개 변수는 없는 작업입니다.

- 2개의 입력 매개 변수와 MSBuild 속성을 반환하는 1개의 출력 매개 변수가 있는 작업입니다.

- 2개의 입력 매개 변수와 MSBuild 항목을 반환하는 1개의 출력 매개 변수가 있는 작업입니다.

작업을 만들고 실행하려면 다음과 같이 Visual Studio와 **Visual Studio 명령 프롬프트 창**을 사용합니다.

1. Visual Studio를 사용하여 MSBuild 프로젝트 파일을 만듭니다.

2. Visual Studio에서 프로젝트 파일을 수정하여 인라인 작업을 만듭니다.

3. **명령 프롬프트 창**을 사용하여 프로젝트를 빌드하고 결과를 검토합니다.

## <a name="create-and-modify-an-msbuild-project"></a>MSBuild 프로젝트 만들기 및 수정

 Visual Studio 프로젝트 시스템은 MSBuild를 기반으로 합니다. 따라서 Visual Studio를 사용하여 MSBuild 프로젝트 파일을 만들 수 있습니다. 이 섹션에서는 Visual C# 프로젝트 파일을 만듭니다. (대신 Visual Basic 프로젝트 파일을 만들 수 있습니다. 이 연습의 컨텍스트에서는 두 프로젝트 파일 간에 별 차이가 없습니다.

#### <a name="to-create-and-modify-a-project-file"></a>프로젝트 파일을 만들고 수정하려면

1. Visual Studio에서 C# **Windows Forms 애플리케이션** 템플릿을 사용하여 새 프로젝트를 만듭니다. **이름** 상자에 `InlineTasks`을 입력합니다. 솔루션의 **위치**를 *D:\\* 와 같이 입력합니다. **솔루션용 디렉터리 만들기**가 선택되어 있고, **소스 제어에 추가**가 선택 취소되어 있고, **솔루션 이름**이 **InlineTasks**인지 확인합니다.

3. **확인**을 클릭하여 프로젝트 파일을 만듭니다.

3. **솔루션 탐색기**에서 **InlineTasks** 프로젝트 노드를 마우스 오른쪽 단추로 클릭한 다음, **프로젝트 언로드**를 클릭합니다.

4. 프로젝트 노드를 다시 마우스 오른쪽 단추로 클릭하고 **InlineTasks.csproj 편집**을 클릭합니다.

     프로젝트 파일이 코드 편집기에 나타납니다.

## <a name="add-a-basic-hello-task"></a>기본 Hello 작업 추가

 이제 프로젝트 파일에 "Hello, world!" 메시지를 표시하는 기본 작업을 추가합니다. 또한 이 작업을 호출하는 기본 TestBuild 대상도 추가합니다.

#### <a name="to-add-a-basic-hello-task"></a>기본 Hello 작업을 추가하려면

1. 루트 `Project` 노드에서 `DefaultTargets` 특성을 `TestBuild`로 변경합니다. 결과 `Project` 노드는 다음 예제와 비슷합니다.

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. 다음 인라인 작업 및 대상을 프로젝트 파일에서 `</Project>` 태그 바로 앞에 추가합니다.

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, "Hello, world!");
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. 프로젝트 파일을 저장합니다.

   이 코드는 이름이 Hello이고 매개 변수, 참조 또는 `Using` 지시문이 없는 인라인 작업을 만듭니다. Hello 작업에는 기본 로깅 디바이스(일반적으로 콘솔 창)에 hello 메시지를 표시하는 코드 한 줄만 포함됩니다.

### <a name="run-the-hello-task"></a>Hello 작업 실행

 **명령 프롬프트 창**에서 MSBuild를 실행하여 Hello 작업을 생성하고 이 작업을 호출하는 TestBuild 대상을 처리합니다.

##### <a name="to-run-the-hello-task"></a>Hello 작업을 실행하려면

1. **시작**을 클릭하고 **모든 프로그램**을 클릭한 후 **Visual Studio Tools** 폴더를 찾고 **Visual Studio 명령 프롬프트**를 마우스 오른쪽 단추로 클릭합니다.

2. **명령 프롬프트 창**에서 프로젝트 파일이 들어 있는 폴더(이 경우 *D:\InlineTasks\InlineTasks\\* )를 찾습니다.

3. 명령 스위치 없이 **msbuild**를 입력하고 **Enter** 키를 누릅니다. 기본적으로 이렇게 하면 *InlineTasks.csproj* 파일이 빌드되고 기본 대상 TestBuild가 처리됩니다. 그 결과 Hello 작업이 호출됩니다.

4. **명령 프롬프트 창**에서 출력을 검토합니다. 다음 줄이 표시됩니다.

    `Hello, world!`

   > [!NOTE]
   > hello 메시지가 표시되지 않으면 프로젝트 파일을 다시 저장해 보고 Hello 작업을 실행하세요.

   코드 편집기와 **명령 프롬프트 창**을 오가면서 프로젝트 파일을 변경하고 결과를 빠르게 확인할 수 있습니다.

## <a name="define-the-echo-task"></a>Echo 작업 정의

 문자열 매개 변수를 수락하고 기본 로깅 디바이스에 문자열을 해당 문자열을 표시하는 인라인 작업을 만듭니다.

#### <a name="to-define-the-echo-task"></a>Echo 작업을 정의하려면

1. 코드 편집기에서 다음 코드를 사용하여 Hello 작업 및 TestBuild 대상을 바꿉니다.

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, Text);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. **명령 프롬프트 창**에서 명령 스위치 없이 **msbuild**를 입력하고 **Enter** 키를 누릅니다. 기본적으로 이 명령은 기본 대상 TestBuild를 처리하며 결과적으로 Echo 작업이 호출됩니다.

3. **명령 프롬프트 창**에서 출력을 검토합니다. 다음 줄이 표시됩니다.

    `Greetings!`

   이 코드는 Echo라고 지칭하며 필수 입력 매개 변수가 Text 1개 뿐인 인라인 작업을 정의합니다. 기본적으로 매개 변수는 System.String 형식입니다. Text 매개 변수의 값은 TestBuild 대상이 Echo 작업을 호출하는 경우에 설정됩니다.

## <a name="define-the-adder-task"></a>Adder 작업 정의

 두 개의 정수 매개 변수를 추가하고 합계를 MSBuild 속성으로 내보내는 인라인 작업을 만듭니다.

#### <a name="to-define-the-adder-task"></a>Adder 작업을 정의하려면

1. 코드 편집기에서 다음 코드를 사용하여 Echo 작업 및 TestBuild 대상을 바꿉니다.

   ```xml
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <A ParameterType="System.Int32" Required="true" />
       <B ParameterType="System.Int32" Required="true" />
       <C ParameterType="System.Int32" Output="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         C = A + B;
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Adder A="4" B="5">
       <Output PropertyName="Sum" TaskParameter="C" />
     </Adder>
     <Message Text="The sum is $(Sum)" Importance="High" />
   </Target>
   ```

2. **명령 프롬프트 창**에서 명령 스위치 없이 **msbuild**를 입력하고 **Enter** 키를 누릅니다. 기본적으로 이 명령은 기본 대상 TestBuild를 처리하며 결과적으로 Echo 작업이 호출됩니다.

3. **명령 프롬프트 창**에서 출력을 검토합니다. 다음 줄이 표시됩니다.

    `The sum is 9`

   이 코드에서는 Adder라고 지칭되며 2개의 필수 정부 입력 매개 변수인 A와 B 및 1개의 정수 출력 매개 변수인 C를 갖는 인라인 작업을 정의합니다. Adder 작업은 2개의 입력 매개 변수를 추가하고 출력 매개 변수에 합계를 반환합니다. 합계는 MSBuild 속성 `Sum`으로 내보내집니다. 입력 매개 변수의 값은 TestBuild 대상이 Adder 작업을 호출하는 경우에 설정됩니다.

## <a name="define-the-regx-task"></a>RegX 작업 정의

 항목 그룹 및 정규식을 수락하고 해당 식과 일치하는 파일 콘텐츠를 포함하는 모든 항목의 목록을 반환하는 인라인 작업을 만듭니다.

#### <a name="to-define-the-regx-task"></a>RegX 작업을 정의하려면

1. 코드 편집기에서 다음 코드를 사용하여 Adder 작업 및 TestBuild 대상을 바꿉니다.

   ```xml
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Expression Required="true" />
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />
     </ParameterGroup>
     <Task>
       <Using Namespace="System.Text.RegularExpressions"/>
       <Code Type="Fragment" Language="cs">
   <![CDATA[
         if (Files.Length > 0)
         {
           Result = new TaskItem[Files.Length];
           for (int i = 0; i < Files.Length; i++)
           {
             ITaskItem item = Files[i];
             string path = item.GetMetadata("FullPath");
             using(StreamReader rdr = File.OpenText(path))
             {
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)
               {
                 Result[i] = new TaskItem(item.ItemSpec);
               }
             }
           }
         }
   ]]>
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <RegX Expression="public|protected" Files="@(Compile)">
       <Output ItemName="MatchedFiles" TaskParameter="Result" />
     </RegX>
     <Message Text="Input files: @(Compile)" Importance="High" />
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />
   </Target>
   ```

2. **명령 프롬프트 창**에서 명령 스위치 없이 **msbuild**를 입력하고 **Enter** 키를 누릅니다. 기본적으로 이 명령은 기본 대상 TestBuild를 처리하며 결과적으로 RegX 작업이 호출됩니다.

3. **명령 프롬프트 창**에서 출력을 검토합니다. 다음 줄이 표시됩니다.

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   이 코드는 RegX로 지칭되고 다음과 같은 세 개의 매개 변수를 갖는 인라인 작업을 정의합니다.

- `Expression`은 일치시킬 정규식에 해당하는 값을 갖는 필수 문자열 입력 매개 변수입니다. 이 예제에서는 식은 단어 "public" 또는 "protected"와 일치하는 항목을 검색합니다.

- `Files`는 일치하는지 검색할 파일 목록에 해당하는 값을 갖는 필수 항목 목록 입력 매개 변수입니다. 이 예제에서 `Files`는 프로젝트 소스 파일을 나열하는 `Compile` 항목으로 설정됩니다.

- `Result`는 정규식과 일치하는지 확인되는 콘텐츠를 포함하는 파일 목록에 해당하는 값을 갖는 출력 매개 변수입니다.

  입력 매개 변수의 값은 TestBuild 대상이 RegX 작업을 호출하는 경우에 설정됩니다. RegX 작업은 모든 파일을 읽고 정규식과 일치하는 파일의 목록을 반환합니다. 이 목록은 `Result` 출력 매개 변수로 반환되고, 해당 출력 매개 변수는 MSBuild 항목 `MatchedFiles`로 내보내집니다.

### <a name="handle-reserved-characters"></a>예약 문자 처리

 MSBuild 파서는 인라인 작업을 XML로 처리합니다. XML에서 예약된 의미를 갖는 문자(예: "\<" 및 ">")는 검색된 후 .NET 소스 코드가 아니라 마치 XML인 것처럼 처리됩니다. `Files.Length > 0`과 같은 코드 식에 예약된 문자를 포함하려면 다음과 같이 해당 콘텐츠가 CDATA 식에 포함되도록 `Code` 요소를 씁니다.

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  // Your code goes here.

  ]]>
</Code>
```

## <a name="see-also"></a>참조

- [인라인 작업](../msbuild/msbuild-inline-tasks.md)
- [작업](../msbuild/msbuild-tasks.md)
- [대상](../msbuild/msbuild-targets.md)
