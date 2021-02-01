---
title: PROFILE_CURRENTID | Microsoft Docs
description: PROFILE_CURRENTID를 사용하여 별도로 지정된 스레드나 프로세스가 아니라 현재 스레드 또는 프로세스에서 함수를 작동시키는 방법을 알아봅니다.
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
ms.openlocfilehash: 5171753ff8ea6722cf1d97e155352e3899fb5562
ms.sourcegitcommit: 18729d7c99c999865cc2defb17d3d956eb3fe35c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/23/2021
ms.locfileid: "98719489"
---
# <a name="profile_currentid"></a>PROFILE_CURRENTID
PROFILE_CURRENTID는 NameProfile, StartProfile, StopProfile, SuspendProfile 및 ResumeProfile 함수에 대한 호출에서 스레드 ID 또는 프로세스 ID에 대한 의사(pseudo) 토큰을 반환합니다. 구체적으로 지정된 것보다 현재 스레드 또는 프로세스에서 작동하는 함수를 발생하는 데 사용합니다.

## <a name="example-1"></a>예제 1
 PROFILE_CURRENTID는 *VSPerf.h* 에서 다음으로 정의됩니다.

```cpp
static const unsigned int PROFILE_CURRENTID = (unsigned int)-1;
```

## <a name="example-2"></a>예 2
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

## <a name="see-also"></a>참조
- [Visual Studio 프로파일러 API 참조(네이티브)](../profiling/visual-studio-profiler-api-reference-native.md)
- [NameProfile](../profiling/nameprofile.md)
- [ResumeProfile](../profiling/resumeprofile.md)
- [StartProfile](../profiling/startprofile.md)
- [StopProfile](../profiling/stopprofile.md)
- [SuspendProfile](../profiling/suspendprofile.md)
