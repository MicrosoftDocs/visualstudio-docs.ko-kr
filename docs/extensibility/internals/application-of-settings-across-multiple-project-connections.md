---
title: 여러 프로젝트 연결에 걸쳐 설정 적용 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710055"
---
# <a name="application-of-settings-across-multiple-project-connections"></a>여러 프로젝트 연결에 걸쳐 설정 적용
소스 제어 플러그인 API 버전 1.2를 사용하여 빌드된 소스 제어 플러그인은 일괄 처리 작업을 사용하여 여러 프로젝트 또는 여러 연결 컨텍스트에서 동일한 소스 제어 작업을 실행할 수 있습니다. 일괄 처리를 사용하여 사용자 환경의 중복 프로젝트별 대화 상자를 제거할 수 있습니다.

 사용자가 소스 제어 플러그인 API 버전 1.1(예: 서로 다른 파일 공유 컴퓨터의 두 웹 프로젝트)을 사용하여 빌드된 소스 제어 플러그인에서 둘 이상의 연결에 속하는 여러 항목을 선택하고 체크 아웃하면 동일한 대화 상자가 반복적으로 표시됩니다. 이 시나리오는 사용자가 각 연결 컨텍스트에 대 한 상태를 재설정 하기 때문에 대화 상자에서 **모두 적용** 확인 란을 클릭 하는 경우에 발생 합니다.

## <a name="new-capability-flag"></a>새 기능 플래그
 이 `SccBeginBatch` 함수는 `SCC_CAP_BATCH` 일괄 처리 작업이 진행 중임을 나타내기 위해 플래그를 설정합니다.

## <a name="new-functions"></a>새로운 함수
다음 새 함수는 일괄 처리 작업을 지원합니다.

- [SccBeginBatch](../../extensibility/sccbeginbatch-function.md)

- [SccEndBatch](../../extensibility/sccendbatch-function.md)

함수는 `SCCBeginBatch` 소스 제어 작업 그룹을 시작합니다. 함수가 `SccEndBatch` 그룹을 닫습니다. 그룹이 중첩되지 않을 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 버전 1.2의 새로운 소식](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
