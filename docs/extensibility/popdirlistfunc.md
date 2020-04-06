---
title: 팝디를리스트푼크 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- POPLISTFUNC
helpviewer_keywords:
- POPDIRLISTFUNC callback function
ms.assetid: 0ee90fd2-5467-4154-ab4c-7eb02ac3a14c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 52a0c16af0e142bda8527c5244a22e0830ced9e0
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702074"
---
# <a name="popdirlistfunc"></a>POPDIRLISTFUNC
이 기능은 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 함수에 주어진 콜백 함수로 디렉터리 컬렉션을 업데이트하고 (선택적으로) 파일 이름을 사용하여 소스 제어하에 있는 파일을 찾습니다.

 콜백은 `POPDIRLISTFUNC` 실제로 소스 제어하에 있는 해당 디렉터리 및 파일 `SccPopulateDirList` 이름(함수에 지정된 목록)에 대해서만 호출해야 합니다.

## <a name="signature"></a>서명

```cpp
typedef BOOL (*POPDIRLISTFUNC)(
   LPVOID pvCallerData,
   BOOL bFolder,
   LPCSTR lpDirectoryOrFileName
);
```

## <a name="parameters"></a>매개 변수
 pvCallerData

【인】 [SccPopulateDirList에](../extensibility/sccpopulatedirlist-function.md)주어진 사용자 값 .

 b폴더

【인】 `TRUE` 의 `lpDirectoryOrFileName` 이름이 디렉토리인 경우; 그렇지 않으면 이름은 파일 이름입니다.

 lpDirectoryOrFile

【인】 소스 코드 제어하에 있는 디렉터리 또는 파일 이름에 대한 전체 로컬 경로입니다.

## <a name="return-value"></a>반환 값
 IDE는 적절한 오류 코드를 반환합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|처리를 계속합니다.|
|SCC_I_OPERATIONCANCELED|처리를 중지합니다.|
|SCC_E_xxx|적절한 소스 제어 오류는 처리를 중지해야 합니다.|

## <a name="remarks"></a>설명
 함수의 `fOptions` 매개 변수에 `SCC_PDL_INCLUDEFILES` 플래그가 포함된 경우 목록에 파일 이름과 디렉터리 이름이 포함될 수 있습니다. `SccPopulateDirList`

## <a name="see-also"></a>참조
- [IDE에서 구현한 콜백 함수](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)
- [오류 코드](../extensibility/error-codes.md)
