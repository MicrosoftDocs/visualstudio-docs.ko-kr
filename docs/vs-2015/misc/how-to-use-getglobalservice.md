---
title: '방법: GetGlobalService 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- services, GetGlobalService
ms.assetid: 4cdf5ab5-9f09-4caf-9011-2dcb2c62f1b7
caps.latest.revision: 14
manager: jillfra
ms.openlocfilehash: 1c1fb48e4bb354ef403b39b0f1320ead92f43967
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62948184"
---
# <a name="how-to-use-getglobalservice"></a>방법: GetGlobalService 사용
다른 방법으로는 이동 하지 않은 도구 창이 나 제어 컨테이너에서 서비스를 가져와야 하거나, 원하는 서비스를 알지 못하는 서비스 공급자와 함께 서비스를 가져와야 하는 경우도 있습니다. 예를 들어, 컨트롤 내에서 활동 로그에 쓸 수 있습니다. 이러한 시나리오와 기타 시나리오에 대 한 자세한 내용은 [방법: 서비스 문제 해결](../extensibility/how-to-troubleshoot-services.md)을 참조 하세요.  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]정적 메서드를 호출 하 여 대부분의 서비스를 가져올 수 있습니다 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> .  
  
 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 는에서 파생 된 VSPackage가 처음으로 배치 될 때 초기화 되는 캐시 된 서비스 공급자에 의존 <xref:Microsoft.VisualStudio.Shell.Package> 합니다. 이 조건에 만족 하거나 null 서비스에 대해 준비 해야 합니다.  
  
 다행히는 <xref:Microsoft.VisualStudio.Shell.Package.GetGlobalService%2A> 대부분의 시간 동안 제대로 작동 합니다.  
  
- VSPackage가 다른 VSPackage만 알려진 서비스를 제공 하는 경우 서비스를 요청 하는 VSPackage는 서비스를 제공 하는 VSPackage가 로드 되기 전에 배치 됩니다.  
  
- 도구 창이 VSPackage에서 생성 되는 경우 도구 창이 만들어지기 전에 VSPackage가 배치 됩니다.  
  
- VSPackage에서 만든 도구 창에서 컨트롤 컨테이너를 호스팅하는 경우 컨트롤 컨테이너를 만들기 전에 VSPackage가 배치 됩니다.  
  
### <a name="to-get-a-service-from-within-a-tool-window-or-control-container"></a>도구 창 또는 컨트롤 컨테이너 내에서 서비스를 가져오려면  
  
- 생성자, 도구 창 또는 컨트롤 컨테이너에이 코드를 삽입 합니다.  
  
     [!code-csharp[UseGetGlobalService#1](../snippets/csharp/VS_Snippets_VSSDK/usegetglobalservice/cs/getglobalservicepackage.cs#1)]
     [!code-vb[UseGetGlobalService#1](../snippets/visualbasic/VS_Snippets_VSSDK/usegetglobalservice/vb/getglobalservicepackage.vb#1)]  
  
     이 코드는 SVsActivityLog 서비스를 가져와 <xref:Microsoft.VisualStudio.Shell.Interop.IVsActivityLog> 활동 로그에 쓰는 데 사용할 수 있는 인터페이스로 캐스팅 합니다. 예제는 [방법: 활동 로그 사용](../extensibility/how-to-use-the-activity-log.md)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [방법: 서비스 문제 해결](../extensibility/how-to-troubleshoot-services.md)   
 [서비스 사용 및 제공](../extensibility/using-and-providing-services.md)   
 [서비스 필수 항목](../extensibility/internals/service-essentials.md)