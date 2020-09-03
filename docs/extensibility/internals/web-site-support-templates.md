---
title: 웹 사이트 지원 템플릿 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- we site projects, templates
ms.assetid: 37173c97-486b-4b3c-8ed3-cf5890c4de23
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0e3c139ae6f2f9ec618e6382a1551a9e35eee7ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80703460"
---
# <a name="web-site-support-templates"></a>웹 사이트 지원 템플릿
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 웹 사이트 프로젝트 및 항목 템플릿은 새 웹 사이트 프로젝트 및 항목을 처음부터 새로 만들 필요가 없도록 하 여 개발 프로세스를 가속화 하는 재사용 가능 하 고 사용자 지정 가능한 웹 사이트 프로젝트 및 항목 스텁을 제공 합니다. 템플릿에 대 한 자세한 내용은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [프로젝트 템플릿 및 항목 템플릿 만들기](../../ide/creating-project-and-item-templates.md)를 참조 하세요.

## <a name="project-template-folder"></a>프로젝트 템플릿 폴더
 웹 프로젝트 템플릿은 일반적으로 웹 프로그래밍 언어를 따라 명명 된 하위 폴더에 있는 [*Visual Studio 설치 경로*] \Common7\IDE\ProjectTemplates\Web에 설치 됩니다 \\ .

## <a name="project-file"></a>프로젝트 파일
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]IDE (통합 개발 환경)에는 템플릿을 올바른 프로젝트 형식에 매핑하는 방법으로 프로젝트 파일 확장명이 필요 합니다. 웹 프로젝트에는 프로젝트 파일이 없으므로 더미 프로젝트 파일 확장명. webproj가 등록 되어 템플릿을 프로젝트 형식에 매핑합니다.

 필요에 따라 템플릿을 기반으로 하는 항목에 대 한 **새 항목 추가** 대화 상자에서 웹 프로젝트 시스템을 사용 하 여 언어 기본값을 설정할 수 있도록 템플릿에 언어 이름 문자열을 추가할 수 있습니다. 문자열은 파일의 첫 번째 줄 이어야 합니다. IntelliSense 엔진 등록에서 AddItemLanguageName에 등록 된 이름과 프로젝트 하위 형식 (.Vstemplate)에 등록 된 이름을 모두 일치 해야 합니다. 자세한 내용은 [웹 사이트 지원 특성](../../extensibility/internals/web-site-support-attributes.md)을 참조 하세요.

 문자열이 없는 경우 웹 프로젝트 시스템은 프로젝트 템플릿에 의해 웹 프로젝트에 추가 된 페이지의 언어 특성 및 파일 확장명을 기준으로 기본 언어를 결정 하려고 합니다.

## <a name="project-templates"></a>프로젝트 템플릿
 웹 사이트 프로젝트 템플릿은 **파일** 메뉴의 **새 웹 사이트** 명령에 대 한 응답으로 새 웹 사이트를 빌드하는 데 사용 됩니다. 현재 세 가지 웹 사이트 프로젝트 형식이 지원 됩니다.

- 빈 웹 사이트 프로젝트

- 웹 사이트 프로젝트

- 웹 서비스 프로젝트

### <a name="empty-web-site-projects"></a>빈 웹 사이트 프로젝트
 이러한 파일은 **빈 웹** 사이트 명령에 대 한 응답으로 빈 웹 사이트를 새로 만듭니다 .이 명령은 **파일**  >  **새로 만들기 웹 사이트**를 선택한 후에 사용할 수 있습니다.

- EmptyWeb

     새 빈 웹 사이트를 만드는 과정을 안내 하는 템플릿 파일입니다.

- EmptyWeb

     이 파일은 프로젝트 템플릿 시스템의 아티팩트입니다. EmptyWeb 파일의 프로젝트 파일 참조를 충족 합니다.

### <a name="web-site-projects"></a>웹 사이트 프로젝트
 이러한 파일은 **ASP.NET 웹 사이트** 명령에 대 한 응답으로 새 웹 사이트를 만듭니다 .이 명령에는 **파일**  >  **새로 만들기 웹 사이트**를 선택한 후 사용할 수 있습니다.

- Default.aspx

     새 웹 사이트의 기본 홈 페이지입니다. Language 특성은 codebehind 언어를 지정 하 고 CodeFile 특성은이 페이지와 연결 된 codebehind 코드를 포함 하는 종속 파일을 지정 합니다.

- Default.aspx. *확장*

     기본 홈 페이지에 대 한 코드 숨김 코드를 포함 하는 종속 파일입니다. Codebehind 언어는이 파일의 *확장명* 을 결정 합니다.

- web.config

     루트 웹 사이트 구성 파일입니다.

- WebApplication .vstemplate

     웹 사이트 솔루션의 콘텐츠를 확인 하 고 App_Data 폴더를 강제로 만들도록 하는 템플릿 파일입니다.

- WebApplication. webproj

     이 파일은 프로젝트 템플릿 시스템의 아티팩트입니다. WebApplication .vstemplate 파일의 프로젝트 파일 참조를 충족 합니다.

### <a name="web-service-projects"></a>웹 서비스 프로젝트
 이러한 파일은 **파일**새로 만들기 웹 사이트를 선택한 후 사용할 수 있는 **ASP.NET 웹 서비스** 명령에 응답 하 여 새 웹 사이트를 만듭니다  >  **New Web Site**.

- Service .asmx

     새 웹 서비스에 대 한 HTML 페이지입니다. Language 특성은 codebehind 언어를 지정 하 고 CodeBehind 특성은이 서비스와 연결 된 코드 숨김 코드를 포함 하는 종속 파일을 지정 합니다.

- 서비스. *확장*

     서비스 클래스를 구현 하는 종속 파일입니다. Codebehind 언어는이 파일의 *확장명* 을 결정 합니다.

- web.config

- 루트 웹 사이트 구성 파일입니다.

- WebService. .vstemplate

     웹 사이트 솔루션의 콘텐츠를 확인 하 고 App_Data 및 App_Code 폴더를 강제로 만들도록 하는 템플릿 파일입니다. 서비스입니다. *확장* 파일이 App_Code 폴더에 복사 됩니다.

- WebService. webproj

     이 파일은 프로젝트 템플릿 시스템의 아티팩트입니다. 웹 서비스는 웹 서비스 .vstemplate 파일의 프로젝트 파일 참조를 충족 합니다.

## <a name="project-item-template-folder"></a>프로젝트 항목 템플릿 폴더
 웹 프로젝트 항목 템플릿은 일반적으로 [*Visual Studio 설치 경로*] \Common7\IDE\ItemTemplates\Web에 설치 되며 \\ , 각각은 웹 프로그래밍 언어를 따라 이름이 지정 된 하위 폴더에 있습니다.

## <a name="project-item-templates"></a>프로젝트 항목 템플릿
 웹 사이트 프로젝트 항목 템플릿은 **기존 항목 추가** 명령에 대 한 응답으로 웹 사이트에 새 웹 페이지를 추가 하는 데 사용 됩니다. 이러한 종류의 웹 페이지는 현재 지원 됩니다.

- 새 클래스

- 새 HTML 페이지

- 새 웹 폼

- 새 마스터 페이지

### <a name="new-class"></a>새 클래스
 이 템플릿은 **새 클래스 추가** 명령에 대 한 응답으로 빈 클래스를 정의 하는 새 소스 파일을 만듭니다.

- 클래스입니다. *확장*

     빈 클래스를 구현 하는 소스 파일입니다. Codebehind 언어는이 파일의 *확장명* 을 결정 합니다.

- 클래스 .vstemplate

     소스 파일을 만들고 해당 내용을 확인 하는 템플릿 파일입니다.

### <a name="new-html-page"></a>새 HTML 페이지
 이 템플릿은 **새 HTML 페이지 추가** 명령에 대 한 응답으로 새 웹 페이지를 만듭니다.

- HTMLPage.htm

     웹 페이지의 시작 콘텐츠입니다. 이 웹 페이지에는 일반적으로 연결 된 codebehind 종속 파일이 없습니다. 연결 된 codebehind 파일이 있는 스마트 페이지를 만들려면 대신 Web Form 템플릿을 사용 합니다.

- HTMLPage

     웹 페이지를 만들고 해당 내용을 확인 하는 템플릿 파일입니다.

### <a name="new-webform"></a>새 WebForm
 이 템플릿은 **새 Web Form 추가** 명령에 대 한 응답으로 새 스마트 웹 페이지를 만듭니다.

 종속 된 코드 숨김 소스 파일을 만들려면 **별도의 파일에 코드 삽입**을 선택 합니다. 그렇지 않으면 빈 스크립팅 블록을 포함 하는 단일 웹 페이지가 만들어지고 \<% Page %> 종속 파일을 후크 하는 지시문이 없습니다.

 선택한 마스터 페이지에 대 한 콘텐츠 페이지를 만들려면 **마스터 페이지 선택**을 선택 합니다.

- WebForm

     웹 페이지의 시작 콘텐츠입니다. 이 웹 페이지에 연결 된 codebehind 종속 파일이 없습니다.

- WebForm_cb .aspx

     웹 페이지의 시작 콘텐츠입니다. 이 웹 페이지에는 연결 된 codebehind 종속 파일이 있습니다.

- 숨김은. *확장*

     Webform 클래스를 구현 하는 종속 파일입니다. Codebehind 언어는이 파일의 *확장명* 을 결정 합니다.

- ContentPage .aspx

     콘텐츠 페이지로 서의 웹 페이지 시작 콘텐츠입니다. 이 웹 페이지에 연결 된 codebehind 종속 파일이 없습니다.

- ContentPage_cb .aspx

     콘텐츠 페이지로 서의 웹 페이지 시작 콘텐츠입니다. 이 웹 페이지에는 연결 된 codebehind 종속 파일이 있습니다.

- WebForm

     새 웹 페이지의 내용과 종속 파일 (있는 경우)을 결정 하는 템플릿 파일입니다.

### <a name="new-master-page"></a>새 마스터 페이지
 이 템플릿은 **새 마스터 페이지 추가** 명령에 대 한 응답으로 새 마스터 페이지를 만듭니다.

 종속 된 코드 숨김 소스 파일을 만들려면 **별도의 파일에 코드 삽입**을 선택 합니다. 그렇지 않으면 빈 스크립팅 블록을 포함 하는 단일 웹 페이지가 만들어지고 \<% Page %> 종속 파일을 후크 하는 지시문이 없습니다.

- MasterPage 마스터

     마스터 페이지의 시작 콘텐츠입니다. 이 마스터 페이지에 연결 된 codebehind 종속 파일이 없습니다.

- MasterPage_cb 마스터

     마스터 페이지의 시작 콘텐츠입니다. 이 마스터 페이지에는 연결 된 codebehind 종속 파일이 있습니다.

- 숨김은. *확장*

     마스터 페이지 클래스를 구현 하는 종속 파일입니다. Codebehind 언어는이 파일의 *확장명* 을 결정 합니다.

- MasterPage .vstemplate

     새 마스터 페이지의 내용과 종속 파일 (있는 경우)을 결정 하는 템플릿 파일입니다.

## <a name="see-also"></a>추가 정보
- [웹 사이트 지원](../../extensibility/internals/web-site-support.md)
