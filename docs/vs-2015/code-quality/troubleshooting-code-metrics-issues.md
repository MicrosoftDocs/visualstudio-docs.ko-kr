---
title: 코드 메트릭 문제 해결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: troubleshooting
ms.assetid: f2fdb995-4888-4246-85dc-7bacadd45968
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b4d374a2737e2ce8892304b615bebcf99d9c60ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672447"
---
# <a name="troubleshooting-code-metrics-issues"></a>코드 메트릭 문제 해결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 메트릭을 수집할 때 다음 문제 중 일부가 발생할 수 있습니다.

- [Visual Studio 2010 코드 복잡성 계산에 대한 변경 내용](#Changes_in_Visual_Studio_2010_code_complexity_calculations)

## <a name="changes-in-visual-studio-2010-code-complexity-calculations"></a><a name="Changes_in_Visual_Studio_2010_code_complexity_calculations"></a> Visual Studio 2010 코드 복잡성 계산의 변경 내용
 동일한 함수의 경우 다음 상황에서 [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]에서 계산 된 코드 복잡성 메트릭이 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]의 이전 버전으로 계산된 메트릭과 다를 수 있습니다.

- 이 함수는 하나 이상의 catch 블록을 포함합니다. [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]의 이전 버전에서 catch 블록은 계산에 포함되지 않았습니다. [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]에서 각 catch 블록의 복잡성은 함수의 복잡성에 추가됩니다.

- 함수는 switch 문(VB에서 Select Case)을 포함합니다. [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]과 이전 버전 간의 컴파일러 차이점은 제어 이동 사례가 포함된 일부 switch 문에 대해 서로 다른 MSIL 코드를 생성할 수 있습니다.

## <a name="see-also"></a>관련 항목
 [관리 코드의 복잡성 및 유지 관리 용이성 측정](../code-quality/measuring-complexity-and-maintainability-of-managed-code.md)
