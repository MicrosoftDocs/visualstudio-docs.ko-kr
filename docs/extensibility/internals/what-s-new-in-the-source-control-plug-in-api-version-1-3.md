---
title: 소스 제어 플러그인 API 버전 1.3에서 새로운&#39;| 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, what's new in API v1.3
- what's new [Visual Studio SDK], source control plug-ins
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9654f1f3ae6d4a3d73ddc3afca2977a57a98297d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703371"
---
# <a name="what39s-new-in-the-source-control-plug-in-api-version-13"></a>소스 제어 플러그인 API 버전 1.3에서&#39;새로운 것
소스 제어 플러그인 API 버전 1.3에서는 보다 고급 제어를 제공하기 위해 다음과 같은 새로운 기능을 도입했습니다.

## <a name="changes"></a>변경
 다음 함수는 소스 제어 플러그인 API 버전 1.3에 대한 새로운 기능입니다.

|함수|개요|
|--------------|--------------|
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|추가 기능 비트를 보고할 수 있습니다.|
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|버전 제어 데이터베이스에 로컬 디스크보다 최신 버전이 있는 파일을 검사할 수 있습니다.|
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|지정된 파일의 이름 변경 상태(이름 변경, 추가 및 삭제)를 검사할 수 있습니다.|
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|버전 제어 데이터베이스의 디렉터리 및 파일 검사 허용|
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|버전 제어 데이터베이스의 지정된 파일 목록을 현재 프로젝트에 추가합니다.|
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|지정된 파일의 자동 "Get"을 수행합니다(사용자 인터페이스가 표시되지 않음)|
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|사용자 별 옵션에 대한 액세스 허용|

## <a name="see-also"></a>참조
- [시작](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)
- [소스 제어 플러그 인 API 버전 1.2의 새로운 기능](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)
