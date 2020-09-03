---
title: '방법: 계측된 이진 파일 재배치 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.binaries
helpviewer_keywords:
- binaries, instrumented
- instrumentation, instrumented binaries
- instrumented binaries and relocating
- profiling tools, instrumented binaries
ms.assetid: 258f49e8-4b09-477e-a132-8fad685b66f4
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 00b39b91b0a776438199d1df3c212cb9fe40f338
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68155510"
---
# <a name="how-to-relocate-instrumented-binaries"></a>방법: 계측된 이진 파일 재배치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

계측하는 동안 애플리케이션 성능을 측정하기 위해 프로브가 이진 파일에 삽입됩니다. 계측된 이진 파일을 재배치하도록 선택하면 원본 이진 파일의 복사본이 계측되어 지정한 위치에 배치됩니다. 이 옵션은 프로파일러에서 원본 이진 파일의 이름을 바꾸지 않으려는 경우에 유용합니다. 이진 파일을 재배치하지 않으면 이진 파일의 원래 버전을 덮어씁니다.  
  
 **요구 사항**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-relocate-instrumented-binary"></a>계측된 이진 파일을 재배치하려면  
  
1. **성능 탐색기**에서 성능 세션을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.  
  
2. **속성 페이지**에서 **이진 파일** 속성을 클릭합니다.  
  
3. **계측된 이진 파일 재배치** 확인란을 선택합니다.  
  
4. 계측된 이진 파일의 위치를 지정합니다.  
  
## <a name="see-also"></a>관련 항목  
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)   
 [VSInstr](../profiling/vsinstr.md)
