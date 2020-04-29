---
title: SGen 작업 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#SGen
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SGen task [MSBuild]
- MSBuild, SGen task
ms.assetid: 22c5ade4-4159-4667-b891-0c1aa06f4df5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cbf18c4477a164ec2e25a5ed4b2105f6fdad9130
ms.sourcegitcommit: 93859158465eab3423a0c0435f06490f0a456a57
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167438"
---
# <a name="sgen-task"></a>SGen 작업

지정된 어셈블리의 형식에 대한 XML serialization 어셈블리를 만듭니다. 이 작업은 XML Serializer 생성기 도구(*Sgen.exe*)를 래핑합니다. 자세한 내용은 [XML Serializer 생성기 도구(Sgen.exe)](/dotnet/framework/serialization/xml-serializer-generator-tool-sgen-exe)를 참조하세요.

## <a name="parameters"></a>매개 변수

 다음 표에서는 `SGen` 작업의 매개 변수에 대해 설명합니다.

| 매개 변수 | 설명 |
|-----------------------------| - |
| `BuildAssemblyName` | 필수 `String` 매개 변수입니다.<br /><br /> serialization 코드를 생성할 어셈블리입니다. |
| `BuildAssemblyPath` | 필수 `String` 매개 변수입니다.<br /><br /> serialization 코드를 생성할 어셈블리 경로입니다. |
| `DelaySign` | 선택적 `Boolean` 매개 변수입니다.<br /><br /> 어셈블리에 공개 키만 저장하려 경우 `true`를 지정합니다. 완전히 서명된 어셈블리를 만들려는 경우 `false`를 지정합니다.<br /><br /> 이 매개 변수는 `KeyFile` 또는 `KeyContainer` 매개 변수와 함께 사용하지 않는 한 효과가 없습니다. |
| `KeyContainer` | 선택적 `String` 매개 변수입니다.<br /><br /> 키 쌍을 보관하는 컨테이너를 지정합니다. 어셈블리 매니페스트에 공개 키를 삽입하여 어셈블리에 서명합니다. 그런 다음 이 작업은 프라이빗 키를 사용하여 최종 어셈블리에 서명합니다. |
| `KeyFile` | 선택적 `String` 매개 변수입니다.<br /><br /> 어셈블리 서명에 사용할 키 쌍 또는 공개 키를 지정합니다. 컴파일러는 퍼블릭 키를 어셈블리 매니페스트에 삽입한 다음 프라이빗 키를 사용하여 최종 어셈블리에 서명합니다. |
| `Platform` | 선택적 `String` 매개 변수입니다.<br /><br /> 출력 어셈블리를 생성하는 데 사용되는 컴파일러 플랫폼을 가져오거나 설정합니다. 이 매개 변수는 `x86`, `x64` 또는 `anycpu` 값을 가질 수 있습니다. 기본값은 `anycpu`입니다. |
| `References` | 선택적 `String[]` 매개 변수입니다.<br /><br /> XML serialization이 필요한 형식에서 참조하는 어셈블리를 지정합니다. |
| `SdkToolsPath` | 선택적 `String` 매개 변수입니다.<br /><br /> *resgen.exe*와 같은 SDK 도구에 대한 경로를 지정합니다. |
| `SerializationAssembly` | 선택적 <xref:Microsoft.Build.Framework.ITaskItem>`[]` 출력 매개 변수입니다.<br /><br /> 생성된 serialization 어셈블리를 포함합니다. |
| `SerializationAssemblyName` | 선택적 `String` 매개 변수입니다.<br /><br /> 생성된 serialization 어셈블리의 이름을 지정합니다. |
| `ShouldGenerateSerializer` | 필수 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 SGen 작업은 serialization 어셈블리를 생성해야 합니다. |
| `Timeout` | 선택적 `Int32` 매개 변수입니다.<br /><br /> 작업 실행 파일이 얼마 후에 종료될 지를 밀리초 단위로 지정합니다. 기본값은 시간 제한이 없음을 나타내는 `Int.MaxValue`입니다. |
| `ToolPath` | 선택적 `String` 매개 변수입니다.<br /><br /> 작업에서 내부 실행 파일(*sgen.exe*)을 로드할 위치를 지정합니다. 이 매개 변수를 지정하지 않으면 작업에서는 MSBuild를 실행하고 있는 프레임워크 버전에 해당하는 SDK 설치 경로가 사용됩니다. |
| `Types` | 선택적 `String[]` 매개 변수입니다.<br /><br /> serialization 코드를 생성하기 위한 특정 형식의 목록을 가져오거나 설정합니다. SGen은 해당 형식에 대해서만 serialization 코드를 생성합니다. |
| `UseProxyTypes` | 필수 `Boolean` 매개 변수입니다.<br /><br /> `true`이면 SGen 작업은 XML Web services 프록시 형식에 대해서만 serialization 코드를 생성합니다. |

[!INCLUDE [ToolTaskExtension arguments](includes/tooltaskextension-base-params.md)]

## <a name="see-also"></a>참조

- [작업 참조](../msbuild/msbuild-task-reference.md)
- [작업](../msbuild/msbuild-tasks.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
