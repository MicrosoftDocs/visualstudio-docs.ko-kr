---
title: 격리 된 셸 응용 프로그램 배포 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: c503a985-d67a-4ef8-9123-7744a78f2f17
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bf0d8a4cab8d30a56e84d1a6869c2c842b982aea
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204673"
---
# <a name="distributing-isolated-shell-applications"></a>격리 셸 애플리케이션 배포
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

격리 셸 응용 프로그램을 만들려면 Visual Studio와 Visual Studio SDK를 설치 해야 합니다. 다른 사용자 또는 고객의 컴퓨터에 응용 프로그램을 배포 하려면 격리 된 셸에 대 한 특수 재배포 가능 패키지를 포함 해야 합니다.  
  
## <a name="prerequisites-for-distributing-isolated-shell-applications"></a>격리 된 셸 응용 프로그램 배포를 위한 필수 구성 요소  
  
|Name|설명|  
|----------|-----------------|  
|Visual Studio SDK|의 확장을 개발 하 고 테스트 하는 데 필요한 SDK [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 입니다. SDK를 사용 하 여 Visual Studio 격리 셸의 고유한 인스턴스를 만들 수도 있습니다.<br /><br /> Visual Studio는 SDK의 필수 구성 요소입니다.|  
|Microsoft Visual Studio 격리 된 셸 재배포 가능 패키지|Visual Studio 격리 셸에서 도구 환경을 빌드할 때 설치 프로그램에 포함 하는 재배포 가능 패키지입니다. 격리 셸 재배포 가능 패키지는 .NET Framework 4.5를 포함 합니다.|  
  
## <a name="creating-an-installation-program-for-the-application"></a>응용 프로그램에 대 한 설치 프로그램 만들기  
 통합 또는 격리 셸 응용 프로그램에 대 한 특수 설치 프로그램을 만들어야 합니다. 자세한 내용은 [격리 된 셸 응용 프로그램 설치](../extensibility/installing-an-isolated-shell-application.md)를 참조 하세요.  
  
## <a name="allowing-for-updates-to-your-application"></a>응용 프로그램에 대 한 업데이트 허용  
 Microsoft 업데이트 또는 회사의 업데이트를 통해 응용 프로그램이 업데이트 될 가능성을 설치 프로그램에서 허용 해야 합니다. 업데이트에 대 한 자세한 내용은 [격리 된 셸 응용 프로그램에 대 한 서비스 지침](../extensibility/servicing-guidelines-for-isolated-shell-applications.md)을 참조 하세요.
