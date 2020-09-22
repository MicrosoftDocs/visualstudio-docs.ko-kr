---
title: ClickOnce 응용 프로그램에 대 한 코드 액세스 보안 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
f1_keywords:
- vb.XBAPProjectPropertiesSecurity.HowTo
- vb.XBAProjectPropertiesSecurity.HowTo
- vb.ProjectPropertiesSecurity.HowTo
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], security
- ClickOnce applications, caspol
- security [ClickOnce], WPF browser-hosted applications
- security [ClickOnce], ClickOnce applications
- ClickOnce applications, code access security policies
- security, ClickOnce
ms.assetid: 04b104d0-0bd3-4ccb-b164-1de92d234487
caps.latest.revision: 33
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 54160bbdfe834a1b3226f4445b862c151bcf35c3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841410"
---
# <a name="code-access-security-for-clickonce-applications"></a>ClickOnce 애플리케이션의 코드 액세스 보안
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ClickOnce 애플리케이션은 .NET Framework를 기반으로 하며 코드 액세스 보안 제약 조건의 적용을 받습니다. 따라서 코드 액세스 보안의 의미를 이해하여 ClickOnce 애플리케이션을 적절하게 작성해야 합니다.  
  
 코드 액세스 보안은 보호된 리소스와 작업에 대한 코드의 액세스를 제한하는 .NET Framework의 메커니즘입니다. 애플리케이션 설치 관리자의 위치에 적합한 영역을 사용하도록 ClickOnce 애플리케이션에 대한 코드 액세스 보안 권한을 구성해야 합니다. 대부분의 경우 제한된 사용 권한 집합을 위한 **인터넷** 영역 또는 보다 큰 사용 권한 집합을 위한 **로컬 인트라넷** 영역을 선택할 수 있습니다.  
  
## <a name="default-clickonce-code-access-security"></a>기본 ClickOnce 코드 액세스 보안  
 기본적으로 ClickOnce 애플리케이션은 클라이언트 컴퓨터에서 설치되거나 실행될 때 완전 신뢰 권한을 받습니다.  
  
- 완전 신뢰 권한이 있는 애플리케이션은 파일 시스템 및 레지스트리와 같은 리소스에 무제한으로 액세스할 수 있습니다. 따라서 애플리케이션(및 최종 사용자 시스템)이 악성 코드에 의해 악용될 수 있습니다.  
  
- 애플리케이션에 완전 신뢰 권한이 필요한 경우 애플리케이션에 사용 권한을 부여하라는 메시지가 최종 사용자에게 표시될 수도 있습니다. 이는 애플리케이션에서 실제로 ClickOnce 환경을 제공하지 않고 경험이 적은 사용자에게 프롬프트가 혼동을 줄 수 있음을 의미합니다.  
  
  > [!NOTE]
  > CD-ROM과 같은 이동식 미디어에서 애플리케이션을 설치하는 경우 사용자에게 메시지가 표시되지 않습니다. 또한 신뢰할 수 있는 소스에서 애플리케이션을 설치하는 경우 사용자에게 메시지를 표시하지 않도록 네트워크 관리자가 네트워크 정책을 구성할 수 있습니다. 자세한 내용은 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)을 참조하십시오.  
  
  ClickOnce 애플리케이션의 사용 권한을 제한하기 위해 애플리케이션에 필요한 사용 권한에 가장 맞는 영역을 애플리케이션이 요청하도록 코드 액세스 보안 권한을 수정할 수 있습니다. 대부분의 경우 애플리케이션이 배포되는 영역을 선택할 수 있습니다. 예를 들어 애플리케이션이 엔터프라이즈 애플리케이션인 경우 **로컬 인트라넷** 영역을 사용할 수 있습니다. 애플리케이션이 인터넷 애플리케이션인 경우 **인터넷** 영역을 사용할 수 있습니다.  
  
## <a name="configuring-security-permissions"></a>보안 권한 구성  
 코드 액세스 보안 권한을 제한하기 위해 항상 적절한 영역을 요청하도록 ClickOnce 애플리케이션을 구성해야 합니다. **프로젝트 디자이너** 의 **보안**페이지에서 보안 권한을 구성할 수 있습니다.  
  
 **프로젝트 디자이너** 의 **보안** 페이지에는 **ClickOnce 보안 설정 사용** 확인란이 포함되어 있습니다. 이 확인란을 선택하면 보안 권한 요청이 애플리케이션에 대한 배포 매니페스트에 추가됩니다. 설치 시 요청된 사용 권한이 애플리케이션이 배포된 영역에 대한 기본 사용 권한을 초과할 경우 권한을 부여하라는 메시지가 사용자에게 표시됩니다. 자세한 내용은 [How to: Enable ClickOnce Security Settings](../deployment/how-to-enable-clickonce-security-settings.md)을 참조하세요.  
  
 서로 다른 위치에서 배포된 애플리케이션에는 메시지 표시 없이 다른 수준의 사용 권한이 부여됩니다. 예를 들어 애플리케이션이 인터넷에서 배포된 경우 매우 제한적인 권한 집합을 받습니다. 로컬 인트라넷에서 설치하는 경우 더 많은 권한이 부여되고, CD-ROM에서 설치하는 경우 완전 신뢰 권한이 부여됩니다.  
  
 사용 권한 구성의 시작점으로, **보안** 페이지의 **영역** 목록에서 보안 영역을 선택할 수 있습니다. 애플리케이션이 둘 이상의 영역에서 배포되는 경우 최소한의 권한을 가진 영역을 선택합니다. 자세한 내용은 [How to: Set a Security Zone for a ClickOnce Application](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)을 참조하십시오.  
  
 설정할 수 있는 속성은 사용 권한 집합에 따라 달라집니다. 일부 사용 권한 집합에는 구성 가능한 속성이 없습니다. 애플리케이션이 요청할 수 있는 사용 권한의 전체 목록에 대한 자세한 내용은 <xref:System.Security.Permissions>를 참조하세요. 사용자 지정 영역에 대해 권한을 설정하는 방법에 대한 자세한 내용은 [How to: Set Custom Permissions for a ClickOnce Application](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)을 참조하세요.  
  
## <a name="debugging-an-application-that-has-restricted-permissions"></a>사용 권한이 제한된 애플리케이션 디버그  
 개발자는 대개 완전 신뢰 권한으로 개발 컴퓨터를 실행합니다. 따라서 사용자가 제한된 권한으로 실행할 때 표시될 수 있는 애플리케이션을 디버그하는 경우 동일한 보안 예외가 표시되지 않습니다.  
  
 이러한 예외를 catch하려면 최종 사용자와 동일한 사용 권한으로 애플리케이션을 디버그해야 합니다. **프로젝트 디자이너** 의 **보안**페이지에서 제한된 권한으로 디버그를 사용하도록 설정할 수 있습니다.  
  
 제한된 권한으로 애플리케이션을 디버그하는 경우 **보안** 페이지에서 사용하도록 설정되지 않은 모든 코드 보안 요청에 대해 예외가 발생합니다. 예외를 방지하기 위해 코드를 수정하는 방법에 대한 제안을 제공하는 예외 도우미가 나타납니다.  
  
 또한 코드를 작성할 때 코드 편집기의 IntelliSense 기능은 구성한 보안 권한에 포함되지 않은 모든 멤버를 사용하지 않도록 설정합니다.  
  
 자세한 내용은 [How to: Debug a ClickOnce Application with Restricted Permissions](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)을 참조하세요.  
  
## <a name="security-permissions-for-browser-hosted-applications"></a>브라우저에서 호스트되는 애플리케이션의 보안 권한  
 Visual Studio에서는 WPF(Windows Presentation Foundation) 애플리케이션에 대해 다음 프로젝트 형식을 제공합니다.  
  
- WPF Windows 애플리케이션  
  
- WPF 웹 브라우저 애플리케이션  
  
- WPF 사용자 지정 컨트롤 라이브러리  
  
- WPF 서비스 라이브러리  
  
  이러한 프로젝트 형식 중에서 WPF 웹 브라우저 애플리케이션만 웹 브라우저에서 호스트되므로 특별한 배포 및 보안 설정이 필요합니다. 이러한 애플리케이션에 대한 기본 보안 설정은 다음과 같습니다.  
  
- **ClickOnce 보안 설정 사용**  
  
- **부분 신뢰 애플리케이션**  
  
- **인터넷 영역** (WPF 웹 브라우저 애플리케이션에 대한 기본 사용 권한 집합이 선택됨)  
  
  **고급 보안 설정** 대화 상자에서 **선택한 권한 집합으로 이 애플리케이션 디버깅** 확인란이 선택되고 사용할 수 없습니다. 이는 브라우저에서 호스트되는 애플리케이션에 대해 영역에서 디버그를 해제할 수 없기 때문입니다.  
  
## <a name="see-also"></a>참고 항목  
 [ClickOnce 응용 프로그램 보안](../deployment/securing-clickonce-applications.md)   
 [방법: ClickOnce 보안 설정 사용](../deployment/how-to-enable-clickonce-security-settings.md)   
 [방법: ClickOnce 응용 프로그램의 보안 영역 설정](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [방법: ClickOnce 응용 프로그램에 대 한 사용자 지정 권한 설정](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [방법: 제한 된 권한으로 ClickOnce 응용 프로그램 디버깅](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [신뢰할 수 있는 응용 프로그램 배포 개요](../deployment/trusted-application-deployment-overview.md)   
 [프로젝트 디자이너, 보안 페이지](../ide/reference/security-page-project-designer.md)
