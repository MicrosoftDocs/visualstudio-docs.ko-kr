---
title: 세계화 경고 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- vs.codeanalysis.globalizationrules
helpviewer_keywords:
- warnings, globalization
- globalization warnings
- globalization [Visual Studio], warnings
- managed code analysis warnings, globalization warnings
ms.assetid: a8d12d41-14bf-4b43-af24-168312d7c390
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7db942f410b9a6a8c2f12a044d0e48ad1ad19950
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667578"
---
# <a name="globalization-warnings"></a>전역화 경고
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

세계화 경고는 전 세계에서 사용할 수 있는 라이브러리 및 응용 프로그램을 지원 합니다.

## <a name="in-this-section"></a>섹션 내용

|규칙|설명|
|----------|-----------------|
|[CA1300: MessageBoxOptions를 지정하세요.](../code-quality/ca1300-specify-messageboxoptions.md)|오른쪽에서 왼쪽으로 읽기 순서를 사용하는 문화권에 대해 메시지 상자를 올바로 표시하려면 MessageBoxOptions 열거형의 RightAlign 및 RtlReading 멤버를 Show 메서드로 전달해야 합니다.|
|[CA1301: 중복 액셀러레이터 키를 사용하지 마십시오.](../code-quality/ca1301-avoid-duplicate-accelerators.md)|액셀러레이터 키라고도 하는 선택키를 사용하면 Alt 키를 사용하여 키보드로 컨트롤에 액세스할 수 있습니다. 여러 컨트롤에 중복되는 선택키가 있으면 선택키의 동작이 제대로 정의되지 않은 경우입니다.|
|[CA1302: 로캘별 문자열을 하드코드하지 마세요.](../code-quality/ca1302-do-not-hardcode-locale-specific-strings.md)|System.Environment.SpecialFolder 열거형에는 특수 시스템 폴더를 참조하는 멤버가 포함되어 있습니다. 이러한 폴더의 위치는 운영 체제에 따라 값이 다를 수 있으며, 사용자가 위치 일부를 변경할 수 있고, 위치는 지역화됩니다. Environment.GetFolderPath 메서드는 Environment.SpecialFolder 열거형과 연관된 위치를 반환하며 이 위치는 지역화되므로 현재 실행되고 있는 컴퓨터에 적합합니다.|
|[CA1303: 리터럴을 지역화된 매개 변수로 전달하지 마세요.](../code-quality/ca1303-do-not-pass-literals-as-localized-parameters.md)|외부에서 볼 수 있는 메서드가 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 클래스 라이브러리의 생성자 또는 메서드에 문자열 리터럴을 매개 변수로 전달하는데 이 문자열은 지역화될 수 있어야 합니다.|
|[CA1304: CultureInfo를 지정하세요.](../code-quality/ca1304-specify-cultureinfo.md)|메서드 또는 생성자가 System.Globalization.CultureInfo 매개 변수를 받아들이는 오버로드가 있는 멤버를 호출하지만 CultureInfo 매개 변수를 사용하는 오버로드는 호출하지 않습니다. CultureInfo 또는 System.IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다.|
|[CA1305: IFormatProvider를 지정하세요.](../code-quality/ca1305-specify-iformatprovider.md)|메서드 또는 생성자가 System.IFormatProvider 매개 변수를 받아들이는 오버로드가 있는 하나 이상의 멤버를 호출하지만 IFormatProvider 매개 변수를 사용하는 오버로드는 호출하지 않습니다. System.Globalization.CultureInfo 또는 IFormatProvider 개체가 제공되지 않으면 오버로드된 멤버에서 제공하는 기본값이 모든 로캘에서 원하는 효과를 나타내지 않을 수 있습니다.|
|[CA1306: 데이터 형식에 맞는 로캘을 설정하세요.](../code-quality/ca1306-set-locale-for-data-types.md)|로캘은 숫자 값에 사용되는 서식, 통화 기호 및 정렬 순서 등과 같은 데이터의 문화권별 표현 요소를 결정합니다. DataTable 또는 DataSet를 만들 때는 로캘을 명시적으로 설정해야 합니다.|
|[CA1307: StringComparison 지정하세요.](../code-quality/ca1307-specify-stringcomparison.md)|문자열 비교 작업에서 StringComparison 매개 변수를 설정하지 않는 메서드 오버로드를 사용합니다.|
|[CA1308: 대문자로 문자열을 정규화하세요.](../code-quality/ca1308-normalize-strings-to-uppercase.md)|문자열은 대문자로 정규화되어야 합니다. 일부 문자는 소문자로 변환될 때 다시 대문자로 변환될 수 없습니다.|
|[CA1309: 서수 StringComparison을 사용하세요.](../code-quality/ca1309-use-ordinal-stringcomparison.md)|비언어 문자열 비교 작업에서는 StringComparison 매개 변수를 Ordinal 또는 OrdinalIgnoreCase로 설정하지 않습니다. 매개 변수가 명시적으로 StringComparison.Ordinal 또는 StringComparison.OrdinalIgnoreCase로 설정되기 때문에 코드 실행 속도, 정확도 및 신뢰도가 향상됩니다.|
|[CA2101: P/Invoke 문자열 인수에 대해 마샬링을 지정 하십시오.](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|플랫폼 호출 멤버는 부분적으로 신뢰할 수 있는 호출자를 허용 하 고 문자열 매개 변수를 포함 하며 문자열을 명시적으로 마샬링할 수 없습니다. 이렇게 하면 보안상 위험할 수 있습니다.|
