---
title: 변경 내용에 대한 대응 및 전파
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fbe09c242fce137d90b90ff2d6c547cee1ed2dc7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75595399"
---
# <a name="respond-to-and-propagate-changes"></a>변경 내용에 대 한 응답 및 전파

요소가 만들어지거나 삭제 되거나 업데이트 되 면 변경 내용을 모델의 다른 부분 또는 파일, 데이터베이스 또는 기타 구성 요소와 같은 외부 리소스에 전파 하는 코드를 작성할 수 있습니다.

## <a name="reference"></a>참조

지침으로 다음과 같은 방법으로 이러한 기술을 고려 합니다.

|방법|시나리오|참조 항목|
|-|-|-|
|계산 된 도메인 속성을 정의 합니다.|모델의 다른 속성에서 값을 계산 하는 도메인 속성입니다. 예를 들어 관련 된 요소 가격의 합계인 가격입니다.|[계산된 스토리지 속성 및 사용자 지정 스토리지 속성](../modeling/calculated-and-custom-storage-properties.md)|
|사용자 지정 저장소 도메인 속성을 정의 합니다.|모델의 다른 부분이 나 외부에 저장 된 도메인 속성입니다. 예를 들어 모델의 트리로 식 문자열을 구문 분석할 수 있습니다.|[계산된 스토리지 속성 및 사용자 지정 스토리지 속성](../modeling/calculated-and-custom-storage-properties.md)|
|OnValueChanging 및 OnDeleting와 같은 변경 처리기 재정의|여러 요소를 동기화 된 상태로 유지 하 고 외부 값을 모델과 동기화 된 상태로 유지 합니다.<br /><br /> 정의 된 범위로 값을 제한 합니다.<br /><br /> 속성 값 및 기타 변경 전후에 바로 호출 됩니다. 예외를 throw 하 여 변경을 종료할 수 있습니다.|[도메인 속성 값 변경 처리기](../modeling/domain-property-value-change-handlers.md)|
|규칙|변경이 발생 한 트랜잭션의 끝 직전에 실행 대기 중인 규칙을 정의할 수 있습니다. 실행 취소 또는 다시 실행 시에는 실행 되지 않습니다. 저장소의 한 부분을 다른 부분에 동기화 하는 데 사용 합니다.|[규칙으로 모델 내부의 변경 내용 전파](../modeling/rules-propagate-changes-within-the-model.md)|
|이벤트 저장|모델링 저장소는 요소나 링크를 추가 또는 삭제 하거나 속성의 값을 변경 하는 등의 이벤트에 대 한 알림을 제공 합니다. 이벤트는 실행 취소 및 다시 실행 에서도 실행 됩니다. 저장소 이벤트를 사용 하 여 저장소에 없는 값을 업데이트 합니다.|[이벤트 처리기로 모델 외부의 변경 내용 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|.NET 이벤트|셰이프에는 마우스 클릭 및 기타 제스처에 응답 하는 이벤트 처리기가 있습니다. 각 개체에 대해 이러한 이벤트를 등록 해야 합니다. 등록은 일반적으로 InitializeInstanceResources의 재정의에서 수행 되며 각 요소에 대해 수행 되어야 합니다.<br /><br /> 이러한 이벤트는 일반적으로 트랜잭션 외부에서 발생 합니다.|[방법: 모양 또는 데코레이터 클릭 가로채기](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)|
|범위 규칙|범위 규칙은 특히 모양의 범위를 제한 하는 데 사용 됩니다.|[BoundsRules로 모양 위치 및 크기 제한](/visualstudio/modeling/boundsrules-constrain-shape-location-and-size?view=vs-2015)|
|선택 규칙|선택 규칙은 사용자가 선택할 수 있는 항목을 구체적으로 제한 합니다.|[방법: 현재 선택 항목 액세스 및 제약](../modeling/how-to-access-and-constrain-the-current-selection.md)|
|OnAssocatedPropertyChanged|도형 및 연결선의 기능을 사용 하는 모델 요소의 상태를 표시 합니다 (예: 그림자, 화살촉, 색, 선 두께 및 스타일).|[모양 및 연결선을 업데이트하여 모델 반영](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)|

## <a name="compare-rules-and-store-events"></a>규칙 및 저장소 이벤트 비교

변경 notifiers, 규칙 및 이벤트는 모델이 변경 될 때 실행 됩니다.

규칙은 일반적으로 변경이 발생 한 끝 트랜잭션에 적용 되며 트랜잭션의 변경 내용이 커밋된 후에 이벤트가 적용 됩니다.

저장소 이벤트를 사용 하 여 저장소 외부의 개체와 모델을 동기화 하 고 저장소 내에서 일관성을 유지 하는 규칙을 사용 합니다.

- **사용자 지정 규칙 만들기** 추상 규칙에서 파생 클래스로 사용자 지정 규칙을 만듭니다. 또한 사용자 지정 규칙에 대해 프레임 워크에 알려야 합니다. 자세한 내용은 [모델 내에서 변경 내용 전파 규칙](../modeling/rules-propagate-changes-within-the-model.md)을 참조 하세요.

- **이벤트 구독** 이벤트를 구독 하려면 이벤트 처리기를 만들고을 위임 합니다. 그런 다음 속성을 사용 <xref:Microsoft.VisualStudio.Modeling.Store.EventManagerDirectory%2A> 하 여 이벤트를 구독 합니다. 자세한 내용은 [이벤트 처리기가 모델 외부에서 변경 내용을 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)하는 방법을 참조 하세요.

- **변경 취소** 트랜잭션을 실행 취소 하면 이벤트가 발생 하지만 규칙은 적용 되지 않습니다. 규칙에서 값을 변경 하 고 해당 변경 내용을 실행 취소 하면 실행 취소 작업 중에 값이 원래 값으로 다시 설정 됩니다. 이벤트가 발생 하는 경우 값을 다시 원래 값으로 다시 변경 해야 합니다. 트랜잭션 및 실행 취소에 대해 자세히 알아보려면 [방법: 트랜잭션을 사용 하 여 모델 업데이트](../modeling/how-to-use-transactions-to-update-the-model.md)를 참조 하세요.

- **규칙 및 이벤트에 이벤트 인수 전달** 이벤트와 규칙에는 `EventArgs` 모델 변경 방법에 대 한 정보가 포함 된 매개 변수가 전달 됩니다.

## <a name="see-also"></a>추가 정보

- [방법: 모양 또는 데코레이터 클릭 가로채기](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)
- [도메인 특정 언어를 사용자 지정 하는 코드 작성](../modeling/writing-code-to-customise-a-domain-specific-language.md)
