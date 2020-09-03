---
title: 프로젝트 형식 배포 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708786"
---
# <a name="deploy-project-types"></a>프로젝트 형식 배포
[!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] 새*ProjectAggregator2.dll*(프로젝트 형식 집계)와 재배포할 Windows Installer 패키지 (*ProjectAggregator2.msi*)를 설치 합니다. 관리 코드 프로젝트 형식에 새 집계를 사용 해야 합니다. ProjectAggregator2는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 관리 코드 프로젝트 형식이 제대로 작동 하지 않도록 하는 프로젝트 집계의 제한 사항을 해결 합니다. 다음 단계에서는 새 집계를 사용 하도록 VSPackage를 변경 하는 방법을 설명 합니다.

1. 솔루션에서 NativeHierarchyWrapper 프로젝트를 제거 합니다.

2. 설치 프로그램에서 NativeHierarchyWrapper 이진 파일을 제거 합니다.

3. 설정에 *ProjectAggregator2.msi* 를 추가 합니다.
