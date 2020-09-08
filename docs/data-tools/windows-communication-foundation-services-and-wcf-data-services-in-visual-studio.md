---
title: Windows Communication Foundation 및 WCF Data Services
ms.date: 11/04/2016
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- services, WCF Data
- WCF services, binding to
- WCF services, asynchronous service methods
- service references [Visual Studio]
- WCF Data Services
- asynchronous calls
- service references [Visual Studio], type sharing
- endpoints [WCF]
- asynchronous service methods
- service references [Visual Studio] endpoints
- WCF services, type sharing
- Windows Communication Foundation, in Visual Studio
- services, WCF
- WCF service, Visual Studio
- data services, WCF
- services, in Visual Studio
- data binding [Visual Studio], WCF
- service endpoints [Visual Studio]
- service references [Visual Studio], asynchronous calls
- services, Windows Communication Foundation
- type sharing in WCF services
- WCF services, endpoints
- service method, called asynchronously[Visual Studio]
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c1f24a33a482b1994d0d8667b4fc71cf968e4625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281047"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Windows Communication Foundation 서비스 및 Visual Studio의 WCF.NET 데이터 서비스

Visual Studio는 분산 앱을 만들기 위한 Microsoft 기술인 Windows Communication Foundation(WCF) 및 WCF Data Services를 사용하기 위한 도구를 제공합니다. 이 항목에서는 Visual Studio 관점에서 서비스를 소개합니다. 전체 설명서는 [WCF Data Services 4.5](/dotnet/framework/data/wcf/index)를 참조하세요.

## <a name="what-is-wcf"></a>WCF란?

WCF(Windows Communication Foundation)는 안전하고 신뢰할 수 있고 트랜잭션되며 상호 운용 가능한 분산 앱을 만들기 위한 통합 프레임워크입니다. ASMX 웹 서비스, .NET Remoting, 엔터프라이즈 서비스(DCOM) 및 MSMQ와 같은 이전 프로세스 간 통신 기술을 대체합니다. WCF는 이 모든 기술의 기능을 통합 프로그래밍 모델에 제공합니다. 이를 통해 분산 앱 개발 환경이 간소화됩니다.

### <a name="what-are-wcf-data-services"></a>WCF Data Services란?

WCF Data Services는 OData(Open Data) Protocol 표준을 구현한 것입니다.  WCF Data Services를 사용하면 표 형식 데이터를 REST API 세트로 표시하여 GET, POST, PUT 또는 DELETE와 같은 표준 HTTP 동사를 사용하여 데이터를 반환할 수 있습니다. 서버 측에서 새 OData 서비스를 만들기 위해 WCF Data Services가 [ASP.NET Web API](https://dotnet.microsoft.com/apps/aspnet/apis)로 대체됩니다. WCF Data Services 클라이언트 라이브러리는 Visual Studio에서 .NET 애플리케이션의 OData 서비스를 사용하는 데 적합 합니다(**프로젝트** > **서비스 참조 추가**). 자세한 내용은 [WCF Data Services 4.5](/dotnet/framework/data/wcf)를 참조하세요.

### <a name="wcf-programming-model"></a>WCF 프로그래밍 모델

WCF 프로그래밍 모델은 WCF 서비스와 WCF 클라이언트라는 두 엔터티 간의 통신을 기반으로 합니다. 프로그래밍 모델은 .NET의 <xref:System.ServiceModel> 네임스페이스에 캡슐화됩니다.

### <a name="wcf-service"></a>WCF 서비스

WCF 서비스는 서비스와 클라이언트 간의 계약을 정의하는 인터페이스를 기반으로 합니다. 다음 코드와 같이 <xref:System.ServiceModel.ServiceContractAttribute> 특성으로 표시됩니다.

[!code-csharp[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
[!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]

<xref:System.ServiceModel.OperationContractAttribute> 특성으로 표시하여 WCF 서비스에 의해 노출되는 함수 또는 메서드를 정의합니다.

[!code-csharp[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
[!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]

추가로 복합 형식을 <xref:System.Runtime.Serialization.DataContractAttribute> 특성으로 표시하여 직렬화된 데이터를 노출할 수 있습니다. 이렇게 하면 클라이언트에서 데이터 바인딩이 가능합니다.

인터페이스와 해당 메서드가 정의된 후에는 인터페이스를 구현하는 클래스에 캡슐화됩니다. 단일 WCF 서비스 클래스는 여러 서비스 계약을 구현할 수 있습니다.

WCF 서비스는 ‘엔드포인트’라는 기능을 통해 사용할 수 있도록 노출됩니다. 엔드포인트는 서비스와 통신하는 유일한 방법을 제공 합니다. 다른 클래스와 마찬가지로 직접 참조를 통해 서비스에 액세스할 수 없습니다.

엔드포인트는 하나의 주소, 바인딩 및 계약으로 구성됩니다. 주소는 서비스의 위치를 정의합니다. 이는 URL, FTP 주소 또는 네트워크나 로컬 경로일 수 있습니다. 바인딩은 서비스와 통신하는 방법을 정의합니다. WCF 바인딩은 HTTP 또는 FTP와 같은 프로토콜, Windows 인증 또는 사용자 이름 및 암호 등의 보안 메커니즘을 지정하는 다양한 모델을 제공합니다. 계약은 WCF 서비스 클래스에 의해 노출되는 작업을 포함합니다.

단일 WCF 서비스에 대해 여러 엔드포인트를 노출할 수 있습니다. 이렇게 하면 여러 클라이언트가 서로 다른 방식으로 동일한 서비스와 통신할 수 있습니다. 예를 들어, 은행 서비스는 직원용 엔드포인트를 제공하고, 다른 주소, 바인딩 및/또는 계약을 사용하는 외부 고객용 엔드포인트를 제공할 수 있습니다.

### <a name="wcf-client"></a>WCF 클라이언트(WCF client)

WCF 클라이언트는 애플리케이션이 WCF 서비스와 통신할 수 있도록 하는 ‘프록시’와 서비스에 대해 정의된 엔드포인트와 일치하는 엔드포인트로 구성됩니다. 프록시는 *app.config* 파일의 클라이언트 측에서 생성되고 서비스에 의해 노출되는 형식 및 메서드에 대한 정보를 포함합니다. 여러 엔드포인트를 노출하는 서비스의 경우 클라이언트는 가장 적합한 방법을 선택할 수 있습니다. 예를 들어, HTTP를 통해 통신하고 Windows 인증을 사용할 수 있습니다.

WCF 클라이언트를 만든 후에는 다른 개체와 마찬가지로 코드에서 서비스를 참조합니다. 예를 들어, 앞서 표시된 `GetData` 메서드를 호출하려면 다음과 같은 코드를 작성합니다.

[!code-csharp[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
[!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio의 WCF 도구

Visual Studio는 WCF 서비스와 WCF 클라이언트를 모두 만드는 데 도움이 되는 도구를 제공합니다. 도구를 보여주는 연습은 [연습: Windows Forms에서 간단한 WCF 서비스 만들기](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)를 참조하세요.

### <a name="create-and-test-wcf-services"></a>WCF 서비스 생성 및 테스트

WCF Visual Studio 템플릿을 기반으로 서비스를 신속하게 만들 수 있습니다. 그런 다음 WCF 서비스 자동 호스트 및 WCF 테스트 클라이언트를 사용하여 서비스를 디버그 및 테스트할 수 있습니다. 해당 도구를 함께 사용하면 디버그 및 테스트를 편리하고 빠르게 수행할 수 있으며 초기 단계에서 호스팅 모델에 주력할 필요가 없습니다.

#### <a name="wcf-templates"></a>WCF 템플릿

WCF Visual Studio 템플릿은 서비스 개발을 위한 기본 클래스 구조를 제공합니다. **새 프로젝트 추가** 대화 상자에서 몇 가지 WCF 템플릿을 사용할 수 있습니다. 여기에는 WCF 서비스 lLibrary 프로젝트, WCF 서비스 웹 사이트 및 WCF 서비스 항목 템플릿이 포함됩니다.

템플릿을 선택하면 서비스 계약, 서비스 구현 및 서비스 구성에 대한 파일이 추가됩니다. 필요한 모든 특성이 이미 추가되어 간단한 “Hello World” 유형의 서비스를 만들 수 있으며, 코드를 작성할 필요가 없습니다. 물론 실제 서비스에 대한 함수 및 메서드를 제공하는 코드를 추가하려고 하지만 템플릿에서 기본 토대를 제공합니다.

WCF 템플릿에 대한 자세한 내용은 [WCF Visual Studio 템플릿](/dotnet/framework/wcf/wcf-vs-templates)을 참조하세요.

#### <a name="wcf-service-host"></a>WCF 서비스 호스트

WCF 서비스 프로젝트에 대한 Visual Studio 디버거를 시작할 때(**F5**를 누름) WCF 서비스 호스트 도구가 자동으로 시작되어 서비스를 로컬로 호스팅합니다. WCF 서비스 호스트는 WCF 서비스 프로젝트의 서비스를 열거하고 프로젝트의 구성을 로드하며, 발견한 각 서비스에 대한 호스트를 인스턴스화합니다.

WCF 서비스 호스트를 사용하면 개발하는 동안 추가 코드를 작성하거나 특정 호스트를 커밋하지 않고 WCF 서비스를 테스트할 수 있습니다.

WCF 서비스 호스트에 대한 자세한 내용은 [WCF 서비스 호스트(WcfSvcHost.exe)](/dotnet/framework/wcf/wcf-service-host-wcfsvchost-exe)를 참조하세요.

#### <a name="wcf-test-client"></a>WCF 테스트 클라이언트

WCF 테스트 클라이언트 도구를 사용하여 테스트 매개 변수를 입력하고, 해당 입력을 WCF 서비스에 제출하고, 서비스가 다시 보내는 응답을 볼 수 있습니다. WCF 서비스 호스트와 결합할 때 편리한 서비스 테스트 환경을 제공합니다. *%ProgramFiles(x86)%\Microsoft Visual Studio\2017\Enterprise\Common7\IDE* 폴더에서 도구를 찾습니다.

**F5** 키를 눌러 WCF 서비스 프로젝트를 디버그하는 경우 WCF 테스트 클라이언트가 열리고 구성 파일에 정의된 서비스 엔드포인트의 목록이 표시됩니다. 그러면 매개 변수를 테스트하고, 서비스를 시작하며, 이 프로세스를 반복하여 테스트를 계속하고 서비스의 유효성을 검사할 수 있습니다.

WCF 테스트 클라이언트에 대한 자세한 내용은 [WCF 테스트 클라이언트(WcfTestClient.exe)](/dotnet/framework/wcf/wcf-test-client-wcftestclient-exe)를 참조하세요.

### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio에서 WCF 서비스 액세스

Visual Studio는 **서비스 참조 추가** 대화 상자를 사용하여 추가하는 서비스에 대한 프록시 및 엔드포인트를 자동으로 생성하여 WCF 클라이언트를 만드는 작업을 간소화합니다. 필요한 모든 구성 정보가 *app.config* 파일에 추가됩니다. 대부분의 경우 이 서비스를 사용하기 위해 서비스를 인스턴스화해야 합니다.

**서비스 참조 추가** 대화 상자를 사용하여 서비스에 대한 주소를 입력하거나 솔루션에 정의된 서비스를 검색할 수 있습니다. 이 대화 상자는 서비스 목록 및 해당 서비스에서 제공하는 작업을 반환합니다. 또한 코드에서 서비스를 참조하는 네임스페이스를 정의할 수 있습니다.

**서비스 참조 구성** 대화 상자를 사용하여 서비스에 대한 구성을 사용자 지정할 수 있습니다. 서비스의 주소를 변경하고, 액세스 수준, 비동기 동작 및 메시지 계약 형식을 지정하고, 형식 재사용을 구성할 수 있습니다.

## <a name="how-to-select-a-service-endpoint"></a>방법: 서비스 엔드포인트 선택

일부 WCF(Windows Communication Foundation) 서비스는 클라이언트가 서비스와 통신할 수 있는 여러 엔드포인트를 노출합니다. 예를 들어, 서비스는 HTTP 바인딩과 사용자 이름 및 암호 보안을 사용하는 하나의 엔드포인트와 FTP 및 Windows 인증을 사용하는 다른 엔드포인트를 노출할 수 있습니다. 첫 번째 엔드포인트는 방화벽 외부에서 서비스에 액세스하는 애플리케이션에서 사용할 수 있지만, 두 번째 엔드포인트는 인트라넷에서 사용할 수 있습니다.

이러한 경우 서비스 참조의 생성자에 대한 매개 변수로 `endpointConfigurationName`을 지정할 수 있습니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-select-a-service-endpoint"></a>서비스 엔드포인트 선택

1. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **서비스 참조 추가**를 선택하여 WCF 서비스에 참조를 추가합니다.

2. 코드 편집기에서 서비스 참조에 대한 생성자를 추가합니다.

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > *ServiceReference*를 서비스 참조에 대한 네임스페이스로 바꾸고 *Service1Client*를 서비스 이름으로 바꿉니다.

3. 생성자에 대한 오버로드가 포함된 IntelliSense 목록이 표시됩니다. `endpointConfigurationName As String` 오버로드를 선택합니다.

4. 오버로드 이후 `=`*ConfigurationName*을 입력합니다. 여기서 *ConfigurationName*은 사용하려는 엔드포인트의 이름입니다.

    > [!NOTE]
    > 사용 가능한 엔드포인트의 이름을 알 수 없는 경우 *app.config* 파일에서 찾을 수 있습니다.

### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>WCF 서비스에 사용할 수 있는 엔드포인트 찾기

1. **솔루션 탐색기**에서 서비스 참조를 포함하는 프로젝트에 대한 **app.config** 파일을 마우스 오른쪽 단추로 클릭한 다음 **열기**를 클릭합니다. 파일이 코드 편집기에 표시됩니다.

2. 파일에서 `<Client>` 태그를 검색합니다.

3. `<Client>` 태그 아래에서 `<Endpoint>`로 시작하는 태그를 검색합니다.

     서비스 참조에서 여러 엔드포인트를 제공하는 경우 두 개 이상의 `<Endpoint` 태그가 있습니다.

4. `<EndPoint>` 태그 내에서 `name="`*SomeService*`"` 매개 변수(여기서 *SomeService*는 엔드포인트 이름을 나타냄)를 찾을 수 있습니다. 서비스 참조에 대한 생성자의 `endpointConfigurationName As String` 오버로드로 전달될 수 있는 엔드포인트의 이름입니다.

## <a name="how-to-call-a-service-method-asynchronously"></a>방법: 비동기적으로 서비스 메서드 호출

WCF(Windows Communication Foundation) 서비스의 대부분 메서드는 동기적 또는 비동기적으로 호출할 수 있습니다. 메서드를 비동기적으로 호출하면 메서드가 저속 연결을 통해 작동할 때 호출되는 동안 애플리케이션 계속 작동할 수 있습니다.

기본적으로 프로젝트에 서비스 참조가 추가된 경우 메서드를 동기적으로 호출하도록 구성됩니다. **서비스 참조 구성** 대화 상자에서 설정을 변경하여 메서드를 비동기적으로 호출하도록 동작을 변경할 수 있습니다.

> [!NOTE]
> 이 옵션은 서비스별로 설정됩니다. 서비스에 대한 메서드 하나가 비동기적으로 호출되는 경우 모든 메서드를 비동기적으로 호출해야 합니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

### <a name="to-call-a-service-method-asynchronously"></a>비동기적으로 서비스 메서드 호출

1. **솔루션 탐색기**에서 서비스 참조를 선택합니다.

2. **프로젝트** 메뉴에서 **서비스 참조 구성**을 클릭합니다.

3. **서비스 참조 구성** 대화 상자에서 **비동기 작업 생성** 확인란을 선택합니다.

## <a name="how-to-bind-data-returned-by-a-service"></a>방법: 서비스에서 반환된 데이터 바인딩

다른 데이터 소스를 컨트롤에 바인딩할 수 있는 것처럼 WCF(Windows Communication Foundation) 서비스에서 반환된 데이터를 컨트롤에 바인딩할 수 있습니다. WCF 서비스에 대한 참조를 추가한 경우 서비스에 데이터를 반환하는 복합 형식이 포함되어 있으면 **데이터 원본** 창에 자동으로 추가됩니다.

### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>WCF 서비스에서 반환하는 단일 데이터 필드에 컨트롤을 바인딩

1. **데이터** 메뉴에서 **데이터 소스 표시**를 클릭합니다.

   **데이터 원본** 창이 표시됩니다.

2. **데이터 원본** 창에서 서비스 참조에 대한 노드를 확장합니다. 서비스에서 반환한 모든 복합 형식이 표시됩니다.

3. 형식에 대한 노드를 확장합니다. 해당 형식에 대한 데이터 필드가 표시됩니다.

4. 필드를 선택하고 드롭다운 화살표를 클릭하면 데이터 형식에 사용할 수 있는 컨트롤 목록이 표시됩니다.

5. 바인딩하려는 컨트롤의 형식을 클릭합니다.

6. 필드를 양식으로 끌어서 놓습니다. 컨트롤이 <xref:System.Windows.Forms.BindingSource> 구성 요소 및 <xref:System.Windows.Forms.BindingNavigator> 구성 요소와 함께 양식에 추가됩니다.

7. 바인딩하려는 다른 모든 필드에서 4~6단계를 반복합니다.

### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>WCF 서비스에서 반환하는 복합 형식에 컨트롤을 바인딩

1. **데이터** 메뉴에서 **데이터 원본 표시**를 선택합니다. **데이터 원본** 창이 표시됩니다.

2. **데이터 원본** 창에서 서비스 참조에 대한 노드를 확장합니다. 서비스에서 반환한 모든 복합 형식이 표시됩니다.

3. 형식에 대한 노드를 선택하고 드롭다운 화살표를 클릭하면 사용 가능한 옵션 목록이 표시됩니다.

4. **DataGridView**를 클릭하면 그리드에 데이터가 표시되고, **Details**를 클릭하면 개별 컨트롤에 데이터가 표시됩니다.

5. 노드를 양식으로 끌어서 놓습니다. 컨트롤이 <xref:System.Windows.Forms.BindingSource> 구성 요소 및 <xref:System.Windows.Forms.BindingNavigator> 구성 요소와 함께 양식에 추가됩니다.

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>방법: 기존 형식을 다시 사용하도록 서비스 구성

서비스 참조가 프로젝트에 추가되면 서비스에 정의된 모든 형식이 로컬 프로젝트에 생성됩니다. 대부분의 경우 서비스에서 공용 .NET 형식을 사용하거나 형식이 공유 라이브러리에 정의되면 중복 형식을 만듭니다.

이 문제를 방지하도록 참조된 어셈블리의 형식이 기본적으로 공유됩니다. 하나 이상의 어셈블리에 대해 형식 공유를 사용하지 않도록 설정하려면 **서비스 참조 구성** 대화 상자에서 이를 수행할 수 있습니다.

### <a name="to-disable-type-sharing-in-a-single-assembly"></a>단일 어셈블리에서 형식 공유를 사용하지 않도록 설정

1. **솔루션 탐색기**에서 서비스 참조를 선택합니다.

2. **프로젝트** 메뉴에서 **서비스 참조 구성**을 클릭합니다.

3. **서비스 참조 구성** 대화 상자에서 **참조된 어셈블리 중 지정된 어셈블리의 형식 재사용**을 선택합니다.

4. 형식 공유를 사용하도록 설정할 각 어셈블리에 대해 확인란을 선택합니다. 어셈블리에 형식 공유를 사용하지 않도록 설정하려면 확인란을 선택하지 않은 상태로 둡니다.

### <a name="to-disable-type-sharing-in-all-assemblies"></a>모든 어셈블리에서 형식 공유를 사용하지 않도록 설정

1. **솔루션 탐색기**에서 서비스 참조를 선택합니다.

2. **프로젝트** 메뉴에서 **서비스 참조 구성**을 클릭합니다.

3. **서비스 참조 구성** 대화 상자에서 **참조된 어셈블리 중 지정된 어셈블리의 형식 재사용** 확인란 선택을 해제합니다.

## <a name="related-topics"></a>관련 항목

| 제목 | 설명 |
| - | - |
| [연습: Windows Forms에서 간단한 WCF 서비스 만들기](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md) | Visual Studio에서 WCF 서비스를 만들고 사용하는 방법에 대한 단계별 데모를 제공합니다. |
| [연습: WPF 및 Entity Framework를 사용하여 WCF 데이터 서비스 만들기](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md) | Visual Studio에서 WCF Data Services를 만들고 사용하는 방법에 대한 단계별 데모를 제공합니다. |
| [WCF 개발 도구 사용](/dotnet/framework/wcf/using-the-wcf-development-tools) | Visual Studio에서 WCF 서비스를 만들고 테스트하는 방법을 설명합니다. |
| | [방법: WCF 데이터 서비스 참조 추가, 업데이트 또는 제거](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md) |
| [서비스 참조 문제 해결](../data-tools/troubleshooting-service-references.md) | 서비스 참조에서 발생할 수 있는 몇 가지 일반적인 오류와 해당 오류를 방지하는 방법을 보여 줍니다. |
| [WCF 서비스 디버그](../debugger/debugging-wcf-services.md) | WCF 서비스를 디버그할 때 발생할 수 있는 일반적인 디버깅 문제와 기술에 관해 설명합니다. |
| [연습: N 계층 데이터 애플리케이션 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md) | 형식화된 데이터 세트을 만들고 TableAdapter 및 데이터 세트 코드를 여러 프로젝트로 분리하는 단계별 지침을 제공합니다. |
| [서비스 참조 구성 대화 상자](../data-tools/configure-service-reference-dialog-box.md) | **서비스 참조 구성** 대화 상자의 사용자 인터페이스 요소를 설명합니다. |

## <a name="reference"></a>참고

- <xref:System.ServiceModel>
- <xref:System.Data.Services>

## <a name="see-also"></a>참조

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
