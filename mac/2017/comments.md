---
title: 코드 주석 처리
description: 이 문서에서는 Mac용 Visual Studio 소스 편집기에서의 주석 사용에 대해 설명합니다.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: 0FE5E929-1846-4F48-B5E3-70990FAF9504
ms.topic: how-to
ms.openlocfilehash: 44eee75b4803b4317bb7d3cd02cb19b55f41a067
ms.sourcegitcommit: 5335a9864d5747bc917ed28d4ebeade3076b10e7
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/03/2020
ms.locfileid: "85949990"
---
# <a name="comments"></a>주석

코드로 디버깅하거나 실험하는 경우 일시적 또는 장기적으로 코드 블록을 주석으로 처리하는 것이 유용할 수 있습니다.

전체 코드 블록을 주석으로 처리하려면

* 코드를 선택하고 상황에 맞는 메뉴에서 **줄 주석 토글**을 선택합니다.

또는

* 선택한 코드에서 `cmd + /` 키 바인딩을 사용합니다.

이러한 방법을 사용하여 코드 섹션을 주석으로 처리하거나 주석 처리를 제거할 수 있습니다. C# 파일에서는 줄 주석 수준을 추가하여 실제 주석을 유지하면서 코드 영역을 주석으로 처리하거나 주석 처리를 제거할 수 있습니다.

![여러 수준의 주석](media/source-editor-image8.png)

주석은 코드를 조작할 수 있는 향후 개발자를 위해 코드를 문서화하는 데에도 유용합니다. 일반적으로 각 언어에서 다음과 같은 방식으로 추가되는 여러 줄 주석의 형태로 수행됩니다.

**C#**

```csharp
/*
 This is a multi-line
 comment in C#
*/
```

**F#**

```fsharp
(*
 This is a multi-line
  comment in F#
*)
```

## <a name="see-also"></a>참조

- [코드 주석 처리(Windows에서)](/visualstudio/ide/quickstart-editor#comment-out-code)