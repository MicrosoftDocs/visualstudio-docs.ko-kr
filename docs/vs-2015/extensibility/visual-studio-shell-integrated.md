---
title: Visual Studio Shell (통합) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell, integrated mode features
- Shell [Visual Studio], integrated mode features
ms.assetid: 0b40d495-f17f-4bb9-ace8-b365a7172784
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 907b71d82a3c630bedc48209e735d9cf817432ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543158"
---
# <a name="visual-studio-shell-integrated"></a>Visual Studio Shell(통합)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 통합 셸에는 IDE (통합 개발 환경), 디버거 및 소스 제어 통합이 포함 되어 있습니다. 프로그래밍 언어는 포함 되지 않습니다. 그러나 통합 셸은 프로그래밍 언어를 추가 하는 데 사용할 수 있는 프레임 워크를 제공 합니다.  
  
 Visual Studio 통합 셸은 실제로는 Visual Studio 격리 셸 및 통합 된 셸 관련 구성 요소가 포함 된 추가 설치의 조합입니다.  통합 셸 응용 프로그램에는 격리 된 셸 재배포 가능 패키지 뿐만 아니라 [Microsoft Visual Studio shell](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)재배포 가능 패키지의 통합 셸 재배포 가능 패키지가 모두 포함 되어야 합니다.  
  
> [!NOTE]
> 격리 되 고 통합 된 셸 재배포 가능 패키지에 액세스 하기 전에 간단한 고객 설문 조사를 입력 하 라는 메시지가 표시 됩니다.  설문 조사를 작성 한 후에는 재배포 가능 패키지 다운로드 링크가 포함 된 Visual Studio 연결 페이지로 이동 됩니다.  **프로그램 &#124; visual studio 2015 통합 및 격리 셸** 탭의 Visual studio Connect 사이트에 대 한 후속 방문에서 다운로드 링크를 찾을 수 있습니다.  
  
 통합 셸 응용 프로그램을 전체 버전의 Visual Studio와 같은 컴퓨터에 설치 하는 경우 응용 프로그램의 구성 요소는 Visual Studio에 직접 통합 됩니다.  
  
## <a name="features-in-the-integrated-shell"></a>통합 셸에서의 기능  
  
|기능 영역|기능|  
|-|-|  
|언어 지원|-없음|  
|IDE|<ul><li>설정<br /><br /> <ul><li>설정 만들기</li><li>설정 가져오기 및 내보내기</li><li>설정 다시 설정</li></ul></li><li>**도구 상자** 통합</li><li>**작업 목록** 통합</li><li>도움말 통합</li><li>**옵션** 대화 상자</li><li>글꼴 및 색 관리</li><li>**출력** 창</li><li>**명령** 창</li><li>창 관리</li><li>명령, 메뉴 및 키 바인딩</li><li>DSL (도메인별 언어) 런타임</li></ul>|  
|프로젝트 시스템 및 프로젝트 형식|-솔루션 및 솔루션 폴더<br />-솔루션 구성 관리자<br />-항목 관리<br />-단일 프로젝트 및 다중 프로젝트 솔루션<br />-애플리케이션 디자이너 (간소화 된 프로젝트 속성)<br />-웹 참조 추가<br />-서비스 참조 추가<br />-단일 프로젝트<br />-웹 사이트 프로젝트 형식<br />-웹 응용 프로그램 프로젝트|  
|빌드|-IDE의 사용자 지정 빌드 단계<br />-지적 재산 (IP) 보호를 위한 사전 컴파일<br />-코드 서명<br />     MSBuild|  
|편집기|-코드 검색 도구 (통합 찾기, 소스 정의, 상속)<br />-코드 탐색<br />-IntelliSense<br />-스마트 태그<br />-리팩터링<br />-매우 나열<br />-IntelliSense 필터링<br />-   **코드 정의** 창|  
|Designer|-Windows Presentation Foundation 디자이너<br />-Windows Forms 디자이너<br />-웹 디자이너 및 HTML 편집기|  
|데이터|-   **서버 탐색기** (단순화: 데이터만). 참고 1을 참조하세요.<br />-   **데이터 소스** 창<br />-전체 데이터 컨트롤 집합<br />-XML 편집기<br />-로컬 데이터 원본에 데이터 바인딩 (. MDF 또는. 않았더라도<br />-개체에 데이터 바인딩<br />-웹 서비스에 데이터 바인딩<br />-로컬 데이터베이스 서버에 데이터 바인딩<br />-원격 데이터베이스 서버에 데이터 바인딩<br />-원격 데이터에 대 한 DDL 도구<br />-   **서버 탐색기** 확장성 ( [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)] 샘플)|  
|디버거|-로컬 디버깅 참고 2를 참조 하세요.<br />-관리 디버깅<br />-로컬 디버깅<br />-로컬 프로세스에 연결<br />-원격 프로세스에 연결<br />-익명 대리자<br />-응용 프로그램 도메인<br />-ASPX 디버깅<br />-특성<br />-Func 중 중단-eval<br />-중단점<br />-중단점 제약 조건<br />-호출 스택<br />-   **명령** 창<br />-크로스 스레드 디버깅<br />-데이터 팁<br />-데이터 시각화 도우미<br />-Mda (관리 디버깅 도우미)에 대 한 디버거 지원<br />-형식 전달자에 대 한 디버거 지원<br />-OTB에 대 한-d Teevents 지원<br />-JMC 스텝 퍼<br />-디버거 AppID 테스트 (DBGCLR)<br />-디버거 프로필<br />-디버거 도구 및 옵션<br />-반복기 디버깅<br />-디자인 타임 식 계산<br />-C # 식 계산기<br />-디스어셈블리<br />-편집 하며 계속 하기<br />-식 계산기 창 (조사식, 지역, 자동)<br />-예외 도우미<br />-예외<br />-실행<br />-   제네릭<br />-올바른 소스 가져오기<br />-HPC/클러스터 디버깅<br />-통합 다국어 디버깅<br />-InterOp 디버깅<br />-Just-in-time 디버깅<br />-로컬 디버깅<br />-관리 디버깅<br />-수동 컨트롤 (프로세스 창)<br />메모리<br />-미니 덤프 지원<br />-모듈<br />-다중 프로세스 디버깅<br />-네이티브 디버깅<br />-새 디버그 엔진 지원<br />최적화 된 코드 디버깅<br />-출력 windows 필터링<br />-관리 디버깅을 위한 프로세스 호스팅<br />-프로세스<br />-간략 한 조사식<br />-레지스터<br />-스택에 등록<br />-원격 디버깅<br />-반환 값<br />-스크립트 디버깅<br />-원본 서비스 지원<br />-보안<br />-Side-by-side<br />-SQL<br />-기호 서버<br />-추적 요소<br />-Thread<br />-시각화<br />-XSLT (Extensible Stylesheet Language 변환) 디버거|  
|64 비트 지원|-64-관리 코드와 네이티브 코드 모두, 모든 언어<br />-x64 기본 지원|  
|소스 코드 제어 (SCC)|-기본 SCC 통합. 참고 3을 참조하세요.<br />-도구 및 옵션 확인|  
|확장성|-Vspackage 및 MEF 구성 요소 사용|  
  
## <a name="notes"></a>참고  
  
#### <a name="1-data-tools"></a>1. 데이터 도구  
 통합 셸에는 데이터 확장성 지원 및 간소화 된 **솔루션 탐색기**와 같은 데이터베이스 개발 도구가 포함 되어 있습니다. 그러나 SQL Server Express, SQL Reporting 및 크리스탈 보고서는 통합 셸에 포함 되지 않습니다.  
  
#### <a name="2-debugging-support"></a>2. 디버깅 지원  
 통합 셸은 커뮤니티 버전의 Visual Studio에 포함 된 것과 동일한 디버깅 엔진을 포함 합니다. 디버깅 엔진에는 관리 코드에 대 한 공통 디버거와 실행, 연결, 중단점 설정, 편집 하며 계속 하기 등의 관련 기능도 포함 되어 있습니다. 그러나 디버깅 엔진은 SQL Server 데이터베이스 디버깅을 지원 하지 않습니다.  
  
 기본 디버깅에 대 한 지원은 기본 디버거 패키지에 포함 되지만 추가 언어를 지원 하도록 확장할 수 없습니다.  
  
#### <a name="3-source-code-control-integration"></a>3. 소스 코드 제어 통합  
 통합 셸은 SCC (소스 코드 제어)를 구현 하 고 MSSCCI 기반 공통 소스 제어 통합 구성 요소를 제공 하기 위한 Api를 제공 합니다.  
  
 SCC 통합은 Visual Studio Pro 버전의 일반 기능이 아니지만 통합 셸에서 SCC 통합이 제공 됩니다.  
  
#### <a name="4-build-support"></a>4. 빌드 지원  
 통합 셸에서는 빌드를 지원 합니다. [MSBuild 참조](../msbuild/msbuild-reference.md)에서 빌드에 대 한 정보를 찾을 수 있습니다.  
  
## <a name="features-not-included-in-the-integrated-shell"></a>통합 셸에 포함 되지 않은 기능  
 다음은 통합 셸에 포함 되지 않은 기능 목록입니다.  
  
- 클래스 디자이너  
  
- PreEmptive Protection - Dotfuscator  
  
- 언어 기능  
  
- Vshost.exe  
  
- Visual Studio 언어나 이와 관련 된 프로젝트 템플릿 또는 프로젝트 항목 템플릿은 통합 셸에 포함 되지 않습니다. 예를 들어 Visual Basic 코드 조각과 같은 다른 기능의 언어 관련 구현은 포함 되지 않습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 개요 확장](https://msdn.microsoft.com/library/3e9078d7-2763-4cc4-8e20-fac69d747f59)
