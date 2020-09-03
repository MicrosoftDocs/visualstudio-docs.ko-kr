---
title: 단순 데이터 바인딩을 지원하는 사용자 정의 컨트롤 만들기
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- custom controls [Visual Studio], Data Sources Window
- Data Sources Window, controls
ms.assetid: b1488366-6dfb-454e-9751-f42fd3f3ddfb
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ace5f9dd2781697525e7041be6cbd8df050bca97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586825"
---
# <a name="create-a-windows-forms-user-control-that-supports-simple-data-binding"></a>단순 데이터 바인딩을 지원하는 Windows Forms 사용자 정의 컨트롤 만들기

Windows 애플리케이션에서 폼에 데이터를 표시할 때는 **도구 상자**에서 기존 컨트롤을 선택할 수도 있고, 표준 컨트롤에서는 제공되지 않는 기능이 애플리케이션에 필요한 경우에는 사용자 지정 컨트롤을 작성할 수도 있습니다. 이 연습에서는 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>를 구현하는 컨트롤을 만드는 방법을 보여줍니다. <xref:System.ComponentModel.DefaultBindingPropertyAttribute>를 구현하는 컨트롤은 데이터에 바인딩할 수 있는 속성 한 개를 포함할 수 있습니다. 이러한 컨트롤은 <xref:System.Windows.Forms.TextBox> 또는 <xref:System.Windows.Forms.CheckBox>와 비슷합니다.

컨트롤 작성에 대 한 자세한 내용은 [디자인 타임에 Windows Forms 컨트롤 개발](/dotnet/framework/winforms/controls/developing-windows-forms-controls-at-design-time)을 참조 하세요.

데이터 바인딩 시나리오에 사용할 컨트롤을 작성할 때는 다음 데이터 바인딩 특성 중 하나를 구현 해야 합니다.

|데이터 바인딩 특성 사용|
| - |
|단일 데이터 열이나 속성을 표시하는 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 등의 단순 컨트롤에 대해 <xref:System.Windows.Forms.TextBox>를 구현합니다. 이 연습 페이지에서 해당 프로세스에 대해 설명합니다.|
|데이터 목록 또는 테이블을 표시하는 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 등의 컨트롤에 대해 <xref:System.Windows.Forms.DataGridView>를 구현합니다. 자세한 내용은 [복합 데이터 바인딩을 지 원하는 사용자 정의 컨트롤 Windows Forms 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md)를 참조 하세요.|
|데이터 목록 또는 테이블을 표시하는 동시에 단일 열이나 속성도 제공해야 하는 <xref:System.ComponentModel.LookupBindingPropertiesAttribute> 등의 컨트롤에 대해 <xref:System.Windows.Forms.ComboBox>를 구현합니다. 자세한 내용은 [조회 데이터 바인딩을 지 원하는 사용자 정의 컨트롤 Windows Forms 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)를 참조 하세요.|

이 연습에서는 테이블 내 단일 열의 데이터를 표시하는 단순 컨트롤을 만듭니다. 이 예에서는 Northwind 샘플 데이터베이스 `Phone` 테이블의 `Customers` 열을 사용합니다. 간단한 사용자 정의 컨트롤은를 사용 하 <xref:System.Windows.Forms.MaskedTextBox> 고 마스크를 전화 번호로 설정 하 여 고객의 전화 번호를 표준 전화 번호 형식으로 표시 합니다.

이 연습에서는 다음 작업을 수행하는 방법을 배웁니다.

- 새 **Windows Forms 응용 프로그램**을 만듭니다.

- 프로젝트에 새 **사용자 정의 컨트롤**을 추가합니다.

- 사용자 컨트롤을 시각적으로 디자인합니다.

- `DefaultBindingProperty` 특성을 구현합니다.

- **데이터 소스 구성** 마법사를 사용 하 여 데이터 집합을 만듭니다.

- 새 컨트롤을 사용하도록 **데이터 원본** 창의 **Phone** 열을 설정합니다.

- 새 컨트롤에 데이터를 표시할 폼을 만듭니다.

## <a name="prerequisites"></a>필수 구성 요소

이 연습에서는 SQL Server Express LocalDB 및 Northwind 샘플 데이터베이스를 사용 합니다.

1. LocalDB SQL Server Express 없는 경우 [SQL Server Express 다운로드 페이지](https://www.microsoft.com/sql-server/sql-server-editions-express)에서 또는 **Visual Studio 설치 관리자**를 통해 설치 합니다. **Visual Studio 설치 관리자**에서 **데이터 저장소 및 처리** 워크 로드의 일부로 또는 개별 구성 요소로 SQL Server Express LocalDB를 설치할 수 있습니다.

2. 다음 단계를 수행 하 여 Northwind 샘플 데이터베이스를 설치 합니다.

    1. Visual Studio에서 **SQL Server 개체 탐색기** 창을 엽니다. SQL Server 개체 탐색기는 **데이터 저장소 및 처리** 워크 로드의 일부로 **Visual Studio 설치 관리자**에 설치 됩니다. **SQL Server** 노드를 확장 합니다. LocalDB 인스턴스를 마우스 오른쪽 단추로 클릭 하 고 **새 쿼리**를 선택 합니다.

       쿼리 편집기 창이 열립니다.

    2. [Northwind transact-sql 스크립트](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) 를 클립보드에 복사 합니다. 이 T-sql 스크립트는 Northwind 데이터베이스를 처음부터 만들어 데이터로 채웁니다.

    3. T-sql 스크립트를 쿼리 편집기에 붙여 넣은 다음 **실행** 단추를 선택 합니다.

       잠시 후 쿼리 실행이 완료 되 고 Northwind 데이터베이스가 만들어집니다.

## <a name="create-a-windows-forms-application"></a>Windows Forms 애플리케이션 만들기

첫 번째 단계는 **Windows Forms 응용 프로그램**을 만드는 것입니다.

1. Visual Studio의 **파일** 메뉴에서 **새로 만들기** > **프로젝트**를 차례로 선택합니다.

2. 왼쪽 창에서 **Visual c #** 또는 **Visual Basic** 을 확장 한 다음 **Windows 데스크톱**을 선택 합니다.

3. 가운데 창에서 **Windows Forms 앱** 프로젝트 형식을 선택 합니다.

4. 프로젝트 이름을 **SimpleControlWalkthrough**로 지정한 다음 **확인**을 선택 합니다.

     **SimpleControlWalkthrough** 프로젝트가 만들어져 **솔루션 탐색기**에 추가됩니다.

## <a name="add-a-user-control-to-the-project"></a>프로젝트에 사용자 정의 컨트롤 추가

이 연습에서는 **사용자 정의 컨트롤**에서 간단한 데이터 바인딩 가능 컨트롤을 만듭니다. **SimpleControlWalkthrough** 프로젝트에 **사용자 정의 컨트롤** 항목을 추가 합니다.

1. **프로젝트** 메뉴에서 **사용자 컨트롤 추가**를 선택합니다.

2. 이름 영역에 **PhoneNumberBox**를 입력하고 **추가**를 클릭합니다.

     **PhoneNumberBox** 컨트롤이 **솔루션 탐색기**에 추가되고 디자이너에서 열립니다.

## <a name="design-the-phonenumberbox-control"></a>PhoneNumberBox 컨트롤 디자인

이 연습은 기존를 확장 <xref:System.Windows.Forms.MaskedTextBox> 하 여 **PhoneNumberBox** 컨트롤을 만듭니다.

1. <xref:System.Windows.Forms.MaskedTextBox>도구 상자**에서 사용자 컨트롤의 디자인 화면으로 **를 끌어 옵니다.

2. 방금 끌어 온 <xref:System.Windows.Forms.MaskedTextBox>에서 스마트 태그를 선택하고 **마스크 설정**을 선택합니다.

3. **입력 마스크** 대화 상자에서 **전화 번호**를 선택하고 **확인**을 클릭하여 마스크를 설정합니다.

## <a name="add-the-required-data-binding-attribute"></a>필요한 데이터 바인딩 특성 추가

데이터 바인딩을 지원하는 단순 컨트롤에 대해 <xref:System.ComponentModel.DefaultBindingPropertyAttribute>를 구현합니다.

1. **PhoneNumberBox** 컨트롤을 코드 보기로 전환 합니다. (**보기** 메뉴에서 **코드**를 선택합니다.)

2. **PhoneNumberBox** 의 코드를 다음으로 바꿉니다.

     [!code-csharp[VbRaddataDisplaying#3](../data-tools/codesnippet/CSharp/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.cs)]
     [!code-vb[VbRaddataDisplaying#3](../data-tools/codesnippet/VisualBasic/create-a-windows-forms-user-control-that-supports-simple-data-binding_1.vb)]

3. **빌드** 메뉴에서 **솔루션 빌드**를 선택합니다.

## <a name="create-a-data-source-from-your-database"></a>데이터베이스에서 데이터 원본 만들기

이 단계에서는 **데이터 원본 구성** 마법사를 사용하여 Northwind 샘플 데이터베이스의 `Customers` 테이블을 기반으로 하는 데이터 원본을 만듭니다. 연결을 만들려면 Northwind 샘플 데이터베이스에 액세스해야 합니다. Northwind 샘플 데이터베이스를 설정 하는 방법에 대 한 자세한 내용은 [방법: 샘플 데이터베이스 설치](../data-tools/installing-database-systems-tools-and-samples.md)를 참조 하세요.

1. 데이터 **소스** 창을 열려면 **데이터** 메뉴에서 **데이터 소스 표시**를 클릭 합니다.

2. **데이터 원본** 창에서 **새 데이터 원본 추가**를 선택하여 **데이터 원본 구성** 마법사를 시작합니다.

3. **데이터 원본 형식 선택** 페이지에서 **데이터베이스**를 선택한 후, **다음**을 클릭합니다.

4. **데이터 연결 선택** 페이지에서 다음 중 한 가지를 수행합니다.

    - Northwind 샘플 데이터베이스에 대한 데이터 연결이 드롭다운 목록에 표시되면 해당 연결을 선택합니다.

    - **새 연결**을 선택하여 **연결 추가/수정** 대화 상자를 시작합니다.

5. 데이터베이스에 암호가 필요하면 중요한 데이터를 포함하는 옵션을 선택한 후, **다음**을 클릭합니다.

6. **응용 프로그램 구성 파일에 연결 문자열 저장** 페이지에서 **다음**을 클릭 합니다.

7. **데이터베이스 개체 선택** 페이지에서 **테이블** 노드를 확장합니다.

8. `Customers` 테이블을 선택한 다음, **마침**을 클릭합니다.

     **NorthwindDataSet** 가 프로젝트에 추가 되 고 `Customers` 테이블이 **데이터 소스** 창에 표시 됩니다.

## <a name="set-the-phone-column-to-use-the-phonenumberbox-control"></a>PhoneNumberBox 컨트롤을 사용 하도록 phone 열 설정

**데이터 소스** 창에서 항목을 폼으로 끌기 전에 만들 컨트롤을 설정할 수 있습니다.

1. 디자이너에서 **Form1**을 엽니다.

2. **데이터 원본** 창에서 **Customers** 노드를 확장합니다.

3. **Customers** 노드에서 드롭다운 화살표를 클릭하고 컨트롤 목록에서 **정보**를 선택합니다.

4. **Phone** 열에서 드롭다운 화살표를 클릭하고 **Customize**를 선택합니다.

5. **데이터 UI 사용자 지정 옵션** 대화 상자의 **연결된 컨트롤** 목록에서 **PhoneNumberBox**를 선택합니다.

6. **Phone** 열에서 드롭다운 화살표를 클릭하고 **PhoneNumberBox**를 선택합니다.

## <a name="add-controls-to-the-form"></a>폼에 컨트롤 추가

**데이터 원본** 창에서 폼으로 항목을 끌어서 데이터 바인딩된 컨트롤을 만들 수 있습니다.

폼에서 데이터 바인딩된 컨트롤을 만들려면 주 **Customers** 노드를 **데이터 소스** 창에서 폼으로 끌고 **PhoneNumberBox** 컨트롤이 **휴대폰** 열의 데이터를 표시 하는 데 사용 되는지 확인 합니다.

설명 레이블이 있는 데이터 바인딩된 컨트롤이 레코드 탐색을 위한 도구 모음인 <xref:System.Windows.Forms.BindingNavigator>와 함께 폼에 나타납니다. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> 및 <xref:System.Windows.Forms.BindingNavigator>가 구성 요소 트레이에 나타납니다.

## <a name="run-the-application"></a>애플리케이션 실행

**F5** 키를 눌러 애플리케이션을 실행합니다.

## <a name="next-steps"></a>다음 단계

애플리케이션 요구 사항에 따라 데이터 바인딩을 지원하는 컨트롤을 만든 후 몇 단계를 더 수행해야 할 수도 있습니다. 일반적으로 수행하는 몇 가지 단계는 다음과 같습니다.

- 다른 애플리케이션에서 다시 사용할 수 있도록 컨트롤 라이브러리에 사용자 지정 컨트롤을 배치합니다.

- 보다 복잡한 데이터 바인딩 시나리오를 지원하는 컨트롤을 만듭니다. 자세한 내용은 [복합 데이터 바인딩을 지 원하는 Windows Forms 사용자 정의 컨트롤 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-complex-data-binding.md) 및 [조회 데이터 바인딩을 지 원하는 Windows Forms 사용자 정의 컨트롤 만들기](../data-tools/create-a-windows-forms-user-control-that-supports-lookup-data-binding.md)를 참조 하세요.

## <a name="see-also"></a>추가 정보

- [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)
