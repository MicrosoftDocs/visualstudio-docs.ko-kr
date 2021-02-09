---
title: 텍스트 템플릿 보안
description: 임의 코드 및 악성 지시문 프로세서와 같은 항목을 포함 하 여 보안 및 텍스트 템플릿에 대해 알아보세요.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, security
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 11352eb33070d3401516948cc01c4b9bd7ab4f95
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99893323"
---
# <a name="security-of-text-templates"></a>텍스트 템플릿 보안
텍스트 템플릿에는 다음과 같은 보안 문제가 있습니다.

- 텍스트 템플릿은 임의의 코드 삽입에 취약 합니다.

- 호스트에서 지시문 프로세서를 찾기 위해 사용 하는 메커니즘이 안전 하지 않은 경우 악성 지시문 프로세서가 실행 될 수 있습니다.

## <a name="arbitrary-code"></a>임의 코드
 템플릿을 작성할 때 태그 안에 모든 코드를 넣을 수 있습니다 \<# #> . 이렇게 하면 텍스트 템플릿 내에서 임의 코드를 실행할 수 있습니다.

 신뢰할 수 있는 원본에서 템플릿을 가져와야 합니다. 응용 프로그램의 최종 사용자에 게 신뢰할 수 있는 원본에서 제공 하지 않는 템플릿을 실행 하지 않도록 경고 해야 합니다.

## <a name="malicious-directive-processor"></a>악성 지시문 프로세서
 텍스트 템플릿 엔진은 변환 호스트 및 하나 이상의 지시문 프로세서와 상호 작용 하 여 템플릿 텍스트를 출력 파일로 변환 합니다. 자세한 내용은 [텍스트 템플릿 변환 프로세스](../modeling/the-text-template-transformation-process.md)를 참조 하세요.

 호스트에서 지시문 프로세서를 찾기 위해 사용 하는 메커니즘이 안전 하지 않은 경우 악성 지시문 프로세서를 실행할 위험이 있습니다. 악의적인 지시문 프로세서는 `FullTrust` 템플릿이 실행 될 때 모드에서 실행 되는 코드를 제공할 수 있습니다. 사용자 지정 텍스트 템플릿 변환 호스트를 만드는 경우 엔진에서 지시문 프로세서를 찾기 위해 레지스트리와 같은 보안 메커니즘을 사용 해야 합니다.
