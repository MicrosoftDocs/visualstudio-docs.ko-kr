---
title: 'Visual Studio 문서: 새로운 기능 기록 '
titleSuffix: ''
description: Visual Studio 문서의 새로운 기능에 관한 기록
ms.date: 09/30/2020
helpviewer_keywords:
- Visual Studio, what's new, docs
- what's new [Visual Studio]
ms.assetid: 511DAFC7-896E-449A-BFF7-0E8F7BBA8A78
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.topic: conceptual
ms.workload:
- multiple
ms.openlocfilehash: b9aba6b9c4be882498535ab96020461f22722c10
ms.sourcegitcommit: c025a5e2013c4955ca685092b13e887ce64aaf64
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91659305"
---
# <a name="history-of-whats-new-in-visual-studio-docs"></a>Visual Studio 문서의 새로운 기능에 관한 기록

Visual Studio 문서의 새로운 기능 기록을 봅니다. 이 항목에는 2020년 7월부터 2020년 9월 이전의 문서 주요 변경 내용이 포함되어 있습니다. 새로운 기능의 최신 내용은 [Visual Studio 문서: 문서에 추가된 새로운 기능](whats-new-visual-studio-docs.md)을 참조하세요.

## <a name="august-2020"></a>2020년 8월
### <a name="azure"></a>Azure

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

### <a name="code-quality"></a>코드 품질

**새 문서**

- [CA1310: 정확성을 위해 StringComparision 지정](/dotnet/fundamentals/code-analysis/quality-rules/ca1310) - CA1310 문서 추가 및 CA1307 문서 업데이트
- [CA1837: Process.GetCurrentProcess().Id 대신 Environment.ProcessId 사용](/dotnet/fundamentals/code-analysis/quality-rules/ca1837) - CA1837 문서
- [CA1838: P/Invokes에 대한 `StringBuilder` 매개 변수 사용하지 않음](/dotnet/fundamentals/code-analysis/quality-rules/ca1838) - CA1838 문서 추가
- [CA2008: TaskScheduler를 전달하지 않은 상태에서 작업을 만들지 않음](/dotnet/fundamentals/code-analysis/quality-rules/ca2008) - CA2008 문서 추가
- [CA2249: String.IndexOf 대신 String.Contains 사용 고려](/dotnet/fundamentals/code-analysis/quality-rules/ca2249) - CA2249 문서
- [CA2361: DataSet.ReadXml()을 포함하는 자동 생성된 클래스가 신뢰할 수 없는 데이터와 함께 사용되지 않도록 하기](/dotnet/fundamentals/code-analysis/quality-rules/ca2361) - 추가 DataSet/DataTable 규칙
- [CA2362: 자동 생성된 직렬화 가능 형식의 안전하지 않은 DataSet 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있음](/dotnet/fundamentals/code-analysis/quality-rules/ca2362) - 추가 DataSet/DataTable 규칙
- [IL3000: 단일 파일로 게시할 때 어셈블리 파일 경로 액세스를 사용하지 않음](/dotnet/fundamentals/code-analysis/quality-rules/il3000) - IL3000 문서 추가
- [IL3001: 단일 파일로 게시할 때 어셈블리 파일 경로 액세스를 사용하지 않음](/dotnet/fundamentals/code-analysis/quality-rules/il3001) - IL3001 문서 추가

**업데이트됨**

- [CA1002: 제네릭 목록을 노출하지 않음](/dotnet/fundamentals/code-analysis/quality-rules/ca1002) - 구성 가능성 추가 - Api Surface 섹션
- [CA1046: 참조 형식에 같음 연산자를 오버로드하지 않음](/dotnet/fundamentals/code-analysis/quality-rules/ca1046) - 구성 가능성 추가 - Api Surface 섹션
- [CA1307: 명확성을 위해 StringComparision 지정](/dotnet/fundamentals/code-analysis/quality-rules/ca1307) - CA1310 문서 추가 및 CA1307 문서 업데이트
- [CA1700: 열거형 값 &#39;Reserved&#39;의 이름을 지정하지 않음](/dotnet/fundamentals/code-analysis/quality-rules/ca1700) - 구성 가능성 추가 - Api Surface 섹션
- [CA1707: 식별자는 밑줄을 포함할 수 없음](/dotnet/fundamentals/code-analysis/quality-rules/ca1707) - 구성 가능성 추가 - Api Surface 섹션
- [CA1822: 멤버를 정적으로 표시](/dotnet/fundamentals/code-analysis/quality-rules/ca1822) - 구성 가능성 추가 - Api Surface 섹션
- [CA2351: DataSet.ReadXml()의 입력을 신뢰할 수 있는지 확인](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) - 추가 DataSet/DataTable 규칙
- [타사 분석기 설치](../code-quality/install-roslyn-analyzers.md) - 코드 분석 문서의 구조 및 제목 변경

### <a name="containers"></a>컨테이너

**업데이트된 문서**

- [Visual Studio를 사용하여 컨테이너 레지스트리에 ASP.NET 컨테이너 배포](../containers/hosting-web-apps-in-docker.md) - Visual Studio 16.7 게시 UI의 컨테이너 도구 업데이트
- [Visual Studio Kubernetes 도구 시작](../containers/bridge-to-kubernetes.md) - Kubernetes 자습서: 제거 단계 추가

### <a name="deployment"></a>배포

**새 문서**

- [Visual Studio 설치 관리자 프로젝트 확장 및 .NET Core 3.1](../deployment/installer-projects-net-core.md) - 설치 관리자 프로젝트 .NET Core 3.1 기능의 새 도움말 페이지 만들기

**업데이트된 문서**

- [폴더, IIS, Azure 또는 다른 대상에 앱 배포](../deployment/deploying-applications-services-and-components-resources.md) - 배포 업데이트
- [Visual Studio에서 배포](../deployment/index.yml) - 배포 업데이트

### <a name="extensibility"></a>확장성

**업데이트된 문서**
- [프로젝트 하위 형식](../extensibility/internals/project-subtypes.md) - 목록 항목 들여쓰기 수정
- [Visual Studio 색 값 참조](../extensibility/ux-guidelines/color-value-reference-for-visual-studio.md) - AB#1759333 누락 열 머리글 수정

### <a name="get-started"></a>시작

**업데이트된 문서**

- [5단계: Azure에 ASP.NET Core 앱 배포](../get-started/csharp/tutorial-aspnet-core-ef-step-05.md) - 새 연결된 서비스 UI의 비디오 자습서 업데이트

### <a name="ide"></a>IDE

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

### <a name="rtvs"></a>RTVS

**업데이트된 문서**

- [SQL Server 및 R 사용](../rtvs/integrating-sql-server-with-r.md) - 열 머리글을 포함하도록 테이블 수정

## <a name="july-2020"></a>2020년 7월
### <a name="code-quality"></a>코드 품질

**새 문서**

- [CA1417: P/Invokes에 대한 문자열 매개 변수에 `OutAttribute`를 사용하지 않음](/dotnet/fundamentals/code-analysis/quality-rules/ca1417) - CA1417에 대한 문서 추가
- [CA1805: 불필요하게 초기화하지 않음](/dotnet/fundamentals/code-analysis/quality-rules/ca1805) - CA1805에 대한 문서 추가
- [CA1836: 사용할 수 있는 경우 Count보다 IsEmpty를 선호함](/dotnet/fundamentals/code-analysis/quality-rules/ca1836) - CA1836에 대한 문서 추가(Count보다 IsEmpty 선호)
- [CA2016: CancellationToken 매개 변수를 사용하는 메서드에 전달](/dotnet/fundamentals/code-analysis/quality-rules/ca2016) - 문서 CA2016 - CancellationToken 매개 변수를 사용하는 메서드에 전달
- [CA2350: DataTable.ReadXml()의 입력을 신뢰할 수 있는지 확인](/dotnet/fundamentals/code-analysis/quality-rules/ca2350) - 초기 DataSet/DataTable Deserialization 규칙 문서
- [CA2351: DataSet.ReadXml()의 입력을 신뢰할 수 있는지 확인](/dotnet/fundamentals/code-analysis/quality-rules/ca2351) - 초기 DataSet/DataTable Deserialization 규칙 문서
- [CA2352: 직렬화 가능 형식의 안전하지 않은 데이터 세트 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있음](/dotnet/fundamentals/code-analysis/quality-rules/ca2352) - 초기 DataSet/DataTable Deserialization 규칙 문서
- [CA2353: 직렬화 가능한 유형의 안전하지 않은 DataSet 또는 DataTable](/dotnet/fundamentals/code-analysis/quality-rules/ca2353) - 초기 DataSet/DataTable Deserialization 규칙 문서
- [CA2354: 역직렬화된 개체 그래프의 안전하지 않은 데이터 세트 또는 DataTable은 원격 코드 실행 공격에 취약할 수 있음](/dotnet/fundamentals/code-analysis/quality-rules/ca2354) - 초기 DataSet/DataTable Deserialization 규칙 문서
- [CA2355: 직렬화된 개체 그래프의 안전하지 않은 DataSet 또는 DataTable](/dotnet/fundamentals/code-analysis/quality-rules/ca2355) - 초기 DataSet/DataTable Deserialization 규칙 문서
- [CA2356: 직렬화된 웹 개체 그래프의 안전하지 않은 DataSet 또는 DataTable 유형](/dotnet/fundamentals/code-analysis/quality-rules/ca2356) - 초기 DataSet/DataTable Deserialization 규칙 문서

### <a name="containers"></a>컨테이너

**새 문서**

- [Kubernetes와 함께 로컬 프로세스 구성](../containers/configure-bridge-to-kubernetes.md) - Kubernetes를 사용한 로컬 프로세스: yaml 구성
- [Kubernetes와 함께 로컬 프로세스 사용(미리 보기)](../containers/bridge-to-kubernetes.md) - 개발 공간 마이그레이션
- [Kubernetes와 함께 로컬 프로세스를 사용하는 경우의 작동 방식](../containers/overview-bridge-to-kubernetes.md)
  - Kubernetes용 로컬 프로세스: 라우팅 섹션 추가
  - 개발 공간 마이그레이션

### <a name="cross-platform"></a>플랫폼 간

**업데이트된 문서**

- [변경 로그(Visual Studio Tools for Unity, Windows)](../cross-platform/change-log-visual-studio-tools-for-unity.md) - 4.7.1.0에 대한 Bump VSTU 변경 로그
- [변경 로그(Visual Studio Tools for Unity, Mac)](../cross-platform/change-log-visual-studio-tools-for-unity-mac.md) - 2.7.1.0에 대한 Bump VSTUM 변경 로그

### <a name="get-started"></a>시작

**새 문서**

- [자습서: 간단한 C# 콘솔 앱 확장](../get-started/csharp/tutorial-console-part-2.md) - 릴리스 확장 사이드워크 자습서 첫 버전

### <a name="ide"></a>IDE

**새 문서**

- [Developer Community 지침](./developer-community-guidelines.md) - DevCom 지침 추가됨
- [가져오지 않은 형식 및 확장 메서드에 대한 IntelliSense 완성](./reference/intellisense-completion-unimported-types-extension-methods.md)

### <a name="install"></a>설치

**새 문서**

- [최소 오프라인 레이아웃으로 Visual Studio 업데이트](../install/update-minimal-layout.md) - 문서 최소 레이아웃 기능
- [Visual Studio 엔터프라이즈 가이드](../install/visual-studio-enterprise-guide.md) - 엔터프라이즈 가이드

### <a name="javascript"></a>JavaScript

**새 문서**

- [TypeScript 코드 컴파일(Node.js)](../javascript/compile-typescript-code-npm.md) - TypeScript 컴파일 및 빌드
- [TypeScript 코드 컴파일(ASP.NET Core)](../javascript/compile-typescript-code-nuget.md) - TypeScript 컴파일 및 빌드

### <a name="msbuild"></a>MSBuild

**새 문서**

- [공통 MSBuild 항목 메타데이터](../msbuild/common-msbuild-item-metadata.md) - MSBuild: Link 및 LinkBase를 사용해 옵션 메타데이터에 대한 테이블 추가
- [MSBuild의 솔루션 필터](../msbuild/solution-filters.md) - MSBuild 솔루션 필터

### <a name="test"></a>테스트

**새 문서**

- [테스트 탐색기를 사용하여 단위 테스트 디버그 및 분석](../test/debug-unit-tests-with-test-explorer.md) - 테스트 탐색기 성능 작업

**업데이트된 문서**

- [ *.runsettings* 파일을 사용하여 단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
  - .runsettings 파일을 사용하여 단위 테스트 구성 업데이트
  - 원인 옵션 설명이 변경되었으며 예제가 추가되었습니다.