---
title: 기호 공급자 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- symbol handler
- debugging [Debugging SDK], symbol handler
ms.assetid: 5fce651b-fead-4418-81b0-a011df7644ab
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6af1af9d2e178241fa8a5957e18c1a5333fa4b09
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68178896"
---
# <a name="symbol-provider"></a>기호 공급자
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

식 계산기 구현은 변수와 식을 계산 하기 위해 언어 컴파일러에 의해 생성 된 기호화 된 디버그 정보에 액세스 해야 합니다. 기호 처리기 라고도 하는 SP (기호 공급자)의 인터페이스를 사용 하 여이를 수행 합니다.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] PDB (프로그램 데이터베이스) 기호 파일 형식을 사용 하 여 네이티브 코드 및 관리 코드에 대 한 SPs를 제공 합니다. 프로그램에서 사용자 지정 형식으로 저장 된 기호를 사용 해야 하는 경우를 제외 하 고에서 제공 하는 SPs를 사용 하는 것이 좋습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
## <a name="implementation-notes"></a>구현 노트  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]디버그 엔진은 CLR (공용 언어 런타임) 인터페이스를 사용 하 여 SPs와 통신할 것으로 간주 합니다. 결과적으로, Visual Studio 디버그 엔진을 사용 하는 SP는 CLR을 지원 해야 합니다. 모든 CLR 디버깅 인터페이스의 전체 목록은의 일부인 debugref.doc에서 찾을 수 있습니다 [!INCLUDE[winsdklong](../../includes/winsdklong-md.md)] .  
  
 사용자 지정 디버그 엔진을 사용 하 여 SP를 사용 하는 경우 디버그 엔진의 필요에 따라 적합 한 것 처럼 SP를 구현할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [디버거 구성 요소](../../extensibility/debugger/debugger-components.md)
