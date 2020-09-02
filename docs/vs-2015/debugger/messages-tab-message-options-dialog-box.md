---
title: 메시지 옵션 대화 상자, 메시지 탭 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- message options, Messages
ms.assetid: fb9fa211-e82c-40a5-9e4b-ba8de07313c0
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: a9eb1c88d935fa307e8b86a9a75da423bc08111c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149440"
---
# <a name="messages-tab-message-options-dialog-box"></a>메시지 옵션 대화 상자, 메시지 탭
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**메시지** 탭을 사용하여 [메시지 뷰](../debugger/messages-view.md)에 나열할 메시지 유형을 선택하고 메시지 검색 조건을 지정할 수 있습니다. [메시지 옵션 대화 상자](../debugger/message-options-dialog-box.md)를 표시하려면 **Spy** 메뉴에서 **로그 메시지**를 선택합니다.  
  
 일반적으로 **메시지 그룹**을 먼저 선택한 다음, 개별 **표시할 메시지**를 선택하여 선택 항목을 미세 조정합니다. **모두** 단추는 모든 메시지 유형을 선택하고, **없음** 단추는 모든 유형을 지웁니다.  
  
 **메시지** 탭에서 사용할 수 있는 설정은 다음과 같습니다.  
  
 **표시할 메시지**  
 보려는 특정 메시지를 선택 합니다. 새 메시지 창을 만들면 이 창에서 모든 메시지를 표시할 수 있습니다. **메시지** 탭에서 메시지를 필터링할 때 해당 필터는 창 뷰에 이미 표시된 메시지가 아닌 새 메시지에만 적용됩니다.  
  
 **메시지 그룹**  
 보려는 메시지 그룹을 선택 합니다. 사용 가능한 그룹은 다음과 같습니다.  
  
- WM_USER: WM_USER보다 크거나 같은 코드를 사용합니다.  
  
- 등록됨: **RegisterWindowMessage** 호출에 등록되었습니다.  
  
- Unknown: 0에서 (WM_USER – 1 사이의 범위에 있는 알 수 없는 메시지  
  
  이러한 **메시지 그룹**은 **표시할 메시지** 아래의 특정 항목에 매핑되지 않습니다. 한 그룹을 선택하면 선택 항목이 해당 메시지 스트림에 직접 적용됩니다.  
  
  **메시지 그룹** 내에서 회색으로 표시된 확인란은 해당 그룹의 메시지에 대해 **표시할 메시지** 목록 상자가 수정되었음을 나타냅니다. 해당 그룹에 있는 메시지 유형 중 일부가 선택되지 않았습니다.  
  
  **설정을 기본값으로 저장**  
  나중에 메시지 검색 옵션으로 사용할 현재 설정을 저장 합니다. 이러한 설정은 Spy++를 종료할 때에도 저장됩니다.
