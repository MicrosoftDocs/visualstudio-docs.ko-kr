---
title: '방법: MSBuild의 이스케이프 특수 문자 | Microsoft Docs'
description: MSBuild 프로젝트 파일에서 특수 문자를 리터럴로 사용할 수 있도록 특수 문자를 이스케이프하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- special characters, escaping
- characters, escapes
- escape characters
- MSBuild, escaping special characters
ms.assetid: 1aa3669c-1647-4960-b770-752e2532102f
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 923c517653c42dd0362b398c420c99454ccf4034
ms.sourcegitcommit: c4927ef8fe239005d7feff6c5a7707c594a7a05c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2020
ms.locfileid: "92436411"
---
# <a name="how-to-escape-special-characters-in-msbuild"></a>방법: MSBuild의 이스케이프 특수 문자

MSBuild 프로젝트 파일에서 특정 문자는 특수한 의미로 사용됩니다. 이러한 문자의 예로는 세미콜론(`;`) 및 별표(`*`)를 들 수 있습니다. 이러한 특수 문자의 전체 목록을 보려면 [MSBuild 특수 문자](../msbuild/msbuild-special-characters.md)를 참조하세요.

프로젝트 파일에서 이러한 특수 문자를 리터럴로 사용하려면 `%<xx>` 구문을 사용하여 해당 문자를 지정해야 합니다. 여기서 `<xx>`는 문자의 ASCII 16진수 값을 나타냅니다.

## <a name="msbuild-special-characters"></a>MSBuild 특수 문자

항목 목록의 `Include` 특성에서 특수 문자가 사용되는 하나의 예가 있습니다. 예를 들어 다음 항목 목록은 두 개의 항목, *MyFile.cs* 및 *MyClass.cs* 를 선언합니다.

```xml
<Compile Include="MyFile.cs;MyClass.cs"/>
```

이름에 세미콜론이 포함된 항목을 선언하려면 `%<xx>` 구문을 사용하여 세미콜론을 이스케이프하고 MSBuild가 두 개의 개별 항목을 선언하지 않게 해야 합니다. 예를 들어 다음 항목은 세미콜론을 이스케이프하고 `MyFile.cs;MyClass.cs`라는 하나의 항목을 선언합니다.

```xml
<Compile Include="MyFile.cs%3BMyClass.cs"/>
```

[속성 함수](../msbuild/property-functions.md)를 사용하여 문자열을 이스케이프할 수도 있습니다. 예를 들어 다음은 위 예제와 같습니다.

```xml
<Compile Include="$([MSBuild]::Escape('MyFile.cs;MyClass.cs'))" />
```

### <a name="to-use-an-msbuild-special-character-as-a-literal-character"></a>MSBuild 특수 문자를 리터럴 문자로 사용하려면

특수 문자 대신 `%<xx>` 표기법을 사용할 수 있습니다. 여기서 `<xx>`는 ASCII 문자의 16진수 값을 나타냅니다. 예를 들어 별표(`*`)를 리터럴 문자로 사용하려면 `%2A` 값을 사용합니다.

## <a name="see-also"></a>참조
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [항목](../msbuild/msbuild-items.md)
