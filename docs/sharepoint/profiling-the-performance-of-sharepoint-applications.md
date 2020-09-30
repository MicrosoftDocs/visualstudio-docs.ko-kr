---
title: SharePoint 응용 프로그램의 성능 프로 파일링 | Microsoft Docs
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.Profiling.SilverlightWebPartOnly
- VS.SharePointTools.Profiling.DotNetTrustLevel
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, profiling
- performance testing [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, performance testing
- profiling [SharePoint development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 87312b5db9357462c822f876220cc239b79106aa
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91585721"
---
# <a name="profile-the-performance-of-sharepoint-applications"></a>SharePoint 응용 프로그램의 성능 프로 파일링

SharePoint 응용 프로그램이 느리거나 비효율적으로 수행 되는 경우 Visual Studio의 프로 파일링 기능을 사용 하 여 문제 코드 및 기타 요소를 식별할 수 있습니다. 부하 테스트 기능을 사용 하 여 많은 사용자가 응용 프로그램에 동시에 액세스 하는 경우와 같이 스트레스 상태에서 SharePoint 응용 프로그램을 수행 하는 방법을 결정할 수 있습니다. 웹 성능 테스트를 실행 하면 응용 프로그램이 웹에서 수행 되는 방식을 측정할 수 있습니다. 코딩 된 UI 테스트를 사용 하 여 사용자 인터페이스를 비롯 한 전체 SharePoint 응용 프로그램이 제대로 작동 하는지 확인할 수 있습니다. 이러한 테스트를 함께 사용 하는 경우 응용 프로그램을 배포 하기 전에 성능 문제를 식별 하는 데 도움이 될 수 있습니다.

## <a name="profile-tools-overview"></a>프로필 도구 개요

프로 파일링은 실행 될 때 응용 프로그램의 성능 동작을 관찰 하 고 기록 하는 프로세스를 말합니다. 응용 프로그램을 프로 파일링 하 여 병목 현상, 비효율적인 코드, 메모리 할당 문제 등의 문제를 발견할 수 있습니다. 그러면 응용 프로그램이 느리게 실행 되거나 너무 많은 메모리가 사용 됩니다. 예를 들어, 프로 파일링을 사용 하 여 코드에서 핫스팟을 식별할 수 있습니다 .이는 자주 호출 되는 코드 세그먼트 이며 응용 프로그램의 전반적인 성능을 저하 시킬 수 있습니다. 핫스팟을 식별 한 후에는 자주 최적화 하거나 제거할 수 있습니다.

IDE (통합 개발 환경)에서 여러 프로 파일링 도구를 사용 하 여 이러한 종류의 성능 문제를 식별 하 고 찾을 수 있습니다. 이러한 도구는 다른 종류의 Visual Studio 프로젝트에서와 동일한 방식으로 SharePoint 프로젝트에 대해 작동 합니다. 프로파일링 도구 성능 마법사는 지정한 테스트를 사용 하는 성능 세션을 만드는 과정을 안내 합니다. 성능 세션은 하나 이상의 프로 파일링 실행 결과와 함께 응용 프로그램에서 성능 정보를 수집 하는 데 사용 되는 구성 데이터의 집합입니다. 성능 세션은 프로젝트 폴더에 저장 되며 **성능 탐색기**에서 볼 수 있습니다. 자세한 내용은 [성능 컬렉션 메서드 이해](../profiling/understanding-performance-collection-methods.md)를 참조하세요.

응용 프로그램에 대 한 프로필 분석을 만들고 실행 한 후에는 보고서에서 성능에 대 한 세부 정보를 제공 합니다. 이 보고서에는 시간별 CPU 사용량 그래프, 계층적 함수 호출 스택 또는 호출 트리와 같은 항목이 포함 될 수 있습니다. 보고서의 정확한 내용은 샘플링 또는 계측과 같은 실행 하는 테스트 유형에 따라 달라질 수 있습니다. 자세한 내용은 [프로파일링 도구 보고서 개요](../profiling/performance-report-overview.md)를 참조 하세요.

## <a name="performance-session-process"></a>성능 세션 프로세스

응용 프로그램을 프로 파일링 하려면 프로파일링 도구 성능 마법사를 사용 하 여 성능 세션을 만드는 것으로 시작 합니다. 메뉴 모음에서 **분석**, **성능 마법사 시작**을 선택 합니다. 마법사를 완료 하면 원하는 프로필 방법과 프로 파일링 하려는 응용 프로그램 등의 성능 세션에 필요한 정보를 입력 합니다. 자세한 내용은 [방법: 성능 마법사를 사용 하 여 웹 사이트 또는 웹 응용 프로그램 프로 파일링](../profiling/how-to-collect-performance-data-for-a-web-site.md)을 참조 하세요. 대신 명령줄 옵션을 사용 하 여 성능 세션을 설정 하 고 실행할 수 있습니다. 자세한 내용은 [명령줄에서 프로파일링 도구 사용](../profiling/using-the-profiling-tools-from-the-command-line.md)을 참조 하세요. 성능 세션의 모든 측면을 수동으로 구성 하려는 경우 [방법: 프로파일링 도구 사용 하 여 수동으로 성능 세션 만들기](../profiling/how-to-manually-create-performance-sessions.md)를 참조 하세요. 또한 **테스트 결과** 창에서 단위 테스트에 대 한 바로 가기 메뉴를 열고 **성능 세션 만들기**를 선택 하 여 단위 테스트에서 성능 세션을 만들 수 있습니다.

성능 세션을 설정 하면 세션 구성이 저장 되 고 서버가 프로 파일링 데이터를 제공 하도록 구성 되며 응용 프로그램이 실행 됩니다. 응용 프로그램을 사용할 때 성능 데이터는 로그 파일에 기록 됩니다. 성능 세션은 **대상** 폴더 아래 **성능 탐색기** 에 나열 됩니다. 성능 세션이 완료 된 후 해당 보고서는 **성능 탐색기**의 **Reports** 폴더에 표시 됩니다. 보고서를 표시 하려면 **성능 탐색기**에서 엽니다. 성능 세션의 속성을 보거나 구성 하려면 **성능 탐색기**에서 바로 가기 메뉴를 열고 **속성**을 선택 합니다. 성능 세션의 특정 속성에 대 한 자세한 내용은 [프로파일링 도구에 대 한 성능 세션 구성](../profiling/configuring-performance-sessions.md)을 참조 하세요. 성능 세션의 결과를 해석 하는 방법에 대 한 자세한 내용은 [프로파일링 도구 데이터 분석](../profiling/analyzing-performance-tools-data.md)을 참조 하세요.

## <a name="stress-test"></a>스트레스 테스트

Visual Studio에서 부하 테스트 및 웹 성능 테스트를 만들어 응용 프로그램의 스트레스 성능을 분석할 수 있습니다. Visual Studio에서 부하 테스트를 만들 때 응용 프로그램을 테스트 하는 시나리오 라는 요소 조합을 지정 합니다. 이러한 요소에는 부하 패턴, 테스트 조합 모델, 테스트 조합, 네트워크 조합 및 웹 브라우저 조합이 포함 됩니다. 부하 테스트 시나리오에는 단위 테스트와 웹 성능 테스트가 모두 포함 될 수 있습니다.

그림 1: 부하 테스트 결과 예제

![실행 중인 부하 테스트 그래프 뷰](../sharepoint/media/load-webgraphs.png "실행 중인 부하 테스트 그래프 뷰")

웹 성능 테스트는 최종 사용자가 SharePoint 응용 프로그램과 상호 작용할 수 있는 방법을 시뮬레이션 합니다. 브라우저 세션에서 HTTP 요청을 기록 하거나 **웹 성능 테스트 레코더**를 사용 하 여 웹 성능 테스트를 만들 수 있습니다. 브라우저 세션이 완료 된 후 웹 요청이 **웹 성능 테스트 편집기** 에 표시 됩니다. 그런 다음 **웹 성능 테스트 결과 뷰어에서**결과를 디버그할 수 있습니다. **웹 성능 테스트 편집기**를 사용 하 여 웹 성능 테스트를 수동으로 빌드할 수도 있습니다.

## <a name="test-user-interfaces"></a>사용자 인터페이스 테스트

코딩 된 UI 테스트는 UI (사용자 인터페이스)를 통해 SharePoint 응용 프로그램을 자동으로 구동 합니다. 이러한 테스트는 단추 및 메뉴와 같은 UI 컨트롤을 포함 하 여 제대로 작동 하는지 확인 합니다. 이러한 종류의 테스트는 웹 페이지에서와 같이 UI에서 유효성 검사 또는 기타 논리를 수행 하는 경우에 특히 유용 합니다. 또한 코딩 된 UI 테스트를 사용 하 여 수동 테스트를 자동화할 수 있습니다. 다른 유형의 응용 프로그램에 대 한 테스트를 만들 때와 동일한 방식으로 SharePoint 응용 프로그램에 대 한 코딩 된 UI 테스트를 만듭니다. 자세한 내용은 [코딩 된 UI 테스트를 사용 하 여 SharePoint 2010 응용 프로그램 테스트](../vs-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests.md?view=vs-2015&preserve-view=true)를 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|Description|
|-----------|-----------------|
|[연습: SharePoint 응용 프로그램 프로 파일링](../sharepoint/walkthrough-profiling-a-sharepoint-application.md)|SharePoint 응용 프로그램에서 샘플링 프로필 분석을 수행 하는 방법을 보여 줍니다.|
|[릴리스 전에 앱 성능 테스트](/azure/devops/test/load-test/run-performance-tests-app-before-release?view=vsts&preserve-view=true)|SharePoint 응용 프로그램을 스트레스 테스트 하는 데 도움이 되는 부하 테스트를 만드는 방법을 설명 합니다.|
|[코드 단위 테스트](../test/unit-test-your-code.md)|단위 테스트를 사용 하 여 코드에서 논리 오류를 찾는 방법을 설명 합니다.|
|[코딩된 UI 테스트를 사용하여 SharePoint 2010 애플리케이션 테스트](../vs-2015/test/testing-sharepoint-2010-applications-with-coded-ui-tests.md?view=vs-2015&preserve-view=true)|SharePoint 응용 프로그램의 사용자 인터페이스를 테스트 하는 방법을 설명 합니다.|

## <a name="see-also"></a>참고 항목

- [SharePoint 솔루션 빌드 및 디버그](../sharepoint/building-and-debugging-sharepoint-solutions.md)
- [코드 품질 향상](../test/improve-code-quality.md)