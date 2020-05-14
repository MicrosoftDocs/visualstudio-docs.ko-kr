---
title: '연습: 시작 페이지에 사용자 지정 XAML 추가 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
monikerRange: vs-2017
ms.openlocfilehash: 4e2afc90dc96978e8a8290afaa2d3278e8b621b3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697686"
---
# <a name="walkthrough-add-custom-xaml-to-the-start-page"></a>연습: 시작 페이지에 사용자 지정 XAML 추가

이 연습에서는 웹 브라우저가 포함된 사용자 지정 Visual Studio 시작 페이지를 만드는 방법을 보여 주며, 이 연습에서는 웹 브라우저가 포함되어 있습니다.

## <a name="add-custom-xaml"></a>사용자 지정 XAML 추가

1. 사용자 지정 시작 페이지 [만들기의](../extensibility/creating-a-custom-start-page.md)지침에 따라 시작 페이지를 만듭니다.

2. *MainWindow.xaml* 파일에서 \<그리드> 섹션을 찾습니다.

3. 다음 \<예제와 같이 \< Grid \<> 요소 내에 TabControl> 요소와 TabItem> 추가합니다.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

4. 새 프로젝트를 \<여는 \<단추> 요소를 함께 두 번째 TabItem> 추가합니다.

    ```xml
    <Grid>
        <TabControl>
            <TabItem Header="MyButton" Height="Auto">
                <Button Name="btnNewProj" Content="New Project"
                    Command="{x:Static vscom:VSCommands.ExecuteCommand}"
                    CommandParameter="File.NewProject" >
                </Button>
            </TabItem>
            <TabItem Header="Bing" Height="Auto">
                <Frame Source="http://www.bing.com" />
            </TabItem>
        </TabControl>
    </Grid>
    ```

## <a name="test-the-custom-start-page"></a>사용자 지정 시작 페이지 테스트

1. **F5**키를 누릅니다.

     사용자 지정 시작 페이지가 설치되었지만 선택되지 않은 Visual Studio의 실험 인스턴스가 열립니다.

2. Visual Studio의 실험 인스턴스에서 **도구 /옵션/ 환경** 페이지를 엽니다.

3. **시작**을 선택합니다. 사용자 **지정 시작 페이지** 목록에서 *.xaml* 파일을 선택하고 **확인을**클릭합니다.

4. **보기** 메뉴에서 **시작 페이지**를 클릭합니다.

5. **Bing** 탭을 클릭합니다.

     Bing 웹 페이지가 표시됩니다.

6. 내 단추 탭을 **클릭합니다.**

     **새 프로젝트** 대화 상자를 여는 **MyProject** 버튼이 표시됩니다.

7. 실험 인스턴스를 닫습니다.

사용자 지정 시작 페이지를 적용하려면 **도구** > **옵션** > **환경에서** **시작**을 선택합니다. 사용자 **지정 시작 페이지** 목록에서 *.xaml* 파일을 선택하고 **확인을**클릭합니다.

## <a name="next-steps"></a>다음 단계

이제 Visual Studio 시작 페이지에 웹 브라우저 탭과 MyButton 탭이 표시되는 탭이 포함되어 있습니다. [시작 페이지에 사용자 컨트롤 추가에](../extensibility/adding-user-control-to-the-start-page.md)표시된 것처럼 코드 *숨는* 모델을 사용하여 사용자 지정 .dll을 추가하여 다른 기능이 있는 사용자 지정 시작 페이지를 만들 수 있습니다. 결과 .vsix 파일을 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트 또는 다른 웹 사이트 또는 네트워크 공유에 게시하여 사용자 지정 시작 페이지를 다른 사용자와 공유할 수 있습니다. 자세한 내용은 [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md)을 참조하세요.

## <a name="see-also"></a>참조

- [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)
- [WPF 컨테이너 컨트롤](https://msdn.microsoft.com/library/a0177167-d7db-4205-9607-8ae316952566)
