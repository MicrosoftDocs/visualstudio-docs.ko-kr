---
title: '&apos;소스 제어 플러그 인 API 1.3의 새로운 기능'
description: 추가 고급 제어 기능을 제공 하는 새로운 기능을 소개 하는 소스 제어 플러그 인 API 버전 1.3의 새로운 기능에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7ab9079248931758efbcfcd792ce3c79ccffb270
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105074264"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>소스 제어 플러그 인 API 버전 1.3의 새로운 기능&#39;
소스 제어 플러그 인 API 버전 1.3에는 보다 고급 제어를 제공 하는 다음과 같은 새로운 기능이 도입 되었습니다.

## <a name="changes"></a>변경
 다음 함수는 소스 제어 플러그 인 API 버전 1.3에 새로 있습니다.

|함수|개요|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|추가 기능 비트를 보고할 수 있습니다.|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|로컬 디스크에 있는 버전 제어 데이터베이스에서 최신 버전을 포함 하는 파일을 검사할 수 있습니다.|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|지정 된 파일에 대 한 이름 변경 (이름 바꾸기, 추가 및 삭제)의 상태를 검사할 수 있습니다.|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|버전 제어 데이터베이스의 디렉터리 및 파일에 대 한 검사를 허용 합니다.|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|버전 제어 데이터베이스의 지정 된 파일 목록을 현재 프로젝트에 추가 합니다.|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|지정 된 파일의 자동 "Get"을 수행 합니다. 사용자 인터페이스가 표시 되지 않습니다.|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|사용자 관련 옵션에 대 한 액세스를 허용 합니다.|

## <a name="see-also"></a>참조
- [시작](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
