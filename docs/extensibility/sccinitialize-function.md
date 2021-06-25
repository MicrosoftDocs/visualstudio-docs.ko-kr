---
description: 이 함수는 소스 제어 플러그 인을 초기화하고 IDE(통합 개발 환경)에 대한 기능 및 제한을 제공합니다.
title: SccInitialize 함수 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccInitialize
helpviewer_keywords:
- SccInitialize function
ms.assetid: 5bc0d28b-2c68-4d43-9e51-541506a8f76e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 633e8909febd758df455a9375f735a93e3407c77
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902529"
---
# <a name="sccinitialize-function"></a>SccInitialize 함수
이 함수는 소스 제어 플러그 인을 초기화하고 IDE(통합 개발 환경)에 대한 기능 및 제한을 제공합니다.

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

[in] 소스 제어 플러그 인은 여기에 컨텍스트 구조에 대한 포인터를 배치할 수 있습니다.

 `hWnd`

[in] 소스 제어 플러그 인이 제공하는 모든 대화 상자의 부모로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 `lpCallerName`

[in] 소스 제어 플러그 인을 호출하는 프로그램의 이름입니다.

 `lpSccName`

[in, out] 소스 제어 플러그 인이 자체 이름을 넣는 버퍼입니다(를 초과하지 `SCC_NAME_LEN` 않음).

 `lpSccCaps`

[out] 소스 제어 플러그 인의 기능 플래그를 반환합니다.

 `lpAuxPathLabel`

[in, out] 소스 제어 플러그 인이 `lpAuxProjPath` [SccOpenProject 및 SccGetProjPath에서](../extensibility/sccopenproject-function.md) 반환된 매개 변수를 설명하는 문자열을 넣는 버퍼입니다(를 초과하지 [](../extensibility/sccgetprojpath-function.md) `SCC_AUXLABEL_LEN` 않음).

 `pnCheckoutCommentLen`

[out] 체크 아웃 주석에 허용되는 최대 길이를 반환합니다.

 `pnCommentLen`

[out] 다른 주석에 대해 허용되는 최대 길이를 반환합니다.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|설명|
|-----------|-----------------|
|SCC_OK|소스 제어 초기화에 성공했습니다.|
|SCC_E_INITIALIZEFAILED|시스템을 초기화할 수 없습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 지정된 작업을 수행할 수 없습니다.|
|SCC_E_NONSPECFICERROR|지정되지 않은 오류; 소스 제어 시스템이 초기화되지 않았습니다.|

## <a name="remarks"></a>설명
 IDE는 소스 제어 플러그 인을 처음 로드할 때 이 함수를 호출합니다. 이를 통해 IDE는 호출자 이름과 같은 특정 정보를 플러그 인에 전달할 수 있습니다. 또한 IDE는 주석에 허용되는 최대 길이 및 플러그 인 기능과 같은 특정 정보를 다시 가져옵니다.

 `ppvContext`포인터를 가리키는 `NULL` 입니다. 소스 제어 플러그 인은 자체 사용을 위해 구조체를 할당하고 해당 구조체에 대한 포인터를 에 저장할 수 `ppvContext` 있습니다. IDE는 다른 모든 VSSCI API 함수에 이 포인터를 전달하여 플러그 인이 전역 스토리지에 의존하지 않고도 컨텍스트 정보를 사용할 수 있도록 하고 플러그 인의 여러 인스턴스를 지원할 수 있도록 합니다. 이 구조체는 [SccUninitialize가](../extensibility/sccuninitialize-function.md) 호출될 때 할당을 미지정해야 합니다.

 `lpCallerName`및 `lpSccName` 매개 변수를 사용하면 IDE 및 소스 제어 플러그 인에서 이름을 교환할 수 있습니다. 이러한 이름은 단순히 여러 인스턴스를 구분하는 데 사용하거나 메뉴 또는 대화 상자에 실제로 표시될 수 있습니다.

 `lpAuxPathLabel`매개 변수는 솔루션 파일에 저장되고 [SccOpenProject](../extensibility/sccopenproject-function.md)호출에서 소스 제어 플러그 인에 전달되는 보조 프로젝트 경로를 식별하기 위해 주석으로 사용되는 문자열입니다. [!INCLUDE[vsvss](../extensibility/includes/vsvss_md.md)] 는 문자열 "SourceSafe Project:"를 사용합니다. 다른 소스 제어 플러그 인은 이 특정 문자열을 사용하지 않도록 해야 합니다.

 `lpSccCaps`매개 변수는 소스 제어 플러그 인에 플러그 인의 기능을 나타내는 비트 플래그를 저장할 위치를 제공합니다. (기능 비트 플래그의 전체 목록은 기능 [플래그를](../extensibility/capability-flags.md)참조하세요.) 예를 들어 플러그 인이 호출자가 제공한 콜백 함수에 결과를 쓰려는 경우 플러그 인은 기능 비트 SCC_CAP_TEXTOUT 설정합니다. 그러면 버전 제어 결과에 대한 창을 만들도록 IDE에 알릴 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
- [SccUninitialize](../extensibility/sccuninitialize-function.md)
- [SccOpenProject](../extensibility/sccopenproject-function.md)
- [기능 플래그](../extensibility/capability-flags.md)
