---
title: 서비스 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, registering
ms.assetid: c4ebac40-0374-4dda-948e-06fdda0e9c81
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: 64f2afa6e853978e919e466f91475bed1e8d698c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62971292"
---
# <a name="registering-services"></a>서비스 등록
요청 시 로드를 지원하려면 서비스 공급자가 글로벌 서비스를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에 등록해야 합니다.  
  
 개발 중에 관리되는 서비스 공급자는 패키지에 대한 소스 코드에 특성을 추가한 다음 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] IDE에서 패키지를 빌드하여 서비스 및 서비스 재정의를 등록합니다. 이렇게 하면 결과 어셈블리에서 RegPkg.exe 유틸리티가 실행되어 패키지를 등록하고 배포 준비를 합니다. 자세한 내용은 [방법: 서비스 등록](../misc/how-to-register-a-service.md)을 참조 하세요.  
  
 관리되지 않는 서비스 공급자는 시스템 레지스트리의 서비스 섹션 또는 서비스 재정의 섹션에서 제공하는 서비스를 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에 등록해야 합니다. 다음 .reg 파일 조각은 SVsTextManager 서비스를 등록하는 방법을 보여 줍니다.  
  
```  
[HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio\<version number>\Services\{F5E7E71D-1401-11d1-883B-0000F87579D2}]  
@="{F5E7E720-1401-11d1-883B-0000F87579D2}"  
"Name"="SVsTextManager"  
```  
  
 위 예제에서 버전 번호는 7.1 또는 8.0과 같은 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]버전이고, {F5E7E71D-1401-11d1-883B-0000F87579D2} 키는 SVsTextManager 서비스의 SID(서비스 ID)이고, 기본값 {F5E7E720-1401-11d1-883B-0000F87579D2}는 서비스를 제공하는 텍스트 관리자 VSPackage의 패키지 GUID입니다.  
  
## <a name="remote-services-and-background-threads"></a>원격 서비스 및 백그라운드 스레드  
 제공하는 서비스는 원격으로 또는 백그라운드 스레드에서 자동으로 사용할 수 없습니다. 사용할 수 있게 하려면 형식 라이브러리를 빌드하고 등록해야 합니다.  
  
 VSL(Visual Studio 라이브러리)을 사용하는 비관리 코드에서 다음과 같은 방법으로 형식 라이브러리를 등록할 수 있습니다.  
  
```  
#define VSL_REGISTER_TYPE_LIB TRUE  
#include <VSLPackageDllEntryPoints.cpp>  
```  
  
 관리 코드에서 다음과 같이 빌드 후 단계를 추가할 수 있습니다.  
  
```  
regasm /tlb MyAssembly.dll  
```  
  
## <a name="see-also"></a>관련 항목  
 [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)   
 [서비스 필수 항목](../extensibility/internals/service-essentials.md)