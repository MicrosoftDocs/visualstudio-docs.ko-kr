---
title: 웹 프로젝트 Essentials | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 95c9f7c530d50a7eb89ebe33fad3862f036972d1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825622"
---
# <a name="web-project-essentials"></a>웹 프로젝트 필수 항목
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

웹 프로젝트는 웹 응용 프로그램을 만듭니다. 웹 프로젝트를 사용 하 여 스마트 웹 페이지를 포함 하는 웹 응용 프로그램을 만들 수 있습니다. 스마트 웹 페이지에는 요청 시 웹 페이지를 렌더링 하는 서버측 코드가 있습니다.  
  
 또는와 같은 기존 프로그래밍 언어를 사용 하 여 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] [!INCLUDE[csprcs](../../includes/csprcs-md.md)] 스마트 웹 페이지를 만들어 사용자 로부터 정보를 수집 및 처리 하 고 데이터베이스에 저장 하는 등의 작업을 수행할 수 있습니다.  
  
- 코드를 사용 하는 모델은 종속 소스 코드 파일을 파일 확장명이 .aspx 또는 .asmx 인 웹 페이지와 연결 합니다. 예를 들어, hello .aspx에는 종속 소스 코드 파일 hello.aspx.cs가 있을 수 있습니다.  
  
- 스마트 웹 페이지와 관련 된 서버 쪽 코드는 웹 사이트 기능 폴더에 있는 실행 파일로 컴파일됩니다.  
  
- 특정 웹 페이지와 연결 되지 않은 도우미 클래스와 같은 추가 소스 코드 파일은 웹 사이트/App_Code 폴더에 있습니다.  
  
  - WSP (웹 사이트 프로젝트)는 각 스마트 웹 페이지에 대해 하나의 실행 파일을 생성 합니다. /App_Code 폴더의 모든 소스 코드 파일에서 실행 파일이 추가로 생성 됩니다.  

  - WAP (웹 응용 프로그램 프로젝트)는/App_Code 폴더의 모든 소스 파일 뿐만 아니라 모든 스마트 웹 페이지에 대 한 코드를 결합 하는 단일 실행 파일을 생성 합니다.  
  
- 웹 프로젝트에 대 한 솔루션 파일은 웹 사이트 자체와 별도로 배치 됩니다. 기본적으로 솔루션 파일은 \Documents 및 설정의 \\ *계정*\My Documents \\ *\<Visual Studio ####>* \projects \\ *웹 사이트*에 있습니다.  
  
    > [!NOTE]
    > 솔루션 파일을 웹 사이트와 함께 유지 하려면 해당 파일을 이동 하 여 다시 엽니다.  
  
- Visual Studio에서 솔루션 파일이 없는 웹 사이트를 열면 새 솔루션 파일이 자동으로 생성 됩니다.  
  
- 웹 프로젝트에는 프로젝트 파일이 없습니다. 프로젝트 정보는 솔루션 파일, web.config 파일 및 기타 위치에 저장 됩니다.  
  
- 웹 프로젝트에 전역 속성을 추가 하면 자동으로 웹 프로젝트 솔루션 폴더에 저장소 파일이 만들어집니다.  
  
- 페이지 지시문 또는 태그를 사용 하 여 서버 쪽 프로그래밍 언어에 스마트 웹 페이지를 연결할 수 있습니다 \<script runat="server"> .  
  
- 또한 웹 페이지에는 모든 스크립팅 언어로 작성 된 많은 수의 클라이언트 쪽 스크립팅 블록이 있을 수 있습니다.  
  
- 웹 사이트 프로젝트 시스템은 프로젝트 및 항목 템플릿을 추가 하 고 프로젝트에 등록 하 여 구현 됩니다 [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] .  
  
- WAP 시스템은 프로젝트 버전 이라는 프로젝트 하위 형식으로 구현 됩니다. Wap [!INCLUDE[vwprvw](../../includes/vwprvw-md.md)] 하위 형식에 의해 프로젝트가 FLAVORED wap 시스템을 만듭니다. 프로젝트 하위 형식에 대 한 자세한 내용은 [프로젝트 하위 형식](../../extensibility/internals/project-subtypes.md)을 참조 하세요.  
  
- 스마트 웹 페이지는 HTML을 서버 쪽 프로그래밍 언어와 결합 합니다. 서버 쪽 언어를 포함 된 언어 라고 합니다. 포함 된 언어를 지원 하려면 웹 프로젝트 시스템에서 인터페이스 패밀리를 구현 해야 합니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> .  
  
  - 편집기에서 포함 된 언어를 지원 하려면 HTML 언어 서비스가 포함 된 언어 서비스에 포함 된 언어 코드를 표시 하는 것을 연기 해야 합니다.  

  - 오류 표식 (빨강 물결 모양)은 항상 코드 편집기의 기본 버퍼에 만들어야 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [웹 프로젝트](../../extensibility/internals/web-projects.md)
