---
title: CommentMarkAtProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- CommentMarkAtProfile
- CommentMarkAtProfileA
ms.assetid: 04294ca3-bf9c-4c76-86f1-898c2140de27
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 36ebd4a2cd130d63b030e80696dbdde7ff179706
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85531523"
---
# <a name="commentmarkatprofile"></a>CommentMarkAtProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`CommentMarkAtProfile` 메서드는 .vsp 파일에 타임스탬프 값, 숫자 기호 및 설명 문자열을 삽입합니다. 외부 이벤트를 동기화하는 데 타임스탬프 값을 사용할 수 있습니다. 삽입될 표시 및 주석의 경우 CommentMarkAtProfile 함수가 포함된 스레드에 대한 프로파일링이 ON이어야 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI CommentMarkAtProfile (  
                                   __int64 dnTimestamp,  
                                   long lMarker,  
                                   LPCTSTR szComment);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `dnTimestamp`  
  
 타임스탬프 값을 나타내는 64비트 정수입니다.  
  
 `lMarker`  
  
 삽입할 숫자 표식입니다. 표식은 0보다 크거나 같아야 합니다.  
  
 `szComment`  
  
 삽입할 텍스트 문자열에 대한 포인터입니다. 문자열은 NULL 종결자를 포함하여 256자 이하여야 합니다.  
  
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
 표시 및 주석을 Mark 명령 또는 API 함수(CommentMarkAtProfile, CommentMarkProfile 또는 MarkProfile)를 사용하여 삽입한 경우 표시 프로필 함수를 포함하는 스레드의 프로파일링 상태는 ON입니다. 프로필 표시는 범위 내에서 전역입니다. 예를 들어 한 스레드에 삽입된 프로필 표시를 사용하여 .vsp 파일의 스레드에 있는 데이터 세그먼트의 시작이나 끝을 표시할 수 있습니다.  
  
> [!IMPORTANT]
> CommentMarkAtProfile 메서드는 계측에서만 사용해야 합니다.  
  
## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>함수 정보  
  
|항목|값|  
|-|-|  
|**머리글**|VSPerf.h 포함|  
|**라이브러리**|VSPerf.lib 사용|  
|**유니코드**|CommentMarkAtProfileW(유니코드) 및 CommentMarkAtProfileA(ANSI)로 구현됩니다.|  
  
## <a name="example"></a>예제  
 다음 코드는 CommentMarkAtProfile 일반 함수 호출의 사용을 보여 줍니다. 예제에서는 코드에서 ANSI 사용 함수를 호출할지 여부를 결정하도록 Win32 문자열 매크로 및 ANSI에 대한 컴파일러 설정의 사용을 가정합니다.  
  
```  
void ExerciseCommentMarkAtProfile(void)  
{  
    // Declare and initalize variables to pass to   
    // CommentMarkAtProfile.  The values of these   
    // parameters are assigned based on the needs   
    // of the code; and for the sake of simplicity  
    // in this example, the variables are assigned  
    // arbitrary values.  
    int64 timeStamp = 0x1111;  
    long markId = 01;  
    TCHAR * markText = TEXT("Exercising CommentMarkAtProfile...");  
  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Declare MarkOperationResult Enumerator.    
    // Holds return value from call to CommentMarkAtProfile.  
    PROFILE_COMMAND_STATUS markResult;  
  
    markResult = CommentMarkAtProfile(  
        timeStamp,  
        markId,  
        markText);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("CommentMarkAtProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
    pszTxt, markResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 프로파일러 API 참조 (네이티브)](../profiling/visual-studio-profiler-api-reference-native.md)
