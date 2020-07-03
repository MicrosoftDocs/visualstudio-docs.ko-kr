---
title: VSInstr 경고 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- instrumentation, VSInstr tool
- warnings
- VSInstr tool
- warnings, VSInstr tool
- performance tools, VSInstr tool
ms.assetid: 47512bc9-a8e9-4628-883a-d9888edab786
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 3af98372102da49e7553d2f2992f3804cf0a619e
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85330545"
---
# <a name="vsinstr-warnings"></a>VSInstr 경고
다음 표에는 *VSInstr.exe* 도구에서 발생되는 경고가 나와 있습니다. 경고 번호와 NOWARN 옵션을 함께 사용하여 경고가 표시되지 않도록 할 수 있습니다.

|경고 번호|설명|
|--------------------|-----------------|
|**VSP1026**|검사는 MSCorLib를 참조하지 않는 라이브러리에서 지원되지 않습니다. 대체로 이식 가능한 라이브러리의 경우가 여기에 해당합니다.<br /><br />.NET Core에는 [/EnableCodeCoverage](../test/vstest-console-options.md) 명령줄 옵션이 필요합니다.|
|**VSP2000**|내부 오류입니다. 이 실행 파일에 대한 모듈 파일 이름을 가져올 수 없습니다.|
|**VSP2001**|\<assembly name>은 강력한 이름의 어셈블리입니다. 다시 서명해야 실행할 수 있습니다.<br /><br /> 이 경고는 서명된 어셈블리를 계측하는 경우에 발생합니다. *sn.exe* 도구를 사용하여 이진 파일에 다시 서명하거나 강력한 이름 요구를 일시적으로 해제할 수 있습니다. 자세한 내용은 [Sn.exe(강력한 이름 도구)](/dotnet/framework/tools/sn-exe-strong-name-tool)를 참조하세요.|
|**VSP2002**|\<filename> 파일에서 \<funcname> 함수를 찾을 수 없습니다.<br /><br /> 이 경고는 지정한 파일에는 함수를 찾을 수 없는 경우에 발생합니다.|
|**VSP2003**|\<filename> 파일에서 \<funcname> 함수로의 크로스 점프를 찾을 수 없습니다.<br /><br /> 이 경고는 VSInstr이 크로스 점프를 무효화할 수 없는 경우에 발생합니다. 크로스 점프는 코드 최적화를 위해 사용됩니다.|
|**VSP2004**|\<funcname> 함수가 EXCLUDE 명령줄 스위치를 통해 제외되었지만 이 함수에 크로스 점프가 들어 있으므로 필요합니다.<br /><br /> 이 경고는 함수가 EXCLUDE 옵션을 사용하여 제외되었으나 계측 프로세스 중에 필요한 경우에 발생합니다. 프로파일러에는 필요한 기능을 자동으로 포함합니다.|
|**VSP2005**|내부 계측 오류 \<error text><br /><br /> 이 경고는 계측을 수행할 수 없는 경우에 발생합니다. 오류 텍스트를 검토하여 수정할 수 있는지 여부를 확인합니다.|
|**VSP2006**|\<name>의 PDB를 찾을 수 없습니다.<br /><br /> 이 경고는 PDB 파일이 검색 경로에 존재하지 않거나 이진 파일과 일치하지 않는 경우에 발생합니다.|
|**VSP2007**|\<filename>에 계측 가능한 코드가 없습니다.<br /><br /> 이 경고는 이진 파일의 함수가 모두 제외되었거나 지정된 파일에 리소스만 포함되어 있는 경우에 발생합니다.|
|**VSP2008**|\<name>에서 보안 특성을 가져올 수 없습니다. 오류 코드 \<code><br /><br /> 이 경고는 사용자에게 READ_DAC 권한이 없는 경우에 발생합니다. 계측 프로세스 동안 프로파일러는 이진 파일에 대한 원래 DACL을 유지하려고 합니다. 이진 파일이 새 이진 파일로 바뀌므로 원래 이진의 DACL이 복사되고 새 이진 파일에 적용되어야 합니다. 사용자에게 원래 이진 파일에 대한 READ_DAC 액세스 권한이 없으므로 이 작업은 실패할 수 있습니다.|
|**VSP2009**|\<name>에 보안 특성을 설정할 수 없습니다. 오류 코드 \<error number><br /><br /> 이 경고는 사용자에게 WRITE_DAC 권한이 없는 경우에 발생합니다. 계측 프로세스 동안 프로파일러는 이진 파일에 대한 원래 DACL을 유지하려고 합니다. 이진 파일이 새 이진 파일로 바뀌므로 원래 이진의 DACL이 복사되고 새 이진 파일에 적용되어야 합니다. 사용자에게 새 이진 파일에 대한 WRITE_DAC 액세스 권한이 없으므로 이 작업은 실패할 수 있습니다.|
|**VSP2010**|-INCLUDE/-EXCLUDE 옵션 때문에 계측하기 위해 선택한 함수가 없습니다.D;A;|
|**VSP2011**|Include/Exclude funcspec \<name>이 다른 함수와 일치하지 않습니다.|
|**VSP2012**|이 이미지에 코드 검사를 위해 계측할 수 있는 코드가 없습니다.<br /><br /> 프로파일러는 다음과 같은 형식의 코드를 계측하지 않습니다.<br /><br /> -   정적 CRT 함수<br />-   NonUserCodeAttribute로 특성이 지정된 관리되는 메서드<br />-   DebuggerHiddenAttribute로 특성이 지정된 관리되는 메서드<br />-   MASM 블록<br /><br /> 이 경고는 이 필터링 후 남은 코드가 없을 때 생성됩니다.|
|**VSP2013**|이 이미지를 계측하려면 32비트 프로세스로 실행해야 합니다. CLR 헤더 플래그가 이를 반영하도록 업데이트되었습니다.<br /><br /> 프로파일러는 64비트 운영 체제가 WOW64 에뮬레이터에서 32비트 프로세스를 열 수 있도록 이진 파일을 수정합니다. 라이브러리(DLL)의 경우 기존 64비트 프로세스에서 로드되면 실패할 수 있습니다. 이 경고는 사용자에게 종속 관계를 알립니다.|
|**VSP2014**|결과로 나오는 계측된 이미지가 잘못 표시되어 실행되지 않을 수 있습니다.<br /><br /> 이 메시지는 최종 계측된 어셈블리에 잘못된 PE 헤더가 있을 때 발생합니다.|

## <a name="see-also"></a>참조
- [VSInstr](../profiling/vsinstr.md)
