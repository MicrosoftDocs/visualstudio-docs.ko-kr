---
title: 데이터 집합에 WPF 컨트롤 바인딩 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio], walkthroughs
- WPF Designer, data binding
ms.assetid: 177420b9-568b-4dad-9d16-1b0e98a24d71
caps.latest.revision: 35
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 937e28e923c26a72940b0181da16cf34199bb9aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852153"
---
# <a name="bind-wpf-controls-to-a-dataset"></a>데이터 세트로 WPF 컨트롤 바인딩
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 데이터 바인딩된 컨트롤을 포함하는 WPF 애플리케이션을 만듭니다. 이러한 컨트롤은 데이터 세트에서 캡슐화된 제품 레코드에 바인딩됩니다. 또한 제품을 찾아보고 제품 레코드 변경 내용을 저장할 수 있는 단추도 추가합니다.

 이 연습에서는 다음 작업을 수행합니다.

- AdventureWorksLT 샘플 데이터베이스의 데이터에서 생성되는 데이터 세트 및 WPF 애플리케이션을 만듭니다.

- **데이터 원본** 창에서 WPF 디자이너의 창으로 데이터 테이블을 끌어 데이터 바인딩된 컨트롤 집합을 만듭니다.

- 제품 레코드를 앞뒤로 탐색하는 데 사용할 단추를 만듭니다.

- 사용자가 제품 레코드에 대해 적용한 변경 내용을 데이터 테이블 및 기본 데이터 소스에 저장하는 단추를 만듭니다.

   [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>필수 구성 요소
 이 연습을 완료하려면 다음과 같은 구성 요소가 필요합니다.

- [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]

- AdventureWorksLT 샘플 데이터베이스가 연결된 SQL Server 또는 SQL Server Express의 실행 중인 인스턴스 액세스 권한. [CodePlex 웹 사이트](https://codeplex.com/SqlServerSamples)에서 AdventureWorksLT 데이터베이스를 다운로드할 수 있습니다.

  또한 다음 개념에 대한 지식은 연습을 완료하는 데 반드시 필요하지는 않지만 사전에 파악해 두면 유용할 수 있습니다.

- 데이터 세트 및 TableAdapter. 자세한 내용은 [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)를 참조 하세요.

- WPF 디자이너 사용법. 자세한 내용은 [WPF 및 Silverlight 디자이너 개요](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62)를 참조 하세요.

- WPF 데이터 바인딩. 자세한 내용은 [데이터 바인딩 개요](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211)를 참조 하세요.

## <a name="create-the-project"></a>프로젝트를 만듭니다.
 새 WPF 프로젝트를 만듭니다. 이 프로젝트에 제품 레코드가 표시됩니다.

#### <a name="to-create-the-project"></a>프로젝트를 만들려면

1. Visual Studio를 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 가리킨 다음 **프로젝트**를 클릭합니다.

3. **Visual Basic** 또는 **Visual C#** 을 확장한 다음, **Windows**를 선택합니다.

4. **WPF 애플리케이션** 프로젝트 템플릿을 선택합니다.

5. **이름** 상자에 `AdventureWorksProductsEditor`를 입력하고 **확인**을 클릭합니다.

     Visual Studio에서 프로젝트를 만듭니다 `AdventureWorksProductsEditor` .

## <a name="create-a-dataset-for-the-application"></a>응용 프로그램에 대 한 데이터 집합 만들기
 데이터 바인딩된 컨트롤을 만들려면 먼저 애플리케이션의 데이터 모델을 정의하고 **데이터 원본** 창에 추가해야 합니다. 이 연습에서는 데이터 모델로 사용할 데이터 세트을 만듭니다.

#### <a name="to-create-a-dataset"></a>데이터 세트를 만들려면

1. **데이터** 메뉴에서 **데이터 소스 표시**를 클릭합니다.

     **데이터 원본** 창이 열립니다.

2. **데이터 소스** 창에서 **새 데이터 소스 추가**를 클릭합니다.

     **데이터 소스 구성** 마법사가 열립니다.

3. **데이터 원본 형식 선택** 페이지에서 **데이터베이스**를 선택한 후, **다음**을 클릭합니다.

4. **데이터베이스 모델 선택** 페이지에서 **데이터 세트**를 선택한 후, **다음**을 클릭합니다.

5. **데이터 연결 선택** 페이지에서 다음 옵션 중 하나를 선택합니다.

    - AdventureWorksLT 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택한 후, **다음**을 클릭합니다.

    - **새 연결**을 클릭하고 AdventureWorksLT 데이터베이스에 대한 연결을 만듭니다.

6. **애플리케이션 구성 파일에 연결 문자열 저장** 페이지에서 **예, 다음으로 연결을 저장합니다.** 확인란을 선택한 후, **다음**을 클릭합니다.

7. **데이터베이스 개체 선택** 페이지에서 **테이블**을 확장한 다음, **Product(SalesLT)** 테이블을 선택합니다.

8. **마침**을 클릭합니다.

     Visual Studio는 프로젝트에 새 Adventureworksltdataset.xsd 파일이 파일을 추가 하 고 해당 **adventureworksltdataset.xsd 파일이** 항목을 **데이터 소스** 창에 추가 합니다. AdventureWorksLTDataSet.xsd 파일은 `AdventureWorksLTDataSet`라는 형식화된 데이터 집합과 `ProductTableAdapter`라는 TableAdapter를 정의합니다. 이 연습 뒷부분에서 `ProductTableAdapter`를 사용하여 데이터 세트에 데이터를 채우고 변경 내용을 데이터베이스에 다시 저장합니다.

9. 프로젝트를 빌드합니다.

## <a name="edit-the-default-fill-method-of-the-tableadapter"></a>TableAdapter의 기본 fill 메서드를 편집 합니다.
 데이터 세트을 데이터로 채우려면 `Fill`의 `ProductTableAdapter` 메서드를 사용합니다. 기본적으로 `Fill` 메서드는 Product 테이블의 모든 데이터 행을 `ProductDataTable`의 `AdventureWorksLTDataSet`에 채웁니다. 이 메서드가 행 하위 집합만 반환하도록 수정할 수 있습니다. 이 연습에서는 사진이 있는 제품의 행만 반환하도록 `Fill` 메서드를 수정합니다.

#### <a name="to-load-product-rows-that-have-photos"></a>사진이 있는 제품 행을 로드하려면

1. **솔루션 탐색기**에서 AdventureWorksLTDataSet.xsd 파일을 두 번 클릭합니다.

     데이터 세트 디자이너가 열립니다.

2. 디자이너에서 **Fill, GetData ()** 쿼리를 마우스 오른쪽 단추로 클릭 하 고 **구성**을 선택 합니다.

     **TableAdapter 구성** 마법사가 열립니다.

3. **SQL 문을 입력하세요.** 페이지의 텍스트 상자에서 `SELECT` 문 뒤에 다음 WHERE 절을 추가합니다.

    ```
    WHERE ThumbnailPhotoFileName <> 'no_image_available_small.gif'
    ```

4. **마침**을 클릭합니다.

## <a name="define-the-user-interface"></a>사용자 인터페이스 정의
 WPF 디자이너에서 XAML을 수정하여 창에 여러 단추를 추가합니다. 이 연습 뒷부분에서 사용자가 이러한 단추를 사용해 제품 레코드를 스크롤하고 변경 내용을 저장할 수 있도록 하는 코드를 추가합니다.

#### <a name="to-define-the-user-interface-of-the-window"></a>창의 사용자 인터페이스를 정의하려면

1. **솔루션 탐색기**에서 mainwindow.xaml를 두 번 클릭 합니다.

     WPF 디자이너에서 창이 열립니다.

2. 디자이너의 [!INCLUDE[TLA#tla_titlexaml](../includes/tlasharptla-titlexaml-md.md)] 뷰에서 `<Grid>` 태그 사이에 다음 코드를 추가합니다.

    ```
    <Grid.RowDefinitions>
        <RowDefinition Height="75" />
        <RowDefinition Height="625" />
    </Grid.RowDefinitions>
    <Button HorizontalAlignment="Left" Margin="22,20,0,24" Name="backButton" Width="75"><</Button>
    <Button HorizontalAlignment="Left" Margin="116,20,0,24" Name="nextButton" Width="75">></Button>
    <Button HorizontalAlignment="Right" Margin="0,21,46,24" Name="saveButton" Width="110">Save changes</Button>
    ```

3. 프로젝트를 빌드합니다.

## <a name="createdata-bound-controls"></a>데이터 바인딩된 createdata
 `Product` **데이터 소스** 창에서 WPF Designer로 테이블을 끌어 고객 레코드를 표시 하는 컨트롤을 만듭니다.

#### <a name="to-create-data-bound-controls"></a>데이터 바인딩된 컨트롤을 만들려면

1. **데이터 소스** 창에서 **Product** 노드의 드롭다운 메뉴를 클릭하고 **정보**를 선택합니다.

2. **Product** 노드를 확장합니다.

3. 이 예에서는 일부 필드를 표시하지 않을 것이므로 다음 노드 옆의 드롭다운 메뉴를 클릭하고 **없음**을 선택합니다.

    - ProductCategoryID

    - ProductModelID

    - ThumbnailPhotoFileName

    - rowguid

    - ModifiedDate

4. **ThumbNailPhoto** 노드 옆의 드롭다운 메뉴를 클릭하고 **이미지**를 선택합니다.

    > [!NOTE]
    > 기본적으로 **데이터 원본** 창에서 사진을 나타내는 항목의 기본 컨트롤은 **없음**으로 설정되어 있습니다. 사진은 데이터베이스에서 바이트 배열로 저장되는데 바이트 배열은 단순한 바이트의 배열에서 대형 애플리케이션의 실행 파일에 이르기까지 모든 항목을 포함할 수 있기 때문입니다.

5. **데이터 원본** 창에서 단추가 포함된 행 아래의 그리드 행으로 **Product** 노드를 끌어 옵니다.

     Visual Studio는 **Product** 테이블의 데이터에 바인딩되는 컨트롤 집합을 정의하는 XAML이 생성됩니다. 또한 데이터를 로드하는 코드도 생성됩니다. 생성 된 XAML 및 코드에 대 한 자세한 내용은 [Visual Studio에서 데이터에 WPF 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)을 참조 하세요.

6. 디자이너에서 **제품 ID** 레이블 옆의 텍스트 상자를 클릭합니다.

7. **속성** 창에서 **IsReadOnly** 속성 옆의 확인란을 선택합니다.

## <a name="navigating-product-records"></a>제품 레코드 탐색
 사용자가 단추를 사용 하 여 제품 레코드를 스크롤할 수 있도록 하는 코드를 추가 **\<** and **>** 합니다.

#### <a name="to-enable-users-to-navigate-product-records"></a>사용자가 제품 레코드를 탐색할 수 있도록 설정하려면

1. 디자이너의 **<** 창 화면에서 단추를 두 번 클릭 합니다.

     Visual Studio가 코드 숨김 파일을 열고 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트에 대해 새 `backButton_Click` 이벤트 처리기를 만듭니다.

2. `Window_Loaded` 이벤트 처리기를 수정하여 `ProductViewSource`, `AdventureWorksLTDataSet` 및 `AdventureWorksLTDataSetProductTableAdapter`가 메서드 외부에 있으며 전체 양식에 액세스할 수 있도록 합니다. 이러한 항목을 폼에 대해 전역적으로 선언 하 고 `Window_Loaded` 다음과 비슷한 이벤트 처리기 내에 할당 합니다.

     [!code-csharp[Data_WPFDATASET#1](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#1)]
     [!code-vb[Data_WPFDATASET#1](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#1)]

3. 다음 코드를 `backButton_Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[Data_WPFDATASET#2](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#2)]
     [!code-vb[Data_WPFDATASET#2](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#2)]

4. 디자이너로 돌아가서 단추를 두 번 클릭 **>** 합니다.

5. 다음 코드를 `nextButton_Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[Data_WPFDATASET#3](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#3)]
     [!code-vb[Data_WPFDATASET#3](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#3)]

## <a name="savechanges-to-product-records"></a>Savechanges 제품 레코드
 사용자가 **변경 내용 저장** 단추를 사용하여 제품 레코드 변경 내용을 저장할 수 있도록 하는 코드를 추가합니다.

#### <a name="to-add-the-ability-to-save-changes-to-product-records"></a>제품 레코드 변경 내용을 저장하는 기능을 추가하려면

1. 디자이너에서 **변경 내용 저장** 단추를 두 번 클릭 합니다.

     Visual Studio가 코드 숨김 파일을 열고 <xref:System.Windows.Controls.Primitives.ButtonBase.Click> 이벤트에 대해 새 `saveButton_Click` 이벤트 처리기를 만듭니다.

2. 다음 코드를 `saveButton_Click` 이벤트 처리기에 추가합니다.

     [!code-csharp[Data_WPFDATASET#4](../snippets/csharp/VS_Snippets_ProTools/data_wpfdataset/cs/mainwindow.xaml.cs#4)]
     [!code-vb[Data_WPFDATASET#4](../snippets/visualbasic/VS_Snippets_ProTools/data_wpfdataset/vb/mainwindow.xaml.vb#4)]

    > [!NOTE]
    > 이 예에서는 `Save`의 `TableAdapter` 메서드를 사용하여 변경 내용을 저장합니다. 이 연습에서는 데이터 테이블을 하나만 변경하므로 이러한 방식이 적절합니다. 여러 데이터 테이블의 변경 내용을 저장해야 하는 경우에는 데이터 세트과 함께 생성되는 `UpdateAll`의 `TableAdapterManager` 메서드를 사용할 수 있습니다. 자세한 내용은 [TableAdapterManager 개요](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)를 참조 하세요.

## <a name="test-the-application"></a>애플리케이션 테스트
 애플리케이션을 빌드 및 실행합니다. 제품 레코드를 보고 업데이트할 수 있는지 확인합니다.

#### <a name="to-test-the-application"></a>애플리케이션을 테스트하려면

1. **F5**키를 누릅니다.

     애플리케이션이 빌드되고 실행됩니다. 다음을 확인합니다.

    - 텍스트 상자에 사진이 포함된 첫 번째 제품 레코드의 데이터가 표시됩니다. 이 제품의 ID는 713이고 이름은 **Long-Sleeve Logo Jersey, S**입니다.

    - 또는 단추를 클릭 **>** **<** 하 여 다른 제품 레코드를 탐색할 수 있습니다.

2. 제품 레코드 중 하나에서 **크기** 값을 변경한 다음, **변경 내용 저장**을 클릭합니다.

3. 애플리케이션을 닫은 다음, Visual Studio에서 **F5**를 눌러 애플리케이션을 다시 시작합니다.

4. 변경한 제품 레코드로 이동하여 변경 내용이 유지되었는지를 확인합니다.

5. 애플리케이션을 닫습니다.

## <a name="next-steps"></a>다음 단계
 이 연습을 완료하고 나면 다음과 같은 관련 작업을 수행할 수 있습니다.

- Visual Studio의 **데이터 원본** 창을 사용하여 WPF 컨트롤을 다른 형식의 데이터 원본에 바인딩하는 방법을 알아봅니다. 자세한 내용은 [WPF 컨트롤을 WCF data service에 바인딩](../data-tools/bind-wpf-controls-to-a-wcf-data-service.md)을 참조 하세요.

- Visual Studio의 **데이터 원본** 창을 사용하여 WPF 컨트롤에 관련 데이터(즉, 부모-자식 관계가 있는 데이터)를 표시하는 방법을 알아봅니다. 자세한 내용은 [연습: WPF 응용 프로그램에서 관련 데이터 표시](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [Visual studio에서 데이터에 wpf 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) visual studio에서 [데이터에 wpf 컨트롤 바인딩](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) visual studio의 데이터 [집합 도구](../data-tools/dataset-tools-in-visual-studio.md) [wpf 및 Silverlight 디자이너 개요](https://msdn.microsoft.com/570b7a5c-0c86-4326-a371-c9b63378fc62) [데이터 바인딩](https://msdn.microsoft.com/library/c707c95f-7811-401d-956e-2fffd019a211) 개요
