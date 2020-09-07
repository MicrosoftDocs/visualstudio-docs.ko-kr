---
title: 전역화 경고
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd215a8b5c8dfb5905117638883d94d09268ce3d
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/07/2020
ms.locfileid: "89509850"
---
# <a name="globalization-warnings"></a>전역화 경고
세계화 경고는 전 세계에서 사용할 수 있는 라이브러리 및 응용 프로그램을 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA1303: 리터럴을 지역화된 매개 변수로 전달하지 마세요.](../code-quality/ca1303.md)|외부에서 볼 수 있는 메서드는 문자열 리터럴을 .NET 생성자 또는 메서드에 대 한 매개 변수로 전달 하 고 해당 문자열을 지역화할 수 있어야 합니다.|
|[CA1304: CultureInfo를 지정하세요.](../code-quality/ca1304.md)|메서드 또는 생성자가 System.Globalization.CultureInfo 매개 변수를 받아들이는 오버로드가 있는 멤버를 호출하지만 CultureInfo 매개 변수를 사용하는 오버로드는 호출하지 않습니다. CultureInfo 또는 System.IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다.|
|[CA1305: IFormatProvider를 지정하세요.](../code-quality/ca1305.md)|메서드 또는 생성자가 System.IFormatProvider 매개 변수를 받아들이는 오버로드가 있는 하나 이상의 멤버를 호출하지만 IFormatProvider 매개 변수를 사용하는 오버로드는 호출하지 않습니다. System.Globalization.CultureInfo 또는 IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다.|
|[CA1306: 데이터 형식에 맞는 로캘을 설정하세요.](../code-quality/ca1306.md)|로캘은 숫자 값에 사용되는 서식, 통화 기호 및 정렬 순서 등과 같은 데이터의 문화권별 표현 요소를 결정합니다. DataTable 또는 DataSet를 만들 때는 로캘을 명시적으로 설정해야 합니다.|
|[CA1307: 명확성을 위해 StringComparison 지정](../code-quality/ca1307.md)|문자열 비교 작업에서 StringComparison 매개 변수를 설정하지 않는 메서드 오버로드를 사용합니다.|
|[CA1308: 대문자로 문자열을 정규화하세요.](../code-quality/ca1308.md)|문자열은 대문자로 정규화되어야 합니다. 일부 문자는 소문자로 변환될 때 다시 대문자로 변환될 수 없습니다.|
|[CA1309: 서수 StringComparison을 사용하세요.](../code-quality/ca1309.md)|비언어 문자열 비교 작업에서는 StringComparison 매개 변수를 Ordinal 또는 OrdinalIgnoreCase로 설정하지 않습니다. 매개 변수가 명시적으로 StringComparison.Ordinal 또는 StringComparison.OrdinalIgnoreCase로 설정되기 때문에 코드 실행 속도, 정확도 및 신뢰도가 향상됩니다.|
|[CA1310: 정확성을 위해 StringComparison 지정](../code-quality/ca1310.md)|문자열 비교 작업은 StringComparison 매개 변수를 설정 하지 않고 기본적으로 문화권별 문자열 비교를 사용 하는 메서드 오버 로드를 사용 합니다.|
|[CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정 하십시오.](../code-quality/ca2101.md)|플랫폼 호출 멤버는 부분적으로 신뢰할 수 있는 호출자를 허용 하 고 문자열 매개 변수를 포함 하며 문자열을 명시적으로 마샬링할 수 없습니다. 이렇게 하면 보안상 위험할 수 있습니다.|
