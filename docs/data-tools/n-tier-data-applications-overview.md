---
title: N 계층 데이터 애플리케이션 개요
ms.date: 11/04/2016
ms.topic: overview
helpviewer_keywords:
- presentation tier
- middle tier
- data tier
- n-tier applications, about n-tier applications
ms.assetid: 1020581d-eaaa-41a2-aca4-bf4c212895f6
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 14527e84d5bbd2d06b2d091ba7a9d4daa9763462
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281957"
---
# <a name="n-tier-data-applications-overview"></a>N 계층 데이터 애플리케이션 개요
‘N 계층’ 데이터 애플리케이션은 여러 ‘계층’으로 분리된 데이터 애플리케이션입니다.  “분산 앱”과 “다중 계층 애플리케이션”이라고도 하는 N 계층 애플리케이션은 클라이언트 및 서버 사이에 분산되는 별개의 계층으로 처리를 분산합니다. 데이터에 액세스하는 애플리케이션을 개발할 때 애플리케이션을 구성하는 여러 계층을 명확하게 구분해야 합니다.

일반적인 N 계층 애플리케이션에는 프레젠테이션 계층, 중간 계층 및 데이터 계층이 포함됩니다. N 계층 애플리케이션의 여러 계층을 분리하는 가장 쉬운 방법은 애플리케이션에 포함할 각 계층에 대해 개별 프로젝트를 만드는 것입니다. 예를 들어, 프레젠테이션 계층은 Windows Forms 애플리케이션일 수 있지만 데이터 액세스 논리는 중간 계층에 위치한 클래스 라이브러리일 수 있습니다. 또한 프레젠테이션 레이어는 웹 서비스와 같은 서비스를 통해 중간 계층의 데이터 액세스 논리와 통신할 수 있습니다. 애플리케이션 구성 요소를 별도의 계층으로 분리하면 애플리케이션의 유지 관리성과 확장성이 높아집니다. 이는 전체 솔루션을 다시 설계하지 않고도 단일 계층에 적용할 수 있는 새로운 기술을 더 쉽게 도입할 수 있기 때문입니다. 또한 N 계층 애플리케이션은 일반적으로 프레젠테이션 계층으로부터 격리를 유지하는 중간 계층에 중요한 정보를 저장합니다.

Visual Studio에는 개발자가 N 계층 애플리케이션을 만드는 데 도움이 되는 몇 가지 기능이 포함되어 있습니다.

- 데이터 세트는 데이터 세트(데이터 엔터티 레이어)와 TableAdapters(데이터 액세스 레이어)를 분리할 수 있도록 하는 **DataSet Project** 속성을 제공합니다.

- [Visual Studio의 LINQ to SQL 도구](../data-tools/linq-to-sql-tools-in-visual-studio2.md)는 DataContext와 데이터 클래스를 별도의 네임스페이스에 생성하는 설정을 제공합니다. 이를 통해 데이터 액세스 및 데이터 엔터티 계층을 논리적으로 분리할 수 있습니다.

- [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index)은 애플리케이션의 여러 계층으로부터 DataContext를 가져오는 데 사용할 수 있는 <xref:System.Data.Linq.Table%601.Attach%2A> 메서드를 제공합니다. 자세한 내용은 [LINQ to SQL을 사용한 N 계층 및 원격 애플리케이션](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)을 참조하세요.

## <a name="presentation-tier"></a>프레젠테이션 계층
‘프레젠테이션 계층’은 사용자가 애플리케이션과 상호 작용하는 계층입니다. 추가 애플리케이션 로직이 포함된 경우가 많습니다. 일반적인 프레젠테이션 계층 구성 요소에는 다음이 포함됩니다.

- <xref:System.Windows.Forms.BindingSource> 및 <xref:System.Windows.Forms.BindingNavigator> 등 데이터 바인딩 구성 요소.

- 프레젠테이션 계층에서 사용하는 [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) 엔터티 클래스와 같은 데이터의 개체 표현.

프레젠테이션 계층은 일반적으로 서비스 참조(예: [Visual Studio 애플리케이션의 Windows Communication Foundation Services 및 WCF Data Services](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)를 사용하여 중간 계층에 액세스합니다. 프레젠테이션 계층은 데이터 계층에 직접 액세스하지 않습니다. 프레젠테이션 계층은 중간 계층의 데이터 액세스 구성 요소에 따라 데이터 계층과 통신합니다.

## <a name="middle-tier"></a>중간 계층
‘중간 계층’은 프레젠테이션 계층과 계층 및 데이터 계층이 서로 간의 통신을 위해 사용하는 계층입니다. 일반적인 중간 계층 구성 요소에는 다음이 포함됩니다.

- 비즈니스 규칙 및 데이터 유효성 검사와 같은 비즈니스 논리.

- 다음과 같은 데이터 액세스 구성 요소 및 논리:

  - [TableAdapters](create-and-configure-tableadapters.md) 및 [DataAdapters and DataReaders](/dotnet/framework/data/adonet/dataadapters-and-datareaders).

  - [LINQ to SQL](/dotnet/framework/data/adonet/sql/linq/index) 엔터티 클래스와 같은 데이터의 개체 표현.

  - 인증, 권한 부여, 개인 설정과 같은 일반적인 애플리케이션 서비스.

다음 그림에서는 Visual Studio에서 사용할 수 있는 기능 및 기술과 N 계층 애플리케이션의 중간 계층에 적합할 수 있는 기능 및 기술을 보여 줍니다.

![중간 계층 구성 요소](../data-tools/media/ntiermid.png) 중간 계층

중간 계층은 일반적으로 데이터 연결을 사용하여 데이터 계층에 연결합니다. 이 데이터 연결은 일반적으로 데이터 액세스 구성 요소에 저장됩니다.

## <a name="data-tier"></a>데이터 계층
*데이터 계층* 은 기본적으로 애플리케이션의 데이터를 저장하는 서버입니다(예: SQL Server를 실행하는 서버).

다음 그림에서는 Visual Studio에서 사용할 수 있는 기능 및 기술과 N 계층 애플리케이션의 데이터 계층에 적합할 수 있는 기능 및 기술을 보여 줍니다.

![데이터 계층 구성 요소](../data-tools/media/ntierdatatier.png) 데이터 계층

프레젠테이션 계층의 클라이언트에서 직접 데이터 계층에 액세스할 수 없습니다. 대신에 중간 계층의 데이터 액세스 구성 요소는 프레젠테이션과 데이터 계층 간의 통신에 사용됩니다.

## <a name="help-for-n-tier-development"></a>N 계층 개발에 대한 도움말
다음 항목은 N 계층 애플리케이션 작업에 관한 정보를 제공합니다.

[데이터 세트 및 TableAdapter를 다른 프로젝트로 분리](../data-tools/separate-datasets-and-tableadapters-into-different-projects.md)

[연습: N 계층 데이터 애플리케이션 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)

[LINQ to SQL을 사용한 N 계층 및 원격 애플리케이션](/dotnet/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql)

## <a name="see-also"></a>추가 정보

- [연습: N 계층 데이터 애플리케이션 만들기](../data-tools/walkthrough-creating-an-n-tier-data-application.md)
- [계층적 업데이트](../data-tools/hierarchical-update.md)
- [Visual Studio의 데이터 세트 도구](../data-tools/dataset-tools-in-visual-studio.md)
- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
