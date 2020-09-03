---
title: T4 Output 지시문 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 03a14993-47ad-4f2e-8032-57db28d5842a
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 149370bfee1b142876dff881625d08083afadea4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652310"
---
# <a name="t4-output-directive"></a>T4 Output 지시문
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 텍스트 템플릿에서 `output` 지시문은 변형된 파일의 인코딩과 파일 이름 확장명을 정의하는 데 사용됩니다.

 예를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 들어 프로젝트에 다음 지시문을 포함 하는 **MyTemplate.tt** 이라는 템플릿 파일이 포함 되어 있는 경우.

 `<#@output extension=".cs"#>`

 그런 다음 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **MyTemplate.cs** 라는 파일을 생성 합니다.

 전처리된 런타임 텍스트 템플릿에는 `output` 지시문이 필요하지 않습니다. 대신 애플리케이션은 `TextTransform()`을 호출하여 생성된 문자열을 가져옵니다. 자세한 내용은 [T4 텍스트 템플릿을 사용 하 여 런타임 텍스트 생성](../modeling/run-time-text-generation-with-t4-text-templates.md)을 참조 하세요.

## <a name="using-the-output-directive"></a>output 지시문 사용

```
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>
```

 각 텍스트 템플릿에 `output` 지시문이 두 개 이상 있어서는 안 됩니다.

## <a name="extension-attribute"></a>확장 특성
 생성된 텍스트 출력 파일의 파일 이름 확장명을 지정합니다.

 기본값은 .cs입니다 **.**

 예제: `<#@ output extension=".txt" #>`

 `<#@ output extension=".htm" #>`

 `<#@ output extension=".cs" #>`

 `<#@ output extension=".vb" #>`

 허용 되는 값: 유효한 모든 파일 이름 확장명입니다.

## <a name="encoding-attribute"></a>encoding 특성
 출력 파일을 생성할 때 사용할 인코딩을 지정합니다. 예를 들면 다음과 같습니다.

 `<#@ output encoding="utf-8"#>`

 기본값은 텍스트 템플릿 파일에 사용되는 인코딩입니다.

 허용 되는 값: `us-ascii`

 `utf-16BE`

 `utf-16`

 `utf-8`

 `utf-7`

 `utf-32`

 `0`(시스템 기본값)

 일반적으로는 <xref:System.Text.Encoding.GetEncodings%2A?displayProperty=fullName>가 반환하는 모든 인코딩으로 된 WebName 문자열 또는 CodePage 번호를 사용할 수 있습니다.
