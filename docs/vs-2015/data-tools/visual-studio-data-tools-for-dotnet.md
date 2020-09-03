---
title: .NET 용 Visual Studio data tools | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9d591595c65f00e0198ded9492ae0b8399e363e5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670095"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET용 Visual Studio 데이터 도구
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 및 .NET Framework는 데이터베이스에 연결 하 고, 메모리의 데이터를 모델링 하 고, 사용자 인터페이스에서 데이터를 표시 하기 위한 광범위 한 API 및 도구 지원을 제공 합니다.  데이터 액세스 기능을 제공 하는 .NET Framework 클래스를 [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)라고 합니다. Visual Studio의 데이터 도구와 함께 ADO.NET는 원래 관계형 데이터베이스 및 XML을 지원 하도록 설계 되었습니다. 이러한 일, 많은 NoSQL 데이터베이스 공급 업체 또는 제 3 자가 ADO.NET 공급자를 제공 합니다.

 Visual Studio 2015 업데이트 2에는 Azure [SQL Database](https://azure.microsoft.com/services/sql-database/) 및 [SQL Server 2016](https://www.microsoft.com/sql-server/sql-server-2016)의 최신 기능에 대 한 지원을 사용 하도록 설정 하는 [SQL Server Data Tools](https://msdn.microsoft.com/library/hh272686\(v=vs.103\).aspx)의 최신 업데이트가 포함 되어 있습니다. [.Net Core](https://www.dotnetfoundation.org/projects?searchquery=dotnet+core&type=project) 는 데이터 집합 및 관련 형식을 제외 하 고 ADO.NET을 지원 합니다. .NET Core를 대상으로 지정 하 고 ORM (개체-관계형 매핑) 계층을 요구 하는 경우 [Entity Framework Core](https://msdn.microsoft.com/data/ef.aspx)를 사용 합니다.

 다음 다이어그램에서는 기본 아키텍처의 단순화 된 보기를 보여 줍니다.

 ![ADO.NET 아키텍처](../data-tools/media/raddata-ado-net-architecture-diagram.png "raddata ADO.NET 아키텍처 다이어그램")

 일반적인 워크플로는 다음과 같습니다.

1. 로컬 컴퓨터에 개발 또는 테스트 데이터베이스를 설치 합니다. [데이터베이스 시스템, 도구 및 샘플 설치](../data-tools/installing-database-systems-tools-and-samples.md)를 참조 하세요. Azure 데이터 서비스를 사용 하는 경우에는이 단계가 필요 하지 않습니다.

2. Visual Studio에서 데이터베이스 (또는 서비스 또는 로컬 파일)에 대 한 연결을 테스트 합니다. [새 연결 추가](../data-tools/add-new-connections.md)를 참조 하세요.

3. 필드 도구를 사용 하 여 새 모델을 생성 하 고 구성 합니다. 새 응용 프로그램에 대 한 기본 권장 사항은 Entity Framework 기반으로 하는 모델입니다. 모델은 사용 하는 모델 중 하나는 응용 프로그램이 상호 작용 하는 데이터 원본입니다. 모델은 데이터베이스 또는 서비스와 응용 프로그램 간에 논리적으로 배치 됩니다.  [새 데이터 소스 추가](../data-tools/add-new-data-sources.md)를 참조 하세요.

4. **데이터 소스 창에서** Windows Forms, ASP.NET 또는 Windows Presentation Foundation 디자인 화면으로 데이터 소스를 끌어 사용자가 지정한 방식으로 데이터를 표시 하는 데이터 바인딩 코드를 생성 합니다. [Visual Studio에서 데이터에 컨트롤 바인딩을](../data-tools/bind-controls-to-data-in-visual-studio.md)참조 하세요.

5. 비즈니스 규칙, 검색 및 데이터 유효성 검사와 같은 항목에 대 한 사용자 지정 코드를 추가 하거나 기본 데이터베이스에서 노출 하는 사용자 지정 기능을 활용 합니다.

   3 단계를 건너뛰고 .NET 응용 프로그램을 프로그래밍 하 여 모델을 사용 하지 않고 데이터베이스에 직접 명령을 실행할 수 있습니다. 이 경우에 관련 설명서를 보면: [ADO.NET](https://msdn.microsoft.com/library/e80y5yhx\(v=vs.110\).aspx)합니다. 데이터 소스 구성 마법사 및 디자이너를 사용 하 여 메모리에 사용자 고유의 개체를 채운 다음 해당 개체에 데이터를 바인딩할 때 데이터 바인딩 코드를 생성할 수도 있습니다.

## <a name="in-this-section"></a>섹션 내용

- [ADO.NET을 사용하여 간단한 데이터 애플리케이션 만들기](../data-tools/create-a-simple-data-application-by-using-adonet.md)

- [새 연결 추가](../data-tools/add-new-connections.md)

- [새 데이터 원본 추가](../data-tools/add-new-data-sources.md)

- [Visual Studio의 엔터티 데이터 모델 도구](../data-tools/entity-data-model-tools-in-visual-studio.md)

- [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)

- [LINQ to SQL Tools in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)(Visual Studio의 LINQ to SQL 도구)

- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)

- [데이터 액세스 오류 문제 해결을 위한 추가 리소스](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

- [Visual Studio에서 서비스 및 WCF Data Services Windows Communication Foundation](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)

- [Visual Studio에서 데이터베이스와 데이터 계층 애플리케이션 만들기 및 관리](../data-tools/creating-and-managing-databases-and-data-tier-applications-in-visual-studio.md)

- [데이터 액세스 오류 문제 해결을 위한 추가 리소스](../data-tools/additional-resources-for-troubleshooting-data-access-errors.md)

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
