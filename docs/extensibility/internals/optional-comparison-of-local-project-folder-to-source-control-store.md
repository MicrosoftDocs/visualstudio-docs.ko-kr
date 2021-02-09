---
title: 프로젝트 폴더를 소스 제어 저장소와 비교 | Microsoft Docs
description: 소스 제어 플러그 인 API에서 로컬 프로젝트 폴더와 원본 제어 간의 비교는 SccDirQueryInfo 및 Sccdidiff를 사용 하 여 수행 됩니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, comparing versions
- source control plug-ins, local project folders
ms.assetid: 65217e8b-15a6-4446-92b0-4cff1c6220f5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 61a23eb1fcb3cbae9e478f35b3ac1fdb6abaf407
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99895481"
---
# <a name="optional-comparison-of-local-project-folder-to-source-control-store"></a>로컬 프로젝트 폴더와 소스 제어 저장소의 선택적 비교
소스 제어 플러그 인 API 1.2에서 [Sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) 및 [Scctdiff](../../extensibility/sccdirdiff-function.md)함수를 사용 하 여 로컬 프로젝트 폴더와 소스 제어를 비교할 수 있습니다.

 **솔루션 탐색기** 내에서 개별 파일 대신 폴더를 선택 하면 **버전 비교** 바로 가기 메뉴에서 소스 제어 플러그 인의 새 [sccdirqueryinfo](../../extensibility/sccdirqueryinfo-function.md) 및 [scctdiff](../../extensibility/sccdirdiff-function.md) 를 호출 합니다.

## <a name="new-capability-flags"></a>새 기능 플래그
 `SCC_CAP_DIRECTORYDIFF`

 `SCC_CAP_DIRECTORYCHECKOUT`

## <a name="new-functions"></a>새로운 함수
- [SccDirDiff](../../extensibility/sccdirdiff-function.md)

- [SccDirQueryInfo](../../extensibility/sccdirqueryinfo-function.md)

 `SccDirQueryInfo`함수는 `SccDirDiff` 작업 디렉터리가 원본에서 제어 되는지 확인 하기 위해 이전에 호출 됩니다. `SccDirDiff`함수는 현재 로컬 디렉터리와 해당 소스 제어 폴더 간의 차이점을 표시 합니다. 이 명령은 원본 제어 플러그 인에 디렉터리에 대 한 변경 내용 목록을 표시 하도록 요청 합니다. 소스 제어 플러그 인은 차이를 표시 하는 자체 UI를 제공 합니다.

> [!NOTE]
> 이 함수는 [Sccdiff](../../extensibility/sccdiff-function.md)와 동일한 명령 플래그를 사용 합니다. 원본 제어 플러그 인 공급자는 디렉터리에 대 한 "빠른 diff" 작업을 지원 하지 않도록 선택할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
