---
title: '방법: 기호 정보 직렬화 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.Performance.General
helpviewer_keywords:
- profiling tools, serializing symbol information
- performance tools, serializing symbol information
ms.assetid: 9e0da706-6325-4073-83d1-aeab3b7c137a
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c4ea056c48525014fffad0243dfeb4dd40a8daa3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65687018"
---
# <a name="how-to-serialize-symbol-information"></a>방법: 기호 정보 직렬화
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

애플리케이션을 분석하기 위해 포함해야 하는 기호를 직렬화할 수 있습니다. 기호를 직렬화하면 기호가 .vsp 파일에 추가됩니다. 기호 정보를 .vsp 파일에 추가하면 다른 사용자가 원래 기호에 대한 액세스 권한이 없어도 성능 보고서를 분석할 수 있습니다. 기호가 직렬화되지 않은 경우 .vsp 파일을 분석하려면 원래 계측된 .exe 및 .pdb 파일이 있어야 합니다.  
  
### <a name="to-automatically-serialize-symbol-information"></a>기호 정보를 자동으로 직렬화하려면  
  
1. **도구** 메뉴에서 **옵션**을 클릭합니다.  
  
     **옵션** 대화 상자가 표시됩니다.  
  
2. **성능 도구**를 클릭합니다.  
  
3. **일반 설정**에서 **자동으로 기호 정보 직렬화**를 선택합니다.  
  
## <a name="see-also"></a>관련 항목  
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)   
 [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)   
 [방법: 분석 된 보고서 파일 저장](https://msdn.microsoft.com/0340ddde-caf4-48ac-8af3-d15dcdade556)
