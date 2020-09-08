---
title: .NET용 데이터 도구
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281073"
---
# <a name="visual-studio-data-tools-for-net"></a>.NET용 Visual Studio 데이터 도구

Visual Studio 및 .NET은 데이터베이스 연결, 메모리에서 데이터 모델링, 사용자 인터페이스에 데이터 표시를 위한 광범위한 API 및 도구 지원을 제공합니다. 데이터 액세스 기능을 제공하는 .NET 클래스를 [ADO.NET](/dotnet/framework/data/adonet/index)이라고 합니다. ADO.NET은 Visual Studio의 데이터 도구와 함께 관계형 데이터베이스 및 XML을 지원하도록 설계되었습니다. 많은 NoSQL 데이터베이스 공급업체 또는 타사에서 ADO.NET 공급자를 제공합니다.

[.NET Core](/dotnet/core/)는 데이터 세트 및 관련 형식을 제외하고 ADO.NET을 지원합니다. .NET Core를 대상으로 지정하고 ORM(개체-관계형 매핑) 레이어를 요구하는 경우 [Entity Framework Core](/ef/core/)를 사용합니다.

다음 다이어그램에서는 단순화된 기본 아키텍처를 보여 줍니다.

![ADO.NET 아키텍처](../data-tools/media/raddata-ado-net-architecture-diagram.png)

## <a name="typical-workflow"></a>일반적인 워크플로

일반적인 워크플로는 다음과 같습니다.

1. 로컬 컴퓨터에 개발 또는 테스트 데이터베이스를 설치합니다. [데이터베이스 시스템, 도구 및 샘플 설치](../data-tools/installing-database-systems-tools-and-samples.md)를 참조하세요. Azure 데이터 서비스를 사용하는 경우에는 이 단계를 수행할 필요가 없습니다.

2. Visual Studio에서 데이터베이스(또는 서비스나 로컬 파일)에 대한 연결을 테스트합니다. [새 연결 추가](../data-tools/add-new-connections.md)를 참조하세요.

3. (선택 사항) 도구를 사용하여 새 모델을 생성하고 구성합니다. Entity Framework 기반 모델은 새 애플리케이션에 대한 기본 권장 사항입니다. 사용하는 모델은 애플리케이션이 상호 작용하는 데이터 원본입니다. 모델은 데이터베이스 사이 또는 서비스와 애플리케이션 사이에 논리적으로 배치됩니다. [새 데이터 원본 추가](../data-tools/add-new-data-sources.md)를 참조하세요.

4. **데이터 원본** 창에서 데이터 원본을 Windows Forms, ASP.NET 또는 Windows Presentation Foundation 디자인 화면으로 끌어서 놓아 사용자가 지정한 방식으로 데이터를 표시하는 데이터 바인딩 코드를 생성합니다. [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)을 참조하세요.

5. 비즈니스 규칙, 검색 및 데이터 유효성 검사와 같은 항목에 대한 사용자 지정 코드를 추가하거나 기본 데이터베이스에서 노출하는 사용자 지정 기능을 활용합니다.

3단계를 건너뛰고 .NET 애플리케이션을 프로그래밍하여 모델을 사용하는 대신 데이터베이스에 직접 명령을 실행할 수 있습니다. 이 경우에 관련 설명서를 보면: [ADO.NET](/dotnet/framework/data/adonet/index)합니다. 메모리에 고유한 개체를 채운 다음 데이터 바인딩 UI 컨트롤을 개체에 채울 때 **데이터 소스 구성 마법사** 및 디자이너를 사용하여 데이터 바인딩 코드를 생성할 수 있습니다.

## <a name="see-also"></a>참조

- [Visual Studio에서 데이터 액세스](../data-tools/accessing-data-in-visual-studio.md)
