---
title: ResourcesGenerator 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- embedding resources into a .resources file [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild]
- ResourcesGenerator task [WPF MSBuild], parameters
ms.assetid: e782bbac-9ee6-472b-8171-3ee008c77b4e
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2b5aba45292aaa55a719eb19d6f0f6f115e8b477
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77632513"
---
# <a name="resourcesgenerator-task"></a>ResourcesGenerator 작업

<xref:Microsoft.Build.Tasks.Windows.ResourcesGenerator> 작업은 하나 이상의 리소스( *.jpg*, *.ico*, *.bmp*, 이진 형식의 XAML 및 기타 확장 형식)를 *.resources* 파일에 포함합니다.

## <a name="task-parameters"></a>작업 매개 변수

|매개 변수|설명|
|---------------|-----------------|
|`OutputPath`|필수 **String** 매개 변수입니다.<br /><br /> 출력 디렉터리의 경로를 지정합니다. 경로가 절대 경로가 아니면 루트 프로젝트 디렉터리의 상대 경로로 처리됩니다.|
|`OutputResourcesFile`|필수 **ITaskItem** 출력 매개 변수입니다.<br /><br /> 생성된 *.resources* 파일의 경로 및 이름을 지정합니다. 경로가 절대 경로가 아니면 루트 프로젝트 디렉터리에 상대적으로 *.resources* 파일이 생성됩니다.|
|`ResourcesFiles`|필수 **ITaskItem[]** 매개 변수입니다.<br /><br /> 생성된 *.resources* 파일에 포함할 하나 이상의 리소스를 지정합니다.|

## <a name="example"></a>예제

 다음 예제에서는 단일 *.bmp* 리소스로 *.resources* 파일을 생성합니다. *.bmp* 리소스는 프로젝트 루트 디렉터리에 상대적인 디렉터리에 생성됩니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <UsingTask
    TaskName="Microsoft.Build.Tasks.Windows.ResourcesGenerator"
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />
  <Target Name="ResourcesGeneratorTask">
    <ResourcesGenerator
      ResourceFiles="Resource1.bmp"
      OutputPath="myresources"
      OutputResourcesFile="myresources\my.resources" />
  </Target>
</Project>
```

## <a name="see-also"></a>참조

- [WPF MSBuild 참조](../msbuild/wpf-msbuild-reference.md)
- [작업 참조](../msbuild/wpf-msbuild-task-reference.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
- [WPF 애플리케이션 빌드(WPF)](/dotnet/framework/wpf/app-development/building-a-wpf-application-wpf)