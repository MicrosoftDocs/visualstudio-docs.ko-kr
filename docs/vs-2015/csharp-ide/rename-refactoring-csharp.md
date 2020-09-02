---
title: '이름 바꾸기 리팩터링 (c #) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.csharp.refactoring.rename
dev_langs:
- CSharp
helpviewer_keywords:
- refactoring [C#], Rename
- Rename refactoring [C#]
ms.assetid: 268942fc-b142-4dfa-8d90-bedd548c2e4f
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0db7696268e5e3d24d005fbf35a08b330f2dc849
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667473"
---
# <a name="rename-refactoring-c"></a>이름 바꾸기 리팩터링(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**이름 바꾸기** 는 VISUAL Studio IDE (통합 개발 환경)의 리팩터링 기능으로, 필드, 지역 변수, 메서드, 네임 스페이스, 속성, 형식 등의 코드 기호에 대 한 식별자 이름을 쉽게 바꿀 수 있는 방법을 제공 합니다. **이름 바꾸기** 를 사용 하 여 주석과 문자열의 이름을 변경 하 고 식별자의 선언과 호출을 변경할 수 있습니다.

> [!NOTE]
> Visual Studio에 대 한 소스 제어를 사용 하는 경우 이름 바꾸기 리팩터링을 수행 하기 전에 최신 버전의 원본을 가져옵니다.

 이름 바꾸기 리팩터링은 다음과 같은 Visual Studio 기능에서 사용할 수 있습니다.

|기능|IDE에서의 리팩터링 동작|
|-------------|----------------------------------------|
|코드 편집기|코드 편집기에서 특정 형식의 코드 기호 위에 커서를 놓으면 이름 바꾸기 리팩터링을 사용할 수 있습니다. 커서가이 위치에 있는 경우 바로 가기 키 (CTRL + R, CTRL + R)를 입력 하거나 스마트 태그, 바로 가기 메뉴 또는 **리팩터링** 메뉴에서 **이름 바꾸기** 명령을 선택 하 여 **rename** 명령을 호출할 수 있습니다.|
|클래스 뷰|클래스 뷰에서 식별자를 선택 하는 경우 바로 가기 메뉴 및 **리팩터링** 메뉴에서 이름 바꾸기 리팩터링을 사용할 수 있습니다.|
|개체 브라우저|개체 브라우저에서 식별자를 선택 **하는 경우 리팩터링 메뉴 에서만** 이름 바꾸기 리팩터링을 사용할 수 있습니다.|
|Windows Forms 디자이너의 속성 표|Windows Forms 디자이너의 **속성 표에서** 컨트롤의 이름을 변경 하면 해당 컨트롤에 대 한 이름 바꾸기 작업이 시작 됩니다. **이름 바꾸기** 대화 상자가 나타나지 않습니다.|
|솔루션 탐색기|**솔루션 탐색기**에서는 바로 가기 메뉴에서 **이름 바꾸기** 명령을 사용할 수 있습니다. 선택한 소스 파일의 클래스 이름이 파일 이름과 동일한 클래스를 포함 하는 경우이 명령을 사용 하 여 소스 파일의 이름을 동시에 바꾸고 이름 바꾸기 리팩터링을 실행할 수 있습니다.<br /><br /> 예를 들어 기본 Windows 기반 응용 프로그램을 만든 다음 Form1.cs 이름을 TestForm.cs로 바꾸면 소스 파일 이름 Form1.cs가 TestForm.cs로 바뀌고 클래스 Form1 및 해당 클래스에 대 한 모든 참조의 이름이 TestForm으로 변경 됩니다. **참고:**  **Undo** 명령 (CTRL + Z)은 코드에서 이름 바꾸기 리팩터링을 실행 취소 하 고 파일 이름을 원래 이름으로 다시 변경 하지 않습니다. <br /><br /> 선택한 소스 파일의 이름이 파일 이름과 동일한 클래스를 포함 하지 않는 경우 **솔루션 탐색기** 의 **rename** 명령은 원본 파일만 이름을 바꾸고 이름 바꾸기 리팩터링을 실행 하지 않습니다.|

## <a name="rename-operations"></a>이름 바꾸기 작업
 **이름 바꾸기**를 실행 하는 경우 리팩터링 엔진은 다음 표에 설명 된 대로 각 코드 기호와 관련 된 이름 바꾸기 작업을 수행 합니다.

|코드 기호|이름 바꾸기 작업|
|-----------------|----------------------|
|필드|필드의 선언과 용도를 새 이름으로 변경 합니다.|
|지역 변수|변수의 선언과 용도를 새 이름으로 변경 합니다.|
|메서드|메서드와 해당 메서드에 대 한 모든 참조의 이름을 새 이름으로 변경 합니다. **참고:**  확장명 메서드의 이름을 바꾸면 확장 메서드가 정적 메서드 또는 인스턴스 메서드로 사용 되 고 있는지 여부에 관계 없이 범위 내에 있는 메서드의 모든 인스턴스에 이름 바꾸기 작업이 전파 됩니다. 자세한 내용은 [확장 메서드](https://msdn.microsoft.com/library/175ce3ff-9bbf-4e64-8421-faeb81a0bb51)를 참조하세요.|
|네임스페이스|선언, 모든 문 및 정규화 된 이름에서 네임 스페이스의 이름을 새 이름으로 변경 합니다 `using` . **참고:**  네임 스페이스의 이름을 바꿀 때는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **프로젝트 디자이너**의 **응용 프로그램** 페이지에서 **기본 네임 스페이스** 속성도 업데이트 합니다. **편집** 메뉴에서 **실행 취소** 를 선택 하 여이 속성을 다시 설정할 수 없습니다. **기본 네임 스페이스** 속성 값을 다시 설정 하려면 **프로젝트 디자이너**에서 속성을 수정 해야 합니다. 자세한 내용은 [응용 프로그램 페이지](../ide/reference/application-page-project-designer-csharp.md)를 참조 하세요.|
|속성|속성의 선언과 용도를 새 이름으로 변경 합니다.|
|형식|생성자 및 소멸자를 포함 하 여 모든 선언과 모든 형식의 사용을 새 이름으로 변경 합니다. 부분 형식의 경우 이름 바꾸기 작업은 모든 부분으로 전파 됩니다.|

#### <a name="to-rename-an-identifier"></a>식별자의 이름을 바꾸려면

1. `RenameIdentifier`이라는 콘솔 애플리케이션을 만들고 `Program`을 다음 예제 코드로 바꿉니다.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. `MethodB`메서드 선언 또는 메서드 호출 중 하나에 커서를 놓습니다.

3. **리팩터링** 메뉴에서 **이름 바꾸기**를 선택 합니다. **이름 바꾸기** 대화 상자가 나타납니다.

     커서를 마우스 오른쪽 단추로 클릭 하 고 상황에 맞는 메뉴에서 **리팩터링** 을 가리킨 다음 **이름 바꾸기** 를 클릭 하 여 **이름 바꾸기** 대화 상자를 표시할 수도 있습니다.

4. **새 이름** 필드에을 입력 `MethodC` 합니다.

5. **주석에서 검색** 확인란을 선택 합니다.

6. **확인**을 클릭합니다.

7. **변경 내용 미리 보기** 대화 상자에서 **적용**을 클릭 합니다.

#### <a name="to-rename-an-identifier-using-smart-tags"></a>스마트 태그를 사용 하 여 식별자 이름을 바꾸려면

1. `RenameIdentifier`이라는 콘솔 애플리케이션을 만들고 `Program`을 다음 예제 코드로 바꿉니다.

    ```csharp
    class ProtoClassA
    {
        // Invoke on 'MethodB'.
        public void MethodB(int i, bool b) { }
    }

    class ProtoClassC
    {
        void D()
        {
            ProtoClassA MyClassA = new ProtoClassA();

            // Invoke on 'MethodB'.
            MyClassA.MethodB(0, false);
        }
    }
    ```

2. 에 대 한 선언에서 `MethodB` 메서드 식별자를 통해 또는 백스페이스를 입력 합니다. 스마트 태그 프롬프트가이 식별자 아래에 표시 됩니다.

    > [!NOTE]
    > 식별자 선언에서 스마트 태그를 사용 하 여 이름 바꾸기 리팩터링을 호출할 수 있습니다.

3. 키보드 바로 가기 키 (SHIFT + ALT + F10)를 입력 한 다음 아래쪽 화살표를 눌러 스마트 태그 메뉴를 표시 합니다.

     또는

     스마트 태그를 표시 하려면 스마트 태그 프롬프트 위로 마우스 포인터를 이동 합니다. 그런 다음 스마트 태그 위로 마우스 포인터를 이동 하 고 아래쪽 화살표를 클릭 하 여 스마트 태그 메뉴를 표시 합니다.

4. 코드 변경 내용 미리 보기 없이 이름 바꾸기 리팩터링을 호출 하려면 ' '에서 ' ' (으) **로 이름 바꾸기 \<identifer1> \<identifier2> ** 메뉴 항목을 선택 합니다. 에 대 한 모든 참조가 **\<identifer1>** 자동으로로 업데이트 됩니다 **\<identifier2>** .

     또는

     코드 변경 내용 미리 보기를 사용 하 여 이름 바꾸기 리팩터링을 호출 하려면 [ **미리 보기로 이름 바꾸기** ] 메뉴 항목을 선택 합니다. **변경 내용 미리 보기** 대화 상자가 표시 됩니다.

## <a name="remarks"></a>설명

## <a name="renaming-implemented-or-overridden-members"></a>구현 되거나 재정의 된 멤버 이름 바꾸기
 다른 형식의 멤버에서 구현/재정의 하거나 구현/재정의 하는 멤버 **의 이름을** 바꾸면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이름 바꾸기 작업을 수행 하면 연계 업데이트를 수행 하는 대화 상자가 표시 됩니다. **계속**을 클릭 하면 리팩터링 엔진이 이름을 바꿀 멤버와의 구현/재정의 관계를 가진 기본 및 파생 형식에서 모든 멤버를 재귀적으로 찾아 이름을 바꿉니다.

 다음 코드 예제에는 구현/재정의 관계가 있는 멤버가 포함 되어 있습니다.

 [!code-csharp[CsUsingCsIDERefactor#1](../snippets/csharp/VS_Snippets_VBCSharp/CsUsingCsIDERefactor/CS/Class1.cs#1)]

 이전 예제에서 이름 바꾸기는을 `C.Method()` `Ibase.Method()` 구현 하기 때문에 이름을 바꿉니다 `C.Method()` `Ibase.Method()` . 그런 다음 리팩터링 엔진은 `Ibase.Method()` 에서에 의해 구현 되 고 이름을 바꾸는 것을 재귀적으로 확인 `Derived.Method()` `Derived.Method()` 합니다. `Base.Method()`는를 재정의 하지 않으므로 리팩터링 엔진은 이름을 바꾸지 않습니다 `Derived.Method()` `Base.Method()` . **이름 바꾸기** 대화 상자에서 **이름을 변경한 오버 로드** 를 확인 하지 않으면 리팩터링 엔진이 여기에서 중지 됩니다.

 **이름 바꾸기 오버 로드** 를 선택 하는 경우 리팩터링 엔진은에 의해 재정의 되기 때문에를 오버 로드 하 `Derived.Method(int i)` `Derived.Method()` `Base.Method(int i)` `Derived.Method(int i)` 고 `Base.Method()` 의 오버 로드 이므로의 `Base.Method(int i)` 이름을 바꿉니다.

> [!NOTE]
> 참조 된 어셈블리에 정의 된 멤버의 이름을 바꾸면 대화 상자에서 이름을 바꾸면 빌드 오류가 발생 한다는 것을 설명 합니다.

## <a name="renaming-properties-of-anonymous-types"></a>익명 형식의 속성 이름 바꾸기
 익명 형식의 속성 이름을 바꾸면 동일한 속성을 가진 다른 무명 형식의 속성에 이름 바꾸기 작업이 전파 됩니다. 다음 예에서는이 동작을 보여 줍니다.

```csharp
var a = new { ID = 1};
var b = new { ID = 2};
```

 위의 코드에서 이름 바꾸기는 `ID` `ID` 동일한 기본 무명 형식이 있으므로 두 문 모두에서 변경 됩니다.

```csharp
var companyIDs =
    from c in companylist
    select new { ID = c.ID, Name = c.Name};

var orderIDs =
    from o in orderlist
    select new { ID = o.ID, Item = o.Name};
```

 앞의 코드에서는 및가 `ID` `ID` `companyIDs` 같은 속성을 포함 하지 않기 때문에 이름 바꾸기는의 인스턴스 하나만의 이름을 바꿉니다 `orderIDs` .

## <a name="see-also"></a>관련 항목
 [리팩터링 (c #)](../csharp-ide/refactoring-csharp.md) [익명 형식](https://msdn.microsoft.com/library/59c9d7a4-3b0e-475e-b620-0ab86c088e9b)