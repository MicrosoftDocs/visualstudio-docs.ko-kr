---
title: TextTransform 유틸리티를 사용 하 여 파일 생성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- text templates, TextTransform utility
- TextTransform.exe
ms.assetid: 06a48235-fe02-403e-a1cf-2ae70b4db62f
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 18776795fdf693c855edd3f629d674089daaaebd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666090"
---
# <a name="generating-files-with-the-texttransform-utility"></a>TextTransform 유틸리티 사용하여 파일 생성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

TextTransform.exe는 텍스트 템플릿을 변환 하는 데 사용할 수 있는 명령줄 도구입니다. TextTransform.exe를 호출 하는 경우 텍스트 템플릿 파일의 이름을 인수로 지정 합니다. TextTransform.exe는 텍스트 변환 엔진을 호출 하 고 텍스트 템플릿을 처리 합니다. TextTransform.exe는 일반적으로 스크립트에서 호출 됩니다. 그러나 Visual Studio 또는 빌드 프로세스에서 텍스트 변환을 수행할 수 있으므로 일반적으로 필요 하지 않습니다.

> [!NOTE]
> 텍스트 변환을 빌드 프로세스의 일부로 수행 하려면 MSBuild 텍스트 변환 작업을 사용 하는 것이 좋습니다. 자세한 내용은 [빌드 프로세스에서 코드 생성](../modeling/code-generation-in-a-build-process.md)을 참조 하세요. 가 설치 된 컴퓨터에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 텍스트 템플릿을 변환 하는 데 사용할 수 있는 응용 프로그램 또는 확장을 작성할 수도 있습니다. 자세한 내용은 [사용자 지정 호스트를 사용 하 여 텍스트 템플릿 처리](../modeling/processing-text-templates-by-using-a-custom-host.md)를 참조 하세요.

 TextTransform.exe은 다음 디렉터리에 있습니다.

 **Files\Common Files\Microsoft Shared\TextTemplating\11.0**

## <a name="syntax"></a>구문

```
TextTransform [<options>] <templateName>
```

#### <a name="parameters"></a>매개 변수

|**Argument**|**설명**|
|------------------|---------------------|
|`templateName`|변환 하려는 템플릿 파일의 이름을 식별 합니다.|

|**옵션**|**설명**|
|----------------|---------------------|
|**-out** \<filename>|변환의 출력을 쓸 파일입니다.|
|**-r**\<assembly>|텍스트 템플릿을 컴파일하고 실행 하는 데 사용 되는 어셈블리입니다.|
|**-u**\<namespace>|템플릿을 컴파일하는 데 사용 되는 네임 스페이스입니다.|
|**-I**\<includedirectory>|지정 된 텍스트 템플릿에 포함 된 텍스트 템플릿을 포함 하는 디렉터리입니다.|
|**-P**\<referencepath>|텍스트 템플릿 내에 지정 된 어셈블리를 검색 하거나 **-r** 옵션을 사용 하는 디렉터리입니다.<br /><br /> 예를 들어 Visual Studio API에 사용 되는 어셈블리를 포함 하려면 다음을 사용 합니다.<br /><br /> `-P "%VSSHELLFOLDER%\Common7\IDE\PublicAssemblies"`|
|**-dp** \<processorName> ! \<className>\<assemblyName&#124;codeBase>|텍스트 템플릿 내에서 사용자 지정 지시문을 처리 하는 데 사용할 수 있는 지시문 프로세서의 이름, 전체 형식 이름 및 어셈블리입니다.|
|**-a** [processorName]! [directiveName \<parameterName> ]!!\<parameterValue>|지시문 프로세서에 대 한 매개 변수 값을 지정 합니다. 매개 변수 이름과 값만 지정 하면 모든 지시문 프로세서에서 매개 변수를 사용할 수 있습니다. 지시문 프로세서를 지정 하는 경우 지정 된 프로세서에만 매개 변수를 사용할 수 있습니다. 지시문 이름을 지정 하는 경우 매개 변수는 지정 된 지시문이 처리 되는 경우에만 사용할 수 있습니다.<br /><br />  텍스트 템플릿에서 `hostspecific` 템플릿 지시문에를 포함 하 고에서 메시지를 호출 `this.Host` 합니다. 예를 들면 다음과 같습니다.<br /><br /> `<#@template language="c#" hostspecific="true"#> [<#= this.Host.ResolveParameterValue("", "", "parameterName") #>]`.<br /><br /> 선택적 프로세서 및 지시문 이름을 생략 하는 경우에도 항상 '! ' 표시를 입력 합니다. 예를 들면 다음과 같습니다.<br /><br /> `-a !!param!value`|
|**-h**|도움말을 제공 합니다.|

## <a name="related-topics"></a>관련 항목

|Task|항목|
|----------|-----------|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션에서 파일을 생성합니다.|[T4 텍스트 템플릿을 사용하여 디자인 타임 코드 생성](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|고유한 데이터 소스를 변형하는 지시문 프로세서를 작성합니다.|[T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md)|
|사용자 고유의 응용 프로그램에서 텍스트 템플릿을 호출할 수 있는 텍스트 템플릿 호스트를 작성 합니다.|[사용자 지정 호스트를 사용하여 텍스트 템플릿 처리](../modeling/processing-text-templates-by-using-a-custom-host.md)|
