---
title: SccInitialize 함수 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700637"
---
# <a name="sccinitialize-function"></a>SccInitialize 함수
이 함수는 소스 제어 플러그 인을 초기화 하 고 IDE (통합 개발 환경)에 기능 및 제한을 제공 합니다.

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

진행 소스 제어 플러그 인은 여기에 컨텍스트 구조에 대 한 포인터를 놓을 수 있습니다.

 `hWnd`

진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.

 `lpCallerName`

진행 소스 제어 플러그 인을 호출 하는 프로그램의 이름입니다.

 `lpSccName`

[in, out] 소스 제어 플러그 인이 자체 이름을 지정 하는 버퍼입니다 (를 초과 하지 않음 `SCC_NAME_LEN` ).

 `lpSccCaps`

제한이 소스 제어 플러그 인의 기능 플래그를 반환 합니다.

 `lpAuxPathLabel`

[in, out] 소스 제어 플러그 인이 `lpAuxProjPath` [Sccopenproject](../extensibility/sccopenproject-function.md) 에서 반환 하는 매개 변수를 설명 하는 문자열과 [SccGetProjPath](../extensibility/sccgetprojpath-function.md) (를 초과 하지 않음)를 나타내는 버퍼 `SCC_AUXLABEL_LEN` 입니다.

 `pnCheckoutCommentLen`

제한이 체크 아웃 설명에 허용 되는 최대 길이를 반환 합니다.

 `pnCommentLen`

제한이 다른 주석에 허용 되는 최대 길이를 반환 합니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|소스 제어를 초기화 했습니다.|
|SCC_E_INITIALIZEFAILED|시스템을 초기화할 수 없습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 지정 된 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECFICERROR|일반 오류입니다. 소스 제어 시스템이 초기화 되지 않았습니다.|

## <a name="remarks"></a>설명
 IDE는 먼저 소스 제어 플러그 인을 로드할 때이 함수를 호출 합니다. IDE에서 호출자 이름과 같은 특정 정보를 플러그 인에 전달할 수 있습니다. 또한 IDE는 주석과 플러그 인의 기능에 허용 되는 최대 길이 등의 특정 정보를 다시 가져옵니다.

 는 `ppvContext` 포인터를 가리킵니다 `NULL` . 소스 제어 플러그 인은 고유한 용도에 대 한 구조체를 할당 하 고의 해당 구조에 대 한 포인터를 저장할 수 있습니다 `ppvContext` . IDE는 다른 모든 VSSCI API 함수에이 포인터를 전달 하 여 플러그 인이 전역 저장소를 사용 하 고 플러그 인의 여러 인스턴스를 지원 하지 않고도 컨텍스트 정보를 사용할 수 있도록 합니다. [SccUninitialize](../extensibility/sccuninitialize-function.md) 가 호출 되 면이 구조를 할당 취소 해야 합니다.

 `lpCallerName`및 `lpSccName` 매개 변수를 사용 하면 IDE와 소스 제어 플러그 인에서 이름을 교환할 수 있습니다. 이러한 이름은 여러 인스턴스를 구분 하는 데만 사용 되거나 실제로 메뉴 또는 대화 상자에 표시 될 수 있습니다.

 `lpAuxPathLabel`매개 변수는 솔루션 파일에 저장 되 고 [Sccopenproject](../extensibility/sccopenproject-function.md)호출에서 소스 제어 플러그 인에 전달 되는 보조 프로젝트 경로를 식별 하기 위해 주석으로 사용 되는 문자열입니다. [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] "SourceSafe 프로젝트:" 문자열을 사용 합니다. 다른 소스 제어 플러그 인은이 특정 문자열을 사용 하지 않도록 합니다.

 `lpSccCaps`매개 변수는 플러그 인의 기능을 나타내는 bitflag를 저장할 원본 제어 플러그 인을 제공 합니다. 기능 비트 플래그의 전체 목록은 [기능 플래그](../extensibility/capability-flags.md)를 참조 하세요. 예를 들어 플러그 인에서 호출자가 제공한 콜백 함수에 결과를 쓸 계획인 경우 플러그 인은 기능 비트 SCC_CAP_TEXTOUT 설정 합니다. 그러면 IDE에서 버전 제어 결과에 대 한 창을 만들도록 신호를 보낼 수 있습니다.

## <a name="see-also"></a>추가 정보
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [기능 플래그](../extensibility/capability-flags.md)
