---
title: 프로젝트 형식 배포 | Microsoft Docs
description: Visual Studio SDK에서 재배포할 새 프로젝트 형식 집계 및 Windows Installer 패키지를 사용 하 여 관리 코드 프로젝트 형식을 배포 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], managed-code
- projects [Visual Studio SDK], aggregator
ms.assetid: 7f132f67-8589-464c-90dc-0d57ae02aa8f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 121dda58b8e01c5b0029d8b3c93ef66d2657446e
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105090995"
---
# <a name="deploy-project-types"></a>프로젝트 형식 배포
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 새 *ProjectAggregator2.dll*(프로젝트 형식 집계)와 재배포할 Windows Installer 패키지 (*ProjectAggregator2.msi*)를 설치 합니다. 관리 코드 프로젝트 형식에 새 집계를 사용 해야 합니다. ProjectAggregator2는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 관리 코드 프로젝트 형식이 제대로 작동 하지 않도록 하는 프로젝트 집계의 제한 사항을 해결 합니다. 다음 단계에서는 새 집계를 사용 하도록 VSPackage를 변경 하는 방법을 설명 합니다.

1. 솔루션에서 NativeHierarchyWrapper 프로젝트를 제거 합니다.

2. 설치 프로그램에서 NativeHierarchyWrapper 이진 파일을 제거 합니다.

3. 설정에 *ProjectAggregator2.msi* 를 추가 합니다.
