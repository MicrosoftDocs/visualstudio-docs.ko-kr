---
title: MSBuild .Targets 파일 | Microsoft Docs
ms.date: 02/24/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- .targets files
- MSBuild, .targets files
ms.assetid: f6d98eb4-d2fa-49b7-8e3c-bae1ca3cf596
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3faa9ca73592722a950f9914437884c33122070e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77633358"
---
# <a name="msbuild-targets-files"></a>MSBuild .Targets 파일

MSBuild에는 일반 시나리오에 대한 항목, 속성, 대상 및 작업이 들어 있는 여러 *.targets* 파일이 포함됩니다. 이러한 파일은 대부분의 Visual Studio 프로젝트 파일로 자동 가져오기되므로 쉽게 유지 관리하고 읽을 수 있습니다.

 일반적으로 프로젝트에서는 하나 이상의 *.targets* 파일을 가져와서 빌드 프로세스를 정의합니다. 예를 들어 Visual Studio로 만든 C# 프로젝트에서 가져오는 *Microsoft.CSharp.targets*는 *Microsoft.Common.targets*를 가져옵니다. C# 프로젝트 자체에서는 해당 프로젝트와 관련된 항목과 속성을 정의하지만, C# 프로젝트에 대한 표준 빌드 규칙은 가져오는 *.targets* 파일에 정의되어 있습니다.

 `$(MSBuildToolsPath)` 값은 일반 *.targets* 파일의 경로를 지정합니다. `ToolsVersion`이 4.0인 경우 파일은 *\<WindowsInstallationPath>\Microsoft.NET\Framework\v4.0.30319\\* 에 위치합니다.

> [!NOTE]
> 대상을 직접 만드는 방법에 대한 자세한 내용은 [대상](../msbuild/msbuild-targets.md)을 참조하세요. `Import` 요소를 사용하여 프로젝트 파일을 다른 프로젝트 파일에 삽입하는 방법에 대한 자세한 내용은 [가져오기 요소(MSBuild)](../msbuild/import-element-msbuild.md) 및 [방법: 여러 프로젝트 파일에서 동일한 대상 사용](../msbuild/how-to-use-the-same-target-in-multiple-project-files.md)을 참조하세요.

## <a name="common-targets-files"></a>일반 .targets 파일

| *.targets* 파일 | 설명 |
|---------------------------------| - |
| *Microsoft.Common.targets* | Visual Basic 및 C# 프로젝트 표준 빌드 프로세스의 단계를 정의합니다.<br /><br /> *Microsoft.CSharp.targets* 및 *Microsoft.VisualBasic.targets* 파일을 통해 가져옵니다. 이러한 파일에는 `<Import Project="Microsoft.Common.targets" />` 문이 포함됩니다. |
| *Microsoft.CSharp.targets* | Visual C# 프로젝트에 대한 표준 빌드 프로세스의 단계를 정의합니다.<br /><br /> Visual C# 프로젝트 파일( *.csproj*)을 통해 가져옵니다. 이러한 파일에는 `<Import Project="$(MSBuildToolsPath)\Microsoft.CSharp.targets" />` 문이 포함됩니다. |
| *Microsoft.VisualBasic.targets* | Visual Basic 프로젝트에 대한 표준 빌드 프로세스의 단계를 정의합니다.<br /><br /> Visual Basic 프로젝트 파일( *.vbproj*)을 통해 가져옵니다. 이러한 파일에는 `<Import Project="$(MSBuildToolsPath)\Microsoft.VisualBasic.targets" />` 문이 포함됩니다. |

## <a name="directorybuildtargets"></a>Directory.Build.targets

*Directory.Build.targets*는 디렉터리 아래에 프로젝트에 대한 사용자 지정을 제공하는 사용자 정의 파일입니다. **ImportDirectoryBuildTargets** 속성을 **false**로 설정한 경우가 아니면 *Microsoft.Common.targets*에서 이 파일을 자동으로 가져옵니다. 자세한 내용은 [빌드 사용자 지정](customize-your-build.md)을 참조하세요.

## <a name="see-also"></a>참조

- [Import 요소(MSBuild)](../msbuild/import-element-msbuild.md)
- [MSBuild 참조](../msbuild/msbuild-reference.md)
- [MSBuild](../msbuild/msbuild.md)
