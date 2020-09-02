---
title: UML 모델에서 요소 및 관계 만들기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML API
ms.assetid: cae81d32-8cc7-4f7c-9f00-20119952bc51
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5ea066aa31cbc1f6408ee55c92a5ca761608f534
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667819"
---
# <a name="create-elements-and-relationships-in-uml-models"></a>UML 모델에서 요소 및 관계 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 확장에 대한 프로그램 코드에서 요소 및 관계를 만들고 삭제할 수 있습니다.

## <a name="create-a-model-element"></a>모델 요소 만들기

### <a name="namespace-imports"></a>네임스페이스 가져오기
 다음 `using` 문을 포함해야 합니다.

 만들기 메서드는 이 네임스페이스에서 확장 메서드로 정의됩니다.

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

### <a name="obtain-the-owner-of-the-element-you-want-to-create"></a>만들려는 요소의 소유자를 가져옵니다.
 모델은 단일 트리를 구성하므로 모든 항목에는 모델 루트를 제외한 하나의 소유자가 포함됩니다. 모델 루트는 `IModel` 형식인 `IPackage` 형식입니다.

 사용자의 현재 다이어그램과 같은 특정 다이어그램에 표시될 요소를 만들고 있으면 대개 해당 다이어그램에 연결된 패키지에서 요소를 만들어야 합니다. 예를 들면 다음과 같습니다.

```
IPackage linkedPackage = Context.CurrentDiagram.Element as IPackage;
```

 이 표에서는 일반적인 모델 요소의 소유권을 간략히 설명합니다.

|만들 요소|소유자|
|---------------------------|-----------|
|`IActor, IUseCase, IComponent, IClass, IInterface, IEnumeration`<br /><br /> `IActivity, IInteraction`|`IPackage, IModel`|
|`IAttribute, IOperation`|`IClass, IInterface`|
|`IPart, IPort`|`IComponent`|
|`IAction, IObjectNode`|`IActivity`|
|`ILifeline, IMessage, ICombinedFragment`|`IInteraction`|

### <a name="invoke-the-create-method-on-the-owner"></a>소유자에 대해 Create 메서드 호출
 메서드 이름의 형식은 `Create` *OwnedType* `()` 입니다. 예를 들면 다음과 같습니다.

```
IUseCase usecase1 = linkedPackage.CreateUseCase();
```

 시퀀스 다이어그램과 같은 일부 형식에는 더 복잡한 만들기 메서드가 포함됩니다. [UML API를 사용 하 여 uml 시퀀스 다이어그램 편집](../modeling/edit-uml-sequence-diagrams-by-using-the-uml-api.md)을 참조 하세요.

 몇 가지 요소 형식의 경우 `SetOwner(newOwner)`를 사용하여 수명 중에 요소의 소유자를 변경할 수 있습니다.

### <a name="set-the-name-and-other-properties"></a>이름 및 기타 속성 설정

```
usecase1.Name = "user logs in";
```

### <a name="example"></a>예

```
using Microsoft.VisualStudio.Uml.Classes;
using Microsoft.VisualStudio.Uml.Extensions;
...
 void InstantiateObserverPattern (IPackage package, string namePrefix)
 {    IInterface observer = package.CreateInterface();
      observer.Name = namePrefix + "Observer";
      IOperation operation = observer.CreateOperation();
      operation.Name = "Update";
      IClass subject = package.CreateClass();
      subject.Name = namePrefix + "Subject"; ...
```

## <a name="create-an-association"></a>연결 만들기

#### <a name="to-create-an-association"></a>연결을 만들려면

1. 대개 관계의 소스 끝이 포함된 패키지 또는 모델인 연결의 소유자를 가져옵니다.

2. 소유자에 대해 필요한 Create 메서드를 호출합니다.

3. 이름과 같은 관계의 속성을 설정합니다.

     예를 들면 다음과 같습니다.

    ```
    IAssociation association = subject.Package.CreateAssociation(subject, observer);
    association .Name = "Observes";
    ```

4. 관계의 각 끝에 대한 속성을 설정합니다. 항상 `MemberEnds` 두 개가 있습니다. 예를 들면 다음과 같습니다.

    ```
    association .MemberEnds[0].Name = "subject";   // role name
    association .MemberEnds[1].Name = "observers"; // role name
    association .MemberEnds[1].SetBounds("0..*");
                // multiplicity defaults to "1"
    association.MemberEnds[0].Aggregation = AggregationKind.Composite;
    ```

## <a name="create-a-generalization"></a>일반화 만들기

```
IGeneralization generalization =
  subclass.CreateGeneralization(superClass);
```

## <a name="delete-an-element-relationship-or-generalization-from-the-model"></a>모델에서 요소, 관계 또는 일반화 삭제

```
anElement.Delete();
```

 모델에서 요소를 삭제할 경우:

- 연결된 모든 관계도 삭제됩니다.

- 다이어그램에서 요소를 나타낸 모든 모양도 삭제됩니다.

## <a name="see-also"></a>관련 항목
 [Uml 모델 및 다이어그램 확장](../modeling/extend-uml-models-and-diagrams.md) [다이어그램에 uml 모델 표시](../modeling/display-a-uml-model-on-diagrams.md)
