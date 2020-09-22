---
title: Spy++ 소개 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Spy++
ms.assetid: 733b514b-63a9-402d-89aa-4f0416766655
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 35e9fa2d75528549f8c55f5b52dbd4c4aa2271a6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843365"
---
# <a name="introducing-spy"></a>Spy++ 소개
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Spy++에서는 다음 작업을 수행할 수 있습니다.  
  
- 시스템 개체 간의 관계를 그래픽 트리로 표시합니다. 여기에는 [프로세스](../debugger/processes-view.md), [스레드](../debugger/threads-view.md)및 [창](../debugger/windows-view.md)이 포함됩니다.  
  
- 지정된 [창](../debugger/how-to-search-for-a-window-in-windows-view.md), [스레드](../debugger/how-to-search-for-a-thread-in-threads-view.md), [프로세스](../debugger/how-to-search-for-a-process-in-processes-view.md)또는 [메시지](../debugger/how-to-search-for-a-message-in-messages-view.md)를 검색합니다.  
  
- 선택한 [창](../debugger/how-to-display-window-properties.md), [스레드](../debugger/how-to-display-thread-properties.md), [프로세스](../debugger/how-to-display-process-properties.md)또는 [메시지](../debugger/how-to-display-message-properties.md)의 속성을 봅니다.  
  
- 보기에서 직접 창, 스레드, 프로세스 또는 메시지를 선택합니다.  
  
- [찾기 도구](../debugger/how-to-use-the-finder-tool.md) 로 마우스 포인터를 이동하여 창을 선택합니다.  
  
- 복잡한 메시지 로그 선택 매개 변수를 사용하여 **메시지 옵션** 을 설정합니다.  
  
  Spy++의 도구 모음과 하이퍼링크를 사용하면 더 빨리 작업할 수 있습니다. 또한 Spy++는 활성 보기를 업데이트할 수 있는 **새로 고침** 명령, 검색을 더 용이하게 해 주는 **창 찾기 도구** , 보기 창을 사용자 지정할 수 있는 **글꼴** 대화 상자를 제공합니다. 또한 Spy++에서는 사용자 기본 설정을 저장 및 복원할 수 있습니다.  
  
  다양한 Spy++ 창에서 마우스 오른쪽 단추를 클릭하면 자주 사용되는 명령의 바로 가기 메뉴를 표시할 수 있습니다. 표시되는 명령은 포인터가 있는 위치에 따라 달라집니다. 예를 들어 창 보기에서 항목을 마우스 오른쪽 단추로 클릭하여 선택한 창이 보이는 경우에 바로 가기 메뉴의 **강조** 를 클릭하면 더 쉽게 찾을 수 있도록 선택한 창의 테두리가 깜빡입니다.  
  
> [!NOTE]
> 그 밖에 Spy++와 유사한 두 가지 유틸리티가 있습니다. PView는 프로세스 및 스레드에 관한 상세 정보를 표시하고, DDESPY.EXE는 DDE(동적 데이터 교환) 메시지 모니터링에 사용할 수 있습니다.  
  
## <a name="64-bit-operating-systems"></a>64비트 운영 체제  
 Spy++의 두 가지 버전이 있습니다. Spy++(spyxx.exe)라는 첫 번째 버전은 32비트 프로세스에서 실행되는 창으로 전송된 메시지를 표시하도록 설계되었습니다. 예를 들어 Visual Studio는 32비트 프로세스로 실행됩니다. 따라서 **솔루션 탐색기**로 전송된 메시지를 표시하는 데 Spy++를 사용할 수 있습니다. Visual Studio에서 대부분의 빌드에 대한 기본 구성은 32비트 프로세스로 실행되므로, Spy++의 첫 번째 버전은 Visual Studio의 **도구** 메뉴에서 사용할 수 있습니다.  
  
 Spy++(64비트)(spyxx_amd64.exe)라는 두 번째 버전은 64비트 프로세스에서 실행되는 창으로 전송된 메시지를 표시하도록 설계되었습니다. 예를 들어 64비트 운영 체제에서는 메모장이 64비트 프로세스로 실행됩니다. 따라서 메모장으로 전송된 메시지를 표시하기 위해 Spy++(64 비트)를 사용할 수 있습니다. Spy++(64 비트)는 일반적으로 다음 위치에 있습니다.  
  
 ..\\*Visual Studio 설치 폴더*\Common7\Tools\spyxx_amd64.exe.  
  
 명령줄에서 직접 Spy++의 버전 중 하나를 실행할 수 있습니다.  
  
> [!NOTE]
> Spy++(64비트) 파일 이름은 "amd"를 포함하지만 x64 Windows 운영 체제에서 실행됩니다.  
  
## <a name="see-also"></a>참고 항목  
 [Spy + + 사용](../debugger/using-spy-increment.md)   
 [Spy + + 뷰](../debugger/spy-increment-views.md)   
 [Spy++ 참조](../debugger/spy-increment-reference.md)
