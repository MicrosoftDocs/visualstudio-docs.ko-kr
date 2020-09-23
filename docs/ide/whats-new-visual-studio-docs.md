---
title: 'Visual Studio 문서: 2020년 8월의 새로운 기능 '
titleSuffix: ''
description: 2020년 8월 추가된 Visual Studio의 새로운 기능을 소개합니다.
ms.date: 09/02/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 89844796-621B-4EF5-9D76-197084B011CB
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: 2411299fbab6dfba8ced0f689bd33825b62614af
ms.sourcegitcommit: 566144d59c376474c09bbb55164c01d70f4b621c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/19/2020
ms.locfileid: "90808983"
---
# <a name="visual-studio-docs-whats-new-for-august-2020"></a>Visual Studio 문서: 2020년 8월의 새로운 기능

2020년 8월 추가된 Visual Studio의 새로운 기능에 대해 알아보세요. 해당 기간 동안 이루어진 문서의 주요 변경 사항을 소개합니다. 이전 달의 새로운 기능에 대한 자세한 내용은 [새로운 기능 기록](whats-new-visual-studio-docs-history.md) 항목을 참조하세요.

## <a name="azure"></a>Azure

**새 문서**

- [Visual Studio 연결된 서비스를 사용하여 Azure Application Insights 추가](../azure/azure-app-insights-add-connected-service.md) - VS 2019 16.7의 연결된 서비스
- [Visual Studio 연결된 서비스를 사용하여 Azure Cache for Redis 추가](../azure/azure-cache-for-redis-add-connected-service.md) - VS 2019 16.7의 연결된 서비스
- [Visual Studio 연결된 서비스를 사용하여 앱에 Azure Cosmos DB 추가](../azure/azure-cosmosdb-add-connected-service.md) - VS 2019 16.7의 연결된 서비스
- [Visual Studio 연결된 서비스를 사용하여 Azure SignalR 추가](../azure/azure-signalr-add-connected-service.md) - VS 2019 16.7의 연결된 서비스
- [Azure SQL Database에 연결 추가](../azure/azure-sql-database-add-connected-service.md) - VS 2019 16.7의 연결된 서비스

**업데이트된 문서**

- [Visual Studio 연결 서비스를 사용하여 Azure Storage 추가](../azure/vs-azure-tools-connected-services-storage.md)
  - VS 2019 16.7의 연결된 서비스
  - Azure Storage 연결된 서비스 문서: 업데이트 UI 및 지원되는 프로젝트 형식

## <a name="code-quality"></a>코드 품질

**새 문서**

- [CA1310: 정확성을 위해 StringComparision 지정](../code-quality/ca1310.md) - CA1310 문서 추가 및 CA1307 문서 업데이트
- [CA1837: Process.GetCurrentProcess().Id 대신 Environment.ProcessId 사용](../code-quality/ca1837.md) - CA1837 문서
- [CA1838: P/Invokes에 대한 `StringBuilder` 매개 변수 사용하지 않음](../code-quality/ca1838.md) - CA1838 문서 추가
- [CA2008: TaskScheduler를 전달하지 않은 상태에서 작업을 만들지 않음](../code-quality/ca2008.md) - CA2008 문서 추가
- [CA2249: String.IndexOf 대신 String.Contains 사용 고려](../code-quality/ca2249.md) - CA2249 문서
- [CA2361: DataSet.ReadXml()을 포함하는 자동 생성된 클래스가 신뢰할 수 없는 데이터와 함께 사용되지 않도록 하기](../code-quality/ca2361.md) - 추가 DataSet/DataTable 규칙
- [CA2362: 자동 생성된 직렬화 가능 형식의 안전하지 않은 DataSet 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있음](../code-quality/ca2362.md) - 추가 DataSet/DataTable 규칙
- [IL3000: 단일 파일로 게시할 때 어셈블리 파일 경로 액세스를 사용하지 않음](../code-quality/il3000.md) - IL3000 문서 추가
- [IL3001: 단일 파일로 게시할 때 어셈블리 파일 경로 액세스를 사용하지 않음](../code-quality/il3001.md) - IL3001 문서 추가

**업데이트됨**

- [CA1002: 제네릭 목록을 노출하지 않음](../code-quality/ca1002.md) - 구성 가능성 추가 - Api Surface 섹션
- [CA1046: 참조 형식에 같음 연산자를 오버로드하지 않음](../code-quality/ca1046.md) - 구성 가능성 추가 - Api Surface 섹션
- [CA1307: 명확성을 위해 StringComparision 지정](../code-quality/ca1307.md) - CA1310 문서 추가 및 CA1307 문서 업데이트
- [CA1700: 열거형 값 &#39;Reserved&#39;의 이름을 지정하지 않음](../code-quality/ca1700.md) - 구성 가능성 추가 - Api Surface 섹션
- [CA1707: 식별자는 밑줄을 포함할 수 없음](../code-quality/ca1707.md) - 구성 가능성 추가 - Api Surface 섹션
- [CA1822: 멤버를 정적으로 표시](../code-quality/ca1822.md) - 구성 가능성 추가 - Api Surface 섹션
- [CA2351: DataSet.ReadXml()의 입력을 신뢰할 수 있는지 확인](../code-quality/ca2351.md) - 추가 DataSet/DataTable 규칙
- [타사 분석기 설치](../code-quality/install-roslyn-analyzers.md) - 코드 분석 문서의 구조 및 제목 변경

## <a name="containers"></a>컨테이너

**업데이트된 문서**

- [Visual Studio를 사용하여 컨테이너 레지스트리에 ASP.NET 컨테이너 배포](../containers/hosting-web-apps-in-docker.md) - Visual Studio 16.7 게시 UI의 컨테이너 도구 업데이트
- [Visual Studio Kubernetes 도구 시작](../containers/tutorial-kubernetes-tools.md) - Kubernetes 자습서: 제거 단계 추가

## <a name="deployment"></a>배포

**새 문서**

- [Visual Studio 설치 관리자 프로젝트 확장 및 .NET Core 3.1](../deployment/installer-projects-net-core.md) - 설치 관리자 프로젝트 .NET Core 3.1 기능의 새 도움말 페이지 만들기

**업데이트된 문서**

- [폴더, IIS, Azure 또는 다른 대상에 앱 배포](../deployment/deploying-applications-services-and-components-resources.md) - 배포 업데이트
- [Visual Studio에서 배포](../deployment/index.yml) - 배포 업데이트

## <a name="extensibility"></a>확장성

**업데이트된 문서**
- [프로젝트 하위 형식](../extensibility/internals/project-subtypes.md) - 목록 항목 들여쓰기 수정
- [Visual Studio 색 값 참조](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) - AB#1759333 누락 열 머리글 수정

## <a name="get-started"></a>시작

**업데이트된 문서**

- [5단계: Azure에 ASP.NET Core 앱 배포](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) - 새 연결된 서비스 UI의 비디오 자습서 업데이트

## <a name="ide"></a>IDE

**새 문서**

- [Visual Studio에서 F1 도움말 키 변경](./not-in-toc/change-f1-help-key.md) - 기본 F1 도움말 페이지 리팩터링
- [텍스트 편집기의 F1 도움말](./not-in-toc/default-f1-text-editor.md) - 기본 F1 도움말 페이지 리팩터링
- [`typeof`를 `nameof`로 변환](./reference/convert-typeof-to-nameof.md) - typeof를 nameof로 변환 리팩터링
- [LINQ 식 간소화](./reference/simplify-linq-expression.md) - LINQ 식 간소화 리팩터링

**업데이트된 문서**

- [Visual Studio에서 창 레이아웃 사용자 지정](./customizing-window-layouts-in-visual-studio.md) - 창 레이아웃 사용자 지정 항목에 모니커된 세로 문서 탭 추가
- [Visual Studio 또는 Visual Studio 설치 관리자로 문제를 보고하는 방법](./how-to-report-a-problem-with-visual-studio.md)
  - NMI에 자세한 정보 추가
  - 전체 문제 보고 페이지 다시 작성
- [F1 도움말](./not-in-toc/default.md) - 기본 F1 도움말 페이지 리팩터링
- [자동 복구, 환경, 옵션 대화 상자](./reference/autorecover-environment-options-dialog-box.md) - 업데이트된 자동 저장 파일 위치에 대한 정보 추가
- [옵션, 텍스트 편집기, 기본(Visual Basic), 고급](./reference/options-text-editor-basic-visual-basic.md) - 인라인 매개 변수 이름 힌트에 대한 기본 문서 추가
- [옵션, 텍스트 편집기, C#, 고급](./reference/options-text-editor-csharp-advanced.md) - 인라인 매개 변수 이름 힌트에 대한 기본 문서 추가
- [Visual Studio 성능 팁과 요령](./visual-studio-performance-tips-and-tricks.md) - ‘맵 모드 사용 안 함' 및 '자동 줄 바꿈 사용 안 함' 정보 추가
- [Visual Studio 2019의 새로운 기능](./whats-new-visual-studio-2019.md) - 16.7 GA 정보로 Visual Studio 2019의 새로운 기능 업데이트

## <a name="rtvs"></a>RTVS

**업데이트된 문서**

- [SQL Server 및 R 사용](../rtvs/integrating-sql-server-with-r.md) - 열 머리글을 포함하도록 테이블 수정

## <a name="community-contributors"></a>커뮤니티 기여자

이 기간 동안 Visual Studio 문서에 기여한 사용자는 다음과 같습니다. 감사합니다! [기여자 가이드](/contribute/)의 지침에 따라 Visual Studio 문서에 기여하는 방법을 알아보세요.

- [AlexB-SheldonMFG](https://github.com/AlexB-SheldonMFG) - Alex Black (11)
- [Youssef1313](https://github.com/Youssef1313) - Youssef Victor (8)
- [hyoshioka0128](https://github.com/hyoshioka0128) - Hiroshi Yoshioka (3)
- [AstroChoco](https://github.com/AstroChoco) - Qian Lu (Chocolate) (1)
- [athyunnath](https://github.com/athyunnath) - Athyunnath Eleti (1)
- [caro-oviedo](https://github.com/caro-oviedo) - Caro Oviedo (1)
- [Evangelink](https://github.com/Evangelink) - Amaury Levé (1)
- [jethas-bennettjones](https://github.com/jethas-bennettjones) - Shafiq Jetha (1)
- [nebuk89](https://github.com/nebuk89) - Ben De St Paer-Gotch (1)
- [pcartwright81](https://github.com/pcartwright81) (1)
- [pkulikov](https://github.com/pkulikov) - Petr Kulikov (1)
- [riQQ](https://github.com/riQQ) (1)
- [tcmetzger](https://github.com/tcmetzger) - Timo Cornelius Metzger (1)
- [weitzhandler](https://github.com/weitzhandler) - Shimmy (1)