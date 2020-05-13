---
title: Azure 코드 최적화
description: Visual Studio에서 Azure 코드 최적화 도구를 사용하여 더욱 강력하고 성능이 뛰어난 코드를 만드는 방법에 대해 알아보세요.
author: ghogen
manager: jillfra
ms.assetid: ed48ee06-e2d2-4322-af22-07200fb16987
ms.topic: conceptual
ms.custom: vs-azure
ms.workload: azure-vs
ms.date: 11/11/2016
ms.author: ghogen
ms.openlocfilehash: e42a746761b09e99e158ecef8e9054bc0049c03d
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489638"
---
# <a name="optimizing-your-azure-code"></a>Azure 코드 최적화
Microsoft Azure를 사용하는 앱을 프로그래밍할 경우 클라우드 환경에서 앱 안정성, 동작 및 성능 문제를 방지하기 위해 몇 가지 코딩 방법을 따라야 합니다. Microsoft는 이와 같이 자주 발생하는 문제를 인식 및 식별하고 해결해 주는 Azure 코드 분석 도구를 제공합니다. 이 도구는 Visual Studio에서 NuGet을 통해 다운로드할 수 있습니다.

## <a name="azure-code-analysis-rules"></a>Azure 코드 분석 규칙
Azure 코드 분석 도구는 성능에 영향을 미치는 알려진 문제를 발견할 경우 Azure 코드에 자동으로 플래그를 표시하는 다음과 같은 규칙을 사용합니다. 감지된 문제는 경고 또는 컴파일러 오류로 나타납니다. 경고 또는 오류를 해결하기 위한 코드 수정 사항 또는 제안은 일반적으로 전구 아이콘을 통해 제공됩니다.

## <a name="avoid-using-default-in-process-session-state-mode"></a>기본(In-Process) 세션 상태 모드 방지
### <a name="id"></a>ID
AP0000

### <a name="description"></a>설명
클라우드 애플리케이션에 대해 기본(In-Process) 세션 상태 모드를 사용할 경우 세션 상태가 끊어질 수 있습니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
기본적으로 web.config 파일에 지정된 세션 상태 모드는 In-Process입니다. 또한 구성 파일에 지정된 항목이 없을 경우 세션 상태 모드가 기본 설정인 In-Process로 설정됩니다. In-Process 모드는 웹 서버의 메모리에 세션 상태를 저장합니다. 인스턴스를 다시 시작하거나 부하 분산 또는 장애 조치(Failover)를 위해 새 인스턴스를 사용할 웹 서버의 메모리에 저장된 세션 상태가 저장되지 않습니다. 이 상황에서는 클라우드에서 애플리케이션이 확장되지 않습니다.

ASP.NET 세션 상태는 세션 상태 데이터에 대해 다양한 스토리지 옵션(InProc, StateServer, SQLServer, 사용자 지정, 해제)을 지원합니다. [Redis용 Azure 세션 상태 제공자](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/)와 같은 사용자 지정 모드를 사용하여 외부 세션 상태 저장소에 데이터를 호스팅하는 것이 좋습니다.

### <a name="solution"></a>솔루션
관리되는 캐시 서비스에 세션 상태를 저장하는 것도 한 가지 권장할 만한 해결 방법입니다. [Redis용 Azure 세션 상태 제공자](https://devblogs.microsoft.com/aspnet/announcing-asp-net-session-state-provider-for-redis-preview-release/) 를 사용하여 세션 상태를 저장하는 방법에 대해 알아보세요. 또한 클라우드에서 애플리케이션을 확장할 수 있도록 다른 위치에도 세션 상태를 저장할 수 있습니다. 다른 해결 방법을 보려면 [세션 상태 모드](https://msdn.microsoft.com/library/ms178586)를 참조하세요.

## <a name="run-method-should-not-be-async"></a>실행 메서드는 비동기가 아니어야 함
### <a name="id"></a>ID
AP1000

### <a name="description"></a>설명
[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) 메서드 밖에 비동기 메서드(예: [await](https://msdn.microsoft.com/library/hh156528.aspx))를 만든 다음 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)에서 비동기 메서드를 호출합니다. [[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) 메서드를 비동기로 선언하면 작업자 역할이 재시작 루트로 전환됩니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) 메서드 내에서 비동기 메서드를 호출하면 클라우드 서비스 런타임이 작업자 역할을 재순환합니다. 작업자 역할이 시작되면 모든 프로그램 실행이 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) 메서드 내에서 수행됩니다. 기존 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) 메서드에서는 작업자 역할이 다시 시작됩니다. 작업자 역할 런타임이 비동기 메서드를 만나면 비동기 메서드 이후에 모든 작업이 디스패치된 다음 반환됩니다. 그러면 [[[[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) 메서드에서 작업자 역할이 종료되고 다시 시작됩니다. 다음에 실행 반복이 발생할 경우 작업자 역할이 다시 비동기 메서드를 만나면 작업자 역할이 다시 재순환됩니다.

### <a name="solution"></a>솔루션
모든 비동기 작업을 [Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) 메서드 밖에 배치합니다. 그런 다음 RunAsync().wait과 같은 [[Run()](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx)](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.serviceruntime.roleentrypoint.run.aspx) 메서드 안에서 리팩터링된 비동기 메서드를 호출합니다. Azure 코드 분석 도구로 이 문제를 해결할 수 있습니다.

다음 코드 조각은 이 문제의 코드 수정 사항을 보여 줍니다.

```csharp
public override void Run()
{
    RunAsync().Wait();
}

public async Task RunAsync()
{
    //Asynchronous operations code logic
    // This is a sample worker implementation. Replace with your logic.

    Trace.TraceInformation("WorkerRole1 entry point called");

    HttpClient client = new HttpClient();

    Task<string> urlString = client.GetStringAsync("https://msdn.microsoft.com");

    while (true)
    {
        Thread.Sleep(10000);
        Trace.TraceInformation("Working");

        string stream = await urlString;
    }

}
```

## <a name="use-service-bus-shared-access-signature-authentication"></a>Service Bus 공유 액세스 서명 인증 사용
### <a name="id"></a>ID
AP2000

### <a name="description"></a>설명
인증에 SAS(공유 액세스 서명)를 사용합니다. 서비스 버스 인증에 ACS(Access Control Service)를 사용 중입니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
보안 강화를 위해 Azure Active Directory에서 ACS 인증을 SAS 인증으로 대체합니다. 전환 계획에 대한 자세한 내용은 [Azure Active Directory가 ACS의 미래](https://cloudblogs.microsoft.com/enterprisemobility/2013/06/22/azure-active-directory-is-the-future-of-acs/) 를 참조하세요.

### <a name="solution"></a>솔루션
앱에 SAS 인증을 사용합니다. 다음 예제는 기존 SAS 토큰을 사용하여 서비스 버스 네임스페이스 또는 엔터티에 액세스하는 방법을 보여 줍니다.

```csharp
MessagingFactory listenMF = MessagingFactory.Create(endpoints, new StaticSASTokenProvider(subscriptionToken));
SubscriptionClient sc = listenMF.CreateSubscriptionClient(topicPath, subscriptionName);
BrokeredMessage receivedMessage = sc.Receive();
```

자세한 내용은 다음 항목을 참조하세요.

* 개요를 보려면 [Service Bus를 사용한 공유 액세스 서명 인증](https://msdn.microsoft.com/library/dn170477.aspx)
* [Service Bus를 사용한 공유 액세스 서명 인증을 사용하는 방법](https://msdn.microsoft.com/library/dn205161.aspx)
* 샘플 프로젝트를 보려면 [Service Bus를 사용한 SAS(공유 액세스 서명) 인증 사용](https://code.msdn.microsoft.com/windowsapps/Shared-Access-Signature-0a88adf8)

## <a name="consider-using-onmessage-method-to-avoid-receive-loop"></a>OnMessage 메시지를 사용하여 "수신 루프"를 방지합니다.
### <a name="id"></a>ID
AP2002

### <a name="description"></a>설명
"수신 루프"로 전환되지 않기 위해서는 **Receive** 메서드를 호출하는 것보다 **OnMessage** 메서드를 호출하는 것이 메시지 수신에 더 효과적인 해결 방법입니다. 하지만 반드시 **Receive** 메서드를 사용하고 기본값 이외의 서버 대기 시간을 지정해야 할 경우 서버 대기 시간을 1분을 초과하도록 설정합니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
**OnMessage**를 호출하면 클라이언트가 큐 또는 구독을 지속적으로 폴링하는 내부 메시지 펌프를 시작합니다. 이 메시지 펌프에는 메시지 수신을 위한 호출을 실행하는 무한 루프가 포함되어 있습니다. 호출 시간이 초과되면 새 호출을 실행합니다. 시간 초과 간격은 사용 중인 [MessagingFactory](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactory.aspx)의 [OperationTimeout](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.messagingfactorysettings.operationtimeout.aspx) 속성 값으로 결정됩니다.

**Receive**에 비해 **OnMessage**를 사용하는 이점은 사용자가 메시지 폴링, 예외 처리, 여러 메시지 병렬 처리, 메시지 완료를 수동으로 수행하지 않아도 된다는 점입니다.

기본값을 사용하지 않고 **Receive** 를 호출할 경우 *ServerWaitTime* 값을 1분 이내로 설정하십시오. *ServerWaitTime* 을 1분을 초과하여 설정하면 메시지가 완전히 수신되기 전에 서버 시간 초과가 발생하지 않습니다.

### <a name="solution"></a>솔루션
다음 코드 예제에서 권장 사용법을 참조하세요. 자세한 내용은 [QueueClient.OnMessage 메서드(Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.onmessage.aspx) 및 [QueueClient.Receive 메서드(Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.receive.aspx)를 참조하세요.

Azure 메시징 인프라의 성능을 개선하려면 [Asynchronous Messaging Primer](https://msdn.microsoft.com/library/dn589781.aspx)디자인 패턴을 참조하세요.

다음은 **OnMessage** 를 사용하여 메시지를 수신하는 예입니다.

```csharp
void ReceiveMessages()
{
    // Initialize message pump options.
    OnMessageOptions options = new OnMessageOptions();
    options.AutoComplete = true; // Indicates if the message-pump should call complete on messages after the callback has completed processing.
    options.MaxConcurrentCalls = 1; // Indicates the maximum number of concurrent calls to the callback the pump should initiate.
    options.ExceptionReceived += LogErrors; // Enables you to get notified of any errors encountered by the message pump.

    // Start receiving messages.
    QueueClient client = QueueClient.Create("myQueue");
    client.OnMessage((receivedMessage) => // Initiates the message pump and callback is invoked for each message that is received, calling close on the client will stop the pump.
    {
        // Process the message.
    }, options);
    Console.WriteLine("Press any key to exit.");
    Console.ReadKey();
```

다음은 기본 서버 대기 시간을 적용하여 **Receive** 를 사용하는 예입니다.

```csharp
string connectionString =
CloudConfigurationManager.GetSetting("Microsoft.ServiceBus.ConnectionString");

QueueClient Client =
    QueueClient.CreateFromConnectionString(connectionString, "TestQueue");

while (true)
{
   BrokeredMessage message = Client.Receive();
   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
```

다음은 기본값이 아닌 서버 대기 시간을 적용하여 **Receive** 를 사용하는 예입니다.

```csharp
while (true)
{
   BrokeredMessage message = Client.Receive(new TimeSpan(0,1,0));

   if (message != null)
   {
      try
      {
         Console.WriteLine("Body: " + message.GetBody<string>());
         Console.WriteLine("MessageID: " + message.MessageId);
         Console.WriteLine("Test Property: " +
            message.Properties["TestProperty"]);

         // Remove message from queue
         message.Complete();
      }

      catch (Exception)
      {
         // Indicate a problem, unlock message in queue
         message.Abandon();
      }
   }
}
```

## <a name="consider-using-asynchronous-service-bus-methods"></a>비동기 Service Bus 메서드 사용 고려
### <a name="id"></a>ID
AP2003

### <a name="description"></a>설명
조정된 메시지의 성능을 개선하려면 비동기 Service Bus 메서드를 사용합니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
비동기 메서드를 사용하면 호출을 실행할 때마다 메인 스레드가 차단되지 않으므로 애플리케이션 동시성이 지원됩니다. Service Bus 메시징 메서드를 사용할 때 작업(보내기, 받기, 삭제 등)을 수행하면 다소 시간이 소요됩니다. 이 시간에는 요청 및 응답 지연 시간과 Service Bus 서비스의 작업 처리가 포함됩니다. 시간당 작업 수를 늘리려면 작업이 동시에 실행되어야 합니다. 자세한 내용을 보려면 [Service Bus 조정된 메시징을 사용한 성능 향상의 모범 사례](https://msdn.microsoft.com/library/azure/hh528527.aspx)를 참조하세요.

### <a name="solution"></a>솔루션
권장 비동기 메서드를 사용하는 방법은 [QueueClient 클래스(Microsoft.ServiceBus.Messaging)](https://msdn.microsoft.com/library/microsoft.servicebus.messaging.queueclient.aspx) 를 참조하세요.

Azure 메시징 인프라의 성능을 개선하려면 [Asynchronous Messaging Primer](https://msdn.microsoft.com/library/dn589781.aspx)디자인 패턴을 참조하세요.

## <a name="consider-partitioning-service-bus-queues-and-topics"></a>Service Bus 큐 및 토픽 분할 고려
### <a name="id"></a>ID
AP2004

### <a name="description"></a>설명
Service Bus 메시징에서 성능을 향상하려면 Service Bus 큐와 토픽을 분할합니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
Service Bus 큐와 토픽을 분할하면 분할된 큐 또는 토픽이 더 이상 단일 메시지 브로커 또는 메시징 스토어의 성능으로 제한되지 않으므로 성능 처리량과 서비스 가용성이 향상됩니다. 또한 메시징 스토어가 일시적으로 중단된 경우에도 분할된 큐 또는 토픽을 계속 사용할 수 있습니다. 자세한 내용은 [메시징 엔터티 분할](https://msdn.microsoft.com/library/azure/dn520246.aspx)을 참조하세요.

### <a name="solution"></a>솔루션
다음 코드 조각은 메시징 엔터티를 분할하는 방법을 보여 줍니다.

```csharp
// Create partitioned topic.
NamespaceManager ns = NamespaceManager.CreateFromConnectionString(myConnectionString);
TopicDescription td = new TopicDescription(TopicName);
td.EnablePartitioning = true;
ns.CreateTopic(td);
```

자세한 내용은 [분할된 Service Bus 큐 및 토픽 | Microsoft Azure 블로그](https://azure.microsoft.com/blog/2013/10/29/partitioned-service-bus-queues-and-topics/) 및 [Microsoft Azure Service Bus 분할 큐](https://code.msdn.microsoft.com/windowsazure/Service-Bus-Partitioned-7dfd3f1f) 샘플을 참조하세요.

## <a name="do-not-set-sharedaccessstarttime"></a>SharedAccessStartTime을 설정하지 마십시오.
### <a name="id"></a>ID
AP3001

### <a name="description"></a>설명
공유 액세스 정책을 즉시 시작하기 위해 SharedAccessStartTimeset을 현재 시간으로 설정하지 마십시오. 이 속성은 나중에 공유 액세스 정책을 시작하려는 경우에만 설정해야 합니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
클록 동기화는 데이터 센터 간 약간의 시간 차이를 발생시킵니다. 예를 들어 DateTime.Now 또는 유사한 메서드를 사용하여 스토리지 SAS 정책의 시작 시간을 현재 시간으로 설정하면 SAS 정책이 즉시 적용된다고 생각하는 것이 일반적입니다. 하지만 데이터 센터 사이에는 약간의 시간 차이가 있으며 시작 시간보다 약간 빠르거나 느린 데이터 센터가 있을 수 있기 때문에 문제가 발생할 수 있습니다. 그 결과, 정책 수명을 너무 짧게 설정할 경우 SAS 정책이 빠르게 또는 즉시 만료될 수 있습니다.

Azure Storage에서 공유 액세스 서명을 사용하는 방법에 대한 지침은 [테이블 SAS(공유 액세스 서명), 큐 SAS, Blob SAS 업데이트 소개 - Microsoft Azure Storage 팀 블로그 - 사이트 홈 - MSDN 블로그](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)를 참조하세요.

### <a name="solution"></a>솔루션
공유 액세스 정책의 시작 시간을 설정하는 문을 제거합니다. Azure 코드 분석 도구는 이 문제에 대한 해결 방법을 제공합니다. 보안 관리에 대한 자세한 내용은 디자인 패턴 [Valet 주요 패턴](https://msdn.microsoft.com/library/dn568102.aspx)을 참조하세요.

다음 코드 조각은 이 문제의 코드 수정 사항을 보여 줍니다.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

## <a name="shared-access-policy-expiry-time-must-be-more-than-five-minutes"></a>공유 액세스 정책 만료 시간은 5분을 초과해야 합니다.
### <a name="id"></a>ID
AP3002

### <a name="description"></a>설명
"클록 스큐"라고 하는 상태로 인해 다른 위치에 있는 데이터 센터 사이에 최대 5분의 클록 차이가 발생할 수 있습니다. SAS 정책 토큰이 계획보다 빨리 만료되지 않도록 하려면 만료 시간을 5분을 초과하여 설정합니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
전 세계 다른 위치에 있는 데이터 센터는 클록 신호를 기준으로 동기화됩니다. 클록 신호가 다른 위치로 이동하려면 시간이 소요되므로 모든 항목이 동기화된 상태가 정상인 것으로 가정할 경우에도 다양한 지리적 위치에서 데이터 센터 간 시간 차이가 발생할 수 있습니다. 이 시간 차이는 공유 액세스 정책 시작 시간 및 만료 간격에 영향을 미칠 수 있습니다. 따라서 공유 액세스 정책을 즉시 적용하기 위해서는 시작 시간을 지정하지 마십시오. 또한 시간 초과가 빨리 발생하지 않도록 만료 시간을 5분을 초과하도록 설정하십시오.

Azure Storage에서 공유 액세스 서명을 사용하는 방법은 [테이블 SAS(공유 액세스 서명), 큐 SAS, Blob SAS 업데이트 소개 - Microsoft Azure Storage 팀 블로그 - 사이트 홈 - MSDN 블로그](https://blogs.msdn.microsoft.com/windowsazurestorage/2012/06/12/introducing-table-sas-shared-access-signature-queue-sas-and-update-to-blob-sas/)를 참조하세요.

### <a name="solution"></a>솔루션
보안 관리에 대한 자세한 내용은 [Valet 주요 패턴](https://msdn.microsoft.com/library/dn568102.aspx)디자인 패턴을 참조하세요.

다음은 공유 액세스 정책의 시작 시간을 지정하지 않은 예입니다.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
   SharedAccessExpiryTime = DateTime.UtcNow.AddHours(10),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

다음은 공유 액세스 정책 시작 시간을 지정하면서 정책 만료 시간을 5분을 초과하도록 지정한 예입니다.

```csharp
// The shared access policy provides
// read/write access to the container for 10 hours.
blobPermissions.SharedAccessPolicies.Add("mypolicy", new SharedAccessBlobPolicy()
{
   // To ensure SAS is valid immediately, don’t set start time.
   // This way, you can avoid failures caused by small clock differences.
  SharedAccessStartTime = new DateTime(2014,1,20),
 SharedAccessExpiryTime = new DateTime(2014, 1, 21),
   Permissions = SharedAccessBlobPermissions.Write |
      SharedAccessBlobPermissions.Read
});
```

자세한 내용은 [공유 액세스 서명 만들기 및 사용](https://msdn.microsoft.com/library/azure/jj721951.aspx)을 참조하세요.

## <a name="use-cloudconfigurationmanager"></a>CloudConfigurationManager 사용
### <a name="id"></a>ID
AP4000

### <a name="description"></a>설명
Azure 웹 사이트, Azure 모바일 서비스 등의 프로젝트에 [ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx)클래스를 사용하면 런타임 문제가 발생하지 않습니다. 하지만 모든 Azure 클라우드 애플리케이션에서 단일화된 구성 관리 방법으로 Cloud[ConfigurationManager](https://msdn.microsoft.com/library/system.configuration.configurationmanager\(v=vs.110\).aspx)를 사용하는 것이 좋습니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
CloudConfigurationManager는 애플리케이션 환경에 적합한 구성 파일을 읽습니다.

[CloudConfigurationManager](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)

### <a name="solution"></a>솔루션
[CloudConfigurationManager 클래스](https://msdn.microsoft.com/library/azure/microsoft.windowsazure.cloudconfigurationmanager.aspx)를 사용하도록 코드를 리팩터링합니다. Azure 코드 분석 도구에서 이 문제에 대한 코드 수정 사항을 보여 줍니다.

다음 코드 조각은 이 문제의 코드 수정 사항을 보여 줍니다. Replace

`var settings = ConfigurationManager.AppSettings["mySettings"];`

다음과 같이 바꿉니다.

`var settings = CloudConfigurationManager.GetSetting("mySettings");`

다음 예제는 App.config 또는 Web.config 파일에서 구성 파일을 저장하는 방법을 보여 줍니다. 구성 파일의 appSettings 섹션에 설정을 추가합니다. 다음은 이전 코드 예제에 대한 Web.config 파일입니다.

```xml
<appSettings>
    <add key="webpages:Version" value="3.0.0.0" />
    <add key="webpages:Enabled" value="false" />
    <add key="ClientValidationEnabled" value="true" />
    <add key="UnobtrusiveJavaScriptEnabled" value="true" />
    <add key="mySettings" value="[put_your_setting_here]"/>
  </appSettings>
```

## <a name="avoid-using-hard-coded-connection-strings"></a>하드 코드된 연결 문자열을 사용하지 마십시오.
### <a name="id"></a>ID
AP4001

### <a name="description"></a>설명
하드 코드 연결 문자열을 사용하면서 나중에 업데이트가 필요할 경우 소스 코드를 변경하고 애플리케이션을 다시 컴파일해야 합니다. 하지만 연결 문자열을 구성 파일에 저장하면 구성 파일만 업데이트하여 변경할 수 있습니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
연결 문자열을 하드 코드할 경우 연결 문자열을 급히 변경해야 할 때 문제가 될 수 있으므로 좋은 방법이 아닙니다. 또한 프로젝트를 소스 제어에 체크인해야 할 경우 문자열을 소스 코드에서 볼 수 있으므로 하드 코드 연결 문자열이 보안에 취약해집니다.

### <a name="solution"></a>솔루션
연결 문자열을 구성 파일 또는 Azure 환경에 저장합니다.

* 독립 실행형 애플리케이션의 경우 app.config를 사용하여 연결 문자열 설정을 저장합니다.
* IIS에서 호스팅되는 애플리케이션의 경우 web.config를 사용하여 연결 문자열 설정을 저장합니다.
* ASP.NET vNext 애플리케이션의 경우 configuration.json을 사용하여 연결 문자열을 저장합니다.

web.config 또는 app.config와 같은 구성 파일을 사용하는 방법은 [ASP.NET 웹 구성 지침](/aspnet/web-forms/overview/deployment/visual-studio-web-deployment/web-config-transformations)을 참조하세요. Azure 환경 변수의 작동 방식에 대해서는 [Azure 웹 사이트: 애플리케이션 문자열 및 연결 문자열 작동 방식](https://azure.microsoft.com/blog/2013/07/17/windows-azure-web-sites-how-application-strings-and-connection-strings-work/)을 참조하세요. 연결 문자열을 소스 제어에 저장하는 방법에 대한 자세한 내용은 [연결 문자열과 같은 민감한 정보를 소스 코드 리포지토리에 저장된 파일에 두지 않는 방식](/aspnet/aspnet/overview/developing-apps-with-windows-azure/building-real-world-cloud-apps-with-windows-azure/source-control)을 참조하세요.

## <a name="use-diagnostics-configuration-file"></a>진단 구성 파일 사용
### <a name="id"></a>ID
AP5000

### <a name="description"></a>설명
Microsoft.WindowsAzure.Diagnostics 프로그래밍 API를 사용하는 등의 방법으로 코드에 진단 설정을 구성하는 대신 diagnostics.wadcfg 파일에 진단 설정을 구성해야 합니다. Azure SDK 2.5를 사용하는 경우에는 diagnostics.wadcfgx를 사용합니다. 그러면 코드를 다시 컴파일하지 않고도 진단 설정을 변경할 수 있습니다.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
Azure SDK 2.5(Azure 진단 1.3 사용) 전에는 스토리지의 구성 Blob에 추가하거나 명령적 코드, 선언적 구성 또는 기본 구성을 사용하는 등의 다양한 방법을 사용하여 Azure Diagnostics(WAD)를 구성할 수 있었습니다. 하지만 애플리케이션 프로젝트에 XML 구성 파일(SDK 2.5 이상에서 diagnostics.wadcfg 또는 diagnostics.wadcfgx)을 사용하여 진단을 구성하는 것이 더 좋은 방법입니다. 이 방식에서는 diagnostics.wadcfg 파일로 구성을 완전히 정의하며 언제든지 업데이트 및 재배포할 수 있습니다. diagnostics.wadcfg 구성 파일을 사용하면서 [DiagnosticMonitor](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.diagnosticmonitor.aspx) 또는 [RoleInstanceDiagnosticManager](https://msdn.microsoft.com/library/microsoft.windowsazure.diagnostics.management.roleinstancediagnosticmanager.aspx) 클래스를 사용하여 프로그래밍 방법으로 구성을 설정할 경우 혼란스러울 수 있습니다. 자세한 내용은 [Azure Diagnostics 구성 초기화 또는 변경](https://msdn.microsoft.com/library/azure/hh411537.aspx)을 참조하세요.

WAD 1.3(Azure SDK 2.5에 기본 제공)부터 코드를 사용하여 진단을 구성할 수 없습니다. 그 결과 진단 확장을 적용 또는 업데이트할 경우에만 구성을 제공할 수 있습니다.

### <a name="solution"></a>솔루션
진단 구성 디자이너를 사용하여 진단 설정을 진단 구성 파일(SDK 2.5 이상에서 diagnostics.wadcfg 또는 diagnostics.wadcfgx)로 이동합니다. 또한 [Azure SDK 2.5](https://social.msdn.microsoft.com/Forums/en-US/home) 를 설치하고 최신 진단 기능을 사용하는 것이 좋습니다.

1. 구성하려는 역할에 대한 바로 가기 메뉴에서 속성을 선택한 다음 구성 탭을 선택합니다.
2. **진단** 섹션에서 **진단 사용** 확인란이 선택되어 있는지 확인합니다.
3. **구성** 단추를 선택합니다.

   ![진단 사용 옵션에 액세스](./media/vs-azure-tools-optimizing-azure-code-in-visual-studio/IC796660.png)

   자세한 내용은 [Azure Cloud Services 및 Virtual Machines에서 진단 구성](vs-azure-tools-diagnostics-for-cloud-services-and-virtual-machines.md) 을 참조하세요.

## <a name="avoid-declaring-dbcontext-objects-as-static"></a>DbContext 개체를 정적으로 선언하지 마십시오
### <a name="id"></a>ID
AP6000

### <a name="description"></a>설명
메모리를 절약하기 위해 DbContext 개체를 정적으로 선언하지 마십시오.

[Azure 코드 분석 의견](https://social.msdn.microsoft.com/Forums/en-US/home)에서 아이디어와 의견을 공유해 주세요.

### <a name="reason"></a>이유
DBContext 개체는 각 호출의 쿼리 결과를 보관합니다. 정적 DBContext 개체는 애플리케이션 도메인이 언로드될 때까지 삭제되지 않습니다. 따라서 정적 DBContext 개체는 많은 양의 메모리를 사용할 수 있습니다.

### <a name="solution"></a>솔루션
DBContext를 지역 변수 또는 비정적 인스턴스 필드로 선언하고 작업에 사용한 다음 사용 후 삭제되도록 합니다.

다음 예제의 MVC 컨트롤러 클래스는 DBContext 개체를 사용하는 방법을 보여 줍니다.

```csharp
public class BlogsController : Controller
    {
        //BloggingContext is a subclass to DbContext
        private BloggingContext db = new BloggingContext();
        // GET: Blogs
        public ActionResult Index()
        {
            //business logics…
            return View();
        }
        protected override void Dispose(bool disposing)
        {
            if (disposing)
            {
                db.Dispose();
            }
            base.Dispose(disposing);
        }
    }
```

## <a name="next-steps"></a>다음 단계
Azure 앱 최적화 및 문제 해결에 대한 자세한 내용은 [Visual Studio를 사용하여 Azure App Service에서 웹앱 문제 해결](/azure/app-service/web-sites-dotnet-troubleshoot-visual-studio)을 참조하세요.
