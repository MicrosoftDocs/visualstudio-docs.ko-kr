---
title: Visual Studio SDK | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
caps.latest.revision: 57
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 27dce16d9fe02063eae935af96c26184285e583d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850375"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual studio SDK를 사용 하 여 visual Studio 기능을 확장 하거나 새 기능을 Visual Studio에 통합할 수 있습니다. Visual Studio 갤러리 뿐만 아니라 다른 사용자에 게 확장을 배포할 수 있습니다. 다음은 Visual Studio를 확장할 수 있는 몇 가지 방법입니다.  
  
- IDE에 명령, 단추, 메뉴 및 기타 UI 요소를 추가 합니다.  
  
- 새 기능에 대 한 도구 창 추가  
  
- 지정 된 언어에 대해 IntelliSense를 확장 하거나 새 프로그래밍 언어에 IntelliSense를 제공 합니다.  
  
- Light 전구를 사용 하 여 개발자가 더 나은 코드를 작성 하는 데 도움이 되는 힌트 및 제안 제공  
  
- 새 언어에 대 한 지원 사용  
  
- 사용자 지정 프로젝트 형식 추가  
  
- Visual Studio Marketplace을 통해 수백만 명의 개발자에 게 접근  
  
  이전에 Visual Studio 확장을 작성 한 적이 없는 경우 이러한 기능에 대 한 자세한 내용과 [Visual Studio 확장 개발을 시작](../extensibility/starting-to-develop-visual-studio-extensions.md)해야 합니다.  
  
## <a name="installing-the-visual-studio-sdk"></a>Visual Studio SDK 설치  
 Visual Studio 2015 부터는 다운로드 센터에서 Visual Studio SDK를 설치 하지 않습니다. Visual Studio 설치 프로그램에서 선택적 기능으로 포함 됩니다. VS SDK는 나중에 설치할 수도 있습니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.  
  
## <a name="whats-new-in-the-visual-studio-2015-sdk"></a>Visual Studio 2015 SDK의 새로운 기능  
 Visual Studio SDK에는 VSIX 패키지를 사용 하 여 메뉴 명령, 도구 창 및 편집기 확장을 만들 수 있는 가벼운 전구 및 새 프로젝트 항목을 비롯 한 몇 가지 새로운 기능이 있습니다. 자세한 내용은 [Visual Studio 2015 SDK의 새로운 기능](../extensibility/what-s-new-in-the-visual-studio-2015-sdk.md)을 참조 하세요.  
  
## <a name="visual-studio-user-experience-guidelines"></a>Visual Studio 사용자 환경 지침  
 [Visual Studio 사용자 환경 지침](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)에서 확장에 대 한 UI를 디자인 하는 데 유용한 팁을 확인 하세요.  
  
 또한 높은 DPI 장치에서 확장을 표시 하는 방법에 대 한 자세한 내용은 [Dpi 문제 해결](../extensibility/addressing-dpi-issues2.md) 항목을 참조 하세요.  
  
 [이미지 서비스와 카탈로그](../extensibility/image-service-and-catalog.md) 를 활용 하 여 뛰어난 이미지 관리 및 높은 DPI 및 테마에 대 한 지원을 받을 수 있습니다.  
  
## <a name="finding-and-installing-existing-visual-studio-extensions"></a>기존 Visual Studio 확장 찾기 및 설치  
 **도구** 메뉴의 **확장 및 업데이트** 대화 상자에서 Visual Studio 확장을 찾을 수 있습니다. 자세한 내용은 [Visual Studio 확장 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)을 참조 하세요. [Visual Studio Marketplace](https://marketplace.visualstudio.com/) 에서 확장을 찾을 수도 있습니다.  
  
## <a name="visual-studio-sdk-reference"></a>Visual Studio SDK 참조  
 Visual studio sdk [참조](../extensibility/visual-studio-sdk-reference.md)에서 VISUAL STUDIO sdk API 참조를 찾을 수 있습니다.  
  
## <a name="visual-studio-sdk-samples"></a>Visual Studio SDK 샘플  
 [Visual Studio 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples)에서 GITHUB의 VS SDK 확장의 오픈 소스 예제를 찾을 수 있습니다. 이 GitHub 리포지토리에는 Visual Studio의 다양 한 확장 가능 기능을 보여 주는 샘플이 포함 되어 있습니다.  
  
## <a name="other-visual-studio-sdk-resources"></a>다른 Visual Studio SDK 리소스  
 이상 사용자에 대 한 질문이 있거나 확장을 개발 하는 환경을 공유 하려면 [Visual Studio 확장성 포럼](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) 또는 [ExtendVS 그룹 채팅](https://gitter.im/Microsoft/extendvs)을 사용할 수 있습니다.  
  
 [VSX Arcana 블로그](https://blogs.msdn.microsoft.com/vsx/) 및 Microsoft mvp가 작성 한 블로그에서 추가 정보를 찾을 수 있습니다.  
  
- [즐겨 찾는 Visual Studio 확장](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)  
  
- [Visual Studio 확장성](http://www.visualstudioextensibility.com/overview/vs/)  
  
- [Visual Studio 확장](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)  
  
## <a name="see-also"></a>관련 항목  
 [메뉴 명령을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)   
 [방법: 확장성 프로젝트를 Visual Studio 2015로 마이그레이션](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md)   
 [FAQ: 추가 기능을 VSPackage 확장으로 변환](../extensibility/faq-converting-add-ins-to-vspackage-extensions.md)   
 [관리 코드에서 여러 스레드 관리](../extensibility/managing-multiple-threads-in-managed-code.md)   
 [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)   
 [도구 모음에 명령 추가](../extensibility/adding-commands-to-toolbars.md)   
 [도구 창 확장 및 사용자 지정](../extensibility/extending-and-customizing-tool-windows.md)   
 [편집기 및 언어 서비스 확장](../extensibility/editor-and-language-service-extensions.md)   
 [프로젝트 확장](../extensibility/extending-projects.md)   
 [사용자 설정 및 옵션 확장](../extensibility/extending-user-settings-and-options.md)   
 [사용자 지정 프로젝트 및 항목 템플릿 만들기](../extensibility/creating-custom-project-and-item-templates.md)   
 [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)   
 [Visual Studio의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)   
 [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)   
 [연결된 서비스 확장](../extensibility/extending-connected-services.md)   
 [Vspackage 관리](../extensibility/managing-vspackages.md)   
 [Visual Studio 격리 셸](../extensibility/visual-studio-isolated-shell.md)   
 [Visual Studio 확장 출시](../extensibility/shipping-visual-studio-extensions.md)   
 [Visual Studio SDK 내부](../extensibility/internals/inside-the-visual-studio-sdk.md)   
 [Visual Studio SDK에 대 한 지원](../extensibility/support-for-the-visual-studio-sdk.md)   
 [보관](../extensibility/archive.md)   
 [Visual Studio SDK 참조](../extensibility/visual-studio-sdk-reference.md)
