---
title: '연습: 시작 페이지에 사용자 지정 XAML 추가 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- custom start page
- xaml start page
ms.assetid: 9af4d5f9-1cfc-4221-aea7-c8cd3f7571a6
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7b2de492bd1eddf4bf18e4824cdb64de4241fa5f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65674120"
---
# <a name="walkthrough-adding-custom-xaml-to-the-start-page"></a>연습: 시작 페이지에 사용자 지정 XAML 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 웹 브라우저가 포함 된 사용자 지정 Visual Studio 시작 페이지를 만드는 방법을 보여 줍니다.  
  
## <a name="adding-custom-xaml"></a>사용자 지정 XAML 추가  
  
1. [사용자 지정 시작 페이지 만들기](../extensibility/creating-a-custom-start-page.md)의 지침에 따라 시작 페이지를 만듭니다.  
  
2. Mainwindow.xaml 파일에서 섹션을 찾습니다 \<Grid> .  
  
3. \<TabControl> \<TabItem> 다음 예제와 같이 요소 내에 요소와을 추가 \< Grid> 합니다.  
  
    ```xml  
    <Grid>  
        <TabControl>  
            <TabItem Header="Bing" Height="Auto">  
                <Frame Source="http://www.bing.com" />  
            </TabItem>  
        </TabControl>  
    </Grid>  
    ```  
  
4. 새 프로젝트를 여는 요소를 사용 하 여 두 번째를 추가 합니다 \<TabItem> \<Button> .  
  
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
  
## <a name="testing-the-custom-start-page"></a>사용자 지정 시작 페이지 테스트  
  
1. F5 키를 누릅니다.  
  
     사용자 지정 시작 페이지가 설치 되었지만 선택 되지 않은 상태로 Visual Studio의 실험적 인스턴스가 열립니다.  
  
2. Visual Studio의 실험적 인스턴스에서 **Tools/Options/Environment** 페이지를 엽니다.  
  
3. **시작**을 선택 합니다. **시작 페이지 사용자 지정** 목록에서 .xaml 파일을 선택 하 고 **확인**을 클릭 합니다.  
  
4. **보기** 메뉴에서 **시작 페이지**를 클릭합니다.  
  
5. **Bing** 탭을 클릭 합니다.  
  
     Bing 웹 페이지가 표시 되어야 합니다.  
  
6. **MyButton** 탭을 클릭 합니다.  
  
     **새 프로젝트** 대화 상자를 여는 **MyProject** 단추가 표시 되어야 합니다.  
  
7. 실험적 인스턴스를 닫습니다.  
  
## <a name="applying-the-custom-start-page"></a>사용자 지정 시작 페이지 적용  
  
#### <a name="to-test-the-custom-start-page"></a>사용자 지정 시작 페이지를 테스트 하려면  
  
1. **도구/옵션/환경**에서 **시작**을 선택 합니다. **시작 페이지 사용자 지정** 목록에서 .xaml 파일을 선택 하 고 **확인**을 클릭 합니다.  
  
## <a name="next-steps"></a>다음 단계  
 이제 Visual Studio 시작 페이지에는 웹 브라우저 탭과 MyButton 탭을 표시 하는 탭이 포함 되어 있습니다. [사용자 정의 컨트롤을 시작 페이지에 추가](../extensibility/adding-user-control-to-the-start-page.md)하는 것과 같이 *코드 숨김이* 포함 된 모델을 사용 하 여 사용자 지정 .dll을 추가 하 여 다른 기능이 있는 사용자 지정 시작 페이지를 만들 수 있습니다. 결과 .vsix 파일을 [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 웹 사이트 또는 다른 웹 사이트 또는 네트워크 공유에 게시 하 여 사용자 지정 시작 페이지를 다른 사용자와 공유할 수 있습니다. 자세한 내용은 [Deploying Custom Start Pages](../extensibility/deploying-custom-start-pages.md)을 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [시작 페이지 사용자 지정](../ide/customizing-the-start-page-for-visual-studio.md)   
 [WPF 컨테이너 컨트롤](https://msdn.microsoft.com/a0177167-d7db-4205-9607-8ae316952566)
