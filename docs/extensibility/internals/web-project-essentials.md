---
title: 웹 프로젝트 필수 사항 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- web projects, essentials
ms.assetid: ca2f4e43-322c-4431-8680-52da846940bc
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 09e33248ca264fefa79a8d5d5fa5d0cfa3d2da1d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703544"
---
# <a name="web-project-essentials"></a>웹 프로젝트 필수 항목
웹 프로젝트는 웹 응용 프로그램을 만듭니다. 웹 프로젝트를 사용하여 스마트 웹 페이지가 있는 웹 응용 프로그램을 만들 수 있습니다. 스마트 웹 페이지에는 필요에 따라 웹 페이지를 렌더링하는 서버 쪽 코드가 있습니다.

 또는 와 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]같은 기존 프로그래밍 언어를 사용하여 스마트 웹 페이지를 만들어 사용자로부터 정보를 수집 및 처리하고 데이터베이스에 저장하는 등의 방법으로 정보를 수집 및 처리할 수 있습니다.

- 코드 숨김 모델은 종속 소스 코드 파일을 파일 확장명 .aspx 또는 .asmx가 있는 웹 페이지와 연결합니다. 예를 들어 hello.aspx에는 종속 소스 코드 파일 hello.aspx.cs 있을 수 있습니다.

- 스마트 웹 페이지와 연결된 서버 쪽 코드는 웹 사이트 /bin 폴더에 있는 실행 파일로 컴파일됩니다.

- 특정 웹 페이지와 연결되지 않은 도우미 클래스와 같은 추가 소스 코드 파일은 웹 사이트 /App_Code 폴더에 있습니다.

  - WSP(웹 사이트 프로젝트)는 각 스마트 웹 페이지에 대해 하나의 실행 파일을 생성합니다. 추가 실행 파일은 /App_Code 폴더의 모든 소스 코드 파일에서 생성됩니다.

  - WAP(웹 응용 프로그램 프로젝트)는 모든 스마트 웹 페이지의 코드와 /App_Code 폴더의 모든 소스 파일을 결합하는 단일 실행 파일을 생성합니다.

- 웹 프로젝트의 솔루션 파일은 웹 사이트 자체와 별도로 있습니다. 기본적으로 솔루션 파일은 \문서 및\\설정*YourAccount*\\\My Documents*\<비주얼 스튜디오 ####>* \Project\\*YourWebSite*에 있습니다.

  > [!NOTE]
  > 웹 사이트와 함께 솔루션 파일을 유지하려면 솔루션 파일을 이동한 다음 다시 열기만 하면 됩니다.

- Visual Studio에 솔루션 파일이 없는 웹 사이트를 열면 새 솔루션 파일이 자동으로 생성됩니다.

- 웹 프로젝트에는 프로젝트 파일이 없습니다. 프로젝트 정보는 솔루션 파일, web.config 파일 및 다른 곳에 저장됩니다.

- 웹 프로젝트에 전역 속성을 추가하면 웹 프로젝트 솔루션 폴더에 저장소 파일이 자동으로 생성됩니다.

- 스마트 웹 페이지는 Page 지시문 또는 \<스크립트 runat="server"> 태그를 사용하여 서버 측 프로그래밍 언어와 연결할 수 있습니다.

- 또한 웹 페이지에는 모든 스크립팅 언어로 작성된 클라이언트 쪽 스크립팅 블록이 여러 개있을 수 있습니다.

- 웹 사이트 프로젝트 시스템은 프로젝트 및 항목 템플릿을 추가하고 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] 프로젝트에 등록하여 구현됩니다.

- WAP 시스템은 프로젝트 풍미라고도 하는 프로젝트 하위 유형으로 구현됩니다. 이 [!INCLUDE[vwprvw](../../extensibility/internals/includes/vwprvw_md.md)] 프로젝트는 WAP 하위 유형에 의해 맛을 내며 WAP 시스템을 만듭니다. 프로젝트 하위 유형에 대한 자세한 내용은 [프로젝트 하위 유형을](../../extensibility/internals/project-subtypes.md)참조하십시오.

- 스마트 웹 페이지는 HTML과 서버 측 프로그래밍 언어를 결합합니다. 서버 쪽 언어를 포함된 언어라고 합니다. 포함된 언어를 지원하려면 웹 프로젝트 시스템에서 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsContainedLanguage> 인터페이스 패밀리를 구현해야 합니다.

  - 편집기에서 포함된 언어를 지원하려면 HTML 언어 서비스가 포함된 언어 코드를 포함된 언어 서비스에 표시하는 것을 연기해야 합니다.

  - 오류 마커(빨간색 squigglies)는 항상 코드 편집기의 기본 버퍼에 만들어야 합니다.

## <a name="see-also"></a>참조
- [웹 프로젝트](../../extensibility/internals/web-projects.md)
