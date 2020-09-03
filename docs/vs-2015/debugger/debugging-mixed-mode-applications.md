---
title: 혼합 모드 애플리케이션 디버깅 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging, property evaluation
- Call Stack window
- mixed-mode debugging
- Call Stack window, mixed-mode debugging
- debugging managed code, mixed code
- mixed-mode debugging, call stack
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: b462d5d0c449b8e47c936242908e5bbe6e433429
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74298313"
---
# <a name="debugging-mixed-mode-applications"></a>혼합 모드 애플리케이션 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

혼합 모드 애플리케이션은 네이티브 코드(C++)와 관리 코드(Visual Basic, Visual C# 또는 C++처럼 공용 언어 런타임에서 실행되는 코드)가 결합된 애플리케이션입니다. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서는 혼합 모드 애플리케이션의 디버깅이 대부분 투명하게 이루어지며 단일 모드 애플리케이션을 디버깅할 때와 크게 다르지 않습니다. 그러나 특별히 몇 가지 사항을 고려해야 합니다.  
  
## <a name="enable-c-edit-and-continue-in-mixed-mode-debugging"></a>혼합 모드 디버깅에서 C++ 편집하며 계속하기 사용  
  
- Visual Studio 2013에서 C++에 대한 편집하며 계속하기를 사용하려면 레거시 디버깅 엔진으로 되돌려야 합니다. Microsoft Application Lifecycle Management 블로그에서 [Visual Studio 2013에서 관리되는 호환성 모드로 전환](https://devblogs.microsoft.com/devops/switching-to-managed-compatibility-mode-in-visual-studio-2013/)을 참조하세요.  
  
## <a name="property-evaluation-in-mixed-mode-applications"></a>혼합 모드 애플리케이션의 속성 확인  
 혼합 모드 애플리케이션에서 디버거의 속성 확인 작업은 많은 리소스를 차지합니다. 그러므로 단계별 실행과 같은 디버깅 작업이 느리게 나타날 수 있습니다. 자세한 내용은 [단계별 실행](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)을 참조하세요. 혼합 모드 디버깅의 성능이 좋지 않을 경우에는 디버거 창에서 속성 확인을 해제할 수 있습니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
#### <a name="to-turn-off-property-evaluation"></a>속성 확인을 해제하려면  
  
1. **도구** 메뉴에서 **옵션**을 선택합니다.  
  
2. **옵션** 대화 상자에서 **디버깅** 폴더를 열고 **일반** 범주를 선택합니다.  
  
3. **속성 확인 및 기타 암시적 함수 호출 사용** 확인란의 선택을 해제합니다.  
  
   네이티브 호출 스택과 관리되는 호출 스택이 서로 다르기 때문에 디버거는 혼합 코드에 대한 완전한 호출 스택을 항상 제공할 수는 없습니다. 네이티브 코드가 관리 코드를 호출할 경우 약간 다를 수 있습니다. 자세한 내용은 [호출 스택 창의 혼합 코드 및 누락된 정보](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [관리 코드 디버그](../debugger/debugging-managed-code.md)
