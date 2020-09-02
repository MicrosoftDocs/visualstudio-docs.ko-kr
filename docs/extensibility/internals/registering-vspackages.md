---
title: Vspackage 등록 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- managed VSPackages, registering
- registration, managed VSPackages
ms.assetid: 79b9424e-7e9b-4fc8-9b9f-00212674573c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b40793a5ab317b6a467e55df13302f19cec82640
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80705739"
---
# <a name="registering-vspackages"></a>VSPackage 등록
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .pkgdef 파일을 사용 하 여 VSPackage를 설명 하 고 찾습니다. .Pkgdef 파일에는 시스템 레지스트리에 추가 되지 않는 모든 등록 정보가 포함 되어 있습니다. 관리 되는 Vspackage는 소스 코드에 특성을 추가한 다음 결과 어셈블리에서 [Createpkgdef 유틸리티](../../extensibility/internals/createpkgdef-utility.md) 를 실행 하 여 .pkgdef 파일을 생성 하는 방식으로 등록 됩니다.

## <a name="in-this-section"></a>섹션 내용
- [VSPackage 파일 위치를 VS Shell에 지정](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 Vspackage에 대 한 로드 경로를 설명 합니다.

- [VSPackage 등록 및 등록 취소](../../extensibility/registering-and-unregistering-vspackages.md)

 VSPackage를 등록 하는 방법을 설명 합니다.
