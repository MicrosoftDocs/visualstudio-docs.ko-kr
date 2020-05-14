---
title: 프로젝트 폴더와 소스 제어 저장소 비교 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: facb3b656e0ac50b50fdb0291307aa2fe98b1df4
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706860"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>로컬 프로젝트 폴더와 소스 제어 저장소의 선택적 비교
소스 제어 플러그인 API 1.2에서 로컬 프로젝트 폴더와 소스 제어 간의 비교는 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) 및 [SccDirDiff](../../extensibility/sccdirdiff-function.md)함수를 사용하여 수행됩니다.

 **솔루션 탐색기**내에서 개별 파일 대신 **폴더를** 선택한 경우 버전 비교 바로 가기 메뉴는 소스 제어 플러그인에서 새 [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md) 및 [SccDirDiff를](../../extensibility/sccdirdiff-function.md) 호출합니다.

## <a name="new-capability-flags"></a>새 기능 플래그
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>새로운 함수
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 이 `SccDirQueryInfo` 함수는 `SccDirDiff` 작업 디렉터리원본이 소스 제어인지 확인하기 위해 이전에 호출됩니다. 이 `SccDirDiff` 함수는 현재 로컬 디렉터리와 해당 소스 제어 폴더 간의 차이점을 표시합니다. 이 명령은 소스 제어 플러그인에 디렉터리변경 목록을 표시하도록 요청합니다. 소스 제어 플러그인은 차이점을 표시하는 자체 UI를 제공합니다.

> [!NOTE]
> 이 함수는 [SccDiff와](../../extensibility/sccdiff-function.md)동일한 명령 플래그를 사용합니다. 소스 제어 플러그인 공급자는 디렉터리에 대한 "빠른 diff" 작업을 지원하지 않도록 선택할 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
