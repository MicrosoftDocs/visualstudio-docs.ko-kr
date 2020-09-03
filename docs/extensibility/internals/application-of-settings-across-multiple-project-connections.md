---
title: 여러 프로젝트 연결에서 설정의 응용 프로그램 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, application of settings
ms.assetid: 2116d3d0-c46c-4d0a-b482-08a178584f46
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bcaed0f7f2380dd36bcbffd776839025fe9efa16
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80710055"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>여러 프로젝트 연결에서 설정 적용
소스 제어 플러그 인 API 버전 1.2을 사용 하 여 빌드된 소스 제어 플러그 인은 일괄 처리 작업을 사용 하 여 여러 프로젝트 또는 여러 연결 컨텍스트에서 동일한 원본 제어 작업을 실행할 수 있습니다. 일괄 처리를 사용 하 여 사용자 환경에서 중복 된 프로젝트별 대화 상자를 제거할 수 있습니다.

 원본 제어 플러그 인에서 원본 제어 플러그 인 1.1 (예: 다른 파일 공유 컴퓨터의 두 웹 프로젝트)를 사용 하 여 빌드한 소스 제어 플러그 인에서 둘 이상의 연결에 속하는 여러 항목을 선택 하는 경우 사용자는 동일한 대화 상자를 반복적으로 표시 합니다. 이 시나리오는 사용자가 대화 상자의 **모두에 적용** 확인란을 클릭 한 경우에도 발생 합니다 .이는 IDE가 각 연결 컨텍스트에 대해 해당 상태를 다시 설정 하기 때문입니다.

## <a name="new-capability-flag"></a>새 기능 플래그
 `SccBeginBatch`함수는 `SCC_CAP_BATCH` 일괄 처리 작업이 진행 중임을 나타내는 플래그를 설정 합니다.

## <a name="new-functions"></a>새로운 함수
다음 새 함수는 일괄 처리 작업을 지원 합니다.

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

`SCCBeginBatch`함수는 소스 제어 작업 그룹을 시작 합니다. `SccEndBatch`함수는 그룹을 닫습니다. 그룹은 중첩 될 수 없습니다.

## <a name="see-also"></a>참고 항목
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
