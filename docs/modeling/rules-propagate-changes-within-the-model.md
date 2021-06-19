---
title: 규칙으로 모델 내부의 변경 내용 전파
description: VMSDK(시각화 및 모델링 SDK)에서 한 요소에서 다른 요소로 변경 내용을 전파하는 저장소 규칙을 만드는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: bde67bd8375e3752370b3b815f8ed155d3123741
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387595"
---
# <a name="rules-propagate-changes-within-the-model"></a>규칙으로 모델 내부의 변경 내용 전파
VMSDK(시각화 및 모델링 SDK)에서 요소 간 변경을 전파하는 저장소 규칙을 만들 수 있습니다. Store의 요소가 변경되면 일반적으로 가장 바깥쪽 트랜잭션이 커밋될 때 규칙이 실행되도록 예약됩니다. 요소 추가 또는 삭제와 같이 다양한 종류의 이벤트에 대한 다양한 규칙 유형이 있습니다. 특정 유형의 요소, 도형 또는 다이어그램에 규칙을 연결할 수 있습니다. 많은 기본 제공 기능은 규칙에 의해 정의됩니다. 예를 들어 규칙은 모델이 변경될 때 다이어그램이 업데이트되도록 합니다. 고유한 규칙을 추가하여 도메인 특정 언어를 사용자 지정할 수 있습니다.

 저장소 규칙은 특히 모델 요소, 관계, 셰이프 또는 커넥터 및 해당 도메인 속성에 대한 변경 내용과 같은 저장소 내에서 변경 내용을 전파하는 데 유용합니다. 사용자가 실행 취소 또는 다시 실행 명령을 호출할 때 규칙이 실행되지 않습니다. 대신 트랜잭션 관리자는 저장소 내용이 올바른 상태로 복원되도록 합니다. 저장소 외부의 리소스에 변경 내용을 전파하려면 Store 이벤트를 사용합니다. 자세한 내용은 [이벤트 처리기 모델 외부에서 변경 내용 전파를 참조하세요.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

 예를 들어 사용자(또는 코드)가 ExampleDomainClass 형식의 새 요소를 만들 때마다 다른 형식의 추가 요소가 모델의 다른 부분에 만들어지도록 지정한다고 가정합니다. AddRule을 작성하고 ExampleDomainClass와 연결할 수 있습니다. 규칙에 코드를 작성하여 추가 요소를 만듭니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;

namespace ExampleNamespace
{
 // Attribute associates the rule with a domain class:
 [RuleOn(typeof(ExampleDomainClass), FireTime=TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class MyAddRule : AddRule
 {
  // Override the abstract method:
  public override void ElementAdded(ElementAddedEventArgs e)
  {
    base.ElementAdded(e);
    ExampleDomainClass element = e.ModelElement;
    Store store = element.Store;
    // Ignore this call if we're currently loading a model:
    if (store.TransactionManager.CurrentTransaction.IsSerializing)
       return;

    // Code here propagates change as required - for example:
      AnotherDomainClass echo = new AnotherDomainClass(element.Partition);
      echo.Name = element.Name;
      echo.Parent = element.Parent;
    }
  }
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
   protected override Type[] GetCustomDomainModelTypes()
   {
     List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
     types.Add(typeof(MyAddRule));
     // If you add more rules, list them here.
     return types.ToArray();
   }
 }
}
```

> [!NOTE]
> 규칙 코드는 Store 내 요소의 상태만 변경해야 합니다. 즉, 규칙은 모델 요소, 관계, 도형, 커넥터, 다이어그램 또는 해당 속성만 변경해야 합니다. 저장소 외부의 리소스에 변경 내용을 전파하려면 저장소 이벤트를 정의합니다. 자세한 내용은 [이벤트 처리기 모델 외부에서 변경 내용 전파를 참조하세요.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

### <a name="to-define-a-rule"></a>규칙을 정의하려면

1. 특성을 접두사로 하여 규칙을 클래스로 `RuleOn` 정의합니다. 특성은 규칙을 도메인 클래스, 관계 또는 다이어그램 요소 중 하나에 연결합니다. 규칙은 추상일 수 있는 이 클래스의 모든 인스턴스에 적용됩니다.

2. 도메인 모델 클래스에서 에서 반환한 집합에 규칙을 추가하여 규칙을 `GetCustomDomainModelTypes()` 등록합니다.

3. 추상 Rule 클래스 중 하나에서 규칙 클래스를 파생시키고 실행 메서드의 코드를 작성합니다.

   다음 섹션에서는 이러한 단계를 좀 더 자세히 설명합니다.

### <a name="to-define-a-rule-on-a-domain-class"></a>도메인 클래스에 규칙을 정의하려면

- 사용자 지정 코드 파일에서 클래스를 정의하고 특성을 접두사로 <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> 추가합니다.

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- 첫 번째 매개 변수의 주체 형식은 도메인 클래스, 도메인 관계, 셰이프, 커넥터 또는 다이어그램일 수 있습니다. 일반적으로 도메인 클래스 및 관계에 규칙을 적용합니다.

     `FireTime`는 일반적으로 `TopLevelCommit` 입니다. 이렇게 하면 트랜잭션의 모든 기본 변경 내용이 적용된 후에만 규칙이 실행됩니다. 대안은 변경 후 즉시 규칙을 실행하는 인라인입니다. 및 LocalCommit - 현재 트랜잭션이 끝날 때 규칙을 실행합니다(가장 외부에 있지 않을 수 있습니다). 큐의 순서에 영향을 주도록 규칙의 우선 순위를 설정할 수도 있지만 이는 필요한 결과를 달성하는 불안정한 방법입니다.

- 추상 클래스를 주체 형식으로 지정할 수 있습니다.

- 규칙은 주체 클래스의 모든 인스턴스에 적용됩니다.

- 의 `FireTime` 기본값은 TimeToFire.TopLevelCommit입니다. 이렇게 하면 가장 외부 트랜잭션이 커밋될 때 규칙이 실행됩니다. 대안은 TimeToFire.Inline입니다. 이렇게 하면 트리거 이벤트 직후에 규칙이 실행됩니다.

### <a name="to-register-the-rule"></a>규칙을 등록하려면

- 도메인 모델에서 에서 반환하는 형식 목록에 규칙 `GetCustomDomainModelTypes` 클래스를 추가합니다.

    ```csharp
    public partial class ExampleDomainModel
     {
       protected override Type[] GetCustomDomainModelTypes()
       {
         List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
         types.Add(typeof(MyAddRule));
         // If you add more rules, list them here.
         return types.ToArray();
       }
     }

    ```

- 도메인 모델 클래스의 이름을 잘 모르는 경우 **Dsl\GeneratedCode\DomainModel.cs 파일 내부를 확인합니다.**

- DSL 프로젝트의 사용자 지정 코드 파일에 이 코드를 작성합니다.

### <a name="to-write-the-code-of-the-rule"></a>규칙의 코드를 작성하려면

- 다음 기본 클래스 중 하나에서 규칙 클래스를 파생합니다.

  | 기본 클래스 | 트리거 |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | 요소, 링크 또는 셰이프가 추가됩니다.<br /><br /> 이를 사용하여 새 요소 외에 새 관계를 검색할 수 있습니다. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | 도메인 속성 값이 변경됩니다. 메서드 인수는 이전 값과 새 값을 제공합니다.<br /><br /> 셰이프의 경우 기본 제공 속성이 변경될 때 셰이프가 이동되면 이 규칙이 `AbsoluteBounds` 트리거됩니다.<br /><br /> 대부분의 경우 재정의 `OnValueChanged` 하거나 속성 처리기에서 더 편리 `OnValueChanging` 합니다. 이러한 메서드는 변경 전후에 즉시 호출됩니다. 반면 규칙은 일반적으로 트랜잭션이 끝날 때 실행됩니다. 자세한 내용은 [도메인 속성 값 변경 처리기 를 참조하세요.](../modeling/domain-property-value-change-handlers.md) **참고:**  이 규칙은 링크를 만들거나 삭제할 때 트리거되지 않습니다. 대신 `AddRule` 도메인 관계에 대한 및 를 `DeleteRule` 작성합니다. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | 요소 또는 링크가 삭제될 때 트리거됩니다. ModelElement.IsDeleting 속성은 트랜잭션이 끝날 때까지 true입니다. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | 요소 또는 링크가 삭제되었을 때 수행됩니다. 규칙은 DeletingRules를 비롯한 다른 모든 규칙이 실행된 후에 실행됩니다. ModelElement.IsDeleting은 false이고 ModelElement.IsDeleted는 true입니다. 후속 실행 취소를 허용하기 위해 요소는 실제로 메모리에서 제거되지 않지만 Store.ElementDirectory에서 제거됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | 요소가 한 저장소 파티션에서 다른 저장소 파티션으로 이동됩니다.<br /><br /> (이는 도형의 그래픽 위치와 관련이 없습니다.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | 이 규칙은 도메인 관계에만 적용됩니다. 링크의 양쪽 끝에 모델 요소를 명시적으로 할당하면 트리거됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | 링크의 MoveBefore 또는 MoveToIndex 메서드를 사용하여 요소 간 링크 순서가 변경될 때 트리거됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | 트랜잭션을 만들 때 실행됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | 트랜잭션이 커밋되려고 할 때 실행됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | 트랜잭션이 롤백되려고 할 때 실행됩니다. |

- 각 클래스에는 재정의하는 메서드가 있습니다. `override`클래스를 입력하여 검색합니다. 이 메서드의 매개 변수는 변경 중인 요소를 식별합니다.

  규칙에 대한 다음 사항을 알아차리세요.

1. 트랜잭션의 변경 집합은 많은 규칙을 트리거할 수 있습니다. 일반적으로 규칙은 가장 외부 트랜잭션이 커밋될 때 실행됩니다. 지정되지 않은 순서로 실행됩니다.

2. 규칙은 항상 트랜잭션 내에서 실행됩니다. 따라서 변경할 새 트랜잭션을 만들 필요가 없습니다.

3. 트랜잭션이 롤백되거나 실행 취소 또는 다시 실행 작업이 수행될 때 규칙이 실행되지 않습니다. 이러한 작업은 Store의 모든 콘텐츠를 이전 상태로 다시 설정합니다. 따라서 규칙이 Store 외부의 상태를 변경하는 경우 Store 콘텐츠와 동기적으로 유지되지 않을 수 있습니다. Store 외부에서 상태를 업데이트하려면 이벤트를 사용하는 것이 좋습니다. 자세한 내용은 [이벤트 처리기 모델 외부에서 변경 내용 전파를 참조하세요.](../modeling/event-handlers-propagate-changes-outside-the-model.md)

4. 일부 규칙은 모델이 파일에서 로드될 때 실행됩니다. 로드 또는 저장이 진행 중인지 확인하려면 를 `store.TransactionManager.CurrentTransaction.IsSerializing` 사용합니다.

5. 규칙 코드에서 더 많은 규칙 트리거를 만드는 경우 실행 목록의 끝에 추가되고 트랜잭션이 완료되기 전에 실행됩니다. DeletedRules는 다른 모든 규칙 후에 실행됩니다. 한 규칙은 트랜잭션에서 각 변경에 대해 한 번씩 여러 번 실행할 수 있습니다.

6. 규칙과 정보를 전달하려면 에 정보를 저장할 수 `TransactionContext` 있습니다. 이 사전은 트랜잭션 중에 유지 관리되는 사전일 뿐입니다. 트랜잭션이 종료되면 삭제됩니다. 각 규칙의 이벤트 인수는 액세스 권한을 제공합니다. 규칙은 예측 가능한 순서로 실행되지 않습니다.

7. 다른 대안을 고려한 후 규칙을 사용합니다. 예를 들어 값이 변경되면 속성을 업데이트하려면 계산된 속성을 사용하는 것이 좋습니다. 셰이프의 크기나 위치를 제한 하려면를 사용 `BoundsRule` 합니다. 속성 값의 변경 내용에 응답 하려면 `OnValueChanged` 속성에 처리기를 추가 합니다. 자세한 내용은 [변경 내용에 대 한 응답 및 전파](../modeling/responding-to-and-propagating-changes.md)를 참조 하세요.

## <a name="example"></a>예제
 다음 예에서는 두 요소를 연결 하기 위해 도메인 관계가 인스턴스화될 때 속성을 업데이트 합니다. 규칙은 사용자가 다이어그램에서 링크를 만들 때 뿐만 아니라 프로그램 코드에서 링크를 만들 때에도 트리거됩니다.

 이 예를 테스트 하려면 작업 흐름 솔루션 템플릿을 사용 하 여 DSL을 만들고 Dsl 프로젝트의 파일에 다음 코드를 삽입 합니다. 솔루션을 빌드 및 실행 하 고 디버깅 프로젝트에서 샘플 파일을 엽니다. 주석 모양과 흐름 요소 사이에 주석 링크를 그립니다. 주석의 텍스트는 연결한 최근 요소에 대 한 보고서로 변경 됩니다.

 실제로 모든 AddRule에 대 한 DeleteRule를 작성 합니다.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.TaskRuleExample
{

  [RuleOn(typeof(CommentReferencesSubjects))]
  public class RoleRule : AddRule
  {

    public override void ElementAdded(ElementAddedEventArgs e)
    {
      base.ElementAdded(e);
      CommentReferencesSubjects link = e.ModelElement as CommentReferencesSubjects;
      Comment comment = link.Comment;
      FlowElement subject = link.Subject;
      Transaction current = link.Store.TransactionManager.CurrentTransaction;
      // Don't want to run when we're just loading from file:
      if (current.IsSerializing) return;
      comment.Text = "Flow has " + subject.FlowTo.Count + " outgoing connections";
    }

  }

  public partial class TaskRuleExampleDomainModel
  {
    protected override Type[] GetCustomDomainModelTypes()
    {
      List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
      types.Add(typeof(RoleRule));
      return types.ToArray();
    }
  }

}
```

## <a name="see-also"></a>참조

- [이벤트 처리기로 모델 외부의 변경 내용 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)