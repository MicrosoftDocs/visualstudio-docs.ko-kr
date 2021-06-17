---
title: IntelliTrace를 사용하여 SharePoint 애플리케이션 디버그
description: IntelliTrace를 사용하여 SharePoint 애플리케이션을 보다 쉽게 디버그하고 수정할 수 있습니다. 기능 수신기에 코드를 만들고 추가합니다. 프로젝트를 테스트합니다. IntelliTrace 데이터를 수집합니다.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- IntelliTrace [SharePoint development in Visual Studio]
- standalone data collector
- SharePoint development in Visual Studio, IntelliTrace
- data collector
- IntelliTrace
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: cf7fa6c7255e05c465d6c209db5e9581a49aee64
ms.sourcegitcommit: 1f27f33852112702ee35fbc0c02fba37899e4cf5
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/15/2021
ms.locfileid: "112112839"
---
# <a name="walkthrough-debug-a-sharepoint-application-by-using-intellitrace"></a>연습: IntelliTrace를 사용하여 SharePoint 애플리케이션 디버그

IntelliTrace를 사용하면 SharePoint 솔루션을 더 쉽게 디버그할 수 있습니다. 기존 디버거는 현재 솔루션의 스냅샷만 제공합니다. 그러나 IntelliTrace를 사용하여 솔루션에서 발생한 과거 이벤트와 발생한 컨텍스트를 검토하고 코드로 이동할 수 있습니다.

 이 연습에서는 Microsoft Monitoring Agent 사용하여 배포된 애플리케이션에서 IntelliTrace 데이터를 수집하여 Visual Studio SharePoint 프로젝트를 디버그하는 방법을 보여줍니다. 해당 데이터를 분석하려면 Visual Studio Enterprise 사용해야 합니다. 이 프로젝트는 기능이 활성화될 때 작업 목록에 작업을 추가하고 공지 목록에 공지하는 기능 수신기를 통합합니다. 기능이 비활성화되면 작업이 완료된 것으로 표시되고 두 번째 알림이 알림 목록에 추가됩니다. 그러나 프로시저에는 프로젝트가 올바르게 실행되지 않도록 하는 논리적 오류가 포함되어 있습니다. IntelliTrace를 사용하면 오류를 찾아서 수정할 수 있습니다.

 **적용된 내용:** 이 항목의 정보는 Visual Studio 만든 SharePoint 솔루션에 적용됩니다.

 이 연습에서는 다음 작업을 수행합니다.

- [기능 수신기 만들기](#create-a-feature-receiver)

- [기능 수신기에 코드 추가](#add-code-to-the-feature-receiver)

- [프로젝트 테스트](#test-the-project)

- [Microsoft Monitoring Agent 사용하여 IntelliTrace 데이터 수집](#collect-intellitrace-data-by-using-microsoft-monitoring-agent)

- [SharePoint 솔루션 디버그 및 수정](#debug-and-fix-the-sharepoint-solution)

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- 지원되는 Windows 및 SharePoint 버전.

- Visual Studio Enterprise.

## <a name="create-a-feature-receiver"></a>기능 수신기 만들기

먼저 기능 수신기가 있는 빈 SharePoint 프로젝트를 만듭니다.

1. 설치한 SharePoint 버전을 대상으로 하는 SharePoint 솔루션 프로젝트를 만들고 이름을 **IntelliTraceTest로** 지정합니다.

     프로젝트에 대한 SharePoint 사이트와 솔루션의 신뢰 수준을 모두 지정할 수 있는 SharePoint **사용자 지정 마법사가** 나타납니다.

2. 팜 **솔루션으로 배포** 옵션 단추를 선택한 **다음, 마침** 단추를 선택합니다.

     IntelliTrace는 팜 솔루션에서만 작동합니다.

3. **솔루션 탐색기** **에서 기능** 노드의 바로 가기 메뉴를 열고 **기능 추가를** 선택합니다.

     *Feature1.feature가* 나타납니다.

4. Feature1.feature에 대한 바로 가기 메뉴를 열고 **이벤트 수신기 추가를** 선택하여 기능에 코드 모듈을 추가합니다.

## <a name="add-code-to-the-feature-receiver"></a>기능 수신기에 코드 추가

다음으로 기능 수신기의 두 메서드인 및 에 코드를 `FeatureActivated` `FeatureDeactivating` 추가합니다. 이러한 메서드는 SharePoint에서 기능이 활성화되거나 비활성화될 때마다 트리거됩니다.

1. 클래스 맨 위에 `Feature1EventReceiver` SharePoint 사이트 및 하위 사이트를 지정하는 변수를 선언하는 다음 코드를 추가합니다.

    ```vb
    ' SharePoint site and subsite.
    Private siteUrl As String = "http://localhost"
    Private webUrl As String = "/"
    ```

    ```csharp
    // SharePoint site and subsite.
    private string siteUrl = "http://localhost";
    private string webUrl = "/";
    ```

2. `FeatureActivated` 메서드를 다음 코드로 바꿉니다.

    ```vb
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim announcementsList As SPList = web.Lists("Announcements")
                    Dim taskList As SPList = web.Lists("Tasks")

                    ' Add an announcement to the Announcements list.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Add a task to the Task list.
                    Dim newTask As SPListItem = taskList.Items.Add()
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)
                    newTask.Update()
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
                    SPList taskList = web.Lists["Tasks"];

                    // Add an announcement to the Announcements list.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Add a task to the Task list.
                    SPListItem newTask = taskList.Items.Add();
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;
                    newTask.Update();
                }
            }
        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }

    }
    ```

3. `FeatureDeactivating` 메서드를 다음 코드로 바꿉니다.

    ```vb
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)
        ' The following line induces an error to demonstrate debugging.
        ' Remove this line later for proper operation.
        Throw New System.InvalidOperationException("Serious error occurred!")
        Try
            Using site As New SPSite(siteUrl)
                Using web As SPWeb = site.OpenWeb(webUrl)
                    ' Reference the lists.
                    Dim taskList As SPList = web.Lists("Tasks")
                    Dim announcementsList As SPList = web.Lists("Announcements")

                    ' Add an announcement that the feature was deactivated.
                    Dim listItem As SPListItem = announcementsList.Items.Add()
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()
                    listItem.Update()

                    ' Find the task that the feature receiver added to the Task list when the
                    ' feature was activated.
                    Dim qry As New SPQuery()
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)

                    For Each taskItem As SPListItem In taskItems
                        ' Mark the task as complete.
                        taskItem("PercentComplete") = 1
                        taskItem("Status") = "Completed"
                        taskItem.Update()
                    Next
                End Using

            End Using

        Catch e As Exception
            Console.WriteLine("Error: " & e.ToString())
        End Try

    End Sub
    ```

    ```csharp
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)
    {
        // The following line induces an error to demonstrate debugging.
        // Remove this line later for proper operation.
        throw new System.InvalidOperationException("A serious error occurred!");
        try
        {
            using (SPSite site = new SPSite(siteUrl))
            {
                using (SPWeb web = site.OpenWeb(webUrl))
                {
                    // Reference the lists.
                    SPList taskList = web.Lists["Tasks"];
                    SPList announcementsList = web.Lists["Announcements"];

                    // Add an announcement that the feature was deactivated.
                    SPListItem listItem = announcementsList.Items.Add();
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();
                    listItem.Update();

                    // Find the task that the feature receiver added to the Task list when the
                    // feature was activated.
                    SPQuery qry = new SPQuery();
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";
                    SPListItemCollection taskItems = taskList.GetItems(qry);

                    foreach (SPListItem taskItem in taskItems)
                    {
                        // Mark the task as complete.
                        taskItem["PercentComplete"] = 1;
                        taskItem["Status"] = "Completed";
                        taskItem.Update();
                    }
                }
            }

        }

        catch (Exception e)
        {
            Console.WriteLine("Error: " + e.ToString());
        }
    }
    ```

## <a name="test-the-project"></a>프로젝트 테스트

이제 코드가 기능 수신기에 추가되고 데이터 수집기에서 실행 중이면 SharePoint 솔루션을 배포하고 실행하여 제대로 작동하는지 테스트합니다.

> [!IMPORTANT]
> 이 예제에서는 FeatureDeactivating 이벤트 처리기에서 오류가 throw됩니다. 이 연습의 후반부에서는 데이터 수집기에서 만든 .iTrace 파일을 사용하여 이 오류를 찾습니다.

1. SharePoint에 솔루션을 배포한 다음 브라우저에서 SharePoint 사이트를 엽니다.

     기능이 자동으로 활성화되어 기능 수신기가 알림 및 작업을 추가합니다.

2. 알림 및 작업 목록의 내용을 표시합니다.

     알림 목록에는 **활성화된 기능이라는** 새 알림이 있어야 합니다. IntelliTraceTest_Feature1 및 작업 목록에는 비활성화 기능이라는 새 작업이 있어야 **합니다. IntelliTraceTest_Feature1.** 이러한 항목 중 하나가 누락된 경우 기능이 활성화되었는지 확인합니다. 활성화되지 않은 경우 활성화합니다.

3. 다음 단계를 수행하여 기능을 비활성화합니다.

   1. SharePoint의 **사이트 작업** 메뉴에서 **사이트 설정** 을 선택합니다.

   2. **사이트 작업에서** **사이트 기능 관리** 링크를 선택합니다.

   3. **IntelliTraceTest Feature1** 옆에 있는 **비활성화** 단추를 선택합니다.

   4. 경고 페이지에서 **이 기능 비활성화** 링크를 선택합니다.

      FeatureDeactivating() 이벤트 처리기가 오류를 throw합니다.

## <a name="collect-intellitrace-data-by-using-microsoft-monitoring-agent"></a>Microsoft Monitoring Agent 사용하여 IntelliTrace 데이터 수집

SharePoint를 실행하는 시스템에 Microsoft Monitoring Agent 설치하는 경우 IntelliTrace에서 반환하는 일반 정보보다 더 구체적인 데이터를 사용하여 SharePoint 솔루션을 디버그할 수 있습니다. 에이전트는 SharePoint 솔루션이 실행되는 동안 PowerShell cmdlet을 사용하여 디버그 정보를 캡처하여 Visual Studio 외부에서 작동합니다.

> [!NOTE]
> 이 섹션의 구성 정보는 이 예제와 관련이 있습니다. 다른 구성 옵션에 대한 자세한 내용은 [IntelliTrace 독립 실행형 수집기 사용을 참조하세요.](../debugger/using-the-intellitrace-stand-alone-collector.md)

1. SharePoint를 실행하는 컴퓨터에서 [Microsoft Monitoring Agent 설정하고 솔루션 모니터링을 시작합니다.](../debugger/using-the-intellitrace-stand-alone-collector.md)

2. 기능을 비활성화합니다.

   1. SharePoint의 **사이트 작업** 메뉴에서 **사이트 설정** 을 선택합니다.

   2. **사이트 작업에서** **사이트 기능 관리** 링크를 선택합니다.

   3. **IntelliTraceTest Feature1** 옆에 있는 **비활성화** 단추를 선택합니다.

   4. 경고 페이지에서 **이 기능 비활성화** 링크를 선택합니다.

      오류가 발생합니다(이 경우 FeatureDeactivating() 이벤트 처리기에서 throw된 오류로 인해).

3. PowerShell 창에서 [Stop-WebApplicationMonitoring](/previous-versions/system-center/powershell/system-center-2012-r2/dn472753(v=sc.20)) 명령을 실행하여 .iTrace 파일을 만들고, 모니터링을 중지하고, SharePoint 솔루션을 다시 시작합니다.

     **Stop-WebApplicationMonitoring***"<\<SharePointSite> \\ SharePointAppName \> "*  

## <a name="debug-and-fix-the-sharepoint-solution"></a>SharePoint 솔루션 디버그 및 수정

이제 Visual Studio IntelliTrace 로그 파일을 보고 SharePoint 솔루션에서 오류를 찾아 수정할 수 있습니다.

1. \IntelliTraceLogs 폴더의 Visual Studio .iTrace 파일을 엽니다.

     **IntelliTrace 요약** 페이지가 나타납니다. 오류가 처리되지 않았기 때문에 SharePoint 상관 관계 ID(GUID)가 **분석** 섹션의 처리되지 않은 예외 영역에 나타납니다. 오류가 발생한 **호출 스택을** 보려면 호출 스택 단추를 선택합니다.

2. 예외 **디버그** 단추를 선택합니다.

     메시지가 표시되면 기호 파일을 로드합니다. **IntelliTrace** 창에서 예외는 "Throw됨: 심각한 오류가 발생했습니다!"로 강조 표시됩니다.

     IntelliTrace 창에서 예외를 선택하여 실패한 코드를 표시합니다.

3. SharePoint 솔루션을 연 다음 FeatureDeactivating() 프로시저 맨 위에 있는 **throw** 문을 주석으로 제거하거나 제거하여 오류를 수정합니다.

4. Visual Studio 솔루션을 다시 빌드한 다음 SharePoint에 다시 배포합니다.

5. 다음 단계를 수행하여 기능을 비활성화합니다.

    1. SharePoint의 **사이트 작업** 메뉴에서 **사이트 설정** 을 선택합니다.

    2. **사이트 작업에서** **사이트 기능 관리** 링크를 선택합니다.

    3. **IntelliTraceTest Feature1** 옆에 있는 **비활성화** 단추를 선택합니다.

    4. 경고 페이지에서 **이 기능 비활성화** 링크를 선택합니다.

6. 작업 목록을 열고 비활성화 작업의 **상태** 값이 "완료"이고 **해당 % 완료** 값이 100%인지 확인합니다.

     이제 코드가 제대로 실행됩니다.

## <a name="see-also"></a>참조

- [SharePoint 코드 확인 및 디버그](../sharepoint/verifying-and-debugging-sharepoint-code.md)
- [IntelliTrace](../debugger/intellitrace.md)
- [연습: 단위 테스트를 사용하여 SharePoint 코드 확인](/previous-versions/visualstudio/visual-studio-2010/gg599006\(v\=vs.100\))
