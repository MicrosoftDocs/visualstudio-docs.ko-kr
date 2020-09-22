---
title: '방법: 편집하며 계속하기 사용(C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Edit and Continue [C#], about Edit and Continue
ms.assetid: 40e136d8-a08c-43bd-b313-fb821c55eb3c
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 39137d5fe60a3c91c8fd3904e797eb83420a8f5d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841803"
---
# <a name="how-to-use-edit-and-continue-c"></a>방법: 편집하며 계속하기 사용(C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

C#에서 편집하며 계속하기를 사용하면 디버깅하는 동안 중단 모드에서 코드를 변경할 수 있습니다. 디버깅 세션을 중지하고 다시 시작하지 않고도 변경 내용을 적용할 수 있습니다.  
  
 편집 하며 계속 하기는 중단 모드에서 변경 하는 경우 자동으로 호출 되 고, **continue**, **Step**또는 **Set Next 문**같은 디버거 실행 명령을 선택 하거나, 디버거 창에서 함수를 평가 합니다.  
  
> [!NOTE]
> Compact Framework, 최적화된 코드, 혼합된 네이티브/관리 코드 또는 SQL Server CLR(공용 언어 런타임) 통합 코드를 디버깅할 때는 편집하며 계속하기가 지원되지 않습니다. 이러한 시나리오 중 하나에서 코드 변경 내용을 적용 하려고 하면 디버거는 편집 하며 계속 하기가 지원 되지 않는다는 것을 설명 하는 대화 상자를 표시 합니다.  
  
### <a name="to-invoke-edit-and-continue-automatically"></a>편집 하며 계속 하기를 자동으로 호출 하려면  
  
1. 중단 모드에서 소스 코드를 변경 합니다.  
  
2. **디버그** 메뉴에서 **계속**, **단계**또는 **다음 문 설정** 또는 디버거 창에서 함수 평가를 클릭 합니다.  
  
     새 코드는 컴파일되고 새 코드를 사용 하 여 디버깅을 계속 합니다. 일부 변경 내용은 편집 하며 계속 하기에서 지원 되지 않습니다. 자세한 내용은 [지원 되는 코드 변경 내용 (c #)](../debugger/supported-code-changes-csharp.md)을 참조 하세요.  
  
### <a name="to-enabledisable-edit-and-continue"></a>편집하며 계속하기를 사용하거나 사용하지 않도록 설정하려면  
  
1. **도구** 메뉴에서 **옵션**을 클릭합니다.  
  
2. **옵션** 대화 상자에서 **디버깅** 노드를 확장 하 고 **편집 하며 계속 하기**를 선택 합니다.  
  
3. **옵션** 대화 상자 **편집 하며 계속 하기** 페이지에서 **편집 하며 계속 하기 사용** 확인란을 선택 하거나 선택 취소 합니다.  
  
     이 설정은 디버깅 세션을 다시 시작할 때 적용 됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [편집 하며 계속 하기 (Visual c #)](../debugger/edit-and-continue-visual-csharp.md)   
 [지원 되는 코드 변경 내용 (c #)](../debugger/supported-code-changes-csharp.md)   
 [편집 하며 계속 하기의 오류 및 경고 (c #)](../misc/edit-and-continue-errors-and-warnings-csharp.md)
