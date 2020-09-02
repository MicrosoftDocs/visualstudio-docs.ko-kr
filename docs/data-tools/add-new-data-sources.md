---
title: 새 데이터 원본 추가
ms.date: 11/21/2018
ms.topic: how-to
f1_keywords:
- vs.datasource.datasourcefieldspicker
helpviewer_keywords:
- data [Visual Studio], data sources
- data sources
ms.assetid: ed28c625-bb89-4037-bfde-cfa435d182a2
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 2e8ad5bf65ad25d197785c3e720ec01c7bdc6f9d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85283049"
---
# <a name="add-new-data-sources"></a>새 데이터 원본 추가

:::moniker range="vs-2019"
> [!NOTE]
> 이 문서에서 설명 하는 기능은 .NET Framework Windows Forms 및 WPF 개발에 적용 됩니다. Visual Studio 2019 (및 이전 버전)에서 WPF 및 Windows Forms에 대 한 .NET Core 개발에는 기능이 지원 되지 않습니다.
:::moniker-end

Visual Studio에서 .NET 데이터 도구를 사용 하는 경우 데이터 *소스* 라는 용어는 데이터 저장소에 연결 되 고 .net 응용 프로그램에서 데이터를 사용할 수 있도록 하는 .net 개체를 나타냅니다. Visual Studio 디자이너 **는 데이터 소스 창에서** 데이터베이스 개체를 끌어서 놓을 때 데이터 원본의 출력을 사용 하 여 데이터를 폼에 바인딩하는 상용구 코드를 생성할 수 있습니다. 이러한 종류의 데이터 소스는 다음과 같을 수 있습니다.

- 특정 종류의 데이터베이스와 연결 된 Entity Framework 모델의 클래스입니다.

- 일부 종류의 데이터베이스와 연결 된 데이터 집합입니다.

- WCF (Windows Communication Foundation) 데이터 서비스 또는 REST 서비스와 같은 네트워크 서비스를 나타내는 클래스입니다.

- SharePoint 서비스를 나타내는 클래스입니다.

- 솔루션의 클래스 또는 컬렉션입니다.

> [!NOTE]
> 데이터 바인딩 기능, 데이터 집합, Entity Framework LINQ to SQL, WCF 또는 SharePoint를 사용 하지 않는 경우 "데이터 원본"의 개념이 적용 되지 않습니다. SQLCommand 개체를 사용 하 여 데이터베이스에 직접 연결 하 고 데이터베이스와 직접 통신 합니다.

Windows Forms 또는 Windows Presentation Foundation 응용 프로그램에서 **데이터 소스 구성 마법사** 를 사용 하 여 데이터 원본을 만들고 편집할 수 있습니다. Entity Framework의 경우 먼저 엔터티 클래스를 만든 다음 **프로젝트**  >  **새 데이터 소스 추가** (이 문서의 뒷부분에서 자세히 설명)를 선택 하 여 마법사를 시작 합니다.

![데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>데이터 소스 창

데이터 원본을 만든 후에는 **데이터** 원본 도구 창에 표시 됩니다.

> [!TIP]
> **데이터 소스** 창을 열려면 프로젝트가 열려 있는지 확인 하 고 **Shift**키를 누르거나 + **Alt** + **D** **View**  >  **다른 Windows**  >  **데이터 원본**보기를 선택 합니다.

**데이터 소스 창에서** 폼 디자인 화면 또는 컨트롤로 데이터 소스를 끌어올 수 있습니다. 이렇게 하면 데이터 저장소의 데이터를 표시 하는 상용구 코드가 생성 됩니다.

다음 그림에서는 Windows form에 끌어 놓은 데이터 집합을 보여 줍니다. 응용 프로그램에서 **F5 키** 를 선택 하면 기본 데이터베이스의 데이터가 폼의 컨트롤에 표시 됩니다.

![데이터 원본 끌기 작업](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>데이터베이스 또는 데이터베이스 파일에 대 한 데이터 원본

데이터베이스나 데이터베이스 파일에 대 한 데이터 원본으로 사용할 데이터 집합 또는 Entity Framework 모델을 만들 수 있습니다.

### <a name="dataset"></a>데이터 세트

데이터 집합을 데이터 원본으로 만들려면 **프로젝트**새 데이터 소스 추가를 선택 하 여 **데이터 소스 구성 마법사** 를 실행 합니다  >  **Add New Data Source**. **데이터베이스** 데이터 원본 유형을 선택 하 고 메시지의 지시에 따라 새 데이터베이스 연결 또는 데이터베이스 파일을 지정 합니다.

### <a name="entity-classes"></a>엔터티 클래스

Entity Framework 모델을 데이터 원본으로 만들려면 다음을 수행 합니다.

1. **엔터티 데이터 모델 마법사** 를 실행 하 여 엔터티 클래스를 만듭니다. **프로젝트**  >  **추가 새 항목**  >  **ADO.NET 엔터티 데이터 모델**를 선택 합니다.

   ![새 Entity Framework 모델 프로젝트 항목](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. 모델을 생성 하려는 방법을 선택 합니다.

   ![엔터티 데이터 모델 마법사](../data-tools/media/raddata-entity-data-model-wizard.png)

1. 모델을 데이터 원본으로 추가 합니다. 생성 된 클래스는 **개체** 범주를 선택할 때 **데이터 소스 구성 마법사** 에 나타납니다.

   ![엔터티 클래스를 사용 하는 데이터 소스 구성 마법사](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>서비스에 대 한 데이터 원본

서비스에서 데이터 소스를 만들려면 **데이터 소스 구성 마법사** 를 실행 하 고 **서비스** 데이터 원본 유형을 선택 합니다. 이는 **솔루션 탐색기** 에서 프로젝트를 마우스 오른쪽 단추로 클릭 하 고 **서비스 참조 추가**를 선택 하 여 액세스할 수도 있는 **서비스 참조 추가** 대화 상자의 바로 가기입니다.

서비스에서 데이터 소스를 만들면 Visual Studio에서 프로젝트에 서비스 참조를 추가 합니다. 또한 Visual Studio는 서비스에서 반환 하는 개체에 해당 하는 프록시 개체를 만듭니다. 예를 들어 데이터 집합을 반환 하는 서비스는 프로젝트에서 데이터 집합으로 표시 됩니다. 특정 형식을 반환 하는 서비스는 프로젝트에서 반환 된 형식으로 표시 됩니다.

다음 유형의 서비스에서 데이터 원본을 만들 수 있습니다.

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF 서비스](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- 웹 서비스

    > [!NOTE]
    > **데이터 소스** 창에 표시 되는 항목은 서비스에서 반환 하는 데이터에 따라 달라 집니다. **데이터 원본 구성 마법사**에서 바인딩 가능한 개체를 만들기에 충분한 정보를 제공하지 않는 서비스도 있습니다. 예를 들어 서비스에서 형식화 되지 않은 데이터 집합을 반환 하는 경우 마법사를 완료 하면 **데이터 소스** 창에 항목이 표시 되지 않습니다. 이는 형식화 되지 않은 데이터 집합이 스키마를 제공 하지 않으므로 마법사에 데이터 소스를 만드는 데 충분 한 정보가 없기 때문입니다.

## <a name="data-source-for-an-object"></a>개체에 대 한 데이터 원본

**데이터 소스 구성 마법사** 를 실행 한 다음 **개체** 데이터 소스 형식을 선택 하 여 하나 이상의 public 속성을 노출 하는 개체에서 데이터 소스를 만들 수 있습니다. 개체의 모든 public 속성이 **데이터 소스** 창에 표시 됩니다. Entity Framework를 사용 하 고 모델을 생성 한 경우 응용 프로그램의 데이터 소스인 엔터티 클래스를 찾을 수 있습니다.

**데이터 개체 선택** 페이지에서 트리 뷰의 노드를 확장 하 여 바인딩할 개체를 찾습니다. 트리 뷰에는 프로젝트 및 프로젝트에서 참조 하는 어셈블리 및 기타 프로젝트에 대 한 노드가 포함 됩니다.

트리 뷰에 표시 되지 않는 어셈블리 또는 프로젝트의 개체에 바인딩하려면 참조 **추가** 를 클릭 하 고 **참조 추가 대화 상자** 를 사용 하 여 어셈블리 또는 프로젝트에 대 한 참조를 추가 합니다. 참조를 추가한 후에는 어셈블리 또는 프로젝트가 트리 뷰에 추가 됩니다.

> [!NOTE]
> 개체를 포함 하는 프로젝트를 작성 한 후에는 개체를 트리 뷰에 표시 해야 할 수 있습니다.

> [!NOTE]
> 끌어서 놓기 데이터 바인딩을 지원 하려면 또는 인터페이스를 구현 하는 개체에 <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> 기본 생성자가 있어야 합니다. 그렇지 않으면 Visual Studio에서 데이터 소스 개체를 인스턴스화할 수 없으며, 항목을 디자인 화면으로 끌 때 오류가 표시 됩니다.

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint 목록에 대 한 데이터 원본

**데이터 소스 구성 마법사** 를 실행 하 고 **sharepoint** 데이터 원본 유형을 선택 하 여 sharepoint 목록에서 데이터 원본을 만들 수 있습니다. SharePoint는 WCF Data Services를 통해 데이터를 노출 하므로 SharePoint 데이터 소스를 만드는 것은 서비스에서 데이터 원본을 만드는 것과 동일 합니다. **데이터 소스 구성 마법사** 에서 **sharepoint** 항목을 선택 하면 SharePoint 서버를 가리켜 sharepoint 데이터 서비스에 연결 하는 **서비스 참조 추가** 대화 상자가 열립니다. 이를 위해서는 SharePoint SDK가 필요 합니다.

## <a name="see-also"></a>추가 정보

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
