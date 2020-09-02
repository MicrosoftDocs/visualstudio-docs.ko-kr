---
title: '방법: 혼합 모드에서 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5e2dd4ea0000eefdbd9f74c8fa97c4c63e06fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681139"
---
# <a name="how-to-debug-in-mixed-mode"></a>How to: Debug in Mixed Mode
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 절차에서는 관리 코드와 네이티브 코드를 모두 디버깅하는 방법에 대해 설명합니다. 이러한 디버깅을 혼합 모드 디버깅이라고도 합니다. 네이티브 코드로 작성된 것이 DLL인지 애플리케이션인지 여부에 따라 혼합 모드 디버깅에는 두 가지 시나리오가 있습니다.  
  
- DLL을 호출하는 호출 애플리케이션이 네이티브 코드로 작성된 경우 DLL이 관리 코드로 작성된 것입니다. 이 경우 관리되는 디버거와 네이티브 디버거가 둘 모두를 디버깅할 수 있어야 합니다. ** \<Project> 속성 페이지** 대화 상자에서이를 확인할 수 있습니다. 이를 수행하는 방법은 DLL 프로젝트에서 디버깅을 시작하는지 아니면 호출 애플리케이션 프로젝트에서 디버깅을 시작하는지에 따라 달라집니다.  
  
- DLL을 호출하는 애플리케이션이 관리 코드로 작성된 경우 DLL이 네이티브 코드로 작성된 것입니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
### <a name="to-enable-mixed-mode-debugging"></a>혼합 모드 디버깅을 사용하도록 설정하려면  
  
1. **솔루션 탐색기**에서 프로젝트를 선택 합니다.  
  
2. **보기** 메뉴에서 **속성 페이지**를 클릭합니다.  
  
3. ** \<Project> 속성 페이지** 대화 상자에서 **구성 속성** 노드를 확장 한 다음 **디버깅**을 선택 합니다.  
  
4. **디버거 형식**을 **혼합** 또는 **자동**으로 설정합니다.  
  
## <a name="see-also"></a>관련 항목  
 [방법: DLL 프로젝트에서 디버그](../debugger/how-to-debug-from-a-dll-project.md)
