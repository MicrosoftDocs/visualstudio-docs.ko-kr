---
title: Visual Studio 격리 셸 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Shell [Visual Studio], shell-based applications%2C isolated mode
- Visual Studio shell, isolated mode
- isolated shell-based applications [Visual Studio]
- Visual Studio shell, shell-based applications%2C isolated mode
- Shell [Visual Studio], isolated mode
ms.assetid: d2620e71-be9e-44c9-b5b7-03a4c8d9cf0b
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef2d1cbffab5e38e603b0e50beb896f1c6efa23d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75919199"
---
# <a name="visual-studio-isolated-shell"></a>Visual Studio Shell(격리)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 격리 셸을 사용 하면 다른 버전의 Visual Studio와 나란히 실행할 수 있는 독립 실행형 응용 프로그램을 만들 수 있습니다. 주로 Visual Studio 서비스를 사용할 수 있지만 사용자 지정 된 모양과 브랜딩을 사용할 수 있는 특수 도구를 호스트 하는 데 사용 됩니다. Visual Studio 기능 및 메뉴 명령 그룹은 쉽게 설정 및 해제할 수 있습니다. 응용 프로그램 제목, 응용 프로그램 아이콘 및 시작 화면을 완전히 사용자 지정할 수 있습니다. 사용자 지정 가능한 기능 목록은 [격리 된 셸 사용자 지정](../extensibility/customizing-the-isolated-shell.md)을 참조 하세요.  
  
 격리 된 셸 프로젝트를 사용 하려면 Visual Studio SDK를 설치 해야 합니다. Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
 격리 된 셸 응용 프로그램을 만들려면 Visual Studio Shell 격리 프로젝트를 시작 합니다. 이 프로젝트에는 자체 격리 셸 응용 프로그램을 개발 하 고 테스트 하는 데 필요한 모든 항목이 포함 되어 있습니다. 응용 프로그램을 배포 하는 설치 프로그램을 작성할 준비가 되 면 [Microsoft Visual Studio Shell(격리) 재배포 가능 패키지](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)에서 격리 된 셸 재배포 가능 패키지를 가져와야 합니다.  
  
> [!NOTE]
> 격리 된 셸 재배포 가능 패키지에 액세스 하기 전에 간단한 고객 설문 조사를 입력 하 라는 메시지가 표시 됩니다.  설문 조사를 작성 한 후에는 재배포 가능 패키지 다운로드 링크가 포함 된 Visual Studio 연결 페이지로 이동 됩니다.  **프로그램 &#124; visual studio 2015 통합 및 격리 셸** 탭의 Visual studio Connect 사이트에 대 한 후속 방문에서 다운로드 링크를 찾을 수 있습니다.  
  
> [!NOTE]
> 격리 셸 기반 응용 프로그램을 배포 하는 방법에 대 한 자세한 내용은 [연습: 기본 격리 셸 응용 프로그램 만들기](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)를 참조 하세요.  
  
## <a name="working-with-the-isolated-shell"></a>격리 셸 사용  
 Visual Studio 격리 셸 응용 프로그램은 Visual Studio 서비스에 대 한 모든 권한을 가지 며 특수 한 사용자 지정 및 브랜딩을 지원 합니다. 여러 가지 방법으로 격리 셸 응용 프로그램을 사용자 지정할 수 있습니다.  
  
- MEF (Vspackage and Managed Extensibility Framework) 구성 요소 부분을 사용 하 여 다른 Visual Studio 확장에서 사용 하는 것과 마찬가지로 격리 된 셸 응용 프로그램을 확장할 수 있습니다. 자세한 내용은 [격리 된 셸 확장](../extensibility/extending-the-isolated-shell.md)을 참조 하세요.  
  
- Visual Studio 기능 및 메뉴 명령 그룹을 사용 하거나 사용 하지 않도록 설정 하려면 응용 프로그램의 UI (사용자 인터페이스) 프로젝트에서 vsct 파일을 업데이트 합니다.  
  
- 응용 프로그램에서 **옵션** 페이지 또는 기타 Visual Studio shell 구성 요소를 제거 하려면 응용 프로그램의 .pkgundef 파일을 업데이트 합니다.  
  
- 셸의 모양이 나 동작의 다른 측면을 수정 하려면 응용 프로그램의 .pkgdef 파일을 업데이트 합니다.  
  
- 응용 프로그램이 시작 되 면 셸의 일부 측면을 지정할 수도 있습니다. 이렇게 하려면 appenvstub.dll의 시작 진입점에 대 한 호출의 매개 변수를 업데이트 합니다.  
  
  사용자 지정할 수 있는 다양 한 요소에 대 한 자세한 내용은 [격리 된 셸의 요소](../extensibility/elements-of-the-isolated-shell.md)를 참조 하세요.  
  
## <a name="standard-features-of-the-isolated-shell"></a>격리 된 셸의 표준 기능  
 다음은 모든 버전의 Visual Studio에 대 한 표준 기능입니다.  
  
|기능 범주|기능|  
|----------------------|-------------|  
|IDE 기능|가져오기/내보내기 설정<br /><br /> 도구 상자 컨트롤 설치 관리자<br /><br /> 작업 목록 & 오류 목록<br /><br /> 출력 창<br /><br /> 시작 페이지<br /><br /> 속성 창<br /><br /> 도구 상자<br /><br /> 솔루션 탐색기<br /><br /> 책갈피 창<br /><br /> 클래스 뷰<br /><br /> 개체 브라우저<br /><br /> 명령 창<br /><br /> 문서 개요<br /><br /> 리소스 뷰<br /><br /> 외부 도구<br /><br /> WCF (Windows Communication Foundation) 서비스 참조 추가<br /><br /> LINQ (통합 언어 쿼리) 지원|  
|편집기/디자이너|코드 검색 도구 (통합 찾기, 소스 정의, 상속)<br /><br /> IntelliSense<br /><br /> 창이<br /><br /> 코드 조각 관리자<br /><br /> 코드 조각<br /><br /> 리팩터링<br /><br /> 매우 나열<br /><br /> IntelliSense 필터링<br /><br /> 코드 정의 창<br /><br /> 애플리케이션 디자이너<br /><br /> Windows Forms 디자이너<br /><br /> Windows Presentation Foundation (WPF) 디자이너|  
|디버깅|C # 식 계산기<br /><br /> 로컬 디버깅<br /><br /> 관리 디버깅<br /><br /> 편집하며 계속하기<br /><br /> 크로스 스레드 디버깅<br /><br /> 시각화<br /><br /> 데이터 팁<br /><br /> 네이티브 디버깅<br /><br /> 스크립트 디버깅<br /><br /> Interop 디버깅<br /><br /> JIT (just-in-time) 디버깅<br /><br /> 다중 프로세스 디버깅<br /><br /> XSLT 디버깅<br /><br /> 로컬 프로세스에 연결<br /><br /> 추적 지점<br /><br /> 중단점 제약 조건|  
|데이터|서버 탐색기 (단순 데이터 전용)<br /><br /> 로컬 데이터에 데이터 바인딩 (. MDF 또는. 않았더라도<br /><br /> 개체에 데이터 바인딩<br /><br /> 웹 서비스에 데이터 바인딩<br /><br /> 전체 데이터 컨트롤 집합<br /><br /> XML 편집기<br /><br /> 로컬 데이터베이스 서버에 데이터 바인딩<br /><br /> 데이터 소스 창|  
|웹|HTML 편집기<br /><br /> 웹 브라우저<br /><br /> Web Forms 디자이너<br /><br /> 웹 사이트 프로젝트<br /><br /> 웹 응용 프로그램 프로젝트|  
|확장성|Vspackage 및 MEF 구성 요소를 사용 합니다.|  
  
## <a name="see-also"></a>관련 항목  
 [셸(격리 또는 통합)](../extensibility/shell-isolated-or-integrated.md)
