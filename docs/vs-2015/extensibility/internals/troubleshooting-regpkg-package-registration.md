---
title: RegPkg 패키지 등록 문제 해결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 241975e475252a18d5e5a91c6e8c4fb40c067a95
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841811"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg 패키지 등록 문제 해결
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Visual Studio에서 패키지를 등록 하는 기본 방법은. .pkgdef 파일을 사용 하는 것입니다. 이렇게 하면 시스템 레지스트리에 액세스할 필요 없이 확장 배포를 수행할 수 있습니다. .Pkgdef 파일은 [Createpkgdef 유틸리티](../../extensibility/internals/createpkgdef-utility.md)를 사용 하 여 만듭니다.  
  
 에서 RegPkg를 사용 하 여 패키지를 등록 하려면 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 패키지에 적합 한 RegPkg 버전을 사용 해야 합니다.  
  
## <a name="regpkg-versions-related-to-package-versions"></a>패키지 버전과 관련 된 RegPkg 버전  
 RegPkg에는 두 가지 버전이 있습니다. 에는 하나의 버전이 포함 되어 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 있습니다. 이 버전을 사용 하 여 다음 어셈블리 중 하나를 사용 하 여 빌드된 패키지를 등록 합니다.  
  
1. Microsoft.VisualStudioShell.9.0.dll  
  
2. Microsoft.VisualStudioShell.10.0.dll  
  
3. Microsoft.VisualStudioShell.11.0.dll  
  
   이전 Microsoft.VisualStudio.Shell.dll 어셈블리를 사용 하 여 빌드된 패키지는 등록할 수 없습니다.  
  
   이전 버전의 RegPkg는 Microsoft.VisualStudio.Shell.dll 어셈블리를 사용 하 여 빌드된 패키지를 등록할 수 있습니다. 그러나 해당 어셈블리의 이후 버전을 사용 하 여 작성 된 패키지는 등록할 수 없습니다.  
  
## <a name="see-also"></a>참고 항목  
 [제품 릴리스](../../misc/releasing-a-visual-studio-integration-product.md)
