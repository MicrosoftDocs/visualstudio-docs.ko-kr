---
title: 도메인 역할의 속성
ms.date: 11/04/2016
ms.topic: reference
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6c1c62126d65107bb25e3c4a475a794116c47193
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544146"
---
# <a name="properties-of-domain-roles"></a>도메인 역할의 속성
다음 표의 속성은 도메인 역할과 연결 되어 있습니다. 도메인 역할에 대 한 자세한 내용은 [모델, 클래스 및 관계 이해](../modeling/understanding-models-classes-and-relationships.md)를 참조 하세요. 이러한 속성을 사용 하는 방법에 대 한 자세한 내용은 [도메인별 언어 사용자 지정 및 확장](../modeling/customizing-and-extending-a-domain-specific-language.md)을 참조 하세요.

|속성|설명|기본값|
|-|-|-|
|컬렉션 형식|이 역할의 다중성이 0 ..1 또는 1.. 인 경우 \* 이 속성은 링크 컬렉션을 저장 하는 데 사용 되는 제네릭 형식을 사용자 지정 합니다.|`(none)` - <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> 사용 됨|
|사용자 지정 특성|여기에서 지정 하는 특성은 생성 된 코드 클래스에 특성으로 추가 됩니다.|<없음\>|
|속성 검색 가능|인 경우 `True` 와 관계의 다중성이 0 ..1 또는 1 ..1 이면 역할 속성은 사용자가 **속성** 창에서 찾을 수 있습니다. 속성은 관계 링크의 다른 쪽 끝에 있는 요소의 이름을 표시 합니다.|`True`|
|속성 생성기|인 경우 `True` 이 역할에 대 한 역할 속성이 생성 되며이 역할은 프로그램 코드에서 관계를 트래버스하는 데 사용할 수 있습니다. 이 값을 false로 설정 하면 도메인 관계의 정적 메서드를 사용 하 여 보다 효율적인 방법으로 관계를 트래버스할 수 있습니다.|`True`|
|속성 Getter 액세스 한정자|생성 된 속성 ( `public` ,, `internal` `private` , 또는)에 대 한 getter의 액세스 한정자 `protected` `protected internal` 입니다.|`public`|
|속성 Setter 액세스 한정자|생성 된 속성 ( `public` ,, `internal` `private` , 또는)에 대 한 setter의 액세스 한정자 `protected` `protected internal` 입니다.|`public`|
|다중성|반대 역할 ( `0..1` , `1..1` , `0..*` 또는)을 재생할 수 있는 모델 요소의 수입니다 `1..*` . 복합성이 `0..*` 또는 이면 생성 된 `1..*` 속성이 컬렉션을 나타내고, 그렇지 않으면 생성 된 속성이 단일 모델 요소를 나타냅니다.|관계 유형에 따라 달라 지 며 관계의 소스 또는 대상 역할 인지에 따라 달라 집니다.|
|Name|도메인 역할의 이름입니다. 이 속성은 공백을 포함할 수 없습니다.|이 역할에 대 한 역할 수행자의 도메인 클래스 이름입니다.|
|복사 전파|`DoNotPropagateCopy` -복사한 역할 플레이어에는이 링크의 복사본이 포함 되지 않습니다.<br /><br /> `PropagateCopyToLinkOnly` -복사 된 링크가 기존 반대 역할 플레이어를 가리킵니다.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer` -복사 된 링크는 반대 역할 수행자의 복사본을 가리킵니다.|`PropagateCopyToLinkAndOppositeRolePlayer` 포함의 원본 역할<br /><br /> `DoNotPropagateCopy` 다른 역할의 경우.<br /><br /> 자세한 내용은 [복사 동작 사용자 지정](../modeling/customizing-copy-behavior.md) 을 참조 하세요.|
|전파 삭제|`True` 관련 링크를 삭제할 때이 역할을 수행 하는 요소를 삭제 하려면입니다.|`True` 포함 역할의 대상입니다.<br /><br /> `False` 다른 역할의 경우.|
|속성 이름|역할 수행자의 코드에서 생성 된 속성의 이름입니다. 이 이름에는 공백을 사용할 수 없습니다.|이 역할에 일 대 일 또는 일 대 일 복합성이 있는 경우 반대쪽 역할의 이름입니다. 그렇지 않으면 반대 역할의 복수화 이름입니다.|
|역할 수행자|관계에서이 역할을 수행할 수 있는 요소의 도메인 클래스입니다. 이 속성은 읽기 전용입니다.|이 역할에 대 한 역할 수행자의 도메인 클래스입니다.|
|참고|도메인 역할과 관련 된 비공식 메모입니다.|<없음\>|
|범주|생성 된 디자이너의 **속성** 창에 생성 된 속성이 표시 되는 범주입니다. 이 속성이 비어 있으면 생성 된 속성이 **기타** 범주 아래에 나타납니다.|<없음\>|
|설명|코드를 문서화 하는 데 사용 되 고 생성 된 디자이너의 UI에 사용 되는 설명입니다.<br /><br /> 설명은 역할 수행자 클래스에서 생성 된 속성에 대 한 IntelliSense 도구 설명에 표시 됩니다.|`Description for`*역할의 전체 이름입니다* .|
|표시 이름|생성 된 디자이너에서 도메인 역할에 대해 표시 되는 이름입니다.|이름 속성의 조정 된 값입니다.|
|Help Keyword|도메인 역할에 대 한 F1 도움말을 인덱싱하는 데 사용 되는 선택적 키워드입니다.|\<none>|
|속성 표시 이름|생성 된 역할 속성에 대해 생성 된 디자이너에 표시 되는 이름입니다.|속성 이름 속성의 조정 된 값입니다.|

> [!NOTE]
> 표시 이름의 기본값은 소문자 문자가 뒤에 오는 각 대문자 앞에 공백을 삽입 하 여 연결 된 속성 값을 기반으로 하며 그 뒤에 다른 대문자 문자가 오지 않습니다.

## <a name="see-also"></a>추가 정보

- [도메인 관계의 속성](../modeling/properties-of-domain-relationships.md)