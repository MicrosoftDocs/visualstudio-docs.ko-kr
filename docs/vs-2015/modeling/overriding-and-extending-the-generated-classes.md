---
title: 생성 된 클래스 재정의 및 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16a09a5b0f5e534d310092036b8e7eb1d4c344d9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668483"
---
# <a name="overriding-and-extending-the-generated-classes"></a>생성된 클래스 재정의 및 확장
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

DSL 정의는 도메인 특정 언어를 기반으로 하는 강력한 도구 집합을 빌드할 수 있는 플랫폼입니다. 많은 확장과 adaptation는 DSL 정의에서 생성 된 클래스를 재정의 하 고 확장 하 여 만들 수 있습니다. 이러한 클래스에는 DSL 정의 다이어그램에서 명시적으로 정의 된 도메인 클래스 뿐 아니라 도구 상자, 탐색기, serialization 등을 정의 하는 기타 클래스도 포함 됩니다.

## <a name="extensibility-mechanisms"></a>확장성 메커니즘
 생성 된 코드를 확장할 수 있는 몇 가지 메커니즘이 제공 됩니다.

### <a name="overriding-methods-in-a-partial-class"></a>Partial 클래스의 메서드 재정의
 Partial 클래스 정의를 사용 하면 클래스를 둘 이상의 위치로 정의할 수 있습니다. 이렇게 하면 생성 된 코드를 사용자가 직접 작성 하는 코드와 분리할 수 있습니다. 수동으로 작성 된 코드에서 생성 된 코드에 의해 상속 된 클래스를 재정의할 수 있습니다.

 예를 들어 DSL 정의에서 라는 도메인 클래스를 정의 하는 경우 `Book` 재정의 메서드를 추가 하는 사용자 지정 코드를 작성할 수 있습니다.

 `public partial class Book`

 `{`

 `protected override void OnDeleting()`

 `{`

 `MessageBox.Show("Deleting book " + this.Title);`

 `base.OnDeleting();`

 `} }`

> [!NOTE]
> 생성 된 클래스의 메서드를 재정의 하려면 항상 생성 된 파일과 구분 되는 파일에 코드를 작성 합니다. 일반적으로 파일은 CustomCode 라는 폴더에 포함 되어 있습니다. 생성 된 코드를 변경 하는 경우 DSL 정의에서 코드를 다시 생성 하면 해당 코드가 손실 됩니다.

 재정의할 수 있는 메서드를 검색 하려면 클래스에서 **override** 를 입력 하 고 그 뒤에 공백을 입력 합니다. IntelliSense 도구 설명에서 재정의할 수 있는 메서드를 알려 줍니다.

### <a name="double-derived-classes"></a>이중 파생 클래스
 생성 된 클래스에 있는 대부분의 메서드는 모델링 네임 스페이스의 고정 클래스 집합에서 상속 됩니다. 그러나 일부 메서드는 생성 된 코드에 정의 되어 있습니다. 일반적으로 이것은 재정의할 수 없음을 의미 합니다. 동일한 클래스의 다른 부분 정의에 정의 된 메서드를 partial 클래스 하나에서 재정의할 수 없습니다.

 그럼에도 불구 하 고 도메인 클래스에 대해 생성 된 **이중 파생** 플래그를 설정 하 여 이러한 메서드를 재정의할 수 있습니다. 이렇게 하면 두 개의 클래스가 생성 되며 하나는 다른 클래스의 추상 기본 클래스입니다. 모든 메서드 및 속성 정의는 기본 클래스에 있으며 생성자만 파생 클래스에 있습니다.

 예를 들어 샘플 라이브러리나 dsl에서 `CirculationBook` 도메인 클래스의 `Generates``Double Derived` 속성은로 설정 `true` 됩니다. 해당 도메인 클래스에 대해 생성 된 코드에는 두 개의 클래스가 포함 됩니다.

- `CirculationBookBase`는 추상 이며 모든 메서드와 속성을 포함 합니다.

- `CirculationBook`에서 파생 되는 `CirculationBookBase` 입니다. 생성자를 제외 하 고는 비어 있습니다.

  메서드를 재정의 하려면와 같은 파생 클래스의 부분 정의를 만듭니다 `CirculationBook` . 생성 된 메서드와 모델링 프레임 워크에서 상속 된 메서드를 모두 재정의할 수 있습니다.

  모델 요소, 관계, 도형, 다이어그램 및 연결선을 비롯 한 모든 형식의 요소에이 메서드를 사용할 수 있습니다. 다른 생성 된 클래스의 메서드를 재정의할 수도 있습니다. ToolboxHelper와 같은 일부 생성 된 클래스는 항상 double로 파생 됩니다.

### <a name="custom-constructors"></a>사용자 지정 생성자
 생성자는 재정의할 수 없습니다. 이중 파생 클래스 에서도 생성자는 파생 클래스에 있어야 합니다.

 사용자 고유의 생성자를 제공 하려는 경우 `Has Custom Constructor` DSL 정의에서 도메인 클래스에 대해를 설정 하 여이 작업을 수행할 수 있습니다. **모든 템플릿 변환**을 클릭 하면 생성 된 코드에는 해당 클래스에 대 한 생성자가 포함 되지 않습니다. 누락 된 생성자에 대 한 호출을 포함 합니다. 이렇게 하면 솔루션을 빌드할 때 오류 보고서가 발생 합니다. 오류 보고서를 두 번 클릭 하 여 생성 된 코드에서 제공 해야 하는 항목을 설명 하는 설명을 확인 합니다.

 생성 된 파일과 별도의 파일에 partial 클래스 정의를 작성 하 고 생성자를 제공 합니다.

### <a name="flagged-extension-points"></a>플래그가 지정 된 확장 위치
 플래그가 지정 된 확장 지점은 DSL 정의에서 사용자 지정 메서드를 제공 한다는 것을 나타내기 위해 속성 또는 확인란을 설정할 수 있는 위치입니다. 사용자 지정 생성자는 한 가지 예입니다. 또 다른 예로는 `Kind` 도메인 속성의를 계산 또는 사용자 지정 저장소로 설정 하거나 연결 작성기에서 Is custom 플래그를 설정 하는 **것이** 있습니다.

 각각의 경우 플래그를 설정 하 고 코드를 다시 생성 하면 빌드 오류가 발생 합니다. 오류를 두 번 클릭 하 여 제공 해야 할 항목을 설명 하는 설명을 표시 합니다.

### <a name="rules"></a>규칙
 트랜잭션 관리자를 사용 하면 속성의 변경과 같이 지정 된 이벤트가 발생 한 트랜잭션의 끝 이전에 실행 되는 규칙을 정의할 수 있습니다. 규칙은 일반적으로 저장소에 있는 서로 다른 요소 간의 synchronism를 유지 관리 하는 데 사용 됩니다. 예를 들어 규칙을 사용 하 여 다이어그램에 모델의 현재 상태가 표시 되는지 확인 합니다.

 규칙은 각 개체에 대해 규칙을 등록 하는 코드를 가질 필요가 없도록 클래스 별로 정의 됩니다. 자세한 내용은 [모델 내에서 변경 내용 전파 규칙](../modeling/rules-propagate-changes-within-the-model.md)을 참조 하세요.

### <a name="store-events"></a>이벤트 저장
 모델링 저장소는 요소의 추가 및 삭제, 속성 값의 변경 등을 비롯 하 여 저장소의 특정 변경 유형을 수신 하는 데 사용할 수 있는 이벤트 메커니즘을 제공 합니다. 이벤트 처리기는 변경이 수행 된 트랜잭션이 종료 된 후에 호출 됩니다. 일반적으로 이러한 이벤트는 저장소 외부의 리소스를 업데이트 하는 데 사용 됩니다.

### <a name="net-events"></a>.NET 이벤트
 셰이프에 대 한 일부 이벤트를 구독할 수 있습니다. 예를 들어, 도형에서 마우스 클릭을 수신할 수 있습니다. 각 개체에 대해 이벤트를 구독 하는 코드를 작성 해야 합니다. 이 코드는 InitializeInstanceResources ()의 재정의로 작성 될 수 있습니다.

 ShapeFields에서 생성 되는 일부 이벤트는 도형에 데코레이터을 그리는 데 사용 됩니다. 예제는 [방법: 모양 또는 데코레이터 클릭 가로채기](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md)를 참조 하세요.

 이러한 이벤트는 일반적으로 트랜잭션 내에서 발생 하지 않습니다. 저장소에서 변경을 수행 하려는 경우 트랜잭션을 만들어야 합니다.
