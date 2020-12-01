---
title: DebuggerDisplay 특성 추가
description: DebuggerDisplay 특성을 추가하여 디버거 변수 창에 개체, 속성 또는 필드가 표시되는 방식을 제어하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 05/12/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: fa6baa6e104fca2d3a3b45cac343fd1ceb086271
ms.sourcegitcommit: 935e4d9a20928b733e573b6801a6eaff0d0b1b14
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/25/2020
ms.locfileid: "95871121"
---
# <a name="add-debuggerdisplay-attribute"></a>DebuggerDisplay 특성 추가

이 코드 생성은 다음에 적용됩니다.

- C#

**내용:** [DebuggerDisplay 특성](../../debugger/using-the-debuggerdisplay-attribute.md)은 개체, 속성 또는 필드가 디버거 변수 창에 표시되는 방식을 제어합니다.

**시기:** 코드에서 프로그래밍 방식으로 디버거 안에 [속성을 고정](../../debugger/view-data-values-in-data-tips-in-the-code-editor.md#pin-properties-in-datatips)하려고 합니다.

**이유:** 속성을 고정하면 디버거에서 해당 속성을 개체의 속성 목록 맨 위로 버블링하여 개체를 신속하게 검사할 수 있습니다. 

## <a name="how-to"></a>방법

1. 형식, 대리자, 속성 또는 필드에 커서를 놓습니다. 

2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거하고 **DebuggerDisplay 특성 추가** 를 선택합니다.

    ![비교 연산자 생성](media/add-debugger-display-attribute.png)

3. DebuggerDisplay 특성은 기본 ToString()을 반환하는 auto 메서드와 함께 추가됩니다. 

## <a name="see-also"></a>참조

- [코드 생성](../code-generation-in-visual-studio.md)
- [변경 내용 미리 보기](../../ide/preview-changes.md)