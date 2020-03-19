---
title: PROFILE_CURRENTID | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- PROFILE_CURRENTID
ms.assetid: 55ccf665-a05e-48c3-adf7-7714c0a9aaef
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 63b44bee152acbf5529acfcadaa49a19e9feb52b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "74778364"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID는 NameProfile, StartProfile, StopProfile, SuspendProfile 및 ResumeProfile 함수에 대한 호출에서 스레드 ID 또는 프로세스 ID에 대한 의사(pseudo) 토큰을 반환합니다. 구체적으로 지정된 것보다 현재 스레드 또는 프로세스에서 작동하는 함수를 발생하는 데 사용합니다.

## <a name="example"></a>예제
 PROFILE_CURRENTID는 *VSPerf.h*에서 다음으로 정의됩니다.

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example"></a>예제
 다음은 PROFILE_CURRENTID에 대한 예입니다. 예제는 [StartProfile](../profiling/startprofile.md) 함수에 대한 호출에서 현재 스레드를 식별하는 매개 변수로 PROFILE_CURRENTID를 사용합니다.

```cpp
void ExerciseProfileCurrentID()
{
    // Declare ProfileOperationResult enumeration
    // to hold return value of a call to StartProfile.
    PROFILE_COMMAND_STATUS profileResult;

    // Variables used to print output.
    HRESULT hResult;
    TCHAR tchBuffer[256];

    profileResult = StartProfile(
        PROFILE_GLOBALLEVEL,
        PROFILE_CURRENTID);

    // Format and print result.
    LPCTSTR pszFormat = TEXT("%s %d.\0");
    TCHAR* pszTxt = TEXT("StartProfile returned");
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,
        pszTxt, profileResult);

#ifdef DEBUG
    OutputDebugString(tchBuffer);
#endif
}
```

## <a name="see-also"></a>참고 항목
- [Visual Studio 프로파일러 API 참조(네이티브)](../profiling/visual-studio-profiler-api-reference-native.md)
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)
