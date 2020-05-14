---
title: SccGet 기능 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c2d69308d2f569fc2e0d72dcf64c762687955d4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700897"
---
# <a name="sccget-function"></a>SccGet 함수
이 함수는 편집할 수 있지만 편집할 수 없는 편집을 위해 하나 이상의 파일의 복사본을 검색합니다. 대부분의 시스템에서 파일은 읽기 전용으로 태그가 지정됩니다.

## <a name="syntax"></a>구문

```cpp
SCCRTN SccGet(
   LPVOID    pvContext,
   HWND      hWnd,
   LONG      nFiles,
   LPCSTR*   lpFileNames,
   LONG      fOptions,
   LPCMDOPTS pvOptions
);
```

### <a name="parameters"></a>매개 변수
 pvContext

【인】 소스 제어 플러그인의 컨텍스트 구조입니다.

 Hwnd

【인】 소스 제어 플러그인이 제공하는 모든 대화 상자에 대한 상위로 사용할 수 있는 IDE 창에 대한 핸들입니다.

 n파일

【인】 배열에 지정된 파일 `lpFileNames` 수입니다.

 lpFile 이름

【인】 검색할 파일의 정규화된 이름의 배열입니다.

 f옵션

【인】 명령 플래그`SCC_GET_ALL` `SCC_GET_RECURSIVE`(, ).

 pv옵션

【인】 소스 제어 플러그인 관련 옵션.

## <a name="return-value"></a>반환 값
 이 함수의 소스 제어 플러그인 구현은 다음 값 중 하나를 반환해야 합니다.

|값|Description|
|-----------|-----------------|
|SCC_OK|작업의 성공.|
|SCC_E_FILENOTCONTROLLED|파일이 소스 제어를 받지 않습니다.|
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템은 이 작업을 지원하지 않습니다.|
|SCC_E_FILEISCHECKEDOUT|사용자가 현재 체크 아웃한 파일을 얻을 수 없습니다.|
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 소스 제어 시스템에 액세스하는 데 문제가 있었습니다. 다시 시도하는 것이 좋습니다.|
|SCC_E_NOSPECIFIEDVERSION|잘못된 버전 또는 날짜/시간을 지정했습니다.|
|SCC_E_NONSPECIFICERROR|비특이적 오류; 파일이 동기화되지 않았습니다.|
|SCC_I_OPERATIONCANCELED|작업이 완료되기 전에 취소되었습니다.|
|SCC_E_NOTAUTHORIZED|사용자가 이 작업을 수행할 권한이 없습니다.|

## <a name="remarks"></a>설명
 이 함수는 검색할 파일의 개수 및 이름 배열로 호출됩니다. IDE가 플래그를 `SCC_GET_ALL`통과하면 해당 `lpFileNames` 항목이 파일이 아니라 디렉터리이며 지정된 디렉터리에서 소스 제어하에 있는 모든 파일을 검색해야 한다는 의미입니다.

 플래그를 `SCC_GET_ALL` `SCC_GET_RECURSIVE` 플래그와 결합하여 지정된 디렉터리및 모든 하위 디렉토리의 모든 파일을 검색할 수 있습니다.

> [!NOTE]
> `SCC_GET_RECURSIVE`없이 전달해서는 `SCC_GET_ALL`안됩니다. 또한 디렉터리 *C:\A와* *C:\A\B가* 모두 재귀 get에 전달되는 경우 *C:\A\B와* 모든 하위 디렉터리는 실제로 두 번 검색됩니다. 소스 제어 플러그인이 아닌 IDE의 책임이며 이와 같은 중복 항목이 어레이에서 유지되도록 합니다.

 마지막으로 소스 제어 플러그인이 초기화에 `SCC_CAP_GET_NOUI` 플래그를 지정하여 Get 명령에 대한 사용자 인터페이스가 없는 경우에도 이 함수는 IDE에서 파일을 검색하도록 호출할 수 있습니다. 플래그는 단순히 IDE가 Get 메뉴 항목을 표시하지 않으며 플러그인이 UI를 제공하지 않을 것으로 예상된다는 것을 의미합니다.

## <a name="rename-files-and-sccget"></a>파일 이름 바꾸기 및 SccGet
 상황: 사용자가 *a.txt와*같은 파일을 체크 아웃하고 수정합니다. *a.txt를* 체크 인하기 전에 두 번째 사용자는 소스 제어 데이터베이스에서 *a.txt를* *b.txt로* 이름을 바꿉니다. *b.txt* 첫 번째 사용자는 두 번째 사용자가 변경한 내용을 원하므로 첫 번째 사용자는 *a.txt* 파일의 로컬 버전 이름을 *b.txt로* 바꾸고 파일을 가져옵니다. 그러나 버전 번호를 추적하는 로컬 캐시는 여전히 *a.txt의* 첫 번째 버전이 로컬에 저장되어 있으므로 소스 제어가 차이를 해결할 수 없다고 생각합니다.

 소스 제어 버전의 로컬 캐시가 원본 제어 데이터베이스와 동기화되지 않는 경우 두 가지 방법으로 이 문제를 해결할 수 있습니다.

1. 현재 체크 아웃된 소스 제어 데이터베이스의 파일 이름을 바꾸는 것은 허용되지 않습니다.

2. "이전 삭제"와 "새 새 추가"에 해당하는 작업을 수행합니다. 다음 알고리즘은 이 작업을 수행하는 한 가지 방법입니다.

    1. 소스 제어 데이터베이스에서 *a.txt에서 b.txt로* 의 이름을 바꾸는 방법에 대해 알아보려면 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 함수를 호출합니다. *b.txt*

    2. 로컬 *a.txt의* 이름을 *b.txt로*바꿉니다.

    3. `SccGet` *a.txt 및 b.txt* 모두에 대한 함수를 *호출합니다.*

    4. *a.txt는* 소스 제어 데이터베이스에 없기 때문에 로컬 버전 캐시는 누락된 *a.txt* 버전 정보를 제거합니다.

    5. 체크 아웃중인 *b.txt* 파일은 로컬 *b.txt* 파일의 내용과 병합됩니다.

    6. 이제 업데이트된 *b.txt* 파일을 체크 인할 수 있습니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인 API 기능](../extensibility/source-control-plug-in-api-functions.md)
- [특정 명령에서 사용되는 비트 플래그](../extensibility/bitflags-used-by-specific-commands.md)
