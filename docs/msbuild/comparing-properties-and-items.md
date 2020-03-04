---
title: 속성 및 항목 비교 | Microsoft 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, msbuild properties
ms.assetid: b9da45ae-d6a6-4399-8628-397deed31486
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6a86365ffe839b45fcd09862040fb88f0d4148bc
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634411"
---
# <a name="compare-properties-and-items"></a>속성 및 항목 비교하기

MSBuild 속성 및 항목은 둘 다 작업에 정보를 전달하고, 조건을 확인한 다음 프로젝트 파일 전체에서 참조할 수 있는 값을 저장하는 데 사용됩니다.

- 속성은 이름-값 쌍입니다. 자세한 내용은 [MSBuild 속성](../msbuild/msbuild-properties.md)을 참조하세요.

- 항목은 일반적으로 파일을 나타내는 개체입니다. 항목 개체에는 연결된 메타데이터 컬렉션이 있을 수 있습니다. 메타데이터는 이름-값 쌍입니다. 자세한 내용은 [항목](../msbuild/msbuild-items.md)을 참조하세요.

## <a name="scalars-and-vectors"></a>스칼라 및 벡터

MSBuild 속성은 문자열 값이 하나만 있는 이름-값 쌍이므로 보통 *스칼라*로 설명됩니다. MSBuild 항목 종류는 항목의 목록이므로 보통 *벡터*로 설명됩니다. 그러나 실제로 속성이 여러 값을 나타낼 수 있으며 항목 종류에는 0개 또는 1개의 항목이 있을 수 있습니다.

### <a name="target-dependency-injection"></a>대상 종속성 주입

속성에서 여러 값을 나타낼 수 있는 방법을 알아보려면 빌드할 대상의 목록에 대상을 추가하기 위한 일반적인 사용 패턴을 고려해 보세요. 이 목록은 일반적으로 대상 이름이 세미콜론으로 구분된 속성 값으로 표시됩니다.

```xml
<PropertyGroup>
    <BuildDependsOn>
        BeforeBuild;
        CoreBuild;
        AfterBuild
    </BuildDependsOn>
</PropertyGroup>
```

`BuildDependsOn` 속성은 일반적으로 대상 `DependsOnTargets` 특성의 인수로 사용되며, 해당 특성을 효과적으로 항목 목록으로 변환합니다. 대상을 추가하거나 대상 실행 순서를 변경하기 위해 이 속성을 재정의할 수 있습니다. 예를 들면 다음과 같습니다.

```xml
<PropertyGroup>
    <BuildDependsOn>
        $(BuildDependsOn);
        CustomBuild;
    </BuildDependsOn>
</PropertyGroup>
```

위의 코드는 대상 목록에 CustomBuild 대상을 추가하면서 `BuildDependsOn`에 `BeforeBuild;CoreBuild;AfterBuild;CustomBuild` 값을 제공합니다.

MSBuild 4.0부터는 대상 종속성 주입이 더 이상 사용되지 않습니다. 대신 `AfterTargets` 및 `BeforeTargets` 특성을 사용하세요. 자세한 내용은 [대상 빌드 순서](../msbuild/target-build-order.md)를 참조하세요.

### <a name="conversions-between-strings-and-item-lists"></a>문자열과 항목 목록 간의 변환

MSBuild는 필요에 따라 항목 종류 및 문자열 값 간의 변환을 수행합니다. 항목 목록이 문자열 값이 되는 방법을 알아보려면 항목 종류가 MSBuild 속성의 값으로 사용되는 경우 발생하는 상황을 고려해야 합니다.

```xml
<ItemGroup>
    <OutputDir Include="KeyFiles\;Certificates\" />
</ItemGroup>
<PropertyGroup>
    <OutputDirList>@(OutputDir)</OutputDirList>
</PropertyGroup>
```

OutputDir 항목 종류에는 "KeyFiles\\;Certificates\\" 값을 가진 `Include` 특성이 있습니다. MSBuild는 이 문자열을 두 개의 항목인 KeyFiles\ 및 Certificates\\로 구문 분석합니다. OutputDir 항목 종류가 OutputDirList 속성의 값으로 사용되면 MSBuild에서 항목 종류를 세미콜론으로 구분된 문자열 "KeyFiles\\;Certificates\\"로 변환하거나 “평면화"합니다.

## <a name="properties-and-items-in-tasks"></a>작업의 속성 및 항목

속성 및 항목은 MSBuild 작업의 입력 및 출력으로 사용됩니다. 자세한 내용은 [작업](../msbuild/msbuild-tasks.md)을 참조하세요.

속성은 특성으로 작업에 전달됩니다. 작업 내에서 MSBuild 속성은 값이 문자열 간에 변환될 수 있는 속성 형식으로 표시됩니다. 지원되는 속성 형식에는 `bool`, `char`, `DateTime`, `Decimal`, `Double`, `int`, `string` 및 <xref:System.Convert.ChangeType%2A>에서 처리할 수 있는 모든 형식이 포함되어 있습니다.

항목은 <xref:Microsoft.Build.Framework.ITaskItem> 개체로 작업에 전달됩니다. 작업 내에서 <xref:Microsoft.Build.Framework.ITaskItem.ItemSpec%2A>는 항목의 값을 나타내며 <xref:Microsoft.Build.Framework.ITaskItem.GetMetadata%2A>는 해당 메타데이터를 검색합니다.

항목 종류의 항목 목록은 `ITaskItem` 개체의 배열로 전달될 수 있습니다. .NET Framework 3.5부터는 `Remove` 특성을 사용하여 항목 목록에서 항목을 제거할 수 없습니다. 항목 목록에서 항목을 제거할 수 있으므로, 항목 종류의 항목이 0개일 수도 있습니다. 항목 목록이 작업에 전달되면 작업의 코드에서 이러한 가능성을 확인해야 합니다.

## <a name="property-and-item-evaluation-order"></a>속성 및 항목 평가 순서

빌드의 평가 단계 중 가져온 파일은 표시되는 순서대로 빌드에 통합됩니다. 속성 및 항목이 다음과 같은 순서로 세 단계로 정의됩니다.

- 속성이 표시되는 순서대로 정의되고 수정됩니다.

- 항목 정의가 표시되는 순서대로 정의되고 수정됩니다.

- 항목이 표시되는 순서대로 정의되고 수정됩니다.

빌드 실행 단계 중 대상 내에 정의된 속성 및 항목은 표시되는 순서대로 단일 단계에서 함께 평가됩니다.

그러나 이것이 다는 아닙니다. 속성, 항목 정의 또는 항목이 정의될 때 값이 계산됩니다. 식 계산기가 값을 지정하는 문자열을 확장합니다. 문자열 확장은 빌드 단계에 따라 달라집니다. 더 자세한 속성 및 항목 평가 순서는 다음과 같습니다.

- 빌드의 평가 단계 중:

  - 속성이 표시되는 순서대로 정의되고 수정됩니다. 속성 함수가 실행됩니다. $(PropertyName) 양식의 속성 값이 식 내에서 확장됩니다. 속성 값이 확장된 식으로 설정됩니다.

  - 항목 정의가 표시되는 순서대로 정의되고 수정됩니다. 속성 함수는 식 내에서 이미 확장되었습니다. 메타데이터 값은 확장된 식으로 설정됩니다.

  - 항목 종류가 표시되는 순서대로 정의되고 수정됩니다. @(ItemType) 양식의 항목 값이 확장됩니다. 항목 변환도 확장됩니다. 속성 함수 및 값은 식 내에서 이미 확장되었습니다. 항목 목록 및 메타데이터 값은 확장된 식으로 설정됩니다.

- 빌드의 실행 단계 중:

  - 대상 내에 정의된 속성 및 항목이 표시되는 순서대로 함께 평가됩니다. 속성 함수가 실행되며, 속성 값이 식 내에서 확장됩니다. 항목 값 및 항목 변환도 확장됩니다. 속성 값, 항목 종류 값 및 메타데이터 값은 확장된 식으로 설정됩니다.

### <a name="subtle-effects-of-the-evaluation-order"></a>평가 순서의 미묘한 효과

빌드의 평가 단계에서 속성 확인이 항목 확인 앞에 옵니다. 그럼에도 불구하고 속성은 항목 값에 따라 다르게 표시되는 값을 가질 수 있습니다. 다음 스크립트를 살펴보세요.

```xml
<ItemGroup>
    <KeyFile Include="KeyFile.cs">
        <Version>1.0.0.3</Version>
    </KeyFile>
</ItemGroup>
<PropertyGroup>
    <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
</PropertyGroup>
<Target Name="AfterBuild">
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

메시지 작업 실행에서 다음 메시지를 표시합니다.

```
KeyFileVersion: 1.0.0.3
```

`KeyFileVersion`의 값은 실제로 “\@(KeyFile->‘%(Version)’)” 문자열이기 때문입니다. 속성을 처음에 정의할 때 항목 및 항목 변환이 확장되지 않으므로 `KeyFileVersion` 속성에는 확장되지 않은 문자열의 값이 할당되었습니다.

빌드의 실행 단계 중 메시지 작업을 처리할 때 MSBuild에서 “\@(KeyFile->‘%(Version)’)” 문자열을 확장하여 “1.0.0.3”을 생성합니다.

속성 및 항목 그룹의 순서가 반대로 된 경우에도 동일한 오류 메시지가 표시됩니다.

두 번째 예제로, 속성 및 항목 그룹이 대상 내에 있는 경우 발생할 수 있는 상황을 고려해 보세요.

```xml
<Target Name="AfterBuild">
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

메시지 작업에서 다음 메시지를 표시합니다.

```
KeyFileVersion:
```

빌드의 실행 단계 중 대상 내에 정의된 속성 및 항목 그룹이 위에서 아래로 동시에 평가되기 때문입니다. `KeyFileVersion`이 정의될 때 `KeyFile`은 알려져 있지 않습니다. 따라서 항목 변환은 빈 문자열로 확장됩니다.

이 경우에 속성 및 항목 그룹의 순서를 반대로 해도 원본 메시지가 그대로 표시됩니다.

```xml
<Target Name="AfterBuild">
    <ItemGroup>
        <KeyFile Include="KeyFile.cs">
            <Version>1.0.0.3</Version>
        </KeyFile>
    </ItemGroup>
    <PropertyGroup>
        <KeyFileVersion>@(KeyFile->'%(Version)')</KeyFileVersion>
    </PropertyGroup>
    <Message Text="KeyFileVersion: $(KeyFileVersion)" />
</Target>
```

`KeyFileVersion`의 값이 “\@(KeyFile->‘%(Version)’)”이 아닌 “1.0.0.3”으로 설정됩니다. 메시지 작업에서 다음 메시지를 표시합니다.

```
KeyFileVersion: 1.0.0.3
```

## <a name="see-also"></a>참조

- [고급 개념](../msbuild/msbuild-advanced-concepts.md)
