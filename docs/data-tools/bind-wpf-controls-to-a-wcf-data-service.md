---
title: WCF 데이터 서비스에 WPF 컨트롤 바인딩
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 8823537c-82f0-41f7-bf30-705f0e5e59fd
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7371e08925ad9227cf15a93a339e6e0ed36d11db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85282854"
---
# <a name="bind-wpf-controls-to-a-wcf-data-service"></a>WCF 데이터 서비스에 WPF 컨트롤 바인딩

이 연습에서는 데이터 바인딩된 컨트롤을 포함하는 WPF 애플리케이션을 만듭니다. 컨트롤은 WCF 데이터 서비스에서 캡슐화 된 고객 레코드에 바인딩됩니다. 또한 고객이 레코드를 보고 업데이트하는 데 사용할 수 있는 단추도 추가합니다.

이 연습에서는 다음 작업을 수행합니다.

- AdventureWorksLT 샘플 데이터베이스의 데이터에서 생성되는 엔터티 데이터 모델을 만듭니다.

- 엔터티 데이터 모델의 데이터를 WPF 응용 프로그램에 노출 하는 WCF 데이터 서비스를 만듭니다.

- **데이터 원본** 창에서 WPF 디자이너로 항목을 끌어 데이터 바인딩된 컨트롤 집합을 만듭니다.

- 고객 레코드를 앞뒤로 탐색하는 데 사용할 단추를 만듭니다.

- 컨트롤의 데이터 변경 내용을 WCF 데이터 서비스 및 기본 데이터 소스에 저장 하는 단추를 만듭니다.

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="prerequisites"></a>필수 구성 요소

이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- Visual Studio

- AdventureWorksLT 샘플 데이터베이스가 연결된 SQL Server 또는 SQL Server Express의 실행 중인 인스턴스 액세스 권한. [CodePlex 웹 사이트](https://archive.codeplex.com/?p=SqlServerSamples)에서 AdventureWorksLT 데이터베이스를 다운로드할 수 있습니다.

또한 다음 개념에 대한 지식은 연습을 완료하는 데 반드시 필요하지는 않지만 사전에 파악해 두면 유용할 수 있습니다.

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview).

- [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)]의 데이터 모델

- 엔터티 데이터 모델 및 ADO.NET Entity Framework 자세한 내용은 [Entity Framework 개요](/dotnet/framework/data/adonet/ef/overview)를 참조 하세요.

- WPF 데이터 바인딩. 자세한 내용은 [데이터 바인딩 개요](/dotnet/desktop-wpf/data/data-binding-overview)를 참조 하세요.

## <a name="create-the-service-project"></a>서비스 프로젝트 만들기

1. C # 또는 Visual Basic **ASP.NET 웹 응용 프로그램** 프로젝트를 만들어이 연습을 시작 합니다. 프로젝트 이름을 **AdventureWorksService**로 합니다.

2. **솔루션 탐색기**에서 **Default.aspx**를 오른쪽 마우스 단추로 클릭하고 **삭제**를 선택합니다. 이 파일은 연습에 필요 하지 않습니다.

## <a name="create-an-entity-data-model-for-the-service"></a>서비스에 대 한 엔터티 데이터 모델 만들기

WCF 데이터 서비스를 사용 하 여 응용 프로그램에 데이터를 노출 하려면 서비스에 대 한 데이터 모델을 정의 해야 합니다. WCF 데이터 서비스는 두 가지 유형의 데이터 모델인 엔터티 데이터 모델 및 인터페이스를 구현 하는 CLR (공용 언어 런타임) 개체를 사용 하 여 정의 되는 사용자 지정 데이터 모델을 지원 합니다 <xref:System.Linq.IQueryable%601> . 이 연습에서는 데이터 모델에 대해 엔터티 데이터 모델을 만듭니다.

1. **프로젝트** 메뉴에서 **새 항목 추가**를 클릭합니다.

2. 설치된 템플릿 목록에서 **데이터**를 클릭한 다음, **ADO.NET 엔터티 데이터 모델** 프로젝트 항목을 선택합니다.

3. 이름을로 변경 하 `AdventureWorksModel.edmx` 고 **추가**를 클릭 합니다.

     **엔터티 데이터 모델** 마법사가 열립니다.

4. **모델 콘텐츠 선택** 페이지에서 **데이터베이스에서 생성**을 클릭한 후, **다음**을 클릭합니다.

5. **데이터 연결 선택** 페이지에서 다음 옵션 중 하나를 선택합니다.

    - AdventureWorksLT 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

    - **새 연결**을 클릭하고 AdventureWorksLT 데이터베이스에 대한 연결을 만듭니다.

6. **데이터 연결 선택** 페이지에서 **다른 이름으로 App.Config의 엔터티 연결 설정 저장** 옵션이 선택되어 있는지 확인한 후, **다음**을 클릭합니다.

7. **데이터베이스 개체 선택** 페이지에서 **테이블**을 확장한 다음, **SalesOrderHeader** 테이블을 선택합니다.

8. **마침**을 클릭합니다.

## <a name="create-the-service"></a>서비스 만들기

엔터티 데이터 모델의 데이터를 WPF 응용 프로그램에 노출 하는 WCF 데이터 서비스를 만듭니다.

1. **프로젝트** 메뉴에서 **새 항목 추가**를 선택합니다.

2. **설치된 템플릿** 목록에서 **웹**을 클릭한 다음, **WCF 데이터 서비스** 프로젝트 항목을 선택합니다.

3. **이름** 상자에 `AdventureWorksService.svc` 를 입력 하 고 **추가**를 클릭 합니다.

     Visual Studio가 `AdventureWorksService.svc` 프로젝트에를 추가 합니다.

## <a name="configure-the-service"></a>서비스 구성

작성한 엔터티 데이터 모델에 대해 작동하도록 서비스를 구성해야 합니다.

1. `AdventureWorks.svc`코드 파일에서 **AdventureWorksService** 클래스 선언을 다음 코드로 바꿉니다.

     [!code-csharp[Data_WPFWCF#1](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_1.cs)]
     [!code-vb[Data_WPFWCF#1](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_1.vb)]

     이 코드는 **AdventureWorksService** <xref:System.Data.Services.DataService%601> `AdventureWorksLTEntities` 엔터티 데이터 모델의 개체 컨텍스트 클래스에서 작동 하는에서 파생 되도록 AdventureWorksService 클래스를 업데이트 합니다. 또한 서비스의 클라이언트에 `InitializeService` 엔터티에 대한 모든 읽기/쓰기 권한을 허용하도록 `SalesOrderHeader` 메서드를 업데이트합니다.

2. 프로젝트를 빌드하고 오류가 없이 빌드되는지 확인합니다.

## <a name="create-the-wpf-client-application"></a>WPF 클라이언트 응용 프로그램 만들기

WCF 데이터 서비스의 데이터를 표시 하려면 서비스를 기반으로 하는 데이터 원본을 사용 하 여 새 WPF 응용 프로그램을 만듭니다. 이 연습 뒷부분에서 애플리케이션에 데이터 바인딩된 컨트롤을 추가합니다.

1. **솔루션 탐색기**에서 솔루션 노드를 마우스 오른쪽 단추로 클릭하고, **추가**를 클릭하고, **새 프로젝트**를 선택합니다.

2. **새 프로젝트** 대화 상자에서 **Visual C#** 또는 **Visual Basic**을 확장한 다음, **Windows**를 선택합니다.

3. **WPF 애플리케이션** 프로젝트 템플릿을 선택합니다.

4. **이름** 상자에 `AdventureWorksSalesEditor`를 입력하고 **확인**을 클릭합니다.

   Visual Studio에서 `AdventureWorksSalesEditor` 프로젝트를 솔루션에 추가 합니다.

5. **데이터** 메뉴에서 **데이터 소스 표시**를 클릭합니다.

   **데이터 원본** 창이 열립니다.

6. **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.

   **데이터 소스 구성** 마법사가 열립니다.

7. 마법사의 **데이터 원본 형식 선택** 페이지에서 **서비스**를 선택한 후, **다음**을 클릭합니다.

8. **서비스 참조 추가** 대화 상자에서 **검색**을 클릭합니다.

   Visual Studio는 현재 솔루션에서 사용 가능한 서비스를 검색 하 고 `AdventureWorksService.svc` **서비스** 상자에서 사용 가능한 서비스 목록에 추가 합니다.

9. **네임스페이스** 상자에 **AdventureWorksService**를 입력합니다.

10. **서비스** 상자에서 **AdventureWorksService.svc**를 클릭한 다음, **확인**을 클릭합니다.

    Visual Studio에서 서비스 정보를 다운로드한 다음, **데이터 원본 구성** 마법사로 돌아갑니다.

11. **서비스 참조 추가** 페이지에서 **마침**을 클릭합니다.

    Visual Studio는 서비스에서 반환하는 데이터를 나타내는 노드를 **데이터 원본** 창에 추가합니다.

## <a name="define-the-user-interface"></a>사용자 인터페이스 정의

WPF 디자이너에서 XAML을 수정하여 창에 여러 단추를 추가합니다. 이 연습 뒷부분에서 사용자가 이러한 단추를 사용해 판매 레코드를 보고 업데이트할 수 있도록 하는 코드를 추가합니다.

1. **솔루션 탐색기**에서 **MainWindow.xaml**을 두 번 클릭합니다.

   WPF 디자이너에서 창이 열립니다.

2. 디자이너의 [!INCLUDE[TLA#tla_titlexaml](../data-tools/includes/tlasharptla_titlexaml_md.md)] 뷰에서 `<Grid>` 태그 사이에 다음 코드를 추가합니다.

   ```xaml
   <Grid.RowDefinitions>
       <RowDefinition Height="75" />
       <RowDefinition Height="525" />
   </Grid.RowDefinitions>
   <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
   <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
   <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
   ```

3. 프로젝트를 빌드합니다.

## <a name="create-the-data-bound-controls"></a>데이터 바인딩된 컨트롤 만들기

`SalesOrderHeaders` **데이터 소스** 창에서 디자이너로 노드를 끌어 고객 레코드를 표시 하는 컨트롤을 만듭니다.

1. **데이터 원본** 창에서 **SalesOrderHeaders** 노드의 드롭다운 메뉴를 클릭하고 **정보**를 선택합니다.

2. **SalesOrderHeaders** 노드를 확장합니다.

3. 이 예에서는 일부 필드를 표시하지 않을 것이므로 다음 노드 옆의 드롭다운 메뉴를 클릭하고 **없음**을 선택합니다.

    - **CreditCardApprovalCode**

    - **ModifiedDate**

    - **OnlineOrderFlag**

    - **RevisionNumber**

    - **rowguid**

    이 작업을 수행하면 다음 단계에서 이러한 노드에 대해 데이터 바인딩된 컨트롤이 작성되지 않습니다. 이 연습에서는 최종 사용자가이 데이터를 볼 필요가 없다고 가정 합니다.

4. **데이터 원본** 창에서 단추가 포함된 행 아래의 데이터 그리드 행으로 **SalesOrderHeaders** 노드를 끌어 옵니다.

     Visual Studio는 **Product** 테이블의 데이터에 바인딩되는 컨트롤 집합을 만드는 XAML 및 코드를 생성합니다. 생성 된 XAML 및 코드에 대 한 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)을 참조 하세요.

5. 디자이너에서 **고객 ID** 레이블 옆의 텍스트 상자를 클릭합니다.

6. **속성** 창에서 **IsReadOnly** 속성 옆의 확인란을 선택합니다.

7. 다음의 각 텍스트 상자에 대해 **IsReadOnly** 속성을 설정합니다.

    - **구매 주문 번호**

    - **판매 주문 ID**

    - **Sales Order Number**

## <a name="load-the-data-from-the-service"></a>서비스에서 데이터 로드

서비스 프록시 개체를 사용 하 여 서비스에서 판매 데이터를 로드 합니다. 그런 다음 반환 된 데이터를 WPF 창에서의 데이터 소스에 할당 합니다 <xref:System.Windows.Data.CollectionViewSource> .

1. 디자이너를 만들려면를 `Window_Loaded` 이벤트 처리기에서 텍스트를 두 번 클릭: **MainWindow**.

2. 이벤트 처리기를 다음 코드로 바꿉니다. 이 코드의 *localhost*주소는 사용 중인 개발 컴퓨터의 로컬 호스트 주소로 바꿔야 합니다.

     [!code-csharp[Data_WPFWCF#2](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_2.cs)]
     [!code-vb[Data_WPFWCF#2](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_2.vb)]

## <a name="navigate-sales-records"></a>판매 레코드 탐색

사용자가 단추를 사용 하 여 판매 레코드를 스크롤할 수 있도록 하는 코드를 추가 **\<** and **>** 합니다.

1. 디자이너의 **<** 창 화면에서 단추를 두 번 클릭 합니다.

     Visual Studio가 코드 숨김 파일을 열고 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트에 대해 새 `backButton_Click` 이벤트 처리기를 만듭니다.

2. 다음 코드를 생성된 `backButton_Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[Data_WPFWCF#3](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_3.cs)]
     [!code-vb[Data_WPFWCF#3](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_3.vb)]

3. 디자이너로 돌아가서 단추를 두 번 클릭 **>** 합니다.

     Visual Studio가 코드 숨김 파일을 열고 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트에 대해 새 `nextButton_Click` 이벤트 처리기를 만듭니다.

4. 다음 코드를 생성된 `nextButton_Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[Data_WPFWCF#4](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_4.cs)]
     [!code-vb[Data_WPFWCF#4](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_4.vb)]

## <a name="save-changes-to-sales-records"></a>판매 레코드 변경 내용 저장

사용자가 **변경 내용 저장** 단추를 사용하여 판매 레코드 변경 내용을 확인 및 저장할 수 있도록 하는 코드를 추가합니다.

1. 디자이너에서 **변경 내용 저장** 단추를 두 번 클릭합니다.

     Visual Studio가 코드 숨김 파일을 열고 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트에 대해 새 `saveButton_Click` 이벤트 처리기를 만듭니다.

2. 다음 코드를 `saveButton_Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[Data_WPFWCF#5](../data-tools/codesnippet/CSharp/bind-wpf-controls-to-a-wcf-data-service_5.cs)]
     [!code-vb[Data_WPFWCF#5](../data-tools/codesnippet/VisualBasic/bind-wpf-controls-to-a-wcf-data-service_5.vb)]

## <a name="test-the-application"></a>애플리케이션 테스트

애플리케이션을 빌드하고 실행하여 고객 레코드를 보고 업데이트할 수 있는지 확인합니다.

1. **빌드** 메뉴에서 **솔루션 빌드**를 클릭 합니다. 솔루션이 오류 없이 빌드되는지 확인합니다.

2. **Ctrl** + **F5**를 누릅니다.

     Visual Studio는 디버깅하지 않고 **AdventureWorksService** 프로젝트를 시작합니다.

3. **솔루션 탐색기**에서 **AdventureWorksSalesEditor** 프로젝트를 마우스 오른쪽 단추로 클릭합니다.

4. 오른쪽 클릭 메뉴 (상황에 맞는 메뉴)의 **디버그**에서 **새 인스턴스 시작**을 클릭 합니다.

     애플리케이션이 실행됩니다. 다음을 확인합니다.

    - 판매 주문 ID가 **71774**인 첫 번째 판매 레코드의 서로 다른 데이터 필드가 텍스트 상자에 표시됩니다.

    - 또는 단추를 클릭 **>** **<** 하 여 다른 판매 레코드를 탐색할 수 있습니다.

5. 판매 레코드 중 하나의 **주석** 상자에 텍스트를 입력한 다음, **변경내용 저장**을 클릭합니다.

6. 애플리케이션을 닫았다가 Visual Studio에서 다시 시작합니다.

7. 변경한 판매 레코드로 이동하여 애플리케이션을 닫았다가 다시 열어도 변경 내용이 그대로 유지되는지 확인합니다.

8. 애플리케이션을 닫습니다.

## <a name="next-steps"></a>다음 단계

이 연습을 완료하고 나면 다음과 같은 관련 작업을 수행할 수 있습니다.

- Visual Studio의 **데이터 원본** 창을 사용하여 WPF 컨트롤을 다른 형식의 데이터 원본에 바인딩하는 방법을 알아봅니다. 자세한 내용은 [WPF 컨트롤을 데이터 집합에 바인딩](../data-tools/bind-wpf-controls-to-a-dataset.md)을 참조 하세요.

- Visual Studio의 **데이터 원본** 창을 사용하여 WPF 컨트롤에 관련 데이터(즉, 부모-자식 관계가 있는 데이터)를 표시하는 방법을 알아봅니다. 자세한 내용은 [연습: WPF 응용 프로그램에서 관련 데이터 표시](../data-tools/display-related-data-in-wpf-applications.md)를 참조 하세요.

## <a name="see-also"></a>참조

- [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [데이터 집합에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-a-dataset.md)
- [WCF 개요 (.NET Framework)](/dotnet/framework/data/wcf/wcf-data-services-overview)
- [Entity Framework 개요 (.NET Framework)](/dotnet/framework/data/adonet/ef/overview)
- [데이터 바인딩 개요 (.NET Framework)](/dotnet/desktop-wpf/data/data-binding-overview)
