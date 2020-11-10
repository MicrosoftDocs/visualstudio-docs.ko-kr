---
title: LC 작업 | Microsoft Docs
description: MSBuild에서 LC 작업을 사용하여 .licx 파일에서 .license 파일을 생성하는 LC.exe를 래핑하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#LC
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, LC task
- LC task [MSBuild]
ms.assetid: d5a53472-6f2a-42b8-a6db-593ca99c9790
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 70c996d5a8d1d4bf296a395bfb64ead6eba1bb01
ms.sourcegitcommit: f1d47655974a2f08e69704a9a0c46cb007e51589
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92903584"
---
# <a name="lc-task"></a>LC 작업

*.licx* 파일에서 *.license* 파일을 생성하는 *LC.exe* 를 래핑합니다. *LC.exe* 에 대한 자세한 내용은 [Lc.exe(라이선스 컴파일러)](/dotnet/framework/tools/lc-exe-license-compiler)를 참조하세요.

## <a name="parameters"></a>매개 변수

다음 표에서는 `LC` 작업의 매개 변수에 대해 설명합니다.

|매개 변수|설명|
|---------------|-----------------|
|`LicenseTarget`|필수 <xref:Microsoft.Build.Framework.ITaskItem> 매개 변수입니다.<br /><br /> *.licenses* 파일이 생성되는 대상 실행 파일을 지정합니다.|
|`NoLogo`|선택적 `Boolean` 매개 변수입니다.<br /><br /> Microsoft 시작 배너를 표시하지 않습니다.|
|`OutputDirectory`|선택적 `String` 매개 변수입니다.<br /><br /> 출력 *.licenses* 파일을 포함할 디렉터리를 지정합니다.|
|`OutputLicense`|선택적 <xref:Microsoft.Build.Framework.ITaskItem> 출력 매개 변수입니다.<br /><br /> *.licenses* 파일의 이름을 지정합니다. 이름을 지정하지 않는 경우 *.licx* 파일의 이름이 사용되고 *.licenses* 파일이 *.licx* 파일을 포함하는 디렉터리에 배치됩니다.|
|`ReferencedAssemblies`|선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> *.license* 파일을 생성할 때 로드할 참조된 구성 요소를 지정합니다.|
|`SdkToolsPath`|선택적 `String` 매개 변수입니다.<br /><br /> *resgen.exe* 와 같은 SDK 도구에 대한 경로를 지정합니다.|
|`Sources`|필수 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 매개 변수입니다.<br /><br /> *.licenses* 파일에 포함할 라이선스가 있는 구성 요소가 포함된 항목을 지정합니다. 자세한 내용은 [Lc.exe(라이선스 컴파일러)의 `/complist` 스위치](/dotnet/framework/tools/lc-exe-license-compiler)에 대한 설명서를 참조하세요.|

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="example"></a>예제

다음 예제에서는 `LC` 작업을 사용하여 라이선스를 컴파일합니다.

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
<!-- Item declarations, etc -->

    <Target Name="CompileLicenses">
        <LC
            Sources="@(LicxFile)"
            LicenseTarget="$(TargetFileName)"
            OutputDirectory="$(IntermediateOutputPath)"
            OutputLicenses="$(IntermediateOutputPath)$(TargetFileName).licenses"
            ReferencedAssemblies="@(ReferencePath);@(ReferenceDependencyPaths)">

            <Output
                TaskParameter="OutputLicenses"
                ItemName="CompiledLicenseFile"/>
        </LC>
    </Target>
</Project>
```

## <a name="see-also"></a>참조

- [작업](../msbuild/msbuild-tasks.md)
- [작업 참조](../msbuild/msbuild-task-reference.md)
