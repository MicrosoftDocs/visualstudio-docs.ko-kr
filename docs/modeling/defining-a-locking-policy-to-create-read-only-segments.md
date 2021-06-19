---
title: 잠금 정책을 정의하여 읽기 전용 세그먼트 만들기
description: 프로그램에서 DSL(도메인 특정 언어) 모델의 일부 또는 전체를 잠그는 정책을 정의하여 읽을 수는 있지만 변경할 수는 없도록 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 6bb8e05ffc030716f32ab7e79233ca9e02ef2e11
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385788"
---
# <a name="defining-a-locking-policy-to-create-read-only-segments"></a>잠금 정책을 정의하여 읽기 전용 세그먼트 만들기
Visual Studio 시각화 및 모델링 SDK의 불변성 API를 사용하면 프로그램이 DSL(도메인 특정 언어) 모델의 일부 또는 전체를 잠글 수 있으므로 읽을 수 있지만 변경할 수는 없습니다. 예를 들어 이 읽기 전용 옵션을 사용하면 사용자가 동료에게 DSL 모델에 주석을 추가 및 검토하도록 요청할 수 있지만 원래 모델을 변경하지 못하도록 할 수 있습니다.

 또한 DSL의 작성자로서 잠금 정책을 정의할 수 *있습니다.* 잠금 정책은 허용되는 잠금, 허용되지 않는 잠금 또는 필수 잠금을 정의합니다. 예를 들어 DSL을 게시할 때 타사 개발자가 새 명령을 사용하여 확장하도록 권장할 수 있습니다. 그러나 잠금 정책을 사용하여 모델에서 지정된 부분의 읽기 전용 상태를 변경하지 못하도록 할 수도 있습니다.

> [!NOTE]
> 리플렉션을 사용하여 잠금 정책을 우회할 수 있습니다. 타사 개발자에게 명확한 경계를 제공하지만 강력한 보안을 제공하지는 않습니다.

 자세한 내용 및 샘플은 Visual Studio [시각화 및 모델링 SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db) 웹 사이트에서 확인할 수 있습니다.

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="setting-and-getting-locks"></a>잠금 설정 및 받기
 저장소, 파티션 또는 개별 요소에 대한 잠금을 설정할 수 있습니다. 예를 들어 이 문은 모델 요소가 삭제되는 것을 방지하고 해당 속성이 변경되지 않도록 합니다.

```csharp
using Microsoft.VisualStudio.Modeling.Immutability; ...
element.SetLocks(Locks.Delete | Locks.Property);
```

 다른 잠금 값을 사용하여 관계 변경, 요소 생성, 파티션 간 이동 및 역할의 링크 순서 다시 정렬을 방지할 수 있습니다.

 잠금은 사용자 작업 및 프로그램 코드에 모두 적용됩니다. 프로그램 코드가 변경하려고 하면 이 `InvalidOperationException` throw됩니다. 실행 취소 또는 다시 실행 작업에서는 잠금이 무시됩니다.

 를 사용하여 지정된 집합에서 요소에 잠금이 있는지 여부를 `IsLocked(Locks)` 검색하고 를 사용하여 요소에 대한 현재 잠금 집합을 가져올 수 `GetLocks()` 있습니다.

 트랜잭션을 사용하지 않고 잠금을 설정할 수 있습니다. 잠금 데이터베이스가 저장소의 일부가 아닙니다. 저장소의 값 변경에 대한 응답으로 잠금을 설정하는 경우(예: OnValueChanged에서) 실행 취소 작업의 일부인 변경 내용을 허용해야 합니다.

 이러한 메서드는 네임스페이스에 정의된 확장 <xref:Microsoft.VisualStudio.Modeling.Immutability> 메서드입니다.

### <a name="locks-on-partitions-and-stores"></a>파티션 및 저장소에 대한 잠금
 파티션 및 저장소에도 잠금을 적용할 수 있습니다. 파티션에 설정된 잠금은 파티션의 모든 요소에 적용됩니다. 따라서 예를 들어 다음 문은 자체 잠금 상태에 관계없이 파티션의 모든 요소가 삭제되지 않도록 방지합니다. 그럼에도 불구하고 와 같은 다른 잠금은 `Locks.Property` 개별 요소에 대해 여전히 설정될 수 있습니다.

```csharp
partition.SetLocks(Locks.Delete);
```

 Store에 설정된 잠금은 파티션 및 요소에 대한 잠금 설정에 관계없이 모든 요소에 적용됩니다.

### <a name="using-locks"></a>잠금 사용
 잠금을 사용하여 다음 예제와 같은 체계를 구현할 수 있습니다.

- 주석을 나타내는 요소를 제외한 모든 요소 및 관계에 대한 변경은 허용되지 않습니다. 이렇게 하면 사용자가 모델을 변경하지 않고도 주석을 출품할 수 있습니다.

- 기본 파티션의 변경을 허용하지 않지만 다이어그램 파티션의 변경은 허용합니다. 사용자는 다이어그램을 다시 정렬할 수 있지만 기본 모델을 변경할 수는 없습니다.

- 별도의 데이터베이스에 등록된 사용자 그룹을 제외하고 Store에 대한 변경은 허용되지 않습니다. 다른 사용자의 경우 다이어그램과 모델은 읽기 전용입니다.

- 다이어그램의 부울 속성이 true로 설정된 경우 모델 변경을 허용되지 않습니다. 해당 속성을 변경하는 메뉴 명령을 제공합니다. 이렇게 하면 사용자가 실수로 변경하지 않도록 할 수 있습니다.

- 특정 클래스의 요소 및 관계 추가 및 삭제를 허용하지 않지만 속성 변경은 허용합니다. 이렇게 하면 사용자가 속성을 채울 수 있는 고정된 양식이 제공됩니다.

## <a name="lock-values"></a>잠금 값
 저장소, 파티션 또는 개별 ModelElement에서 잠금을 설정할 수 있습니다. 잠금은 `Flags` 열거형입니다. '&#124;'을 사용하여 값을 결합할 수 있습니다.

- ModelElement의 잠금은 항상 해당 파티션의 잠금을 포함합니다.

- 파티션의 잠금에는 항상 저장소 잠금이 포함됩니다.

  파티션 또는 저장소에 대한 잠금을 설정할 수 없으며, 동시에 개별 요소에 대한 잠금을 사용하지 않도록 설정할 수 없습니다.

|값|가 `IsLocked(Value)` true이면 의미|
|-|-|
|없음|제한이 없습니다.|
|속성|요소의 도메인 속성은 변경할 수 없습니다. 관계에서 도메인 클래스의 역할에 의해 생성되는 속성에는 적용되지 않습니다.|
|추가|파티션이나 저장소에는 새 요소와 링크를 만들 수 없습니다.<br /><br /> 은 에 적용되지 `ModelElement` 않습니다.|
|이동|가 true이거나 가 true이면 요소를 파티션 간에 이동할 수 `element.IsLocked(Move)` `targetPartition.IsLocked(Move)` 없습니다.|
|DELETE|이 잠금이 요소 자체 또는 포함된 요소 및 셰이프와 같이 삭제가 전파되는 요소에 설정되어 있으면 요소를 삭제할 수 없습니다.<br /><br /> 를 사용하여 `element.CanDelete()` 요소를 삭제할 수 있는지 여부를 검색할 수 있습니다.|
|순서|역할 재생자에서 링크의 순서를 변경할 수 없습니다.|
|RolePlayer|이 요소에서 소스가 되는 링크 집합을 변경할 수 없습니다. 예를 들어 새 요소는 이 요소 아래에 포함할 수 없습니다. 이 요소가 대상인 링크에는 영향을 주지 않습니다.<br /><br /> 이 요소가 링크인 경우 해당 소스 및 대상은 영향을 받지 않습니다.|
|모두|다른 값의 비트 OR입니다.|

## <a name="locking-policies"></a>잠금 정책
 DSL의 작성자로서 *잠금 정책* 를 정의할 수 있습니다. 잠금 정책은 SetLocks() 작업을 조정하여 특정 잠금이 설정되지 않도록 방지하거나 특정 잠금을 설정하도록 위임할 수 있습니다. 일반적으로 잠금 정책을 사용하여 변수를 선언할 수 있는 것과 동일한 방식으로 사용자 또는 개발자가 의도한 DSL 사용을 실수로 위반하지 않도록 할 수 `private` 있습니다.

 잠금 정책을 사용하여 요소의 형식에 종속된 모든 요소에 대한 잠금을 설정할 수도 있습니다. 이는 `SetLocks(Locks.None)` 요소가 파일에서 처음 만들어지거나 deserialized 될 때 가 항상 호출하기 때문입니다.

 그러나 정책을 사용하여 수명 동안 요소에 대한 잠금을 변경할 수는 없습니다. 이러한 효과를 얻으려면 호출을 사용해야 `SetLocks()` 합니다.

 잠금 정책을 정의하려면 다음을 수행해야 합니다.

- <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy>를 구현하는 클래스를 만듭니다.

- DSL의 DocData를 통해 사용할 수 있는 서비스에 이 클래스를 추가합니다.

### <a name="to-define-a-locking-policy"></a>잠금 정책을 정의하려면
 <xref:Microsoft.VisualStudio.Modeling.Immutability.ILockingPolicy> 에는 다음 정의가 있습니다.

```csharp
public interface ILockingPolicy
{
  Locks RefineLocks(ModelElement element, Locks proposedLocks);
  Locks RefineLocks(Partition partition, Locks proposedLocks);
  Locks RefineLocks(Store store, Locks proposedLocks);
}
```

 이러한 메서드는 `SetLocks()` Store, Partition 또는 ModelElement에서 를 호출할 때 호출됩니다. 각 메서드에서 제안된 잠금 집합이 제공됩니다. 제안된 집합을 반환하거나 잠금을 추가하고 뺄 수 있습니다.

 예를 들면 다음과 같습니다.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  public class MyLockingPolicy : ILockingPolicy
  {
    /// <summary>
    /// Moderate SetLocks(this ModelElement target, Locks locks)
    /// </summary>
    /// <param name="element">target</param>
    /// <param name="proposedLocks">locks</param>
    /// <returns></returns>
    public Locks RefineLocks(ModelElement element, Locks proposedLocks)
    {
      // In my policy, users can never delete an element,
      // and other developers cannot easily change that:
      return proposedLocks | Locks.Delete);
    }
    public Locks RefineLocks(Store store, Locks proposedLocks)
    {
      // Only one user can change this model:
      return Environment.UserName == "aUser"
           ? proposedLocks : Locks.All;
    }
```

 다른 코드가 를 호출하는 경우에도 사용자가 항상 요소를 삭제할 수 있도록 하려면 `SetLocks(Lock.Delete):`

 `return proposedLocks & (Locks.All ^ Locks.Delete);`

 MyClass의 모든 요소에 대한 모든 속성 변경을 허용되지 않는 경우:

 `return element is MyClass ? (proposedLocks | Locks.Property) : proposedLocks;`

### <a name="to-make-your-policy-available-as-a-service"></a>정책을 서비스로 사용할 수 있도록 하려면
 프로젝트에서 `DslPackage` 다음 예제와 유사한 코드가 포함된 새 파일을 추가합니다.

```csharp
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Immutability;
namespace Company.YourDsl.DslPackage // Change
{
  // Override the DocData GetService() for this DSL.
  internal partial class YourDslDocData // Change
  {
    /// <summary>
    /// Custom locking policy cache.
    /// </summary>
    private ILockingPolicy myLockingPolicy = null;

    /// <summary>
    /// Called when a service is requested.
    /// </summary>
    /// <param name="serviceType">Service requested</param>
    /// <returns>Service implementation</returns>
    public override object GetService(System.Type serviceType)
    {
      if (serviceType == typeof(SLockingPolicy)
       || serviceType == typeof(ILockingPolicy))
      {
        if (myLockingPolicy == null)
        {
          myLockingPolicy = new MyLockingPolicy();
        }
        return myLockingPolicy;
      }
      // Request is for some other service.
      return base.GetService(serviceType);
    }
}
```
