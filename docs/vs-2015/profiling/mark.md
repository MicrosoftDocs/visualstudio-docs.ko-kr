---
title: 표시 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e6d7902ec588af2687b048639a930847ec02b3fa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155790"
---
# <a name="mark"></a>표시
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

VSPerfCmd.exe **Mark** 옵션은 프로파일링 데이터 파일에 지정된 정보를 삽입합니다. Mark는 별도 VSPerfReport 보고서 또는 프로파일러 UI의 표시 보고서 보기에 나열될 수 있습니다. **Mark**는 보고서 및 보기 필터에서 시작점과 끝점을 지정하는 데 사용될 수 있습니다.  
  
 **Mark** 옵션은 명령줄에 지정된 유일한 옵션이어야 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]  
```  
  
#### <a name="parameters"></a>매개 변수  
 `MarkID`  
 프로파일러 보기 및 보고서에서 표시 ID로 나열되는 사용자 지정 정수입니다. `MarkID`는 고유할 필요가 없습니다.  
  
 `MarkName`  
 (선택 사항) 프로파일러 보기 및 보고서에서 표시 이름으로 나열되는 사용자 지정 문자열입니다. `MarkName`이 지정되지 않은 경우 나열된 표시의 표시 이름 필드는 비어 있습니다. 따옴표에서 공백 또는 슬래시("/")가 포함된 문자열을 묶습니다.  
  
## <a name="example"></a>예제  
 이 예제에서는 ID 123으로 표시 및 "TestMark"의 표시 이름을 삽입합니다.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
