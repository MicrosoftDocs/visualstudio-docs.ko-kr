---
title: 텍스트 템플릿에서 이스케이프 시퀀스 사용
description: 텍스트 템플릿에서 이스케이프 시퀀스를 사용하여 텍스트 템플릿 태그를 생성하고 C# 코드에서만 제어 문자와 따옴표를 이스케이프하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 2a3cdabd38f2bf4ef38a31807fabed3ac837b26b
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388453"
---
# <a name="use-escape-sequences-in-text-templates"></a>텍스트 템플릿에서 이스케이프 시퀀스 사용

텍스트 템플릿에서 이스케이프 시퀀스를 사용하여 텍스트 템플릿 태그를 생성하고(C# 코드에서만) 제어 문자와 따옴표를 이스케이프할 수 있습니다.

표준 코드 블록의 열려 있는 태그를 출력 파일에 인쇄하고 닫려면 다음과 같이 태그를 이스케이프합니다.

```
\<# ... \#>
```

다른 텍스트 템플릿 지시문 및 코드 블록 태그에서도 동일한 작업을 수행할 수 있습니다.

텍스트 블록에 텍스트 템플릿 태그를 이스케이프하는 데 사용되는 문자열이 포함된 경우 다음 이스케이프 시퀀스를 사용할 수 있습니다.

- 텍스트 템플릿 태그 앞에 짝수 개의 이스케이프( ) 문자가 오는 경우 \\ 템플릿 파서가 이스케이프 문자의 절반을 포함하고 시퀀스를 텍스트 템플릿 태그로 포함합니다. 예를 들어 텍스트 템플릿에 네 개의 이스케이프 문자가 있는 경우 생성된 파일에는 두 개의 " \\ " 문자가 있습니다.

- 텍스트 템플릿 태그 앞에 홀수 이스케이프( ) 문자가 오는 경우 \\ 템플릿 파서에는 " \\ " 문자의 절반과 태그 자체( \<# or #> )가 포함됩니다. 태그는 텍스트 템플릿 태그로 간주되지 않습니다.

- 이스케이프( \\ ) 문자가 컨트롤 문자 또는 따옴표(C#에서만 해당)를 이스케이프하는 위치 이외의 다른 시퀀스에서 나타나는 경우 문자는 직접 출력됩니다.

## <a name="see-also"></a>참조

- [방법: 이스케이프 시퀀스를 사용하여 템플릿에서 템플릿 생성](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
