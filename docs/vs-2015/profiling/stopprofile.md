---
title: StopProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- StopProfile
ms.assetid: be75b03c-7af5-4abe-a54a-6ee5479ad877
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b8be45de29f379161845cc7ba8ec58d2d1bc9285
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193308"
---
# <a name="stopprofile"></a>StopProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`StopProfile` 함수는 지정된 프로파일링 수준에 대한 카운터를 0(off)으로 설정합니다.  
  
## <a name="syntax"></a>구문  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI StopProfile(  
                       PROFILE_CONTROL_LEVEL Level,   
                       unsigned int dwId);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `Level`  
  
 성능 데이터 수집을 적용할 수 있는 프로필 수준을 나타냅니다. 다음 **PROFILE_CONTROL_LEVEL** 열거자는 성능 데이터 수집을 적용할 수 있는 세 가지 수준 중 하나를 나타내는 데 사용될 수 있습니다.  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|전역 수준 설정은 프로파일링 실행의 모든 프로세스와 스레드에 영향을 줍니다.|  
|PROFILE_PROCESSLEVEL|프로세스 수준 설정은 지정된 프로세스의 일부인 모든 스레드에 영향을 줍니다.|  
|PROFILE_THREADLEVEL|스레드 프로파일링 수준 설정은 지정된 스레드에 영향을 줍니다.|  
  
 `dwId`  
  
 시스템에서 생성한 프로세스 또는 스레드 식별자입니다.  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 이 함수는 **PROFILE_COMMAND_STATUS** 열거형을 사용하여 성공 또는 실패를 나타냅니다. 반환 값은 다음 중 하나일 수 있습니다.  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE_ERROR_ID_NOEXIST|프로파일링 요소 ID가 없습니다.|  
|PROFILE_ERROR_LEVEL_NOEXIST|지정된 프로파일링 수준이 없습니다.|  
|PROFILE_ERROR_MODE_NEVER|이 함수가 호출될 때 프로파일링 모드가 NEVER로 설정되었습니다.|  
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|프로파일링 함수 호출, 프로파일링 수준 또는 호출과 수준의 조합이 아직 구현되지 않았습니다.|  
|PROFILE_OK|호출이 성공했습니다.|  
  
## <a name="remarks"></a>설명  
 StartProfile 및 StopProfile은 프로파일링 수준에 대한 Start/Stop 상태를 제어합니다. Start/Stop의 기본값은 1입니다. 레지스트리에서 초기 값을 변경할 수 있습니다. StartProfile에 대한 각 호출은 Start/Stop을 1로 설정합니다. StopProfile에 대한 각 호출은 0으로 설정합니다.  
  
 Start/Stop이 0보다 큰 경우 수준에 대한 Start/Stop 상태는 ON입니다. 0보다 작거나 같은 경우 Start/Stop 상태가 OFF입니다.  
  
 Start/Stop 상태와 Suspend/Resume 상태가 둘 다 ON인 경우 수준에 대한 프로파일링 상태는 ON입니다. 프로파일링될 스레드의 경우 스레드에 대한 전역, 프로세스 및 스레드 수준 상태는 ON이어야 합니다.  
  
## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>함수 정보  
 헤더: VSPerf.h에서 선언됨  
  
 가져오기 라이브러리: VSPerf.lib  
  
## <a name="example"></a>예제  
 다음 예제에서는 StopProfile 메서드를 보여 줍니다. 예제에서는 StartProfile 메서드에 대한 호출이 [PROFILE_CURRENTID](../profiling/profile-currentid.md)에서 식별된 동일한 스레드 또는 프로세스에 대해 만들어졌다고 가정합니다.  
  
```  
void ExerciseStopProfile()  
{  
    // StartProfile and StopProfile control the   
    // Start/Stop state for the profiling level.   
    // The default initial value of Start/Stop is 1.   
    // The initial value can be changed in the registry.   
    // Each call to StartProfile sets Start/Stop to 1;   
    // each call to StopProfile sets it to 0.   
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare enumeration to hold result of call  
    // to StopProfile.  
    PROFILE_COMMAND_STATUS profileResult;  
  
    profileResult = StopProfile(  
        PROFILE_THREADLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("StopProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, profileResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 프로파일러 API 참조 (네이티브)](../profiling/visual-studio-profiler-api-reference-native.md)
