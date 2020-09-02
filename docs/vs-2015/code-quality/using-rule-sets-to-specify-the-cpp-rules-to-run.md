---
title: 규칙 집합을 사용 하 여 실행할 c + + 규칙 지정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: ff105af1d817613b324e1158130457eb906c753f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77277858"
---
# <a name="using-rule-sets-to-specify-the-c-rules-to-run"></a>규칙 집합을 사용하여 실행할 C++ 규칙 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsPreShort](../includes/vspreshort-md.md)]및에서는 [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] 코드 분석과 관련 된 특정 프로젝트 요구 사항에 맞게 사용자 지정 *규칙 집합* 을 만들고 수정할 수 있습니다. 사용자 지정 C++ 규칙 집합을 만들기 위해서는 C/C++ 프로젝트를 Visual Studio IDE에서 열어야 합니다. 그런 다음 규칙 집합 편집기에서 표준 규칙 집합을 열고, 특정 규칙을 추가 또는 제거하고, 필요에 따라 코드 분석으로 규칙이 위반된 것으로 확인될 때 발생하는 작업을 변경합니다.  
  
 새 사용자 지정 규칙 집합을 만들려면 새 파일 이름을 사용 하 여 저장 합니다. 사용자 지정 규칙 집합이 프로젝트에 자동으로 할당 됩니다.  
  
## <a name="opening-the-rule-set-editor"></a>규칙 집합 편집기 열기  
  
#### <a name="to-create-a-custom-rule-from-a-single-existing-rule-set"></a>기존 규칙 집합 하나에서 사용자 지정 규칙을 만들려면  
  
1. 솔루션 탐색기에서 프로젝트에 대 한 바로 가기 메뉴를 열고 **속성**을 선택 합니다.  
  
2. **속성** 탭에서 **코드 분석**을 선택 합니다.  
  
3. **규칙 집합** 드롭다운 목록에서 다음 중 하나를 수행 합니다.  
  
   - 사용자 지정하려는 규칙 집합을 선택합니다.  
  
     \- 또는 -  
  
   - **\<Browse...>** 목록에 없는 기존 규칙 집합을 지정 하려면 선택 합니다.  
  
4. **열기** 를 선택 하 여 규칙 집합 편집기에서 규칙을 표시 합니다.  
  
#### <a name="to-modify-a-rule-set-in-the-rule-set-editor"></a>규칙 집합 편집기에서 규칙 집합을 수정 하려면  
  
- 규칙 집합의 표시 이름을 변경 하려면 **보기** 메뉴에서 **속성 창**을 선택 합니다. **이름** 상자에 표시 이름을 입력 합니다. 표시 이름은 파일 이름과 다를 수 있습니다.  
  
- 그룹의 모든 규칙을 사용자 지정 규칙 집합에 추가 하려면 그룹의 확인란을 선택 합니다. 그룹의 모든 규칙을 제거 하려면 확인란의 선택을 취소 합니다.  
  
- 사용자 지정 규칙 집합에 특정 규칙을 추가 하려면 규칙의 확인란을 선택 합니다. 규칙 집합에서 규칙을 제거 하려면 확인란의 선택을 취소 합니다.  
  
- 코드 분석에서 규칙을 위반할 때 수행 되는 동작을 변경 하려면 규칙에 대 한 **작업** 필드를 선택 하 고 다음 값 중 하나를 선택 합니다.  
  
     **Warn** -경고를 생성 합니다.  
  
     **오류** -오류를 생성 합니다.  
  
     **없음** -규칙을 사용 하지 않도록 설정 합니다. 이 동작은 규칙 집합에서 규칙을 제거 하는 것과 같습니다.  
  
#### <a name="to-group-filter-or-change-the-fields-in-the-rule-set-editor-by-using-the-rule-set-editor-toolbar"></a>규칙 집합 편집기 도구 모음을 사용 하 여 규칙 집합 편집기에서 필드를 그룹화, 필터링 또는 변경 하려면  
  
- 모든 그룹의 규칙을 확장 하려면 **모두 확장**을 선택 합니다.  
  
- 모든 그룹의 규칙을 축소 하려면 **모두 축소**를 선택 합니다.  
  
- 규칙을 그룹화 하는 필드를 변경 하려면 **그룹화** 방법 목록에서 필드를 선택 합니다. 규칙을 그룹화 하지 않고 표시 하려면를 선택 **\<None>** 합니다.  
  
- 규칙 열에서 필드를 추가 하거나 제거 하려면 **열 옵션**을 선택 합니다.  
  
- 현재 솔루션에 적용 되지 않는 규칙을 숨기려면 **현재 솔루션에 적용 되지 않는 규칙 숨기기**를 선택 합니다.  
  
- 오류 동작에 할당 된 규칙 표시 및 숨기기를 전환 하려면 **코드 분석 오류를 생성할 수 있는 규칙 표시**를 선택 합니다.  
  
- 경고 작업에 할당 된 규칙 표시/숨기기를 전환 하려면 **코드 분석 경고를 생성할 수 있는 규칙 표시**를 선택 합니다.  
  
- **없음** 작업에 할당 된 규칙 표시/숨기기를 전환 하려면 **사용 하도록 설정 되지 않은 규칙 표시**를 선택 합니다.  
  
- 현재 규칙 집합에 Microsoft 기본 규칙 집합을 추가 하거나 제거 하려면 **자식 규칙 집합 추가 또는 제거**를 선택 합니다.
