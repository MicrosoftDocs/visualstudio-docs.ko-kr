---
title: 프로그램 코드에서 모델 탐색 및 업데이트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
ms.assetid: 1427ae91-be8a-4ce7-85df-00038faa2cbb
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cb7c99e345b676576d51c97799cdc7b35f8279ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668514"
---
# <a name="navigating-and-updating-a-model-in-program-code"></a>프로그램 코드에서 모델 탐색 및 업데이트
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모델 요소를 만들고 삭제 하 고, 해당 속성을 설정 하 고, 요소 간의 링크를 만들고 삭제 하는 코드를 작성할 수 있습니다. 모든 변경 작업은 트랜잭션 내에서 수행 해야 합니다. 요소가 다이어그램에서 표시 되는 경우 다이어그램은 트랜잭션이 끝날 때 자동으로 "고정" 됩니다.

## <a name="in-this-topic"></a>항목 내용
 [DSL 정의 예](#example)

 [모델 탐색](#navigation)

 [클래스 정보 액세스](#metadata)

 [트랜잭션 내에서 변경 수행](#transaction)

 [모델 요소 만들기](#elements)

 [관계 링크 만들기](#links)

 [요소 삭제](#deleteelements)

 [관계 링크 삭제](#deletelinks)

 [관계의 링크 다시 정렬](#reorder)

 [잠금](#locks)

 [복사 및 붙여넣기](#copy)

 [다이어그램 탐색 및 업데이트](#diagrams)

 [모양 및 요소 간 이동](#views)

 [셰이프 및 연결선의 속성](#shapeProperties)

 [DocView 및 Docview](#docdata)

 도형, 연결선 및 다이어그램과 모델 요소에 대 한 관계는 별도의 항목에서 설명 합니다. 자세한 내용은 [방법: 다이어그램 탐색 및 업데이트](../misc/how-to-navigate-and-update-a-diagram.md)를 참조 하세요.

## <a name="an-example-dsl-definition"></a><a name="example"></a> DSL 정의 예
 다음은이 항목의 예제에 대 한 자세한 설명입니다. dsl의 주요 부분입니다.

 ![DSL 정의 다이어그램 &#45; 패밀리 트리 모델](../modeling/media/familyt-person.png "FamilyT_Person")

 이 모델은이 DSL의 인스턴스입니다.

 ![Tudor 패밀리 트리 모델](../modeling/media/tudor-familytreemodel.png "Tudor_FamilyTreeModel")

### <a name="references-and-namespaces"></a>참조 및 네임 스페이스
 이 항목의 코드를 실행 하려면 다음을 참조 해야 합니다.

 `Microsoft.VisualStudio.Modeling.Sdk.11.0.dll`

 코드에서이 네임 스페이스를 사용 합니다.

 `using Microsoft.VisualStudio.Modeling;`

 또한 DSL이 정의 된 것과 다른 프로젝트에서 코드를 작성 하는 경우에는 Dsl 프로젝트에서 빌드된 어셈블리를 가져와야 합니다.

## <a name="navigating-the-model"></a><a name="navigation"></a> 모델 탐색

### <a name="properties"></a>속성
 DSL 정의에서 정의 하는 도메인 속성은 프로그램 코드에서 액세스할 수 있는 속성이 됩니다.

 `Person henry = ...;`

 `if (henry.BirthDate < 1500) ...`

 `if (henry.Name.EndsWith("VIII")) ...`

 속성을 설정 하려면 [트랜잭션](#transaction)내에서이를 수행 해야 합니다.

 `henry.Name = "Henry VIII";`

 DSL 정의에서 속성의 **종류가** **계산**된 경우이를 설정할 수 없습니다. 자세한 내용은 [계산 된 저장소 속성 및 사용자 지정 저장소 속성](../modeling/calculated-and-custom-storage-properties.md)을 참조 하세요.

### <a name="relationships"></a>관계
 DSL 정의에서 정의 하는 도메인 관계는 관계의 각 끝에 있는 클래스에서 하나씩의 속성 쌍이 됩니다. 속성의 이름은 각 관계의 양쪽에서 역할에 대 한 레이블로 DslDefinition 다이어그램에 표시 됩니다. 역할의 복합성에 따라 속성의 형식은 관계의 다른 쪽 end에 있는 클래스 이거나 해당 클래스의 컬렉션입니다.

 `foreach (Person child in henry.Children) { ... }`

 `FamilyTreeModel ftree = henry.FamilyTreeModel;`

 관계의 반대쪽 끝에 있는 속성은 항상 역입니다. 링크를 만들거나 삭제 하면 두 요소의 역할 속성이 모두 업데이트 됩니다. `System.Linq`예제의 ParentsHaveChildren 관계에 대 한 다음 식은 항상 true입니다.

 `(Person p) => p.Children.All(child => child.Parents.Contains(p))`

 `&& p.Parents.All(parent => parent.Children.Contains(p));`

 **Elementlinks**. 관계는 도메인 관계 형식의 인스턴스인 *링크*라는 모델 요소로도 표현 됩니다. 링크에는 항상 하나의 소스 요소와 하나의 대상 요소가 있습니다. 소스 요소와 대상 요소는 동일할 수 있습니다.

 링크 및 해당 속성에 액세스할 수 있습니다.

 `ParentsHaveChildren link = ParentsHaveChildren.GetLink(henry, edward);`

 `// This is now true:`

 `link == null || link.Parent == henry && link.Child == edward`

 기본적으로 하나 이상의 관계 인스턴스에서 모델 요소 쌍을 연결할 수 있습니다. 그러나 DSL 정의에서 `Allow Duplicates` 관계에 대 한 플래그가 true 이면 둘 이상의 링크가 있을 수 있으며 다음을 사용 해야 합니다 `GetLinks` .

 `foreach (ParentsHaveChildren link in ParentsHaveChildren.GetLinks(henry, edward)) { ... }`

 또한 링크에 액세스 하는 다른 방법도 있습니다. 예를 들면 다음과 같습니다.

 `foreach (ParentsHaveChildren link in     ParentsHaveChildren.GetLinksToChildren(henry)) { ... }`

 **숨겨진 역할.** DSL 정의에서 특정 역할에 대해 **생성** 된 속성이 **false** 인 경우 해당 역할에 해당 하는 속성이 생성 되지 않습니다. 그러나 관계의 메서드를 사용 하 여 여전히 링크에 액세스 하 고 링크를 이동할 수 있습니다.

 `foreach (Person p in ParentsHaveChildren.GetChildren(henry)) { ... }`

 가장 자주 사용 되는 예제는 <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> 모델 요소를 다이어그램에 표시 하는 모양에 연결 하는 관계입니다.

 `PresentationViewsSubject.GetPresentation(henry)[0] as PersonShape`

### <a name="the-element-directory"></a>요소 디렉터리
 요소 디렉터리를 사용 하 여 저장소의 모든 요소에 액세스할 수 있습니다.

 `store.ElementDirectory.AllElements`

 다음과 같은 요소를 찾는 방법도 있습니다.

 `store.ElementDirectory.FindElements(Person.DomainClassId);`

 `store.ElementDirectory.GetElement(elementId);`

## <a name="accessing-class-information"></a><a name="metadata"></a> 클래스 정보 액세스
 DSL 정의의 클래스, 관계 및 기타 요소에 대 한 정보를 가져올 수 있습니다. 예를 들면 다음과 같습니다.

 `DomainClassInfo personClass = henry.GetDomainClass();`

 `DomainPropertyInfo birthProperty =`

 `personClass.FindDomainProperty("BirthDate")`

 `DomainRelationshipInfo relationship =`

 `link.GetDomainRelationship();`

 `DomainRoleInfo sourceRole = relationship.DomainRole[0];`

 모델 요소의 상위 클래스는 다음과 같습니다.

- ModelElement-모든 요소 및 관계는 ModelElements입니다.

- ElementLink-모든 관계가 Elementlink입니다.

## <a name="perform-changes-inside-a-transaction"></a><a name="transaction"></a> 트랜잭션 내에서 변경 수행
 프로그램 코드가 스토어에서 모든 항목을 변경할 때마다 트랜잭션 내에서이 작업을 수행 해야 합니다. 이는 모든 모델 요소, 관계, 모양, 다이어그램 및 해당 속성에 적용 됩니다. 자세한 내용은 <xref:Microsoft.VisualStudio.Modeling.Transaction>를 참조하세요.

 트랜잭션을 관리 하는 가장 편리한 방법은 문에 포함 된 문을 사용 하는 것입니다 `using` `try...catch` .

```
Store store; ...
try
{
  using (Transaction transaction =
    store.TransactionManager.BeginTransaction("update model"))
    // Outermost transaction must always have a name.
  {
    // Make several changes in Store:
    Person p = new Person(store);
    p.FamilyTreeModel = familyTree;
    p.Name = "Edward VI";
    // end of changes to Store

    transaction.Commit(); // Don't forget this!
  } // transaction disposed here
}
catch (Exception ex)
{
  // If an exception occurs, the Store will be
  // rolled back to its previous state.
}
```

 한 트랜잭션 내에서 원하는 수의 변경 작업을 수행할 수 있습니다. 활성 트랜잭션 내에서 새 트랜잭션을 열 수 있습니다.

 변경 내용을 영구적으로 적용 하려면 `Commit` 트랜잭션이 삭제 되기 전에 수행 해야 합니다. 트랜잭션 내에서 catch 되지 않는 예외가 발생 하면 저장소는 변경 전 상태로 다시 설정 됩니다.

## <a name="creating-model-elements"></a><a name="elements"></a> 모델 요소 만들기
 다음 예에서는 기존 모델에 요소를 추가 합니다.

```
FamilyTreeModel familyTree = ...; // The root of the model.
using (Transaction t =
    familyTree.Store.TransactionManager
    .BeginTransaction("update model"))
{
  // Create a new model element
  // in the same partition as the model root:
  Person edward = new Person(familyTree.Partition);
  // Set its embedding relationship:
  edward.FamilyTreeModel = familyTree;
          // same as: familyTree.People.Add(edward);
  // Set its properties:
  edward.Name = "Edward VII";
  t.Commit(); // Don't forget this!
}
```

 이 예제에서는 요소를 만드는 데 필요한 다음과 같은 사항에 대해 설명 합니다.

- 저장소의 특정 파티션에 새 요소를 만듭니다. 모델 요소 및 관계의 경우 셰이프는 아니지만 일반적으로 기본 파티션입니다.

- 포함 관계의 대상으로 만듭니다. 이 예제의 DslDefinition에서 각 사용자는 포함 관계 FamilyTreeHasPeople의 대상 이어야 합니다. 이를 위해 Person 개체의 FamilyTreeModel role 속성을 설정 하거나 FamilyTreeModel 개체의 Person role 속성에 Person을 추가할 수 있습니다.

- 새 요소의 속성, 특히 `IsName` DslDefinition에서가 true 인 속성을 설정 합니다. 이 플래그는 해당 소유자 내에서 요소를 고유 하 게 식별 하는 데 사용 되는 속성을 표시 합니다. 이 경우 Name 속성에는 해당 플래그가 있습니다.

- 이 DSL의 DSL 정의가 저장소에 로드 되어 있어야 합니다. 메뉴 명령과 같은 확장을 작성 하는 경우 일반적으로이는 이미 true입니다. 다른 경우에는 모델을 저장소에 명시적으로 로드 하거나 [ModelBus](/previous-versions/ee904639(v=vs.140)) 를 사용 하 여 로드할 수 있습니다. 자세한 내용은 [방법: 프로그램 코드에서 파일을 통해 모델 열기](../modeling/how-to-open-a-model-from-file-in-program-code.md)를 참조 하세요.

  이러한 방식으로 요소를 만들면 셰이프가 자동으로 만들어집니다 (DSL에 다이어그램이 있는 경우). 기본 셰이프, 색 및 기타 기능을 사용 하 여 자동으로 할당 된 위치에 표시 됩니다. 연결 된 셰이프가 표시 되는 위치 및 방법을 제어 하려면 [요소 및 해당 모양 만들기](#merge)를 참조 하세요.

## <a name="creating-relationship-links"></a><a name="links"></a> 관계 링크 만들기
 예제 DSL 정의에는 두 가지 관계가 정의 되어 있습니다. 각 관계는 관계의 각 끝에 있는 클래스의 *역할 속성* 을 정의 합니다.

 관계의 인스턴스를 만들 수 있는 방법에는 세 가지가 있습니다. 이러한 세 가지 메서드는 모두 동일한 결과를 가집니다.

- 원본 역할 수행자의 속성을 설정 합니다. 예를 들면 다음과 같습니다.

  - `familyTree.People.Add(edward);`

  - `edward.Parents.Add(henry);`

- 대상 역할 수행자의 속성을 설정 합니다. 예를 들면 다음과 같습니다.

  - `edward.familyTreeModel = familyTree;`

       이 역할의 복합성은 이므로 `1..1` 값을 할당 합니다.

  - `henry.Children.Add(edward);`

       이 역할의 복합성은 이므로 `0..*` 컬렉션에를 추가 합니다.

- 관계의 인스턴스를 명시적으로 생성 합니다. 예를 들면 다음과 같습니다.

  - `FamilyTreeHasPeople edwardLink = new FamilyTreeHasPeople(familyTreeModel, edward);`

  - `ParentsHaveChildren edwardHenryLink = new ParentsHaveChildren(henry, edward);`

  마지막 메서드는 관계 자체에 대 한 속성을 설정 하려는 경우에 유용 합니다.

  이러한 방식으로 요소를 만들면 다이어그램의 커넥터가 자동으로 만들어지지만 기본 셰이프, 색 및 기타 기능이 포함 됩니다. 연결 된 커넥터를 만드는 방법을 제어 하려면 [요소 및 해당 모양 만들기](#merge)를 참조 하세요.

## <a name="deleting-elements"></a><a name="deleteelements"></a> 요소 삭제
 다음을 호출 하 여 요소를 삭제 합니다 `Delete()` .

 `henry.Delete();`

 이 작업도 삭제 합니다.

- 요소와의 관계 링크입니다. 예를 `edward.Parents` 들어에는 더 이상이 포함 되지 않습니다 `henry` .

- 플래그가 true 인 역할의 요소 `PropagatesDelete` 입니다. 예를 들어 요소를 표시 하는 셰이프는 삭제 됩니다.

  기본적으로 모든 포함 관계는 `PropagatesDelete` 대상 역할에 적용 됩니다. 을 삭제 `henry` 해도는 삭제 되지 `familyTree` 않지만 `familyTree.Delete()` 모든를 삭제 합니다 `Persons` . 자세한 내용은 [삭제 동작 사용자 지정](../modeling/customizing-deletion-behavior.md)을 참조 하세요.

  기본적으로 `PropagatesDelete` 는 참조 관계의 역할에 대해 true가 아닙니다.

  개체를 삭제할 때 삭제 규칙에서 특정 전파를 생략할 수 있습니다. 이는 다른 요소에 대 한 요소를 대체 하는 경우에 유용 합니다. 삭제를 전파 하지 않아야 하는 하나 이상의 역할에 대 한 GUID를 제공 합니다. GUID는 relationship 클래스에서 가져올 수 있습니다.

  `henry.Delete(ParentsHaveChildren.SourceDomainRoleId);`

  이 특정 예제는 `PropagatesDelete` `false` 관계의 역할에 대 한 이므로 적용 되지 않습니다 `ParentsHaveChildren` .

  경우에 따라 요소 또는 전파에 의해 삭제 되는 요소에 잠금이 있으므로 삭제할 수 없습니다. `element.CanDelete()`를 사용 하 여 요소를 삭제할 수 있는지 여부를 확인할 수 있습니다.

## <a name="deleting-relationship-links"></a><a name="deletelinks"></a> 관계 링크 삭제
 역할 속성에서 요소를 제거 하 여 관계 링크를 삭제할 수 있습니다.

 `henry.Children.Remove(edward); // or:`

 `edward.Parents.Remove(henry);  // or:`

 링크를 명시적으로 삭제할 수도 있습니다.

 `edwardHenryLink.Delete();`

 이 세 가지 메서드는 모두 동일한 효과를 가집니다. 그 중 하나를 사용 하기만 하면 됩니다.

 역할의 다중성이 0 ..1 또는 1 ..1 인 경우 `null` , 또는를 다른 값으로 설정할 수 있습니다.

 `edward.FamilyTreeModel = null;` 디스크나

 `edward.FamilyTreeModel = anotherFamilyTree;`

## <a name="re-ordering-the-links-of-a-relationship"></a><a name="reorder"></a> 관계의 링크 다시 정렬
 특정 모델 요소에서 원본 또는 대상으로 지정 된 특정 관계의 링크에는 특정 시퀀스가 있습니다. 추가 된 순서 대로 표시 됩니다. 예를 들어,이 문은 항상 자식을 동일한 순서로 생성 합니다.

 `foreach (Person child in henry.Children) ...`

 링크의 순서를 변경할 수 있습니다.

 `ParentsHaveChildren link = GetLink(henry,edward);`

 `ParentsHaveChildren nextLink = GetLink(henry, elizabeth);`

 `DomainRoleInfo role =`

 `link.GetDomainRelationship().DomainRoles[0];`

 `link.MoveBefore(role, nextLink);`

## <a name="locks"></a><a name="locks"></a> 중지
 잠금으로 인해 변경이 방지 될 수 있습니다. 잠금은 개별 요소, 파티션 및 저장소에 대해 설정할 수 있습니다. 이러한 수준에 변경 내용을 적용할 수 없도록 하는 잠금이 있는 경우 시도할 때 예외가 throw 될 수 있습니다. 요소를 사용 하 여 잠금을 설정할지 여부를 검색할 수 있습니다. GetLocks ()는 네임 스페이스에 정의 된 확장 메서드입니다 <xref:Microsoft.VisualStudio.Modeling.Immutability> .

 자세한 내용은 [잠금 정책을 정의 하 여 읽기 전용 세그먼트 만들기](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)를 참조 하세요.

## <a name="copy-and-paste"></a><a name="copy"></a> 복사 및 붙여넣기
 요소 또는 요소의 그룹을에 복사할 수 있습니다 <xref:System.Windows.Forms.IDataObject> .

```
Person person = personShape.ModelElement as Person;
Person adopter = adopterShape.ModelElement as Person;
IDataObject data = new DataObject();
personShape.Diagram.ElementOperations
      .Copy(data, person.Children.ToList<ModelElement>());
```

 요소는 serialize 된 요소 그룹으로 저장 됩니다.

 IDataObject의 요소를 모델에 병합할 수 있습니다.

```
using (Transaction t = targetDiagram.Store.
        TransactionManager.BeginTransaction("paste"))
{
  adopterShape.Diagram.ElementOperations.Merge(adopter, data);
}
```

 `Merge ()` 또는 중 하나를 사용할 수 있습니다 `PresentationElement` `ModelElement` . 지정 하는 경우 `PresentationElement` 대상 다이어그램의 위치를 세 번째 매개 변수로 지정할 수도 있습니다.

## <a name="navigating-and-updating-diagrams"></a><a name="diagrams"></a> 다이어그램 탐색 및 업데이트
 DSL에서 사람 또는 노래와 같은 개념을 나타내는 도메인 모델 요소는 다이어그램에 표시 되는 모양을 나타내는 shape 요소와는 별개입니다. 도메인 모델 요소는 개념의 중요 한 속성 및 관계를 저장 합니다. Shape 요소는 다이어그램에 개체 뷰의 크기, 위치 및 색, 구성 요소 파트의 레이아웃을 저장 합니다.

### <a name="presentation-elements"></a>프레젠테이션 요소
 ![기본 모양 및 요소 형식의 클래스 다이어그램](../modeling/media/dslshapesandelements.png "DSLshapesAndElements")

 DSL 정의에서 지정 하는 각 요소는 다음 표준 클래스 중 하나에서 파생 되는 클래스를 만듭니다.

|요소의 종류|기본 클래스|
|---------------------|----------------|
|도메인 클래스|<xref:Microsoft.VisualStudio.Modeling.ModelElement>|
|도메인 관계|<xref:Microsoft.VisualStudio.Modeling.ElementLink>|
|도형|<xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>|
|커넥터|<xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>|
|다이어그램|<xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>|

 다이어그램의 요소는 일반적으로 모델 요소를 나타냅니다. 일반적으로 (하지만 항상 그렇지는 않음)는 <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape> 도메인 클래스 인스턴스를 나타내고는 <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape> 도메인 관계 인스턴스를 나타냅니다. <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject>관계는 노드 또는 링크 셰이프를 나타내는 모델 요소에 연결 합니다.

 모든 노드 또는 링크 도형은 하나의 다이어그램에 속합니다. 이진 링크 셰이프는 두 노드 셰이프를 연결 합니다.

 셰이프는 두 집합에 자식 셰이프를 포함할 수 있습니다. 집합의 도형은 `NestedChildShapes` 부모의 경계 상자로 한정 됩니다. 목록에 있는 셰이프는 `RelativeChildShapes` 부모 경계 외부 또는 부분적으로 나타날 수 있습니다 (예: 레이블 또는 포트). 다이어그램에는 `RelativeChildShapes` 및이 없습니다 `Parent` .

### <a name="navigating-between-shapes-and-elements"></a><a name="views"></a> 모양 및 요소 간 이동
 도메인 모델 요소와 모양 요소는 관계를 통해 관련 됩니다 <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationViewsSubject> .

```csharp
// using Microsoft.VisualStudio.Modeling;
// using Microsoft.VisualStudio.Modeling.Diagrams;
// using System.Linq;
Person henry = ...;
PersonShape henryShape =
  PresentationViewsSubject.GetPresentation(henry)
    .FirstOrDefault() as PersonShape;
```

 동일한 관계는 다이어그램의 커넥터와 관계를 연결 합니다.

```
Descendants link = Descendants.GetLink(henry, edward);
DescendantConnector dc =
   PresentationViewsSubject.GetPresentation(link)
     .FirstOrDefault() as DescendantConnector;
// dc.FromShape == henryShape && dc.ToShape == edwardShape
```

 또한이 관계는 모델의 루트를 다이어그램에 연결 합니다.

```
FamilyTreeDiagram diagram =
   PresentationViewsSubject.GetPresentation(familyTree)
      .FirstOrDefault() as FamilyTreeDiagram;
```

 셰이프가 나타내는 모델 요소를 가져오려면 다음을 사용 합니다.

 `henryShape.ModelElement as Person`

 `diagram.ModelElement as FamilyTreeModel`

### <a name="navigating-around-the-diagram"></a>다이어그램 살펴보기
 일반적으로 다이어그램에서 도형과 연결선을 탐색 하는 것은 바람직하지 않습니다. 다이어그램의 모양에 대 한 작업을 수행 해야 하는 경우에만 셰이프와 연결선 간을 이동 하 여 모델에서 관계를 탐색 하는 것이 좋습니다. 이러한 메서드는 연결선을 각 끝의 셰이프에 연결 합니다.

 `personShape.FromRoleLinkShapes, personShape.ToRoleLinkShapes`

 `connector.FromShape, connector.ToShape`

 여러 셰이프는 합성입니다. 부모 셰이프와 하나 이상의 자식 계층으로 구성 됩니다. 다른 셰이프를 기준으로 배치 된 셰이프는 *자식 항목*이라고 합니다. 부모 셰이프가 이동 하면 자식이 함께 이동 합니다.

 *상대 자식은* 부모 셰이프의 경계 상자 외부에 나타날 수 있습니다. *중첩* 된 자식은 부모 범위 내에서 엄격 하 게 표시 됩니다.

 다이어그램의 최상위 셰이프 집합을 가져오려면 다음을 사용 합니다.

 `Diagram.NestedChildShapes`

 셰이프 및 연결선의 상위 클래스는 다음과 같습니다.

 <xref:Microsoft.VisualStudio.Modeling.ModelElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.PresentationElement>

 -- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement>

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.Diagram>

 ------- *기타 모양*

 ----- <xref:Microsoft.VisualStudio.Modeling.Diagrams.LinkShape>

 ------- <xref:Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape>

 --------- *커넥터*

### <a name="properties-of-shapes-and-connectors"></a><a name="shapeProperties"></a> 셰이프 및 연결선의 속성
 대부분의 경우에는 모양을 명시적으로 변경할 필요가 없습니다. 모델 요소를 변경한 경우 "수정" 규칙은 셰이프 및 연결선을 업데이트 합니다. 자세한 내용은 [변경 내용에 대 한 응답 및 전파](../modeling/responding-to-and-propagating-changes.md)를 참조 하세요.

 그러나 모델 요소와 무관 한 속성에서 모양을 명시적으로 변경 하는 것이 유용 합니다. 예를 들어 다음과 같은 속성을 변경할 수 있습니다.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Size%2A> -도형의 높이와 너비를 결정 합니다.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.NodeShape.Location%2A> -부모 모양 또는 다이어그램을 기준으로 하는 위치

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.StyleSet%2A> -도형 또는 연결선을 그리는 데 사용 되는 펜 및 브러시 집합

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Hide%2A> -셰이프를 보이지 않게 만듭니다.

- <xref:Microsoft.VisualStudio.Modeling.Diagrams.ShapeElement.Show%2A> -셰이프를 다음에 표시 합니다. `Hide()`

### <a name="creating-an-element-and-its-shape"></a><a name="merge"></a> 요소 및 해당 모양 만들기
 요소를 만들고 포함 관계의 트리에 링크 하면 셰이프가 자동으로 만들어지고 연결 됩니다. 이 작업은 트랜잭션의 끝에서 실행 되는 "픽스업" 규칙에 의해 수행 됩니다. 그러나 셰이프는 자동으로 할당 된 위치에 표시 되 고 셰이프, 색 및 기타 기능에는 기본값이 있습니다. 셰이프를 만드는 방법을 제어 하려면 merge 함수를 사용 하면 됩니다. 먼저 ElementGroup에 추가 하려는 요소를 추가한 다음 그룹을 다이어그램에 병합 해야 합니다.

 이 메서드는 다음과 같습니다.

- 속성을 요소 이름으로 할당 한 경우 이름을 설정 합니다.

- DSL 정의에서 지정한 모든 요소 병합 지시문을 관찰 합니다.

  이 예에서는 사용자가 다이어그램을 두 번 클릭할 때 마우스 위치에 셰이프를 만듭니다. 이 샘플에 대 한 DSL 정의에서는 `FillColor` 의 속성이 `ExampleShape` 노출 되었습니다.

```

using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
partial class MyDiagram
{
  public override void OnDoubleClick(DiagramPointEventArgs e)
  {
    base.OnDoubleClick(e);

    using (Transaction t = this.Store.TransactionManager
        .BeginTransaction("double click"))
    {
      ExampleElement element = new ExampleElement(this.Store);
      ElementGroup group = new ElementGroup(element);

      { // To use a shape of a default size and color, omit this block.
        ExampleShape shape = new ExampleShape(this.Partition);
        shape.ModelElement = element;
        shape.AbsoluteBounds = new RectangleD(0, 0, 1.5, 1.0);
        shape.FillColor = System.Drawing.Color.Azure;
        group.Add(shape);
      }

      this.ElementOperations.MergeElementGroupPrototype(
        this,
        group.CreatePrototype(),
        PointD.ToPointF(e.MousePosition));
      t.Commit();
    }
  }
}

```

 둘 이상의 셰이프를 제공 하는 경우를 사용 하 여 상대 위치를 설정 `AbsoluteBounds` 합니다.

 이 방법을 사용 하 여 커넥터의 색 및 기타 노출 된 속성을 설정할 수도 있습니다.

### <a name="use-transactions"></a>트랜잭션 사용
 셰이프, 연결선 및 다이어그램은 저장소의 하위 형식으로 <xref:Microsoft.VisualStudio.Modeling.ModelElement> 서 라이브입니다. 따라서 트랜잭션 내 에서만 변경 해야 합니다. 자세한 내용은 [방법: 트랜잭션을 사용 하 여 모델 업데이트](../modeling/how-to-use-transactions-to-update-the-model.md)를 참조 하세요.

## <a name="document-view-and-document-data"></a><a name="docdata"></a> 문서 보기 및 문서 데이터
 ![표준 다이어그램 형식의 클래스 다이어그램](../modeling/media/dsldiagramsanddocs.png "DSLDiagramsandDocs")

## <a name="store-partitions"></a>저장소 파티션
 모델을 로드 하면 함께 제공 된 다이어그램이 동시에 로드 됩니다. 일반적으로 모델은 Store. DefaultPartition에 로드 되 고 다이어그램 콘텐츠는 다른 파티션에 로드 됩니다. 일반적으로 각 파티션의 콘텐츠를 로드 하 고 별도의 파일에 저장 합니다.

## <a name="see-also"></a>관련 항목
 <xref:Microsoft.VisualStudio.Modeling.ModelElement>도메인별 언어 [에서 코드를 생성](../modeling/generating-code-from-a-domain-specific-language.md) 하는 [도메인별 언어의 유효성 검사](../modeling/validation-in-a-domain-specific-language.md) [방법: 트랜잭션을 사용 하 여 모델 업데이트](../modeling/how-to-use-transactions-to-update-the-model.md) [Visual Studio를 사용 하 여 모델 통합 Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md) [변경 내용에 대 한 응답 및 전파](../modeling/responding-to-and-propagating-changes.md)
