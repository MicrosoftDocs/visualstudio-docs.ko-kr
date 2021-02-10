---
title: XSLT 기본 템플릿
description: 스타일시트에 일치하는 명시적 템플릿 규칙이 없는 경우 XSLT를 처리하는 동안 사용되는 XSLT 기본 템플릿에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 74b4cfebc7a6160577f1e817c9171f2eae69533c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99874758"
---
# <a name="xslt-default-templates"></a>XSLT 기본 템플릿

기본 템플릿은 스타일시트에 일치하는 명시적 템플릿 규칙이 없는 경우 XSLT 처리 동안 사용됩니다. 기본 제공 템플릿 규칙이라고도 하는 기본 템플릿은 W3C XSLT 1.0 권장 사항의 5.8 단원에 정의되어 있습니다. 기본 템플릿을 사용하면 일치하는 명시적 템플릿 규칙이 없는 경우에도 XSLT 프로세서에서 노드를 처리할 수 있습니다. 그러나 기본 제공 템플릿 규칙은 스타일시트에 명시적으로 정의되어 있지 않기 때문에 예기치 않은 또는 혼란스러운 XSLT 변환 결과가 발생할 수 있습니다.

이제 XSLT 디버거는 XSLT 기본 템플릿의 코드를 표시합니다. XSLT 변환을 단계별로 실행할 때 기본 템플릿이 사용되는 경우 디버거는 기본 템플릿을 창에 표시합니다. 이렇게 하면 기본 템플릿의 코드를 단계별로 실행하고 해당 명령에 따라 중단점을 설정할 수 있습니다.

## <a name="see-also"></a>참조

- [XSLT 디버그](../xml-tools/debugging-xslt.md)
