---
title: Scc초기화 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 661e0a24fa1d222079fd5ee728c5f42a5386c75b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700637"
---
# <a name="sccinitialize-function"></a>SccInitialize 함수
이 함수는 소스 제어 플러그인을 초기화하고 통합 개발 환경(IDE)에 대한 기능과 제한을 제공합니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccInitialize (
   LPVOID* ppvContext,
   HWND    hWnd,
   LPCSTR  lpCallerName,
   LPSTR   lpSccName,
   LPLONG  lpSccCaps,
   LPSTR   lpAuxPathLabel,
   LPLONG  pnCheckoutCommentLen,
   LPLONG  pnCommentLen
);
```

#### <a name="parameters"></a>매개 변수
 `ppvContext`

【인】 소스 제어 플러그인은 컨텍스트 구조에 대한 포인터를 여기에 배치할 수 있습니다.

 `hWnd`

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 `lpCallerName`

【인】 소스 제어 플러그인을 호출하는 프로그램의 이름입니다.

 `lpSccName`

【인, 아웃】 소스 제어 플러그인이 자체 이름을 넣는 버퍼입니다(초과하지 `SCC_NAME_LEN`않음).

 `lpSccCaps`

【아웃】 소스 제어 플러그인의 기능 플래그를 반환합니다.

 `lpAuxPathLabel`

【인, 아웃】 소스 제어 플러그인이 [SccOpenProject](../extensibility/sccopenproject-function.md) 및 [SccGetProjPath에서](../extensibility/sccgetprojpath-function.md) 반환되는 `lpAuxProjPath` 매개 변수를 설명하는 문자열을 배치하는 `SCC_AUXLABEL_LEN`버퍼입니다(초과하지 않음).

 `pnCheckoutCommentLen`

【아웃】 체크 아웃 주석에 대한 최대 허용 길이를 반환합니다.

 `pnCommentLen`

【아웃】 다른 주석에 대한 최대 허용 길이를 반환합니다.

## <a name="return-value"></a>Return Value
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|소스 제어 초기화가 성공했습니다.|
|SCC_E_INITIALIZEFAILED|시스템을 초기화할 수 없습니다.|
|SCC_E_NOTAUTHORIZED|사용자는 지정된 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECFICERROR|비특이적 오류; 소스 제어 시스템이 초기화되지 않았습니다.|

## <a name="remarks"></a>설명
 IDE는 소스 제어 플러그인을 처음 로드할 때 이 함수를 호출합니다. 이를 통해 IDE는 호출자 이름과 같은 특정 정보를 플러그인에 전달할 수 있습니다. 또한 IDE는 주석에 허용되는 최대 길이 및 플러그인 기능과 같은 특정 정보를 다시 가져옵니다.

 포인터를 `ppvContext` 가리킵니다. `NULL` 소스 제어 플러그인은 자체 사용을 위해 구조를 할당하고 해당 구조에 `ppvContext`대한 포인터를 에 저장할 수 있습니다. IDE는 이 포인터를 다른 모든 VSSCI API 함수에 전달하여 플러그인이 전역 저장소에 의존하지 않고 컨텍스트 정보를 사용할 수 있도록 하고 플러그인의 여러 인스턴스를 지원할 수 있도록 합니다. 이 구조는 [SccUninitialize가](../extensibility/sccuninitialize-function.md) 호출될 때 할당 해제되어야 합니다.

 및 `lpCallerName` `lpSccName` 매개 변수를 사용하면 IDE 및 소스 제어 플러그인이 이름을 교환할 수 있습니다. 이러한 이름은 단순히 여러 인스턴스를 구분하는 데 사용되거나 실제로 메뉴 또는 대화 상자에 나타날 수 있습니다.

 매개 `lpAuxPathLabel` 변수는 솔루션 파일에 저장되고 [SccOpenProject에](../extensibility/sccopenproject-function.md)대한 호출에서 소스 제어 플러그인에 전달되는 보조 프로젝트 경로를 식별하기 위해 주석으로 사용되는 문자열입니다. [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)]"SourceSafe 프로젝트:"문자열을 사용합니다. 다른 소스 제어 플러그인은 이 특정 문자열사용을 삼가야 합니다.

 매개 `lpSccCaps` 변수는 소스 제어 플러그인에 플러그인의 기능을 나타내는 비트 플래그를 저장할 수 있는 위치를 제공합니다. 기능 비트 플래그의 전체 목록은 [기능 플래그를](../extensibility/capability-flags.md)참조하십시오. 예를 들어 플러그인이 발신자가 제공한 콜백 함수에 결과를 작성하려는 경우 플러그인은 기능 비트를 SCC_CAP_TEXTOUT 설정합니다. 이렇게 하면 IDE가 버전 제어 결과에 대한 창을 만들도록 신호를 보시입니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [기능 플래그](../extensibility/capability-flags.md)
