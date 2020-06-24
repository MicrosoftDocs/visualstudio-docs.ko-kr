---
title: .NET 용 Data tools
ms.date: 11/04/2016
ms.topic: overview
ms.assetid: c3175080-1dfb-4ab8-a460-92dadbb844b4
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
- dotnet
ms.openlocfilehash: 67cf4969a5db8900910b375d4cf560b1e30da4eb
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281073"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET용 Visual Studio 데이터 도구

Visual Studio 및 .NET은 데이터베이스에 연결 하 고, 메모리에서 데이터를 모델링 하 고, 사용자 인터페이스에서 데이터를 표시 하기 위한 광범위 한 API 및 도구 지원을 제공 합니다. 데이터 액세스 기능을 제공 하는 .NET 클래스를 [ADO.NET](/dotnet/framework/data/adonet/index)라고 합니다. ADO.NET는 Visual Studio의 데이터 도구와 함께 관계형 데이터베이스 및 XML을 지원 하기 위해 주로 설계 되었습니다. 이러한 일, 많은 NoSQL 데이터베이스 공급 업체 또는 제 3 자가 ADO.NET 공급자를 제공 합니다.

[.Net Core](/dotnet/core/) 는 데이터 집합 및 관련 형식을 제외 하 고 ADO.NET을 지원 합니다. .NET Core를 대상으로 지정 하 고 ORM (개체-관계형 매핑) 계층을 요구 하는 경우 [Entity Framework Core](/ef/core/)를 사용 합니다.

다음 다이어그램에서는 기본 아키텍처의 단순화 된 보기를 보여 줍니다.

![ADO.NET 아키텍처](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>일반적인 워크플로

일반적인 워크플로는 다음과 같습니다.

1. 로컬 컴퓨터에 개발 또는 테스트 데이터베이스를 설치 합니다. [데이터베이스 시스템, 도구 및 샘플 설치](../data-tools/installing-database-systems-tools-and-samples.md)를 참조 하세요. Azure 데이터 서비스를 사용 하는 경우에는이 단계가 필요 하지 않습니다.

2. Visual Studio에서 데이터베이스 (또는 서비스 또는 로컬 파일)에 대 한 연결을 테스트 합니다. [새 연결 추가](../data-tools/add-new-connections.md)를 참조 하세요.

3. 필드 도구를 사용 하 여 새 모델을 생성 하 고 구성 합니다. 새 응용 프로그램에 대 한 기본 권장 사항은 Entity Framework 기반으로 하는 모델입니다. 사용 하는 모델은 응용 프로그램이 상호 작용 하는 데이터 원본입니다. 모델은 데이터베이스 또는 서비스와 응용 프로그램 간에 논리적으로 배치 됩니다. [새 데이터 소스 추가](../data-tools/add-new-data-sources.md)를 참조 하세요.

4. **데이터 소스 창에서** Windows Forms, ASP.NET 또는 Windows Presentation Foundation 디자인 화면으로 데이터 소스를 끌어 사용자가 지정한 방식으로 데이터를 표시 하는 데이터 바인딩 코드를 생성 합니다. [Visual Studio에서 데이터에 컨트롤 바인딩을](../data-tools/bind-controls-to-data-in-visual-studio.md)참조 하세요.

5. 비즈니스 규칙, 검색 및 데이터 유효성 검사와 같은 항목에 대 한 사용자 지정 코드를 추가 하거나 기본 데이터베이스에서 노출 하는 사용자 지정 기능을 활용 합니다.

3 단계를 건너뛰고 .NET 응용 프로그램을 프로그래밍 하 여 모델을 사용 하지 않고 데이터베이스에 직접 명령을 실행할 수 있습니다. 이 경우에 관련 설명서를 보면: [ADO.NET](/dotnet/framework/data/adonet/index)합니다. **데이터 소스 구성 마법사** 및 디자이너를 사용 하 여 메모리에 사용자 고유의 개체를 채운 다음 해당 개체에 데이터를 바인딩할 때 데이터 바인딩 코드를 생성할 수도 있습니다.

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
