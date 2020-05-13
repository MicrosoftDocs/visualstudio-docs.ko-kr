---
title: Mac용 Visual Studio 확장 연습
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/14/2017
ms.technology: vs-ide-sdk
ms.assetid: 7D00512B-9688-4D8D-87A7-F04F207E3D02
ms.openlocfilehash: c5b3b759b32acfc86b4b584b3f3d52298c138a2c
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "74985033"
---
# <a name="extending-visual-studio-for-mac-walkthrough"></a>Mac용 Visual Studio 확장 연습

이 항목에서는 [간단한 확장 패키지](https://github.com/mjh4/AddIns/tree/master/DateInserter)를 빌드하는 과정을 안내합니다. 확장 패키지는 Mac용 Visual Studio의 편집 메뉴에 새 명령을 만듭니다. 이 명령을 통해 사용자는 열려 있는 텍스트 문서에 현재 날짜와 시간을 삽입할 수 있습니다.

이 예제에서는 Add-in Maker를 사용합니다. Add-in Maker는 새 프로젝트 템플릿을 만들고 사용자 지정 확장 패키지에 필요한 파일로 채웁니다.

1. 아직 열려 있지 않은 경우 먼저 Mac용 Visual Studio를 시작합니다.

   ![Mac용 Visual Studio 스크린샷](media/extending-visual-studio-mac-addin3.png)

2. 확장 관리자를 사용하여 _Add-in Maker 확장 패키지_를 설치합니다. Visual Studio 메뉴에서 **확장...** 을 선택합니다.

   ![추가 기능 관리자 탭](media/extending-visual-studio-mac-addin4.png)

3. 갤러리 탭으로 이동한 다음 오른쪽 위의 검색 창에 `Addin Maker`를 입력합니다. 추가 기능 개발 범주에서 Add-in Maker를 선택하고 <kbd>설치</kbd>를 클릭합니다. 아무것도 표시되지 않는 경우 [새로 고침]을 누르고 다시 검색합니다.

   ![추가 기능 관리자](media/extending-visual-studio-mac-addin5.png)

4. 이제 Add-in Maker가 설치되었으므로 확장 패키지 빌드를 시작할 수 있습니다. 먼저 새 솔루션을 만듭니다.

5. **새 솔루션 대화 상자**에서 **기타 > 기타 > 일반 > Xamarin Studio 추가 기능 > C#** 템플릿을 선택하고 다음 화면에서 새 솔루션의 이름을 `DateInserter`로 지정합니다.

   ![새 솔루션 만들기](media/extending-visual-studio-mac-addin7New.png)

6. Mac용 Visual Studio에서 새 솔루션을 채웁니다.

   ![채워진 솔루션](media/extending-visual-studio-mac-addin8.png)

7. `Manifest.addin.xml`에서 템플릿 코드를 제거하고 다음 코드로 바꿉니다.

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
      <ExtensionModel>
          <Extension path = "/MonoDevelop/Ide/Commands/Edit">
              <Command id = "DateInserter.DateInserterCommands.InsertDate"
                  _label = "Insert Date"
                  defaultHandler = "DateInserter.InsertDateHandler" />
          </Extension>

          <Extension path = "/MonoDevelop/Ide/MainMenu/Edit">
              <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
          </Extension>
      </ExtensionModel>
   ```

8. 이제 텍스트 편집기에 날짜와 시간 삽입을 처리할 파일을 설정해야 합니다. 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 새 파일을 추가합니다. **일반 > 빈 클래스**를 선택하고 새 파일의 이름을 *InsertDateHandler*로 지정합니다.

   ![날짜 삽입 처리기](media/extending-visual-studio-mac-addin9.png)

9. `InsertDateHandler.cs`에서 템플릿 코드를 제거하고 다음 코드로 바꾸겠습니다.

   ```cs
   using MonoDevelop.Components.Commands;
   using MonoDevelop.Ide;
   using MonoDevelop.Ide.Gui;
   using System;

   namespace DateInserter
   {
      class InsertDateHandler : CommandHandler
      {
          protected override void Run()
          {

          }

          protected override void Update(CommandInfo info)
          {

          }
      }
   }
   ```

   나중에 이러한 두 자리 표시자 메서드를 확장할 것입니다.

10. **DateInserter** 프로젝트를 마우스 오른쪽 단추로 클릭하고 **추가 > 새 파일**을 선택합니다. **일반 > 빈 열거형**을 선택하고 새 파일의 이름을 *DateInserterCommands*로 지정합니다.

    ![DateInserterCommands](media/extending-visual-studio-mac-addin10.png)

11. `InsertDate` 파일에 `DateInserterCommands.cs` 명령을 새 열거형으로 추가합니다.

    ``` cs
    using System;

    namespace DateInserter
    {
      public enum DateInserterCommands
      {
          InsertDate,
      }
    }
    ```

12. 이 시점에는 작동하는 확장 패키지가 있어야 합니다. 작업 내용을 저장하고 애플리케이션을 실행하여 테스트할 수 있습니다. IDE에서 새 확장 패키지가 설치된 Mac용 Visual Studio의 새 인스턴스를 시작합니다. **편집 메뉴**로 이동하면 아래 스크린샷과 같이 Mac용 Visual Studio에 **날짜 삽입**이라는 새 옵션이 있습니다.

    ![날짜 삽입 명령](media/extending-visual-studio-mac-addin11.png)

    현재 구현에는 자리 표시자 메서드만 있으므로 메뉴에서 날짜 삽입을 선택해도 적용되지 않습니다.

13. 이 프레임워크는 확장 패키지를 위해 구현되었으며, 날짜 삽입을 구동하는 코드를 작성해야 합니다. 먼저, **의**  메서드를 다음 코드로 바꿔 사용자가 텍스트 파일을 연 경우에만 `Update`날짜 삽입 명령`InsertDateHandler.cs`을 사용할 수 있도록 합니다.

    ```cs
    protected override void Update(CommandInfo info)
    {
      info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
    }
    ```

14. 명령의 `Run` 메서드를 업데이트하여 날짜와 시간을 다음 코드로 삽입합니다.

    ``` cs
    protected override void Run () {
      var editor = IdeApp.Workbench.ActiveDocument.Editor;
      var date = DateTime.Now.ToString ();
      editor.InsertAtCaret (date);

    }
    ```

15. 마지막으로, 확장 패키지를 실행하여 테스트하겠습니다. Mac용 Visual Studio의 새 인스턴스에서 **편집 > 날짜 삽입**을 선택합니다. 아래 스크린샷과 같이 현재 날짜와 시간이 캐럿에 삽입됩니다.

    ![날짜 삽입 스크린샷](media/extending-visual-studio-mac-addin12.png)

## <a name="see-also"></a>참고 항목

- [첫 번째 확장 만들기(Windows의 Visual Studio)](/visualstudio/extensibility/extensibility-hello-world)