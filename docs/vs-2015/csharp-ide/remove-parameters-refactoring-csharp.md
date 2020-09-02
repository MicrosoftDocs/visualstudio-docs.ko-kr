---
title: '매개 변수 리팩터링 제거 (c #) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.remove
dev_langs:
- CSharp
helpviewer_keywords:
- parameters [C#], removing
- refactoring [C#], Remove Parameters
- Remove Parameters refactoring [C#]
ms.assetid: f4fc3265-0ef8-4398-a691-c338178697a6
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 40c373c3575f007952143e29c8dfc2cfac3d080f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667486"
---
# <a name="remove-parameters-refactoring-c"></a>리팩터링 매개 변수 제거(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`Remove Parameters` 는 메서드, 인덱서 또는 대리자에서 매개 변수를 제거 하는 쉬운 방법을 제공 하는 리팩터링 작업입니다. 매개 변수 제거 선언을 변경 합니다. 멤버가 호출 되는 모든 위치에서 매개 변수는 새 선언을 반영 하기 위해 제거 됩니다.

 먼저 메서드, 인덱서 또는 대리자에 커서 위치를 지정 하 여 매개 변수 제거 작업을 수행 합니다. 커서가 위치에 있는 동안 제거 작업을 호출 하려면 `Parameters` **리팩터링** 메뉴를 클릭 하 고 바로 가기 키를 누르거나 바로 가기 메뉴에서 명령을 선택 합니다.

> [!NOTE]
> 확장 메서드의 첫 번째 매개 변수는 제거할 수 없습니다.

### <a name="to-remove-parameters"></a>매개 변수를 제거 하려면

1. 이라는 콘솔 응용 프로그램을 만들고 `RemoveParameters` 를 `Program` 다음 코드로 바꿉니다.

    ```csharp
    class A
    {
        // Invoke on 'A'.
        public A(string s, int i) { }
    }

    class B
    {
        void C()
        {
            // Invoke on 'A'.
            A a = new A("a", 2);
        }
    }
    ```

2. 메서드 `A` 선언 또는 메서드 호출 중 하나에 커서를 놓습니다.

3. **리팩터링** 메뉴에서 **매개 변수 제거** 를 선택 하 여 **매개 변수 제거** 대화 상자를 표시 합니다.

     바로 가기 키 CTRL + R, V를 입력 하 여 **매개 변수 제거** 대화 상자를 표시할 수도 있습니다.

     커서를 마우스 오른쪽 단추로 클릭 하 고 **리팩터링**을 가리킨 다음 **매개 변수 제거** 를 클릭 하 여 **매개 변수 제거** 대화 상자를 표시할 수도 있습니다.

4. **매개 변수** 필드를 사용 하 여 커서를에 배치 하 `int i` 고 **제거**를 클릭 합니다.

5. **확인**을 클릭합니다.

6. **변경 내용 미리 보기-매개 변수 제거** 대화 상자에서 **적용**을 클릭 합니다.

## <a name="remarks"></a>설명
 메서드 선언 또는 메서드 호출에서 매개 변수를 제거할 수 있습니다. 메서드 선언 또는 대리자 이름에 커서를 놓고 Remove Parameters를 호출 합니다.

> [!CAUTION]
> 매개 변수를 제거 하면 멤버 본문에서 참조 되는 매개 변수를 제거할 수 있지만 메서드 본문의 해당 매개 변수에 대 한 참조는 제거 되지 않습니다. 이렇게 하면 코드에 빌드 오류가 발생할 수 있습니다. 그러나 리팩터링 작업을 실행 하기 전에 **변경 내용 미리 보기** 대화 상자를 사용 하 여 코드를 검토할 수 있습니다.

 메서드를 호출 하는 동안 제거 되는 매개 변수를 수정 하면 매개 변수를 제거 해도 수정이 제거 됩니다. 예를 들어, 메서드 호출이에서 변경 된 경우

```csharp
MyMethod(param1++, param2);
```

 다음으로 변경:

```csharp
MyMethod(param2);
```

 리팩터링 작업을 통해는 `param1` 증가 되지 않습니다.

## <a name="see-also"></a>관련 항목
 [리팩터링(C#)](../csharp-ide/refactoring-csharp.md)