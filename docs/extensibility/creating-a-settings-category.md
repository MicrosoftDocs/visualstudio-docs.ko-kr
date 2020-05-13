---
title: 설정 범주 만들기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5f4b2fa9d82181d0eb899bf9680e8a9debd6c50b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739612"
---
# <a name="create-a-settings-category"></a>설정 범주 만들기

이 연습에서는 Visual Studio 설정 범주를 만들고 이를 사용하여 설정 파일에서 값을 저장하고 복원합니다. 설정 범주는 "사용자 지정 설정 지점"으로 표시되는 관련 속성의 그룹입니다. 즉, **가져오기 및 내보내기 설정** 마법사의 확인란으로 표시됩니다. 도구 **메뉴에서** 찾을 수 있습니다. 설정은 범주로 저장되거나 복원되며 개별 설정은 마법사에 표시되지 않습니다. 자세한 내용은 [환경 설정](../ide/environment-settings.md)을 참조하세요.

클래스에서 파생하여 설정 범주를 <xref:Microsoft.VisualStudio.Shell.DialogPage> 만듭니다.

이 연습을 시작하려면 먼저 옵션 만들기 [페이지의](../extensibility/creating-an-options-page.md)첫 번째 섹션을 완료해야 합니다. 결과 옵션 속성 그리드를 사용하면 범주의 속성을 검사하고 변경할 수 있습니다. 설정 파일에 속성 범주를 저장한 후 파일을 검사하여 속성 값이 저장되는 방식을 확인합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015부터는 다운로드 센터에서 Visual Studio SDK를 설치하지 않습니다. 시각적 스튜디오 설정에서 선택적 기능으로 포함됩니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="create-a-settings-category"></a>설정 범주 만들기
 이 섹션에서는 사용자 지정 설정 점을 사용하여 설정 범주의 값을 저장하고 복원합니다.

### <a name="to-create-a-settings-category"></a>설정 범주를 만들려면

1. 옵션 [만들기 페이지를](../extensibility/creating-an-options-page.md)완료합니다.

2. *VSPackage.resx* 파일을 열고 다음 세 가지 문자열 리소스를 추가합니다.

    |이름|값|
    |----------|-----------|
    |106|내 카테고리|
    |107|내 설정|
    |108|옵션인테이거 및 옵션플로|

     이렇게 하면 범주 "내 범주", 개체 "내 설정", 범주 설명 "OptionInteger 및 OptionFloat"의 이름을 지정하는 리소스가 만들어집니다.

    > [!NOTE]
    > 이 세 가지 중 가져오기 **및 내보내기 설정** 마법사에는 범주 이름만 나타나지 않습니다.

3. *MyToolsOptionsPackage.cs*다음 `float` 예제와 `OptionFloat` 같이 `OptionPageGrid` 클래스에 명명된 속성을 추가합니다.

    ```csharp
    public class OptionPageGrid : DialogPage
    {
        private int optionInt = 256;
        private float optionFloat = 3.14F;

        [Category("My Options")]
        [DisplayName("My Integer option")]
        [Description("My integer option")]
        public int OptionInteger
        {
            get { return optionInt; }
            set { optionInt = value; }
        }
        [Category("My Options")]
        [DisplayName("My Float option")]
        [Description("My float option")]
        public float OptionFloat
        {
            get { return optionFloat; }
            set { optionFloat = value; }
        }
    }
    ```

    > [!NOTE]
    > "내 범주"라는 범주는 `OptionPageGrid` 이제 두 `OptionInteger` 속성및 `OptionFloat`.

4. 클래스에 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> `MyToolsOptionsPackage` a를 추가하고 범주 이름 "내 범주"를 지정하고 개체 이름 "내 설정"을 지정하고 setisToolsOptionPage를 true로 설정합니다. 범주ResourceID, objectNameResourceID 및 설명ResourceID를 이전에 만든 해당 문자열 리소스 ID로 설정합니다.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 내 **그리드 페이지에** 정수 및 부동 값이 모두 있음을 알 수 있습니다.

## <a name="examine-the-settings-file"></a>설정 파일 검사
 이 섹션에서는 속성 범주 값을 설정 파일로 내보냅니다. 파일을 검사한 다음 값을 속성 범주로 다시 가져옵니다.

1. **F5를**눌러 디버그 모드에서 프로젝트를 시작합니다. 그러면 실험 인스턴스가 시작됩니다.

2. **도구** > **옵션** 대화 상자를 엽니다.

3. 왼쪽 창의 트리 보기에서 **내 범주를** 확장한 다음 **내 그리드 페이지를 클릭합니다.**

4. **옵션플로의** 값을 3.1416으로 변경하고 **옵션인테이거를** 12로 변경합니다. **확인**을 클릭합니다.

5. **도구** 메뉴에서 **설정 가져오기 및 내보내기**를 선택합니다.

     **가져오기 및 내보내기 설정 마법사가** 나타납니다.

6. 선택한 **환경 설정 내보내기를** 선택한 다음 **다음을**클릭합니다.

     **내보낼 설정 선택** 페이지가 나타납니다.

7. **내 설정을**클릭합니다.

     **설명이** **옵션인테이거 및 옵션플로로**변경됩니다.

8. **내 설정이** 선택된 유일한 범주인지 확인한 다음 **다음**을 클릭합니다.

     **설정 파일 이름 페이지가** 나타납니다.

9. 새 설정 파일 *MySettings.vssettings의* 이름을 지정하고 적절한 디렉토리에 저장합니다. **Finish**를 클릭합니다.

     **완료 내보내기** 페이지에서 설정이 성공적으로 내보냈다고 보고합니다.

10. **파일** 메뉴에서 **열기**를 가리킨 다음 **파일**을 클릭합니다. *MySettings.vs 설정을* 찾아 엽니다.

     내보낸 속성 범주는 파일의 다음 섹션에서 찾을 수 있습니다(GUID는 다를 수 있음).

    ```
    <Category name="My Category_My Settings"
          Category="{4802bc3e-3d9d-4591-8201-23d1a05216a6}"
          Package="{6bb6942e-014c-489e-a612-a935680f703d}"
          RegisteredName="My Category_My Settings">
          PackageName="MyToolsOptionsPackage">
       <PropertyValue name="OptionFloat">3.1416</PropertyValue>
       <PropertyValue name="OptionInteger">12</PropertyValue>
    </Category>
    ```

     전체 범주 이름은 범주 이름에 밑줄이 추가되고 개체 이름이 추가되어 형성됩니다. OptionFloat 및 OptionInteger는 내보낸 값과 함께 범주에 나타납니다.

11. 설정 파일을 변경하지 않고 닫습니다.

12. **도구** 메뉴에서 **옵션을**클릭하고 **내 범주를**확장하고 **내 그리드 페이지를** 클릭한 다음 **OptionFloat** 값을 1.0으로 변경하고 **OptionInteger를** 1로 변경합니다. **확인**을 클릭합니다.

13. **도구** 메뉴에서 **설정 가져오기를 클릭하고** **선택한 환경 설정 가져오기를**선택한 다음 다음 을 **클릭합니다.**

     **현재 설정 저장 페이지가** 나타납니다.

14. **아니요를** 선택하고 새 설정을 가져온 다음 **다음을**클릭합니다.

     **가져올 설정 모음 선택** 페이지가 나타납니다.

15. 트리 뷰의 **내 설정** 노드에서 *MySettings.vssettings* 파일을 선택합니다. 파일이 트리 보기에 나타나지 않으면 **찾아보기를** 클릭하고 찾습니다. **다음**을 클릭합니다.

     **가져올 설정 선택** 대화 상자가 나타납니다.

16. **내 설정이** 선택되어 있는지 확인한 다음 **완료를 클릭합니다.** 가져오기 완료 페이지가 나타나면 **닫기**를 **클릭합니다.**

17. **도구** 메뉴에서 **옵션을**클릭하고 **내 범주를**확장하고 **내 그리드 페이지를** 클릭하고 속성 범주 값이 복원되었는지 확인합니다.
