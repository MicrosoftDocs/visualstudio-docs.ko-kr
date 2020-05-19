---
title: Windows Form 디버그 | Microsoft Docs
ms.custom: seodec18
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], walkthroughs
- debugging managed code, Windows Forms
- debugging [Visual Studio], Windows Forms
- Attach to Process dialog box
- debugger, attaching to programs
- Attach to Process dialog box, walkthroughs
- Windows Forms, debugging
- debugging Windows Forms, walkthroughs
ms.assetid: 529db1e2-d9ea-482a-b6a0-7c543d17f114
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 701d156d5fdc23a5e98ac1de43c1882f3065171e
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72728326"
---
# <a name="walkthrough-debugging-a-windows-form"></a>연습: Windows Form 디버깅
Windows Form은 가장 일반적인 관리형 애플리케이션 중 하나입니다. Windows Form은 표준 Windows 애플리케이션을 만듭니다. Visual Basic, C# 또는 C++를 사용하여 이 연습을 완료할 수 있습니다.

 먼저 열려 있는 모든 솔루션을 닫아야 합니다.

### <a name="to-prepare-for-this-walkthrough"></a>이 연습을 준비하려면

- 열려 있는 솔루션이 있으면 닫습니다. **파일** 메뉴에서 **솔루션 닫기**를 선택합니다.

## <a name="create-a-new-windows-form"></a>새 Windows Form 만들기
 다음에는 새 Windows Form을 만듭니다.

#### <a name="to-create-the-windows-form-for-this-walkthrough"></a>이 연습에 사용할 Windows Form을 만들려면

1. **파일** 메뉴에서 **새로 만들기**를 선택하고 **프로젝트**를 클릭합니다.

     **새 프로젝트** 대화 상자가 나타납니다.

2. 프로젝트 형식 창에서 **Visual Basic**, **Visual C#** 또는 **Visual C++** 노드를 연 다음,

    1. Visual Basic 또는 Visual C#의 경우 **Windows 데스크톱** > **Windows Form 앱**을 선택합니다.

    2. Visual C++의 경우 **Windows 데스크톱 애플리케이션**을 선택합니다.

3. **이름** 상자에서 프로젝트에 고유한 이름(예: Walkthrough_SimpleDebug)을 지정합니다.

4. **확인**을 클릭합니다.

     Visual Studio에서 새 프로젝트를 만들고 Windows Forms 디자이너에 새 양식을 표시합니다. 자세한 내용은 [Windows Forms 디자이너](/previous-versions/visualstudio/visual-studio-2010/e06hs424\(v\=vs.100\))를 참조하세요.

5. **보기** 메뉴에서 **도구 상자**를 선택합니다.

     도구 상자가 열립니다. 자세한 내용은 [도구 상자](../ide/reference/toolbox.md)를 참조하세요.

6. 도구 상자에서 **Button** 컨트롤을 클릭하고 컨트롤을 양식 디자인 화면으로 끌어 옵니다. 양식에 단추를 놓습니다.

7. 도구 상자에서 **TextBox** 컨트롤을 클릭하고 컨트롤을 양식 디자인 화면으로 끌어 옵니다. 양식에 **TextBox**를 놓습니다.

8. 양식 디자인 화면에서 단추를 두 번 클릭합니다.

     이렇게 하면 코드 페이지로 이동합니다. 커서는 `button1_Click`에 있어야 합니다.

10. `button1_Click` 함수에 다음 코드를 추가합니다.

    ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

11. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

     프로젝트가 오류 없이 빌드되어야 합니다.

## <a name="debug-your-form"></a>양식 디버그
 이제 디버깅을 시작할 준비가 되었습니다.

#### <a name="to-debug-the-windows-form-created-for-this-walkthrough"></a>이 연습용으로 만든 Windows Form을 디버그하려면

1. 소스 창에서 추가한 텍스트와 같은 줄에서 왼쪽 여백을 클릭합니다.

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

     빨간 점이 나타나며 해당 줄의 텍스트가 빨간색으로 강조 표시됩니다. 빨간 점은 중단점을 나타냅니다. 자세한 내용은 [중단점](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583)을 참조하세요. 디버거에서 애플리케이션을 실행하면 코드가 적중되는 위치에서 디버거가 실행을 중단합니다. 그런 다음 애플리케이션의 상태를 보고 디버깅할 수 있습니다.

    > [!NOTE]
    > 코드 줄을 마우스 오른쪽 단추로 클릭하고, **중단점**을 가리킨 다음, **중단점 삽입**을 클릭하여 해당 줄에 중단점을 추가할 수도 있습니다.

2. **디버그** 메뉴에서 **시작**을 선택합니다.

     Windows Form이 실행되기 시작합니다.

3. Windows Form에서 추가한 단추를 클릭합니다.

     Visual Studio의 경우 이 작업을 수행하면 코드 페이지에서 중단점을 설정한 줄로 이동합니다. 이 줄은 노란색으로 강조 표시되어 있어야 합니다. 이제 애플리케이션의 변수를 보고 해당 애플리케이션의 실행을 제어할 수 있습니다. 이제 애플리케이션의 실행이 중지되었고 사용자의 작업을 기다립니다.

4. **디버그** 메뉴에서 **창**을 선택한 다음, **조사식**을 선택하고, **Watch1**을 클릭합니다.

5. **Watch1** 창에서 빈 행을 클릭합니다. **이름** 열에 `textBox1.Text`(Visual Basic 또는 Visual C#을 사용하는 경우) 또는 `textBox1->Text`(C++를 사용하는 경우)를 입력한 다음, Enter 키를 누릅니다.

     **Watch1** 창에는 이 변수의 값이 따옴표로 묶여서 표시됩니다.

    `""`

6. **디버그** 메뉴에서 **한 단계씩 코드 실행**을 선택합니다.

     textBox1.Text의 값이 **Watch1** 창에서 다음으로 바뀝니다.

    `Button was clicked!`

7. **디버그** 메뉴에서 **계속**을 선택하여 프로그램 디버그를 다시 시작합니다.

8. Windows Form에서 단추를 다시 클릭합니다.

     Visual Studio가 실행을 다시 중단합니다.

9. 중단점을 나타내는 빨간색 점을 클릭합니다.

     이렇게 하면 코드에서 중단점이 제거됩니다.

10. **디버그** 메뉴에서 **디버깅 중지**를 선택합니다.

## <a name="attach-to-your-windows-form-application-for-debugging"></a>디버깅을 위해 Windows Form 애플리케이션에 연결
 [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)]에서는 실행 중인 프로세스에 디버거를 연결할 수 있습니다. Express Edition을 사용하는 경우 이 기능이 지원되지 않습니다.

#### <a name="to-attach-to-the-windows-form-application-for-debugging"></a>디버깅을 위해 Windows Form 애플리케이션에 연결하려면

1. 위에서 만든 프로젝트에서 왼쪽 여백을 클릭하여 추가한 줄에 중단점을 다시 한번 설정합니다.

     ```vb
    textBox1.Text = "Button was clicked!"
    ```

    ```csharp
    textBox1.Text = "Button was clicked!";
    ```

    ```cpp
    textBox1->Text = "Button was clicked!";
    ```

2. **디버그** 메뉴에서 **디버그하지 않고 시작**을 선택합니다.

     Windows Form은 실행 파일을 두 번 클릭한 것처럼 Windows에서 실행되기 시작합니다. 디버거가 연결되어 있지 않습니다.

3. **디버그** 메뉴에서 **프로세스에 연결**을 선택합니다. 이 명령은 **도구** 메뉴에서도 사용할 수 있습니다.

     **프로세스에 연결** 대화 상자가 나타납니다.

4. **사용 가능한 프로세스** 창의 **프로세스** 열에서 프로세스 이름(Walkthrough_SimpleDebug.exe)을 찾고 클릭합니다.

5. **연결** 단추를 클릭합니다.

6. Windows Form에서 단추를 한 번만 클릭합니다.

     디버거는 중단점에서 Windows Form의 실행을 중단합니다.

## <a name="see-also"></a>참조
- [관리 코드 디버그](../debugger/debugging-managed-code.md)
- [디버거 보안](../debugger/debugger-security.md)
