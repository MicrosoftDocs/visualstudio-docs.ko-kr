---
title: 서비스 Essentials | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- services, essentials
ms.assetid: fbe84ad9-efe1-48b1-aba3-b50b90424d47
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 407dda2f203b7be20b19c0e296caa9ce1c95b32c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696075"
---
# <a name="service-essentials"></a>서비스 필수 항목
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

서비스는 두 Vspackage 사이의 계약입니다. 하나의 VSPackage는 다른 VSPackage에서 사용할 특정 인터페이스 집합을 제공 합니다. [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 자체는 다른 Vspackage에 서비스를 제공 하는 Vspackage의 컬렉션입니다.  
  
 예를 들어, SVsActivityLog 서비스를 사용 하 여 활동 로그에 쓰는 데 사용할 수 있는 IVsActivityLog 인터페이스를 가져올 수 있습니다. 자세한 내용은 [방법: 활동 로그 사용](../../extensibility/how-to-use-the-activity-log.md)을 참조 하세요.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 또한는 등록 되지 않은 몇 가지 기본 제공 서비스도 제공 합니다. Vspackage는 서비스 재정의를 제공 하 여 기본 제공 또는 다른 서비스를 대체할 수 있습니다. 서비스에 대 한 서비스 재정의는 하나만 허용 됩니다.  
  
 서비스는 검색할 수 없습니다. 따라서 사용 하려는 서비스의 SID (서비스 식별자)를 알아야 하며, 제공 하는 인터페이스를 알고 있어야 합니다. 서비스에 대 한 참조 설명서에서는이 정보를 제공 합니다.  
  
- 서비스를 제공 하는 Vspackage를 서비스 공급자 라고 합니다.  
  
- 다른 Vspackage에 제공 되는 서비스를 글로벌 서비스 라고 합니다.  
  
- 이러한 서비스를 구현 하는 VSPackage 사용할 수 있는 서비스 또는 만든 개체에만 사용할 수 있는 서비스를 로컬 서비스 라고 합니다.  
  
- 다른 패키지에서 제공 하는 기본 제공 서비스 또는 서비스를 대체 하는 서비스를 서비스 재정의 라고 합니다.  
  
- 서비스 또는 서비스 재정의는 요구에 따라 로드 됩니다. 즉, 서비스 공급자가 제공 하는 서비스가 다른 VSPackage에 의해 요청 될 때 로드 됩니다.  
  
- 요청 시 로드를 지원 하기 위해 서비스 공급자는에 전역 서비스를 등록 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 합니다. 자세한 내용은 [서비스 등록](../../misc/registering-services.md)을 참조 하세요.  
  
- 서비스를 구한 후에는 [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) (비관리 코드) 또는 캐스트 (관리 코드)를 사용 하 여 원하는 인터페이스를 가져옵니다. 예를 들면 다음과 같습니다.  
  
    ```vb  
    TryCast(GetService(GetType(SVsActivityLog)), IVsActivityLog)  
    ```  
  
    ```csharp  
    GetService(typeof(SVsActivityLog)) as IVsActivityLog;  
  
    ```  
  
- 관리 코드는 해당 형식으로 서비스를 참조 하지만 비관리 코드는 해당 GUID로 서비스를 참조 합니다.  
  
- 에서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] VSPackage를 로드할 때 서비스 공급자를 VSPackage에 전달 하 여 글로벌 서비스에 대 한 VSPackage 액세스를 제공 합니다. 이를 VSPackage의 "사이 팅" 이라고 합니다.  
  
- Vspackage은 자신이 만드는 개체의 서비스 공급자 일 수 있습니다. 예를 들어, 폼은 색 서비스에 대 한 요청을 해당 프레임으로 보내 요청을에 전달할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
- 깊게 중첩 되거나 전혀 배치 되지 않는 관리 되는 개체는 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 전역 서비스에 대 한 직접 액세스를 호출할 수 있습니다. 자세한 내용은 [방법: GetGlobalService 사용](../../misc/how-to-use-getglobalservice.md)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [사용 가능한 서비스 목록](../../extensibility/internals/list-of-available-services.md)   
 [서비스 사용 및 제공](../../extensibility/using-and-providing-services.md)   
 [캐스팅 및 형식 변환](https://msdn.microsoft.com/library/568df58a-d292-4b55-93ba-601578722878)   
 [캐스팅](https://msdn.microsoft.com/library/3dbeb06e-2f4b-4693-832d-624bc8ec95de)
