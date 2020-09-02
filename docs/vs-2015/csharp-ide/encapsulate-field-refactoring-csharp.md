---
title: '필드 캡슐화 리팩터링 (c #) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.encapsulatefield
dev_langs:
- CSharp
helpviewer_keywords:
- Encapsulate Field refactoring operation [C#]
- refactoring [C#], Encapsulate Field
ms.assetid: bf714a04-ab1e-49ce-99ce-dda1ebb1a17f
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b4f5ddbe7eab925b06584f00b04bed3c74e9811
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667566"
---
# <a name="encapsulate-field-refactoring-c"></a>필드 캡슐화 리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**필드 캡슐화** 리팩터링 작업을 사용 하면 기존 필드에서 속성을 빠르게 만든 다음 새 속성에 대 한 참조를 사용 하 여 코드를 원활 하 게 업데이트할 수 있습니다.

 [필드가](https://msdn.microsoft.com/library/3cbb2f61-75f8-4cce-b4ef-f5d1b3de0db7) [public](https://msdn.microsoft.com/library/0ae45d16-a551-4b74-9845-57208de1328e)인 경우 다른 개체는 해당 필드에 직접 액세스할 수 있으며 해당 필드를 소유 하는 개체에서 해당 필드를 수정할 수 있습니다. [속성](https://msdn.microsoft.com/library/e295a8a2-b357-4ee7-a12e-385a44146fa8) 을 사용 하 여 해당 필드를 캡슐화 하면 필드에 대 한 직접 액세스를 허용 하지 않을 수 있습니다.

 새 속성을 만들기 위해 **필드 캡슐화** 작업은 캡슐화 할 필드에 대 한 액세스 한정자를 [private](https://msdn.microsoft.com/library/654c0bb8-e6ac-4086-bf96-7474fa6aa1c8)로 변경 하 고 해당 필드에 대 한 [get](https://msdn.microsoft.com/library/a52de048-fbe0-41b0-82ec-8e4ac04d3a71) 및 [set](https://msdn.microsoft.com/library/30d7e4e5-cc2e-4635-a597-14a724879619) 접근자를 생성 합니다. 필드가 읽기 전용으로 선언되는 경우와 같이 몇몇 경우에는 `get` 접근자만 생성됩니다.

 리팩터링 엔진은 **필드 캡슐화** 대화 상자의 **참조 업데이트** 섹션에 지정 된 영역에서 새 속성에 대 한 참조를 사용 하 여 코드를 업데이트 합니다.

### <a name="to-create-a-property-from-a-field"></a>필드에서 속성을 만들려면

1. `EncapsulateFieldExample`이라는 콘솔 애플리케이션을 만들고 `Program`을 다음 예제 코드로 바꿉니다.

    ```csharp
    class Square
    {
        // Select the word 'width' and then use Encapsulate Field.
        public int width, height;
    }
    class MainClass
    {
        public static void Main()
        {
            Square mySquare = new Square();
            mySquare.width = 110;
            mySquare.height = 150;
            // Output values for width and height.
            Console.WriteLine("width = {0}", mySquare.width);
            Console.WriteLine("height = {0}", mySquare.height);
        }
    }
    ```

2. [코드 편집기](../ide/writing-code-in-the-code-and-text-editor.md)의 선언에 캡슐화 할 필드 이름에 커서를 놓습니다. 아래 예제에서 커서를 단어 `width`에 배치합니다.

    ```csharp
    public int width, height;
    ```

3. **리팩터링** 메뉴에서 **필드 캡슐화**를 클릭 합니다.

     **필드 캡슐화** 대화 상자가 나타납니다.

     키보드 바로 가기 키 CTRL + R, E를 입력 하 여 **필드 캡슐화** 대화 상자를 표시할 수도 있습니다.

     커서를 마우스 오른쪽 단추로 클릭 하 고 **리팩터링**을 가리킨 다음 **필드 캡슐화** 를 클릭 하 여 **필드 캡슐화** 대화 상자를 표시할 수도 있습니다.

4. 설정을 지정합니다.

5. ENTER 키를 누르거나 **확인** 단추를 클릭 합니다.

6. **참조 변경 내용 미리 보기** 옵션을 선택한 경우 **참조 변경 내용 미리 보기** 창이 열립니다. **적용** 단추를 클릭합니다.

     다음 `get` 및 `set` 접근자 코드가 소스 파일에 표시됩니다.

    ```csharp
    public int Width
    {
        get { return width; }
        set { width = value; }
    }
    ```

     `Main` 메서드의 코드도 새 `Width` 속성 이름으로 업데이트됩니다.

    ```csharp
    Square mySquare = new Square();
    mySquare.Width = 110;
    mySquare.height = 150;
    // Output values for width and height.
    Console.WriteLine("width = {0}", mySquare.Width);
    ```

## <a name="remarks"></a>설명
 **필드 캡슐화** 작업은 커서를 필드 선언과 같은 줄에 배치 하는 경우에만 가능 합니다.

 여러 필드를 선언 하는 선언의 경우 **필드 캡슐화** 는 쉼표를 필드 사이에 경계로 사용 하 고 커서가 가장 가까운 필드와 커서와 같은 줄에서 리팩터링을 시작 합니다. 선언에서 필드 이름을 선택하여 캡슐화할 필드를 지정할 수도 있습니다.

 이 리팩터링 작업으로 생성된 코드는 필드 캡슐화 코드 조각 기능을 통해 모델링됩니다. 코드 조각은 수정 가능합니다. 자세한 내용은 [코드 조각](../ide/code-snippets.md)을 참조하세요.

## <a name="see-also"></a>관련 항목
 [리팩터링 (c #)](../csharp-ide/refactoring-csharp.md) [Visual c # 코드 조각](../ide/visual-csharp-code-snippets.md)