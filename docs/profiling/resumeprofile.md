---
title: ResumeProfile | Microsoft Docs
description: ResumeProfile 메서드를 사용하여 지정된 프로파일링 수준의 Suspend/Resume 카운터를 감소시키는 방법을 알아봅니다.
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ResumeProfile
ms.assetid: 876f145b-ec07-4240-ade6-4f6e44baadce
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1b700359977e13e4664067ef62af4913d41cbabb
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98720243"
---
# <a name="resumeprofile"></a>ResumeProfile
`ResumeProfile` 메서드는 지정된 프로파일링 수준에 대한 Suspend/Resume 카운터를 감소시킵니다.

## <a name="syntax"></a>구문

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI ResumeProfile(
                       PROFILE_CONTROL_LEVEL Level,
                       unsigned int dwId);
```

#### <a name="parameters"></a>매개 변수
 `Level`

 성능 데이터 수집을 적용할 수 있는 프로필 수준을 나타냅니다. 다음 **PROFILE_CONTROL_LEVEL** 열거자는 성능 데이터 수집을 적용할 수 있는 세 가지 수준 중 하나를 나타내는 데 사용될 수 있습니다.

|열거자|설명|
|----------------|-----------------|
|PROFILE_GLOBALLEVEL|전역 수준 설정은 프로파일링 실행의 모든 프로세스와 스레드에 영향을 줍니다.|
|PROFILE_PROCESSLEVEL|프로세스 수준 설정은 지정된 프로세스의 일부인 모든 스레드에 영향을 줍니다.|
|PROFILE_THREADLEVEL|스레드 프로파일링 수준 설정은 지정된 스레드에 영향을 줍니다.|

 `dwId`

 시스템에서 생성한 프로세스 또는 스레드 식별자입니다.

## <a name="property-valuereturn-value"></a>속성 값/반환 값
 이 함수는 **PROFILE_COMMAND_STATUS** 열거형을 사용하여 성공 또는 실패를 나타냅니다. 반환 값은 다음 중 하나일 수 있습니다.

|열거자|설명|
|----------------|-----------------|
|PROFILE_ERROR_ID_NOEXIST|프로파일링 요소 ID가 없습니다.|
|PROFILE_ERROR_LEVEL_NOEXIST|지정된 프로파일링 수준이 없습니다.|
|PROFILE_ERROR_MODE_NEVER|이 함수가 호출될 때 프로파일링 모드가 NEVER로 설정되었습니다.|
|PROFILE_ERROR_NOT_YET_IMPLEMENTED|프로파일링 함수 호출, 프로파일링 수준 또는 호출과 수준의 조합이 아직 구현되지 않았습니다.|
|PROFILE_OK|호출이 성공했습니다.|

## <a name="remarks"></a>설명
 Suspend/Resume 카운터의 초기값은 0입니다. SuspendProfile에 대한 각 호출은 Suspend/Resume 카운트에 1을 추가합니다. ResumeProfile에 대한 각 호출은 1을 뺍니다.

 Suspend/Resume 카운트가 0보다 큰 경우 수준에 대한 Suspend/Resume 상태는 OFF입니다. 카운트가 0보다 작거나 같은 경우 Suspend/Resume 상태는 ON입니다.

 Start/Stop 상태와 Suspend/Resume 상태가 둘 다 ON인 경우 수준에 대한 프로파일링 상태는 ON입니다. 프로파일링될 스레드의 경우 스레드에 대한 전역, 프로세스 및 스레드 수준 상태는 모두 ON이어야 합니다.

## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>함수 정보
 헤더: *VSPerf.h* 에서 선언됨

 가져오기 라이브러리: *VSPerf.lib*

## <a name="example"></a>예
 다음 예제에서는 ResumeProfile 함수를 보여 줍니다. 예제에서는 SuspendProfile 메서드에 대한 호출이 [PROFILE_CURRENTID](../profiling/profile-currentid.md)에서 식별된 동일한 스레드 또는 프로세스에 대해 만들어졌다고 가정합니다.

```cpp
void ExerciseResumeProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the Suspend/Resume
    // count; each call to ResumeProfile subtracts 1.

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call to ResumeProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = ResumeProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("ResumeProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>참조
- [Visual Studio 프로파일러 API 참조(네이티브)](../profiling/visual-studio-profiler-api-reference-native.md)
