---
title: RegPkg 유틸리티 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- regpkg, registration utility
- registration, regpkg utility
ms.assetid: 1683ee18-59d1-4bab-a674-dd00dd960de3
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1895d3b57e5109f824728021cb1d64f0c527384b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90842030"
---
# <a name="regpkg-utility"></a>RegPkg 유틸리티
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

> [!NOTE]
> Visual Studio에서 패키지를 등록 하는 기본 방법은. .pkgdef 파일을 사용 하는 것입니다. 이를 통해 시스템 레지스트리에 액세스할 필요 없이 확장 배포를 수행할 수 있습니다 .이는 VSIX 배포를 위한 요구 사항입니다. .Pkgdef 파일은 [Createpkgdef 유틸리티](../../extensibility/internals/createpkgdef-utility.md)를 사용 하 여 만듭니다. Visual Studio 패키지 배포에 대 한 자세한 내용은 [Visual Studio 확장](../../extensibility/shipping-visual-studio-extensions.md)제공을 참조 하세요.  
  
 RegPkg.exe 유틸리티는를 사용 하 여 VSPackage를 등록 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 하 고 배포용으로 준비 합니다. 이 유틸리티는 VSPackage 개발 중에 백그라운드에서 사용 됩니다. 이는 실험적 hive에서 VSPackage를 빌드하고 실행할 수 있도록 빌드 프로세스의 일부로 실행 됩니다.  
  
 RegPkg는 여러 형식으로 시스템 레지스트리 스크립트를 생성할 수 있습니다. .Msi 프로젝트 또는 Windows Installer XML 도구 집합 파일 등의 배포 프로젝트에 이러한 스크립트를 통합할 수 있습니다.  
  
 RegPkg.exe은 일반적으로\VisualStudioIntegration\Tools\Bin\RegPkg.exe에 있습니다 \<*Visual Studio SDK installation path*> . RegPkg는 다음 구문을 따릅니다.  
  
```  
RegPkg [/root:<root>] [/regfile:<regfile>] [/rgsfile:<rgsfile> [/rgm]] [/vrgfile:<vrgfile>] [/codebase | /assembly] [/unregister] AssemblyPath  
```  
  
 /root: root  
 지정 된에서 등록을 수행 합니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] root.  
  
 /regfile: 파일 이름  
 레지스트리를 업데이트 하는 대신 .reg 파일을 만듭니다.  /Vrgfile 또는/rgsfile 또는/wixfile.와 함께 사용할 수 없습니다.  
  
 /rgsfile: 파일 이름  
 레지스트리를 업데이트 하는 대신 .rgs 파일을 만듭니다.  /Vrgfile 또는/regfile 또는/wixfile.와 함께 사용할 수 없습니다.  
  
 /vrgfile: 파일 이름  
 레지스트리를 업데이트 하는 대신 vrg 파일을 만듭니다.  /Regfile 또는/rgsfile 또는/wixfile.와 함께 사용할 수 없습니다.  
  
 /rgm  
 .Rgs 파일 외에도. rgm 파일을 만듭니다.  /Rgsfile.와 함께 사용 해야 합니다.  
  
 /wixfile: 파일 이름  
 레지스트리를 업데이트 하는 대신 Windows Installer XML 도구 집합 호환 파일을 만듭니다.  /Regfile 또는/rgsfile 또는/vrgfile.와 함께 사용할 수 없습니다.  
  
 /codebase  
 어셈블리 대신 코드 베이스를 사용 하 여 등록 합니다.  
  
 /assembly  
 코드 베이스가 아닌 어셈블리를 사용 하 여 등록 합니다.  
  
 /unregister  
 이 패키지의 등록을 취소 합니다.  사용할 수 없음  
  
 /regfile 또는/vrgfile 또는/rgsfile 또는/wixfile. 사용  
  
## <a name="see-also"></a>참고 항목  
 [제품 릴리스](../../misc/releasing-a-visual-studio-integration-product.md)   
 [RegPkg 패키지 등록 문제 해결](../../extensibility/internals/troubleshooting-regpkg-package-registration.md)
