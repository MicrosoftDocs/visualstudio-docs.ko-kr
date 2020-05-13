---
title: 래핑, 들여쓰기 및 리팩터링 정렬
description: 메서드 호출의 체인을 래핑하고 맞추는 방법에 대해 알아봅니다.
ms.date: 03/10/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jillfra
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: d801f052cb02e6a5b53189eeae342b9015d30f9b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "79093881"
---
# <a name="wrap-indent-and-align-refactorings"></a>래핑, 들여쓰기 및 리팩터링 정렬

## <a name="wrap-and-align-call-chains"></a>호출 체인 래핑 및 맞춤

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 메서드 호출의 체인을 래핑 및 맞출 수 있습니다.

**시기:** 하나의 문에 여러 메서드 호출로 구성된 긴 체인이 있습니다.

**이유:** 사용자 기본 설정에 따라 래핑하거나 들여쓰기할 때 긴 목록을 읽기가 더 쉽습니다.

### <a name="how-to"></a>방법

1. 호출 체인에 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
3. 리팩터링을 수락하려면 **호출 체인 래핑** 또는 **호출 체인 래핑 및 맞춤**을 선택합니다.

   ![호출 체인 래핑 및 맞춤](media/wrap-call-chain.png)

## <a name="wrap-indent-and-align-parameters-or-arguments"></a>매개 변수 또는 인수 래핑, 들여쓰기 및 정렬

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 매개 변수 또는 인수를 래핑, 들여쓰기 및 정렬할 수 있습니다.

**시기:** 여러 개의 매개 변수 또는 인수가 있는 메서드 선언 또는 호출이 있습니다.

**이유:** 사용자 기본 설정에 따라 래핑하거나 들여쓰기할 때 긴 매개 변수 또는 인수의 목록을 읽는 것이 더 쉽습니다.

### <a name="how-to"></a>방법

1. 매개 변수 목록에 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.

   ![래핑, 들여쓰기 및 매개 변수 정렬](media/wrap-parameters.png)

3. 리팩터링을 수락하려면 **모든 매개 변수 래핑**을 선택합니다.

## <a name="wrap-binary-expressions"></a>이진 식 래핑

이 리팩터링은 다음에 적용됩니다.

- C#

- Visual Basic

**내용:** 이진 식을 래핑할 수 있습니다.

**시기:** 이진 식이 있습니다.

**이유:** 사용자 기본 설정으로 래핑되는 경우 이진 식을 더 쉽게 읽을 수 있습니다.

### <a name="how-to"></a>방법

1. 이진 식에 커서를 놓습니다.
2. 줄의 임의 위치에서 **Ctrl**+ **.** 를 눌러 **빠른 작업 및 리팩터링** 메뉴를 트리거합니다.
3. 리팩터링을 수락하려면 **식 래핑**을 선택합니다.

   ![호출 체인 래핑 및 맞춤](media/wrap-binary-expression.png)

## <a name="see-also"></a>참조

- [리팩터링](../refactoring-in-visual-studio.md)
