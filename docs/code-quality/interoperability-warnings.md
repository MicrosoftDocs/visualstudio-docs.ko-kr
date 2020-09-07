---
title: 이식성 및 상호 운용성 경고
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis warnings, interoperability warnings, portability warnings
- portability warnings
- warnings, portability
- interoperability warnings
- warnings, interoperability
ms.assetid: 95de6eb3-40c4-4063-9f59-25cb70e3b2b3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 306c2477e6e5f731ed6dbf20b2cf4d03d4556467
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509915"
---
# <a name="portability-and-interoperability-warnings"></a>이식성 및 상호 운용성 경고

이식성 경고는 여러 플랫폼 간의 이식성을 지원 합니다. 상호 운용성 경고는 COM 클라이언트와의 상호 작용을 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

| 규칙 | 설명 |
| - | - |
| [CA1401: P/Invoke는 노출 되지 않아야 합니다.](../code-quality/ca1401.md) | 공용 형식의 public 또는 protected 메서드에 System.Runtime.InteropServices.DllImportAttribute 특성이 있습니다 .이 특성은 Visual Basic의 Declare 키워드에 의해 구현 됩니다. 이러한 메서드는 노출되지 않아야 합니다. |
| [CA1417: `OutAttribute` P/invoke에 문자열 매개 변수를 사용 하지 마십시오.](../code-quality/ca1417.md) | 로 값으로 전달 되는 문자열 매개 변수는 `OutAttribute` 문자열이 인턴 문자열이 면 런타임을 불안정 하 게 만들 수 있습니다. |