---
title: 도메인 역할의 속성
description: 컬렉션 유형, 사용자 지정 특성 및 Is Property Browsable과 같은 도메인 역할과 연결된 속성에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 670704a86f0c149d26c7c869259c0f2f6bb75881
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385150"
---
# <a name="properties-of-domain-roles"></a>도메인 역할의 속성
다음 표의 속성은 도메인 역할과 연결됩니다. 도메인 역할에 대한 자세한 내용은 [모델, 클래스 및 관계 이해를 참조하세요.](../modeling/understanding-models-classes-and-relationships.md) 이러한 속성을 사용하는 방법에 대한 자세한 내용은 [Domain-Specific 언어 사용자 지정 및 확장을 참조하세요.](../modeling/customizing-and-extending-a-domain-specific-language.md)

|속성|설명|기본값|
|-|-|-|
|컬렉션 형식|이 역할의 복합성이 0..* 또는 1.. 인 경우 \* 이 속성은 링크 컬렉션을 저장하는 데 사용되는 제네릭 형식을 사용자 지정합니다.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> 가 사용되었습니다.|
|사용자 지정 특성|여기서 지정하는 특성은 생성된 코드 클래스에 특성으로 추가됩니다.|<없음\>|
|속성 검색 가능|`True`이고 관계의 복합성이 0..1 또는 1..1이면 **속성** 창에서 사용자가 역할 속성을 검색할 수 있습니다. 속성은 관계 링크의 다른 쪽 끝에 있는 요소의 이름을 표시합니다.|`True`|
|Is 속성 생성기|이면 `True` 프로그램 코드에서 관계를 트래버스하는 데 사용할 수 있는 이 역할에 대한 역할 속성이 생성됩니다. 이 false를 설정하면 도메인 관계의 정적 메서드를 사용하여 덜 효율적인 방식으로 관계를 트래버스할 수 있습니다.|`True`|
|속성 Getter 액세스 한정자|생성된 속성(, 또는 )에 대한 getter의 액세스 한정자입니다. `public` `internal` `private` `protected` `protected internal`|`public`|
|속성 Setter 액세스 한정자|생성된 속성(, 또는 )에 대한 setter의 액세스 한정자입니다. `public` `internal` `private` `protected` `protected internal`|`public`|
|다중성|반대 역할(, , 또는 )을 재생할 수 있는 모델 요소의 `0..1` `1..1` `0..*` `1..*` 수입니다. 복합성이 또는 이면 `0..*` `1..*` 생성된 속성이 컬렉션을 나타내고, 그렇지 않으면 생성된 속성이 단일 모델 요소를 나타냅니다.|관계 유형 및 관계의 원본 역할인지 아니면 대상 역할인지에 따라 달라집니다.|
|속성|도메인 역할의 이름입니다. 이 속성은 공백을 포함할 수 없습니다.|이 역할에 대한 역할 플레이어의 도메인 클래스 이름입니다.|
|복사 전파|`DoNotPropagateCopy` - 복사된 역할 플레이어에는 이 링크의 복사본이 없습니다.<br /><br /> `PropagateCopyToLinkOnly` - 복사된 링크는 기존의 반대 역할 플레이어를 가리킵니다.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` - 복사된 링크는 반대쪽 역할 플레이어의 복사본을 가리킵니다.|`PropagateCopyToLinkAndOppositeRolePlayer` 포함의 원본 역할에 대한 입니다.<br /><br /> `DoNotPropagateCopy` 다른 역할의 경우 입니다.<br /><br /> 자세한 내용은 [복사 동작 사용자 지정을 참조하세요.](../modeling/customizing-copy-behavior.md)|
|삭제 전파|`True` 연결된 링크가 삭제될 때 이 역할을 수행하는 요소를 삭제하려면 입니다.|`True` 포함 역할의 대상에 대한 입니다.<br /><br /> `False` 다른 역할의 경우 입니다.|
|속성 이름|역할 플레이어의 코드에서 생성된 속성의 이름입니다. 이 이름은 공백을 포함할 수 없습니다.|이 역할에 0대 1 또는 일 대 일 복합성이 있는 경우 반대 역할의 이름입니다. 그렇지 않으면 반대 역할의 복수화된 이름입니다.|
|역할 플레이어|관계에서 이 역할을 할 수 있는 요소의 도메인 클래스입니다. 이 속성은 읽기 전용입니다.|이 역할에 대한 역할 플레이어의 도메인 클래스입니다.|
|참고|도메인 역할과 관련된 비공식 메모입니다.|<없음\>|
|범주|생성된 속성이 생성된 디자이너의 **속성** 창에 표시되는 범주입니다. 이 속성이 비어 있으면 생성된 속성이 **기타** 범주 아래에 표시됩니다.|<없음\>|
|설명|코드를 문서화하는 데 사용되며 생성된 디자이너의 UI에 사용되는 설명입니다.<br /><br /> 설명은 역할 플레이어 클래스에서 생성된 속성에 대한 IntelliSense 도구 설명에 표시됩니다.|`Description for`*역할의 전체 이름*|
|표시 이름|도메인 역할에 대해 생성된 디자이너에 표시되는 이름입니다.|Name 속성의 조정된 값입니다.|
|Help Keyword|도메인 역할에 대한 F1 도움말을 인덱싱하는 데 사용되는 선택적 키워드입니다.|\<none>|
|속성 표시 이름|생성된 역할 속성에 대해 생성된 디자이너에 표시되는 이름입니다.|속성 이름 속성의 조정된 값입니다.|

> [!NOTE]
> 표시 이름의 기본값은 뒤에 소문자 문자가 있고 그 뒤에 다른 대문자 문자가 없는 각 대문자 문자 앞에 공백을 삽입하여 연결된 속성 값을 기반으로 합니다.

## <a name="see-also"></a>참조

- [도메인 관계의 속성](../modeling/properties-of-domain-relationships.md)