---
title: SccDiff 함수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccDiff
helpviewer_keywords:
- SccDiff function
ms.assetid: d49bc8c5-f631-4153-9d3c-feb3564da305
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: aa5ea0a269cdbfe678328dc652b4177bdc667b99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841330"
---
# <a name="sccdiff-function"></a>SccDiff 함수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 함수는 소스 제어 시스템에서 현재 파일 (로컬 디스크의)과 마지막으로 체크 인 한 버전 간의 차이점을 표시 하거나 선택적으로 확인 합니다.  
  
## <a name="syntax"></a>구문  
  
```cpp#  
SCCRTN SccDiff(  
   LPVOID    pvContext,  
   HWND      hWnd,  
   LPCSTR    lpFileName,  
   LONG      fOptions,  
   LPCMDOPTS pvOptions  
);  
```  
  
#### <a name="parameters"></a>매개 변수  
 pvContext  
 진행 소스 제어 플러그 인 컨텍스트 구조입니다.  
  
 hWnd  
 진행 소스 제어 플러그 인이 제공 하는 대화 상자의 부모로 사용할 수 있는 IDE 창에 대 한 핸들입니다.  
  
 lpFileName  
 진행 차이를 요청 하는 파일 이름입니다.  
  
 fOptions  
 진행 명령 플래그입니다. 자세한 내용은 설명 부분을 참조 하십시오.  
  
 pvOptions  
 진행 원본 제어 플러그 인 관련 옵션입니다.  
  
## <a name="return-value"></a>반환 값  
 이 함수의 소스 제어 플러그 인 구현은 다음 값 중 하나를 반환 해야 합니다.  
  
|값|Description|  
|-----------|-----------------|  
|SCC_OK|작업 복사본과 서버 버전이 동일 합니다.|  
|SCC_I_FILESDIFFERS|작업 복사본이 소스 제어에서 사용 하는 버전과 다릅니다.|  
|SCC_I_RELOADFILE|파일이 나 프로젝트를 다시 로드 해야 합니다.|  
|SCC_E_FILENOTCONTROLLED|파일이 소스 제어에 있지 않습니다.|  
|SCC_E_NOTAUTHORIZED|사용자가이 작업을 수행할 수 없습니다.|  
|SCC_E_ACCESSFAILURE|네트워크 또는 경합 문제로 인해 원본 제어 시스템에 액세스 하는 동안 문제가 발생 했습니다. 다시 시도 하는 것이 좋습니다.|  
|SCC_E_NONSPECIFICERROR|일반 오류입니다. 파일의 차이를 얻지 못했습니다.|  
|SCC_E_FILENOTEXIST|로컬 파일을 찾을 수 없습니다.|  
  
## <a name="remarks"></a>설명  
 이 함수는 두 가지 용도로 사용 됩니다. 기본적으로 파일에 대 한 변경 내용 목록을 표시 합니다. 소스 제어 플러그 인은 사용자가 선택 하는 모든 형식으로 자체 창을 열어 디스크의 사용자 파일과 소스 제어에 있는 파일의 최신 버전 간 차이를 표시 합니다.  
  
 또는 파일이 변경 되었는지 여부만 확인 해야 할 수 있습니다. 예를 들어, IDE는 사용자에 게 알리지 않고 파일을 체크 아웃 하는 것이 안전한 지 여부를 확인 해야 할 수 있습니다. 이 경우 IDE는 플래그를 전달 합니다 `SCC_DIFF_CONTENTS` . 소스 제어 플러그 인은 원본 제어 파일에 대 한 디스크의 파일 (바이트)을 확인 하 고, 사용자에 게 아무것도 표시 하지 않고 두 파일이 다른 지를 나타내는 값을 반환 해야 합니다.  
  
 성능 최적화를 위해 소스 제어 플러그 인은에 의해 호출 되는 바이트 단위 비교 대신 체크섬 또는 타임 스탬프를 기반으로 하는 대체를 사용할 수 있습니다 `SCC_DIFF_CONTENTS` . 이러한 종류의 비교는 분명히 빠르지만 안정성이 떨어집니다. 모든 소스 제어 시스템에서 이러한 대체 비교 메서드를 지원할 수 있는 것은 아니므로 플러그 인은 내용 비교로 대체 해야 할 수 있습니다. 모든 소스 제어 플러그 인은 최소한 콘텐츠 비교를 지원 해야 합니다.  
  
> [!NOTE]
> 빠른 차이 플래그는 함께 사용할 수 없습니다. 플래그를 전달 하는 것은 유효 하지 않지만, 동시에 둘 이상의를 전달 하는 것은 유효 하지 않습니다. `SCC_DIFF_QUICK_DIFF`모든 플래그를 조합 하는 마스크로,를 테스트 하는 데 사용할 수 있지만 매개 변수로 전달 되어서는 안 됩니다.  
  
|`fOption`|의미|  
|---------------|-------------|  
|SCC_DIFF_IGNORECASE|대/소문자를 구분 하지 않는 비교 (빠른 또는 시각적 차이에 사용 될 수 있음)|  
|SCC_DIFF_IGNORESPACE|공백을 무시 합니다 (빠른 또는 시각적 차이에 사용 될 수 있음).|  
|SCC_DIFF_QD_CONTENTS|바이트 단위로 파일을 자동으로 비교 합니다.|  
|SCC_DIFF_QD_CHECKSUM|지원 되는 경우 체크섬을 통해 파일을 자동으로 비교 합니다. 지원 되지 않는 경우는 내용 비교로 대체 됩니다.|  
|SCC_DIFF_QD_TIME|지원 될 때 타임 스탬프를 통해 파일을 자동으로 비교 합니다. 지원 되지 않는 경우는 내용 비교로 대체 됩니다.|  
  
## <a name="see-also"></a>참고 항목  
 [소스 제어 플러그 인 API 함수](../extensibility/source-control-plug-in-api-functions.md)
