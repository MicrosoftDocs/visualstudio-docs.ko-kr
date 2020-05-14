---
title: VS패키지 등록 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705739"
---
# <a name="registering-vspackages"></a>VSPackage 등록
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage를 설명하고 찾을 수 있습니다. .pkgdef 파일에는 시스템 레지스트리에 추가될 모든 등록 정보가 포함되어 있습니다. 관리되는 VSPackage는 소스 코드에 특성을 추가한 다음 결과 어셈블리에서 [CreatePkgDef 유틸리티를](../../extensibility/internals/createpkgdef-utility.md) 실행하여 .pkgdef 파일을 생성하여 등록됩니다.

## <a name="in-this-section"></a>섹션 내용
- [VSPackage 파일 위치를 VS Shell 지정](../../extensibility/internals/specifying-vspackage-file-location-to-the-vs-shell.md)

 VSPackage에 대한 로드 경로를 설명합니다.

- [VSPackage 등록 및 등록 취소](../../extensibility/registering-and-unregistering-vspackages.md)

 VSPackage를 등록하는 방법을 설명합니다.
