---
title: MarkProfile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MarkProfile
ms.assetid: 54dac8c8-c8ee-4023-af27-b25466e3a6ec
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: f53b51f9e78e2cb5d327abd3a79ebf2faa3a9204
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778572"
---
# <a name="markprofile"></a>MarkProfile
`MarkProfile` 메서드는 .*vsp* 파일에 프로필 표시를 삽입합니다. 해당 표시를 삽입하려면 `MarkProfile` 함수를 포함하는 스레드에 대한 프로파일링이 ON이어야 합니다.

## <a name="syntax"></a>구문

```cpp
PROFILE_COMMAND_STATUS PROFILERAPI MarkProfile( long lMarker );
```

#### <a name="parameters"></a>매개 변수
 `lMarker`

 삽입할 표식입니다. 표식은 0보다 크거나 같아야 합니다.

## <a name="property-valuereturn-value"></a>속성 값/반환 값
 이 함수는 **PROFILE_COMMAND_STATUS** 열거형을 사용하여 성공 또는 실패를 나타냅니다. 반환 값은 다음 중 하나일 수 있습니다.

|Enumerator|Description|
|----------------|-----------------|
|MARK_ERROR_MARKER_RESERVED|매개 변수가 0보다 작거나 같습니다. 이러한 값은 예약되어 있습니다. 표시와 주석이 기록되지 않습니다.|
|MARK_ERROR_MODE_NEVER|이 함수가 호출될 때 프로파일링 모드가 NEVER로 설정되었습니다. 표시와 주석이 기록되지 않습니다.|
|MARK_ERROR_MODE_OFF|이 함수가 호출될 때 프로파일링 모드가 OFF로 설정되었습니다. 표시와 주석이 기록되지 않습니다.|
|MARK_ERROR_NO_SUPPORT|이 컨텍스트에서는 표시가 지원되지 않습니다. 표시와 주석이 기록되지 않습니다.|
|MARK_ERROR_OUTOFMEMORY|메모리에 이벤트를 기록할 수 없습니다. 표시와 주석이 기록되지 않습니다.|
|MARK_TEXTTOOLONG|문자열이 최대값인 256자를 초과합니다. 주석 문자열이 잘리고 표시와 주석이 기록됩니다.|
|MARK_OK|MARK_OK는 성공을 나타내기 위해 반환됩니다.|

## <a name="remarks"></a>설명
 MarkProfile 함수를 포함하는 스레드가 프로파일링되면 코드가 실행될 때마다 .*vsp* 파일에 표시 값이 삽입됩니다. MarkProfile을 여러 번 호출할 수 있습니다.

 프로필 표시는 범위 내에서 전역입니다. 예를 들어 한 스레드에 삽입된 프로필 표시를 사용하여 .*vsp* 파일의 스레드에 있는 데이터 세그먼트의 시작이나 끝을 표시할 수 있습니다.

 표시 및 주석을 Mark 명령 또는 API 함수(CommentMarkAtProfile, CommentMarkProfile 또는 MarkProfile)를 사용하여 삽입한 경우 표시 프로필 함수를 포함하는 스레드의 프로파일링 상태는 ON입니다.

> [!IMPORTANT]
> MarkProfile 메서드는 계측 프로파일링에서만 사용해야 합니다.

## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값
 *Microsoft.VisualStudio.Profiler.dll*

## <a name="function-information"></a>함수 정보
 헤더: *VSPerf.h*에서 선언됨

 가져오기 라이브러리: *VSPerf.lib*

## <a name="example"></a>예제
 다음 코드에서는 MarkProfile 함수를 보여 줍니다.

```cpp
void ExerciseMarkProfile()
{
    // Declare and initialize variables to pass to
    // MarkProfile.  The values of these parameters
    // are assigned based on the needs of the code;
    // and for the sake of simplicity in this example,
    // the variables are assigned arbitrary values.
    int markId = 03;

    // Declare enumeration to hold return value of
    // call to MarkProfile.
    PROFILE_COMMAND_STATUS markResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    markResult = MarkProfile(markId);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("MarkProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, markResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 프로파일러 API 참조(네이티브)](../profiling/visual-studio-profiler-api-reference-native.md)
