---
title: 레그랩 유틸리티 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cebfd7a9782a2760eb33f7e56bfe16b126fc6251
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705644"
---
# <a name="regpkg-utility"></a>RegPkg 유틸리티
> [!NOTE]
> Visual Studio에서 패키지를 등록하는 기본 방법은 .pkgdef 파일을 사용하는 것입니다. 이렇게 하면 VSIX 배포에 대한 요구 사항인 시스템 레지스트리에 액세스할 필요 없이 확장 배포가 가능합니다. Pkgdef 파일은 [CreatePkgDef 유틸리티를 사용하여 생성됩니다.](../../extensibility/internals/createpkgdef-utility.md) Visual Studio 패키지 배포에 대한 자세한 내용은 [Visual Studio 확장 서를](../../extensibility/shipping-visual-studio-extensions.md)참조하십시오.

 RegPkg.exe 유틸리티는 VSPackage를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 등록하고 배포를 준비합니다. 이 유틸리티는 VSPackage 개발 중에 뒤에서 사용됩니다. 실험용 하이브에서 VSPackage를 빌드하고 실행할 수 있도록 빌드 프로세스의 일부로 실행됩니다.

 RegPkg은 여러 형식으로 시스템 레지스트리 스크립트를 생성할 수 있습니다. .msi 프로젝트 또는 Windows 설치 관리자 XML 도구 집합 파일과 같은 배포 프로젝트에 이러한 스크립트를 통합할 수 있습니다.

 RegPkg.exe는 일반적으로 \< *비주얼 스튜디오 SDK 설치 경로*>\VisualStudio통합\도구\빈\RegPkg.exe에 있습니다. RegPkg은 다음 구문을 따릅니다.

```
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath
```

 /root:root는 지정된 아래에서 등록을 수행합니다.

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] root.

 /regfile:FileName 레지스트리를 업데이트하는 대신 .reg 파일을 만듭니다.  /vrgfile 또는 /rgsfile 또는 /wixfile과 함께 사용할 수 없습니다.

 /rgsfile:FileName 레지스트리를 업데이트하는 대신 .rgs 파일을 만듭니다.  /vrgfile 또는 /regfile 또는 /wixfile과 함께 사용할 수 없습니다.

 /vrgfile:FileName 레지스트리를 업데이트하는 대신 .vrg 파일을 만듭니다.  /regfile 또는 /rgsfile 또는 /wixfile과 함께 사용할 수 없습니다.

 /rgm rgs 파일 외에 .rgm 파일을 만듭니다.  /rgsfile과 결합해야 합니다.

 /wixfile:FileName 레지스트리를 업데이트 하는 대신 Windows 설치 관리자 XML 도구 집합 호환 파일을 만듭니다.  /regfile 또는 /rgsfile 또는 /vrgfile과 함께 사용할 수 없습니다.

 /codebase 어셈블리가 아닌 코드베이스로 등록합니다.

 /어셈블리 코드베이스가 아닌 어셈블리에 등록합니다.

 /등록 취소 이 패키지입니다.  사용할 수 없음

 /regfile 또는 /vrgfile 또는 /rgsfile 또는 /wixfile을 사용하십시오.

## <a name="see-also"></a>참조
- [VSPackage](../../extensibility/internals/vspackages.md)
- [RegPkg 패키지 등록 문제 해결](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
