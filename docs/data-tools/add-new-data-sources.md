---
title: 새 데이터 원본 추가
description: Visual Studio 새 데이터 원본을 추가합니다. 데이터 원본은 데이터 저장소에 연결하고 .NET 애플리케이션에서 데이터를 사용할 수 있도록 하는 .NET 개체입니다.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: a377acba7b8c64503e5e5f821b5f3f833a8d73b2
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112308053"
---
# <a name="add-new-data-sources"></a>새 데이터 원본 추가

:::moniker range=">=vs-2019"
> [!NOTE]
> 이 문서에서 설명하는 기능은 .NET Framework Windows Forms 및 WPF 개발에 적용합니다. WPF 및 Windows Forms .NET Core 개발에는 기능이 지원되지 않습니다.
:::moniker-end

Visual Studio .NET 데이터 도구의 컨텍스트에서 *데이터 원본이라는* 용어는 데이터 저장소에 연결하고 .NET 애플리케이션에서 데이터를 사용할 수 있도록 하는 .NET 개체를 나타냅니다. Visual Studio 디자이너는 데이터 원본 창에서 데이터베이스 개체를 끌어서 놓을 때 데이터를 폼에 바인딩하는 상용구 코드를 생성하기 위해 **데이터 원본의 출력을** 사용할 수 있습니다. 이러한 종류의 데이터 원본은 다음과 같을 수 있습니다.

- 일종의 데이터베이스와 연결된 Entity Framework 모델의 클래스입니다.

- 일종의 데이터베이스와 연결된 데이터 세트입니다.

- WCF(Windows Communication Foundation) 데이터 서비스 또는 REST 서비스와 같은 네트워크 서비스를 나타내는 클래스입니다.

- SharePoint 서비스를 나타내는 클래스입니다.

- 솔루션의 클래스 또는 컬렉션입니다.

> [!NOTE]
> 데이터 바인딩 기능, 데이터 세트, Entity Framework, LINQ to SQL, WCF 또는 SharePoint를 사용하지 않는 경우 "데이터 원본"의 개념은 적용되지 않습니다. SQLCommand 개체를 사용하여 데이터베이스에 직접 연결하고 데이터베이스와 직접 통신하기만 합니다.

Windows Forms 또는 Windows Presentation Foundation 애플리케이션에서 **데이터 원본 구성 마법사를** 사용하여 데이터 원본을 만들고 편집합니다. Entity Framework 경우 먼저 엔터티 클래스를 만든 다음 프로젝트 새 데이터 원본 추가를 선택하여 **마법사를**  >   시작합니다(이 문서의 후반부에서 자세히 설명).

![데이터 소스 구성 마법사](../data-tools/media/data-source-configuration-wizard.png)

## <a name="data-sources-window"></a>데이터 소스 창

데이터 원본을 만든 후 **데이터 원본** 도구 창에 표시됩니다.

> [!TIP]
> **데이터 원본** 창을 열려면 프로젝트가 열려 있는지 확인한 다음 **Shift** + **Alt** + **D를** 누르거나 다른 Windows 데이터 원본 **보기를**  >    >  **선택합니다.**

데이터 원본 창에서 양식 디자인 표면 또는 컨트롤로 **데이터 원본을** 끌 수 있습니다. 이렇게 하면 데이터 저장소의 데이터를 표시하는 상용구 코드가 생성됩니다.

다음 그림에서는 Windows 양식에 삭제된 데이터 세트를 보여 주는 그림입니다. 애플리케이션에서 **F5를** 선택하면 기본 데이터베이스의 데이터가 폼의 컨트롤에 표시됩니다.

![데이터 원본 끌기 작업](../data-tools/media/raddata-data-source-drag-operation.png)

## <a name="data-source-for-a-database-or-a-database-file"></a>데이터베이스 또는 데이터베이스 파일의 데이터 원본

데이터베이스 또는 데이터베이스 파일의 데이터 원본으로 사용할 데이터 세트 또는 Entity Framework 모델을 만들 수 있습니다.

### <a name="dataset"></a>데이터 세트

데이터 세트를 데이터 원본으로 만들려면 **프로젝트** 새 데이터 원본 추가 를 선택하여 **데이터 원본 구성 마법사를** 실행합니다.  >   **데이터베이스** 데이터 원본 유형을 선택하고 프롬프트에 따라 새 또는 기존 데이터베이스 연결 또는 데이터베이스 파일을 지정합니다.

### <a name="entity-classes"></a>엔터티 클래스

데이터 원본으로 Entity Framework 모델을 만들려면 다음을 수행합니다.

1. 엔터티 데이터 모델 **마법사를** 실행하여 엔터티 클래스를 만듭니다. **프로젝트**  >  **새 항목 추가**  >  **ADO.NET 엔터티 데이터 모델** 선택합니다.

   ![새 Entity Framework 모델 프로젝트 항목](../data-tools/media/raddata-new-entity-framework-model-project-item.png)

1. 모델을 생성할 방법을 선택합니다.

   ![엔터티 데이터 모델 마법사](../data-tools/media/raddata-entity-data-model-wizard.png)

1. 모델을 데이터 원본으로 추가합니다. 생성된 클래스는 **개체** 범주를 선택하면 **데이터 원본 구성 마법사에** 표시됩니다.

   ![엔터티 클래스가 있는 데이터 원본 구성 마법사](../data-tools/media/raddata-data-source-configuration-wizard-with-entity-classes.png)

## <a name="data-source-for-a-service"></a>서비스의 데이터 원본

서비스에서 데이터 원본을 만들려면 **데이터 원본 구성 마법사를** 실행하고 **서비스** 데이터 원본 유형을 선택합니다. 이는 **서비스 참조 추가** 대화 상자의 바로 가기일 뿐이며, **솔루션 탐색기** 프로젝트를 마우스 오른쪽 단추로 클릭하고 서비스 **참조 추가를** 선택하여 액세스할 수도 있습니다.

서비스에서 데이터 원본을 만들 때 Visual Studio 프로젝트에 서비스 참조를 추가합니다. Visual Studio 서비스에서 반환하는 개체에 해당하는 프록시 개체도 만듭니다. 예를 들어 데이터 세트를 반환하는 서비스는 프로젝트에 데이터 세트로 표시됩니다. 특정 형식을 반환하는 서비스는 반환된 형식으로 프로젝트에 표시됩니다.

다음 유형의 서비스에서 데이터 원본을 만들 수 있습니다.

- [WCF Data Services](/dotnet/framework/data/wcf/wcf-data-services-overview)

- [WCF 서비스](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- 웹 서비스

    > [!NOTE]
    > **데이터 원본** 창에 표시되는 항목은 서비스가 반환하는 데이터에 따라 달라집니다. **데이터 원본 구성 마법사** 에서 바인딩 가능한 개체를 만들기에 충분한 정보를 제공하지 않는 서비스도 있습니다. 예를 들어 서비스에서 형식화되지 않은 데이터 세트를 반환하는 경우 마법사를 완료할 때 **데이터 원본** 창에 항목이 표시되지 않습니다. 이는 형식화되지 않은 데이터 세트가 스키마를 제공하지 않으므로 마법사에 데이터 원본을 만들기에 충분한 정보가 없기 때문입니다.

## <a name="data-source-for-an-object"></a>개체에 대한 데이터 원본

데이터 원본 **구성 마법사를** 실행한 다음 개체 데이터 원본 형식을 선택하여 하나 이상의 공용 속성을 노출하는 **개체에서** 데이터 원본을 만들 수 있습니다. 개체의 모든 공용 속성이 **데이터 원본** 창에 표시됩니다. Entity Framework 사용하고 모델을 생성한 경우 애플리케이션의 데이터 원본인 엔터티 클래스를 찾을 수 있습니다.

데이터 **개체 선택** 페이지에서 트리 뷰의 노드를 확장하여 바인딩할 개체를 찾습니다. 트리 뷰에는 프로젝트에 대한 노드와 프로젝트에서 참조하는 어셈블리 및 기타 프로젝트에 대한 노드가 포함됩니다.

트리 뷰에 표시되지 않는 어셈블리 또는 프로젝트의 개체에 바인딩하려면 **참조 추가를** 클릭하고 **참조 추가 대화 상자를** 사용하여 어셈블리 또는 프로젝트에 대한 참조를 추가합니다. 참조를 추가하면 어셈블리 또는 프로젝트가 트리 뷰에 추가됩니다.

> [!NOTE]
> 개체가 트리 뷰에 표시되기 전에 개체가 포함된 프로젝트를 빌드해야 할 수 있습니다.

> [!NOTE]
> 끌어서 놓기 데이터 바인딩을 지원하려면 또는 인터페이스를 구현하는 <xref:System.ComponentModel.ITypedList> <xref:System.ComponentModel.IListSource> 개체에 기본 생성자가 있어야 합니다. 그렇지 않으면 Visual Studio 데이터 소스 개체를 인스턴스화할 수 없으며 항목을 디자인 화면으로 끌 때 오류가 표시됩니다.

## <a name="data-source-for-a-sharepoint-list"></a>SharePoint 목록의 데이터 원본

데이터 원본 **구성 마법사를** 실행하고 SharePoint 데이터 원본 유형을 선택하여 **SharePoint** 목록에서 데이터 원본을 만들 수 있습니다. SharePoint는 WCF Data Services 통해 데이터를 노출하므로 SharePoint 데이터 원본을 만드는 것은 서비스에서 데이터 원본을 만드는 것과 동일합니다. **데이터 원본 구성 마법사에서** **SharePoint** 항목을 선택하면 **sharePoint** 서버를 가리켜 SharePoint 데이터 서비스에 연결하는 서비스 참조 추가 대화 상자가 열립니다. 이렇게 하려면 SharePoint SDK가 필요합니다.

## <a name="see-also"></a>참조

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
