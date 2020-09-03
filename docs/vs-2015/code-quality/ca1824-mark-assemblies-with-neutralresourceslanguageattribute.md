---
title: 'CA1824: NeutralResourcesLanguageAttribute를 사용 하 여 어셈블리 표시 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1824
- MarkAssembliesWithNeutralResourcesLanguage
helpviewer_keywords:
- MarkAssembliesWithNeutralResourcesLanguage
- CA1824
ms.assetid: 10e97f8a-aa6e-47aa-b253-1e5d3a295d82
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 19077a63d5aa22bda3f968943703a82488e2745d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85545290"
---
# <a name="ca1824-mark-assemblies-with-neutralresourceslanguageattribute"></a>CA1824: NeutralResourcesLanguageAttribute로 어셈블리를 표시하세요.
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|항목|값|
|-|-|
|TypeName|MarkAssembliesWithNeutralResourcesLanguage|
|CheckId|CA1824|
|범주|Microsoft 성능|
|변경 수준|최신이 아님|

## <a name="cause"></a>원인
 어셈블리가 **ResX**기반 리소스를 포함 하지만이 리소스에는 적용 되지 않습니다 <xref:System.Resources.NeutralResourcesLanguageAttribute?displayProperty=fullName> .

## <a name="rule-description"></a>규칙 설명
 **NeutralResourcesLanguage** 특성은 어셈블리에 대 한 중립 문화권의 리소스를 표시 하는 데 사용 된 언어를 **ResourceManager** 에 알립니다. 중립 리소스 언어와 동일한 문화권에서 리소스를 조회 하는 경우 **ResourceManager** 는 주 어셈블리에 있는 리소스를 자동으로 사용 합니다. 현재 스레드에 대 한 현재 사용자 인터페이스 문화권이 있는 위성 어셈블리를 검색 하는 대신이를 수행 합니다. 이렇게 하면 로드한 첫 리소스에 대한 찾기 성능을 향상시킬 수 있으며 작업이 간단해집니다.

## <a name="fixing-violations"></a>위반 수정
 이 규칙 위반 문제를 해결 하려면 어셈블리에 특성을 추가 하 고 중립 문화권의 리소스 언어를 지정 합니다.

## <a name="specifying-the-language"></a>언어 지정

#### <a name="to-specify-the-language-of-the-resource-of-the-neutral-culture"></a>중립 문화권의 리소스 언어를 지정 하려면

1. **솔루션 탐색기**에서 프로젝트를 마우스 오른쪽 단추로 클릭 한 다음 **속성**을 클릭 합니다.

2. 왼쪽 탐색 모음에서 **응용 프로그램**을 선택 하 고 **어셈블리 정보**를 클릭 합니다.

3. **어셈블리 정보** 대화 상자의 **중립 언어** 드롭다운 목록에서 언어를 선택 합니다.

4. **확인**을 클릭합니다.

## <a name="when-to-suppress-warnings"></a>경고를 표시하지 않는 경우
 이 규칙에서는 경고를 표시 하지 않을 수 있습니다. 그러나 시작 성능이 저하 될 수 있습니다.
