---
title: 도메인 관계의 속성
description: 액세스 한정자, 사용자 지정 특성 및 이중 파생 생성과 같은 도메인 relationshop과 연결된 속성에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fc92bbc32a454208f3d455734b7697a2e69037b4
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112390661"
---
# <a name="properties-of-domain-relationships"></a>도메인 관계의 속성
다음 표의 속성은 도메인 관계와 연결됩니다. 도메인 관계에 대한 자세한 내용은 [모델, 클래스 및 관계 이해를 참조하세요.](../modeling/understanding-models-classes-and-relationships.md) 이러한 속성을 사용하는 방법에 대한 자세한 내용은 [Domain-Specific 언어 사용자 지정 및 확장을 참조하세요.](../modeling/customizing-and-extending-a-domain-specific-language.md)

|속성|설명|기본값|
|-|-|-|
|액세스 한정자|도메인 관계의 액세스 수준( `public` 또는 `internal` )입니다.|`public`|
|사용자 지정 특성|도메인 관계에서 생성된 소스 코드 클래스에 특성을 추가하는 데 사용됩니다.|\<none>|
|Double 파생 생성|이면 `True` 재정의를 통한 사용자 지정을 지원하기 위해 기본 클래스와 partial 클래스가 모두 생성됩니다. 자세한 내용은 [재정의 및 생성된 클래스 확장을 참조하세요.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|사용자 지정 생성자가 있습니다.|이면 `True` 사용자 지정 생성자가 소스 코드에 제공되었음을 나타냅니다. 자세한 내용은 [재정의 및 생성된 클래스 확장을 참조하세요.](../modeling/overriding-and-extending-the-generated-classes.md)|`False`|
|상속 한정자|도메인 관계( 또는 )에서 생성된 소스 코드 클래스의 상속 종류를 `none` `abstract` `sealed` 설명합니다.|\<none>|
|중복 허용|이면 `True` 동일한 두 요소 간에 도메인 관계의 중복 링크를 만들 수 있습니다.|`False`|
|기본 관계|도메인 관계가 파생된 경우 도메인 관계의 기본 관계입니다.|\<none>|
|포함 중|이면 `True` 도메인 관계가 포함 관계입니다. `False`이면 관계가 참조 관계입니다.|\<both>|
|속성|도메인 관계의 이름입니다.|현재 이름|
|네임스페이스|도메인 관계와 관련된 네임스페이스입니다.|현재 네임스페이스|
|참고|도메인 관계와 관련된 비공식 메모입니다.|\<none>|
|설명|코드를 문서화하는 데 사용되며 생성된 디자이너의 UI에 사용되는 설명입니다.|\<none>|
|표시 이름|도메인 관계에 대해 생성된 디자이너에 표시되는 이름입니다.|\<none>|
|Help Keyword|도메인 관계에 대한 F1 도움말을 인덱싱하는 데 사용되는 선택적 키워드입니다.|\<none>|

## <a name="see-also"></a>참조

- [도메인 특정 언어 도구 용어집](/previous-versions/bb126564(v=vs.100))