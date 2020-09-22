---
title: 도메인 관계의 속성
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Domain-Specific Language, domain relationships
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 0e432e9738009c84b6930b0363ae4048c925d0a6
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90810004"
---
# <a name="properties-of-domain-relationships"></a>도메인 관계의 속성
다음 표의 속성은 도메인 관계와 연결 되어 있습니다. 도메인 관계에 대 한 자세한 내용은 [모델, 클래스 및 관계 이해](../modeling/understanding-models-classes-and-relationships.md)를 참조 하세요. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)을 참조 하세요.

|속성|설명|기본값|
|-|-|-|
|액세스 한정자|도메인 관계 (또는)에 대 한 액세스 수준입니다 `public` `internal` .|`public`|
|사용자 지정 특성|도메인 관계에서 생성 되는 소스 코드 클래스에 특성을 추가 하는 데 사용 됩니다.|\<none>|
|Double 파생을 생성 합니다.|이면 `True` 재정의를 통한 사용자 지정을 지원 하기 위해 기본 클래스와 partial 클래스가 모두 생성 됩니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|`False`|
|사용자 지정 생성자 있음|인 경우 `True` 소스 코드에서 사용자 지정 생성자가 제공 됨을 나타냅니다. 자세한 내용은 [생성 된 클래스 재정의 및 확장](../modeling/overriding-and-extending-the-generated-classes.md)을 참조 하세요.|`False`|
|상속 한정자|도메인 관계 (또는)에서 생성 되는 소스 코드 클래스의 상속 유형을 설명 합니다 `none` `abstract` `sealed` .|\<none>|
|중복 허용|인 경우 `True` 동일한 두 요소 간에 도메인 관계의 중복 링크를 만들 수 있습니다.|`False`|
|기본 관계|도메인 관계가 파생 된 경우 도메인 관계의 기본 관계입니다.|\<none>|
|포함|이면 `True` 도메인 관계가 포함 관계입니다. 인 경우 `False` 관계는 참조 관계입니다.|\<both>|
|Name|도메인 관계의 이름입니다.|현재 이름|
|네임스페이스|도메인 관계와 관련 된 네임 스페이스입니다.|현재 네임 스페이스|
|참고|도메인 관계와 관련 된 비공식 메모입니다.|\<none>|
|설명|코드를 문서화 하는 데 사용 되 고 생성 된 디자이너의 UI에 사용 되는 설명입니다.|\<none>|
|표시 이름|생성 된 디자이너에서 도메인 관계에 대해 표시 되는 이름입니다.|\<none>|
|Help Keyword|도메인 관계에 대 한 F1 도움말을 인덱싱하는 데 사용 되는 선택적 키워드입니다.|\<none>|

## <a name="see-also"></a>추가 정보

- [도메인 특정 언어 도구 용어집](/previous-versions/bb126564(v=vs.100))