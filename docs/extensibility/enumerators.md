---
title: 열거자 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80711848"
---
# <a name="enumerators"></a>Enumerators
이 섹션에는 소스 제어 플러그 인에서 알고 있어야 하는 소스 제어 플러그 인 API의 열거자 데이터 형식이 나열 되어 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [명령 코드](../extensibility/command-code-enumerator.md) [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 및 [SccPopulateList](../extensibility/sccpopulatelist-function.md) 함수에 대 한 옵션을 열거 합니다.

- [메시지](../extensibility/message-enumerator.md) 인쇄 콜백과 [Lptextoutproc](../extensibility/lptextoutproc.md)에 사용 되는 플래그를 열거 합니다.

- [파일 상태 코드](../extensibility/file-status-code-enumerator.md) 소스 제어에서 파일의 상태를 지정 하는 명명 된 상수 값을 포함 합니다.

- [디렉터리 상태 코드](../extensibility/directory-status-code-enumerator.md) 원본 제어에서 디렉터리의 상태를 지정 하는 명명 된 상수 값을 포함 합니다.

## <a name="related-sections"></a>관련 단원
- [소스 제어 플러그 인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md) 소스 제어 플러그 인 SDK를 정의 하 고 포함 된 리소스를 설명 합니다.

- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 지정 된 명령에 대 한 고급 옵션을 사용자에 게 표시 합니다.

- [SccPopulateList](../extensibility/sccpopulatelist-function.md) 현재 상태에 대 한 파일 목록을 검사 합니다. 또한은 함수를 사용 하 여 `pfnPopulate` 파일이의 조건과 일치 하지 않는 경우 호출자에 게 알립니다 `nCommand` .

- [Lptextoutproc](../extensibility/lptextoutproc.md) IDE를 통해 소스 제어 플러그 인의 메시지를 표시 하기 위해 [Sccopenproject](../extensibility/sccopenproject-function.md) 에서 사용 하는 콜백 함수에 대해 설명 합니다.

- [소스 제어 플러그](../extensibility/source-control-plug-ins.md) 인 소스 제어 플러그 인 API의 모든 요소에 대 한 전체 목록을 제공 합니다.
