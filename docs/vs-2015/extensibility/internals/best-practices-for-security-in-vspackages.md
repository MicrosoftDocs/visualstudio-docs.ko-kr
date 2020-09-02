---
title: Vspackage의 보안에 대 한 모범 사례 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Visual Studio SDK]
- security best practices, VSPackages
- best practices, security
ms.assetid: 212a0504-cf6c-4e50-96b0-f2c1c575c0ff
caps.latest.revision: 20
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 940644cd3950c38c6383371c1844b54b328acd0c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697276"
---
# <a name="best-practices-for-security-in-vspackages"></a>VSPackage의 보안 모범 사례
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

컴퓨터에를 설치 하려면 [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] 관리자 자격 증명을 사용 하 여 컨텍스트에서를 실행 해야 합니다. 응용 프로그램의 기본 보안 및 배포 단위는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] [vspackage](../../extensibility/internals/vspackages.md)입니다. VSPackage를 사용 하 여 등록 해야 하며 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ,이 경우에도 관리 자격 증명이 필요 합니다.  
  
 관리자는 레지스트리 및 파일 시스템에 대 한 모든 권한을 가지 며 모든 코드를 실행할 수 있습니다. VSPackage를 개발, 배포 또는 설치 하려면 다음 권한이 있어야 합니다.  
  
 설치 되는 즉시 VSPackage는 완전히 신뢰할 수 있습니다. VSPackage와 연결 된이 높은 권한으로 인해 악의적인 의도를 가진 VSPackage를 실수로 설치할 수 있습니다.  
  
 사용자는 신뢰할 수 있는 원본 에서만 Vspackage를 설치 해야 합니다. Vspackage를 개발 하는 회사는 사용자의 변조를 방지 하기 위해 강력한 이름을 지정 하 고 서명 해야 합니다. Vspackage를 개발 하는 회사는 웹 서비스 및 원격 설치와 같은 외부 종속성을 검토 하 여 보안 문제를 평가 하 고 수정 해야 합니다.  
  
 자세한 내용은 .NET Framework에 대 한 보안 코딩 지침 ()을 참조 하세요 [https://msdn.microsoft.com/library/d55zzx87.aspx](https://msdn.microsoft.com/library/d55zzx87.aspx) .  
  
## <a name="see-also"></a>관련 항목  
 [추가 기능 보안](https://msdn.microsoft.com/library/44a5c651-6246-4310-b371-65378917c799)   
 [DDEX 보안](https://msdn.microsoft.com/44a52a70-5c98-450e-993d-4a3b32f69ba8)
