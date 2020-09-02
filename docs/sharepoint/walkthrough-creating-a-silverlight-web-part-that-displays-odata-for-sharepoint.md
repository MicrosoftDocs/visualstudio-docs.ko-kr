---
title: SharePoint 용 OData를 표시 하는 Silverlight 웹 파트 만들기
ms.date: 02/22/2017
ms.topic: how-to
f1_keywords:
- VS.SharePointTools.SPE.SilverlightWebPart
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 75653f0357bcc605e666ee271a527b616985b641
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "86017171"
---
# <a name="walkthrough-create-a-silverlight-web-part-that-displays-odata-for-sharepoint"></a>연습: SharePoint 용 OData를 표시 하는 Silverlight 웹 파트 만들기
  SharePoint 2010는 OData를 통해 목록 데이터를 노출 합니다. SharePoint에서 OData 서비스는 RESTful 서비스 ListData .svc에 의해 구현 됩니다. 이 연습에서는 Silverlight 응용 프로그램을 호스팅하는 SharePoint 웹 파트를 만드는 방법을 보여 줍니다. Silverlight 응용 프로그램은 ListData .svc를 사용 하 여 SharePoint 알림 목록 정보를 표시 합니다. 자세한 내용은 [SharePoint FOUNDATION REST 인터페이스](/previous-versions/office/developer/sharepoint-2010/ff521587(v=office.14)) 및 [Open Data Protocol](https://www.odata.org/)을 참조 하세요.

 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight 응용 프로그램 및 Silverlight 웹 파트 만들기
 먼저 Visual Studio에서 Silverlight 응용 프로그램을 만듭니다. Silverlight 응용 프로그램은 ListData. .svc 서비스를 사용 하 여 SharePoint 알림 목록에서 데이터를 검색 합니다.

> [!NOTE]
> 4.0 이전 버전의 Silverlight는 SharePoint 목록 데이터를 참조 하는 데 필요한 인터페이스를 지원 하지 않습니다.

#### <a name="to-create-a-silverlight-application-and-silverlight-web-part"></a>Silverlight 응용 프로그램 및 Silverlight 웹 파트를 만들려면

1. 메뉴 모음에서 **파일**  >  **새로 만들기**  >  **프로젝트** 를 선택 하 여 **새 프로젝트** 대화 상자를 표시 합니다.

2. **Visual c #** 또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. 템플릿 창에서 **SharePoint 2010 Silverlight 웹 파트** 템플릿을 선택 합니다.

4. **이름** 상자에 **slwebparttest** 를 입력 하 고 **확인** 단추를 선택 합니다.

    **SharePoint 사용자 지정 마법사** 대화 상자가 나타납니다.

5. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 사이트 정의를 디버깅할 SharePoint 서버 사이트의 URL을 입력 하거나 기본 위치 (http://<em>시스템 이름</em>/)를 사용 합니다.

6. **이 SharePoint 솔루션의 신뢰 수준을** 선택 하십시오. 섹션에서 **팜 솔루션으로 배포** 옵션 단추를 선택 합니다.

    이 예제에서는 팜 솔루션을 사용 하지만, Silverlight 웹 파트 프로젝트를 팜 또는 샌드박스가 적용 된 솔루션으로 배포할 수 있습니다. 샌드박스 솔루션과 팜 솔루션에 대 한 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

7. **Silverlight 구성 정보 지정** 페이지의 **silverlight 웹 파트를 연결 하는 방법** 섹션에서 **새 silverlight 프로젝트 만들기 및 웹 파트에 연결** 옵션 단추를 선택 합니다.

8. **이름을** **slapplication**으로 변경 하 고 **Language** 를 **Visual Basic** 또는 **Visual c #** 으로 설정한 후 **silverlight 버전** 을 **silverlight 4.0**로 설정 합니다.

9. **마침** 단추를 선택합니다. 프로젝트는 **솔루션 탐색기**표시 됩니다.

     이 솔루션에는 Silverlight 응용 프로그램 및 Silverlight 웹 파트의 두 프로젝트가 포함 되어 있습니다. Silverlight 응용 프로그램은 SharePoint에서 목록 데이터를 검색 및 표시 하 고 silverlight 웹 파트는 Silverlight 응용 프로그램을 호스트 하 여 SharePoint에서 볼 수 있도록 합니다.

## <a name="customize-the-silverlight-application"></a>Silverlight 응용 프로그램 사용자 지정
 Silverlight 응용 프로그램에 코드 및 디자인 요소를 추가 합니다.

#### <a name="to-customize-the-silverlight-application"></a>Silverlight 응용 프로그램을 사용자 지정 하려면

1. Silverlight 응용 프로그램에서 System.object에 대 한 어셈블리 참조를 추가 합니다. 자세한 내용은 [방법: 참조 추가 대화 상자를 사용 하 여 참조 추가 또는 제거](https://msdn.microsoft.com/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)를 참조 하세요.

2. **솔루션 탐색기**에서 **참조**에 대 한 바로 가기 메뉴를 열고 **서비스 참조 추가**를 선택 합니다.

    > [!NOTE]
    > Visual Basic를 사용 하는 경우 **솔루션 탐색기** 맨 위에 있는 **모든 파일 표시** 아이콘을 선택 하 여 **참조** 노드를 표시 해야 합니다.

3. **서비스 참조 추가** 대화 상자의 주소 상자에 SharePoint 사이트의 URL (예:)을 입력 하 **http://MySPSite** 고 **이동** 단추를 선택 합니다.

     Silverlight에서 SharePoint OData 서비스 ListData .svc를 찾으면 해당 주소를 전체 서비스 URL로 바꿉니다. 이 예제에서는가가 됩니다 http://myserver http://myserver/_vti_bin/ListData.svc .

4. **확인** 단추를 선택 하 여 프로젝트에 서비스 참조를 추가 하 고 기본 서비스 이름인 ServiceReference1를 사용 합니다.

5. 메뉴 모음에서 **빌드** > **솔루션 빌드**를 선택합니다.

6. SharePoint 서비스를 기반으로 프로젝트에 새 데이터 원본을 추가 합니다. 이렇게 하려면 메뉴 모음에서 **View**  >  **다른 Windows**  >  **데이터 원본**보기를 선택 합니다.

     **데이터 소스** 창에는 사용 가능한 모든 SharePoint 목록 데이터 (예: 작업, 알림 및 일정)가 표시 됩니다.

7. Silverlight 응용 프로그램에 알림 목록 데이터를 추가 합니다. **데이터 소스** 창에서 Silverlight designer로 "공지"를 끌어올 수 있습니다.

     이렇게 하면 SharePoint 사이트의 공지 목록에 바인딩된 그리드 컨트롤이 만들어집니다.

8. Silverlight 페이지에 맞게 표 형태 컨트롤의 크기를 조정 합니다.

9. Mainpage 코드 파일 (Visual c #의 경우 또는 Visual Basic*mainpage* )에서 다음 네임 스페이스 참조를 추가 합니다. *MainPage.xaml.vb*

    ```vb
    ' Add the following three Imports statements.
    Imports SLApplication.ServiceReference1
    Imports System.Windows.Data
    Imports System.Data.Services.Client
    ```

    ```csharp
    // Add the following three using directives.
    using SLApplication.ServiceReference1;
    using System.Windows.Data;
    using System.Data.Services.Client;
    ```

10. 클래스의 맨 위에 다음 변수 선언을 추가 합니다.

    ```vb
    Private context As TeamSiteDataContext
    Private myCollectionViewSource As CollectionViewSource
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()
    ```

    ```csharp
    private TeamSiteDataContext context;
    private CollectionViewSource myCollectionViewSource;
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();
    ```

11. 프로시저를 `UserControl_Loaded` 다음 코드로 바꿉니다.

    ```vb
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)
        ' The URL for the OData service.
        ' Replace <server name> in the next line with the name of your SharePoint server.
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))

        ' Do not load your data at design time.
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then
            'Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)
            announcements.LoadAsync(context.Announcements)
        End If
    End Sub
    ```

    ```csharp
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)
    {
        // The URL for the OData service.
        // Replace <server name> in the next line with the name of your
        // SharePoint server.
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));

        // Do not load your data at design time.
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))
        {
            //Load your data here and assign the results to the CollectionViewSource.
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);
            announcements.LoadAsync(context.Announcements);
        }
    }
    ```

     *ServerName* 자리 표시자를 SharePoint를 실행 하는 서버의 이름으로 바꾸어야 합니다.

12. 다음 오류 처리 프로시저를 추가 합니다.

    ```vb
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)
        ' Handle any errors.
        If e.[Error] Is Nothing Then
            myCollectionViewSource.Source = announcements
        Else
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))
        End If
    End Sub

    ```

    ```csharp
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)
    {
        // Handle any errors.
        if (e.Error == null)
        {
            myCollectionViewSource.Source = announcements;
        }
        else
        {
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));
        }
    }
    ```

## <a name="modify-the-silverlight-web-part"></a>Silverlight 웹 파트 수정
 Silverlight 디버깅을 사용 하도록 설정 하려면 Silverlight 웹 파트 프로젝트에서 속성을 변경 합니다.

#### <a name="to-modify-the-silverlight-web-part"></a>Silverlight 웹 파트를 수정 하려면

1. Silverlight 웹 파트 프로젝트 (**Slwebparttest**)에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

2. **속성** 창에서 **SharePoint** 탭을 선택 합니다.

3. 아직 선택 하지 않은 경우에는 **스크립트 디버깅 대신 Silverlight 디버깅 사용** 확인란을 선택 합니다.

4. 프로젝트를 저장합니다.

## <a name="test-the-silverlight-web-part"></a>Silverlight 웹 파트 테스트
 Sharepoint에서 새 Silverlight 웹 파트를 테스트 하 여 SharePoint 목록 데이터를 제대로 표시 하는지 확인 합니다.

#### <a name="to-test-the-silverlight-web-part"></a>Silverlight 웹 파트를 테스트 하려면

1. **F5** 키를 선택 하 여 SharePoint 솔루션을 빌드하고 실행 합니다.

2. SharePoint의 **사이트 작업** 메뉴에서 **새로 만들기 페이지**를 선택 합니다.

3. **새 페이지** 대화 상자에서 **SL 웹 파트 테스트**와 같은 제목을 입력 한 다음 **만들기** 단추를 선택 합니다.

4. 페이지 디자이너의 **편집 도구** 탭에서 **삽입**을 선택 합니다.

5. 탭 스트립에서 **웹 파트**를 선택 합니다.

6. **범주** 상자에서 **사용자 지정** 폴더를 선택 합니다.

7. **웹 파트** 목록에서 Silverlight 웹 파트를 선택한 다음 **추가** 단추를 선택 하 여 디자이너에 웹 파트를 추가 합니다.

8. 원하는 웹 페이지를 모두 추가한 후에는 **페이지** 탭을 선택 하 고 도구 모음에서 **& 닫기** 단추를 선택 합니다.

     이제 Silverlight 웹 파트는 SharePoint 사이트의 알림 데이터를 표시 해야 합니다. 기본적으로이 페이지는 SharePoint의 사이트 페이지 목록에 저장 됩니다.

    > [!NOTE]
    > 도메인 간에 Silverlight의 데이터에 액세스 하는 경우 Silverlight는 웹 응용 프로그램을 악용 하는 데 사용할 수 있는 보안 취약성을 방지 합니다. Silverlight에서 원격 데이터에 액세스할 때 문제가 발생 하면 [도메인 경계에서 서비스를 사용할 수 있도록 설정](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc197955(v=vs.95))을 참조 하세요.

## <a name="see-also"></a>추가 정보
- [SharePoint 용 웹 파트 만들기](../sharepoint/creating-web-parts-for-sharepoint.md)
- [SharePoint 솔루션 패키지 배포, 게시 및 업그레이드](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)
