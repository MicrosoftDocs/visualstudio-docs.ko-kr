---
title: NameProfile | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- NameProfile
- NameProfileA
ms.assetid: 1bb05441-c4ff-4323-9fef-f3924fba4430
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7cac308de96c3edc2dfe5c7577b0bee8077bf9e7
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85548441"
---
# <a name="nameprofile"></a>NameProfile
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`NameProfile` 함수는 지정된 프로세스 또는 스레드에 문자열을 할당합니다.  
  
 NameProfile API는 계측 프로파일링에 사용할 수 있습니다. NameProfile API는 샘플링 프로파일링에 대해 지원되지 않습니다.  
  
## <a name="syntax"></a>구문  
  
```  
PROFILE_COMMAND_STATUS PROFILERAPI NameProfile(  
                                   LPCTSTR pszName,   
                                   PROFILE_CONTROL_LEVEL Level,  
                                   unsigned int dwId);  
```  
  
#### <a name="parameters"></a>매개 변수  
 `pszName`  
  
 프로파일링 요소의 이름입니다. 다음의 경우 이름이 잘못되었습니다(NameProfileA에서 NAME_ERROR_INVALID_NAME 반환).  
  
- NameProfileA로 전달된 포인터가 NULL 값인 경우  
  
- pszName의 문자열 데이터가 숫자로 시작하는 경우  
  
- pszName의 문자열 데이터에 공백이 포함된 경우  
  
- pszName의 문자열 데이터에 ,;.`~!@#$%^&*()=[]{}&#124;\\?/<>> 문자 중 하나가 포함된 경우  
  
  `Level`  
  
  성능 데이터 수집을 적용할 수 있는 프로필 수준을 나타냅니다. 다음 **PROFILE_CONTROL_LEVEL** 값은 성능 데이터 수집을 적용할 수 있는 세 가지 수준 중 하나를 나타내는 데 사용될 수 있습니다.  
  
|Enumerator|Description|  
|----------------|-----------------|  
|PROFILE_GLOBALLEVEL|전역 수준 설정은 프로파일링 실행의 모든 프로세스와 스레드에 영향을 줍니다.|  
|PROFILE_PROCESSLEVEL|프로세스 수준 설정은 지정된 프로세스의 일부인 모든 스레드에 영향을 줍니다.|  
|PROFILE_THREADLEVEL|스레드 프로파일링 수준 설정은 지정된 스레드에 영향을 줍니다.|  
  
 `dwId`  
  
 프로파일링 수준 식별자입니다. 시스템에서 생성한 프로세스 또는 스레드 식별자를 사용합니다.  
  
## <a name="property-valuereturn-value"></a>속성 값/반환 값  
 이 함수는 **PROFILE_COMMAND_STATUS** 열거형을 사용하여 성공 또는 실패를 나타냅니다. 반환 값은 다음 중 하나일 수 있습니다.  
  
|Enumerator|Description|  
|----------------|-----------------|  
|NAME_ERROR_ID_NOEXIST|지정된 프로파일링 요소가 없습니다.|  
|NAME_ERROR_INVALID_NAME|이름이 잘못되었습니다.|  
|NAME_ERROR_LEVEL_NOEXIST|지정된 프로파일링 수준이 없습니다.|  
|NAME_ERROR_NO_SUPPORT|지정된 작업은 지원되지 않습니다.|  
|NAME_ERROR_OUTOFMEMORY|메모리에 이벤트를 기록할 수 없습니다.|  
|NAME_ERROR_REDEFINITION|이름이 프로필 요소에 이미 할당되었습니다. 이 함수의 이름은 무시됩니다.|  
|NAME_ERROR_TEXTTRUNCATED|이름 텍스트가 null 문자를 포함하여 32자를 초과했으므로 잘렸습니다.|  
|NAME_OK|이름이 등록되었습니다.|  
  
## <a name="remarks"></a>설명  
 하나의 이름만 각 프로세스 또는 스레드에 할당될 수 있습니다. 프로파일링 요소에 이름이 지정된 후 해당 요소의 NameProfile에 대한 후속 호출은 무시됩니다.  
  
 서로 다른 스레드 또는 프로세스에 같은 이름이 지정된 경우 보고서는 해당 이름을 가진 해당 수준에서 모든 요소의 데이터를 포함합니다.  
  
 현재 이외의 프로세스 또는 스레드를 지정하는 경우 이름을 지정하기 전에 초기화되었고 실행이 시작되었는지 확인해야 합니다. 그렇지 않으면 NameProfile 메서드가 실패합니다.  
  
> [!IMPORTANT]
> CreateProcess() 및 CreateThread() API 함수는 스레드 또는 프로세스가 초기화되기 전에 반환할 수 있습니다.  
  
## <a name="net-framework-equivalent"></a>.NET Framework의 해당 값  
 Microsoft.VisualStudio.Profiler.dll  
  
## <a name="function-information"></a>함수 정보  
  
|항목|설명|  
|-|-|  
|**머리글**|VSPerf.h 포함|  
|**라이브러리**|VSPerf.lib 사용|  
|**유니코드**|`NameProfileW`(유니코드) 및 `NameProfileA`(ANSI)로 구현됐습니다.|  
  
## <a name="example"></a>예제  
 다음 코드에서는 NameProfile 함수 호출을 보여 줍니다. 예제에서는 코드에서 ANSI 사용 함수를 호출할지 여부를 결정하도록 Win32 문자열 매크로 및 ANSI에 대한 컴파일러 설정의 사용을 가정합니다.  
  
```  
void ExerciseNameProfile()  
{  
    // Variables used to print output.  
    HRESULT hResult;  
    TCHAR tchBuffer[256];  
  
    // Create and initialize variables to pass to   
    // ExerciseNameProfile.  The value of this   
    // parameter is based on the needs of the code;  
    // and for the sake of simplicity in this example,   
    // the variable is assigned an arbitrary value.  
    TCHAR * profileName = TEXT("ExerciseNameProfile");  
  
    // Declare enumeration to hold result of call to   
    // ExerciseNameProfle.  
    PROFILE_COMMAND_STATUS nameResult;  
  
    nameResult =  NameProfile(  
        profileName,  
        PROFILE_GLOBALLEVEL,  
        PROFILE_CURRENTID);  
  
    // Format and print result.  
    LPCTSTR pszFormat = TEXT("%s %d.\0");  
    TCHAR* pszTxt = TEXT("NameProfile returned");  
    hResult = StringCchPrintf(tchBuffer, 256, pszFormat,   
        pszTxt, nameResult);  
  
#ifdef DEBUG  
    OutputDebugString(tchBuffer);  
#endif  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 프로파일러 API 참조 (네이티브)](../profiling/visual-studio-profiler-api-reference-native.md)
