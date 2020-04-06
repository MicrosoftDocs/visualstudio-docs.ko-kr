---
title: 프로젝트 유형 배포 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 835e85ade4d309d0b5692aa9b857476cd6b5927a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708786"
---
# <a name="deploy-project-types"></a>프로젝트 유형 배포
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)]*[프로젝트](ProjectAggregator2.dll)와*재배포를 위한 Windows 설치 관리자*패키지(ProjectAggregator2.msi)를*설치합니다. 관리 코드 프로젝트 형식에 새 집계를 사용해야 합니다. ProjectAggregator2는 관리 코드 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 형식이 제대로 작동하지 않도록 하는 프로젝트 집계의 제한 사항에 대해 작동합니다. 다음 단계에서는 새 애그리게이터를 사용하도록 VSPackage를 변경하는 방법을 설명합니다.

1. 솔루션에서 네이티브 계층래퍼 프로젝트를 제거합니다.

2. 설치에서 네이티브 계층래퍼 바이너리를 제거합니다.

3. 설치에 *ProjectAggregator2.msi를* 추가합니다.
