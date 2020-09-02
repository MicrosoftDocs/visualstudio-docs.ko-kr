---
title: 의사 변수 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Watch window, pseudovariables
- debugging [Visual Studio], pseudovariables
- pseudovariables
ms.assetid: fae84f68-2138-4144-9bd4-c9e271b6182a
caps.latest.revision: 40
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e9ce72d69cb64b0421771324803a785546fa884f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65693760"
---
# <a name="pseudovariables"></a>의사 변수
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

의사 변수는 변수 창이나 **간략한 조사식** 대화 상자에서 특정 정보를 표시하는 데 사용되는 용어입니다. 일반적인 변수와 같은 방식으로 의사 변수를 입력할 수 있습니다. 하지만 의사 변수는 변수가 아니며 프로그램에서 변수 이름에 해당되지 않습니다.  
  
## <a name="example"></a>예제  
 네이티브 코드 애플리케이션을 작성 중이며 애플리케이션에 할당된 핸들 수를 표시하려고 한다고 가정합니다. **조사식** 창에서 **이름** 열에 다음 의사 변수를 입력한 다음, 반환을 누르면 핸들 수가 계산됩니다.  
  
```  
$handles  
```  
  
 다음 테이블에 표시된 의사 변수는 네이티브 코드에 사용할 수 있습니다.  
  
|의사 변수|기능|  
|--------------------|--------------|  
|`$err`|SetLastError 함수로 설정된 마지막 오류 값을 표시합니다. 표시된 값은 GetLastError 함수에 의해 반환되는 값입니다.<br /><br /> `$err,hr`을 사용하면 이 값이 디코딩된 형태를 확인할 수 있습니다. 예를 들어 마지막 오류가 3이었다면 `$err,hr`은 `ERROR_PATH_NOT_FOUND : The system cannot find the path specified.`를 표시합니다.|  
|`$handles`|애플리케이션에 할당된 핸들 수를 표시합니다.|  
|`$vframe`|현재 스택 프레임의 주소를 표시합니다.|  
|`$tid`|현재 스레드의 스레드 ID를 표시합니다.|  
|`$env`|문자열 뷰어의 환경 블록을 표시합니다.|  
|`$cmdline`|프로그램을 시작한 명령줄 문자열을 표시합니다.|  
|`$pid`|프로세스 ID를 표시합니다.|  
|`$` *registername*<br /><br /> 또는<br /><br /> `@` *registername*|레지스터*registername*의 내용을 표시합니다.<br /><br /> 일반적으로 레지스터 이름 입력만으로 레지스터 내용을 표시할 수 있습니다. 이 구문은 레지스터 이름이 변수 이름을 오버로드하는 경우에만 사용하게 됩니다. 레지스터 이름이 현재 범위의 변수 이름과 같다면 디버거는 해당 이름을 변수 이름으로 해석합니다. 따라서 이 경우에 `$`*registername* 또는 `@`*registername*을 유용하게 사용할 수 있습니다.|  
|`$clk`|클록 주기 시간을 표시합니다.|  
|`$user`|애플리케이션을 실행한 계정의 계정 정보가 포함된 구조체를 표시합니다. 보안상의 이유로 암호 정보는 표시되지 않습니다.|  
|`$exceptionstack`|현재 Windows 런타임 예외에 대한 스택 추적을 표시합니다. `$ exceptionstack` Windows 8.1 이상에서 실행 되는 스토어 앱 에서만 작동 합니다. C++ 및 SHE 예외에는 `$ exceptionstack`이 지원되지 않습니다.|  
|`$ReturnValue`|.NET Framework 메서드의 반환 값을 표시합니다. [메서드 호출의 반환 값 검사를](https://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f) 참조 하십시오.|  
  
 다음 테이블에 표시된 의사 변수는 C# 및 Visual Basic에서 사용할 수 있습니다.  
  
|의사 변수|기능|  
|--------------------|--------------|  
|`$exception`|마지막 예외에 대한 정보를 표시합니다. 예외가 발생하지 않은 경우에 `$exception`을 계산하면 오류 메시지가 표시됩니다.<br /><br /> Visual C#에 한해, 예외 도우미를 사용하지 않도록 설정한 경우 예외가 발생하면 `$exception`이 **로컬** 창에 자동으로 추가됩니다.|  
|`$user`|애플리케이션을 실행한 계정의 계정 정보가 포함된 구조체를 표시합니다. 보안상의 이유로 암호 정보는 표시되지 않습니다.|  
  
 다음 테이블에 표시된 의사 변수는 Visual Basic에서 사용할 수 있습니다.  
  
|의사 변수|기능|  
|--------------------|--------------|  
|`$delete` 또는 `$$delete`|**직접 실행** 창에서 만들어진 암시적 변수를 삭제합니다. 구문은 `$delete,` *변수* 또는`$delete,` *변수*`.`입니다.|  
|`$objectids` 또는 `$listobjectids`|모든 활성 개체 ID를 지정된 식의 자식으로 표시합니다. 구문은 `$objectid,` *식* 또는`$listobjectids,` *식*`.`입니다.|  
|`$` *N* `#`|개체 ID가 *N*인 개체를 표시합니다.|  
|`$dynamic`|`IDynamicMetaObjectProvider`. 인터페이스를 구현한 개체에 대해 특별한 **동적 뷰** 노드를 표시합니다. 구문은 `$dynamic,` *개체*입니다. 이 기능은 .NET Framework 버전 4가 사용되는 코드에만 적용됩니다. [동적 뷰](https://msdn.microsoft.com/library/4c851b17-2c12-46a0-9828-eb6ea6f5c563)를 참조 하세요.|  
  
## <a name="see-also"></a>관련 항목  
 [조사식 및 간략 한 조사식 창](../debugger/watch-and-quickwatch-windows.md)   
 [변수 창](https://msdn.microsoft.com/library/ce0a67f6-2502-4b7a-ba45-cc32f8aeba3e)
