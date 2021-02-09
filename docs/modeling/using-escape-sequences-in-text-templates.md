---
title: 텍스트 템플릿에서 이스케이프 시퀀스 사용
description: '텍스트 템플릿에서 이스케이프 시퀀스를 사용 하 여 텍스트 템플릿 태그를 생성 하 고 c # 코드 에서만 제어 문자와 따옴표를 이스케이프 처리 하는 방법에 대해 알아봅니다.'
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, escape sequences
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 126fe3f4e42c9c6cf0b75bf740e1e7e2c4b269ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924340"
---
# <a name="use-escape-sequences-in-text-templates"></a>텍스트 템플릿에서 이스케이프 시퀀스 사용

텍스트 템플릿에서 이스케이프 시퀀스를 사용 하 여 텍스트 템플릿 태그를 생성 하 고 (c # 코드 에서만) 제어 문자 및 따옴표를 이스케이프할 수 있습니다.

표준 코드 블록의 여는 태그와 닫는 태그를 출력 파일에 인쇄 하려면 다음과 같이 태그를 이스케이프 합니다.

```
\<# ... \#>
```

다른 텍스트 템플릿 지시문 및 코드 블록 태그를 사용 하 여 동일한 작업을 수행할 수 있습니다.

텍스트 블록에 텍스트 템플릿 태그를 이스케이프 하는 데 사용 되는 문자열이 포함 된 경우 다음 이스케이프 시퀀스를 사용할 수 있습니다.

- 텍스트 템플릿 태그 앞에 짝수 개의 이스케이프 문자 ()가 오면 \\ 템플릿 파서는 이스케이프 문자의 절반을 포함 하 고 시퀀스를 텍스트 템플릿 태그로 포함 합니다. 예를 들어 텍스트 템플릿에 이스케이프 문자가 4 개 있는 경우 생성 된 파일에는 두 개의 " \\ " 문자가 있습니다.

- 텍스트 템플릿 태그 앞에 홀수 개의 이스케이프 문자 ()가 오면 \\ 템플릿 파서는 " \\ " 문자 및 태그 자체 ()의 절반을 포함 합니다 \<# or #> . 태그는 텍스트 템플릿 태그로 간주 되지 않습니다.

- 이스케이프 \\ 문자 ()가 제어 문자 또는 따옴표를 이스케이프 하는 위치 (c # 에서만)가 아닌 다른 위치에 있으면 문자는 직접 출력 됩니다.

## <a name="see-also"></a>참고 항목

- [방법: 이스케이프 시퀀스를 사용하여 템플릿에서 템플릿 생성](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)
