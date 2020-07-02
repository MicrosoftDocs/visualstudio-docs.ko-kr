---
title: 연결선의 속성
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a7bf5492d7da845b65904959cb57737fd438c28b
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85532277"
---
# <a name="properties-of-connectors"></a>연결선의 속성
커넥터는 생성 된 디자이너에서 도메인 관계를 나타냅니다.

 자세한 내용은 [도메인별 언어를 정의 하는 방법](../modeling/how-to-define-a-domain-specific-language.md)을 참조 하세요. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)을 참조 하세요.

 커넥터에는 다음 표에 나열 된 속성이 있습니다.

|속성|설명|기본값|
|-|-|-|
|색상|이 연결선의 색입니다.|검정|
|대시 스타일|이 연결선의 선 대시 스타일입니다 (Solid, 대시, 점, 일점 Dot, DashDotDot 또는 사용자 지정).|단색|
|원본 끝 스타일|이 연결선의 소스 끝 스타일 (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond 또는 None)입니다.|없음|
|대상 끝 스타일|이 연결선의 대상 끝 스타일 (HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond 또는 None)입니다.|없음|
|텍스트 색|이 커넥터와 연결 된 텍스트 데코레이터에 사용 되는 색입니다.|검정|
|Thickness|이 연결선의 선 두께 (인치)입니다.|0.03125|
|액세스 한정자|클래스의 액세스 수준 ( `public` 또는 `internal` )입니다.|공용|
|사용자 지정 특성|이 커넥터에서 생성 되는 소스 코드 클래스에 특성을 추가 하는 데 사용 됩니다.|\<none>|
|Double 파생을 생성 합니다.|이면 `True` 재정의를 통한 사용자 지정을 지원 하기 위해 기본 클래스와 partial 클래스가 모두 생성 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|False|
|사용자 지정 생성자 있음|이면 `True` 사용자 지정 생성자가 소스 코드에 제공 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|False|
|상속 한정자|커넥터 ( `none` , 또는)에서 생성 되는 소스 코드 클래스의 상속 종류에 대해 설명 `abstract` 합니다 `sealed` .|없음|
|기본 연결선|이 커넥터의 기본 클래스입니다.|(없음)|
|Name|이 커넥터의 이름입니다.|현재 이름|
|네임스페이스|이 커넥터와 관련 된 네임 스페이스입니다.|현재 네임 스페이스|
|도구 설명 형식|도구 설명을 정의 하는 방법 (고정, 변수 또는 없음)입니다. 고정 된 경우 `Fixed Tooltip Text` 속성 값이 도구 설명으로 사용 되 고, 변수 이면 도구 설명이 사용자 지정 코드에 정의 됩니다.|\<none>|
|참고|이 커넥터와 연결 된 비공식 메모입니다.|\<none>|
|라우팅 스타일|커넥터를 라우팅하는 데 사용 되는 스타일입니다. `Rectilinear`커넥터는 필요에 따라 직각 회전을 수행 `Straight` 합니다. 연결선은 그렇지 않습니다.|직각선|
|노출 된 색을 속성으로<br /><br /> 대시 스타일을 속성으로 노출<br /><br /> 노출 된 두께 (속성)<br /><br /> 텍스트 색을 노출 합니다.|이면 `True` 사용자가 셰이프의 설명 된 속성을 설정할 수 있습니다. 이를 설정 하려면 셰이프 정의를 마우스 오른쪽 단추로 클릭 하 고 **노출 추가**를 클릭 합니다.|False|
|설명|생성 된 디자이너를 문서화 하는 데 사용 됩니다.|\<none>|
|표시 이름|이 커넥터에 대해 생성 된 디자이너에 표시 되는 이름입니다.|\<none>|
|고정 도구 설명 텍스트|고정 도구 설명에 사용 되는 텍스트입니다.|\<none>|
|Help Keyword|이 요소에 대 한 F1 도움말을 인덱싱하는 데 사용 되는 키워드입니다.|\<none>|

## <a name="see-also"></a>참고 항목

- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)