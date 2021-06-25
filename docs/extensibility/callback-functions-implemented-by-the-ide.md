---
title: IDE | 의해 구현되는 콜백 함수 Microsoft Docs
description: IDE에 정보를 전달하기 위해 소스 제어 작업 중에 플러그 인이 적절한 시간에 호출할 수 있는 콜백 함수에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 78ce3a9cdd183cff0518ee3c6da9326c63297a85
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899149"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE에서 구현하는 콜백 함수
IDE(통합 개발 환경)와 최대한 원활하게 통합하고 통합된 최종 사용자 환경을 제공하기 위해 소스 제어 플러그 인은 IDE에서 구현하는 콜백 함수를 사용할 수 있습니다. 플러그 인은 소스 제어 작업 중에 적절한 시간에 이러한 함수를 호출하여 정보를 IDE에 전달할 수 있습니다. 그런 다음 IDE는 이 정보를 네이티브 UI에 포함된 요소로 표시할 수 있습니다. 이 시나리오에서 사용자는 플러그 인이 자체 UI를 사용하는 경우보다 덜 조각화된 환경을 겪습니다.

 필요한 헤더 파일은 *scc.h* 입니다. 기본 위치는 *\Program Files\VSIP 8.0\EnvSDK\common\inc 입니다. \\* *\Program Files\VSIP 8.0\MSSCCI에 \\* 소스 제어 플러그 인 샘플이 있는 VSIP 폴더에도 있습니다.

## <a name="in-this-section"></a>단원 내용
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) [SccOpenProject에서](../extensibility/sccopenproject-function.md) IDE를 통해 소스 제어 플러그 인의 메시지를 표시하는 데 사용하는 콜백 함수에 대해 설명합니다.

- [POPLISTFUNC](../extensibility/poplistfunc.md) 버전 제어 아래 파일의 전체 목록과 같이 소스 제어 플러그 인에서만 사용할 수 있는 정보에 대한 완전한 액세스 권한이 IDE에 없는 경우 [SccPopulateList에서](../extensibility/sccpopulatelist-function.md) 사용하는 콜백 함수에 대해 설명합니다.

- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) [SccQueryChanges](../extensibility/sccquerychanges-function.md) 작업에서 사용하는 콜백 함수에 대해 설명합니다.

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 작업에서 사용하는 콜백 함수에 대해 설명합니다.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 소스 제어 플러그 인이 이름 변경 내용을 IDE에 다시 전달할 수 있도록 [하는 SccSetOption](../extensibility/sccsetoption-function.md) 호출에 의해 설정된 콜백 함수에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원
- [SccOpenProject](../extensibility/sccopenproject-function.md) 프로젝트를 엽니다.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) 파일 목록에서 현재 상태를 검사합니다. 또한 는 함수를 사용하여 `pfnPopulate` 파일이 의 조건과 일치하지 않을 때 호출자에게 알립니다. `nCommand`

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 소스 제어에 있는 프로젝트 또는 프로젝트의 디렉터리 및 파일 목록을 검사합니다. 찾은 각 디렉터리 및 파일 이름은 콜백 함수에 전달됩니다.

- [SccQueryChanges](../extensibility/sccquerychanges-function.md) 파일 목록에 대해 변경된 이름을 검사합니다. 각 파일 이름은 변경 상태와 함께 콜백 함수에 전달됩니다.

- [SccSetOption](../extensibility/sccsetoption-function.md) 다양한 옵션을 설정합니다. 각 옵션은 로 시작하고 `SCC_OPT_xxx` 고유한 정의된 값 집합을 가짐

- [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md) 소스 제어 플러그 인 SDK의 참조 섹션 내용에 대해 설명합니다.
