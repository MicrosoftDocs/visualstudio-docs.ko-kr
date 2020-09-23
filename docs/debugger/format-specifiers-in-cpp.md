---
title: 디버거의 형식 지정자(C++) | Microsoft Docs
ms.date: 3/11/2019
ms.topic: conceptual
f1_keywords:
- vs.debug
dev_langs:
- C++
helpviewer_keywords:
- QuickWatch dialog box, format specifiers in C++
- variables [debugger], watch variable symbols
- symbols, watch variable formatting
- QuickWatch dialog box, using format specifiers
- expressions [C++], format specifiers
- specifiers, watch variable format
- specifiers
- Watch window, format specifiers in C++
- watch variable symbols
- format specifiers, debugger
- debugger, format specifiers recognized by
ms.assetid: 0f6f3b7c-ce2c-4b4d-b14f-7589dbed5444
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- cplusplus
ms.openlocfilehash: 287ef3ccfd344786bd98098c5f28d0a2bd6573f6
ms.sourcegitcommit: 4a9689890f271f9b8b73c3333e0699cce84a95d8
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/21/2020
ms.locfileid: "90832322"
---
# <a name="format-specifiers-for-c-in-the-visual-studio-debugger"></a>Visual Studio 디버거의 C++용 형식 지정자
형식 지정자를 사용하여 **조사식**, **자동** 및 **지역** 창에 값이 표시되는 형식을 변경할 수 있습니다.

또한 **직접 실행** 창, **명령** 창, [추적점](../debugger/using-breakpoints.md#BKMK_Print_to_the_Output_window_with_tracepoints) 그리고 소스 창에서도 형식 지정자를 사용할 수 있습니다. 이러한 창에서 식을 일시 중지하면 [DataTip](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)에 결과가 표시됩니다. DataTip 표시는 형식 지정자를 반영합니다.

> [!NOTE]
> Visual Studio 네이티브 디버거가 새 디버깅 엔진으로 변경될 때 일부 형식 지정자가 새로 추가되었으며 일부 이전 형식 지정자가 제거되었습니다. C++/CLI를 사용하여 interop(혼합 네이티브 및 관리) 디버깅을 수행할 때 이전 디버거가 계속 사용됩니다.

## <a name="set-format-specifiers"></a>형식 지정자 설정
다음 예제 코드를 사용합니다.

```C++
int main() {
    int my_var1 = 0x0065;
    int my_var2 = 0x0066;
    int my_var3 = 0x0067;
}
```

디버그 중에 `my_var1` 변수를 **조사식** 창에 추가합니다(**디버그** > **창** > **조사식** > **조사식 1**). 그런 다음, 변수를 마우스 오른쪽 단추로 클릭하고 **16진수 표시**를 선택합니다. 이제 **조사식** 창에 0x0065 값이 표시됩니다. 이 값이 정수가 아닌 문자로 표시되도록 하려면 먼저 마우스 오른쪽 단추를 클릭하고 **16진수 표시**를 선택 취소합니다. 그런 다음, **이름** 열에서 변수 이름 뒤에 문자 형식 지정자 **, c**를 추가합니다. 이제 **값** 열에 **101 ‘e’** 가 표시됩니다.

![WatchFormatCPlus1](../debugger/media/watchformatcplus1.png "WatchFormatCPlus1")

::: moniker range=">= vs-2019" 
**조사식** 창에서 값에 쉼표(,)를 추가하여 사용 가능한 형식 지정자 목록을 보고 형식 지정자를 선택할 수 있습니다. 

![WatchFormatSpecDropdown](../debugger/media/vs-2019/format-specs-cpp.png "FormatSpecCpp")

::: moniker-end

## <a name="format-specifiers"></a><a name="BKMK_Visual_Studio_2012_format_specifiers"></a> 형식 지정자
다음 표에는 Visual Studio에서 사용할 수 있는 형식 지정자가 설명되어 있습니다. 굵게 표시된 지정자는 새 디버거에서만 지원되며 C++/CLI를 사용하는 interop 디버깅에서는 지원되지 않습니다.

::: moniker range=">= vs-2019" 

|지정자|서식|원래 조사식 값|표시되는 값|
|---------------|------------|--------------------------|---------------------|
|일|10진수 정수|0x00000066|102|
|o|부호 없는 8진수 정수|0x00000066|000000000146|
|x<br /><br /> **h**|16진수 정수|102|0xcccccccc|
|X<br /><br /> **H**|16진수 정수|102|0xcccccccc|
|xb<br /><br /> **hb**|16진수 정수(앞에 0x 포함하지 않음)|102|cccccccc|
|Xb<br /><br /> **Hb**|16진수 정수(앞에 0x 포함하지 않음)|102|CCCCCCCC|
|b|부호 없는 이진 정수|25|0b00000000000000000000000000011001|
|bb|부호 없는 이진 정수(앞에 0b 포함하지 않음)|25|00000000000000000000000000011001|
|e|과학적 표기법|25000000|2.500000e+07|
|g|과학적 점 또는 부동 소수점 중 더 짧은 항목|25000000|2.5e+07|
|c|단일 문자|0x0065|101 'e'|
|초|const char* 문자열(따옴표 포함)|\<location> "hello world"|"hello world"|
|**sb**|const char* 문자열(따옴표 없음)|\<location> “hello world”|hello world|
|s8|UTF-8 문자열|\<location> “This is a UTF-8 coffee cup â˜•”|“This is a UTF-8 coffee cup ☕”|
|**s8b**|UTF-8 문자열(따옴표 제외)|\<location> “hello world”|hello world|
|su|유니코드(UTF-16 인코딩) 문자열(따옴표 포함)|\<location> L“hello world”|L"hello world"<br /><br /> u"hello world"|
|sub|유니코드(UTF-16 인코딩) 문자열(따옴표 없음)|\<location> L“hello world”|hello world|
|bstr|BSTR 이진 문자열(따옴표 포함)|\<location> L“hello world”|L"hello world"|
|env|환경 블록(이중 null로 종결되는 문자열)|\<location> L“=::=::\\\\|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|UTF-32 문자열(따옴표 포함)|\<location> U“hello world”|u"hello world"|
|**s32b**|UTF-32 문자열(따옴표 제외)|\<location> U“hello world”|hello world|
|**en**|enum|Saturday(6)|토요일|
|**hv**|포인터 유형 - 검사 중인 포인터 값이 배열의 힙 할당 결과임을 나타냅니다(예: `new int[3]`).|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**na**|개체에 대한 포인터의 메모리 주소를 표시하지 않습니다.|\<location>, {member=value...}|{member=value...}|
|**nd**|파생된 클래스는 무시하고 기본 클래스 정보만 표시합니다.|`(Shape*) square` 에는 기본 클래스 및 파생 클래스 정보가 포함됩니다.|기본 클래스 정보만 표시합니다.|
|hr|HRESULT 또는 Win32 오류 코드. HRESULT의 경우 디버거가 자동으로 디코딩하므로 이 지정자가 더 이상 필요하지 않습니다.|S_OK|S_OK|
|wc|Window 클래스 플래그|0x0010|WC_DEFAULTCHAR|
|wm|Windows 메시지 번호|16|WM_CLOSE|
|nr|“Raw 뷰” 항목 표시 안 함|
|nvo|숫자 값에 대해서만 “Raw 뷰” 항목 표시|
|!|원시 형식. 모든 데이터 형식 뷰의 사용자 지정을 무시합니다.|\<customized representation>|4|

::: moniker-end

::: moniker range="vs-2017" 

|지정자|서식|원래 조사식 값|표시되는 값|
|---------------|------------|--------------------------|---------------------|
|일|10진수 정수|0x00000066|102|
|o|부호 없는 8진수 정수|0x00000066|000000000146|
|x<br /><br /> **h**|16진수 정수|102|0xcccccccc|
|X<br /><br /> **H**|16진수 정수|102|0xcccccccc|
|c|단일 문자|0x0065, c|101 'e'|
|초|const char* 문자열(따옴표 포함)|\<location> “hello world”|"hello world"|
|**sb**|const char* 문자열(따옴표 없음)|\<location> “hello world”|hello world|
|s8|UTF-8 문자열|\<location> “This is a UTF-8 coffee cup â˜•”|“This is a UTF-8 coffee cup ☕”|
|**s8b**|UTF-8 문자열(따옴표 제외)|\<location> “hello world”|hello world|
|su|유니코드(UTF-16 인코딩) 문자열(따옴표 포함)|\<location> L“hello world”|L"hello world"<br /><br /> u"hello world"|
|sub|유니코드(UTF-16 인코딩) 문자열(따옴표 없음)|\<location> L“hello world”|hello world|
|bstr|BSTR 이진 문자열(따옴표 포함)|\<location> L“hello world”|L"hello world"|
|env|환경 블록(이중 null로 종결되는 문자열)|\<location> L“=::=::\\\\|L"=::=::\\\\\\0=C:=C:\\\\windows\\\\system32\\0ALLUSERSPROFILE=...|
|**s32**|UTF-32 문자열(따옴표 포함)|\<location> U“hello world”|u"hello world"|
|**s32b**|UTF-32 문자열(따옴표 제외)|\<location> U“hello world”|hello world|
|**en**|enum|Saturday(6)|토요일|
|**hv**|포인터 유형 - 검사 중인 포인터 값이 배열의 힙 할당 결과임을 나타냅니다(예: `new int[3]`).|\<location>{\<first member>}|\<location>{\<first member>, \<second member>, ...}|
|**na**|개체에 대한 포인터의 메모리 주소를 표시하지 않습니다.|\<location>, {member=value...}|{member=value...}|
|**nd**|파생된 클래스는 무시하고 기본 클래스 정보만 표시합니다.|`(Shape*) square` 에는 기본 클래스 및 파생 클래스 정보가 포함됩니다.|기본 클래스 정보만 표시합니다.|
|hr|HRESULT 또는 Win32 오류 코드. HRESULT의 경우 디버거가 자동으로 디코딩하므로 이 지정자가 더 이상 필요하지 않습니다.|S_OK|S_OK|
|wc|Window 클래스 플래그|0x0010|WC_DEFAULTCHAR|
|wm|Windows 메시지 번호|16|WM_CLOSE|
|!|원시 형식. 모든 데이터 형식 뷰의 사용자 지정을 무시합니다.|\<customized representation>|4|

::: moniker-end

> [!NOTE]
> **hv** 형식 지정자가 있는 경우 디버거는 버퍼의 길이를 확인하여 해당 숫자의 요소를 표시하려고 합니다. 디버거에서 항상 배열의 정확한 버퍼 크기를 찾을 수는 없으므로 가능한 한 크기 지정자 `(pBuffer,[bufferSize])` 를 사용해야 합니다. **hv** 형식 지정자는 버퍼 크기를 즉시 사용할 수 없는 경우에 유용합니다.

### <a name="size-specifiers-for-pointers-as-arrays"></a><a name="BKMK_Size_specifiers_for_pointers_as_arrays_in_Visual_Studio_2012"></a> 배열로 사용되는 포인터에 대한 크기 지정자
배열로 표시할 개체에 대한 포인터가 있는 경우 다음과 같이 정수 또는 식을 사용하여 배열 요소의 수를 지정할 수 있습니다.

|지정자|서식|원래 조사식 값|표시되는 값|
|---------------|------------|---------------------------|---------------------|
|n|10진수 또는 **16진수** 정수|pBuffer,[32]<br /><br /> pBuffer, **[0x20]**|`pBuffer` 를 요소가 32개인 배열로 표시합니다.|
|**[exp]**|정수로 확인되는 유효한 C++ 식입니다.|pBuffer,[bufferSize]|PBuffer를 `bufferSize` 요소의 배열로 표시합니다.|
|**expand(n)**|정수로 확인되는 유효한 C++ 식입니다.|pBuffer, expand(2)|`pBuffer`의 세 번째 요소를 표시합니다.|

## <a name="format-specifiers-for-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_for_interop_debugging_and_C___edit_and_continue"></a> C++/CLI를 사용하는 interop 디버깅의 형식 지정자
**굵게** 표시된 지정자는 네이티브 및 C++/CLI 코드 디버깅에 대해서만 지원됩니다.

|지정자|서식|원래 조사식 값|표시되는 값|
|---------------|------------|--------------------------|---------------------|
|**d**<br /><br />**i**|부호 있는 10진수 정수|0xF000F065|-268373915|
|**u**|부호 없는 10진수 정수|0x0065|101|
|o|부호 없는 8진수 정수|0xF065|0170145|
|x<br /><br />X|16진수 정수|61541|0x0000f065|
|**l**<br /><br />**h**|d, i, u, o, x, X에 대한 long 또는 short 접두사|00406042|0x0c22|
|**f**|부호 있는 부동 소수점|(3./2.), f|1.500000|
|**e**|부호 있는 과학적 표기법|(3.0/2.0)|1.500000e+000|
|**g**|부호 있는 부동 소수점 또는 부호 있는 과학적 표기법 중<br/> 더 짧은 것|(3.0/2.0)|1.5|
|c|단일 문자|\<location>|101 'e'|
|초|const char*(따옴표 포함)|\<location>|"hello world"|
|su|const wchar_t*<br /><br /> const char16_t\*(따옴표 포함)|\<location>|L"hello world"|
|sub|const wchar_t*<br /><br /> const char16_t\*|\<location>|hello world|
|s8|const char*(따옴표 포함)|\<location>|"hello world"|
|hr|HRESULT 또는 Win32 오류 코드.<br/>HRESULT의 경우 디버거가 자동으로 디코딩하므로 이 지정자가 더 이상 필요하지 않습니다.|S_OK|S_OK|
|wc|Window 클래스 플래그|0x00000040,|WC_DEFAULTCHAR|
|wm|Windows 메시지 번호|0x0010|WM_CLOSE|
|!|원시 형식. 모든 데이터 형식 뷰의 사용자 지정을 무시합니다.|\<customized representation>|4|

### <a name="format-specifiers-for-memory-locations-in-interop-debugging-with-ccli"></a><a name="BKMK_Format_specifiers_memory_locations_in_interop_debugging_and_C___edit_and_continue"></a> C++/CLI를 사용하는 interop 디버깅의 메모리 위치 형식 지정자
다음 표에는 메모리 위치에 사용되는 형식 지정 기호가 설명되어 있습니다. 메모리 위치 지정자를 위치로 확인되는 값이나 수식에 사용할 수 있습니다.

|Symbol|서식|원래 조사식 값|표시되는 값|
|------------|------------|--------------------------|---------------------|
|**ma**|ASCII 문자 64개|0x0012ffac|0x0012ffac .4...0...".0W&.......1W&.0.:W..1...."..1.JO&.1.2.."..1...0y....1|
|**m**|16바이트 16진수 뒤에 ASCII 문자 16개|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**mb**|16바이트 16진수 뒤에 ASCII 문자 16개|0x0012ffac|0x0012ffac B3 34 CB 00 84 30 94 80 FF 22 8A 30 57 26 00 00 .4...0...".0W&amp;.|
|**mw**|워드 8개|0x0012ffac|0x0012ffac 34B3 00CB 3084 8094 22FF 308A 2657 0000|
|**md**|더블워드 4개|0x0012ffac|0x0012ffac 00CB34B3 80943084 308A22FF 00002657|
|**mq**|쿼드워드 2개|0x0012ffac|0x0012ffac 7ffdf00000000000 5f441a790012fdd4|
|**mu**|2바이트 유니코드 문자|0x0012ffac|0x0012ffac 8478 77f4 ffff ffff 0000 0000 0000 0000|

### <a name="size-specifier-for-pointers-as-arrays-in-interop-debugging-with-ccli"></a><a name="BKMK_Size_specifier_for_pointers_as_arrays_in_interop_debugging_and_C___edit_and_continue"></a> C++/CLI를 사용하는 interop 디버깅에서 배열로 사용되는 포인터의 크기 지정자
배열로 표시할 개체에 대한 포인터가 있는 경우 다음과 같이 정수를 사용하여 배열 요소의 수를 지정할 수 있습니다.

|지정자|서식|식|표시되는 값|
|---------------|------------|----------------|---------------------|
|n|10진수 정수|pBuffer[32]|`pBuffer`를 32개 요소 배열로 표시합니다.|