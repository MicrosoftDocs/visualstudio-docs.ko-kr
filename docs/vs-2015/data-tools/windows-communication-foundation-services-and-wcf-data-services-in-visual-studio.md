---
title: Windows Communication Foundation 서비스 및 WCF Data Services
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e988c8818cdee756310b73d0d214deda43226f2b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850221"
---
# <a name="windows-communication-foundation-services-and-wcf-data-services-in-visual-studio"></a>Windows Communication Foundation 서비스 및 Visual Studio의 WCF.NET 데이터 서비스
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio는 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 배포 응용 프로그램을 만들기 위한 Microsoft 기술 및 WCF (Windows Communication Foundation)를 사용 하기 위한 도구를 제공 합니다. 이 항목에서는 큐브 뷰의 서비스를 소개 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다. 전체 설명서는 [WCF Data Services 4.5](https://msdn.microsoft.com/library/73d2bec3-7c92-4110-b905-11bb0462357a)을 참조 하세요.

## <a name="what-is-wcf"></a>WCF 란?
 [!INCLUDE[vsindigo](../includes/vsindigo-md.md)] 는 안전 하 고 신뢰할 수 있으며 트랜잭션 되 고 상호 운용할 수 있는 분산 응용 프로그램을 만들기 위한 통합 프레임 워크입니다. ASMX 웹 서비스, .NET Remoting, 엔터프라이즈 서비스 (DCOM) 및 MSMQ와 같은 이전 프로세스 간 통신 기술을 대체 합니다. WCF는 통합 프로그래밍 모델에서 모든 기술의 기능을 함께 제공 합니다. 이렇게 하면 배포 응용 프로그램을 개발 하는 환경이 간소화 됩니다.

#### <a name="what-are-wcf-data-services"></a>WCF Data Services 정의
 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] 는 OData (Open Data) 프로토콜 표준의 구현입니다.  WCF Data Services를 사용 하면 테이블 형식 데이터를 일련의 REST Api로 노출 하 여 GET, POST, PUT 또는 DELETE와 같은 표준 HTTP 동사를 사용 하 여 데이터를 반환할 수 있습니다. 서버 쪽에서는 새 OData 서비스를 만들기 위해 WCF Data Services [ASP.NET Web API](https://dotnet.microsoft.com/apps/aspnet/apis) 으로 대체 됩니다. WCF Data Services 클라이언트 라이브러리는 Visual Studio (**Project &#124; 서비스 참조 추가**)의 .net 응용 프로그램에서 OData 서비스를 사용 하는 데 적합 합니다. 자세한 내용은 [WCF Data Services 4.5](https://msdn.microsoft.com/library/cc668792.aspx)를 참조하세요.

### <a name="wcf-programming-model"></a>WCF 프로그래밍 모델
 WCF 프로그래밍 모델은 WCF 서비스와 WCF 클라이언트 라는 두 엔터티 간의 통신을 기반으로 합니다. 프로그래밍 모델은의 네임 스페이스에 캡슐화 되어 <xref:System.ServiceModel> [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 있습니다.

#### <a name="wcf-service"></a>WCF 서비스
 WCF 서비스는 서비스와 클라이언트 간의 계약을 정의 하는 인터페이스를 기반으로 합니다. <xref:System.ServiceModel.ServiceContractAttribute>다음 코드와 같이 특성으로 표시 됩니다.

 [!code-csharp[WCFWalkthrough#6](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#6)]
 [!code-vb[WCFWalkthrough#6](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#6)]

 [!code-csharp[WCFWalkthrough#1](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/iservice1.cs#1)]
 [!code-vb[WCFWalkthrough#1](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/iservice1.vb#1)]

 WCF 서비스에 의해 노출 되는 함수 또는 메서드를 특성으로 표시 하 여 정의 <xref:System.ServiceModel.OperationContractAttribute> 합니다. 또한 복합 형식을 특성으로 표시 하 여 serialize 된 데이터를 노출할 수 있습니다 <xref:System.Runtime.Serialization.DataContractAttribute> . 이렇게 하면 클라이언트에서 데이터를 바인딩할 수 있습니다.

 인터페이스와 해당 메서드를 정의한 후에는 인터페이스를 구현 하는 클래스에 캡슐화 됩니다. 단일 WCF 서비스 클래스는 여러 서비스 계약을 구현할 수 있습니다.

 WCF 서비스는 *끝점*이라고 하는 항목을 통해 사용 하기 위해 노출 됩니다. 끝점은 서비스와 통신 하는 유일한 방법을 제공 합니다. 다른 클래스와 마찬가지로 직접 참조를 통해 서비스에 액세스할 수 없습니다.

 끝점은 주소, 바인딩 및 계약으로 구성 됩니다. 주소는 서비스의 위치를 정의 합니다. URL, FTP 주소 또는 네트워크 또는 로컬 경로일 수 있습니다. 바인딩은 서비스와 통신 하는 방법을 정의 합니다. WCF 바인딩은 HTTP 또는 FTP와 같은 프로토콜, Windows 인증 또는 사용자 이름 및 암호 등의 보안 메커니즘을 지정 하는 다양 한 모델을 제공 합니다. 계약은 WCF 서비스 클래스에 의해 노출 되는 작업을 포함 합니다.

 단일 WCF 서비스에 대해 여러 끝점을 노출할 수 있습니다. 이렇게 하면 여러 클라이언트가 서로 다른 방식으로 동일한 서비스와 통신할 수 있습니다. 예를 들어, 은행 서비스는 직원을 위한 끝점을 제공 하 고, 다른 주소, 바인딩 및/또는 계약을 사용 하는 외부 고객에 게 다른 끝점을 제공할 수 있습니다.

#### <a name="wcf-client"></a>WCF 클라이언트
 WCF 클라이언트는 응용 프로그램이 WCF 서비스와 통신할 수 있도록 하는 *프록시와* 서비스에 대해 정의 된 끝점과 일치 하는 끝점으로 구성 됩니다. 프록시는 app.config 파일의 클라이언트 쪽에서 생성 되 고 서비스에서 노출 하는 형식 및 메서드에 대 한 정보를 포함 합니다. 여러 끝점을 노출 하는 서비스의 경우 클라이언트는 HTTP를 통해 통신 하 고 Windows 인증을 사용 하는 등의 요구에 가장 적합 한 항목을 선택할 수 있습니다.

 WCF 클라이언트를 만든 후에는 다른 개체와 마찬가지로 코드에서 서비스를 참조 합니다. 예를 들어 앞에 표시 된 메서드를 호출 하려면 `GetData` 다음과 같은 코드를 작성 합니다.

 [!code-csharp[WCFWalkthrough#3](../snippets/csharp/VS_Snippets_VBCSharp/wcfwalkthrough/cs/form1.cs#3)]
 [!code-vb[WCFWalkthrough#3](../snippets/visualbasic/VS_Snippets_VBCSharp/wcfwalkthrough/vb/form1.vb#3)]

## <a name="wcf-tools-in-visual-studio"></a>Visual Studio의 WCF 도구
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] WCF 서비스와 WCF 클라이언트를 만드는 데 도움이 되는 도구를 제공 합니다. 도구를 보여 주는 연습은 [연습: Windows Forms에서 간단한 WCF 서비스 만들기](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)를 참조 하세요.

### <a name="creating-and-testing-wcf-services"></a>WCF 서비스 만들기 및 테스트
 WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 템플릿을 기반으로 사용 하 여 서비스를 신속 하 게 만들 수 있습니다. 그런 다음 WCF 서비스 자동 호스트 및 WCF 테스트 클라이언트를 사용 하 여 서비스를 디버깅 하 고 테스트할 수 있습니다. 이러한 도구는 빠르고 편리한 디버그 및 테스트 주기를 제공 하 고 초기 단계에서 호스팅 모델에 커밋하지 않아도 되는 요구 사항을 제거 합니다.

#### <a name="wcf-templates"></a>WCF 템플릿
 WCF [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 템플릿은 서비스 개발을 위한 기본 클래스 구조를 제공 합니다. **새 프로젝트 추가** 대화 상자에서 사용할 수 있는 몇 가지 WCF 템플릿이 있습니다. 여기에는 WCF 서비스 라이브러리 프로젝트, WCF 서비스 웹 사이트 및 WCF 서비스 항목 템플릿이 포함 됩니다.

 템플릿을 선택 하면 서비스 계약, 서비스 구현 및 서비스 구성에 대 한 파일이 추가 됩니다. 필요한 모든 특성이 이미 추가 되었으며 간단한 "Hello World" 유형의 서비스를 만들고 코드를 작성할 필요가 없습니다. 물론 실제 서비스에 대 한 함수 및 메서드를 제공 하는 코드를 추가 하려고 하지만 템플릿에서 기본 토대를 제공 합니다.

 WCF 템플릿에 대 한 자세한 내용은 [Wcf Visual Studio 템플릿](https://msdn.microsoft.com/library/6a608575-3535-4190-89da-911e24c8374f)을 참조 하세요.

#### <a name="wcf-service-host"></a>WCF 서비스 호스트
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Wcf 서비스 프로젝트에 대해 F5 키를 눌러 디버거를 시작 하면 Wcf 서비스 호스트 도구가 자동으로 시작 되어 서비스를 로컬로 호스팅합니다. WCF 서비스 호스트는 WCF 서비스 프로젝트에서 서비스를 열거 하 고 프로젝트의 구성을 로드 한 다음 찾은 각 서비스에 대 한 호스트를 인스턴스화합니다.

 WCF 서비스 호스트를 사용 하 여 개발 중에 추가 코드를 작성 하거나 특정 호스트를 커밋하지 않고도 WCF 서비스를 테스트할 수 있습니다.

 WCF 서비스 호스트에 대 한 자세한 내용은 [Wcf 서비스 호스트 (WcfSvcHost.exe)](https://msdn.microsoft.com/library/8643a63d-a357-4c39-bd6c-cdfdf71e370e)를 참조 하세요.

#### <a name="wcf-test-client"></a>WCF 테스트 클라이언트
 WCF 테스트 클라이언트 도구를 사용 하 여 테스트 매개 변수를 입력 하 고, 해당 입력을 WCF 서비스에 제출 하 고, 서비스가 다시 보내는 응답을 볼 수 있습니다. WCF 서비스 호스트와 결합할 때 편리한 서비스 테스트 환경을 제공 합니다. 이 도구는 C: 드라이브에 설치 된 Visual Studio 2015에 대 한 \Common7\IDE 폴더에서 찾을 수 있습니다 .이 폴더는 **C:\Program files (x86) \Microsoft Visual Studio 14.0 \\ \ Common7\IDE**에 있습니다.

 F5 키를 눌러 WCF 서비스 프로젝트를 디버깅할 때 WCF 테스트 클라이언트는 구성 파일에 정의 된 서비스 끝점 목록을 열고 표시 합니다. 매개 변수를 테스트 하 고 서비스를 시작 하 고이 프로세스를 반복 하 여 서비스를 지속적으로 테스트 하 고 유효성을 검사할 수 있습니다.

 WCF 테스트 클라이언트에 대해 자세히 알아보려면 [Wcf 테스트 클라이언트 (WcfTestClient.exe)](https://msdn.microsoft.com/library/d4302855-677f-4640-aa90-c5d785d72fb7)를 참조 하세요.

### <a name="accessing-wcf-services-in-visual-studio"></a>Visual Studio에서 WCF 서비스 액세스
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**서비스 참조 추가** 대화 상자를 사용 하 여 추가 하는 서비스에 대 한 프록시 및 끝점을 자동으로 생성 하는 WCF 클라이언트 만들기 작업을 간소화 합니다. 필요한 모든 구성 정보가 app.config 파일에 추가 됩니다. 대부분의 경우에는이 서비스를 사용 하기 위해 서비스를 인스턴스화해야 합니다.

 **서비스 참조 추가** 대화 상자를 사용 하 여 서비스에 대 한 주소를 입력 하거나 솔루션에 정의 된 서비스를 검색할 수 있습니다. 이 대화 상자는 서비스 목록 및 해당 서비스에서 제공 하는 작업을 반환 합니다. 또한 코드에서 서비스를 참조 하는 네임 스페이스를 정의할 수 있습니다.

 **서비스 참조 구성** 대화 상자를 사용 하 여 서비스에 대 한 구성을 사용자 지정할 수 있습니다. 서비스의 주소를 변경 하 고, 액세스 수준, 비동기 동작 및 메시지 계약 형식을 지정 하 고, 형식 재사용을 구성할 수 있습니다.

## <a name="how-to-select-a-service-endpoint"></a>방법: 서비스 끝점 선택
 WCF (일부 Windows Communication Foundation) 서비스는 클라이언트가 서비스와 통신할 수 있는 여러 끝점을 노출 합니다. 예를 들어 서비스는 HTTP 바인딩 및 사용자 이름/암호 보안을 사용 하는 하나의 끝점과 FTP 및 Windows 인증을 사용 하는 두 번째 끝점을 노출할 수 있습니다. 첫 번째 끝점은 방화벽 외부에서 서비스에 액세스 하는 응용 프로그램에서 사용 될 수 있지만, 두 번째 끝점은 인트라넷에서 사용 될 수 있습니다.

 이 경우을 `endpointConfigurationName` 서비스 참조의 생성자에 대 한 매개 변수로 지정할 수 있습니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-select-a-service-endpoint"></a>서비스 끝점을 선택 하려면

1. 솔루션 탐색기에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭 하 고 **서비스 참조 추가** 를 선택 하 여 WCF 서비스에 대 한 참조를 추가 합니다.

2. 코드 편집기에서 서비스 참조에 대 한 생성자를 추가 합니다.

    ```vb
    Dim proxy As New ServiceReference.Service1Client(
    ```

    ```csharp
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(
    ```

    > [!NOTE]
    > *ServiceReference* 을 서비스 참조의 네임 스페이스로 바꾸고 *Service1Client* 을 서비스 이름으로 바꿉니다.

3. IntelliSense 목록이 생성자에 대 한 오버 로드와 함께 표시 됩니다. `endpointConfigurationName As String`오버 로드를 선택 합니다.

4. 오버 로드 뒤에 `=` *configurationname*을 입력 합니다. 여기서 *configurationname* 은 사용 하려는 끝점의 이름입니다.

    > [!NOTE]
    > 사용 가능한 끝점의 이름을 모르는 경우 app.config 파일에서 찾을 수 있습니다.

#### <a name="to-find-the-available-endpoints-for-a-wcf-service"></a>WCF 서비스에 사용할 수 있는 끝점을 찾으려면

1. **솔루션 탐색기**에서 서비스 참조가 포함 된 프로젝트에 대 한 app.config 파일을 마우스 오른쪽 단추로 클릭 한 다음 **열기**를 클릭 합니다. 파일이 코드 편집기에 표시 됩니다.

2. `<Client>`파일에서 태그를 검색 합니다.

3. 태그 아래에서 `<Client>` 로 시작 하는 태그를 검색 `<Endpoint>` 합니다.

     서비스 참조에서 여러 끝점을 제공 하는 경우 두 개 이상의 `<Endpoint` 태그가 있습니다.

4. 태그 내에서 `<EndPoint>` SomeService 매개 변수를 찾을 수 있습니다 `name="` *SomeService* `"` (여기서 *SomeService* 는 끝점 이름을 나타냄). `endpointConfigurationName As String`서비스 참조에 대 한 생성자의 오버 로드에 전달 될 수 있는 끝점의 이름입니다.

## <a name="how-to-call-a-service-method-asynchronously"></a>방법: 비동기적으로 서비스 메서드 호출
 WCF (Windows Communication Foundation) 서비스의 대부분의 메서드는 동기적 또는 비동기적으로 호출할 수 있습니다. 메서드를 비동기적으로 호출 하면 메서드가 저속 연결을 통해 작동할 때 호출 되는 동안 응용 프로그램이 계속 작동할 수 있습니다.

 기본적으로 서비스 참조가 프로젝트에 추가 되 면 메서드를 동기적으로 호출 하도록 구성 됩니다. **서비스 참조 구성** 대화 상자에서 설정을 변경 하 여 메서드를 비동기적으로 호출 하는 동작을 변경할 수 있습니다.

> [!NOTE]
> 이 옵션은 서비스 별로 설정 됩니다. 서비스에 대 한 한 메서드가 비동기적으로 호출 되는 경우 모든 메서드를 비동기적으로 호출 해야 합니다.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

#### <a name="to-call-a-service-method-asynchronously"></a>서비스 메서드를 비동기적으로 호출 하려면

1. **솔루션 탐색기**에서 서비스 참조를 선택 합니다.

2. **프로젝트** 메뉴에서 **서비스 참조 구성**을 클릭 합니다.

3. **서비스 참조 구성** 대화 상자에서 **비동기 작업 생성** 확인란을 선택 합니다.

## <a name="how-to-bind-data-returned-by-a-service"></a>방법: 서비스에서 반환 되는 데이터 바인딩
 다른 데이터 소스를 컨트롤에 바인딩할 수 있는 것 처럼 WCF (Windows Communication Foundation) 서비스에서 반환 되는 데이터를 컨트롤에 바인딩할 수 있습니다. WCF 서비스에 대 한 참조를 추가 하는 경우 서비스에 데이터를 반환 하는 복합 형식이 포함 되어 있으면 **데이터 소스** 창에 자동으로 추가 됩니다.

#### <a name="to-bind-a-control-to-single-data-field-returned-by-a-wcf-service"></a>WCF 서비스에서 반환 하는 단일 데이터 필드에 컨트롤을 바인딩하려면

1. **데이터** 메뉴에서 **데이터 소스 표시**를 클릭합니다. **데이터 소스** 창이 표시 됩니다.

2. **데이터 소스** 창에서 서비스 참조에 대 한 노드를 확장 합니다. 서비스에서 반환 되는 모든 복합 형식이 표시 됩니다.

3. 형식에 대 한 노드를 확장 합니다. 해당 형식에 대 한 데이터 필드가 표시 됩니다.

4. 필드를 선택 하 고 드롭다운 화살표를 클릭 하 여 데이터 형식에 사용할 수 있는 컨트롤의 목록을 표시 합니다.

5. 바인딩하려는 컨트롤의 형식을 클릭 합니다.

6. 필드를 폼으로 끌어 놓습니다. 컨트롤은 <xref:System.Windows.Forms.BindingSource> 구성 요소 및 구성 요소와 함께 폼에 추가 됩니다 <xref:System.Windows.Forms.BindingNavigator> .

7. 바인딩하려는 다른 모든 필드에 대해 4 ~ 6 단계를 반복 합니다.

#### <a name="to-bind-a-control-to-composite-type-returned-by-a-wcf-service"></a>WCF 서비스에서 반환 하는 복합 형식에 컨트롤을 바인딩하려면

1. **데이터** 메뉴에서 **데이터 소스 표시**를 선택 합니다. **데이터 소스** 창이 표시 됩니다.

2. **데이터 소스** 창에서 서비스 참조에 대 한 노드를 확장 합니다. 서비스에서 반환 되는 모든 복합 형식이 표시 됩니다.

3. 형식에 대 한 노드를 선택 하 고 드롭다운 화살표를 클릭 하 여 사용 가능한 옵션 목록을 표시 합니다.

4. 표 형태의 데이터를 표시 하려면 **DataGridView** 를 클릭 하거나 개별 컨트롤에 데이터를 표시 하려면 **세부 정보** 를 클릭 합니다.

5. 노드를 폼으로 끌어 옵니다. 컨트롤은 <xref:System.Windows.Forms.BindingSource> 구성 요소 및 구성 요소와 함께 폼에 추가 됩니다 <xref:System.Windows.Forms.BindingNavigator> .

## <a name="how-to-configure-a-service-to-reuse-existing-types"></a>방법: 서비스를 구성 하 여 기존 형식 다시 사용
 서비스 참조가 프로젝트에 추가 되 면 서비스에 정의 된 모든 형식이 로컬 프로젝트에 생성 됩니다. 대부분의 경우 서비스에서 공용 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 형식을 사용 하거나 형식이 공유 라이브러리에 정의 된 경우 중복 형식을 만듭니다.

 이 문제를 방지 하기 위해 참조 된 어셈블리의 형식이 기본적으로 공유 됩니다. 하나 이상의 어셈블리에 대해 형식 공유를 사용 하지 않도록 설정 하려면 **서비스 참조 구성** 대화 상자에서이 작업을 수행할 수 있습니다.

#### <a name="to-disable-type-sharing-in-a-single-assembly"></a>단일 어셈블리에서 형식 공유를 사용 하지 않도록 설정 하려면

1. **솔루션 탐색기**에서 서비스 참조를 선택 합니다.

2. **프로젝트** 메뉴에서 **서비스 참조 구성**을 클릭 합니다.

3. **서비스 참조 구성** 대화 상자에서 **지정 된 참조 된 어셈블리의 형식 재사용**을 선택 합니다.

4. 형식 공유를 사용 하도록 설정할 각 어셈블리에 대 한 확인란을 선택 합니다. 어셈블리에 대해 형식 공유를 사용 하지 않도록 설정 하려면 확인란을 선택 하지 않은 상태로 둡니다.

#### <a name="to-disable-type-sharing-in-all-assemblies"></a>모든 어셈블리에서 형식 공유를 사용 하지 않도록 설정 하려면

1. **솔루션 탐색기**에서 서비스 참조를 선택 합니다.

2. **프로젝트** 메뉴에서 **서비스 참조 구성**을 클릭 합니다.

3. **서비스 참조 구성** 대화 상자에서 **참조 된 어셈블리의 형식 재사용** 확인란의 선택을 취소 합니다.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[연습: Windows Forms에서 간단한 WCF 서비스 만들기](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|에서 WCF 서비스를 만들고 사용 하는 방법에 대 한 단계별 데모를 제공 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다.|
|[연습: WPF 및 Entity Framework를 사용하여 WCF 데이터 서비스 만들기](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|에서을 만들고 사용 하는 방법에 대 한 단계별 데모를 제공 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다.|
|[WCF 개발 도구 사용](https://msdn.microsoft.com/library/054adb87-c244-4d5a-83d1-0b2b44bd454b)|에서 WCF 서비스를 만들고 테스트 하는 방법을 설명 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다.|
|[방법: 서비스 참조 추가, 업데이트 또는 제거](https://msdn.microsoft.com/library/cacc14bd-4455-4a44-be78-d2ac16113dd9)|프로젝트에서 WCF 서비스를 추가, 업데이트 또는 제거 하는 방법을 설명 합니다.|
|[방법: WCF 데이터 서비스 참조 추가, 업데이트 또는 제거](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|에서를 참조 하 고 사용 하는 방법을 설명 [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 합니다.|
|[서비스 참조 문제 해결](../data-tools/troubleshooting-service-references.md)|서비스 참조에서 발생할 수 있는 몇 가지 일반적인 오류와 이러한 오류를 방지 하는 방법을 보여 줍니다.|
|[WCF 서비스 디버그](../debugger/debugging-wcf-services.md)|WCF 서비스를 디버그할 때 발생할 수 있는 일반적인 디버깅 문제와 기술에 대해 설명 합니다.|
|[Windows Communication Foundation 인증 서비스 개요](https://msdn.microsoft.com/library/6e121a28-89e8-4974-88a8-70aaa6a7d52b)|WCF를 사용 하 여 웹 사이트에 대 한 역할 서비스를 제공 하는 방법을 설명 합니다.|
|[연습: N 계층 데이터 응용 프로그램 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|형식화된 데이터 세트을 만들고 TableAdapter 및 데이터 세트 코드를 여러 프로젝트로 분리하는 단계별 지침을 제공합니다.|
|[서비스 참조 구성 대화 상자](../data-tools/configure-service-reference-dialog-box.md)|**서비스 참조 구성** 대화 상자의 사용자 인터페이스 요소에 대해 설명 합니다.|

## <a name="reference"></a>참조
 <xref:System.ServiceModel>

 <xref:System.Data.Services>

## <a name="see-also"></a>관련 항목
 [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
