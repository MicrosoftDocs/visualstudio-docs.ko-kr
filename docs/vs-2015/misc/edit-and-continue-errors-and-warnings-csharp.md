---
title: '편집 하며 계속 하기의 오류 및 경고 (c #) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.csharp.enc.error_4001
- vs.csharp.enc.error_4034
- vs.csharp.enc.error_4003
- vs.csharp.enc.error_4026
- vs.csharp.enc.error_4032
- vs.csharp.enc.error_4017
- vs.csharp.enc.error_4053
- vs.csharp.enc.error_4024
- vs.csharp.enc.error_4012
- vs.csharp.enc.error_4066
- vs.csharp.enc.error_4020
- vs.csharp.enc.error_4008
- vs.csharp.enc.error_4033
- vs.csharp.enc.error_4014
- vs.csharp.enc.error_4023
- vs.csharp.enc.error_4011
- vs.csharp.enc.error_4006
- vs.csharp.enc.error_4059
- vs.csharp.enc.error_4015
- vs.csharp.enc.error_4018
- vs.csharp.enc.error_4028
- vs.csharp.enc.error_4013
- vs.csharp.enc.error_4009
- vs.csharp.enc.error_4021
- vs.csharp.enc.error_4065
- vs.csharp.enc.error_4029
- vs.csharp.enc.error_4058
- vs.csharp.enc.error_4019
- vs.csharp.enc.error_4007
- vs.csharp.enc.error_4052
- vs.csharp.enc.error_4025
- vs.csharp.enc.error_4055
- vs.csharp.enc.error_4022
- vs.csharp.enc.error_4002
- vs.csharp.enc.error_4016
- vs.csharp.enc.error_4043
- vs.csharp.enc.error_4027
- vs.csharp.enc.error_4054
- vs.csharp.enc.error_4004
- vs.csharp.enc.error_4010
- vs.csharp.enc.error_4030
- vs.csharp.enc.error_4005
- vs.csharp.enc.error_4035
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], errors and warnings
- errors [C#], debugging
- errors [debugger], Edit and Continue
ms.assetid: c0e12b0a-8009-4a4a-979f-c804a91a5d9b
caps.latest.revision: 11
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eec40bc584e831f8b43b79c9bc7cee5a48a291aa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75850968"
---
# <a name="edit-and-continue-errors-and-warnings-c"></a>편집하며 계속하기의 오류 및 경고(C#)
Visual C# 편집하며 계속하기에서 허용되지 않는 코드의 섹션을 편집했습니다.  
  
 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] 편집하며 계속하기를 사용하면 중단 모드에서 프로그램 실행을 중지하고 실행 코드를 변경한 다음 새로 통합된 변경 내용을 사용하여 프로그램 실행을 다시 시작할 수 있습니다.  
  
 클래스의 공용 구조체에 영향을 주는 선언 코드 편집은 일반적으로 금지되며, 클래스 내의 private 선언, 속성 본문 또는 메서드에 대한 일부 편집이 허용되지 않습니다. 편집하며 계속하기에서는 편집할 수 없는 코드를 가능한 경우 항상 연한 회색으로 표시하고 오류 메시지를 표시합니다.  
  
 의 편집 하며 계속 하기에서 지원 되는 편집에 대 한 자세한 내용은 [!INCLUDE[csharp_current_short](../includes/csharp-current-short-md.md)] [지원 되는 코드 변경 내용 (c #)](../debugger/supported-code-changes-csharp.md)을 참조 하세요. 특정 오류 또는 경고에 대한 자세한 정보가 필요한 경우 MSDN [Visual C# IDE 포럼](https://social.msdn.microsoft.com/Forums/en-US/csharpide/threads)에서 검색하거나 질문을 게시할 수 있습니다.  
  
### <a name="to-correct-this-error"></a>이 오류를 해결하려면  
  
1. **디버그** 메뉴에서 **실행 취소** 를 선택하여 변경 내용을 취소합니다.  
  
     또는  
  
2. 디버깅 세션을 중지하고 편집 작업을 수행한 다음 새 디버깅 세션을 시작합니다.  
  
## <a name="see-also"></a>관련 항목  
 [편집하며 계속하기(Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
