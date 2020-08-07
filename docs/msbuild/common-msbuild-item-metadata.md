---
title: 공통 MSBuild 항목 메타데이터 | Microsoft Docs
ms.date: 07/13/2020
ms.topic: reference
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- msbuild, common item metadata
- item metadata (MSBuild)
ms.assetid: 9857505d-ae15-42f1-936d-6cd7fb9dd276
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 1c715c16782733a08bb617a464c1aa9510d35b54
ms.sourcegitcommit: dda98068c0f62ccd1a19fdfde4bdb822428d0125
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/30/2020
ms.locfileid: "87425970"
---
# <a name="common-msbuild-item-metadata"></a>공통 MSBuild 항목 메타데이터

다음 표에서는 일부 MSBuild SDK 또는 대상에 대해 유효하지만 모든 항목에 대해 기본적으로 설정되지는 않은 선택적 항목 메타데이터에 대해 설명합니다. 이러한 메타데이터를 설정하여 빌드 동작에 영향을 줄 수 있지만 이는 사용 중인 SDK 또는 대상 파일이 이를 인식하는 경우에만 해당됩니다.

| 항목 메타데이터 | SDK | 설명 |
|---------------| ------- | -------------|
|%(Link)| 모두 |Visual Studio 프로젝트 시스템은 `Link` 메타데이터(있는 경우)를 사용하여 프로젝트 트리에 표시되는 항목을 변경합니다. **솔루션 탐색기**의 다른 논리적 폴더 구조에 파일을 넣을 수 있습니다.<br />또한 `AssignTargetPath` 작업은 `Link`를 확인하여 복사되는 항목 중 하나일 경우 출력 디렉터리에서 파일을 복사할 위치를 결정합니다.|
|%(LinkBase)| .NET Core SDK | 항목 그룹의 `Link` 메타데이터에 사용할 폴더를 설정하는 데 사용됩니다. |

## <a name="see-also"></a>참조

- [일반적인 MSBuild 프로젝트 속성](../msbuild/common-msbuild-project-properties.md)
- [일반적인 MSBuild 프로젝트 항목](../msbuild/common-msbuild-project-items.md)
- [MSBuild 잘 알려진 항목 메타데이터](msbuild-well-known-item-metadata.md)