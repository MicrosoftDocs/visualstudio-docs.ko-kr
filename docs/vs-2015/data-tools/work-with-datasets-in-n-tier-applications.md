---
title: N 계층 응용 프로그램에서 데이터 집합 작업 | Microsoft Docs
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
caps.latest.revision: 25
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 4f7be307ec94b15871da20ace8055fc7121d5d92
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657811"
---
# <a name="work-with-datasets-in-n-tier-applications"></a>n 계층 애플리케이션에서 데이터 세트 작업
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

N 계층 데이터 응용 프로그램 *은 여러 논리 계층 (또는 *계층*)으로 구분 되는 데이터 중심 응용 프로그램입니다. 다시 말해서 N 계층 데이터 애플리케이션은 여러 프로젝트로 구분되며 데이터 액세스 계층, 비즈니스 논리 계층 및 표시 계층이 각 프로젝트에 포함되는 애플리케이션입니다. 자세한 내용은 [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)를 참조 하세요.

 TableAdapter 및 데이터 클래스를 개별 프로젝트로 생성할 수 있도록 형식화된 데이터 세트이 향상되었습니다. 따라서 애플리케이션 계층을 빠르게 분리하고 N 계층 데이터 애플리케이션을 생성하는 기능이 제공됩니다.

 형식화 된 데이터 집합의 n 계층 지원을 통해 n 계층 디자인에 대 한 응용 프로그램 아키텍처의 반복적인 개발을 수행할 수 있습니다. 또한 코드를 두 개 이상의 프로젝트로 수동으로 분리 하는 요구 사항을 제거 합니다. 데이터 세트 디자이너를 사용 하 여 데이터 계층 디자인을 시작 합니다. 애플리케이션 아키텍처에 N 계층 디자인을 적용할 준비가 되면 데이터 세트 클래스를 별도의 프로젝트로 생성하도록 데이터 세트의 **데이터 세트 프로젝트** 속성을 설정합니다.

## <a name="in-this-section"></a>섹션 내용
 [데이터 집합 및 tableadapter를 다른 프로젝트로 분리](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md) 생성 된 TableAdapter 클래스를 포함 하는 프로젝트에서 생성 된 데이터 집합 클래스를 새 프로젝트로 이동 하는 방법을 설명 합니다.

 [N 계층 응용 프로그램에서 tableadapter에 코드 추가](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md) N 계층 TableAdapter에 대해 코드를 추가할 수 있는 partial 클래스를 생성 하는 방법에 대해 설명 합니다.

 [N 계층 응용 프로그램의 데이터 집합에 코드 추가](../data-tools/add-code-to-datasets-in-n-tier-applications.md) N 계층 데이터 집합에 대 한 코드를 추가할 수 있는 partial 클래스를 생성 하는 방법을 설명 합니다.

 [N 계층 데이터 집합에 유효성 검사 추가](../data-tools/add-validation-to-an-n-tier-dataset.md) 데이터 변경에 대 한 유효성 검사를 수행 하는 코드를 추가할 위치에 대해 설명 합니다.

 [연습: N 계층 데이터 응용 프로그램 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md) 형식화 된 데이터 집합을 만들고 TableAdapter 및 데이터 집합 코드를 여러 프로젝트로 분리 하는 방법에 대 한 단계별 지침을 제공 합니다.

 [연습: N 계층 데이터 응용 프로그램에 유효성 검사 추가](https://msdn.microsoft.com/library/b35d072c-31f0-49ba-a225-69177592c265) N 계층 데이터 응용 프로그램 연습에서 만든 응용 프로그램에 유효성 검사를 추가 하는 방법에 대 한 단계별 지침을 제공 합니다.

## <a name="reference"></a>참고
 <xref:System.Data.DataSet>

 <xref:System.Data.TypedTableBase%601>

## <a name="related-sections"></a>관련 단원

- [N 계층 데이터 응용 프로그램 개요](../data-tools/n-tier-data-applications-overview.md)
- [계층적 업데이트](../data-tools/hierarchical-update.md)
- [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
- [LINQ to SQL을 사용한 N 계층 및 원격 애플리케이션](https://msdn.microsoft.com/library/854a1cdd-53cb-45f5-83ca-63962a9b3598)