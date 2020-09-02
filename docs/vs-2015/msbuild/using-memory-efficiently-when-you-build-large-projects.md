---
title: 대규모 프로젝트 빌드 시 메모리의 효율적인 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 28d9f3d43faa53731b101dfdf58fe1e68a0920c5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178291"
---
# <a name="using-memory-efficiently-when-you-build-large-projects"></a>대규모 프로젝트 빌드 시 메모리의 효율적인 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

대규모 프로젝트는 종종 많은 하위 프로젝트와 다른 종속 파일을 포함하고 빌드 시 많은 시스템 메모리를 사용할 수 있습니다. 사용 가능한 시스템 메모리가 감소하는 경우 시스템 성능이 저하될 수 있습니다. 메모리 또는 프로젝트가 제거된 버전 3.5에 이전 버전의 [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트가 남아 있었지만 나중에 검색을 위해 캐시에 빌드 결과를 유지했습니다.  
  
 버전 4.0는 프로젝트에서 `UnloadProjectsOnCompletion` 및 `UseResultsCache`와 같은 속성을 사용할 필요가 없도록 하여 이 메모리 관리를 자동으로 처리합니다.  
  
## <a name="see-also"></a>관련 항목  
 [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
