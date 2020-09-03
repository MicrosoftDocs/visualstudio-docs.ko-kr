---
title: Shell (격리 또는 통합) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio shell
- Visual Studio, Shell
- Shell [Visual Studio]
- Visual Studio shell, shell-based applications
- Shell [Visual Studio], shell-based applications
ms.assetid: c64a9bf0-9bf8-45c3-8fa2-306fa6cab66a
caps.latest.revision: 26
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa346ebfe321e4672ea3fa71a4dcc872ebf22cda
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850228"
---
# <a name="shell-isolated-or-integrated"></a>셸(격리 또는 통합)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

통합 모드나 격리 모드에서 Visual Studio 기반 응용 프로그램을 직접 만들 수 있습니다. 통합 모드에서는 응용 프로그램 외에도 많은 Visual Studio 기능을 사용할 수 있습니다. 격리 모드에서는 사용자 고유의 확장과 함께 배포 하려는 Visual Studio 기능의 하위 집합을 선택 합니다.  
  
## <a name="integrated-mode"></a>통합 모드  
 통합 모드를 사용 하면 사용자가 표준 Visual Studio 기능을 사용자 지정 도구와 함께 사용할 수 있습니다. 통합 셸은 주로 프로그래밍 언어 및 소프트웨어 개발 도구를 호스팅하기 위한 것입니다.  
  
 통합 셸에서 빌드된 사용자 지정 도구는 동일한 컴퓨터에 설치 된 다른 모든 버전의 Visual Studio와 자동으로 병합 됩니다. Visual Studio가 아직 설치 되지 않은 경우 재배포 가능 버전의 Visual Studio 통합 셸을 제공할 수 있습니다.  
  
 재배포 가능 버전의 Visual Studio 통합 셸에는 해당 프로젝트 시스템을 지 원하는 프로그래밍 언어 및 기능이 포함 되어 있지 않습니다.  
  
> [!NOTE]
> Visual Studio shell 통합 모드는 Express edition을 제외한 모든 버전의 Visual Studio와 함께 설치할 수 있습니다.  
  
 자세한 내용은 [Visual Studio Shell (통합)](../extensibility/visual-studio-shell-integrated.md)을 참조 하세요.  
  
## <a name="isolated-mode"></a>격리 모드  
 격리 모드를 사용 하면 다른 버전의 Visual Studio와 나란히 실행 되는 사용자 지정 도구를 만들 수 있습니다. 모든 표준 Visual Studio 기능에 의존 하지 않고 Visual Studio 서비스에 액세스할 수 있는 도구를 주로 사용 합니다. Visual Studio 격리 셸을 기반으로 하는 응용 프로그램의 모양을 사용자 지정할 수 있습니다. 응용 프로그램과 함께 표시 하지 않을 기능 및 메뉴 명령 그룹을 쉽게 해제할 수 있습니다.  
  
 자세한 내용은 [Visual Studio 격리 셸](../extensibility/visual-studio-isolated-shell.md)을 참조 하세요.  
  
## <a name="distributing-your-integrated-or-isolated-shell-application"></a>통합 또는 격리 셸 응용 프로그램 배포  
 통합 또는 격리 셸 응용 프로그램을 배포 하려면 응용 프로그램, 특수 한 통합 또는 격리 셸 재배포 가능 패키지 및 설치 프로그램을 포함 해야 합니다. 배포 및 설치에 대 한 자세한 내용은 [격리 된 셸 응용 프로그램 배포](../extensibility/distributing-isolated-shell-applications.md)를 참조 하세요.  
  
> [!IMPORTANT]
> Visual Studio 통합 및 격리 된 셸에 대 한 [EULA (최종 사용자 사용권 계약)](https://www.visualstudio.com/support/legal/mt171552) 에는 데이터 컬렉션에 대 한 섹션이 포함 되어 있습니다 (**섹션 3). 데이터**).  응용 프로그램에 빌드하는 통합 또는 격리 된 셸 소프트웨어의 사용자가 Microsoft에서 수집할 수 있는 고객 사용 데이터에 대해 설명 합니다. 자세한 내용은 [Microsoft Visual Studio 제품군 개인 정보 취급 방침](https://www.visualstudio.com/dn948229)을 참조 하세요.  
> 
> 응용 프로그램을 통해 고객의 별도의 사용 현황 데이터를 수집 하는 경우 수집 하는 내용에 대 한 응용 프로그램 사용자에 게 적절 한 알림을 제공 해야 합니다.  Visual Studio 소프트웨어 개발 키트 라이선스에 따라 격리 되었거나 통합 된 셸 소프트웨어를 응용 프로그램의 일부로 배포 하는 경우 다음 중 하나를 포함 해야 합니다.  
> 
> - 응용 프로그램 라이선스의 일부로 최종 사용자 사용권 계약  
> - 고객이 셸 소프트웨어에 대 한 Microsoft 최종 사용자 사용 조건 이상으로 Visual Studio 통합 또는 격리 셸을 보호 하는 약관에 동의 해야 하는 사용자의 EULA  
  
## <a name="additional-resources"></a>추가 리소스  
 재배포 가능 패키지에 대 한 자세한 내용은 [Visual Studio 확장성 다운로드](https://msdn.microsoft.com/vstudio/bb984878.aspx) 웹 사이트를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 확장 전달](../extensibility/shipping-visual-studio-extensions.md)
