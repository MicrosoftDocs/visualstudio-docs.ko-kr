---
title: 부하 테스트 결과 관리
ms.date: 10/19/2016
ms.topic: how-to
helpviewer_keywords:
- load tests, results repository
- results, load test
- load test results, repository
- Load Test Results Repository
ms.assetid: 1cd63c4b-4f74-4133-b675-5e8fbeab25f3
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9945551469541cdcffe520844da600d758dc43b5
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85286767"
---
# <a name="manage-load-test-results-in-the-load-test-results-repository"></a>부하 테스트 결과 리포지토리에서 부하 테스트 결과 관리

부하 테스트를 실행할 때 부하 테스트 실행 도중 수집된 정보는 *부하 테스트 결과 리포지토리*라는 SQL 데이터베이스에 저장될 수 있습니다. 부하 테스트 결과 리포지토리에는 성능 카운터 데이터와 기록된 오류에 대한 정보가 들어 있습니다. 결과 리포지토리 데이터베이스는 컨트롤러용 설치 프로그램에서 만들어지거나 부하 테스트를 처음으로 로컬에서 실행할 때 자동으로 만들어집니다. 부하 테스트를 로컬로 실행할 때 부하 테스트 스키마가 없으면 데이터베이스가 자동으로 만들어집니다.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

다른 서버를 사용하도록 컨트롤러의 결과 리포지토리 연결 문자열을 수정하는 경우 새 서버에서 *loadtestresultsrepository.sql* 스크립트를 실행하여 스키마를 만들어야 합니다.

Visual Studio Enterprise에서는 기술을 기반으로 일반적인 성능 카운터를 수집하는 명명된 카운터 집합을 제공합니다. 이러한 집합은 IIS 서버, ASP.NET 서버 또는 SQL 서버를 분석할 때 유용합니다. 카운터 집합으로 수집된 모든 데이터는 부하 테스트 결과 리포지토리에 저장됩니다.

> [!IMPORTANT]
> 카운터 집합과 성능 카운터 데이터에는 차이가 있습니다. 카운터 집합은 메타데이터이며 IIS 또는 SQL Server와 같은 특정 역할을 수행 중인 컴퓨터에서 수집되어야 하는 성능 카운터 그룹을 정의합니다. 카운터 집합은 부하 테스트 정의의 일부입니다. 반면 성능 카운터 데이터는 카운터 집합, 특정 컴퓨터에 대한 카운터 집합 매핑, 샘플링 주기를 기반으로 수집됩니다.

## <a name="sql-server-versions"></a>SQL Server 버전

부하 테스트를 사용하려면 Visual Studio와 함께 설치되는 SQL Server Express LocalDB를 사용할 수 있습니다. 부하 테스트(Microsoft Excel 통합 포함)에 대한 기본 데이터베이스 서버입니다. SQL Server Express LocalDB는 프로그램 개발자를 대상으로 하는 SQL Server Express의 실행 모드입니다. SQL Server Express LocalDB 설치는 SQL Server 데이터베이스 엔진을 시작하는 데 필요한 최소한의 파일 집합을 복사합니다.

팀이 많은 데이터베이스 요구를 예상하거나 프로젝트가 SQL Server Express LocalDB보다 커지는 경우 추가 확장 가능성을 제공하기 위해 SQL Express 또는 전체 SQL Server로 업그레이드하는 것을 고려해야 합니다. SQL Server로 업그레이드하는 경우 SQL Server Express LocalDB의 MDF 및 LDF는 사용자 프로필 폴더에 저장됩니다. 부하 테스트 데이터베이스를 SQL Server Express 또는 SQL Server로 가져오는 데 이 파일을 사용할 수 있습니다.

## <a name="load-test-results-store-considerations"></a>부하 테스트 결과 저장소 고려 사항

Visual Studio Enterprise가 설치된 경우 부하 테스트 결과 저장소는 컴퓨터에 설치된 SQL Express의 인스턴스를 사용하도록 설정됩니다. SQL Express는 최대 4GB의 디스크 공간을 사용하도록 제한됩니다. 장기간에 걸쳐 여러 부하 테스트를 실행할 경우에는 가능하면 전체 SQL Server 제품의 인스턴스를 사용하도록 부하 테스트 결과 저장소를 구성해야 합니다.

## <a name="load-test-analyzer-tasks"></a>부하 테스트 분석기 작업

|작업|관련 항목|
|-|-----------------------|
|**부하 테스트 결과 리포지토리 설정:** SQL 데이터베이스에 부하 테스트 결과 리포지토리를 설정할 수 있습니다. **참고:** 테스트 컨트롤러를 설치할 때 부하 테스트 리포지토리를 만들 수도 있습니다. 자세한 내용은 [테스트 에이전트 설치 및 구성](../test/lab-management/install-configure-test-agents.md)을 참조하세요.||
|**결과 리포지토리 선택 및 보기:** 특정 결과 리포지토리를 선택할 수 있습니다. 로컬 결과 저장소로 제한되지는 않습니다. 부하 테스트는 주로 에이전트 컴퓨터의 원격 집합에서 실행됩니다. 에이전트나 로컬 컴퓨터의 테스트 결과는 부하 테스트 결과 저장소가 만들어진 모든 SQL 서버에 저장할 수 있습니다. 에이전트나 로컬 컴퓨터 모두 **테스트 컨트롤러 관리** 창을 사용하여 부하 테스트 결과를 저장할 위치를 식별해야 합니다.|-   [방법: 부하 테스트 결과 리포지토리 선택](../test/how-to-select-a-load-test-results-repository.md)<br />-   [방법: 분석을 위한 부하 테스트 결과 액세스](../test/how-to-access-load-test-results-for-analysis.md)|
|**리포지토리에서 부하 테스트 결과 삭제:** **부하 테스트 결과 열기 및 관리** 대화 상자를 사용하여 **부하 테스트 편집기**에서 부하 테스트 결과를 제거할 수 있습니다.|-   [방법: 리포지토리에서 부하 테스트 결과 삭제](../test/how-to-delete-load-test-results-from-a-repository.md)|
|**리포지토리에서 결과 가져오기 및 내보내기:** **부하 테스트 편집기**에서 부하 테스트 결과를 가져오고 내보낼 수 있습니다.|-   [방법: 리포지토리로 부하 테스트 결과 가져오기](../test/how-to-import-load-test-results-into-a-repository.md)<br />-   [방법: 리포지토리에서 부하 테스트 결과 내보내기](../test/how-to-export-load-test-results-from-a-repository.md)|

## <a name="related-tasks"></a>관련 작업

[부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)

**부하 테스트 분석기**를 사용하여 실행 중인 부하 테스트와 완료된 부하 테스트 모두의 결과를 볼 수 있습니다.

## <a name="see-also"></a>참고 항목

- [부하 테스트 결과 분석](../test/analyze-load-test-results-using-the-load-test-analyzer.md)
- [방법: 분석을 위한 부하 테스트 결과 액세스](../test/how-to-access-load-test-results-for-analysis.md)
