---
title: n 계층 애플리케이션에서 데이터 세트 작업
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- datasets [Visual Basic], n-tier applications
- multi-tier database applications
- DataSet project [VS n-tier applications]
- distributed applications [VS n-tier applications]
- data [Visual Basic], n-tier applications
- TableAdapters, n-tier applications
- n-tier applications
- tiers, n-tier applications
- typed datasets, n-tier applications
- multiple tier applications
ms.assetid: f6ae2ee0-ea5f-4a79-8f4b-e21c115afb20
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: c7532bed6a7d43c24d698870723d2265fc2b176f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75585927"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>n 계층 애플리케이션에서 데이터 세트 작업

*N 계층 데이터 응용 프로그램* 은 여러 *논리 계층으로*구분 되는 데이터 중심 응용 프로그램입니다. 다시 말해서 N 계층 데이터 애플리케이션은 여러 프로젝트로 구분되며 데이터 액세스 계층, 비즈니스 논리 계층 및 표시 계층이 각 프로젝트에 포함되는 애플리케이션입니다. 자세한 내용은 [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)를 참조 하세요.

TableAdapter 및 데이터 클래스를 개별 프로젝트로 생성할 수 있도록 형식화된 데이터 세트이 향상되었습니다. 따라서 애플리케이션 계층을 빠르게 분리하고 N 계층 데이터 애플리케이션을 생성하는 기능이 제공됩니다.

형식화 된 데이터 집합의 n 계층 지원을 통해 n 계층 디자인에 대 한 응용 프로그램 아키텍처의 반복적인 개발을 수행할 수 있습니다. 또한 코드를 두 개 이상의 프로젝트로 수동으로 분리 하는 요구 사항을 제거 합니다. **데이터 세트 디자이너**를 사용 하 여 데이터 계층 디자인을 시작 합니다. 애플리케이션 아키텍처에 N 계층 디자인을 적용할 준비가 되면 데이터 세트 클래스를 별도의 프로젝트로 생성하도록 데이터 세트의 **데이터 세트 프로젝트** 속성을 설정합니다.

## <a name="reference"></a>참고

- <xref:System.Data.DataSet>
- <xref:System.Data.TypedTableBase%601>

## <a name="see-also"></a>참조

- [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)
- [연습: n 계층 데이터 응용 프로그램 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [n 계층 애플리케이션에서 TableAdapter에 코드 추가](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)
- [n 계층 애플리케이션에서 데이터 세트에 코드 추가](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [N 계층 데이터 집합에 유효성 검사 추가](../data-tools/add-validation-to-an-n-tier-dataset.md)
- [데이터 세트 및 TableAdapter를 다른 프로젝트로 분리](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)
- [계층적 업데이트](../data-tools/hierarchical-update.md)
- [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
- [TableAdapter 만들기 및 구성](../data-tools/create-and-configure-tableadapters.md)
- [LINQ to SQL를 사용 하는 N 계층 및 원격 응용 프로그램](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)
