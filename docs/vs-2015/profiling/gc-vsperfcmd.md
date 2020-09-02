---
title: GC(VSPerfCmd) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 7c81e88b-a748-4cf5-a7a1-3429608e1b54
caps.latest.revision: 17
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2bdb28f74dd305dc497521e95d38e00192c21c54
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68193598"
---
# <a name="gc-vsperfcmd"></a>GC(VSPerfCmd)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**GC** 옵션은 .NET Framework 메모리 할당 및 개체 수명 데이터의 수집을 활성화합니다. **GC** 옵션은 샘플링 프로파일링 방법 및 **Launch** 옵션과만 사용할 수 있습니다.  
  
 **GC** 옵션을 사용하는 경우 VSPerfClrEnv **/sampleon** 명령은 필요하지 않습니다.  
  
 매개 변수가 지정되지 않거나 **Allocation** 매개 변수가 지정된 경우 .NET Framework 메모리 할당 데이터만 수집됩니다. **Lifetime** 매개 변수가 지정된 경우 .NET Framework 메모리 할당 및 .NET Framework 개체 수명 데이터가 모두 수집됩니다.  
  
## <a name="syntax"></a>구문  
  
```  
VSPerfCmd.exe /Launch:AppName /GC[:{Allocation|Lifetime}] [Options]  
```  
  
#### <a name="parameters"></a>매개 변수  
 **Allocation**  
 기본값 .NET Framework 메모리 할당 데이터를 수집합니다.  
  
 **수명**  
 .NET Framework 메모리 할당 데이터 및 NET Framework 개체 수명 데이터를 모두 수집합니다.  
  
## <a name="required-options"></a>필수 옵션  
 **GC** 옵션은 **Launch** 옵션에만 사용할 수 있습니다.  
  
 **시작:**`AppName`  
 지정된 애플리케이션을 시작하고 샘플링 방법으로 프로파일링을 시작합니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 애플리케이션을 시작하고 .NET Framework 메모리 할당 데이터를 수집합니다.  
  
```  
VSPerfCmd.exe /Launch:TestApp.exe /gc  
```  
  
## <a name="see-also"></a>관련 항목  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [독립 실행형 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [ASP.NET 웹 응용 프로그램 프로 파일링](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [서비스 프로파일링](../profiling/command-line-profiling-of-services.md)
