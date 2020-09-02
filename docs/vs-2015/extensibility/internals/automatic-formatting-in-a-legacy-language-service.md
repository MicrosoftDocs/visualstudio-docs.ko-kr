---
title: 레거시 언어 서비스의 자동 서식 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e6183fc47138ebb5108e4fbbd2bfa407e5804a72
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157264"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>레거시 언어 서비스의 자동 서식
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

자동 서식 지정을 사용 하면 사용자가 알려진 코드 구문을 입력 하기 시작할 때 언어 서비스에서 코드 조각을 자동으로 삽입 합니다.  
  
## <a name="automatic-formatting-behavior"></a>자동 서식 지정 동작  
 예를 들어를 입력 하면 `if` 언어 서비스에서 일치 하는 중괄호를 자동으로 삽입 하거나 enter 키를 누르면 이전 줄이 새 범위를 열리는지 여부에 따라 언어 서비스에서 새 줄의 삽입 지점을 적절 한 들여쓰기 수준으로 강제 합니다.  
  
 언어 서비스의 나머지 부분에 사용 되는 명령 필터는 자동 서식 지정에도 사용할 수 있습니다. 을 호출 하 여 짝이 되는 중괄호를 강조 표시할 수도 있습니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A> .  
  
## <a name="see-also"></a>관련 항목  
 [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
