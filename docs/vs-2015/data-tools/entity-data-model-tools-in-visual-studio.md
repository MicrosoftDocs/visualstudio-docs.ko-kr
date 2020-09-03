---
title: 엔터티 데이터 모델 도구
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
caps.latest.revision: 24
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d663b86603145f8a665f189e5abfbfa2b0b360ae
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672387"
---
# <a name="entity-data-model-tools-in-visual-studio"></a>Visual Studio의 엔터티 데이터 모델 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Entity Framework는 .NET 개발자가 도메인별 개체를 사용 하 여 관계형 데이터 작업을 수행할 수 있도록 하는 개체-관계형 매핑 기술입니다. 여기서는 개발자가 일반적으로 작성해야 하는 대부분의 데이터 액세스 코드가 필요하지 않습니다. Entity Framework은 새로운 .NET 응용 프로그램에 권장 되는 ORM (개체 관계형 매핑) 모델링 기술입니다.

 3 월 2016 현재 릴리스된 버전은 [Entity Framework 6](https://msdn.microsoft.com/data/ef) 입니다. [Entity Framework 7](https://docs.efproject.net/en/latest/) 은 시험판에 있습니다.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 도구는 응용 프로그램을 빌드하는 데 도움이 되도록 설계 되었습니다 [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] . 도구에 대 한 전체 설명서는 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] [Entity Framework](https://msdn.microsoft.com/data/jj590134)있습니다.

 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)]도구를 사용 하면 기존 데이터베이스에서 *개념적 모델* 을 만든 다음 개념적 모델을 그래픽으로 시각화 하 고 편집할 수 있습니다. 또는 먼저 개념적 모델을 그래픽으로 만든 후 모델을 지원하는 데이터베이스를 생성할 수 있습니다. 이 두 경우 모두 기본 데이터베이스가 변경될 때 모델을 자동으로 업데이트하고 애플리케이션에 대한 개체 계층 코드를 자동으로 생성할 수 있습니다. 데이터베이스 생성 및 개체 계층 코드 생성 작업은 사용자 지정할 수 있습니다.

 다음은 Visual Studio 2015에서 엔터티 데이터 모델 도구를 구성 하는 특정 도구입니다.

- [!INCLUDE[vstecado](../includes/vstecado-md.md)] ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 디자이너** (**Entity Designer**)를 사용 하 여 엔터티, 연결, 매핑 및 상속 관계를 시각적으로 만들고 수정할 수 있습니다. 또한 **Entity Designer** 는 [!INCLUDE[TLA#tla_cshrp](../includes/tlasharptla-cshrp-md.md)] 또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] 개체 계층 코드를 생성 합니다.

- ** [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 마법사** 를 사용 하 여 기존 데이터베이스에서 개념적 모델을 생성 하 고 응용 프로그램에 데이터베이스 연결 정보를 추가할 수 있습니다.

- **데이터베이스 만들기 마법사** 를 사용 하 여 먼저 개념적 모델을 만든 다음 모델을 지 원하는 데이터베이스를 만들 수 있습니다.

- 기본 데이터베이스가 변경 된 경우 **모델 업데이트 마법사** 를 사용 하 여 개념적 모델, 저장소 모델 및 매핑을 업데이트할 수 있습니다.

  > [!NOTE]
  > Visual Studio 2010부터 도구는를 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] 지원 하지 않습니다 [!INCLUDE[ss2k](../includes/ss2k-md.md)] .

  도구는 .edmx 파일을 생성 하거나 수정 합니다. 이 파일에는 개념적 모델, 저장소 모델 및 두 모델 간의 매핑을 설명 하는 정보가 포함 되어 있습니다. 자세한 내용은  [EDMX](https://msdn.microsoft.com/data/jj650889.aspx)를 참조 하세요.

  Entity Framework Power Tools는 엔터티 데이터 모델를 사용 하는 응용 프로그램을 빌드하는 데 도움이 됩니다. 도구는 개념적 모델을 생성 하 고, 기존 모델의 유효성을 검사 하 고, 개념적 모델을 기반으로 하는 개체 클래스가 포함 된 소스 코드 파일을 생성 하 고, 모델이 생성 하는 뷰를 포함 하는 소스 코드 파일을 생성할 수 있습니다. 자세한 내용은 [미리 생성 된 매핑 뷰](https://msdn.microsoft.com/data/dn469601.aspx)를 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[ADO.NET Entity Framework](https://msdn.microsoft.com/library/a437041f-6899-4ae7-96ce-aabf528d7205)|에서 제공 하는 도구를 사용 하 여 응용 프로그램을 만드는 방법을 설명 합니다 [!INCLUDE[adonet_edm](../includes/adonet-edm-md.md)] [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] .|
|[엔터티 데이터 모델](https://msdn.microsoft.com/library/2dda3d5b-4582-4ba0-a91d-fcd7a1498137)|에서 빌드된 응용 프로그램에서 사용 하는 데이터 작업을 위한 링크와 정보를 제공 [!INCLUDE[adonet_ef](../includes/adonet-ef-md.md)] 합니다.|
|[전체 .NET (콘솔, WinForms, WPF 등)에서 시작](/ef/ef6/get-started)|Entity Framework 7을 사용 하는 .NET 데스크톱 응용 프로그램을 만드는 방법에 대 한 자습서를 제공 합니다.|
|[ASP.NET 5 응용 프로그램을 새 데이터베이스로](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html)|Entity Framework 7을 사용 하 여 새 ASP.NET 5 응용 프로그램을 만드는 방법을 설명 합니다.|

## <a name="see-also"></a>관련 항목
 [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
