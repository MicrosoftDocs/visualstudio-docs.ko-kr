---
title: 대규모 프로젝트 빌드 시 메모리의 효율적인 사용 | Microsoft Docs
description: 대량 프로젝트를 빌드할 때 MSBuild가 이전 버전 언로드, 캐시 검색과 같이 메모리를 자동으로 관리하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- memory use (MSBuild)
- msbuild, efficient memory use building large trees
- caching (MSBuild)
ms.assetid: 853a21ed-69f7-4817-af00-57f73e2c74b5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 61bfa09bf91b49c163e47bbf71c0d192b6950160
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/30/2020
ms.locfileid: "93047603"
---
# <a name="use-memory-efficiently-when-you-build-large-projects"></a>대규모 프로젝트 빌드 시 메모리의 효율적인 사용

대규모 프로젝트는 종종 빌드 시 많은 시스템 메모리를 사용할 수 있는 많은 하위 프로젝트와 다른 종속 파일을 포함합니다. 사용 가능한 시스템 메모리가 감소하는 경우 시스템 성능이 저하될 수 있습니다. 이전 버전의 MSBuild 프로젝트는 메모리에 남아 있었습니다. 버전 3.5에는 이전 버전의 프로젝트가 제거되었지만 나중에 검색을 위해 캐시에 빌드 결과가 유지되었습니다.

 버전 4.0는 프로젝트에서 `UnloadProjectsOnCompletion` 및 `UseResultsCache`와 같은 속성을 사용할 필요가 없도록 하여 이 메모리 관리를 자동으로 처리합니다.

### <a name="see-also"></a>참고 항목

- [병렬로 여러 프로젝트 빌드](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md)
