---
title: SccGet 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGet
helpviewer_keywords:
- SccGet function
ms.assetid: 09a18bd2-b788-411a-9da6-067d806e46f6
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 2a5d5065ca427f0319174aa59e6b87d356816d4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841722"
---
# <a name="sccget-function"></a>SccGet 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 보기 및 컴파일을 위해 하나 이상의 파일 복사본을 검색 하지만 편집할 수는 없습니다. 대부분의 시스템에서 파일은 읽기 전용으로 태그가 지정 됩니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccGet(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LONG      nFiles,  
   LPCSTR*   lpFileNames,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 진행 소스 제어 플러그 인의 컨텍스트 구조입니다.  
  
 hWnd  
 진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.  
  
 n  
 진행 배열에 지정 된 파일 수 `lpFileNames` 입니다.  
  
 lpFileNames 이름  
 진행 검색할 파일의 정규화 된 이름 배열입니다.  
  
 fOptions  
 진행 명령 플래그 ( `SCC_GET_ALL` , `SCC_GET_RECURSIVE` ).  
  
 pvOptions  
 진행 원본 제어 플러그 인 관련 옵션입니다.  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|가져오기 작업의 성공입니다.|  
|SCC_E_FILENOTCONTROLLED|파일이 소스 제어에 있지 않습니다.|  
|SCC_E_OPNOTSUPPORTED|소스 제어 시스템에서이 작업을 지원 하지 않습니다.|  
|SCC_E_FILEISCHECKEDOUT|사용자가 현재 체크 아웃 한 파일을 가져올 수 없습니다.|  
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|  
|SCC_E_NOSPECIFIEDVERSION|가 잘못 된 버전 또는 날짜/시간을 지정 했습니다.|  
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 파일이 동기화 되지 않았습니다.|  
|SCC_I_OPERATIONCANCELED|작업이 완료 되기 전에 취소 되었습니다.|  
|SCC_E_NOTAUTHORIZED|사용자에 게이 작업을 수행할 수 있는 권한이 없습니다.|  
  
## <a name="remarks"></a>설명  
 이 함수는 검색할 파일의 수 및 이름 배열을 사용 하 여 호출 됩니다. IDE에서 플래그를 전달 하는 경우 `SCC_GET_ALL` 의 항목은 `lpFileNames` 파일이 아니라 디렉터리 이며 지정 된 디렉터리에서 소스 제어에 있는 모든 파일을 검색 해야 함을 의미 합니다.  
  
 `SCC_GET_ALL`플래그는 플래그와 함께 사용 `SCC_GET_RECURSIVE` 하 여 지정 된 디렉터리 및 모든 하위 디렉터리의 모든 파일을 검색할 수 있습니다.  
  
> [!NOTE]
> `SCC_GET_RECURSIVE` 는 없이 전달 되어서는 안 됩니다 `SCC_GET_ALL` . 또한 C:\A 및 C:\A\B 디렉터리가 모두 재귀적 get에 전달 되 면 C:\A\B와 모든 하위 디렉터리가 실제로 두 번 검색 됩니다. 이는 소스 제어 플러그 인이 아닌 IDE의 책임 이며, 이와 같은 중복이 배열에서 제외 되도록 합니다.  
  
 마지막으로, 소스 제어 플러그 인 `SCC_CAP_GET_NOUI` 이 초기화 시 플래그를 지정 하 여 Get 명령의 사용자 인터페이스가 없음을 나타내는 경우에도 IDE에서이 함수를 호출 하 여 파일을 검색할 수 있습니다. 플래그는 IDE에 Get 메뉴 항목이 표시 되지 않고 플러그 인에서 UI를 제공할 것으로 예상 되지 않는다는 것을 의미 합니다.  
  
## <a name="renaming-and-sccget"></a>이름 바꾸기 및 SccGet  
 상황: 사용자가 파일 (예: a.txt)을 체크 아웃 하 고 수정 합니다. a.txt를 체크 인하기 전에 두 번째 사용자가 소스 제어 데이터베이스에서 b.txt a.txt의 이름을 바꾸고 b.txt를 체크 아웃 한 다음 파일을 수정 하 고에서 파일을 확인 합니다. 첫 번째 사용자는 두 번째 사용자가 변경한 내용을 확인 하 여 첫 번째 사용자가 a.txt 파일의 로컬 버전을 b.txt로 바꾸고 파일에 대해 get을 수행 하도록 합니다. 그러나 버전 번호를 추적 하는 로컬 캐시는 a.txt의 첫 번째 버전을 로컬에 저장 하는 것으로 간주 하므로 소스 제어에서 차이점을 해결할 수 없습니다.  
  
 소스 제어 버전의 로컬 캐시가 원본 제어 데이터베이스와 동기화 되지 않는이 상황을 해결 하는 방법에는 두 가지가 있습니다.  
  
1. 현재 체크 아웃 된 소스 제어 데이터베이스에서 파일의 이름을 바꿀 수 없습니다.  
  
2. "기존 항목 삭제"와 "새로 추가"에 해당 하는 작업을 수행 합니다. 다음 알고리즘은이를 수행 하는 한 가지 방법입니다.  
  
    1. [Sccquerychanges](../extensibility/sccquerychanges-function.md) 함수를 호출 하 여 원본 제어 데이터베이스에서 b.txt a.txt 이름 바꾸기에 대해 알아봅니다.  
  
    2. 로컬 a.txt의 이름을 b.txt로 바꿉니다.  
  
    3. `SccGet`a.txt와 b.txt 모두에 대해 함수를 호출 합니다.  
  
    4. a.txt 원본 제어 데이터베이스에 없으므로 로컬 버전 캐시가 누락 된 a.txt 버전 정보를 제거 합니다.  
  
    5. 체크 아웃 중인 b.txt 파일은 로컬 b.txt 파일의 내용과 병합 됩니다.  
  
    6. 이제 업데이트 된 b.txt 파일을 체크 인할 수 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)   
 [특정 명령에 사용되는 Bitflag](../extensibility/bitflags-used-by-specific-commands.md)
