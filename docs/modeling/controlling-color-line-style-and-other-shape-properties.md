---
title: 색, 선 스타일 및 기타 모양 속성 제어
description: 색 및 선 스타일과 같은 도형 속성 제어에 대한 정보를 제공합니다.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 836c77f3651b7686e9366fe75ea7922a248fd28f
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389633"
---
# <a name="controlling-color-line-style-and-other-shape-properties"></a>색, 선 스타일 및 기타 모양 속성 제어

색과 같은 일부 도형 속성은 '노출'될 수 있습니다. 즉, 속성은 도형의 도메인 속성에 연결할 수 있습니다. 다른 일부는 직접 제어해야 합니다.

## <a name="exposing-a-property"></a>속성 노출
 색과 같은 일부 도형 속성은 도메인 속성 값에 연결할 수 있습니다.

 DSL 정의에서 도형, 커넥터 또는 다이어그램 클래스를 선택합니다. 오른쪽 클릭 메뉴에서 노출된 **추가를** 선택한 다음 채우기 색과 같이 원하는 속성을 선택합니다.

 이제 도형에 프로그램 코드 또는 사용자로 설정할 수 있는 도메인 속성이 있습니다.

## <a name="dynamically-updating-an-exposed-property"></a>노출된 속성을 동적으로 업데이트
 일반적으로 노출된 속성이 다른 속성에 종속되도록 하려고 합니다. 예를 들어 특정 도메인 속성이 0보다 작은 경우 셰이프를 빨간색으로 설정할 수 있습니다. 이 종속성을 만들려면 [규칙을](../modeling/rules-propagate-changes-within-the-model.md)만듭니다. 예를 들어:

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Microsoft.VisualStudio.Modeling;
using Microsoft.VisualStudio.Modeling.Diagrams;
namespace ExampleNamespace
{
 // Attribute associates the rule with class:
 [RuleOn(typeof(CarShape), FireTime = TimeToFire.TopLevelCommit)]
 // The rule is a class derived from one of the abstract rules:
 class CarShapeAddRule : AddRule
 {
 // Override the abstract method:
 public override void ElementAdded(ElementAddedEventArgs e)
 {
 base.ElementAdded(e);
 CarShape shape = e.ModelElement as CarShape;
 Store store = shape.Store;
 // Ignore this call if we're currently loading a model:
 if (store.TransactionManager.CurrentTransaction.IsSerializing)
  return;
 Car car = shape.ModelElement as Car;
 // Code here propagates change as required - for example:
 shape.FillColor = car.Somebool ? System.Drawing.Color.Red : System.Drawing.Color.Green;
 }
}
 // The rule must be registered:
 public partial class ExampleDomainModel
 {
 protected override Type[] GetCustomDomainModelTypes()
 {
  List<Type> types = new List<Type>(base.GetCustomDomainModelTypes());
  types.Add(typeof(CarShapeAddRule));
  // If you add more rules, list them here.
  return types.ToArray();
 }
 }
}
```