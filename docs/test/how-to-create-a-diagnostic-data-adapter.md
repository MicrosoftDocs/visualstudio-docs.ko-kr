---
title: '방법: 진단 데이터 어댑터 만들기'
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- Diagnostic Data Adapter, creating
ms.assetid: bd7ad36c-54cb-4d2a-9aea-9d10ad98d7ba
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 43519a96e0718a0864065864d9dd4fbd2ac16b23
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85288080"
---
# <a name="how-to-create-a-diagnostic-data-adapter"></a>방법: 진단 데이터 어댑터 만들기

*진단 데이터 어댑터*를 만들려면 Visual Studio를 사용해서 클래스 라이브러리를 만든 후 Visual Studio Enterprise에서 제공되는 진단 데이터 어댑터 API를 사용자의 클래스 라이브러리에 추가합니다. 테스트 실행 중 발생한 이벤트를 처리할 때 프레임워크에서 제공되는 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>에 원하는 정보를 스트림 또는 파일 형태로 보냅니다. <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>로 보낸 스트림이나 파일은 테스트를 마칠 때 테스트 결과에 첨부 파일로 저장됩니다. [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]를 사용하거나 이러한 테스트 결과를 기반으로 하여 버그를 만들면 해당 버그에도 이 파일이 연결됩니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

테스트를 실행하는 컴퓨터에 적용되거나 테스트 대상 애플리케이션을 실행하는 데 사용할 환경에 속한 컴퓨터에 적용되는 진단 데이터 어댑터를 만들 수 있습니다. 예를 들어 테스트를 실행하는 테스트 컴퓨터에서 파일을 수집하거나 애플리케이션의 웹 서버 역할을 하는 컴퓨터에서 파일을 수집할 수 있습니다.

Visual Studio 또는 Microsoft Test Manager(Visual Studio 2017에서 더 이상 사용되지 않음)를 사용하여 테스트 설정을 만들 때 표시되는 알기 쉬운 이름을 진단 데이터 어댑터에 지정할 수 있습니다. 테스트 설정을 사용하면 테스트를 실행할 때 해당 환경에서 특정 진단 데이터 어댑터를 실행할 컴퓨터 역할을 정의할 수 있습니다. 테스트 설정을 만들 때 진단 데이터 어댑터를 구성할 수도 있습니다. 예를 들어 웹 서버에서 사용자 지정 로그를 수집하는 진단 데이터 어댑터를 만들 수 있습니다. 테스트 설정을 만들 때 이 웹 서버 역할을 수행하는 컴퓨터에서 이 진단 데이터 어댑터를 실행하도록 선택할 수 있고 작성된 로그 중 마지막 로그 세 개만 수집하도록 테스트 설정의 구성을 수정할 수 있습니다. 테스트 설정에 대한 자세한 내용은 [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)을 참조하세요.

테스트를 실행하면 진단 데이터 어댑터가 테스트의 해당 지점에서 작업을 수행할 수 있도록 이벤트가 발생합니다.

> [!IMPORTANT]
> 이러한 이벤트는 여러 컴퓨터에서 테스트를 실행할 때를 포함하여 여러 스레드에서 발생할 수 있습니다. 따라서 발생할 수 있는 스레드 문제를 알고 사용자 지정 어댑터의 내부 데이터를 실수로 손상시키지 않도록 주의해야 합니다. 진단 데이터 어댑터는 스레드로부터 안전합니다.

아래 목록에는 진단 데이터 어댑터를 만들 때 사용할 수 있는 몇 가지 주요 이벤트가 나와 있습니다. 진단 데이터 어댑터 이벤트의 전체 목록을 보려면 추상 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents> 클래스를 참조하십시오.

|이벤트|설명|
|-|-----------------|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionStart>|테스트 실행을 시작합니다.|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.SessionEnd>|테스트 실행을 끝냅니다.|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseStart>|테스트 실행의 각 테스트를 시작합니다.|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseEnd>|테스트 실행의 각 테스트를 끝냅니다.|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepStart>|테스트의 각 테스트 단계를 시작합니다.|
|<xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestStepEnd>|테스트의 각 테스트 단계를 끝냅니다.|

> [!NOTE]
> 수동 테스트를 완료하면 어떠한 데이터 수집 이벤트도 더 이상 진단 데이터 어댑터로 전달되지 않습니다. 테스트가 다시 실행되면 새 테스트 사례 식별자가 추가됩니다. 사용자가 테스트 중 테스트를 다시 설정하여 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents.TestCaseReset> 이벤트가 발생하거나 테스트 단계 결과를 변경하면, 데이터 수집 이벤트가 진단 데이터 어댑터로 보내지지 않지만 테스트 사례 식별자는 동일하게 유지됩니다. 테스트 사례가 다시 설정되었는지 여부를 확인하려면 진단 데이터 어댑터의 테스트 사례 식별자를 추적해야 합니다.

테스트 설정을 만들 때 구성한 정보를 기반으로 데이터 파일을 수집하는 진단 데이터 어댑터를 만들려면 다음 절차를 따릅니다.

사용자 지정 구성 편집기를 비롯한 전체 예제 진단 데이터 어댑터 프로젝트는 [진단 데이터 어댑터를 만들기 위한 샘플 프로젝트](../test/quickstart-create-a-load-test-project.md)를 참조하세요.

## <a name="create-and-install-a-diagnostic-data-adapter"></a>진단 데이터 어댑터 만들기 및 설치

1. 새 **클래스 라이브러리** 프로젝트를 만듭니다.

2. 어셈블리 **Microsoft.VisualStudio.QualityTools.ExecutionCommon**을 추가합니다.

   1. **솔루션 탐색기**에서 **참조**를 마우스 오른쪽 단추로 클릭하고, **참조 추가** 명령을 선택합니다.

   2. **.NET**를 선택하고 **Microsoft.VisualStudio.QualityTools.ExecutionCommon.dll**을 찾습니다.

   3. **확인**을 선택합니다.

3. 어셈블리 **Microsoft.VisualStudio.QualityTools.Common**을 추가합니다.

   1. **솔루션 탐색기**에서 **참조**를 마우스 오른쪽 단추로 클릭하고, **참조 추가** 명령을 선택합니다.

   2. **/.NET**를 선택하고 **Microsoft.VisualStudio.QualityTools.Common.dll**을 찾습니다.

   3. **확인**을 선택합니다.

4. 다음 `using` 지시문을 클래스 파일에 추가합니다.

   ```csharp
   using Microsoft.VisualStudio.TestTools.Common;
   using Microsoft.VisualStudio.TestTools.Execution;
   using System.Linq;
   using System.Text;
   using System.Xml;
   using System;
   ```

5. <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>를 진단 데이터 어댑터의 클래스에 추가하여 이를 진단 데이터 어댑터로 표시합니다. 여기서 **회사**, **제품** 및 **버전**을 진단 데이터 어댑터에 맞는 적절한 정보로 바꿉니다.

   ```csharp
   [DataCollectorTypeUri("datacollector://Company/Product/Version")]
   ```

6. <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute> 특성을 클래스에 추가합니다. 여기서 매개 변수를 진단 데이터 어댑터에 맞는 적절한 정보로 바꿉니다.

   ```csharp
   [DataCollectorFriendlyName("Collect Log Files", false)]
   ```

    이렇게 지정한 이름이 테스트 설정 작업에 표시됩니다.

   > [!NOTE]
   > <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>를 추가하여 이 데이터 어댑터에 대한 사용자 지정 구성 편집기의 `Type`을 지정하고, 필요할 경우 편집기에 사용할 도움말 파일을 지정할 수도 있습니다.
   >
   > 또한 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>를 적용하여 이 특성이 항상 사용되도록 지정할 수도 있습니다.

7. 진단 데이터 어댑터 클래스는 다음과 같이 <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector> 클래스에서 상속되어야 합니다.

   ```csharp
   public class MyDiagnosticDataAdapter : DataCollector
   ```

8. 다음과 같이 지역 변수를 추가합니다.

   ```csharp
   private DataCollectionEvents dataEvents;
   private DataCollectionLogger dataLogger;
   private DataCollectionSink dataSink;
   private XmlElement configurationSettings;
   ```

9. <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector.Initialize*> 메서드 및 **Dispose** 메서드를 추가합니다. `Initialize` 메서드에서 다음과 같이 데이터 싱크 및 테스트 설정의 구성 데이터를 초기화하고 사용할 이벤트 처리기를 등록합니다.

    ```csharp
    public override void Initialize(
        XmlElement configurationElement,
        DataCollectionEvents events,
        DataCollectionSink sink,
        DataCollectionLogger logger,
        DataCollectionEnvironmentContext environmentContext)
    {
           dataEvents = events;  // The test events
           dataLogger = logger;  // The error and warning log
           dataSink = sink;      // Saves collected data
           // Configuration from the test settings
           configurationSettings = configurationElement;

           // Register common events for the data collector
           // Not all of the events are used in this class
        dataEvents.SessionStart +=
            new EventHandler<SessionStartEventArgs>(OnSessionStart);
        dataEvents.SessionEnd +=
            new EventHandler<SessionEndEventArgs>(OnSessionEnd);
        dataEvents.TestCaseStart +=
            new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
        dataEvents.TestCaseEnd +=
            new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
    }

    public override void Dispose(bool disposing)
    {
        if (disposing)
        {
            // Unregister the registered events
            dataEvents.SessionStart -=
                new EventHandler<SessionStartEventArgs>(OnSessionStart);
            dataEvents.SessionEnd -=
                new EventHandler<SessionEndEventArgs>(OnSessionEnd);
            dataEvents.TestCaseStart -=
                new EventHandler<TestCaseStartEventArgs>(OnTestCaseStart);
            dataEvents.TestCaseEnd -=
                new EventHandler<TestCaseEndEventArgs>(OnTestCaseEnd);
        }
    }
    ```

10. 다음 이벤트 처리기 코드 및 전용 메서드를 사용하여 테스트 중에 생성된 로그 파일을 수집합니다.

    ```csharp
    public void OnTestCaseEnd(sender, TestCaseEndEventArgs e)
    {
        // Get any files to be collected that are
        // configured in your test settings
        List<string> files = getFilesToCollect();

        // For each of the files, send the file to the data sink
        // which will attach it to the test results or to a bug
        foreach (string file in files)
        {
            dataSink.SendFileAsync(e.Context, file, false);
        }
    }

    // A private method that returns the file names
    private List<string> getFilesToCollect()
    {
        // Get a namespace manager with our namespace
        XmlNamespaceManager nsmgr =
            new XmlNamespaceManager(
                configurationSettings.OwnerDocument.NameTable);
        nsmgr.AddNamespace("ns",
            "http://MyCompany/schemas/MyDataCollector/1.0");

        // Find all of the "File" elements under our configuration
        XmlNodeList files =
            configurationSettings.SelectNodes(
                "//ns:MyDataCollector/ns:File");

        // Build the list of files to collect from the
        // "FullPath" attributes of the "File" nodes.
        List<string> result = new List<string>();
        foreach (XmlNode fileNode in files)
        {
            XmlAttribute pathAttribute =
                fileNode.Attributes["FullPath"];
            if (pathAttribute != null &&
                !String.IsNullOrEmpty(pathAttribute.Value))
            {
                result.Add(pathAttribute.Value);
            }
        }

        return result;
    }
    ```

     이러한 파일은 테스트 결과에 연결됩니다. [!INCLUDE[mtrlong](../test/includes/mtrlong_md.md)]를 사용하거나 이러한 테스트 결과를 기반으로 하여 버그를 만들면 해당 버그에도 이 파일이 연결됩니다.

     사용자 고유의 편집기를 사용하여 테스트 설정에 사용할 데이터를 수집하려면 [방법: 진단 데이터 어댑터 데이터용 사용자 지정 편집기 만들기](../test/quickstart-create-a-load-test-project.md)를 참조하세요.

11. 테스트가 완료될 때 테스트 설정에 구성된 항목을 기반으로 로그 파일을 수집하려면 *App.config* 파일을 만들고 솔루션에 추가해야 합니다. 이 파일은 다음과 같은 형식으로 만들며, 이때 진단 데이터 어댑터를 식별할 수 있도록 진단 데이터 어댑터의 URL을 포함해야 합니다. 이 예에서 "Company/ProductName/Version"은 실제 값으로 대체합니다.

    > [!NOTE]
    > 진단 데이터 어댑터의 정보를 구성할 필요가 없는 경우에는 구성 파일을 만들지 않아도 됩니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <configuration>
      <configSections>
        <section name="DataCollectorConfiguration" type="Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationSection, Microsoft.VisualStudio.QualityTools.ExecutionCommon, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a "/>
      </configSections>
      <DataCollectorConfiguration xmlns="http://microsoft.com/schemas/VisualStudio/TeamTest/2010">
        <DataCollector typeUri="datacollector://MyCompany/MyProduct/1.0">
          <DefaultConfiguration>
            <!-- Your default config settings -->
            <Binaries>
              <Binary FullPath="C:\Example\Example.dll"/>
              <Binary FullPath="\\Server2\Example2.dll"/>
            </Binaries>
            <Symbols>
              <Symbol FullPath="\\ExampleServer\ExampleSymbol.pdb"/>
            </Symbols>
          </DefaultConfiguration>
        </DataCollector>
      </DataCollectorConfiguration>
    </configuration>
    ```

    > [!NOTE]
    > 기본 구성 요소에는 필요한 모든 데이터가 포함될 수 있습니다. 테스트 설정에서 진단 데이터 어댑터를 구성하지 않은 경우에는 진단 데이터 어댑터가 실행될 때 기본 데이터가 전달됩니다. `<DefaultConfigurations>` 섹션에 추가하는 XML은 선언된 스키마의 일부가 될 수 없으므로 XML 오류가 생성되더라도 무시하면 됩니다.
    >
    > 설치 디렉터리에 따라 다음 경로에는 추가 구성 파일의 다른 예제가 있습니다. *Program Files\Microsoft Visual Studio 10.0\Common7\IDE\PrivateAssemblies\DataCollectors*.

     테스트를 실행할 때 환경을 사용하도록 테스트 설정을 구성하는 방법에 대한 자세한 내용은 [수동 테스트에서 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)을 참조하세요.

     구성 파일 설치에 대한 자세한 내용은 [방법: 사용자 지정 진단 데이터 어댑터 설치](../test/quickstart-create-a-load-test-project.md)를 참조하세요.

12. 진단 데이터 어댑터 어셈블리를 만들 솔루션을 빌드합니다.

13. 사용자 지정 편집기 설치에 대한 자세한 내용은 [방법: 사용자 지정 진단 데이터 어댑터 설치](../test/quickstart-create-a-load-test-project.md)를 참조하세요.

14. 테스트를 실행할 때 환경을 사용하도록 테스트 설정을 구성하는 방법에 대한 자세한 내용은 [수동 테스트에서 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)을 참조하세요.

15. 진단 데이터 어댑터를 선택하려면 먼저 기존 테스트 설정을 선택하거나 Visual Studio 또는 Microsoft Test Manager(Visual Studio 2017에서 더 이상 사용되지 않음)에서 새 항목을 만들어야 합니다. 어댑터는 클래스에 할당된 이름으로 테스트 설정의 **데이터 및 진단** 탭에 표시됩니다.

16. 이러한 테스트 설정을 활성으로 설정합니다. 테스트 설정에 대한 자세한 내용은 [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)을 참조하세요.

17. 진단 데이터 어댑터가 선택된 테스트 설정을 사용하여 테스트를 실행합니다.

    지정한 데이터 파일이 테스트 결과에 연결됩니다.

## <a name="see-also"></a>참조

- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorConfigurationEditorAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionEvents>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollector>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectionSink>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorTypeUriAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorFriendlyNameAttribute>
- <xref:Microsoft.VisualStudio.TestTools.Execution.DataCollectorEnabledByDefaultAttribute>
- [테스트 설정을 사용하여 진단 정보 수집](../test/collect-diagnostic-information-using-test-settings.md)
- [수동 테스트에서 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/mtm/collect-more-diagnostic-data-in-manual-tests?view=vsts)
- [테스트하는 동안 진단 데이터 수집(Azure Test Plans)](/azure/devops/test/collect-diagnostic-data?view=vsts)
- [방법: 진단 데이터 어댑터 데이터용 사용자 지정 편집기 만들기](../test/quickstart-create-a-load-test-project.md)
