---
title: IDE에서 구현한 콜백 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 666486f5b800707a4467a129abeed7a13306f10a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739900"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE에서 구현한 콜백 함수
통합 개발 환경(IDE)과 가능한 한 원활하게 통합하고 통합된 최종 사용자 환경을 제공하기 위해 소스 제어 플러그인은 IDE에서 구현한 콜백 기능을 사용할 수 있습니다. 플러그인은 소스 제어 작업 중에 적절한 시간에 이러한 함수를 호출하여 IDE에 정보를 전달할 수 있습니다. 그런 다음 IDE는 이 정보를 기본 UI에 포함된 요소로 표시할 수 있습니다. 사용자는 플러그인이 자체 UI를 사용하는 경우보다 이 시나리오에서 덜 조각화된 환경을 가지고 있습니다.

 필요한 헤더 파일은 *scc.h.* 기본 위치는 *\프로그램 파일\VSIP 8.0\EnvSDK\common\inc.\\* 또한 *\프로그램 파일\VSIP 8.0\MSSCCI에서\\*소스 제어 플러그인 샘플이 있는 VSIP 폴더에 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) [SccOpenProject에서](../extensibility/sccopenproject-function.md) IDE를 통해 소스 제어 플러그인의 메시지를 표시하는 데 사용되는 콜백 함수에 대해 설명합니다.

- [팝리스트푼크](../extensibility/poplistfunc.md) IDE가 버전 제어 하에 있는 파일의 전체 목록과 같이 소스 제어 플러그인에서만 사용할 수 있는 정보에 대한 완전한 액세스 권한이 없는 경우 [SccPopulateList에서](../extensibility/sccpopulatelist-function.md) 사용하는 콜백 함수에 대해 설명합니다.

- [쿼리 변경FUNC](../extensibility/querychangesfunc.md) [SccQueryChanges](../extensibility/sccquerychanges-function.md) 작업에서 사용되는 콜백 함수에 대해 설명합니다.

- [팝디리스트푼크](../extensibility/popdirlistfunc.md) [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 작업에서 사용되는 콜백 함수에 대해 설명합니다.

- [옵트네임 체인지PFN](../extensibility/optnamechangepfn.md) 소스 제어 플러그인이 이름 변경 내용을 IDE로 다시 전달할 수 있도록 [하는 SccSetOption](../extensibility/sccsetoption-function.md) 호출에 의해 설정된 콜백 함수에 대해 설명합니다.

## <a name="related-sections"></a>관련 단원
- [스시오픈프로젝트](../extensibility/sccopenproject-function.md) 프로젝트를 엽니다.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) 파일의 현재 상태를 검사합니다. 또한 이 함수를 사용하여 파일이 `pfnPopulate` `nCommand`의 조건과 일치하지 않을 때 호출자에게 알립니다.

- [스클레스디리스트](../extensibility/sccpopulatedirlist-function.md) 소스 제어하에 있는 프로젝트 또는 프로젝트의 디렉터리 및 파일 목록을 검사합니다. 발견된 각 디렉터리 및 파일 이름은 콜백 함수에 전달됩니다.

- [Scc쿼리 변경](../extensibility/sccquerychanges-function.md) 파일 목록에 변경된 이름 변경 내용을 검사합니다. 각 파일 이름은 변경 상태와 함께 콜백 함수에 전달됩니다.

- [SccSet옵션](../extensibility/sccsetoption-function.md) 다양한 옵션을 설정합니다. 각 옵션에서 `SCC_OPT_xxx` 시작하여 자체적으로 정의된 값 집합을 가짐

- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md) 소스 제어 플러그인 SDK의 참조 섹션의 내용을 설명합니다.
