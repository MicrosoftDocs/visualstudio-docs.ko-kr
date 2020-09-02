---
title: '메서드 추출 리팩터링 (c #) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.extractmethod
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Extract Method
- Extract Method refactoring operation [C#]
ms.assetid: eeba11df-a815-4bec-9c21-8a831891b783
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6e6d5e7913a7433fd4b30da490f33dd614c3e2b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667537"
---
# <a name="extract-method-refactoring-c"></a>메서드 추출 리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Extract 메서드** 는 기존 멤버의 코드 조각에서 새 메서드를 만드는 쉬운 방법을 제공 하는 리팩터링 작업입니다.

 **Extract 메서드**를 사용 하 여 기존 멤버의 코드 블록 내에서 선택 된 코드를 추출 하 여 새 메서드를 만들 수 있습니다. 추출 된 새 메서드는 선택한 코드를 포함 하 고 기존 멤버의 선택 된 코드는 새 메서드에 대 한 호출로 바뀝니다. 코드 조각을 자체 메서드로 전환 하면 재사용 및 가독성 향상을 위해 신속 하 고 정확 하 게 코드를 재구성할 수 있습니다.

 **Extract 메서드** 는 다음과 같은 이점을 제공 합니다.

- 재사용 가능한 불연속 메서드를 강조 하 여 최상의 코딩 방법을 권장 합니다.

- 좋은 조직을 통해 자체 문서화 코드를 장려 합니다.

     설명이 포함 된 이름을 사용 하는 경우 고급 메서드는 일련의 주석과 유사한 정보를 읽을 수 있습니다.

- 재정의를 간소화 하기 위해 세부적인 메서드를 만들도록 권장 합니다.

- 코드 중복을 줄입니다.

### <a name="to-use-extract-method"></a>Extract 메서드를 사용 하려면

1. `ExtractMethod`이라는 콘솔 애플리케이션을 만들고 `Program`을 다음 예제 코드로 바꿉니다.

    ```csharp
    class A
    {
        const double PI = 3.141592;

        double CalculatePaintNeeded(double paintPerUnit, double radius)
        {
            // Select any of the following:
            // 1. The entire next line of code.
            // 2. The right-hand side of the next line of code.
            // 3. Just "PI *" of the right-hand side of the next line
            //    of code (to see the prompt for selection expansion).
            // 4.  All code within the method body.
            // ...Then invoke Extract Method.

            double area = PI * radius * radius;

            return area / paintPerUnit;
        }
    }
    ```

2. 추출 하려는 코드 조각을 선택 합니다.

    ```csharp
    double area = PI * radius * radius;
    ```

3. **리팩터링** 메뉴에서 **메서드 추출**을 클릭 합니다.

     **메서드 추출** 대화 상자가 나타납니다.

     또는 바로 가기 키 CTRL + R, M을 입력 하 여 **메서드 추출** 대화 상자를 표시할 수도 있습니다.

     선택한 코드를 마우스 오른쪽 단추로 클릭 하 고 **리팩터링**을 가리킨 다음 **메서드 추출** 을 클릭 하 여 **메서드 추출** 대화 상자를 표시할 수도 있습니다.

4. 새 `CircleArea` **메서드 이름** 상자에와 같은 새 메서드의 이름을 지정 합니다.

     새 메서드 시그니처의 미리 보기가 **메서드 시그니처 미리**보기에 표시 됩니다.

5. **확인**을 클릭합니다.

## <a name="remarks"></a>설명
 **Extract method** 명령을 사용 하면 동일한 클래스의 소스 멤버 다음에 새 메서드가 삽입 됩니다.

## <a name="partial-types"></a>부분 형식(Partial Type)
 클래스가 partial 형식이 면 **Extract 메서드** 는 소스 멤버 바로 다음에 새 메서드를 생성 합니다. **Extract 메서드** 는 새 메서드의 서명을 결정 하 고 새 메서드의 코드에서 참조 하는 인스턴스 데이터가 없을 때 정적 메서드를 만듭니다.

## <a name="generic-type-parameters"></a>제네릭 형식 매개 변수
 제한 되지 않은 제네릭 형식 매개 변수를 포함 하는 메서드를 추출 하면 생성 된 코드는 `ref` 값이 할당 되지 않은 경우 해당 매개 변수에 한정자를 추가 하지 않습니다. 추출 된 메서드에서 제네릭 형식 인수로 참조 형식을 지원 하면 `ref` 메서드 시그니처의 매개 변수에 한정자를 수동으로 추가 해야 합니다.

## <a name="anonymous-methods"></a>무명 메서드
 무명 메서드 외부에서 선언 되거나 참조 되는 지역 변수에 대 한 참조를 포함 하는 무명 메서드의 일부를 추출 하려고 하면 Visual Studio에서 잠재적 의미 변화에 대해 경고 합니다.

 무명 메서드는 지역 변수의 값을 사용 하는 경우 무명 메서드가 실행 될 때 값을 가져옵니다. 무명 메서드를 다른 메서드로 추출할 경우 추출 된 메서드를 호출 하는 순간 지역 변수의 값을 가져옵니다.

 다음 예에서는 이러한 의미 체계 변경을 보여 줍니다. 이 코드가 실행 되 면 **11** 이 콘솔에 출력 됩니다. **Extract 메서드** 를 사용 하 여 코드 주석으로 표시 된 코드 영역을 자체 메서드로 추출한 다음 리팩터링된 코드를 실행 하는 경우 **10** 이 콘솔에 출력 됩니다.

```csharp
class Program
{
    delegate void D();
    D d;
    static void Main(string[] args)
    {
        Program p = new Program();
        int i = 10;
        /*begin extraction*/
            p.d = delegate { Console.WriteLine(i++); };
        /*end extraction*/
        i++;
        p.d();
    }
}
```

 이 상황을 해결 하려면 클래스의 무명 메서드 필드에서 사용 되는 지역 변수를 만듭니다.

## <a name="see-also"></a>관련 항목
 [리팩터링(C#)](../csharp-ide/refactoring-csharp.md)