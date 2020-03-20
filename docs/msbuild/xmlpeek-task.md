---
title: XmlPeek 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- XmlPeek task [MSBuild]
- MSBuild, XmlPeek task
ms.assetid: 19196031-a3bc-41b5-9c4a-f2572630e179
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c5a76bf033fa3eb85f0626478b965285f32e5fb6
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79094665"
---
# <a name="xmlpeek-task"></a>XmlPeek 작업

XML 파일에서 XPath 쿼리에 의해 지정된 대로 값을 반환합니다.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `XmlPeek` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`Namespaces`|선택적 `String` 매개 변수입니다.<br /><br /> XPath 쿼리 접두사에 대한 네임스페이스를 지정합니다.|
|`Query`|선택적 `String` 매개 변수입니다.<br /><br /> XPath 쿼리를 지정합니다.|
|`Result`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 이 작업으로 반환되는 결과를 포함합니다.|
|`XmlContent`|선택적 `String` 매개 변수입니다.<br /><br /> XML 입력을 문자열로 지정합니다.|
|`XmlInputPath`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> XML 입력을 파일 경로로 지정합니다.|

## <a name="remarks"></a>설명

 이 작업은 표에 나열된 매개 변수 외에, <xref:Microsoft.Build.Utilities.Task> 클래스에서 직접 상속하는 <xref:Microsoft.Build.Tasks.TaskExtension> 클래스의 매개 변수도 상속합니다. 이러한 추가 매개 변수 및 해당 설명이 포함된 목록은 [TaskExtension 기본 클래스](../msbuild/taskextension-base-class.md)를 참조하세요.



## <a name="example"></a>예제

다음은 읽을 샘플 XML 파일 `settings.config`입니다.

```xml
<appSettings>
  <add key="ProjectFolder" value="S1" />
</appSettings>
```

이 예제에서 `value`를 읽으려면 다음과 같은 코드를 사용합니다.

```xml
<Target Name="BeforeBuild">
    <XmlPeek XmlInputPath="settings.config" Query="appSettings/add[@key='ProjectFolder']/@value">
        <Output TaskParameter="Result" ItemName="value" />
    </XmlPeek>
    <Message Text="Using project folder @(value)." Importance="high" />
    <PropertyGroup>
        <ProjectFolder>@(value)</ProjectFolder>
    </PropertyGroup>
    <ItemGroup>
        <Compile Include="Projects\$(ProjectFolder)\Controls\Control1.ascx.cs">
            <SubType>ASPXCodeBehind</SubType>
        </Compile>
    </ItemGroup>
</Target>
```

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
