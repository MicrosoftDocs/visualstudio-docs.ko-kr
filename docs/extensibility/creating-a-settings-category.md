---
title: 설정 범주 만들기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- profile settings, creating categories
ms.assetid: 97c88693-05ff-499e-8c43-352ee073dcb7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 03d50ca998efa034b1d4392c1fb7cecb8de8ed06
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85904018"
---
# <a name="create-a-settings-category"></a>설정 범주 만들기

이 연습에서는 Visual Studio 설정 범주를 만든 다음이를 사용 하 여 설정 파일에서 값을 저장 하 고 값을 복원 합니다. 설정 범주는 "사용자 지정 설정 지점"으로 표시 되는 관련 속성 그룹입니다. 즉, **설정 가져오기 및 내보내기** 마법사의 확인란을 선택 합니다. **도구** 메뉴에서 찾을 수 있습니다. 설정은 범주로 저장 되거나 복원 되며 개별 설정은 마법사에 표시 되지 않습니다. 자세한 내용은 [환경 설정](../ide/environment-settings.md)을 참조하세요.

클래스에서 파생 시켜 설정 범주를 만듭니다 <xref:Microsoft.VisualStudio.Shell.DialogPage> .

이 연습을 시작 하려면 먼저 [옵션 만들기 페이지](../extensibility/creating-an-options-page.md)의 첫 번째 섹션을 완료 해야 합니다. 결과 옵션 속성 표를 사용 하 여 범주의 속성을 검토 하 고 변경할 수 있습니다. 속성 범주를 설정 파일에 저장 한 후 파일을 검사 하 여 속성 값이 저장 되는 방법을 확인 합니다.

## <a name="prerequisites"></a>사전 요구 사항
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="create-a-settings-category"></a>설정 범주 만들기
 이 섹션에서는 사용자 지정 설정 지점을 사용 하 여 설정 범주의 값을 저장 하 고 복원 합니다.

### <a name="to-create-a-settings-category"></a>설정 범주를 만들려면

1. [옵션 만들기 페이지](../extensibility/creating-an-options-page.md)를 완료 합니다.

2. *VSPackage* 파일을 열고 다음 세 개의 문자열 리소스를 추가 합니다.

    |이름|값|
    |----------|-----------|
    |106|내 범주|
    |107|내 설정|
    |108|I 정수 및 기타 Float|

     이렇게 하면 범주의 이름을 "My Category", 개체 "My Settings" 및 category description "Tiinteger and o s o s"로 설정 하는 리소스가 생성 됩니다.

    > [!NOTE]
    > 이 세 가지 중에서 범주 이름만 **설정 가져오기 및 내보내기** 마법사에 표시 되지 않습니다.

3. *MyToolsOptionsPackage.cs*에서 `float` `OptionFloat` `OptionPageGrid` 다음 예제와 같이 라는 속성을 클래스에 추가 합니다.

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
    > `OptionPageGrid`이제 이름이 "My category" 인 범주가 및의 두 속성으로 구성 `OptionInteger` 됩니다 `OptionFloat` .

4. 를 <xref:Microsoft.VisualStudio.Shell.ProvideProfileAttribute> 클래스에 추가 `MyToolsOptionsPackage` 하 고 범주를 "내 범주"로 지정 하 고, ObjectName "my Settings"를 제공 하 고, isToolsOptionPage를 true로 설정 합니다. CategoryResourceID, objectNameResourceID 및 설명 Resourceid를 앞에서 만든 해당 문자열 리소스 Id로 설정 합니다.

    ```csharp
    [ProvideProfileAttribute(typeof(OptionPageGrid),
        "My Category", "My Settings", 106, 107, isToolsOptionPage:true, DescriptionResourceID = 108)]
    ```

5. 프로젝트를 빌드하고 디버깅을 시작합니다. 실험적 인스턴스에서 이제 **내 그리드 페이지** 에 정수 및 부동 소수점 값이 모두 포함 되어 있음을 확인 해야 합니다.

## <a name="examine-the-settings-file"></a>설정 파일 검사
 이 섹션에서는 속성 범주 값을 설정 파일로 내보냅니다. 파일을 검사 하 고 값을 다시 속성 범주로 가져옵니다.

1. **F5**키를 눌러 디버그 모드에서 프로젝트를 시작 합니다. 그러면 실험적 인스턴스가 시작 됩니다.

2. **도구**  >  **옵션** 대화 상자를 엽니다.

3. 왼쪽 창의 트리 뷰에서 **내 범주** 를 확장 한 다음 **내 그리드 페이지**를 클릭 합니다.

4. Tifloat 값을 **OptionFloat** 3.1416로 변경 하 고,을 **정수** 를 12로 변경 합니다. **확인**을 클릭합니다.

5. **도구** 메뉴에서 **설정 가져오기 및 내보내기**를 선택합니다.

     **설정 가져오기 및 내보내기** 마법사가 나타납니다.

6. **선택한 환경 설정 내보내기** 가 선택 되어 있는지 확인 하 고 **다음**을 클릭 합니다.

     **내보낼 설정 선택** 페이지가 나타납니다.

7. **내 설정**을 클릭 합니다.

     **Description은 Description** **정수 및 기타 float**로 변경 됩니다.

8. **내 설정** 이 선택 된 유일한 범주 인지 확인 하 고 **다음**을 클릭 합니다.

     **설정 파일 이름** 페이지가 나타납니다.

9. 새 설정 파일의 이름을 *Mysettings* 로 설정 하 고 해당 디렉터리에 저장 합니다. **Finish**를 클릭합니다.

     **내보내기 완료** 페이지에서 설정을 성공적으로 내보냈습니다.

10. **파일** 메뉴에서 **열기**를 가리킨 다음 **파일**을 클릭합니다. *Mysettings* 를 찾아 엽니다.

     파일의 다음 섹션에서 내보낸 속성 범주 (Guid는 다름)를 찾을 수 있습니다.

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

     전체 범주 이름은 범주 이름에 밑줄을 추가 하 고 그 뒤에 개체 이름을 추가 하 여 구성 됩니다. 기타 Float 및 to Integer는 내보낸 값과 함께 범주에 표시 됩니다.

11. 설정 파일을 변경 하지 않고 닫습니다.

12. **도구** 메뉴에서 **옵션**을 클릭 하 고 **내 범주**를 확장 한 **다음 내 그리드 페이지** 를 클릭 하 고 옵션의 **값을 1.0로,** 옵션 **integer** 를 1로 변경 합니다. **확인**을 클릭합니다.

13. **도구** 메뉴에서 **설정 가져오기 및 내보내기**를 클릭 하 고 **선택한 환경 설정 가져오기**를 선택한 후 **다음**을 클릭 합니다.

     **현재 설정 저장** 페이지가 나타납니다.

14. **아니요, 새 설정을 가져옵니다 .를** 선택 하 고 **다음**을 클릭 합니다.

     **가져올 설정 컬렉션 선택** 페이지가 나타납니다.

15. 트리 뷰의 **내 설정** 노드에서 *mysettings .vssettings* 파일을 선택 합니다. 파일이 트리 뷰에 표시 되지 않는 경우 **찾아보기** 를 클릭 하 여 찾습니다. **다음**을 클릭합니다.

     **가져올 설정 선택** 대화 상자가 나타납니다.

16. **내 설정** 이 선택 되어 있는지 확인 하 고 **마침**을 클릭 합니다. **가져오기 완료** 페이지가 표시 되 면 **닫기**를 클릭 합니다.

17. **도구** 메뉴에서 **옵션**을 클릭 하 고 **내 범주**를 확장 한 다음 **내 그리드 페이지** 를 클릭 하 고 속성 범주 값이 복원 되었는지 확인 합니다.
