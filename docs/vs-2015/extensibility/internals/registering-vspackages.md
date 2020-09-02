---
title: Vspackage 등록 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
caps.latest.revision: 21
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 053157b0ce1cb4250d8c666725431515c75b5fa2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157385"
---
# <a name="registering-vspackages"></a>VSPackage 등록
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .pkgdef 파일을 사용 하 여 VSPackage를 설명 하 고 찾습니다. .Pkgdef 파일에는 시스템 레지스트리에 추가 되지 않는 모든 등록 정보가 포함 되어 있습니다. 관리 되는 Vspackage는 소스 코드에 특성을 추가한 다음 결과 어셈블리에서 [Createpkgdef 유틸리티](../../extensibility/internals/createpkgdef-utility.md) 를 실행 하 여 .pkgdef 파일을 생성 하는 방식으로 등록 됩니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [VSPackage 파일 위치를 VS Shell에 지정](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)  
 Vspackage에 대 한 로드 경로를 설명 합니다.  
  
 [VSPackage 등록 및 등록 취소](../../extensibility/registering-and-unregistering-vspackages.md)  
 VSPackage를 등록 하는 방법을 설명 합니다.  
  
 [사용자 지정 등록 특성을 사용하여 확장 등록](../../misc/using-a-custom-registration-attribute-to-register-an-extension.md)  
 관리 되는 VSPackage를 배포 하는 데 사용할 수 있는 등록 매니페스트를 만드는 방법을 설명 합니다.
