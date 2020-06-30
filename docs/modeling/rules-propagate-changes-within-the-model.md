---
title: 규칙으로 모델 내부의 변경 내용 전파
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, rules
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2050fe0ea2d1a9bb0bf278c13c2beb587412c643
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85542560"
---
# <a name="rules-propagate-changes-within-the-model"></a>규칙으로 모델 내부의 변경 내용 전파
시각화 및 모델링 SDK (VMSDK)에서 한 요소에서 다른 요소로 변경 내용을 전파 하는 저장소 규칙을 만들 수 있습니다. 저장소의 요소가 변경 되 면 일반적으로 가장 바깥쪽 트랜잭션이 커밋될 때 규칙이 실행 되도록 예약 됩니다. 요소를 추가 하거나 삭제 하는 등의 다양 한 종류의 이벤트에 대해 다양 한 유형의 규칙이 있습니다. 특정 형식의 요소, 모양 또는 다이어그램에 규칙을 추가할 수 있습니다. 규칙으로 정의 된 많은 기본 제공 기능입니다. 예를 들어 규칙은 모델이 변경 될 때 다이어그램이 업데이트 되도록 합니다. 사용자 고유의 규칙을 추가 하 여 도메인별 언어를 사용자 지정할 수 있습니다.

 저장소 규칙은 저장소 내에서 변경 내용 (모델 요소, 관계, 모양, 연결선 및 해당 도메인 속성의 변경 내용)을 전파 하는 데 특히 유용 합니다. 사용자가 실행 취소 또는 다시 실행 명령을 호출할 때 규칙이 실행 되지 않습니다. 대신 트랜잭션 관리자가 저장소 콘텐츠가 올바른 상태로 복원 되었는지 확인할 수 있습니다. 저장소 외부의 리소스에 변경 내용을 전파 하려면 저장소 이벤트를 사용 합니다. 자세한 내용은 [이벤트 처리기가 모델 외부에서 변경 내용을 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)하는 방법을 참조 하세요.

 예를 들어 사용자 (또는 코드)가 ExampleDomainClass 형식의 새 요소를 만들 때마다 다른 형식의 추가 요소가 모델의 다른 부분에 생성 되도록 지정 하려고 한다고 가정 합니다. AddRule을 작성 하 고 ExampleDomainClass에 연결할 수 있습니다. 규칙에서 코드를 작성 하 여 추가 요소를 만듭니다.

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
> 규칙의 코드는 저장소 내의 요소에 대 한 상태만 변경 해야 합니다. 즉, 규칙은 모델 요소, 관계, 모양, 연결선, 다이어그램 또는 해당 속성만 변경 해야 합니다. 저장소 외부의 리소스에 변경 내용을 전파 하려면 저장소 이벤트를 정의 합니다. 자세한 내용은 [이벤트 처리기가 모델 외부에서 변경 내용을 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)하는 방법을 참조 하세요.

### <a name="to-define-a-rule"></a>규칙을 정의 하려면

1. 규칙을 특성 접두사가 접두사로 지정 된 클래스로 정의 합니다 `RuleOn` . 특성은 규칙을 도메인 클래스, 관계 또는 다이어그램 요소 중 하 나와 연결 합니다. 이 규칙은 추상 일 수 있는이 클래스의 모든 인스턴스에 적용 됩니다.

2. 규칙을 `GetCustomDomainModelTypes()` 도메인 모델 클래스의에서 반환 된 집합에 추가 하 여 등록 합니다.

3. 추상 규칙 클래스 중 하나에서 규칙 클래스를 파생 시키고 실행 메서드의 코드를 작성 합니다.

   다음 섹션에서는 이러한 단계를 좀 더 자세히 설명합니다.

### <a name="to-define-a-rule-on-a-domain-class"></a>도메인 클래스에 대 한 규칙을 정의 하려면

- 사용자 지정 코드 파일에서 클래스를 정의 하 고 특성을 사용 하 여 접두사를 지정 합니다 <xref:Microsoft.VisualStudio.Modeling.RuleOnAttribute> .

    ```csharp
    [RuleOn(typeof(ExampleElement),
         // Usual value - but required, because it is not the default:
         FireTime = TimeToFire.TopLevelCommit)]
    class MyRule ...

    ```

- 첫 번째 매개 변수의 주체 형식은 도메인 클래스, 도메인 관계, 셰이프, 연결선 또는 다이어그램 일 수 있습니다. 일반적으로 도메인 클래스 및 관계에 규칙을 적용 합니다.

     는 `FireTime` 일반적으로 `TopLevelCommit` 입니다. 이렇게 하면 트랜잭션의 모든 기본 변경 내용이 적용 된 후에만 규칙이 실행 됩니다. 대체 방법은 변경 후 즉시 규칙을 실행 하는 인라인입니다. 현재 트랜잭션의 끝에서 규칙을 실행 하는 LocalCommit (가장 바깥쪽이 아닐 수도 있음). 또한 큐의 순서에 영향을 주는 규칙의 우선 순위를 설정할 수 있지만이는 필요한 결과를 얻을 수 있는 신뢰할 수 없는 방법입니다.

- 추상 클래스를 주체 형식으로 지정할 수 있습니다.

- 규칙은 subject 클래스의 모든 인스턴스에 적용 됩니다.

- 의 기본값은 `FireTime` TimeToFire. TopLevelCommit입니다. 이렇게 하면 가장 바깥쪽 트랜잭션이 커밋될 때 규칙이 실행 됩니다. 대안은 TimeToFire입니다. 이렇게 하면 트리거 이벤트 후에 규칙이 즉시 실행 됩니다.

### <a name="to-register-the-rule"></a>규칙을 등록 하려면

- 도메인 모델에서에서 반환 하는 형식 목록에 규칙 클래스를 추가 합니다 `GetCustomDomainModelTypes` .

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

- 도메인 모델 클래스의 이름을 잘 모르는 경우에는 파일 ( **Dsl\generatedcode\domainmodel.cs** )을 찾습니다.

- DSL 프로젝트의 사용자 지정 코드 파일에이 코드를 작성 합니다.

### <a name="to-write-the-code-of-the-rule"></a>규칙의 코드를 작성 하려면

- 다음 기본 클래스 중 하나에서 규칙 클래스를 파생 시킵니다.

  | 기본 클래스 | 트리거 |
  |-|-|
  | <xref:Microsoft.VisualStudio.Modeling.AddRule> | 요소, 링크 또는 모양이 추가 됩니다.<br /><br /> 새 요소 외에 새 관계를 검색 하는 데 사용 합니다. |
  | <xref:Microsoft.VisualStudio.Modeling.ChangeRule> | 도메인 속성 값이 변경 되었습니다. 메서드 인수는 이전 값과 새 값을 제공 합니다.<br /><br /> 모양의 경우이 규칙은 기본 제공 `AbsoluteBounds` 속성이 변경 될 때 (도형이 이동 된 경우) 트리거됩니다.<br /><br /> 대부분의 경우 `OnValueChanged` 속성 처리기에서 또는를 재정의 하는 것이 더 편리 `OnValueChanging` 합니다. 이러한 메서드는 변경 전후에 즉시 호출 됩니다. 이와 대조적으로 규칙은 일반적으로 트랜잭션이 끝날 때 실행 됩니다. 자세한 내용은 [도메인 속성 값 변경 처리기](../modeling/domain-property-value-change-handlers.md)를 참조 하세요. **참고:**  이 규칙은 링크가 만들어지거나 삭제 될 때 트리거되지 않습니다. 대신 `AddRule` `DeleteRule` 도메인 관계에 대 한 및을 (를) 작성 합니다. |
  | <xref:Microsoft.VisualStudio.Modeling.DeletingRule> | 요소 또는 링크를 삭제 하려고 할 때 트리거됩니다. ModelElement 속성은 트랜잭션이 끝날 때까지 true입니다. |
  | <xref:Microsoft.VisualStudio.Modeling.DeleteRule> | 요소 또는 링크가 삭제 된 경우 수행 됩니다. 규칙은 DeletingRules를 포함 하 여 다른 모든 규칙이 실행 된 후에 실행 됩니다. ModelElement가 false이 고 ModelElement가 true입니다. 후속 실행 취소를 허용 하기 위해 요소는 실제로 메모리에서 제거 되지 않지만,이 요소는 저장소. ElementDirectory에서 제거 됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.MoveRule> | 한 저장소 파티션에서 다른 저장소 파티션으로 요소가 이동 합니다.<br /><br /> (도형의 그래픽 위치와는 관련이 없습니다.) |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerChangeRule> | 이 규칙은 도메인 관계에만 적용 됩니다. 모델 요소를 링크의 끝에 명시적으로 할당 하는 경우 트리거됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.RolePlayerPositionChangeRule> | 링크에서 MoveBefore 또는 MoveToIndex 메서드를 사용 하 여 요소에 대 한 링크의 순서가 변경 될 때 트리거됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionBeginningRule> | 트랜잭션이 만들어질 때 실행 됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionCommittingRule> | 트랜잭션이 커밋될 때 실행 됩니다. |
  | <xref:Microsoft.VisualStudio.Modeling.TransactionRollingBackRule> | 트랜잭션이 롤백될 때 실행 됩니다. |

- 각 클래스에는 재정의 하는 메서드가 있습니다. 클래스를 입력 `override` 하 여 검색 합니다. 이 메서드의 매개 변수는 변경 되는 요소를 식별 합니다.

  규칙에 대 한 다음 사항에 유의 하세요.

1. 트랜잭션의 변경 내용 집합은 많은 규칙을 트리거할 수 있습니다. 일반적으로 규칙은 가장 바깥쪽 트랜잭션이 커밋될 때 실행 됩니다. 이는 지정 되지 않은 순서로 실행 됩니다.

2. 규칙은 항상 트랜잭션 내에서 실행 됩니다. 따라서 변경 하기 위해 새 트랜잭션을 만들 필요는 없습니다.

3. 트랜잭션은 트랜잭션을 롤백하거나 실행 취소 또는 다시 실행 작업을 수행할 때 실행 되지 않습니다. 이러한 작업은 저장소의 모든 콘텐츠를 이전 상태로 다시 설정 합니다. 따라서 규칙이 스토어 외부에서 모든 항목의 상태를 변경 하는 경우 스토어 콘텐츠와 synchronism 되지 않을 수 있습니다. 저장소 외부의 상태를 업데이트 하려면 이벤트를 사용 하는 것이 좋습니다. 자세한 내용은 [이벤트 처리기가 모델 외부에서 변경 내용을 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)하는 방법을 참조 하세요.

4. 일부 규칙은 파일에서 모델을 로드할 때 실행 됩니다. 로드 또는 저장이 진행 중인지 여부를 확인 하려면를 사용 `store.TransactionManager.CurrentTransaction.IsSerializing` 합니다.

5. 규칙의 코드에서 더 많은 규칙 트리거를 만드는 경우 실행 목록의 끝에 추가 되 고 트랜잭션이 완료 되기 전에 실행 됩니다. DeletedRules는 다른 모든 규칙 다음에 실행 됩니다. 한 규칙은 트랜잭션에서 여러 번 실행 될 수 있으며 각 변경에 대해 한 번만 실행 될 수 있습니다.

6. 규칙에 정보를 전달 하기 위해에 정보를 저장할 수 있습니다 `TransactionContext` . 이는 트랜잭션 중에 유지 관리 되는 사전입니다. 트랜잭션이 종료 될 때 삭제 됩니다. 각 규칙의 이벤트 인수는이에 대 한 액세스를 제공 합니다. 규칙은 예측 가능한 순서로 실행 되지 않습니다.

7. 다른 대안을 고려한 후 규칙을 사용 합니다. 예를 들어 값이 변경 될 때 속성을 업데이트 하려면 계산 된 속성을 사용 하는 것이 좋습니다. 셰이프의 크기나 위치를 제한 하려면를 사용 `BoundsRule` 합니다. 속성 값의 변경 내용에 응답 하려면 `OnValueChanged` 속성에 처리기를 추가 합니다. 자세한 내용은 [변경 내용에 대 한 응답 및 전파](../modeling/responding-to-and-propagating-changes.md)를 참조 하세요.

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

## <a name="see-also"></a>참고 항목

- [이벤트 처리기로 모델 외부의 변경 내용 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)