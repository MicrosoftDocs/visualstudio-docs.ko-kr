---
title: '방법: WPF 트리 시각화 도우미 사용 | Microsoft Docs'
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
- WPF, debugging
- debugging, WPF
ms.assetid: 2a1bf1cd-90f9-4d06-9fb4-1bfc925afef3
caps.latest.revision: 21
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 381dc45351ae03e615afbdd31239869e3dba8e4e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "67825430"
---
# <a name="how-to-use-the-wpf-tree-visualizer"></a>방법: WPF 트리 시각화 도우미 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

WPF 트리 시각화 도우미를 사용하여 WPF 개체의 표시 트리를 탐색하고 트리에 포함된 개체의 WPF 종속성 속성을 볼 수 있습니다. 시각적 트리에 관한 자세한 내용은 [WPF의 트리](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)를 참조하세요. 종속성 속성에 관한 자세한 내용은 [종속성 속성 개요](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)를 참조하세요.  
  
 WPF 트리 시각화 도우미를 열면 왼쪽에 **시각적 트리** 창이 표시되고 오른쪽에 ‘이름’ **:** ‘형식’**의 속성** 창이 표시됩니다.  **시각적 트리** 창에서 개체를 선택하면 ‘이름’ **:** 형식’**의 속성** 창이 자동으로 업데이트되어 해당 개체의 속성이 표시됩니다.   
  
### <a name="to-open-the-wpf-tree-visualizer"></a>WPF 트리 시각화 도우미를 열려면  
  
1. DataTip, **조사식** 창, **자동** 창 또는 **로컬** 창에서 WPF 개체 이름 옆에 나타나는 돋보기 모양 아이콘 옆의 화살표를 클릭합니다.  
  
     시각화 도우미의 목록이 나타납니다.  
  
2. **WPF 트리 시각화 도우미**를 클릭합니다.  
  
### <a name="to-search-the-visual-tree"></a>표시 트리를 검색하려면  
  
- **표시 트리** 창의 **검색** 상자에 검색할 문자열을 입력합니다.  
  
  WPF 트리 시각화 도우미가 입력한 문자열과 일치하는 표시 트리의 첫 번째 개체를 즉시 찾습니다. 문자를 추가로 입력하여 좀 더 정확하게 일치하는 항목을 찾을 수 있습니다.  

  - 표시 트리 내에서 다음 일치 항목으로 이동하려면 **다음**을 클릭합니다.  

  - 이전 일치 항목으로 이동하려면 **이전**을 클릭합니다.  

  - 검색 조건을 지우려면 **지우기**를 클릭합니다.  

### <a name="to-search-the-properties-list"></a>속성 목록을 검색하려면  
  
- _이름_**:**_유형_ 창의 **속성** 에서 **필터** 상자에 검색할 문자열을 입력 합니다.  
  
  WPF 트리 시각화 도우미가 입력한 문자열과 일치하는 속성을 즉시 찾습니다. 이제 목록에는 입력한 문자열과 일치하는 속성만 표시됩니다. 문자를 추가로 입력하여 좀 더 정확하게 일치하는 항목을 찾을 수 있습니다.  

  - 검색 조건을 지우려면 **지우기**를 클릭합니다.  
  
### <a name="to-close-the-visualizer"></a>시각화 도우미를 닫으려면  
  
- 대화 상자의 오른쪽 위 모퉁이에서 **닫기** 아이콘을 클릭합니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: 시각화 도우미 사용](../misc/how-to-use-a-visualizer.md)   
 [사용자 지정 시각화 도우미 만들기](../debugger/create-custom-visualizers-of-data.md)   
 [WPF의 트리](https://msdn.microsoft.com/library/e83f25e5-d66b-4fc7-92d2-50130c9a6649)   
 [종속성 속성 개요](https://msdn.microsoft.com/library/d119d00c-3afb-48d6-87a0-c4da4f83dee5)
