---
title: '방법: 시각화 도우미 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
f1_keywords:
- vs.debug.dataviewer
- vs.debug.stringviewer
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, visualizers
- visualizers, about visualizers
ms.assetid: d2611385-0134-4387-8c5a-979fe625a462
caps.latest.revision: 37
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 0f981b76d471658fe82e874901ad784a17841891
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778369"
---
# <a name="how-to-use-a-visualizer"></a>방법: 시각화 도우미 사용
시각화 도우미를 사용하여 변수 또는 개체의 내용을 데이터 형식에 대해 의미 있는 방식으로 표시할 수 있습니다. **DataTips**, **조사식** 창, **자동** 창 또는 **지역** 창에서 시각화 도우미를 사용할 수 있습니다.  
  
 Compact Framework에서는 시각화 도우미가 지원되지 않습니다.  
  
> [!NOTE]
> **스토어** 앱에서는 표준 텍스트, HTML, XML 및 JSON 시각화 도우미만 지원 됩니다. 사용자가 만든 사용자 지정 시각화 도우미는 지원되지 않습니다.  
  
### <a name="to-open-a-visualizer"></a>시각화 도우미를 열려면  
  
1. **DataTips**, **조사식** 창 또는 **자동**, **지역**또는 **간략 한 조사식** 창에서 변수 이름 옆에 표시 되는 돋보기 아이콘을 클릭 합니다.  
  
     시각화 도우미의 목록이 나타납니다.  
  
2. 사용할 시각화 도우미를 클릭합니다.  
  
### <a name="to-use-a-visualizer-for-managed-code-during-remote-debugging"></a>원격 디버깅하는 동안 관리 코드에 시각화 도우미를 사용하려면  
  
- 디버깅 세션을 시작하기 전에 시각화 도우미 DLL을 원격 컴퓨터에 복사합니다.  
  
     DLL에 대한 경로는 원격 컴퓨터와 로컬 컴퓨터에서 같아야 합니다. 이 경로는 다음 위치 중 하나일 수 있습니다.  
  
     *Visual Studio 설치 경로* `\Common7\Packages\Debugger\Visualizers`  
  
     또는  
  
     `My Documents\Visual Studio 2010\Visualizers`*Visual Studio 버전*`\Visualizers`  
  
## <a name="see-also"></a>관련 항목  
 [사용자 지정 시각화 도우미 만들기](../debugger/create-custom-visualizers-of-data.md)   
 [방법: 시각화 도우미 설치](../debugger/how-to-install-a-visualizer.md)   
 [방법: 시각화 도우미 작성](../debugger/how-to-write-a-visualizer.md)   
 [데이터 팁에서 데이터 값 보기](../debugger/view-data-values-in-data-tips-in-the-code-editor.md)