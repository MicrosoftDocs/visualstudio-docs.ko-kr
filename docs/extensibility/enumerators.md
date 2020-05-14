---
title: 열거자 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, enumerators
ms.assetid: a60030c5-e1d1-47e1-84bb-cbfe838ab479
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ee48d064612e5519d5ad7e5eaf04de6c5a697837
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711848"
---
# <a name="enumerators"></a>Enumerators
이 섹션에서는 소스 제어 플러그인 API에 열거자 데이터 형식을 나열합니다.

## <a name="in-this-section"></a>섹션 내용
- [명령 코드](../extensibility/command-code-enumerator.md) [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 및 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 함수에 대 한 옵션을 나열 합니다.

- [메시지 메시지](../extensibility/message-enumerator.md) 인쇄 콜백에 사용되는 플래그를 새길 [수](../extensibility/lptextoutproc.md)있습니다.

- [파일 상태 코드](../extensibility/file-status-code-enumerator.md) 소스 제어하에 파일의 상태를 지정하는 명명된 상수 값을 포함합니다.

- [디렉터리 상태 코드](../extensibility/directory-status-code-enumerator.md) 소스 제어에서 디렉터리 상태를 지정하는 명명된 상수 값을 포함합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md) 소스 제어 플러그인 SDK를 정의하고 포함된 리소스에 대해 설명합니다.

- [SccGetCommand옵션](../extensibility/sccgetcommandoptions-function.md) 지정된 명령에 대한 고급 옵션을 사용자에게 요청합니다.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) 파일의 현재 상태를 검사합니다. 또한 이 함수를 사용하여 파일이 `pfnPopulate` `nCommand`의 조건과 일치하지 않을 때 호출자에게 알립니다.

- [LPTEXTOUTPROC](../extensibility/lptextoutproc.md) [SccOpenProject에서](../extensibility/sccopenproject-function.md) IDE를 통해 소스 제어 플러그인의 메시지를 표시하는 데 사용되는 콜백 함수에 대해 설명합니다.

- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md) 소스 제어 플러그인 API의 모든 요소에 대한 전체 목록을 제공합니다.
