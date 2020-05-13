---
title: VS패키지 보안 모범 사례 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d4309feeed3233d2149586afb1bf4efafacb21ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709901"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackage의 보안에 대한 모범 사례
컴퓨터에 설치하려면 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 관리 자격 증명이 있는 컨텍스트에서 실행중이어야 합니다. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 응용 프로그램의 보안 및 배포의 기본 단위는 [VSPackage](../../extensibility/internals/vspackages.md)입니다. VSPackage는 관리 자격 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]증명이 필요한 을 사용하여 등록해야 합니다.

 관리자는 레지스트리 및 파일 시스템에 작성하고 코드를 실행할 수 있는 모든 권한을 갖습니다. VSPackage를 개발, 배포 또는 설치하려면 이러한 권한이 있어야 합니다.

 VSPackage가 설치되는 즉시 완전히 신뢰할 수 있습니다. VSPackage와 연결된 높은 수준의 권한으로 인해 악의적인 의도가 있는 VSPackage를 실수로 설치할 수 있습니다.

 사용자는 신뢰할 수 있는 원본에서만 VSPackage를 설치해야 합니다. VSPackage를 개발하는 회사는 사용자가 변조를 방지할 수 있도록 이름을 강력하게 지정하고 서명해야 합니다. VSPackage를 개발하는 회사는 웹 서비스 및 원격 설치와 같은 외부 종속성을 검사하여 보안 문제를 평가하고 해결해야 합니다.

 자세한 내용은 [.NET Framework에 대한 보안 코딩 지침을](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90))참조하십시오.

## <a name="see-also"></a>참조
- [추가 기능 보안](https://msdn.microsoft.com/Library/44a5c651-6246-4310-b371-65378917c799)
- [DDEX 보안](https://msdn.microsoft.com/library/44a52a70-5c98-450e-993d-4a3b32f69ba8)
