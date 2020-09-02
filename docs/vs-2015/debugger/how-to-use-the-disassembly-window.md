---
title: '방법: 디스어셈블리 창 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.disassembly
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
- assembly language, debugging inline assembly code
- breakpoints, Disassembly window
- Disassembly window
- machine code
ms.assetid: eaf84dd0-c82d-481b-af51-690b74e7794c
caps.latest.revision: 34
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c25c3cdeb96abacb4123b2d0a851ac3d4acb0cd5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65696140"
---
# <a name="how-to-use-the-disassembly-window"></a>방법: 디스어셈블리 창 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 기능은 **옵션** 대화 상자의 **디버깅** 노드에서 주소 수준 디버깅을 사용 하도록 설정한 경우에만 사용할 수 있습니다. 스크립트 또는 SQL 디버깅에는 사용할 수 없습니다.  
  
 **디스어셈블리** 창에는 컴파일러에서 만든 명령에 따라 어셈블리 코드가 표시됩니다. 관리 코드를 디버깅하는 경우 이러한 어셈블리 명령은 Visual Studio 컴파일러에서 생성한 MSIL(Microsoft Intermediate Language)이 아닌 JIT(Just-in-Time) 컴파일러에서 만든 네이티브 코드에 대응합니다.  
  
 **디스어셈블리** 창에는 어셈블리 지침뿐 아니라 다음과 같은 선택적 정보도 표시할 수 있습니다.  
  
- 각 명령이 있는 메모리 주소, 네이티브 애플리케이션의 경우 실제 메모리 주소, Visual Basic, C# 또는 관리 코드의 경우 함수 시작 부분으로부터의 오프셋  
  
- 어셈블리 코드가 파생된 소스 코드  
  
- 코드 바이트(실제 컴퓨터 또는 MSIL 명령의 바이트 표시)  
  
- 메모리 주소의 기호 이름  
  
- 소스 코드에 해당하는 줄 번호  
  
  어셈블리 언어 명령은 명령 이름의 약어인 니모닉과 변수, 레지스터 및 상수를 나타내는 기호로 이루어집니다. 각 컴퓨터 언어 명령은 하나의 어셈블리 언어 니모닉으로 표시되며 그 뒤에는 보통 하나 이상의 변수, 레지스터 또는 상수가 옵니다.  
  
  어셈블리 언어를 읽을 수 없을 때 디스어셈블리 창을 최대한 활용하려면 어셈블리 언어 프로그래밍 관련 서적을 참조하십시오. 어셈블리 언어 프로그래밍은 디스어셈블리 창에 대한 이 간략한 소개의 범위를 벗어납니다.  
  
  어셈블리 코드는 프로세서 레지스터(관리 코드의 경우에는 공용 언어 런타임 레지스터)를 많이 사용하기 때문에 레지스터의 내용을 검사할 수 있는 레지스터 창과 함께 디스어셈블리 창을 사용하는 것이 좋습니다.  
  
  아마 컴퓨터 코드 명령을 어셈블리 언어가 아닌 원시 숫자 형식으로 보려는 사람은 없을 것입니다. 그러나 그렇게 하려면 용도에 따라 메모리 창을 사용하거나 디스어셈블리 창의 바로 가기 메뉴에서 코드 바이트를 선택할 수 있습니다.  
  
> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 활성 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기** 를 선택합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.  
  
### <a name="to-display-the-disassembly-window"></a>디스어셈블리 창을 표시하려면  
  
- **디버그** 메뉴에서 **창**을 선택 하 고 **디스어셈블리**를 클릭 합니다.  
  
     디버거는 실행 중이거나 중단 모드에 있어야 합니다.  
  
### <a name="to-turn-optional-information-on-or-off"></a>선택적 정보 표시 여부를 선택하려면  
  
- **디스어셈블리** 창을 마우스 오른쪽 단추로 클릭 하 고 바로 가기 메뉴에서 원하는 옵션을 설정 하거나 선택 취소 합니다.  
  
     왼쪽 여백의 노란색 화살표는 현재 실행 위치를 나타냅니다. 네이티브 코드에서는 이 화살표가 CPU의 프로그램 카운터에 해당합니다. 이 위치는 프로그램에서 다음에 실행될 명령을 나타냅니다.  
  
     자세한 내용은 [메모리에서 페이지 위나 아래로 이동](../debugger/how-to-page-up-or-down-in-memory.md)을 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [디버거에서 데이터 보기](../debugger/viewing-data-in-the-debugger.md)   
 [방법: 레지스터 창 사용](../debugger/how-to-use-the-registers-window.md)
