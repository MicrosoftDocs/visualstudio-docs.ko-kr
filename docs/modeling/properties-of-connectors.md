---
title: 연결선의 속성
description: 커넥터가 생성된 디자이너에서 도메인 관계를 나타내고 이러한 속성을 사용하여 도메인 특정 언어를 사용자 지정하고 확장하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, connectors
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 43f55aecf134bf8e4d043a4fc7f6ffa2201f8e95
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390817"
---
# <a name="properties-of-connectors"></a>연결선의 속성
커넥터는 생성된 디자이너에서 도메인 관계를 나타냅니다.

 자세한 내용은 [Domain-Specific 언어를 정의하는 방법을 참조하세요.](../modeling/how-to-define-a-domain-specific-language.md) 이러한 속성을 사용하는 방법에 대한 자세한 내용은 [Domain-Specific 언어 사용자 지정 및 확장을 참조하세요.](../modeling/customizing-and-extending-a-domain-specific-language.md)

 커넥터에는 다음 표에 나열된 속성이 있습니다.

|속성|설명|기본값|
|-|-|-|
|색|이 커넥터의 색입니다.|검정|
|대시 스타일|이 커넥터의 선에 대한 대시 스타일(Solid, Dash, Dot, DashDot, DashDotDot 또는 Custom)입니다.|단색|
|원본 끝 스타일|이 커넥터의 소스 끝 스타일(EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond 또는 None)입니다.|없음|
|대상 끝 스타일|이 커넥터의 대상 끝 스타일입니다(EmptyArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond 또는 None).|없음|
|텍스트 색|이 커넥터와 연결된 텍스트 데코레이터에 사용되는 색입니다.|검정|
|Thickness|이 커넥터에 대한 선 두께(인치 단위)입니다.|0.03125|
|액세스 한정자|클래스의 액세스 수준( `public` 또는 `internal` )입니다.|공용|
|사용자 지정 특성|이 커넥터에서 생성된 소스 코드 클래스에 특성을 추가하는 데 사용됩니다.|\<none>|
|Double 파생 생성|이면 `True` 재정의를 통한 사용자 지정을 지원하기 위해 기본 클래스와 partial 클래스가 모두 생성됩니다. 자세한 내용은 [재정의 및 생성된 클래스 확장을 참조하세요.](../modeling/overriding-and-extending-the-generated-classes.md)|거짓|
|사용자 지정 생성자가 있습니다.|이면 `True` 소스 코드에 사용자 지정 생성자가 제공됩니다. 자세한 내용은 [재정의 및 생성된 클래스 확장을 참조하세요.](../modeling/overriding-and-extending-the-generated-classes.md)|거짓|
|상속 한정자|커넥터( 또는 )에서 생성된 소스 코드 클래스의 상속 종류에 대해 `none` `abstract` `sealed` 설명합니다.|없음|
|기본 커넥터|이 커넥터의 기본 클래스입니다.|(없음)|
|속성|이 커넥터의 이름입니다.|현재 이름|
|네임스페이스|이 커넥터와 관련된 네임스페이스입니다.|현재 네임스페이스|
|도구 설명 형식|도구 설명이 정의되는 방식(고정, 변수 또는 없음)입니다. 고정된 경우 `Fixed Tooltip Text` 속성 값이 도구 설명으로 사용됩니다. 변수이면 도구 설명이 사용자 지정 코드에 정의됩니다.|\<none>|
|참고|이 커넥터와 관련된 비공식 참고 사항입니다.|\<none>|
|라우팅 스타일|커넥터를 라우팅하는 데 사용되는 스타일입니다. `Rectilinear`커넥터는 필요에 따라 오른쪽 턴을 만듭니다. `Straight` 커넥터는 그렇지 않습니다.|직선|
|노출되는 색 속성<br /><br /> 대시 스타일을 속성으로 노출<br /><br /> 노출되는 두께를 속성으로<br /><br /> 텍스트 색 노출|이면 `True` 사용자가 도형의 명시된 속성을 설정할 수 있습니다. 이를 설정하려면 도형 정의를 마우스 오른쪽 단추로 클릭하고 **노출된 추가를** 클릭합니다.|거짓|
|설명|생성된 디자이너를 문서화하는 데 사용됩니다.|\<none>|
|표시 이름|이 커넥터에 대해 생성된 디자이너에 표시할 이름입니다.|\<none>|
|고정 도구 설명 텍스트|고정 도구 설명에 사용되는 텍스트입니다.|\<none>|
|Help Keyword|이 요소에 대한 F1 도움말을 인덱싱하는 데 사용되는 키워드입니다.|\<none>|

## <a name="see-also"></a>참조

- [도메인 특정 언어 도구 용어집](/previous-versions/bb126564(v=vs.100))