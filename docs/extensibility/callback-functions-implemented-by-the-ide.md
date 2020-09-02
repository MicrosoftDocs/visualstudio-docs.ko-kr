---
title: IDE에서 구현 하는 콜백 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739900"
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE에서 구현 하는 콜백 함수
IDE (통합 개발 환경)와 최대한 원활 하 게 통합 하 고 통합 최종 사용자 환경을 제공 하기 위해 소스 제어 플러그 인은 IDE에서 구현 하는 콜백 함수를 사용할 수 있습니다. 플러그 인은 소스 제어 작업 중에 적절 한 시간에 이러한 함수를 호출 하 여 IDE로 정보를 전달할 수 있습니다. 그러면 IDE는이 정보를 네이티브 UI에 포함 된 요소로 표시할 수 있습니다. 사용자는 플러그 인에서 자체 UI를 사용 하는 경우 보다 조각화 된 환경이이 시나리오에서 더 낮습니다.

 필요한 헤더 파일은 *scc. h입니다.* 기본 위치는 c # *Files\VSIP 8.0 \ EnvSDK\common\inc \\ *입니다. 또한 c #에서 소스 제어 플러그 인 샘플이 포함 된 VSIP 폴더 ( *Files\VSIP 8.0 \MSSCCI \\ *)에 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [Lptextoutproc](../extensibility/lptextoutproc.md) IDE를 통해 소스 제어 플러그 인의 메시지를 표시 하기 위해 [Sccopenproject](../extensibility/sccopenproject-function.md) 에서 사용 하는 콜백 함수에 대해 설명 합니다.

- [POPLISTFUNC](../extensibility/poplistfunc.md) [SccPopulateList](../extensibility/sccpopulatelist-function.md) 에서 사용 하는 콜백 함수에 대해 설명 합니다 .이는 IDE가 소스 제어 플러그 인 에서만 사용할 수 있는 정보 (예: 버전 제어에서 전체 파일 목록)에 대 한 완전 한 액세스 권한을가지고 있지 않은 경우에 사용 됩니다.

- [Query인 함수](../extensibility/querychangesfunc.md) [Sccquerychanges](../extensibility/sccquerychanges-function.md) 작업에서 사용 하는 콜백 함수에 대해 설명 합니다.

- [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md) [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 작업에서 사용 하는 콜백 함수에 대해 설명 합니다.

- [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md) 소스 제어 플러그 인이 이름 변경을 IDE에 다시 전달할 수 있도록 하는 [Sccsetoption](../extensibility/sccsetoption-function.md) 호출로 설정 된 콜백 함수에 대해 설명 합니다.

## <a name="related-sections"></a>관련 단원
- [Sccopenproject](../extensibility/sccopenproject-function.md) 프로젝트를 엽니다.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) 현재 상태에 대 한 파일 목록을 검사 합니다. 또한은 함수를 사용 하 여 `pfnPopulate` 파일이의 조건과 일치 하지 않는 경우 호출자에 게 알립니다 `nCommand` .

- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 소스 제어에서 사용할 프로젝트 또는 프로젝트의 디렉터리 및 파일 목록을 검사 합니다. 찾은 각 디렉터리와 파일 이름이 콜백 함수에 전달 됩니다.

- [Sccquerychanges](../extensibility/sccquerychanges-function.md) 파일 목록에 대 한 이름 변경을 검사 합니다. 각 파일 이름은 해당 변경 상태와 함께 콜백 함수에 전달 됩니다.

- [Sccsetoption](../extensibility/sccsetoption-function.md) 다양 한 옵션을 설정 합니다. 각 옵션은로 시작 `SCC_OPT_xxx` 하 고 고유 하 게 정의 된 값 집합을 가집니다.

- [소스 제어 플러그](../extensibility/source-control-plug-ins.md) 인 소스 제어 플러그 인 SDK의 참조 섹션 콘텐츠를 설명 합니다.
