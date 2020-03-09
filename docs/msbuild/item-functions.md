---
title: Item 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, Item functions
ms.assetid: 5e6df3cc-2db8-4cbd-8fdd-3ffd03ac0876
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: af4fb872206611ea5eb1aa93b7aa759615b56e41
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633683"
---
# <a name="item-functions"></a>항목 함수

작업 및 대상의 코드는 프로젝트의 항목에 대한 정보를 얻기 위해 항목 함수를 호출할 수 있습니다(MSBuild 4.0 이상). 이러한 함수를 사용하면 고유 항목을 간편하게 가져올 수 있으며 항목을 반복하는 방식보다 속도도 더 빠릅니다.

## <a name="string-item-functions"></a>문자열 항목 함수

.NET Framework에서 문자열 메서드 및 속성을 사용하여 모든 항목 값을 작동할 수 있습니다. <xref:System.String> 메서드의 경우 메서드 이름을 지정합니다. <xref:System.String> 속성의 경우 "get_" 뒤에 속성 이름을 지정합니다.

여러 문자열에 있는 항목의 경우 문자열 메서드 또는 속성이 각 문자열에서 실행됩니다.

다음 예제에서는 이러한 문자열 항목 함수를 사용하는 방법을 보여 줍니다.

```xml
<ItemGroup>
    <theItem Include="andromeda;tadpole;cartwheel" />
</ItemGroup>

<Target Name = "go">
    <Message Text="IndexOf  @(theItem->IndexOf('r'))" />
    <Message Text="Replace  @(theItem->Replace('tadpole', 'pinwheel'))" />
    <Message Text="Length   @(theItem->get_Length())" />
    <Message Text="Chars    @(theItem->get_Chars(2))" />
</Target>

  <!--
  Output:
    IndexOf  3;-1;2
    Replace  andromeda;pinwheel;cartwheel
    Length   9;7;9
    Chars    d;d;r
  -->
```

## <a name="intrinsic-item-functions"></a>내장 항목 함수

아래 표는 항목에 사용할 수 있는 내장 함수를 나열합니다.

|기능|예제|설명|
|--------------|-------------|-----------------|
|`Count`|`@(MyItem->Count())`|항목 수를 반환합니다.|
|`DirectoryName`|`@(MyItem->DirectoryName())`|각 항목에 대한 해당 `Path.DirectoryName`을 반환합니다.|
|`Distinct`|`@(MyItem->Distinct())`|고유한 `Include` 값이 있는 항목을 반환합니다. 메타데이터는 무시됩니다. 비교 시 대/소문자가 구분되지 않습니다.|
|`DistinctWithCase`|`@(MyItem->DistinctWithCase())`|고유한 `itemspec` 값이 있는 항목을 반환합니다. 메타데이터는 무시됩니다. 대/소문자를 구분하고 비교합니다.|
|`Reverse`|`@(MyItem->Reverse())`|항목을 역순으로 반환합니다.|
|`AnyHaveMetadataValue`|`@(MyItem->AnyHaveMetadataValue("MetadataName", "MetadataValue"))`|모든 항목에 지정된 메타데이터 이름 및 값이 있는지 여부를 나타내도록 `boolean`을 반환합니다. 비교 시 대/소문자가 구분되지 않습니다.|
|`ClearMetadata`|`@(MyItem->ClearMetadata())`|해당 메타데이터가 지워진 항목을 반환합니다. `itemspec`만 유지됩니다.|
|`HasMetadata`|`@(MyItem->HasMetadata("MetadataName"))`|지정된 메타데이터 이름을 가진 항목을 반환합니다. 비교 시 대/소문자가 구분되지 않습니다.|
|`Metadata`|`@(MyItem->Metadata("MetadataName"))`|메타데이터 이름을 포함하는 메타데이터의 값을 반환합니다.|
|`WithMetadataValue`|`@(MyItem->WithMetadataValue("MetadataName", "MetadataValue"))`|지정된 메타데이터 이름 및 값을 가진 항목을 반환합니다. 비교 시 대/소문자가 구분되지 않습니다.|

다음 예제에서는 내장 항목 함수를 사용하는 방법을 보여 줍니다.

```xml
<ItemGroup>
    <TheItem Include="first">
        <Plant>geranium</Plant>
    </TheItem>
    <TheItem Include="second">
        <Plant>algae</Plant>
    </TheItem>
    <TheItem Include="third">
        <Plant>geranium</Plant>
    </TheItem>
</ItemGroup>

<Target Name="go">
    <Message Text="MetaData:    @(TheItem->Metadata('Plant'))" />
    <Message Text="HasMetadata: @(theItem->HasMetadata('Plant'))" />
    <Message Text="WithMetadataValue: @(TheItem->WithMetadataValue('Plant', 'geranium'))" />
    <Message Text=" " />
    <Message Text="Count:   @(theItem->Count())" />
    <Message Text="Reverse: @(theItem->Reverse())" />
</Target>

  <!--
  Output:
    MetaData:    geranium;algae;geranium
    HasMetadata: first;second;third
    WithMetadataValue: first;third

    Count:   3
    Reverse: third;second;first
  -->
```

## <a name="see-also"></a>참조

- [항목](../msbuild/msbuild-items.md)
