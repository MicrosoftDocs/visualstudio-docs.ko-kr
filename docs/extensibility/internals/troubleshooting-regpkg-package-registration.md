---
title: RegPkg 패키지 등록 문제 해결 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- RegPkg
ms.assetid: f33f822f-697a-4bad-9c10-554b4c8f6246
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ebae9f7c5b4d1a6dcfee20c3b36c02f8ead2e0bc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704322"
---
# <a name="troubleshooting-regpkg-package-registration"></a>RegPkg 패키지 등록 문제 해결
> [!NOTE]
> Visual Studio에서 패키지를 등록하는 기본 방법은 .pkgdef 파일을 사용하는 것입니다. 이렇게 하면 시스템 레지스트리에 액세스할 필요 없이 확장 배포가 가능합니다. Pkgdef 파일은 [CreatePkgDef 유틸리티를 사용하여 생성됩니다.](../../extensibility/internals/createpkgdef-utility.md)

 에서 RegPkg을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]사용하여 패키지를 등록하려면 패키지에 적합한 RegPkg 버전을 사용해야 합니다.

## <a name="regpkg-versions-related-to-package-versions"></a>패키지 버전과 관련된 RegPkg 버전
 RegPkg에는 두 가지 버전이 있습니다. 하나의 버전이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에 포함되어 있습니다. 다음 어셈블리 중 하나를 사용하여 빌드된 패키지를 등록하려면 이 버전을 사용합니다.

1. 마이크로소프트.비주얼스튜디오쉘.9.0.dll

2. 마이크로소프트.비주얼스튜디오쉘.10.0.dll

3. 마이크로소프트.비주얼스튜디오쉘.11.0.dll

   이전 Microsoft.VisualStudio.Shell.dll 어셈블리를 사용하여 빌드된 패키지를 등록할 수 없습니다.

   이전 버전의 RegPkg은 Microsoft.VisualStudio.Shell.dll 어셈블리를 사용하여 빌드된 패키지를 등록할 수 있습니다. 그러나 해당 어셈블리의 이후 버전을 사용하여 빌드된 패키지를 등록할 수 없습니다.

## <a name="see-also"></a>참조
- [VSPackage](../../extensibility/internals/vspackages.md)
