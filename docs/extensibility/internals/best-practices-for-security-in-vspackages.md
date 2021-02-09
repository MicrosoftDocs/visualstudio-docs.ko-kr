---
title: Vspackage의 보안에 대 한 모범 사례 | Microsoft Docs
description: Visual Studio 응용 프로그램의 기본 보안 및 배포 단위인 VSPackage의 보안에 대 한 모범 사례에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a4e706a115e8cec3b13ef58cf6cdef61912f5810
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99905984"
---
# <a name="best-practices-for-security-in-vspackages"></a>Vspackage의 보안에 대 한 모범 사례
컴퓨터에를 설치 하려면 [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 관리자 자격 증명을 사용 하 여 컨텍스트에서를 실행 해야 합니다. 응용 프로그램의 기본 보안 및 배포 단위는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] [VSPackage](../../extensibility/internals/vspackages.md)입니다. VSPackage를 사용 하 여 등록 해야 하며 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ,이 경우에도 관리 자격 증명이 필요 합니다.

 관리자는 레지스트리 및 파일 시스템에 대 한 모든 권한을 가지 며 모든 코드를 실행할 수 있습니다. VSPackage를 개발, 배포 또는 설치 하려면 다음 권한이 있어야 합니다.

 설치 되는 즉시 VSPackage는 완전히 신뢰할 수 있습니다. VSPackage와 연결 된이 높은 권한으로 인해 악의적인 의도를 가진 VSPackage를 실수로 설치할 수 있습니다.

 사용자는 신뢰할 수 있는 원본 에서만 Vspackage를 설치 해야 합니다. Vspackage를 개발 하는 회사는 사용자의 변조를 방지 하기 위해 강력한 이름을 지정 하 고 서명 해야 합니다. Vspackage를 개발 하는 회사는 웹 서비스 및 원격 설치와 같은 외부 종속성을 검토 하 여 보안 문제를 평가 하 고 수정 해야 합니다.

 자세한 내용은 [.NET Framework에 대 한 보안 코딩 지침](/previous-versions/visualstudio/visual-studio-2008/d55zzx87(v=vs.90))을 참조 하세요.

## <a name="see-also"></a>참고 항목
- [추가 기능 보안](/previous-versions/1326zbk3(v=vs.140))
- [DDEX 보안](/previous-versions/bb163703(v=vs.140))