---
title: 텍스트 템플릿 보안
description: 임의 코드 및 악성 지시문 프로세서와 같은 항목을 포함하여 보안 및 텍스트 템플릿에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a740a6f7a4c532a61a5e412c94fa4321c5da707
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385762"
---
# <a name="security-of-text-templates"></a>텍스트 템플릿 보안
텍스트 템플릿에는 다음과 같은 보안 문제가 있습니다.

- 텍스트 템플릿은 임의의 코드 삽입에 취약합니다.

- 호스트에서 지시문 프로세서를 찾는 데 사용하는 메커니즘이 안전하지 않으면 악의적인 지시문 프로세서를 실행할 수 있습니다.

## <a name="arbitrary-code"></a>임의 코드
 템플릿을 작성할 때 태그 내에 코드를 넣을 수 \<# #> 있습니다. 이렇게 하면 텍스트 템플릿 내에서 임의의 코드를 실행할 수 있습니다.

 신뢰할 수 있는 원본에서 템플릿을 얻어야 합니다. 신뢰할 수 있는 원본에서 제공하지 않는 템플릿을 실행하지 않도록 애플리케이션의 최종 사용자에게 경고해야 합니다.

## <a name="malicious-directive-processor"></a>악성 지시문 프로세서
 텍스트 템플릿 엔진은 변환 호스트 및 하나 이상의 지시문 프로세서와 상호 작용하여 템플릿 텍스트를 출력 파일로 변환합니다. 자세한 내용은 텍스트 템플릿 변환 프로세스 를 [참조하세요.](../modeling/the-text-template-transformation-process.md)

 호스트가 지시문 프로세서를 찾는 데 사용하는 메커니즘이 안전하지 않은 경우 악의적인 지시문 프로세서를 실행할 위험이 있습니다. 악성 지시문 프로세서는 템플릿이 실행되면 모드에서 실행되는 코드를 제공할 수 `FullTrust` 있습니다. 사용자 지정 텍스트 템플릿 변환 호스트를 만드는 경우 엔진이 지시문 프로세서를 찾을 수 있도록 레지스트리와 같은 보안 메커니즘을 사용해야 합니다.
