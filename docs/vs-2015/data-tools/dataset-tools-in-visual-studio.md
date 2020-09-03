---
title: 데이터 세트 도구
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.data.DataSet
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- untyped datasets
- datasets [Visual Basic], extended properties
- typed datasets
- current record in dataset
- XML [Visual Basic], datasets
- DataSet class, about datasets
- unique constraints (datasets)
- data relationships
- parent records in datasets
- extended properties, in typed datasets
- datasets [Visual Basic]
- schemas [Visual Basic], datasets
- datasets [Visual Basic], msprop
- master-detail tables, datasets
- databases [Visual Basic], updating
- msprop
- foreign keys, datasets
- DataSet class
- datasets [Visual Basic], filling
- case sensitivity, datasets
- constraints [Visual Basic], datasets
- child records
- related tables, datasets
- updating datasets, about dataset updates
- data caching, datasets
- DataRelation object, datasets
- untyped datasets, compared to typed datasets
- cache [Visual Studio], datasets
- datasets [Visual Basic], relationships
- related tables
- XML schemas, about XML schemas and datasets
- relationships, datasets
- typed datasets, compared to untyped datasets
- datasets [Visual Basic], populating
- datasets [Visual Basic], namespace
- data adapters, populating datasets
ms.assetid: ee57f4f6-9fe1-4e0a-be9a-955c486ff427
caps.latest.revision: 53
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 23e4deba53288383a569f6da6e14d27f723825ee
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657379"
---
# <a name="dataset-tools-in-visual-studio"></a>Visual Studio의 데이터 세트 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 데이터 집합 및 관련 클래스는 응용 프로그램이 데이터베이스와의 연결을 해제 하는 동안 응용 프로그램에서 메모리의 데이터를 사용할 수 있도록 하는 초기 2000s의 레거시 .NET 기술입니다. 사용자가 데이터를 수정 하 고 변경 내용을 데이터베이스에 다시 저장할 수 있도록 하는 응용 프로그램에 특히 유용 합니다. 데이터 집합은 매우 성공적인 기술로 입증 되었지만 새 .NET 응용 프로그램에서 Entity Framework를 사용 하는 것이 좋습니다. Entity Framework은 테이블 형식 데이터를 개체 모델로 사용 하는 보다 자연 스러운 방법을 제공 하 고 프로그래밍 인터페이스를 단순화 합니다.

 DataSet 개체는 기본적으로 미니 데이터베이스인 메모리 내 개체입니다. 여기에는 열려 있는 연결을 유지 관리할 필요 없이 하나 이상의 데이터베이스에서 데이터를 저장 하 고 수정할 수 있는 DataTable, DataColumn 및 DataRow 개체가 포함 되어 있습니다. 데이터 집합은 해당 데이터 변경 내용에 대 한 정보를 유지 하므로 응용 프로그램이 다시 연결 되 면 업데이트를 추적 하 고 데이터베이스로 다시 보낼 수 있습니다.

 데이터 집합 및 관련 클래스는 .NET Framework 클래스 라이브러리의 System.object 네임 스페이스에 정의 됩니다. 코드에서 데이터 집합을 동적으로 만들고 수정할 수 있습니다. 이 작업을 수행 하는 방법에 대 한 자세한 내용은 ADO.NET를 참조 하세요. 이 단원의 설명서에서는 Visual Studio 디자이너를 사용 하 여 데이터 집합으로 작업 하는 방법을 보여 줍니다. 한 가지 주의할 점은 디자이너를 통해 수행 되는 데이터 집합은 TableAdapter 개체를 사용 하 여 데이터베이스와 상호 작용 하는 반면 프로그래밍 방식으로 만들어진 데이터 집합은 DataAdapter 개체를 사용 합니다. 프로그래밍 방식으로 데이터 집합을 만드는 방법에 대 한 자세한 내용은 [dataadapter 및 DataReaders](https://msdn.microsoft.com/library/cc952ca2-ec19-46ab-9189-15174b52cb74)를 참조 하세요.

 응용 프로그램에서 데이터베이스의 데이터만 읽고 업데이트, 추가 또는 삭제를 수행 해야 하는 경우 일반적으로 DataReader 개체를 사용 하 여 제네릭 목록 개체 또는 다른 컬렉션 개체에 데이터를 검색 하는 방식으로 더 나은 성능을 얻을 수 있습니다. 데이터를 표시 하는 경우 사용자 인터페이스를 컬렉션에 데이터 바인딩할 수 있습니다.

## <a name="dataset-workflow"></a>데이터 집합 워크플로
 Visual Studio는 데이터 집합 작업을 간소화 하기 위해 많은 도구를 제공 합니다. 기본 종단 간 워크플로는 다음과 같습니다.

- **데이터 소스** 창을 사용 하 여 하나 이상의 데이터 원본에서 새 데이터 집합을 만들 수 있습니다. **데이터 세트 디자이너** 를 사용 하 여 데이터 집합을 구성 하 고 해당 속성을 설정 합니다. 예를 들어 데이터 원본에서 포함할 테이블과 각 테이블의 열을 지정 해야 합니다. 데이터 집합에 필요한 메모리 양을 신중 하 게 선택 합니다. 자세한 내용은 [데이터 세트 만들기 및 구성](../data-tools/create-and-configure-datasets-in-visual-studio.md)을 참조하세요.

- 외래 키가 올바르게 처리 되도록 테이블 간의 관계를 지정 합니다. 자세한 내용은 [tableadapter를 사용 하 여 데이터 집합 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)를 참조 하세요.

- **TableAdapter 구성 마법사** 를 사용 하 여 데이터 집합을 채울 쿼리 또는 저장 프로시저와 구현할 데이터베이스 작업 (업데이트, 삭제 등)을 지정할 수 있습니다. 자세한 내용은 다음 항목을 참조하세요.

  - [TableAdapters를 사용하여 데이터 세트 채우기](../data-tools/fill-datasets-by-using-tableadapters.md)

  - [데이터 집합의 데이터 편집](../data-tools/edit-data-in-datasets.md)

  - [데이터 세트의 데이터 유효성 검사](../data-tools/validate-data-in-datasets.md)

  - [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)

- 데이터 집합의 데이터를 쿼리하고 검색 합니다. 자세한 내용은 [쿼리 데이터 집합](../data-tools/query-datasets.md)을 참조 하세요. [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] 개체의 데이터에 대해 [LINQ (통합 언어 쿼리)](https://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) 를 사용 하도록 설정 <xref:System.Data.DataSet> 합니다. 자세한 내용은 [LINQ to DataSet](https://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17)을 참조하세요.

- **데이터 소스** 창을 사용 하 여 사용자 인터페이스 컨트롤을 데이터 집합 또는 개별 열에 바인딩하고 사용자가 편집할 수 있는 열을 지정할 수 있습니다. 자세한 내용은 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)을 참조 하세요.

## <a name="datasets-and-n-tier-architecture"></a>데이터 집합 및 N 계층 아키텍처
 N 계층 응용 프로그램의 데이터 집합에 대 한 자세한 내용은 [n 계층 응용 프로그램에서 데이터 집합 작업](../data-tools/work-with-datasets-in-n-tier-applications.md)을 참조 하세요.

## <a name="datasets-and-xml"></a>데이터 집합 및 XML
 데이터 집합을 XML로 변환 하는 방법에 대 한 자세한 내용은 [xml 데이터를 데이터 집합으로 읽어](../data-tools/read-xml-data-into-a-dataset.md) 데이터 집합을 [xml로 저장](../data-tools/save-a-dataset-as-xml.md)을 참조 하세요.

## <a name="see-also"></a>관련 항목
 [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
