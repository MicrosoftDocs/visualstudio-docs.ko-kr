---
title: RegPkg 패키지 등록 문제 해결 | Microsoft Docs
description: 이 정보를 사용 하 여 Visual Studio에서 RegPkg 패키지 등록 문제를 해결할 수 있습니다. 패키지에 적합 한 버전의 RegPkg를 사용 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: troubleshooting
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: eef67b86925bc38a317196bbf00860b75a6ee15c
ms.sourcegitcommit: 19061b61759ce8e3b083a0e01a858e5435580b3e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/15/2020
ms.locfileid: "97487714"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg 패키지 등록 문제 해결
> [!NOTE]
> Visual Studio에서 패키지를 등록 하는 기본 방법은. .pkgdef 파일을 사용 하는 것입니다. 이렇게 하면 시스템 레지스트리에 액세스할 필요 없이 확장 배포를 수행할 수 있습니다. .Pkgdef 파일은 [Createpkgdef 유틸리티](../../extensibility/internals/createpkgdef-utility.md)를 사용 하 여 만듭니다.

 에서 RegPkg를 사용 하 여 패키지를 등록 하려면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 패키지에 적합 한 RegPkg 버전을 사용 해야 합니다.

## <a name="regpkg-versions-related-to-package-versions"></a>패키지 버전과 관련 된 RegPkg 버전
 RegPkg에는 두 가지 버전이 있습니다. 에는 하나의 버전이 포함 되어 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 있습니다. 이 버전을 사용 하 여 다음 어셈블리 중 하나를 사용 하 여 빌드된 패키지를 등록 합니다.

1. Microsoft.VisualStudioShell.9.0.dll

2. Microsoft.VisualStudioShell.10.0.dll

3. Microsoft.VisualStudioShell.11.0.dll

   이전 Microsoft.VisualStudio.Shell.dll 어셈블리를 사용 하 여 빌드된 패키지는 등록할 수 없습니다.

   이전 버전의 RegPkg는 Microsoft.VisualStudio.Shell.dll 어셈블리를 사용 하 여 빌드된 패키지를 등록할 수 있습니다. 그러나 해당 어셈블리의 이후 버전을 사용 하 여 작성 된 패키지는 등록할 수 없습니다.

## <a name="see-also"></a>참고 항목
- [VSPackages](../../extensibility/internals/vspackages.md)
- [Visual Studio 문제 해결](/troubleshoot/visualstudio/welcome-visual-studio/)
