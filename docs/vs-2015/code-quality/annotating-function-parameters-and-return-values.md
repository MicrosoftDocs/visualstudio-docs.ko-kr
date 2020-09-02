---
title: 함수 매개 변수 및 반환 값에 주석 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
f1_keywords:
- _Outptr_opt_result_bytebuffer_to_
- _Inout_updates_all_opt_
- _Post_equal_to_
- _Outptr_opt_result_maybenull_
- _Out_writes_bytes_all_
- _Out_writes_all_opt_
- _In_opt_
- _Outptr_
- _Outptr_result_maybenull_
- _Outref_result_bytebuffer_all_maybenull_
- _Inout_updates_opt_z_
- _Inout_updates_z_
- _Out_writes_
- _Out_writes_to_ptr_opt_z_
- _In_reads_to_ptr_opt_
- _Ret_writes_to_maybenull_
- _Outref_result_maybenull_
- _Ret_writes_bytes_
- _Outptr_result_bytebuffer_
- _Out_writes_opt_
- _Inout_updates_bytes_opt_
- _In_z_
- _Inout_updates_to_
- _Ret_maybenull_
- _Ret_writes_bytes_to_
- _Ret_z_
- _COM_Outptr_
- _Ret_maybenull_z_
- _Out_opt_
- _In_reads_opt_z_
- _Outptr_result_bytebuffer_to_
- _Ret_notnull_
- _COM_Outptr_opt_result_maybenull_
- _Inout_updates_to_opt_
- _Inout_updates_
- _Outptr_opt_result_buffer_
- _Outptr_result_buffer_to_
- _Out_writes_to_ptr_opt_
- _Out_writes_bytes_all_opt_
- _Inout_updates_all_
- _Deref_inout_range_
- _Ret_writes_
- _Out_writes_z_
- _Ret_writes_to_
- _Out_writes_to_ptr_z_
- _Out_writes_bytes_to_opt_
- _In_reads_or_z_
- _Inout_updates_bytes_to_
- _In_reads_z_
- _In_opt_z_
- _Outref_result_buffer_maybenull_
- _Ret_range_
- _COM_Outptr_opt_
- _Ouptr_opt_result_maybenull_z_
- _In_reads_opt_
- _Inout_
- _Field_range_
- _Ret_writes_z_
- _Out_writes_to_
- _Out_writes_to_ptr_
- _Inout_opt_z_
- _Outref_
- _Deref_out_range_
- _Outref_result_buffer_
- _Outref_result_buffer_to_
- _Outref_result_bytebuffer_to_maybenull_
- _In_reads_bytes_
- _Outptr_opt_result_buffer_to_
- _Outref_result_buffer_all_
- _Out_writes_bytes_to_
- _Result_zeroonfailure_
- _In_reads_bytes_opt_
- _Outref_result_buffer_to_maybenull_
- _Outref_result_bytebuffer_all_
- _Outref_result_buffer_all_maybenull_
- _Ret_writes_maybenull_z_
- _In_range_
- _Inout_updates_bytes_all_opt_
- _Outref_result_bytebuffer_to_
- _Inout_updates_bytes_to_opt_
- _Pre_equal_to_
- _Ret_writes_bytes_maybenull_
- _COM_Outptr_result_maybenull_
- _Ret_writes_maybenull_
- _Out_writes_bytes_
- _Outptr_opt_
- _Out_writes_opt_z_
- _Outref_result_nullonfailure_
- _Outptr_opt_result_z_
- _Inout_opt_
- _Deref_in_range_
- _Outptr_result_z_
- _In_reads_to_ptr_opt_z_
- _Struct_size_bytes_
- _Outptr_result_nullonfailure_
- _In_
- _Inout_updates_bytes_
- _In_reads_to_ptr_z_
- _Ret_writes_bytes_to_maybenull
- _Outptr_opt_result_nullonfailure_
- _In_reads_to_ptr_
- _Outptr_result_buffer_
- _Out_
- _Outref_result_bytebuffer_maybenull_
- _Outptr_result_maybenull_z_
- _In_reads_
- _Inout_updates_opt_
- _Out_writes_to_opt_
- _Outptr_opt_result_bytebuffer_
- _Out_writes_all_
- _Out_range_
- _Inout_updates_bytes_all_
- _Inout_z_
- _Outref_result_bytebuffer_
- _Result_nullonfailure_
- _Ret_null_
ms.assetid: 82826a3d-0c81-421c-8ffe-4072555dca3a
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 71854388f3fb1c5eaea7d40ed2757af9cecacf1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85543808"
---
# <a name="annotating-function-parameters-and-return-values"></a>함수 매개 변수 및 반환 값에 주석 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 문서에서는 간단한 함수 매개 변수 (스칼라) 및 구조체와 클래스에 대 한 포인터, 대부분의 버퍼에 대 한 주석의 일반적인 사용에 대해 설명 합니다.  또한이 문서에서는 주석의 일반적인 사용 패턴을 보여 줍니다. 함수와 관련 된 추가 주석은 [함수 동작에 주석](../code-quality/annotating-function-behavior.md) 추가를 참조 하세요.  
  
## <a name="pointer-parameters"></a>포인터 매개 변수  
 다음 표의 주석에서는 포인터 매개 변수를 주석으로 처리 하는 경우 포인터가 null 인 경우 분석기에서 오류를 보고 합니다.  이는 포인터가 가리키는 모든 데이터 항목에 적용 됩니다.  
  
 **주석 및 설명**  
  
- `_In_`  
  
     스칼라, 구조체, 구조체에 대 한 포인터 및 이와 같은 입력 매개 변수를 주석을 추가 합니다.  Simple 스칼라에서 명시적으로 사용할 수 있습니다.  매개 변수는 사전 상태에서 유효 해야 하며 수정 되지 않습니다.  
  
- `_Out_`  
  
     주석을 추가는 스칼라, 구조체, 구조체에 대 한 포인터 및 이와 같은 출력 매개 변수를 출력 합니다.  값으로 전달 되는 스칼라와 같이 값을 반환할 수 없는 개체에는이를 적용 하지 마십시오.  매개 변수는 사전 상태에서 유효 하지 않아도 되지만 사후 상태에서 유효 해야 합니다.  
  
- `_Inout_`  
  
     주석을 추가 함수에 의해 변경 되는 매개 변수입니다.  사전 상태와 사후 상태 모두에서 유효 해야 하지만 호출 전후에 다른 값을 갖는 것으로 간주 됩니다. 수정할 수 있는 값에 적용 해야 합니다.  
  
- `_In_z_`  
  
     입력으로 사용 되는 null로 끝나는 문자열에 대 한 포인터입니다.  문자열은 사전 상태에서 유효 해야 합니다.  `PSTR`이미 올바른 주석이 있는의 변형은 선호 됩니다.  
  
- `_Inout_z_`  
  
     수정 되는 null로 끝나는 문자 배열에 대 한 포인터입니다.  이 값은 호출 전후에 유효 해야 하지만 값은 변경 된 것으로 간주 됩니다.  Null 종결자는 이동 될 수 있지만 원래의 null 종결자 까지의 요소만 액세스할 수 있습니다.  
  
- `_In_reads_(s)`  
  
     `_In_reads_bytes_(s)`  
  
     함수에서 읽는 배열에 대 한 포인터입니다.  배열의 크기는 `s` 모두 유효 해야 합니다.  
  
     `_bytes_`변형은 요소 대신 크기 (바이트)를 제공 합니다. 크기를 요소로 표현할 수 없는 경우에만이를 사용 합니다.  예를 들어 `char` 문자열은에서 `_bytes_` 사용 하는 유사한 함수에서 variant를 사용 `wchar_t` 합니다.  
  
- `_In_reads_z_(s)`  
  
     Null로 종료 되 고 크기가 알려진 배열에 대 한 포인터입니다. Null 종결자 ( `s` null 종결자가 없는 경우)의 요소는 사전 상태에서 유효 해야 합니다.  크기를 바이트 단위로 알고 있으면 `s` 요소 크기를 기준으로 크기를 조정 합니다.  
  
- `_In_reads_or_z_(s)`  
  
     Null로 끝나는 배열에 대 한 포인터 이거나, 해당 크기 또는 둘 다를 포함 하는 배열에 대 한 포인터입니다. Null 종결자 ( `s` null 종결자가 없는 경우)의 요소는 사전 상태에서 유효 해야 합니다.  크기를 바이트 단위로 알고 있으면 `s` 요소 크기를 기준으로 크기를 조정 합니다.  (제품군에 사용 됨 `strn` )  
  
- `_Out_writes_(s)`  
  
     `_Out_writes_bytes_(s)`  
  
     `s`함수에서 쓸 요소 (응답)의 배열에 대 한 포인터입니다.  배열 요소는 사전 상태에서 유효 하지 않아도 되며 사후 상태에서 유효한 요소 수는 지정 되지 않습니다.  매개 변수 형식에 주석이 있으면 사후 상태에 적용 됩니다. 예를 들어, 다음과 같은 코드를 생각해 볼 수 있습니다.  
  
     `typedef _Null_terminated_ wchar_t *PWSTR; void MyStringCopy(_Out_writes_ (size) PWSTR p1,    _In_ size_t size,    _In_ PWSTR p2);`  
  
     이 예제에서 호출자는의 요소 버퍼를 제공 합니다 `size` `p1` .  `MyStringCopy` 이러한 요소 중 일부를 사용할 수 있도록 합니다. 무엇 보다도, `_Null_terminated_` 의 주석은 `PWSTR` `p1` 사후 상태에서 null로 종료 됨을 의미 합니다.  이러한 방식으로 올바른 요소 수는 여전히 잘 정의 되어 있지만 특정 요소 수는 필요 하지 않습니다.  
  
     `_bytes_`변형은 요소 대신 크기 (바이트)를 제공 합니다. 크기를 요소로 표현할 수 없는 경우에만이를 사용 합니다.  예를 들어 `char` 문자열은에서 `_bytes_` 사용 하는 유사한 함수에서 variant를 사용 `wchar_t` 합니다.  
  
- `_Out_writes_z_(s)`  
  
     요소의 배열에 대 한 포인터 `s` 입니다.  요소는 사전 상태에서 유효 하지 않아도 됩니다.  사후 상태에서 null 종결자 (존재 해야 함) 까지의 요소가 유효 해야 합니다.  크기를 바이트 단위로 알고 있으면 `s` 요소 크기를 기준으로 크기를 조정 합니다.  
  
- `_Inout_updates_(s)`  
  
     `_Inout_updates_bytes_(s)`  
  
     함수에서 읽고 쓸 수 있는 배열에 대 한 포인터입니다.  크기 `s` 요소 이며 사전 상태 및 사후 상태에서 유효 합니다.  
  
     `_bytes_`변형은 요소 대신 크기 (바이트)를 제공 합니다. 크기를 요소로 표현할 수 없는 경우에만이를 사용 합니다.  예를 들어 `char` 문자열은에서 `_bytes_` 사용 하는 유사한 함수에서 variant를 사용 `wchar_t` 합니다.  
  
- `_Inout_updates_z_(s)`  
  
     Null로 종료 되 고 크기가 알려진 배열에 대 한 포인터입니다. Null 종결자 (존재 해야 함)의 요소는 사전 상태와 사후 상태 모두에서 유효 해야 합니다.  사후 상태 값은 사전 상태 값과 다른 것으로 간주 됩니다. 여기에는 null 종결자의 위치가 포함 됩니다. 크기를 바이트 단위로 알고 있으면 `s` 요소 크기를 기준으로 크기를 조정 합니다.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     요소의 배열에 대 한 포인터 `s` 입니다.  요소는 사전 상태에서 유효 하지 않아도 됩니다.  사후 상태에서 `c` -th 요소 까지의 요소가 유효 해야 합니다.  크기를 바이트 단위로 알 수 있으면 크기를 조정 `s` 하 고 `c` 요소 크기를 조정 하거나 `_bytes_` 다음과 같이 정의 된 variant를 사용 합니다.  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     즉, 사전 상태에서 버퍼에 있는 모든 요소는 `s` 사후 상태에서 유효 합니다.  예를 들면 다음과 같습니다.  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     함수에서 읽고 쓰는 배열에 대 한 포인터입니다.  크기는 요소 이며 `s` , 모든 요소는 사전 상태에서 유효 해야 하며 `c` 요소는 사후 상태에서 유효 해야 합니다.  
  
     `_bytes_`변형은 요소 대신 크기 (바이트)를 제공 합니다. 크기를 요소로 표현할 수 없는 경우에만이를 사용 합니다.  예를 들어 `char` 문자열은에서 `_bytes_` 사용 하는 유사한 함수에서 variant를 사용 `wchar_t` 합니다.  
  
- `_Inout_updates_z_(s)`  
  
     Null로 종료 되 고 크기가 알려진 배열에 대 한 포인터입니다. Null 종결자 (존재 해야 함)의 요소는 사전 상태와 사후 상태 모두에서 유효 해야 합니다.  사후 상태 값은 사전 상태 값과 다른 것으로 간주 됩니다. 여기에는 null 종결자의 위치가 포함 됩니다. 크기를 바이트 단위로 알고 있으면 `s` 요소 크기를 기준으로 크기를 조정 합니다.  
  
- `_Out_writes_to_(s,c)`  
  
     `_Out_writes_bytes_to_(s,c)`  
  
     `_Out_writes_all_(s)`  
  
     `_Out_writes_bytes_all_(s)`  
  
     요소의 배열에 대 한 포인터 `s` 입니다.  요소는 사전 상태에서 유효 하지 않아도 됩니다.  사후 상태에서 `c` -th 요소 까지의 요소가 유효 해야 합니다.  크기를 바이트 단위로 알 수 있으면 크기를 조정 `s` 하 고 `c` 요소 크기를 조정 하거나 `_bytes_` 다음과 같이 정의 된 variant를 사용 합니다.  
  
     `_Out_writes_to_(_Old_(s), _Old_(s))    _Out_writes_bytes_to_(_Old_(s), _Old_(s))`  
  
     즉, 사전 상태에서 버퍼에 있는 모든 요소는 `s` 사후 상태에서 유효 합니다.  예를 들면 다음과 같습니다.  
  
     `void *memcpy(_Out_writes_bytes_all_(s) char *p1,    _In_reads_bytes_(s) char *p2,    _In_ int s); void * wordcpy(_Out_writes_all_(s) DWORD *p1,     _In_reads_(s) DWORD *p2,    _In_ int s);`  
  
- `_Inout_updates_to_(s,c)`  
  
     `_Inout_updates_bytes_to_(s,c)`  
  
     함수에서 읽고 쓰는 배열에 대 한 포인터입니다.  크기는 요소 이며 `s` , 모든 요소는 사전 상태에서 유효 해야 하며 `c` 요소는 사후 상태에서 유효 해야 합니다.  
  
     `_bytes_`변형은 요소 대신 크기 (바이트)를 제공 합니다. 크기를 요소로 표현할 수 없는 경우에만이를 사용 합니다.  예를 들어 `char` 문자열은에서 `_bytes_` 사용 하는 유사한 함수에서 variant를 사용 `wchar_t` 합니다.  
  
- `_Inout_updates_all_(s)`  
  
     `_Inout_updates_bytes_all_(s)`  
  
     크기 요소의 함수로 읽고 쓰는 배열에 대 한 포인터 `s` 입니다. 다음에 해당 하는 것으로 정의 됩니다.  
  
     `_Inout_updates_to_(_Old_(s), _Old_(s))    _Inout_updates_bytes_to_(_Old_(s), _Old_(s))`  
  
     즉, 사전 상태에서 버퍼에 있는 모든 요소는 사전 상태 `s` 및 사후 상태에서 유효 합니다.  
  
     `_bytes_`변형은 요소 대신 크기 (바이트)를 제공 합니다. 크기를 요소로 표현할 수 없는 경우에만이를 사용 합니다.  예를 들어 `char` 문자열은에서 `_bytes_` 사용 하는 유사한 함수에서 variant를 사용 `wchar_t` 합니다.  
  
- `_In_reads_to_ptr_(p)`  
  
     식 `p` `_Curr_` (즉, `p` 빼기 `_Curr_` )이 적절 한 언어 표준에 의해 정의 되는 배열에 대 한 포인터입니다.  이전 요소는 `p` 사전 상태에서 유효 해야 합니다.  
  
- `_In_reads_to_ptr_z_(p)`  
  
     식 `p` `_Curr_` (즉, `p` 빼기 `_Curr_` )이 적절 한 언어 표준에 의해 정의 되는 null로 끝나는 배열에 대 한 포인터입니다.  이전 요소는 `p` 사전 상태에서 유효 해야 합니다.  
  
- `_Out_writes_to_ptr_(p)`  
  
     식 `p` `_Curr_` (즉, `p` 빼기 `_Curr_` )이 적절 한 언어 표준에 의해 정의 되는 배열에 대 한 포인터입니다.  이전 요소는 `p` 사전 상태에서 유효 하지 않아도 되며 사후 상태에서 유효 해야 합니다.  
  
- `_Out_writes_to_ptr_z_(p)`  
  
     식 `p` `_Curr_` (즉, `p` 빼기 `_Curr_` )이 적절 한 언어 표준에 의해 정의 되는 null로 끝나는 배열에 대 한 포인터입니다.  이전 요소는 `p` 사전 상태에서 유효 하지 않아도 되며 사후 상태에서 유효 해야 합니다.  
  
## <a name="optional-pointer-parameters"></a>선택적 포인터 매개 변수  
 포인터 매개 변수 주석에 포함 된 경우 `_opt_` 매개 변수가 null 일 수 있음을 나타냅니다. 그렇지 않으면 주석은 포함 되지 않은 버전과 동일 하 게 수행 `_opt_` 됩니다. `_opt_`포인터 매개 변수 주석의 변형 목록은 다음과 같습니다.  
  
`_In_opt_`, `_Out_opt_`, `_Inout_opt_`, `_In_opt_z_`, `_Inout_opt_z_`, `_In_reads_opt_`, `_In_reads_bytes_opt_`, `_In_reads_opt_z_`|`_Out_writes_opt_`, `_Out_writes_opt_z_`, `_Inout_updates_opt_`, `_Inout_updates_bytes_opt_`, `_Inout_updates_opt_z_`, `_Out_writes_to_opt_`, `_Out_writes_bytes_to_opt_`, `_Out_writes_all_opt_`, `_Out_writes_bytes_all_opt_`|`_Inout_updates_to_opt_`, `_Inout_updates_bytes_to_opt_`, `_Inout_updates_all_opt_`, `_Inout_updates_bytes_all_opt_`, `_In_reads_to_ptr_opt_`, `_In_reads_to_ptr_opt_z_`, `_Out_writes_to_ptr_opt_`, `_Out_writes_to_ptr_opt_z_`|  
  
## <a name="output-pointer-parameters"></a>포인터 매개 변수 출력  
 출력 포인터 매개 변수에는 매개 변수 및 가리킨 위치에서 null을 구분 하기 위해 특수 한 표기법이 필요 합니다.  
  
 **주석 및 설명**  
  
- `_Outptr_`  
  
   매개 변수는 null 일 수 없으며 사후 상태에서 가리키는 위치는 null 일 수 없으며 유효한 상태 여야 합니다.  
  
- `_Outptr_opt_`  
  
   매개 변수는 null 일 수 있지만 사후 상태에서 위치가 null 일 수 없으며 유효한 상태 여야 합니다.  
  
- `_Outptr_result_maybenull_`  
  
   매개 변수는 null 일 수 없으며 사후 상태에서 가리키는 위치는 null 일 수 있습니다.  
  
- `_Outptr_opt_result_maybenull_`  
  
   매개 변수는 null 일 수 있으며, 사후 상태에서 가리키는 위치는 null 일 수 있습니다.  
  
  다음 표에서는 주석의 의미를 더 한정 하기 위해 주석 이름에 추가 부분 문자열이 삽입 됩니다.  다양 한 부분 문자열은 `_z` ,, `_COM_` `_buffer_` , `_bytebuffer_` 및 `_to_` 입니다.  
  
> [!IMPORTANT]
> 주석을 추가할 인터페이스가 COM 인 경우 이러한 주석의 COM 폼을 사용 합니다. 다른 형식 인터페이스에는 COM 주석을 사용 하지 마십시오.  
  
 **주석 및 설명**  
  
- `_Outptr_result_z_`  
  
   `_Outptr_opt_result_z_`  
  
   `_Outptr_result_maybenull_z_`  
  
   `_Ouptr_opt_result_maybenull_z_`  
  
   반환 된 포인터에 `_Null_terminated_` 주석이 있습니다.  
  
- `_COM_Outptr_`  
  
   `_COM_Outptr_opt_`  
  
   `_COM_Outptr_result_maybenull_`  
  
   `_COM_Outptr_opt_result_maybenull_`  
  
   반환 된 포인터에는 COM 의미 체계가 있으므로 반환 된 `_On_failure_` 포인터가 null 인 사후 조건을 전달 합니다.  
  
- `_Outptr_result_buffer_(s)`  
  
   `_Outptr_result_bytebuffer_(s)`  
  
   `_Outptr_opt_result_buffer_(s)`  
  
   `_Outptr_opt_result_bytebuffer_(s)`  
  
   반환 된 포인터는 크기 요소 또는 바이트의 올바른 버퍼를 가리킵니다 `s` .  
  
- `_Outptr_result_buffer_to_(s, c)`  
  
   `_Outptr_result_bytebuffer_to_(s, c)`  
  
   `_Outptr_opt_result_buffer_to_(s,c)`  
  
   `_Outptr_opt_result_bytebuffer_to_(s,c)`  
  
   반환 된 포인터는 `s` 첫 번째가 유효한 크기의 요소 또는 바이트의 버퍼를 가리킵니다 `c` .  
  
  특정 인터페이스 규칙은 출력 매개 변수가 실패 시 무효화 것으로 가정 합니다.  명시적 COM 코드를 제외 하 고 다음 표에 나와 있는 폼을 선호 합니다.  COM 코드의 경우 이전 섹션에 나열 된 해당 COM 폼을 사용 합니다.  
  
  **주석 및 설명**  
  
- `_Result_nullonfailure_`  
  
   다른 주석을 수정 합니다. 함수가 실패 하면 결과가 null로 설정 됩니다.  
  
- `_Result_zeroonfailure_`  
  
   다른 주석을 수정 합니다. 함수가 실패 하는 경우 결과는 0으로 설정 됩니다.  
  
- `_Outptr_result_nullonfailure_`  
  
   반환 된 포인터는 함수가 성공 하는 경우 유효한 버퍼를 가리키거나 함수가 실패 하면 null입니다. 이 주석은 선택적인 매개 변수를 위한 것입니다.  
  
- `_Outptr_opt_result_nullonfailure_`  
  
   반환 된 포인터는 함수가 성공 하는 경우 유효한 버퍼를 가리키거나 함수가 실패 하면 null입니다. 이 주석은 선택적 매개 변수에 대 한 것입니다.  
  
- `_Outref_result_nullonfailure_`  
  
   반환 된 포인터는 함수가 성공 하는 경우 유효한 버퍼를 가리키거나 함수가 실패 하면 null입니다. 이 주석은 참조 매개 변수에 대 한 것입니다.  
  
## <a name="output-reference-parameters"></a>참조 매개 변수 출력  
 참조 매개 변수는 일반적으로 output 매개 변수에 사용 됩니다.  간단한 출력 참조 매개 변수의 경우 (예: `int&` ) `_Out_` 는 올바른 의미 체계를 제공 합니다.  그러나 출력 값이 포인터인 경우 `int *&` 와 같이 동일한 포인터 주석이 `_Outptr_ int **` 올바른 의미 체계를 제공 하지 않는 경우를 예로 들 수 있습니다.  포인터 형식에 대 한 출력 참조 매개 변수의 의미를 간결 하 게 표현 하려면 다음 복합 주석을 사용 합니다.  
  
 **주석 및 설명**  
  
- `_Outref_`  
  
     결과는 사후 상태에서 유효 해야 하며 null 일 수 없습니다.  
  
- `_Outref_result_maybenull_`  
  
     결과는 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다.  
  
- `_Outref_result_buffer_(s)`  
  
     결과는 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 는 크기 요소의 올바른 버퍼를 가리킵니다 `s` .  
  
- `_Outref_result_bytebuffer_(s)`  
  
     결과는 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 는 크기 바이트의 올바른 버퍼를 가리킵니다 `s` .  
  
- `_Outref_result_buffer_to_(s, c)`  
  
     결과는 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 는 `s` 첫 번째가 유효한 요소의 버퍼를 가리킵니다 `c` .  
  
- `_Outref_result_bytebuffer_to_(s, c)`  
  
     결과는 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 는 `s` 첫 번째가 유효한 바이트의 버퍼를 가리킵니다 `c` .  
  
- `_Outref_result_buffer_all_(s)`  
  
     결과는 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 올바른 크기의 유효한 버퍼를 가리킵니다 `s` .  
  
- `_Outref_result_bytebuffer_all_(s)`  
  
     결과는 사후 상태에서 유효 해야 하며 null 일 수 없습니다. 유효한 요소의 올바른 바이트 버퍼를 가리킵니다 `s` .  
  
- `_Outref_result_buffer_maybenull_(s)`  
  
     결과는 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다. 는 크기 요소의 올바른 버퍼를 가리킵니다 `s` .  
  
- `_Outref_result_bytebuffer_maybenull_(s)`  
  
     결과는 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다. 는 크기 바이트의 올바른 버퍼를 가리킵니다 `s` .  
  
- `_Outref_result_buffer_to_maybenull_(s, c)`  
  
     결과는 사후 상태에서 유효 해야 하지만 사후 상태에서 null 일 수 있습니다. 는 `s` 첫 번째가 유효한 요소의 버퍼를 가리킵니다 `c` .  
  
- `_Outref_result_bytebuffer_to_maybenull_(s,c)`  
  
     결과는 사후 상태에서 유효 해야 하지만 post 상태에서 null 일 수 있습니다. 는 `s` 첫 번째가 유효한 바이트의 버퍼를 가리킵니다 `c` .  
  
- `_Outref_result_buffer_all_maybenull_(s)`  
  
     결과는 사후 상태에서 유효 해야 하지만 post 상태에서 null 일 수 있습니다. 올바른 크기의 유효한 버퍼를 가리킵니다 `s` .  
  
- `_Outref_result_bytebuffer_all_maybenull_(s)`  
  
     결과는 사후 상태에서 유효 해야 하지만 post 상태에서 null 일 수 있습니다. 유효한 요소의 올바른 바이트 버퍼를 가리킵니다 `s` .  
  
## <a name="return-values"></a>반환 값  
 함수의 반환 값은 `_Out_` 매개 변수와 비슷하지만 참조의 다른 수준에 있으므로 결과에 대 한 포인터의 개념을 고려할 필요가 없습니다.  다음 주석에서 반환 값은 주석이 추가 된 개체 (스칼라, 구조체에 대 한 포인터 또는 버퍼에 대 한 포인터)입니다. 이러한 주석에는 해당 주석과 동일한 의미 체계가 있습니다 `_Out_` .  
  
`_Ret_z_`, `_Ret_writes_(s)`, `_Ret_writes_bytes_(s)`, `_Ret_writes_z_(s)`, `_Ret_writes_to_(s,c)`, `_Ret_writes_maybenull_(s)`, `_Ret_writes_to_maybenull_(s)`, `_Ret_writes_maybenull_z_(s)`|`_Ret_maybenull_`, `_Ret_maybenull_z_`, `_Ret_null_`, `_Ret_notnull_`, `_Ret_writes_bytes_to_`, `_Ret_writes_bytes_maybenull_`, `_Ret_writes_bytes_to_maybenull_`
  
## <a name="other-common-annotations"></a>기타 일반 주석  
 **주석 및 설명**  
  
- `_In_range_(low, hi)`  
  
     `_Out_range_(low, hi)`  
  
     `_Ret_range_(low, hi)`  
  
     `_Deref_in_range_(low, hi)`  
  
     `_Deref_out_range_(low, hi)`  
  
     `_Deref_inout_range_(low, hi)`  
  
     `_Field_range_(low, hi)`  
  
     매개 변수, 필드 또는 결과가에서 까지의 범위 (포함)입니다 `low` `hi` .  주석이 지정 된 `_Satisfies_(_Curr_ >= low && _Curr_ <= hi)` 개체에 적절 한 사전 상태 또는 사후 상태 조건과 함께 적용 되는와 동일 합니다.  
  
    > [!IMPORTANT]
    > 이름에 "in" 및 "out"이 포함 되어 있지만 및의 의미 체계는 `_In_` `_Out_` 이러한 주석에 적용 **되지** 않습니다.  
  
- `_Pre_equal_to_(expr)`  
  
     `_Post_equal_to_(expr)`  
  
     주석이 추가 된 값은 정확 `expr` 합니다.  주석이 지정 된 `_Satisfies_(_Curr_ == expr)` 개체에 적절 한 사전 상태 또는 사후 상태 조건과 함께 적용 되는와 동일 합니다.  
  
- `_Struct_size_bytes_(size)`  
  
     구조체 또는 클래스 선언에 적용 됩니다.  에서 제공 하는 바이트 수를 사용 하 여 해당 형식의 유효한 개체가 선언 된 형식 보다 클 수 있음을 나타냅니다 `size` .  예를 들면 다음과 같습니다.  
  
     `typedef _Struct_size_bytes_(nSize) struct MyStruct {    size_t nSize;    ... };`  
  
     형식의 매개 변수 버퍼 크기 (바이트)는 `pM` `MyStruct *` 다음과 같습니다.  
  
     `min(pM->nSize, sizeof(MyStruct))`  
  
## <a name="related-resources"></a>관련 리소스  
 [코드 분석 팀 블로그](https://blogs.msdn.com/b/codeanalysis/)  
  
## <a name="see-also"></a>관련 항목  
 [C/c + + 코드 오류를 줄이기 위해 SAL 주석 사용](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)   
 [SAL 이해](../code-quality/understanding-sal.md)   
 [함수 동작에 주석 달기](../code-quality/annotating-function-behavior.md)   
 [구조체 및 클래스에 주석 달기](../code-quality/annotating-structs-and-classes.md)   
 [잠금 동작에 주석 달기](../code-quality/annotating-locking-behavior.md)   
 [주석이 적용 되는 시기 및 위치 지정](../code-quality/specifying-when-and-where-an-annotation-applies.md)   
 [내장 함수](../code-quality/intrinsic-functions.md)   
 [모범 사례 및 예제](../code-quality/best-practices-and-examples-sal.md)
