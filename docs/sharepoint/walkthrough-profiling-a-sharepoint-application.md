---
title: '연습: SharePoint 응용 프로그램 프로 파일링 | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 27024f3b28b97a1a5d0befc3d70dbf8144fb9e24
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277655"
---
# <a name="walkthrough-profile-a-sharepoint-application"></a>연습: SharePoint 응용 프로그램 프로 파일링
  이 연습에서는 Visual Studio에서 프로파일링 도구를 사용하여 SharePoint 애플리케이션의 성능을 최적화하는 방법을 보여 줍니다. 예제 애플리케이션은 기능 이벤트 수신기의 성능을 저하시키는 유휴 루프가 포함된 SharePoint 기능 이벤트 수신기입니다. Visual Studio profiler를 사용 하면 프로젝트의 가장 비용이 많이 드는 (가장 느리게 수행 되는) 부분을 찾아서 제거할 수 있습니다 (실행 *부하 과다 경로*라고도 함).

 이 연습에서는 다음 작업을 수행합니다.

- [기능 및 기능 이벤트 수신기를 추가](#add-a-feature-and-feature-event-receiver)합니다.

- [SharePoint 응용 프로그램을 구성 하 고 배포](#configure-and-deploy-the-sharepoint-application)합니다.

- [SharePoint 응용 프로그램을 실행](#run-the-sharepoint-application)합니다.

- [프로필 결과를 확인 하 고 해석](#view-and-interpret-the-profile-results)합니다.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 조건
 이 연습을 완료하려면 다음 구성 요소가 필요합니다.

- 지원되는 Microsoft Windows 및 SharePoint 버전.

- [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].

## <a name="create-a-sharepoint-project"></a>SharePoint 프로젝트 만들기
 먼저 SharePoint 프로젝트를 만듭니다.

### <a name="to-create-a-sharepoint-project"></a>SharePoint 프로젝트를 만들려면

1. 메뉴 모음에서 **파일** > **새** > **프로젝트** 를 선택 하 여 **새 프로젝트** 대화 상자를 표시 합니다.

2. **시각적 개체 C#**  또는 **Visual Basic**에서 **SharePoint** 노드를 확장 한 다음 **2010** 노드를 선택 합니다.

3. 템플릿 창에서 **SharePoint 2010 프로젝트** 템플릿을 선택 합니다.

4. **이름** 상자에 **ProfileTest**를 입력 하 고 **확인** 단추를 선택 합니다.

    **SharePoint 사용자 지정 마법사** 가 나타납니다.

5. **디버깅에 사용할 사이트 및 보안 수준 지정** 페이지에서 사이트 정의를 디버깅할 SharePoint 서버 사이트의 URL을 입력 하거나 기본 위치 (http://<em>시스템 이름</em>/)를 사용 합니다.

6. **이 SharePoint 솔루션의 신뢰 수준을** 선택 하십시오. 섹션에서 **팜 솔루션으로 배포** 옵션 단추를 선택 합니다.

    현재 팜 솔루션만 프로파일링할 수 있습니다. 샌드박스 솔루션과 팜 솔루션에 대 한 자세한 내용은 [샌드박스 솔루션 고려 사항](../sharepoint/sandboxed-solution-considerations.md)을 참조 하세요.

7. **마침** 단추를 선택합니다. 프로젝트가 **솔루션 탐색기**에 나타납니다.

## <a name="add-a-feature-and-feature-event-receiver"></a>기능 및 기능 이벤트 수신기 추가
 다음 작업으로, 기능의 이벤트 수신기와 함께 프로젝트에 기능을 추가합니다. 이 이벤트 수신기에는 프로파일링할 코드가 포함됩니다.

### <a name="to-add-a-feature-and-feature-event-receiver"></a>기능 및 기능 이벤트 수신기를 추가하려면

1. **솔루션 탐색기**에서 **기능** 노드에 대 한 바로 가기 메뉴를 열고 **기능 추가**를 선택한 다음 이름을 기본값 **Feature1**로 둡니다.

2. **솔루션 탐색기**에서 **Feature1**의 바로 가기 메뉴를 열고 **이벤트 수신기 추가**를 선택 합니다.

     주석 처리된 몇 가지 이벤트 처리기가 포함된 코드 파일이 기능에 추가되고 편집할 수 있도록 열립니다.

3. 이벤트 수신기 클래스에서 다음 변수 선언을 추가합니다.

    ```vb
    ' SharePoint site/subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site/subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

4. `FeatureActivated` 프로시저를 다음 코드로 바꿉니다.

    ```vb
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add a new announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    ' Waste some time.
                    TimeCounter()
                    ' Update the list.
                    listItem.Update()
                End Using
            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try
    End Sub
    ```

    ```csharp
    public override void FeatureActivated(SPFeatureReceiverProperties properties)
    {
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add a new announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +
    DateTime.Now.ToString();
                    // Waste some time.
                    TimeCounter();
                    // Update the list.
                    listItem.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

5. `FeatureActivated`프로시저 아래에 다음 프로시저를 추가 합니다.

    ```vb

    Public Sub TimeCounter()
        Dim result As Integer
        For i As Integer = 0 To 99999
            For j As Integer = 0 To 9999
                result = i * j
            Next j
        Next i
    End Sub
    ```

    ```csharp
    public void TimeCounter()
    {
        for (int i = 0; i < 100000; i++)
        {
            for (int j = 0; j < 10000; j++)
            {
                int result = i * j;
            }
        }
    }
    ```

6. **솔루션 탐색기**에서 프로젝트 (**ProfileTest**)에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.

7. **속성** 대화 상자에서 **SharePoint** 탭을 선택 합니다.

8. **활성 배포 구성** 목록에서 **활성화 안 함**을 선택 합니다.

     이 배포 구성을 선택하면 SharePoint에서 나중에 기능을 수동으로 활성화할 수 있습니다.

9. 프로젝트를 저장합니다.

## <a name="configure-and-deploy-the-sharepoint-application"></a>SharePoint 응용 프로그램 구성 및 배포
 SharePoint 프로젝트가 준비되었으므로 이 프로젝트를 구성하고 SharePoint 서버에 배포합니다.

### <a name="to-configure-and-deploy-the-sharepoint-application"></a>SharePoint 애플리케이션을 구성하고 배포하려면

1. **분석** 메뉴에서 **성능 마법사 시작**을 선택 합니다.

2. **성능 마법사**의 1 페이지에서 프로 파일링 방법을 **CPU 샘플링** 으로 유지 하 고 **다음** 단추를 선택 합니다.

     다른 프로파일링 방법은 고급 프로파일링 상황에서 사용할 수 있습니다. 자세한 내용은 [성능 컬렉션 메서드 이해](../profiling/understanding-performance-collection-methods.md)를 참조하세요.

3. **성능 마법사**의 두 페이지에서 프로필 대상을 **ProfileTest** 로 두고 **다음** 단추를 선택 합니다.

     솔루션에 여러 프로젝트가 있는 경우 해당 프로젝트가 이 목록에 나타납니다.

4. **성능 마법사**의 세 번째 페이지에서 **계층 상호 작용 프로 파일링 사용** 확인란의 선택을 취소 하 고 **다음** 단추를 선택 합니다.

     TIP(계층 상호 작용 프로파일링) 기능은 데이터베이스를 쿼리하는 애플리케이션의 성능을 측정하고 웹 페이지가 요청된 횟수를 표시하는 데 유용합니다. 해당 데이터가 이 예제에 필요하지 않기 때문에 이 기능을 사용하도록 설정하지 않을 것입니다.

5. **성능 마법사**의 4 페이지에서 **마법사를 완료 한 후 프로 파일링 시작** 확인란을 선택 된 상태로 두고 **마침** 단추를 선택 합니다.

     마법사는 서버에서 응용 프로그램 프로 파일링을 사용 하도록 설정 하 고 **성능 탐색기** 창을 표시 한 다음 SharePoint 응용 프로그램을 빌드, 배포 및 실행 합니다.

## <a name="run-the-sharepoint-application"></a>SharePoint 응용 프로그램 실행
 SharePoint에서 기능을 활성화하여 `FeatureActivation` 이벤트 코드가 실행되도록 합니다.

### <a name="to-run-the-sharepoint-application"></a>SharePoint 애플리케이션을 실행하려면

1. SharePoint에서 **사이트 작업** 메뉴를 열고 **사이트 설정**을 선택 합니다.

2. **사이트 작업** 목록에서 **사이트 기능 관리** 링크를 선택 합니다.

3. **기능** 목록에서 **ProfileTest Feature1**옆에 있는 **활성화** 단추를 선택 합니다.

     유휴 루프가 `FeatureActivated` 함수에서 호출되기 때문에 이 작업을 수행할 때 일시 중지됩니다.

4. **빠른 실행** 모음에서 **목록** 을 선택한 다음 목록 목록에서 **공지**를 **선택 합니다.**

     기능이 활성화되었다는 새 알림이 목록에 추가되었음을 확인합니다.

5. SharePoint 사이트를 닫습니다.

     SharePoint를 닫은 후 프로파일러는 샘플 프로 파일링 보고서를 만들어 표시 하 고 **ProfileTest** 프로젝트의 폴더에 .vsp 파일로 저장 합니다.

## <a name="view-and-interpret-the-profile-results"></a>프로필 결과 보기 및 해석
 SharePoint 애플리케이션을 실행하고 프로파일링했으므로 테스트 결과를 확인합니다.

### <a name="to-view-and-interpret-the-profile-results"></a>프로필 결과를 보고 해석 하려면

1. 샘플 프로 파일링 보고서의 **개별 작업을 수행** 하는 함수 섹션에서 `TimeCounter`가 목록의 맨 위에 있는지 확인 합니다.

     이 위치는 `TimeCounter`가 샘플이 가장 많은 함수 중 하나이므로 애플리케이션에서 가장 큰 성능 병목 지점 중 하나임을 나타냅니다. 그러나 이 상황은 예시 목적으로 그렇게 의도적으로 설계되었기 때문에 놀라운 것은 아닙니다.

2. **개별 작업을 수행** 하는 함수 섹션에서 `ProcessRequest` 링크를 선택 하 여 `ProcessRequest` 함수의 비용 분포를 표시 합니다.

     `ProcessRequest`에 대 한 **호출 된 함수** 섹션에서 가장 비용이 많이 드는 호출 된 함수로 **FeatureActiviated** 함수가 나열 되어 있는지 확인 합니다.

3. 호출 된 **함수** 섹션에서 **featureactivated** 됨 단추를 선택 합니다.

     **Featureactivated**의 **호출 된 함수** 섹션에서 `TimeCounter` 함수는 가장 비용이 많이 드는 호출 된 함수로 나열 됩니다. **함수 코드 뷰** 창에서 강조 표시 된 코드 (`TimeCounter`)는 핫스폿이 며 수정이 필요한 위치를 나타냅니다.

4. 샘플 프로파일링 보고서를 닫습니다.

     언제 든 지 보고서를 다시 보려면 **성능 탐색기** 창에서 .vsp 파일을 엽니다.

## <a name="fix-the-code-and-reprofile-the-application"></a>코드를 수정 하 고 응용 프로그램을 다시 프로 파일링 합니다.
 SharePoint 애플리케이션의 핫 스폿 함수가 식별되었으므로 해당 함수를 수정합니다.

### <a name="to-fix-the-code-and-reprofile-the-application"></a>코드를 수정하고 애플리케이션을 다시 프로파일링하려면

1. 기능 이벤트 수신기 코드의 `TimeCounter`에서 `FeatureActivated` 메서드 호출을 주석으로 처리하여 호출되지 않도록 합니다.

2. 프로젝트를 저장합니다.

3. **성능 탐색기**에서 대상 폴더를 연 다음 **ProfileTest** 노드를 선택 합니다.

4. **성능 탐색기** 도구 모음에 있는 **작업** 탭에서 **프로 파일링 시작** 단추를 선택 합니다.

     응용 프로그램을 다시 프로 파일링 하기 전에 프로 파일링 속성을 변경 하려면 **성능 마법사 시작** 단추를 대신 선택 합니다.

5. 이 항목의 앞부분에 나오는 **SharePoint 응용 프로그램을 실행** 하는 방법 섹션의 지침을 따르세요.

     유휴 루프 호출이 제거되었으므로 기능이 훨씬 빠르게 활성화됩니다. 샘플 프로파일링 보고서는 이를 반영합니다.

## <a name="see-also"></a>참고 항목
- [성능 세션 개요](../profiling/performance-session-overview.md)
- [초보자를 위한 성능 프로파일링 지침](../profiling/beginners-guide-to-performance-profiling.md)
- [Visual Studio Profiler를 사용 하 여 응용 프로그램 병목 상태 찾기](https://msdn.microsoft.com/magazine/cc337887.aspx)
