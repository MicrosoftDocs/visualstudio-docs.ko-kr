---
title: CRT 디버그 라이브러리 사용 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7e14a181b432dede3f00a4465d40154fdb393bb0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65697853"
---
# <a name="crt-debug-library-use"></a>CRT 디버그 라이브러리 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C 런타임 라이브러리는 디버깅을 폭넓게 지원합니다. CRT 디버그 라이브러리 중 하나를 사용하려면 [/DEBUG](https://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103)로 연결하고 **/MDd**, **/MTd** 또는 **/LDd**로 컴파일해야 합니다.  
  
## <a name="remarks"></a>설명  
 CRT 디버깅의 주요 정의와 매크로는 CRTDBG.h 헤더 파일에 포함되어 있습니다.  
  
 CRT 디버그 라이브러리의 함수는 최적화 없이 디버그 정보([/Z7, /Zd, /Zi, /ZI(디버깅 정보 형식)](https://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8))를 사용하여 컴파일됩니다. 일부 함수는 함수에 전달된 매개 변수를 확인하기 위해 어설션을 사용하며 소스 코드를 제공합니다. 이 소스 코드를 사용하면 CRT 함수를 단계적으로 실행하여 원하는 대로 함수가 작동하고 있는지 확인하고 잘못된 매개 변수나 메모리 상태를 검사할 수 있습니다. 일부 CRT 기술은 독점되어 있어서 예외 처리, 부동 소수점 및 다른 몇 가지 루틴에 대한 소스 코드를 제공하지 않습니다.  
  
 Visual C++를 설치할 때 하드 디스크에 C 런타임 라이브러리 소스 코드를 설치할지 선택할 수 있습니다. 소스 코드를 설치하지 않으면 CD-ROM을 사용하여 CRT 함수를 단계적으로 실행해야 합니다.  
  
 사용할 수 있는 런타임 라이브러리에 대한 자세한 내용은 [C 런타임 라이브러리](https://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [CRT 디버깅 기술](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD(런타임 라이브러리 사용)](https://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
