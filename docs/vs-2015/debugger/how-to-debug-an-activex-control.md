---
title: '방법: ActiveX 컨트롤 디버그 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vc.controls.debug
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- testing [Visual Studio], test containers
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- data-bound controls, ActiveX
- test container
- containers, specifying for debug sessions
- ActiveX controls, debugging
- testing [Visual Studio], ActiveX controls
ms.assetid: bbc02cf7-a7e6-44fe-99af-87a43e1d7251
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9524ab08ab955609f29f437e8a1576af02738aa1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704459"
---
# <a name="how-to-debug-an-activex-control"></a>방법: ActiveX 컨트롤 디버그
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

참고]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 도구 메뉴에서 설정 가져오기 및 내보내기를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
 ActiveX 컨트롤을 디버깅하려면 컨트롤을 실행할 컨테이너(실행 파일)를 지정해야 합니다.  
  
### <a name="to-specify-a-container-for-the-debug-session"></a>디버그 세션에 사용할 컨테이너를 지정하려면  
  
1. 솔루션 탐색기에서 프로젝트를 선택합니다.  
  
2. **보기** 메뉴에서 **속성 페이지**를 선택합니다.  
  
3. **프로젝트 속성 페이지** 대화 상자에서 **구성 속성** 폴더를 열고 **디버깅**을 선택합니다.  
  
4. **디버깅** 범주에서 **명령** 속성을 찾습니다.  
  
5. 컨테이너의 경로 이름을 지정하십시오. 예를 들어, C:\Program Files\Internet Explorer\IEXPLORE.EXE와 같이 입력하십시오.  
  
6. Internet Explorer를 컨테이너로 지정하고 Active Desktop을 사용하는 경우에는 **명령 인수** 상자에 `/new`를 입력합니다.  
  
7. **확인**을 클릭합니다.  
  
     **프로젝트 속성 페이지** 대화 상자에서 컨테이너를 지정하지 않은 경우에는 디버깅을 시작할 때 컨테이너를 지정할 수 있습니다. 디버깅을 시작하는 실행 명령을 선택하면 [디버깅 세션에 사용할 실행 파일 대화 상자](../debugger/executable-for-debugging-session-dialog-box.md)가 나타납니다. 대화 상자에서 컨테이너의 경로 이름을 지정합니다.  
  
## <a name="see-also"></a>관련 항목  
 [ActiveX 컨트롤](https://msdn.microsoft.com/library/52aaec4d-3889-402e-b57d-758078f8ac57)   
 [테스트 컨테이너로 속성 및 이벤트 테스트](https://msdn.microsoft.com/library/626867cf-fe53-4c30-8973-55bb93ef3917)   
 [COM 및 ActiveX 디버깅](../debugger/com-and-activex-debugging.md)   
 [Visual Studio의 디버깅](../debugger/debugging-in-visual-studio.md)
