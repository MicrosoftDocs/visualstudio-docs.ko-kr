---
title: 데이터베이스 및 데이터 계층 응용 프로그램 만들기 및 관리
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
helpviewer_keywords:
- managing change, databases
- database features of Visual Studio, managing change
- databases, managing change
- managing change, database servers
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
caps.latest.revision: 40
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b793789e092b46f14db397c1f8aef4e98544f856
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75851692"
---
# <a name="creating-and-managing-databases-and-data-tier-applications-in-visual-studio"></a>Visual Studio에서 데이터베이스와 데이터 계층 애플리케이션 만들기 및 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

중요]
> 이전 버전의에 포함 된 데이터베이스 프로젝트는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 이제 도구에서 제공 됩니다 [!INCLUDE[sql_Denali_long](../includes/sql-denali-long-md.md)] . 자세한 내용은 [SQL Server Developer 도구](https://msdn.microsoft.com/library/hh272686(VS.103).aspx)를 참조 하세요.

 데이터베이스 프로젝트를 사용 하 여 새 데이터베이스, 새 Dac (데이터 계층 응용 프로그램)를 만들고 기존 데이터베이스 및 데이터 계층 응용 프로그램을 업데이트할 수 있습니다. 데이터베이스 프로젝트와 DAC 프로젝트를 모두 사용 하면 관리 코드 또는 네이티브 코드에 이러한 기술을 적용 하는 것과 거의 동일한 방식으로 데이터베이스 개발 작업에 버전 제어 및 프로젝트 관리 기법을 적용할 수 있습니다. *DAC 프로젝트*, *데이터베이스 프로젝트*또는 *서버 프로젝트* 를 만들고 버전 제어에 배치 하 여 개발 팀이 데이터베이스 및 데이터베이스 서버에 대 한 변경 내용을 관리 하도록 지원할 수 있습니다. 팀 멤버는 파일을 체크 아웃 하 여 *격리 된 개발 환경*에서 변경 내용을 적용, 빌드 및 테스트 한 후 팀과 공유할 수 있습니다. 코드 품질을 보장 하기 위해 팀은 변경 내용을 프로덕션에 배포 하기 전에 스테이징 환경에서 데이터베이스의 특정 릴리스에 대 한 모든 변경 내용을 완료 하 고 테스트할 수 있습니다.

 데이터 계층 응용 프로그램에서 지원 되는 데이터베이스 기능 목록은 Microsoft 웹 사이트의 [데이터 계층 응용 프로그램에서 지원](https://msdn.microsoft.com/library/ee362013(VS.100).aspx) 되는 기능을 참조 하십시오. 데이터 계층 응용 프로그램에서 지원 하지 않는 기능을 데이터베이스에서 사용 하는 경우에는 데이터베이스 프로젝트를 사용 하 여 데이터베이스에 대 한 변경 내용을 관리 해야 합니다.

## <a name="common-high-level-tasks"></a>일반적인 상위 수준 작업

|상위 수준 작업|지원 콘텐츠|
|----------------------|------------------------|
|**데이터 계층 응용 프로그램 개발을 시작 합니다.** DAC는 [!INCLUDE[sskatmai_r2](../includes/sskatmai-r2-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 클라이언트-서버 또는 3 계층 응용 프로그램에서 사용 하는 데이터베이스 및 지원 인스턴스 개체에 대 한 정의를 포함 하는에 도입 된 새로운 개념입니다. DAC에는 데이터베이스 개체 (예: 테이블 및 뷰)와 함께 인스턴스 엔터티 (예: 로그인)가 포함 됩니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 사용 하 여 dac 프로젝트를 만들고, dac 패키지 파일을 작성 하 고, 데이터베이스 엔진 인스턴스에 배포 하기 위해 dac 패키지 파일을 데이터베이스 관리자에 게 보낼 수 있습니다 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] .|-   [데이터 계층 응용 프로그램 만들기 및 관리](https://msdn.microsoft.com/library/ee361996(VS.100).aspx) (Microsoft 웹 사이트)<br />-   [SQL Server Management Studio](https://msdn.microsoft.com/library/hh213248(SQL.110).aspx)|
|**반복적인 데이터베이스 개발 수행:** 개발자 또는 테스터 인 경우 프로젝트의 일부를 체크 아웃 한 다음 격리 된 개발 환경에서 업데이트 합니다. 이러한 유형의 환경을 사용 하 여 팀의 다른 멤버에 게 영향을 주지 않고 변경 내용을 테스트할 수 있습니다. 변경이 완료 되 면 파일을 다시 버전 제어에 체크 인 합니다. 그러면 다른 팀 멤버가 변경 내용을 가져와 테스트 서버에 빌드하고 배포할 수 있습니다.|-   [쿼리 및 텍스트 편집기 (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft 웹 사이트)<br />-   [Transact-sql 디버거](https://msdn.microsoft.com/library/cc645997(SQL.110).aspx) (Microsoft 웹 사이트)|
|**프로토타입 생성, 테스트 결과 확인 및 데이터베이스 스크립트 및 개체 수정:** 편집기를 사용 [!INCLUDE[tsql](../includes/tsql-md.md)] 하 여 이러한 일반적인 작업 중 하나를 수행할 수 있습니다.|-   [쿼리 및 텍스트 편집기 (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms173477(SQL.110).aspx) (Microsoft 웹 사이트)|

## <a name="see-also"></a>관련 항목
 [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
