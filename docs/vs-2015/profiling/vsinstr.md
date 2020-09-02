---
title: VSInstr | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, instrumentation
- instrumentation, VSInstr tool
- profiling tools,VSInstr
- command-line tools, instrumentation
- command line, tools
- VSInstr
- VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 7b1334f7-f9b0-4a82-a145-d0607bfa8467
caps.latest.revision: 49
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 09562c3372a6dd933d3656f1b2f7ccf7ca68109d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145310"
---
# <a name="vsinstr"></a>VSInstr
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSInstr 도구는 이진 파일을 계측하는 데 사용됩니다. 다음 구문을 사용하여 이 도구를 호출합니다.  
  
```  
VSInstr [/U] filename [/options]  
```  
  
 아래 표에는 VSInstr 도구의 옵션에 대한 설명이 나와 있습니다.  
  
|옵션|설명|  
|-------------|-----------------|  
|**Help** 또는 **?**|도움말을 표시합니다.|  
|**U**|리디렉션된 콘솔 출력을 유니코드로 기록합니다. 첫 번째 옵션으로 지정해야 합니다.|  
|`@filename`|명령 옵션이 한 줄에 하나씩 포함된 지시 파일의 이름을 지정합니다.  따옴표는 사용하지 마세요.|  
|**OutputPath** `:path`|계측된 이미지의 대상 디렉터리를 지정합니다. 출력 경로를 지정하지 않으면 같은 디렉터리에서 파일 이름에 "Orig "가 추가되어 원래 이진 파일 이름이 바뀌며 이진 파일의 복사본이 계측됩니다.|  
|**제외**`:funcspec`|프로브를 통한 계측에서 제외할 함수 사양을 지정합니다. 함수에 프로파일링 프로브를 삽입할 때 예기치 않은 결과 또는 원치 않는 결과가 발생하는 경우 유용합니다.<br /><br /> 같은 이진 파일의 함수를 참조하는 **Exclude** 및 **Include** 옵션은 사용하지 마세요.<br /><br /> 개별 **Exclude** 옵션을 여러 개 포함하여 여러 함수 사양을 지정할 수 있습니다.<br /><br /> `funcspec`은 다음과 같이 정의됩니다.<br /><br /> [namespace\<separator1>] [class\<separator2>]function<br /><br /> \<separator1>은 네이티브 코드의 경우 `::`이고 관리 코드의 경우 `.`입니다.<br /><br /> \<separator2>는 항상 `::`입니다.<br /><br /> **Exclude**는 코드 검사에서 지원됩니다.<br /><br /> 와일드 카드 문자 \*가 지원됩니다. 예를 들어 네임스페이스에서 모든 함수를 제외하려면 다음 구문을 사용합니다.<br /><br /> MyNamespace::\*<br /><br /> **VSInstr /DumpFuncs**를 사용하면 지정한 이진 파일의 전체 함수 이름 목록을 확인할 수 있습니다.|  
|**포함**`:funcspec`|프로브를 사용하여 계측할 이진 파일의 함수 사양을 지정합니다. 이진 파일의 기타 모든 함수는 계측되지 않습니다.<br /><br /> 개별 **Include** 옵션을 여러 개 포함하여 여러 함수 사양을 지정할 수 있습니다.<br /><br /> 같은 이진 파일의 함수를 참조하는 **Include** 및 **Exclude** 옵션은 사용하지 마세요.<br /><br /> **Include**는 코드 검사에서 지원되지 않습니다.<br /><br /> `funcspec`은 다음과 같이 정의됩니다.<br /><br /> [namespace\<separator1>] [class\<separator2>]function<br /><br /> \<separator1>은 네이티브 코드의 경우 `::`이고 관리 코드의 경우 `.`입니다.<br /><br /> \<separator2>는 항상 `::`입니다.<br /><br /> 와일드 카드 문자 \*가 지원됩니다. 예를 들어 네임스페이스의 모든 함수를 포함하려면 다음 구문을 사용합니다.<br /><br /> MyNamespace::\*<br /><br /> **VSInstr /DumpFuncs**를 사용하면 지정한 이진 파일의 전체 함수 이름 목록을 확인할 수 있습니다.|  
|**DumpFuncs**|지정된 이미지 내의 함수 목록을 표시합니다. 계측은 수행되지 않습니다.|  
|**ExcludeSmallFuncs**|함수를 호출하지 않는 짧은 함수인 작은 함수를 계측에서 제외합니다. **ExcludeSmallFuncs** 옵션을 사용하는 경우 계측 오버헤드가 감소하므로 계측 속도를 높일 수 있습니다.<br /><br /> 또한 작은 함수를 제외하면 .vsp 파일의 크기와 분석에 필요한 시간도 감소합니다.|  
|**Mark:** {**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname,markid`|.vsp 보고서 파일에서 데이터 범위의 시작이나 끝을 식별하는 데 사용할 수 있는 프로필 표시(보고서의 데이터를 구분하는 데 사용되는 식별자)를 삽입합니다.<br /><br /> **Before** - 대상 함수 진입 위치 바로 앞에 삽입합니다.<br /><br /> **After** - 대상 함수 종료 위치 바로 뒤에 삽입합니다.<br /><br /> **Top** - 대상 함수의 진입 위치 바로 뒤에 삽입합니다.<br /><br /> **Bottom** - 대상 함수의 각 반환 바로 앞에 삽입합니다.<br /><br /> `funcname` - 대상 함수의 이름입니다.<br /><br /> `Markid` - 프로필 표시의 식별자로 사용할 양의 정수(long)입니다.|  
|**Coverage**|검사 계측을 수행합니다. **Verbose**, **OutputPath**, **Exclude**, **Logfile** 옵션과 함께 사용해야 합니다.|  
|**Verbose**|**Verbose** 옵션은 계측 프로세스에 대한 자세한 정보를 확인하는 데 사용됩니다.|  
|**NoWarn** `[:[Message Number[;Message Number]]]`|모든 경고를 표시하지 않거나 특정 경고를 표시하지 않습니다.<br /><br /> `Message Number` - 경고 번호입니다. `Message Number`를 생략 하면 모든 경고가 표시되지 않습니다.<br /><br /> 자세한 내용은 [VSInstr 경고](../profiling/vsinstr-warnings.md)를 참조하세요.|  
|**컨트롤** `:{` **스레드** `&#124;` **프로세스** `&#124;` **전역**`}`|다음 VSInstr 데이터 수집 제어 옵션의 프로파일링 수준을 지정합니다.<br /><br /> **Start**<br /><br /> **StartOnly**<br /><br /> **Suspend**<br /><br /> **StopOnly**<br /><br /> **SuspendOnly**<br /><br /> **ResumeOnly**<br /><br /> **Thread** - 스레드 수준 데이터 수집 제어 함수를 지정합니다. 현재 스레드에 대해서만 프로파일링이 시작되거나 중지됩니다. 다른 스레드의 프로파일링 상태는 영향을 받지 않습니다. 기본값은 thread입니다.<br /><br /> **Process** - 프로세스 수준 프로파일링 데이터 수집 제어 함수를 지정합니다. 현재 프로세스의 모든 스레드에 대해 프로파일링이 시작되거나 중지됩니다. 다른 프로세스의 프로파일링 상태는 영향을 받지 않습니다.<br /><br /> **Global** - 전역 수준(프로세스 간) 데이터 수집 제어 함수를 지정합니다.<br /><br /> 프로파일링 수준을 지정하지 않으면 오류가 발생합니다.|  
|**시작** `:{` **내부** `&#124;` **외부**`},funcname`|대상 함수 및 해당 함수가 호출하는 자식 함수로 데이터 수집을 제한합니다.<br /><br /> **Inside** - 대상 함수로의 진입 위치 바로 뒤에 StartProfile 함수를 삽입합니다. 대상 함수의 각 반환 바로 앞에 StartProfile 함수를 삽입합니다.<br /><br /> **Outside** - 각 대상 함수 호출 바로 앞에 StartProfile 함수를 삽입합니다. 각 대상 함수 호출 바로 뒤에 StopProfile 함수를 삽입합니다.<br /><br /> `funcname` - 대상 함수의 이름입니다.|  
|**일시 중단** `:{` **내부** `&#124;` **외부**`},funcname`|대상 함수 및 해당 함수가 호출하는 자식 함수에 대한 데이터 수집을 제외합니다.<br /><br /> **Inside** - 대상 함수로의 진입 위치 바로 뒤에 SuspendProfile 함수를 삽입합니다. 대상 함수의 각 반환 바로 앞에 ResumeProfile 함수를 삽입합니다.<br /><br /> **Outside** - 대상 함수로의 진입 위치 바로 앞에 SuspendProfile 함수를 삽입합니다. 대상 함수의 종료 위치 바로 뒤에 ResumeProfile 함수를 삽입합니다.<br /><br /> `funcname` - 대상 함수의 이름입니다.<br /><br /> 대상 함수가 StartProfile 함수를 포함하는 경우에는 그 앞에 SuspendProfile 함수가 삽입됩니다. 대상 함수가 StopProfile 함수를 포함하는 경우에는 그 뒤에 ResumeProfile 함수가 삽입됩니다.|  
|**StartOnly:** `{` **Before** `&#124;` **After** `&#124;` **Top** `&#124;` **Bottom** `},funcname`|프로파일링 실행 중에 데이터 수집을 시작합니다. 지정된 위치에 StartProfile API 함수를 삽입합니다.<br /><br /> **Before** - 대상 함수 진입 위치 바로 앞에 삽입합니다.<br /><br /> **After** - 대상 함수 종료 위치 바로 뒤에 삽입합니다.<br /><br /> **Top** - 대상 함수의 진입 위치 바로 뒤에 삽입합니다.<br /><br /> **Bottom** - 대상 함수의 각 반환 바로 앞에 삽입합니다.<br /><br /> `funcname` - 대상 함수의 이름입니다.|  
|**StopOnly:** {**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname`|프로파일링 실행 중에 데이터 수집을 중지합니다. 지정된 위치에 StopProfile 함수를 삽입합니다.<br /><br /> **Before** - 대상 함수 진입 위치 바로 앞에 삽입합니다.<br /><br /> **After** - 대상 함수 종료 위치 바로 뒤에 삽입합니다.<br /><br /> **Top** - 대상 함수의 진입 위치 바로 뒤에 삽입합니다.<br /><br /> **Bottom** - 대상 함수의 각 반환 바로 앞에 삽입합니다.<br /><br /> `funcname` - 대상 함수의 이름입니다.|  
|**SuspendOnly:** {**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname`|프로파일링 실행 중에 데이터 수집을 중지합니다. 지정된 위치에 SuspendProfile API를 삽입합니다.<br /><br /> **Before** - 대상 함수 진입 위치 바로 앞에 삽입합니다.<br /><br /> **After** - 대상 함수 종료 위치 바로 뒤에 삽입합니다.<br /><br /> **Top** - 대상 함수의 진입 위치 바로 뒤에 삽입합니다.<br /><br /> **Bottom** - 대상 함수의 각 반환 바로 앞에 삽입합니다.<br /><br /> `funcname` - 대상 함수의 이름입니다.<br /><br /> 대상 함수가 StartProfile 함수를 포함하는 경우에는 그 앞에 SuspendProfile 함수가 삽입됩니다.|  
|**ResumeOnly:** {**Before**`&#124;`**After**`&#124;`**Top**`&#124;`**Bottom**}`,funcname`|프로파일링 실행 중에 데이터 수집을 시작하거나 다시 시작합니다.<br /><br /> 일반적으로 **SuspendOnly** 옵션이 프로파일링을 중지한 후 프로파일링을 시작하는 데 사용됩니다. 지정된 위치에 ResumeProfile API를 삽입합니다.<br /><br /> **Before** - 대상 함수 진입 위치 바로 앞에 삽입합니다.<br /><br /> **After** - 대상 함수 종료 위치 바로 뒤에 삽입합니다.<br /><br /> **Top** - 대상 함수의 진입 위치 바로 뒤에 삽입합니다.<br /><br /> **Bottom** - 대상 함수의 각 반환 바로 앞에 삽입합니다.<br /><br /> `funcname` - 대상 함수의 이름입니다.<br /><br /> 대상 함수가 StopProfile 함수를 포함하는 경우에는 그 뒤에 ResumeProfile 함수가 삽입됩니다.|  
  
## <a name="see-also"></a>관련 항목  
 [Vsperfmon.exe](../profiling/vsperfmon.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [VSInstr 경고](../profiling/vsinstr-warnings.md)   
 [성능 보고서 뷰](../profiling/performance-report-views.md)
