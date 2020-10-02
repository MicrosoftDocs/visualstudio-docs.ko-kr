---
title: 관리 코드에 대한 전역화 규칙 규칙 집합
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3c4032ee-0805-4581-8c48-b1827cd6b213
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 0c3b899ec8e19160d9ee4a307a86c576d217004c
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91658544"
---
# <a name="globalization-rules-rule-set-for-managed-code"></a>관리 코드에 대한 전역화 규칙 규칙 집합

Microsoft 전역화 규칙 규칙 집합을 사용 하 여 응용 프로그램의 데이터가 다른 언어, 로캘 및 문화권에서 올바르게 나타나지 않도록 하는 문제에 초점을 맞출 수 있습니다. 응용 프로그램이 지역화, 세계화 또는 둘 다 인 경우이 규칙 집합을 포함 해야 합니다.

|규칙|설명|
|----------|-----------------|
|[CA1303](/dotnet/fundamentals/code-analysis/quality-rules/ca1303)|리터럴을 지역화된 매개 변수로 전달하지 마세요.|
|[CA1304](/dotnet/fundamentals/code-analysis/quality-rules/ca1304)|CultureInfo를 지정하세요.|
|[CA1305](/dotnet/fundamentals/code-analysis/quality-rules/ca1305)|IFormatProvider를 지정하세요.|
|[CA1307](/dotnet/fundamentals/code-analysis/quality-rules/ca1307)|명확성을 위해 StringComparison 지정|
|[CA1308](/dotnet/fundamentals/code-analysis/quality-rules/ca1308)|대문자로 문자열을 정규화하세요.|
|[CA1309](/dotnet/fundamentals/code-analysis/quality-rules/ca1309)|서수 StringComparison을 사용하세요.|
|[CA1310](/dotnet/fundamentals/code-analysis/quality-rules/ca1310)|정확성을 위해 StringComparison 지정|
|[CA2101](/dotnet/fundamentals/code-analysis/quality-rules/ca2101)|P/Invoke 문자열 인수에 대해 마샬링을 지정하십시오.|
