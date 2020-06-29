---
title: 웹 성능 테스트용 레코더 플러그 인 만들기
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, recorder plug-in
ms.assetid: 6fe13be1-aeb5-4927-9bff-35950e194da9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3f75114683a4f456d0514af20c1c201c373bd4b0
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85288011"
---
# <a name="how-to-create-a-recorder-plug-in"></a>방법: 레코더 플러그 인 만들기

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>을 사용하여 기록된 웹 성능 테스트를 수정할 수 있습니다. 수정 사항은 **웹 성능 테스트 레코더** 도구 모음의 **중지**를 선택한 후에 테스트가 저장되고 웹 성능 테스트 편집기에 표시되기 전에 적용됩니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

레코더 플러그 인을 사용하면 동적 매개 변수에서 사용자 지정 상관 관계를 수행할 수 있습니다. 웹 성능 테스트에서는 기본 제공 상관 관계 기능을 사용하여 테스트가 완료될 때 또는 사용자가 **웹 성능 테스트 편집기** 도구 모음의 **동적 매개 변수를 웹 테스트 매개 변수로 수준 올리기**를 사용할 때 웹 기록에서 동적 매개 변수를 검색합니다. 그러나 기본 제공 검색 기능으로 항상 모든 동적 매개 변수를 찾을 수 있는 것은 아닙니다. 예를 들어 대개 5-30분마다 값이 변경되는 세션 ID는 찾지 못합니다. 따라서 상관 관계 프로세스를 사용자가 직접 수행해야 합니다.

<xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>을 사용하면 사용자 고유의 사용자 지정 플러그 인에 대한 코드를 작성할 수 있습니다. 이 플러그 인은 웹 성능 테스트가 저장되고 웹 성능 테스트 편집기에 표시되기 전에 여러 가지 방법으로 상관 관계 연결을 수행하거나 웹 성능 테스트를 수정할 수 있습니다. 따라서 많은 기록에 대해 특정 동적 변수를 연결해야 하는 것으로 판단될 경우 이 프로세스를 자동화할 수 있습니다.

레코더 플러그 인은 웹 성능 테스트에서 추출 및 유효성 검사 규칙을 추가하거나, 컨텍스트 매개 변수를 추가하거나, 주석을 트랜잭션으로 변환하는 데도 사용할 수도 있습니다.

다음 절차에서는 레코더 플러그 인의 기본적인 코드를 만들고 이 플러그 인을 배포 및 실행하는 방법에 대해 설명합니다. 절차 다음에 나오는 샘플 코드에서는 Visual C#을 사용하여 사용자 지정 동적 매개 변수 상관 관계 레코더 플러그 인을 만드는 방법을 보여 줍니다.

## <a name="create-a-recorder-plug-in"></a>레코더 플러그 인 만들기

### <a name="to-create-a-recorder-plug-in"></a>레코더 플러그 인을 만들려면

1. 레코더 플러그 인을 만들려는 웹 성능 테스트가 포함된 웹 성능 및 부하 테스트 프로젝트가 들어 있는 솔루션을 엽니다.

2. 새 **클래스 라이브러리** 프로젝트를 솔루션에 추가합니다.

3. **솔루션 탐색기**의 새 클래스 라이브러리 프로젝트 폴더에서 **References** 폴더를 마우스 오른쪽 단추로 클릭하고 **참조 추가**를 선택합니다.

    > [!TIP]
    > 새 클래스 라이브러리 프로젝트 폴더의 예는 **RecorderPlugins**입니다.

     **참조 추가** 대화 상자가 표시됩니다.

4. **.NET** 탭을 선택합니다.

5. 아래로 스크롤하여 **Microsoft.VisualStudio.QualityTools.WebTestFramework**를 선택한 다음, **확인**을 선택합니다.

     **Microsoft.VisualStudio.QualityTools.WebTestFramework**가 **솔루션 탐색기**의 **References** 폴더에 추가됩니다.

6. 레코더 플러그 인의 코드를 작성합니다. 먼저 <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin>에서 파생되는 새 공용 클래스를 만듭니다.

7. <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*> 메서드를 재정의합니다.

    ```csharp
    public class Class1 : WebTestRecorderPlugin
        {
            public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
            {
                base.PostWebTestRecording(sender, e);
            }
        }
    ```

     이벤트 인수는 작업에 사용할 두 개의 개체, 즉 기록된 결과와 기록된 웹 성능 테스트 개체를 제공합니다. 따라서 결과를 반복하여 특정 값을 찾고 웹 성능 테스트 내의 동일한 요청으로 이동하여 수정 작업을 수행할 수 있습니다. 컨텍스트 매개 변수를 추가하거나 URL의 일부를 매개 변수화하려는 경우에 웹 성능 테스트를 수정할 수도 있습니다.

    > [!NOTE]
    > 웹 성능 테스트를 수정할 경우에는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.PostWebTestRecordingEventArgs.RecordedWebTestModified*> 속성도 true로 설정해야 합니다(`e.RecordedWebTestModified = true;`).

8. 웹 기록이 발생한 후 레코더 플러그 인에서 실행할 작업에 따라 원하는 코드를 더 추가합니다. 예를 들어 다음 샘플과 같이 사용자 지정 상관 관계를 처리하는 코드를 추가할 수 있습니다. 주석을 트랜잭션으로 변환하거나 웹 성능 테스트에 유효성 검사 규칙을 추가하는 등의 작업을 위한 레코더 플러그 인을 만들 수도 있습니다.

9. **빌드** 메뉴에서 **빌드\<class library project name>** 를 선택합니다.

그런 다음, Visual Studio에 등록하기 위해 레코더 플러그 인을 배포합니다.

### <a name="deploy-the-recorder-plug-in"></a>레코더 플러그 인 배포

레코더 플러그 인을 컴파일한 후 결과 DLL을 다음 두 위치 중 하나에 배치합니다.

- *%ProgramFiles(x86)%\Microsoft Visual Studio\\[version]\\[edition]\Common7\IDE\PrivateAssemblies\WebTestPlugins*

- *%USERPROFILE%\Documents\Visual Studio [version]\WebTestPlugins*

> [!WARNING]
> 레코더 플러그 인을 두 위치 중 하나에 복사한 후 Visual Studio를 다시 시작해야 레코더 플러그 인이 등록됩니다.

### <a name="execute-the-recorder-plug-in"></a>레코더 플러그 인 실행

1. 새 웹 성능 테스트를 만듭니다.

     **WebTestRecordPlugins 사용** 대화 상자가 나타납니다.

2. 레코더 플러그 인의 확인란을 선택하고 **확인**을 선택합니다.

     웹 성능 테스트의 기록이 완료된 후 새 레코더 플러그 인이 실행됩니다.

    > [!WARNING]
    > 이 플러그 인을 사용하는 부하 테스트 또는 웹 성능 테스트를 실행할 때 다음과 유사한 오류가 발생할 수 있습니다.
    >
    > **요청 실패: \<plug-in> 이벤트의 예외: 파일 또는 어셈블리 '\<"Plug-in name".dll file>, Version=\<n.n.n.n>, Culture=neutral, PublicKeyToken=null' 또는 해당 종속성 중 하나를 로드할 수 없습니다. 지정한 파일을 찾을 수 없습니다.**
    >
    > 이 오류는 플러그 인의 코드를 변경하고 새 DLL 버전 **(버전=0.0.0.0)** 을 만들었지만 해당 플러그 인이 계속해서 원래 플러그 인 버전을 참조하는 경우에 발생합니다. 이 문제를 해결하려면 다음 단계를 수행합니다.
    >
    > 1. 웹 성능 및 부하 테스트 프로젝트에서는 참조에 경고가 표시됩니다. 참조를 제거했다가 플러그 인 DLL에 다시 추가합니다.
    > 2. 테스트 또는 적절한 위치에서 플러그 인을 제거했다가 다시 추가합니다.

## <a name="example"></a>예제

이 샘플에서는 사용자 지정된 웹 성능 테스트 레코더 플러그 인을 만들어 사용자 지정 동적 매개 변수 상관 관계 연결을 수행하는 방법을 보여줍니다.

> [!NOTE]
> 전체 샘플 코드 목록은 이 항목의 맨 아래에 있습니다.

### <a name="iterate-through-the-result-to-find-first-page-with-reportsession"></a>결과를 반복하여 ReportSession이 있는 첫 번째 페이지 찾기

이 코드 샘플 부분에서는 기록된 각 개체를 반복하고 응답 본문에서 ReportSession을 검색합니다.

```csharp
foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
 {
     WebTestResultPage page = unit as WebTestResultPage;
     if (page != null)
     {
         if (!foundId)
         {
             int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
             if (indexOfReportSession > -1)
             {
```

### <a name="add-an-extraction-rule"></a>추출 규칙 추가

응답을 찾았으면 추출 규칙을 추가해야 합니다. 이 코드 샘플 부분에서는 <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference> 클래스를 사용하여 추출 규칙을 만든 다음, 웹 성능 테스트에서 추출 규칙을 추가할 올바른 요청을 찾습니다. 각 결과 개체에는 웹 성능 테스트에서 올바른 요청을 가져오기 위해 코드에서 사용되는 DeclarativeWebTestItemId라는 새 속성이 추가되어 있습니다.

```csharp
ExtractionRuleReference ruleReference = new ExtractionRuleReference();
     ruleReference.Type = typeof(ExtractText);
     ruleReference.ContextParameterName = "SessionId";
     ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
     ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
     ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

     WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
     if (requestInWebTest != null)
     {
         requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
         e.RecordedWebTestModified = true;
     }
```

### <a name="replace-query-string-parameters"></a>쿼리 문자열 매개 변수 바꾸기

이제 코드에서는 다음 코드 샘플 부분과 같이 이름이 ReportSession인 모든 쿼리 문자열 매개 변수를 찾아 해당 값을 {{SessionId}}로 변경합니다.

```csharp
WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
if (requestInWebTest != null)
{
    foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
    {
         if (param.Name.Equals("ReportSession"))
         {
             param.Value = "{{SessionId}}";
         }
     }
 }
```

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.TestTools.WebTesting;
using Microsoft.VisualStudio.TestTools.WebTesting.Rules;

namespace RecorderPlugin
{
    [DisplayName("Correlate ReportSession")]
    [Description("Adds extraction rule for Report Session and binds this to querystring parameters that use ReportSession")]
    public class CorrelateSessionId : WebTestRecorderPlugin
    {
        public override void PostWebTestRecording(object sender, PostWebTestRecordingEventArgs e)
        {
            //first find the session id
            bool foundId = false;
            foreach (WebTestResultUnit unit in e.RecordedWebTestResult.Children)
            {
                WebTestResultPage page = unit as WebTestResultPage;
                if (page != null)
                {
                    if (!foundId)
                    {
                        int indexOfReportSession = page.RequestResult.Response.BodyString.IndexOf("ReportSession");
                        if (indexOfReportSession > -1)
                        {
                            //add an extraction rule to this request
                            // Get the corresponding request in the Declarative Web performance test
                            ExtractionRuleReference ruleReference = new ExtractionRuleReference();

                            ruleReference.Type = typeof(ExtractText);
                            ruleReference.ContextParameterName = "SessionId";
                            ruleReference.Properties.Add(new PluginOrRuleProperty("EndsWith", "&ControlID="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("HtmlDecode", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("IgnoreCase", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Index", "0"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("Required", "True"));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("StartsWith", "ReportSession="));
                            ruleReference.Properties.Add(new PluginOrRuleProperty("UseRegularExpression", "False"));

                            WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                            if (requestInWebTest != null)
                            {
                                requestInWebTest.ExtractionRuleReferences.Add(ruleReference);
                                e.RecordedWebTestModified = true;
                            }
                            foundId = true;

                        }
                    }
                    else
                    {
                        //now update query string parameters
                        WebTestRequest requestInWebTest = e.RecordedWebTest.GetItem(page.DeclarativeWebTestItemId) as WebTestRequest;
                        if (requestInWebTest != null)
                        {
                            foreach (QueryStringParameter param in requestInWebTest.QueryStringParameters)
                            {
                                if (param.Name.Equals("ReportSession"))
                                {
                                    param.Value = "{{SessionId}}";
                                }
                            }
                        }
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRequestPlugin>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.ExtractionRuleReference>
- <xref:Microsoft.VisualStudio.TestTools.WebTesting.WebTestRecorderPlugin.PostWebTestRecording*>
- [부하 테스트에 대한 사용자 지정 코드 및 플러그 인 만들기](../test/create-custom-code-and-plug-ins-for-load-tests.md)
- [코딩된 웹 성능 테스트 생성 및 실행](../test/generate-and-run-a-coded-web-performance-test.md)
