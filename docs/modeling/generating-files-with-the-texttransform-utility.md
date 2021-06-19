---
title: TextTransform 유틸리티 사용하여 파일 생성
description: TextTransform 유틸리티가 텍스트 템플릿을 변환하는 데 사용할 수 있는 명령줄 도구인 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 743b7deb118bb3506773ec1a82d2331633afa7bc
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388830"
---
# <a name="generate-files-with-the-texttransform-utility"></a>TextTransform 유틸리티를 통해 파일 생성

TextTransform.exe 텍스트 템플릿을 변환하는 데 사용할 수 있는 명령줄 도구입니다. TextTransform.exe 호출할 때 텍스트 템플릿 파일의 이름을 인수로 지정합니다. TextTransform.exe 텍스트 변환 엔진을 호출하고 텍스트 템플릿을 처리합니다. TextTransform.exe 일반적으로 스크립트에서 호출됩니다. 그러나 Visual Studio 또는 빌드 프로세스에서 텍스트 변환을 수행할 수 있으므로 일반적으로 필요하지는 않습니다.

> [!NOTE]
> 빌드 프로세스의 일부로 텍스트 변환을 수행하려면 MSBuild 텍스트 변환 작업을 사용하는 것이 좋습니다. 자세한 내용은 [빌드 프로세스의 코드 생성을 참조하세요.](../modeling/code-generation-in-a-build-process.md) Visual Studio 설치된 컴퓨터에서 텍스트 템플릿을 변환할 수 있는 애플리케이션 또는 Visual Studio 확장을 작성할 수도 있습니다. 자세한 내용은 [사용자 지정 호스트를 사용하여 텍스트 템플릿 처리를 참조하세요.](../modeling/processing-text-templates-by-using-a-custom-host.md)

TextTransform.exe 다음 디렉터리에 있습니다.

::: moniker range=">=vs-2019"

**\Program Files (x86)\Microsoft Visual Studio\2019\Professional\Common7\IDE**

Professional Edition의 경우 또는

**\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE**

Enterprise Edition의 경우

::: moniker-end

::: moniker range="vs-2017"

**\Program Files (x86)\Microsoft Visual Studio\2017\Professional\Common7\IDE**

Professional Edition의 경우 또는

**\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE**

Enterprise Edition의 경우

이전 버전의 Visual Studio 파일은 다음 위치에 있습니다.

**\Program Files (x86)\Common Files\Microsoft Shared\TextTemplating \{ version}**

여기서 {version}은 설치된 이전 버전에 따라 달라집니다.

::: moniker-end

## <a name="syntax"></a>구문

```
TextTransform [<options>] <templateName>
```

### <a name="parameters"></a>매개 변수

|**Argument**|**설명**|
|-|-|
|`templateName`|변환할 템플릿 파일의 이름을 식별합니다.|

|**옵션**|**설명**|
|-|-|
|**-out**\<filename>|변환의 출력이 기록되는 파일입니다.|
|**-r**\<assembly>|텍스트 템플릿을 컴파일하고 실행하는 데 사용되는 어셈블리입니다.|
|**-u**\<namespace>|템플릿을 컴파일하는 데 사용되는 네임스페이스입니다.|
|**-I**\<includedirectory>|지정된 텍스트 템플릿에 포함된 텍스트 템플릿을 포함하는 디렉터리입니다.|
|**-P**\<referencepath>|텍스트 템플릿 내에 지정된 어셈블리를 검색하거나 **-r** 옵션을 사용하기 위한 디렉터리입니다.<br /><br /> 예를 들어 Visual Studio API에 사용되는 어셈블리를 포함하려면 를 사용합니다.<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName> \<className> ! !\<assemblyName&#124;codeBase>|텍스트 템플릿 내에서 사용자 지정 지시문을 처리하는 데 사용할 수 있는 지시문 프로세서의 이름, 전체 형식 이름 및 어셈블리입니다.|
|**-a** [processorName]! [directiveName]! \<parameterName> !\<parameterValue>|지시문 프로세서에 대한 매개 변수 값을 지정합니다. 매개 변수 이름 및 값만 지정하면 모든 지시문 프로세서에서 매개 변수를 사용할 수 있습니다. 지시문 프로세서를 지정하는 경우 매개 변수는 지정된 프로세서에서만 사용할 수 있습니다. 지시문 이름을 지정하는 경우 매개 변수는 지정된 지시문이 처리되는 경우에만 사용할 수 있습니다.<br /><br /> 지시문 프로세서 또는 텍스트 템플릿에서 매개 변수 값에 액세스하려면 [ITextTemplatingEngineHost.ResolveParameterValue](/previous-versions/visualstudio/visual-studio-2012/bb126369\(v\=vs.110\))를 사용합니다. 텍스트 템플릿에서 `hostspecific` 템플릿 지시문에 를 포함하고 에서 메시지를 `this.Host` 호출합니다. 예를 들면 다음과 같습니다.<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> 선택적 프로세서 및 지시문 이름을 생략하더라도 항상 '!' 표시를 입력합니다. 예를 들면 다음과 같습니다.<br /><br /> `-a !!param!value`|
|**-h**|도움말을 제공합니다.|

## <a name="related-topics"></a>관련 항목

|Task|항목|
|-|-|
|Visual Studio 솔루션에서 파일을 생성합니다.|[T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|고유한 데이터 소스를 변형하는 지시문 프로세서를 작성합니다.|[T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md)|
|사용자 고유의 애플리케이션에서 텍스트 템플릿을 호출할 수 있는 텍스트 템플릿 호스트를 작성합니다.|[사용자 지정 호스트를 사용하여 텍스트 템플릿 처리](../modeling/processing-text-templates-by-using-a-custom-host.md)|
