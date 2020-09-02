---
title: '방법: Nullable 형식 만들기(클래스 디자이너) | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- nullable types, Class Designer
- Class Designer [Visual Studio], nullable types
ms.assetid: 84673a89-3f6d-4668-919e-1c0f56182fe5
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 438f84a172c7e0a2d0dc957c578adc568a46495f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668153"
---
# <a name="how-to-create-a-nullable-type-class-designer"></a>방법: Nullable 형식 만들기(클래스 디자이너)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

특정 값 형식에 항상 정의된 값이 포함되거나 필요한 것은 아닙니다. 이는 일부 필드에 값이 할당되지 않을 수 있는 데이터베이스에서 일반적인 경우입니다. 예를 들어 데이터베이스 필드에 null 값을 할당하여 아직 값이 할당되지 않았음을 나타낼 수 있습니다.

 *Nullable 형식*은 해당 형식에 대한 일반적인 값 범위 및 null 값도 사용하도록 확장하는 값 형식입니다. Nullable\<Int32>로도 나타내는 `Int32`의 nullable에는 -2147483648에서 2147483647까지 값이 할당되거나 null 값이 할당될 수 있습니다. Nullable\<bool>에는 `True`, `False` 또는 null(전혀 값이 없음) 값이 할당될 수 있습니다.

 Nullable 형식은 <xref:System.Nullable%601> 구조체의 인스턴스입니다. Nullable 형식의 각 인스턴스에는 두 개의 public 읽기 전용 속성 `HasValue` 및 `Value`가 포함됩니다.

- `HasValue`는 `bool` 형식이고 변수에 정의된 값이 포함되는지 여부를 나타냅니다. `True`는 변수에 null이 아닌 값이 포함됨을 의미합니다. `if (x.HasValue)` 또는 `if (y != null)` 등의 문을 사용하여 정의된 값을 테스트할 수 있습니다.

- `Value`는 기본 형식과 같은 형식입니다. `HasValue`가 `True`이면 `Value`에는 의미 있는 값이 포함됩니다. `HasValue`가 `False`일 경우 `Value`에 액세스하면 잘못된 작업 예외가 throw됩니다.

  기본적으로 변수를 nullable 형식으로 선언하면 기본 값 형식의 기본값 외에 정의된 값(`HasValue`가 `False`임)이 포함되지 않습니다.

  클래스 디자이너에는 nullable 형식이 기본 형식이 표시되는 것처럼 표시됩니다.

  Visual C#의 nullable 형식에 대한 자세한 내용은 [Nullable 형식](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6)을 참조하세요. Visual Basic의 nullable 형식에 대한 자세한 내용은 [Nullable 값 형식](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6)을 참조하세요.

  [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-a-nullable-type-by-using-the-class-designer"></a>클래스 디자이너를 사용하여 nullable 형식을 추가하려면

1. 클래스 다이어그램에서 기존 클래스를 확장하거나 새 클래스를 만듭니다.

2. 프로젝트에 클래스를 추가하려면 **클래스 다이어그램** 메뉴에서 **추가**를 클릭하고 **클래스 추가**를 클릭합니다.

3. 클래스 모양을 확장하려면 **클래스 다이어그램** 메뉴에서 **확장**을 클릭합니다.

4. 클래스 모양을 선택합니다. **클래스 다이어그램** 메뉴에서 **추가**를 클릭하고 **필드**를 클릭합니다. 기본 이름 **필드**가 포함된 새 필드가 클래스 모양 및 **클래스 세부 내용** 창에 나타납니다.

5. **클래스 세부 내용** 창의 **이름** 열(또는 클래스 모양 자체)에서 새 필드의 이름을 유효하고 의미 있는 이름으로 변경합니다.

6. **클래스 세부 내용** 창의 **형식** 열에서 다음 코드에 표시된 대로 형식을 nullable 형식으로 선언합니다.

    ```csharp
    // Declare a nullable type in Visual C#:
    class Test
    {
       int? building_number = 5;
    }
    ```

    ```vb
    ' Declare a nullable type in Visual Basic:
    Class Test
       Dim buildingNumber As Nullable(Of Integer) = 5
    End Class
    ```

### <a name="to-add-a-nullable-type-by-using-the-code-editor"></a>코드 편집기를 사용하여 nullable 형식을 추가하려면

1. 프로젝트에 클래스를 추가합니다. **솔루션 탐색기**에서 프로젝트 노드를 선택하고 **프로젝트** 메뉴에서 **클래스 추가**를 클릭합니다.

2. 새 클래스에 대한 .cs 또는 .vb 파일에서 새 클래스의 nullable 형식 하나 이상을 클래스 선언에 추가합니다.

3. 클래스 뷰에서 새 클래스 아이콘을 클래스 디자이너 디자인 화면으로 끌어서 놓습니다. 클래스 모양이 클래스 다이어그램에 나타납니다.

4. 클래스 모양에 대한 세부 정보를 확장하고 마우스 포인터를 클래스 멤버 위로 이동합니다. 도구 설명에 각 멤버의 선언이 표시됩니다.

5. 클래스 모양을 마우스 오른쪽 단추로 클릭하고 **클래스 세부 내용**을 클릭합니다. **클래스 세부 내용** 창에서 새 형식의 속성을 보거나 수정할 수 있습니다.

## <a name="see-also"></a>관련 항목
 <xref:System.Nullable%601>Nullable 형식을 [사용 하](https://msdn.microsoft.com/library/0bacbe72-ce15-4b14-83e1-9c14e6380c28) 는 [nullable](https://msdn.microsoft.com/library/e473cb01-28ca-42be-9cea-f717055d72c6) 형식 [방법: Nullable 형식](https://msdn.microsoft.com/library/d4b67ee2-66e8-40c1-ae9d-545d32c71387) [nullable 값 형식](https://msdn.microsoft.com/library/9ac3b602-6f96-4e6d-96f7-cd4e81c468a6) 식별
