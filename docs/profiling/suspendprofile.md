---
title: SuspendProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SuspendProfile
ms.assetid: 7c8de6e6-bb88-4353-92c3-ce7290310d61
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 1eb0d0f41b17c4f23c3898b044ad49182d47aae0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778195"
---
# <a name="suspendprofile"></a>SuspendProfile
`SuspendProfile` 메서드는 지정된 프로파일링 수준에 대한 Suspend/Resume 카운터를 증가시킵니다.

## <a name="syntax"></a>구문

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI SuspendProfile(
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
 Suspend/Resume 카운터의 초기값은 0입니다. SuspendProfile에 대한 각 호출은 Suspend/Resume 카운트에 1을 추가합니다. ResumeProfile에 대한 각 호출은 1을 뺍니다.

 Suspend/Resume 카운트가 0보다 큰 경우 수준에 대한 Suspend/Resume 상태는 OFF입니다. 카운트가 0보다 작거나 같은 경우 Suspend/Resume 상태는 ON입니다.

 Start/Stop 상태와 Suspend/Resume 상태가 둘 다 ON인 경우 수준에 대한 프로파일링 상태는 ON입니다. 프로파일링될 스레드의 경우 스레드에 대한 전역, 프로세스 및 스레드 수준 상태는 모두 ON이어야 합니다.

## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>함수 정보
 헤더: *VSPerf.h*에서 선언됨

 가져오기 라이브러리: *VSPerf.lib*

## <a name="example"></a>예제
 다음 예제에서는 SuspendProfile 메서드를 보여 줍니다. 이 예에서는 StartProfile에 대한 이전 호출이 [PROFILE_CURRENTID](../profiling/profile-currentid.md)에 의해 식별된 프로세스 또는 스레드에 대해 만들어졌다고 가정합니다.

```cpp
void ExerciseSuspendProfile()
{
    // The initial value of the Suspend/Resume counter is 0.
    // Each call to SuspendProfile adds 1 to the
    // Suspend/Resume count; each call
    // to ResumeProfile subtracts 1.

    // Variables used to print output
    HRESULT hResult;
    TCHAR tchBuffer[256];

    // Declare enumeration to hold result of call
    // to SuspendProfile
    PROFILE_COMMAND_STATUS profileResult;

    profileResult = SuspendProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("SuspendProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 프로파일러 API 참조(네이티브)](../profiling/visual-studio-profiler-api-reference-native.md)
