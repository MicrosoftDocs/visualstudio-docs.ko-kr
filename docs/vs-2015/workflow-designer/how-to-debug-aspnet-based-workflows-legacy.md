---
title: '방법: ASP.NET 기반 워크플로 디버깅 (레거시) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- ASP.NET, debugging workflows
- debugging workflows, ASP.NET workflows
- ASP.NET workflows, debugging
- debugging, ASP.NET workflows
ms.assetid: 79b21edc-9e7d-410d-af68-09c1598b9c30
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f3bed38f5229cb489f663878759517480b48302c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668662"
---
# <a name="how-to-debug-aspnet-based-workflows-legacy"></a>방법: ASP.NET 기반 워크플로 디버깅(레거시)
이 항목에서는 레거시 [!INCLUDE[vstecasp](../includes/vstecasp-md.md)]에서 [!INCLUDE[wf](../includes/wf-md.md)] 또는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)]를 대상으로 하는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)] 기반의 [!INCLUDE[wfd1](../includes/wfd1-md.md)] 애플리케이션을 디버깅하는 방법에 대해 설명합니다.

 ASP.NET에서 시작된 레거시 워크플로나 웹 서비스로 게시된 레거시 워크플로를 워크플로가 호스트되는 프로세스에 연결하여 디버깅할 수 있습니다.

### <a name="to-debug-an-aspnet-based-workflow"></a>ASP.NET 기반 워크플로를 디버깅하려면

1. web.config 파일에서 **debug = true** 를 설정 하 여 ASP.NET 응용 프로그램에 대 한 디버깅을 사용 하도록 설정 합니다.

2. 워크플로 라이브러리를 시작 프로젝트로 설정하고 워크플로에 중단점을 설정합니다.

3. 워크플로 프로젝트 속성 **디버그** 옵션 **외부 url이 있는 브라우저 시작** 텍스트 상자에 기본 웹 페이지의 URL을 입력 합니다.

4. **디버그** 메뉴에서 **프로세스에 연결을** 선택 합니다.

5. **사용 가능한 프로세스** 목록에서 연결할 프로세스를 선택 합니다.

     워크플로가 호스트되는 프로세스인 w3wp.exe, webdev.webserver 또는 aspnet_wp에 연결합니다.

6. **연결 대상** 입력란 옆의 **선택** 을 클릭 합니다.

     **코드 형식 선택** 대화 상자가 나타납니다.

7. **다음 코드 형식 디버깅** 을 선택 하 고 **워크플로**를 선택 합니다.

8. **확인**을 클릭합니다.

9. **연결**을 클릭합니다.

10. 브라우저에서 기본 웹 페이지를 열고 워크플로를 시작합니다.

## <a name="see-also"></a>관련 항목
 [Windows Workflow Foundation에 대 한 Visual Studio 디버거 호출 (레거시)](../workflow-designer/invoking-the-visual-studio-debugger-for-windows-workflow-foundation-legacy.md) [방법: 워크플로에 중단점 설정 (레거시)](../workflow-designer/how-to-set-breakpoints-in-workflows-legacy.md) [레거시 워크플로 디버깅](../workflow-designer/debugging-legacy-workflows.md)