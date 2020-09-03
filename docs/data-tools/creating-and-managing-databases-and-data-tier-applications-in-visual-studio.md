---
title: 데이터베이스 프로젝트 및 DAC 프로젝트
ms.date: 11/21/2018
ms.topic: conceptual
helpviewer_keywords:
- databases, managing change
ms.assetid: 40b51f5a-d52c-44ac-8f84-037a0917af33
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc8d32ddcc332264278cf76392ac69a6188ca51c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75586733"
---
# <a name="database-projects-and-data-tier-applications"></a>데이터베이스 프로젝트 및 데이터 계층 응용 프로그램

데이터베이스 프로젝트를 사용 하 여 새 데이터베이스, 새 Dac (데이터 계층 응용 프로그램)를 만들고 기존 데이터베이스 및 데이터 계층 응용 프로그램을 업데이트할 수 있습니다. 데이터베이스 프로젝트와 DAC 프로젝트를 모두 사용 하면 관리 코드 또는 네이티브 코드에 이러한 기술을 적용 하는 것과 거의 동일한 방식으로 데이터베이스 개발 작업에 버전 제어 및 프로젝트 관리 기법을 적용할 수 있습니다. DAC 프로젝트, 데이터베이스 프로젝트 또는 서버 프로젝트를 만들고 버전 제어에 배치 하 여 개발 팀이 데이터베이스 및 데이터베이스 서버에 대 한 변경 내용을 관리 하도록 지원할 수 있습니다. 팀 멤버는 파일을 체크 아웃 하 여 격리 된 개발 환경에서 변경 내용을 적용, 빌드 및 테스트 한 후 팀과 공유할 수 있습니다. 코드 품질을 보장 하기 위해 팀은 변경 내용을 프로덕션에 배포 하기 전에 스테이징 환경에서 데이터베이스의 특정 릴리스에 대 한 모든 변경 내용을 완료 하 고 테스트할 수 있습니다.

데이터 계층 응용 프로그램에서 지원 되는 데이터베이스 기능 목록은 [SQL Server 개체에 대 한 DAC 지원](/sql/relational-databases/data-tier-applications/dac-support-for-sql-server-objects-and-versions)을 참조 하세요. 데이터 계층 응용 프로그램에서 지원 하지 않는 기능을 데이터베이스에서 사용 하는 경우에는 데이터베이스 프로젝트를 사용 하 여 데이터베이스에 대 한 변경 내용을 관리 해야 합니다.

## <a name="common-high-level-tasks"></a>일반적인 상위 수준 작업

| 상위 수준 작업 | 지원 콘텐츠 |
| - | - |
| **데이터 계층 응용 프로그램 개발을 시작 합니다.** DAC (데이터 계층 응용 프로그램)의 개념은 SQL Server 2008에서 도입 되었습니다. DAC에는 클라이언트-서버 또는 3 계층 응용 프로그램에서 사용 하는 SQL Server 데이터베이스 및 지원 인스턴스 개체에 대 한 정의가 포함 되어 있습니다. DAC에는 데이터베이스 개체 (예: 테이블 및 뷰)와 함께 인스턴스 엔터티 (예: 로그인)가 포함 됩니다. Visual Studio를 사용 하 여 DAC 프로젝트를 만들고, DAC 패키지 파일을 작성 하 고, SQL Server 데이터베이스 엔진 인스턴스에 배포 하기 위해 DAC 패키지 파일을 데이터베이스 관리자에 게 보낼 수 있습니다. | - [데이터 계층 응용 프로그램](/sql/relational-databases/data-tier-applications/data-tier-applications)<br />- [SQL Server Management Studio](/sql/ssms/sql-server-management-studio-ssms) |
| **반복적인 데이터베이스 개발 수행:** 개발자는 프로젝트의 일부를 체크 아웃 하 고 격리 된 개발 환경에서 업데이트할 수 있습니다. 이러한 유형의 환경을 사용 하 여 팀의 다른 멤버에 게 영향을 주지 않고 변경 내용을 테스트할 수 있습니다. 변경이 완료 되 면 파일을 다시 버전 제어에 체크 인 합니다. 그러면 다른 팀 멤버가 변경 내용을 가져와 테스트 서버에 빌드하고 배포할 수 있습니다. | - [프로젝트 기반 오프 라인 데이터베이스 개발 (SQL Server Data Tools)](/sql/ssdt/project-oriented-offline-database-development)<br />- [Transact-sql 디버거 (SQL Server Management Studio)](/sql/ssms/scripting/transact-sql-debugger) |
| **프로토타입 생성, 테스트 결과 확인 및 데이터베이스 스크립트 및 개체 수정:** Transact-sql 편집기를 사용 하 여 이러한 일반적인 작업 중 하나를 수행할 수 있습니다. | - [쿼리 및 텍스트 편집기 (SQL Server Management Studio)](/sql/ssms/scripting/query-and-text-editors-sql-server-management-studio) |

## <a name="see-also"></a>추가 정보

- [.NET용 Visual Studio 데이터 도구](../data-tools/visual-studio-data-tools-for-dotnet.md)
