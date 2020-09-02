---
title: 샘플링 데이터 값 이해 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- sampling profiling method
- Profiling Tools, sampling
ms.assetid: fad540a8-24b6-4ff9-91ce-e67e9a58399d
caps.latest.revision: 27
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 91a4a50ecc745c0b56167d6a5dbb1932af7ed2bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145413"
---
# <a name="understanding-sampling-data-values"></a>샘플링 데이터 값 이해
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 프로파일링 도구의 *샘플링* 프로파일링 방법은 설정된 간격으로 컴퓨터 프로세서를 중단하여 함수 호출 스택을 수집합니다. *호출 스택*은 프로세서에서 실행되는 함수에 대한 정보를 저장하는 동적 구조체입니다.  
  
 **요구 사항**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  프로파일러 분석에서는 프로세서가 대상 프로세스에서 코드를 실행하고 있는지 확인합니다. 프로세서가 대상 프로세스에서 코드를 실행하고 있지 않으면 샘플은 삭제됩니다.  
  
  프로세서가 대상 코드를 실행하고 있으면 프로파일러는 호출 스택에서 각 함수의 샘플 개수를 증가시킵니다. 샘플을 가져오는 시간에는 호출 스택에서 하나의 함수만이 현재 코드를 실행하고 있는 상태입니다. 스택의 다른 함수는 자식이 반환되기를 대기 중인 함수 호출 계층의 부모입니다.  
  
  샘플 이벤트의 경우 프로파일러는 현재 명령을 실행 중인 함수의 *전용* 샘플 개수를 증가시킵니다. 전용 샘플은 함수의 전체(*포괄*) 샘플에도 포함되므로 현재 활성 상태인 함수의 포괄 샘플 개수도 증가합니다.  
  
  프로파일러는 호출 스택에 있는 다른 모든 함수의 포괄 샘플 개수를 증가시킵니다.  
  
## <a name="inclusive-samples"></a>포괄 샘플  
 대상 함수 실행 중에 수집된 샘플의 총 수입니다.  
  
 여기에는 함수 코드 직접 실행 중에 수집된 샘플과, 대상 함수가 호출한 자식 함수의 실행 중에 수집된 샘플이 포함됩니다.  
  
## <a name="exclusive-samples"></a>전용 샘플  
 대상 함수의 직접 명령 실행 중에 수집된 샘플의 수입니다.  
  
 대상 함수가 호출한 함수의 실행 중에 수집된 샘플은 전용 샘플에 포함되지 않습니다.  
  
## <a name="inclusive-percent"></a>포함(백분율)  
 프로파일링 실행 내 포괄 샘플 중 함수 또는 데이터 범위의 포괄 샘플 총 수의 백분율입니다.  
  
## <a name="exclusive-percent"></a>제외(백분율)  
 프로파일링 실행 내 전용 샘플 중 함수 또는 데이터 범위의 전용 샘플 총 수의 백분율입니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: 수집 방법 선택](../profiling/how-to-choose-collection-methods.md)   
 [성능 도구 데이터 분석](../profiling/analyzing-performance-tools-data.md)
