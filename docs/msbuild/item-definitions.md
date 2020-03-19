---
title: 항목 정의 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, item definitions
ms.assetid: 8e3dc223-f9e5-4974-aa0e-5dc7967419cb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 18d6a2a30af4fb29a8d9e924c44c1570ff1efe29
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77633709"
---
# <a name="item-definitions"></a>항목 정의

MSBuild 2.0에서는 [ItemGroup](../msbuild/itemgroup-element-msbuild.md) 요소를 사용하여 프로젝트 파일에서 항목의 정적 선언을 수행할 수 있습니다. 그러나 메타데이터는 모든 항목에 대해 동일하더라도 항목 수준에만 추가할 수 있습니다. MSBuild 3.5부터 [ItemDefinitionGroup](../msbuild/itemdefinitiongroup-element-msbuild.md)이라는 프로젝트 요소가 이 제한 사항을 해결합니다. *ItemDefinitionGroup*을 사용하면 명명된 항목 형식의 모든 항목에 기본 메타데이터 값을 추가하는 항목 정의 집합을 정의할 수 있습니다.

*ItemDefinitionGroup* 요소는 프로젝트 파일의 [Project](../msbuild/project-element-msbuild.md) 요소 바로 뒤에 표시됩니다. 항목 정의는 다음과 같은 기능을 제공합니다.

- 대상 외부에 있는 항목에 대한 전역 기본 메타데이터를 정의할 수 있습니다. 즉, 동일한 메타데이터가 지정된 형식의 모든 항목에 적용됩니다.

- 항목 형식은 여러 정의를 포함할 수 있습니다. 추가 메타데이터 사양이 형식에 추가되면 마지막 사양이 우선적으로 적용됩니다. \(메타데이터는 속성이 따르는 동일한 가져오기 순서를 따릅니다.\)

- 메타데이터는 가산될 수 있습니다. 예를 들어 CDefines 값은 설정되는 속성에 따라 조건부로 누적됩니다. 예: `MT;STD_CALL;DEBUG;UNICODE`.

- 메타데이터는 제거될 수 있습니다.

- 메타데이터의 포함 여부를 제어하는 데 조건을 사용할 수 있습니다.

## <a name="item-metadata-default-values"></a>항목 메타데이터 기본값

ItemDefinitionGroup에 정의된 항목 메타데이터는 기본 메타데이터의 선언일 뿐입니다. 이 메타데이터는 ItemGroup을 사용하여 메타데이터 값을 포함하는 Item을 정의해야만 적용됩니다.

> [!NOTE]
> 이 항목에 나오는 대부분의 예제에서는 ItemDefinitionGroup 요소는 표시되지만 해당 ItemGroup 정의는 간결성을 위해 생략되어 있습니다.

ItemGroup에 명시적으로 정의된 메타데이터는 ItemDefinitionGroup의 메타데이터보다 우선합니다. ItemDefinitionGroup의 메타데이터는 ItemGroup의 정의되지 않은 메타데이터에만 적용됩니다. 예를 들어:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemGroup>
    <i Include="a">
        <o>o1</o>
        <n>n2</n>
    </i>
</ItemGroup>
```

이 예제에서 기본 메타데이터 "m"은 Item "i"로 명시적으로 정의되지 않으므로 Item "i"에 적용됩니다. 그러나 기본 메타데이터 "n"은 Item "i"로 이미 정의되어 있으므로 Item "i"에 적용되지 않습니다.

> [!NOTE]
> XML 요소 및 매개 변수 이름은 대소문자를 구분합니다. 항목 메타데이터 및 ITEM\/속성 이름은 대소문자를 구분하지 않습니다. 따라서 이름에서 대/소문자만 다른 ItemDefinitionGroup 항목은 같은 ItemGroup으로 취급해야 합니다.

## <a name="value-sources"></a>값 원본

ItemDefinitionGroup에 정의된 메타데이터 값은 다음과 같은 다양한 소스에서 가져올 수 있습니다.

- PropertyGroup 속성

- ItemDefinitionGroup의 항목

- ItemDefinitionGroup 항목의 항목 변환

- 환경 변수

- *MSBuild.exe* 명령줄의 전역 속성

- 예약된 속성

- ItemDefinitionGroup의 항목에서 잘 알려진 메타데이터

- CDATA 섹션 \<\!\[CDATA\[여기에 있는 내용은 구문 분석되지 않음\]\]\>

> [!NOTE]
> ItemGroup의 항목 메타데이터는 ItemDefinitionGroup 요소가 ItemGroup 요소보다 먼저 처리되므로 ItemDefinitionGroup 메타데이터 선언에서 사용 가능하지 않습니다.

## <a name="additive-and-multiple-definitions"></a>가산 및 다중 정의

정의를 추가하거나 여러 ItemDefinitionGroup을 사용할 때는 다음 사항에 유의하세요.

- 추가 메타데이터 사양은 형식에 추가됩니다.

- 마지막 사양이 우선적으로 적용됩니다.

여러 ItemDefinitionGroup이 있는 경우 각 후속 사양은 해당 메타데이터를 이전 정의에 추가합니다. 예를 들어:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <n>n1</n>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <o>o1</o>
    </i>
</ItemDefinitionGroup>
```

이 예제에서는 "o" 메타데이터는 "m"와 "n"에 추가됩니다.

또한 이전에 정의된 메타데이터 값을 추가할 수도 있습니다. 예를 들어:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

이 예제에서는 메타데이터 "m"에 대해 이전에 정의된 값 \(m1\)이 새 값 \(m2\)에 추가되므로 최종 값은 "m1;m2"가 됩니다.

> [!NOTE]
> 이 작업은 동일한 ItemDefinitionGroup에서도 발생할 수 있습니다.

이전에 정의된 메타데이터를 재정의하면 마지막 사양이 우선적으로 적용됩니다. 다음 예제에서 메타데이터 "m"의 최종 값은 "m1"에서 "m1a"로 이동합니다.

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m>m1a</m>
    </i>
</ItemDefinitionGroup>
```

## <a name="use-conditions-in-an-itemdefinitiongroup"></a>ItemDefinitionGroup에서 조건 사용

ItemDefinitionGroup에서 조건을 사용하여 메타데이터의 포함 여부를 제어할 수 있습니다. 예를 들어:

```xml
<ItemDefinitionGroup Condition="'$(Configuration)'=='Debug'">
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
```

이 경우에 "Configuration" 속성의 값이 "Debug"인 경우에만 항목 "i"의 기본 메타데이터 "m1"이 포함됩니다.

> [!NOTE]
> 로컬 메타데이터 참조만 조건에서 지원됩니다.

이전 ItemDefinitionGroup에 정의된 메타데이터에 대한 참조는 정의 그룹이 아닌 항목에 로컬입니다. 즉, 참조의 범위는 항목별로 고유합니다. 예를 들어:

```xml
<ItemDefinitionGroup>
    <test>
        <yes>1</yes>
    </test>
    <i>
        <m>m0</m>
        <m Condition="'%(test.yes)'=='1'">m1</m>
    </i>
</ItemDefinitionGroup>

```

위 예제에서 항목 "i"는 해당 Condition의 항목 "test"를 참조합니다. MSBuild는 ItemDefinitionGroup의 다른 항목 메타데이터에 대한 참조를 빈 문자열로 해석하기 때문에 이 Condition은 절대 true가 되지 않습니다. 따라서 "m"은 "m0"로 설정됩니다.

```xml
  <ItemDefinitionGroup>
    <i>
      <m>m0</m>
      <yes>1</yes>
      <m Condition="'%(i.yes)'=='1'">m1</m>
    </i>
  </ItemDefinitionGroup>

```

위 예제에서 Condition은 항목 "yes"에 대한 항목 "i"의 메타데이터 값을 참조하므로 값 "m1"으로 설정됩니다.

## <a name="override-and-delete-metadata"></a>메타데이터 재정의 및 삭제

ItemDefinitionGroup 요소에 정의된 메타데이터는 메타데이터 값을 다른 값으로 설정하여 나중에 ItemDefinitionGroup 요소에서 재정의할 수 있습니다. 또한 빈 값으로 설정하면 메타데이터 항목을 효과적으로 삭제할 수 있습니다. 예를 들어:

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
    </i>
</ItemDefinitionGroup>
<ItemDefinitionGroup>
    <i>
        <m></m>
    </i>
</ItemDefinitionGroup>
```

항목 "i"에는 여전히 메타데이터 "m"이 포함되지만 해당 값은 이제 비어 있습니다.

## <a name="scope-of-metadata"></a>메타데이터의 범위

ItemDefinitionGroup의 정의된 전역 속성에는 해당 항목이 정의되는 전역 범위가 지정됩니다. ItemDefinitionGroup의 기본 메타데이터 정의는 자체 참조될 수 있습니다. 예를 들어 다음에서는 간단한 메타데이터 참조를 사용합니다.

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(m);m2</m>
    </i>
</ItemDefinitionGroup>
```

정규화된 메타데이터 참조를 사용할 수도 있습니다.

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>%(i.m);m2</m>
    </i>
</ItemDefinitionGroup>
```

그러나 다음은 유효하지 않습니다.

```xml
<ItemDefinitionGroup>
    <i>
        <m>m1</m>
        <m>@(x)</m>
    </i>
</ItemDefinitionGroup>
```

MSBuild 3.5부터는 ItemGroups 또한 자체 참조될 수 있습니다. 예를 들어:

```xml
<ItemGroup>
    <item Include="a">
        <m>m1</m>
        <m>%(m);m2</m>
    </item>
</ItemGroup>
```

## <a name="see-also"></a>참조

- [일괄 처리](../msbuild/msbuild-batching.md)
