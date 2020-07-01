---
title: 'CA2210: 어셈블리에는 올바른 강력한 이름이 있어야 합니다. | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
helpviewer_keywords:
- AssembliesShouldHaveValidStrongNames
- CA2210
ms.assetid: 8ed33d1c-8ec6-4b47-a692-e22dc8693088
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 8f800a550717abfabdfb9296fc8f6de49d127d73
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548202"
---
# <a name="ca2210-assemblies-should-have-valid-strong-names"></a>CA2210: 어셈블리에는 올바른 강력한 이름을 사용해야 합니다.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|AssembliesShouldHaveValidStrongNames|
|CheckId|CA2210|
|범주|Microsoft 디자인|
|변경 수준|주요 변경 아님|

## <a name="cause"></a>원인
 어셈블리가 강력한 이름으로 서명 되지 않았거나, 강력한 이름을 확인할 수 없거나, 컴퓨터의 현재 레지스트리 설정 없이 강력한 이름이 유효 하지 않습니다.

## <a name="rule-description"></a>규칙 설명
 이 규칙은 어셈블리의 강력한 이름을 검색 하 고 확인 합니다. 다음 조건 중 하나에 해당 하는 경우 위반이 발생 합니다.

- 어셈블리에 강력한 이름이 없습니다.

- 서명 후 어셈블리를 변경 했습니다.

- 어셈블리의 서명이 연기 되었습니다.

- 어셈블리가 잘못 서명 되었거나 서명이 실패 했습니다.

- 어셈블리에는 확인을 통과 하는 레지스트리 설정이 필요 합니다. 예를 들어 강력한 이름 도구 (Sn.exe)를 사용 하 여 어셈블리에 대 한 확인을 건너뜁니다.

  강력한 이름은 클라이언트에서 무단으로 변경된 어셈블리를 모르는 사이에 로드하지 못하도록 보호합니다. 강력한 이름이 없는 어셈블리는 극히 제한된 시나리오 이외에는 배포하면 안 됩니다. 제대로 서명되지 않은 어셈블리를 공유하거나 배포하면 어셈블리가 무단으로 변경되거나, 공용 언어 런타임에서 어셈블리를 로드할 수 없거나, 사용자가 자신의 컴퓨터에서 확인을 사용하지 못하게 될 수 있습니다. 강력한 이름이 없는 어셈블리는 다음과 같은 단점이 있습니다.

- 해당 원본을 확인할 수 없습니다.

- 어셈블리의 내용이 변경 된 경우 공용 언어 런타임에서 사용자에 게 경고를 표시 하지 않습니다.

- 전역 어셈블리 캐시에 로드할 수 없습니다.

  서명이 연기 된 어셈블리를 로드 하 고 분석 하려면 어셈블리에 대 한 확인을 사용 하지 않도록 설정 해야 합니다.

## <a name="how-to-fix-violations"></a>위반 문제를 해결하는 방법
 **키 파일을 만들려면**

 다음 절차 중 하나를 사용 합니다.

- SDK에서 제공 하는 어셈블리 링커 도구 (Al.exe)를 사용 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 합니다.

- V1.0 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 또는 v 1.1의 경우 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> 또는 특성을 사용 <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName> 합니다.

- 의 경우 [!INCLUDE[dnprdnlong](../includes/dnprdnlong-md.md)] , `/keyfile` 또는 `/keycontainer` 컴파일러 옵션 [/Keyfile (어셈블리에 서명할 키 또는 키 쌍 지정)](https://msdn.microsoft.com/library/9b71f8c0-541c-4fe5-a0c7-9364f42ecb06) 또는 [/KEYCONTAINER (어셈블리에 서명할 키 컨테이너 지정)](https://msdn.microsoft.com/library/94882d12-b77a-49c7-96d0-18a31aee001e) 링커 옵션을 c + +로 사용 합니다.

  **Visual Studio에서 강력한 이름으로 어셈블리를 서명 하려면**

1. 에서 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션을 엽니다.

2. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 속성을 클릭 **합니다.**

3. **서명** 탭을 클릭 하 고 **어셈블리 서명** 확인란을 선택 합니다.

4. **강력한 이름 키 파일 선택**에서 **새로 만들기**를 선택 합니다.

    **강력한 이름 키 만들기** 창이 표시 됩니다.

5. **키 파일 이름**에 강력한 이름 키의 이름을 입력 합니다.

6. 키를 암호로 보호할 지 여부를 선택 하 고 **확인**을 클릭 합니다.

7. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **빌드**를 클릭 합니다.

   **Visual Studio 외부에서 강력한 이름으로 어셈블리를 서명 하려면**

- SDK에서 제공 하는 강력한 이름 도구 (Sn.exe)를 사용 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 합니다. 자세한 내용은 [Sn.exe (강력한 이름 도구)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)를 참조 하세요.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 콘텐츠가 무단으로 변조 되지 않는 환경에서 어셈블리를 사용 하는 경우에만이 규칙에서 경고를 표시 하지 않습니다.

## <a name="see-also"></a>참고 항목
 <xref:System.Reflection.AssemblyKeyFileAttribute?displayProperty=fullName> <xref:System.Reflection.AssemblyKeyNameAttribute?displayProperty=fullName>
 [방법: 강력한 이름으로 어셈블리 서명](https://msdn.microsoft.com/library/2c30799a-a826-46b4-a25d-c584027a6c67) [Sn.exe (강력한 이름 도구)](https://msdn.microsoft.com/library/c1d2b532-1b8e-4c7a-8ac5-53b801135ec6)
