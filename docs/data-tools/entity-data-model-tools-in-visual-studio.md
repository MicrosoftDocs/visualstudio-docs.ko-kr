---
title: Entity Framework 도구
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 1b06b573-84aa-4458-b3f5-e238df47bf45
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 250f1ad55f8d60396b8423098e58801d0ed81e77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75916730"
---
# <a name="entity-framework-tools-in-visual-studio"></a>Visual Studio의 Entity Framework Tools

Entity Framework는 .NET 개발자가 도메인별 개체를 사용 하 여 관계형 데이터 작업을 수행할 수 있도록 하는 개체-관계형 매핑 기술입니다. 여기서는 개발자가 일반적으로 작성해야 하는 대부분의 데이터 액세스 코드가 필요하지 않습니다. Entity Framework은 새로운 .NET 응용 프로그램에 권장 되는 ORM (개체 관계형 매핑) 모델링 기술입니다.

Entity Framework Tools는 EF (Entity Framework) 응용 프로그램을 빌드하는 데 도움이 되도록 설계 되었습니다. Entity Framework에 대 한 전체 설명서는 [개요-EF 6](/ef/ef6/)에서 확인할 수 있습니다.

  > [!NOTE]
  > 이 페이지에 설명 된 Entity Framework Tools는 EF Core에서 지원 되지 않는 .edmx 파일을 생성 하는 데 사용 됩니다 *.* 기존 데이터베이스에서 EF Core 모델을 생성 하려면 [리버스 엔지니어링-EF Core](/ef/core/managing-schemas/scaffolding)을 참조 하세요. EF 6과 EF Core 간의 차이점에 대 한 자세한 내용은 [ef 6 및 EF Core 비교](/ef/efcore-and-ef6/)를 참조 하세요.

Entity Framework Tools를 사용 하면 기존 데이터베이스에서 *개념적 모델* 을 만든 다음 개념적 모델을 그래픽으로 시각화 하 고 편집할 수 있습니다. 또는 먼저 개념적 모델을 그래픽으로 만든 후 모델을 지원하는 데이터베이스를 생성할 수 있습니다. 이 두 경우 모두 기본 데이터베이스가 변경될 때 모델을 자동으로 업데이트하고 애플리케이션에 대한 개체 계층 코드를 자동으로 생성할 수 있습니다. 데이터베이스 생성 및 개체 계층 코드 생성 작업은 사용자 지정할 수 있습니다.

Entity Framework 도구는 Visual Studio 설치 관리자에서 **데이터 저장소 및 처리** 워크 로드의 일부로 설치 됩니다. **Sdk, 라이브러리 및 프레임 워크** 범주 아래에 개별 구성 요소로 설치할 수도 있습니다.

다음은 Visual Studio에서 Entity Framework 도구를 구성 하는 특정 도구입니다.

- [!INCLUDE[vstecado](../data-tools/includes/vstecado_md.md)] ** [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 디자이너** (**Entity Designer**)를 사용 하 여 엔터티, 연결, 매핑 및 상속 관계를 시각적으로 만들고 수정할 수 있습니다. 또한 **Entity Designer** 는 [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)] 또는 [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] 개체 계층 코드를 생성 합니다.

- ** [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] 마법사** 를 사용 하 여 기존 데이터베이스에서 개념적 모델을 생성 하 고 응용 프로그램에 데이터베이스 연결 정보를 추가할 수 있습니다.

- **데이터베이스 만들기 마법사** 를 사용 하 여 먼저 개념적 모델을 만든 다음 모델을 지 원하는 데이터베이스를 만들 수 있습니다.

- 기본 데이터베이스가 변경 된 경우 **모델 업데이트 마법사** 를 사용 하 여 개념적 모델, 저장소 모델 및 매핑을 업데이트할 수 있습니다.

  > [!NOTE]
  > Visual Studio 2010부터 Entity Framework 도구는를 지원 하지 않습니다 [!INCLUDE[ss2k](../data-tools/includes/ss2k_md.md)] .

도구는 *.edmx* 파일을 생성 하거나 수정 합니다. 이 *.edmx* 파일에는 개념적 모델, 저장소 모델 및 두 모델 간의 매핑을 설명 하는 정보가 포함 되어 있습니다. 자세한 내용은 [EDMX](/ef/ef6/)를 참조 하세요.

[Entity Framework Power Tools](https://marketplace.visualstudio.com/items?itemName=EntityFrameworkTeam.EntityFrameworkPowerToolsBeta4) 는 엔터티 데이터 모델를 사용 하는 응용 프로그램을 빌드하는 데 도움이 됩니다. Power tools는 개념적 모델을 생성 하 고, 기존 모델의 유효성을 검사 하 고, 개념적 모델을 기반으로 하는 개체 클래스가 포함 된 소스 코드 파일을 생성 하 고, 모델이 생성 하는 뷰를 포함 하는 소스 코드 파일을 생성할 수 있습니다. 자세한 내용은 [미리 생성 된 매핑 뷰](/ef/ef6/fundamentals/performance/pre-generated-views)를 참조 하세요.

## <a name="related-topics"></a>관련 항목

| 제목 | 설명 |
| - | - |
| [ADO.NET Entity Framework](/dotnet/framework/data/adonet/ef/index) | 에서 제공 하는 도구를 사용 하 여 응용 프로그램을 만드는 방법을 설명 합니다 [!INCLUDE[adonet_edm](../data-tools/includes/adonet_edm_md.md)] [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] . |
| [엔터티 데이터 모델](/dotnet/framework/data/adonet/entity-data-model) | 에서 빌드된 응용 프로그램에서 사용 하는 데이터 작업을 위한 링크와 정보를 제공 [!INCLUDE[adonet_ef](../data-tools/includes/adonet_ef_md.md)] 합니다. |
| [Entity Framework (EF) 설명서)](/ef/ef6/get-started) | Entity Framework를 최대한 활용 하는 데 도움이 되는 비디오, 자습서 및 고급 설명서의 인덱스를 제공 합니다. |
| [ASP.NET 5 응용 프로그램을 새 데이터베이스로](https://docs.efproject.net/en/latest/platforms/aspnetcore/new-db.html) | Entity Framework 7을 사용 하 여 새 ASP.NET 5 응용 프로그램을 만드는 방법을 설명 합니다. |

## <a name="see-also"></a>추가 정보

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
