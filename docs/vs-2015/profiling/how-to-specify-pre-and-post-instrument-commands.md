---
title: '방법: 계측 전 명령 및 계측 후 명령 지정 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.performance.property.instrument
helpviewer_keywords:
- profiling tools, pre-instrument events
- events [Visual Studio], pre-instrument
- pre-instrument events, performance tools
ms.assetid: 6a8d5340-1d1b-4d81-88dd-8e1f435eb828
caps.latest.revision: 33
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ab7ecbe97ba0b174a1cc4c0f0d169834ce25e8d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841495"
---
# <a name="how-to-specify-pre--and-post-instrument-commands"></a>방법: 계측 전 명령 및 계측 후 명령 지정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

성능 세션의 이진 파일이 계측되기 전이나 계측된 후 실행되는 명령을 지정할 수 있습니다. 명령줄에서 실행될 수 있는 모든 명령을 계측 전 또는 계측 후 이벤트로 지정할 수 있습니다. 예를 들어 이진 파일이 계측된 후 실행되는 배치 파일에서 강력한 이름 키를 사용하여 어셈블리 재서명을 자동화하는 명령을 지정할 수 있습니다.  
  
 프로파일링 실행의 모든 계측된 이진 파일에 대한 명령이나 개별 이진 파일에 대한 명령을 지정합니다. 그러나 계측 프로세스 전에 실행할 계측 전 명령을 하나만 지정하고 계측 프로세스 후에 실행할 계측 후 명령을 하나만 지정할 수 있습니다. 모든 이진 파일 및 개별 이진 파일에 대한 명령을 둘 다 지정할 수는 없습니다. 모든 이진 파일에 대한 명령을 지정하면 세션에서 각 이진 파일의 계측 이전 또는 이후에 명령이 실행됩니다.  
  
 **요구 사항**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
  명령이 실행되는 작업 디렉터리는 [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]를 실행 중인 운영 체제 및 프로파일링된 애플리케이션의 대상 플랫폼에 따라 달라집니다.  
  
  **32비트 컴퓨터**  
  
  32비트 컴퓨터에서 기본 프로파일러 도구가 위치한 디렉터리는 드라이브\Program Files\Microsoft Visual Studio 10.0\Team Tools\Performance Tools입니다.  
  
  **64비트 컴퓨터**  
  
  64비트 컴퓨터에서 프로파일링된 애플리케이션의 대상 플랫폼에 따라 경로를 지정합니다.  
  
- 32비트 애플리케이션의 경우 기본 프로파일러 도구 디렉터리는 다음과 같습니다.  
  
   *드라이브*\ 파일 파일 (x86) \Microsoft Visual Studio 10.0 \ o m s s p o r t s.  
  
- 64비트 애플리케이션의 경우 기본 프로파일러 도구가 위치한 디렉터리는 다음과 같습니다.  
  
   *드라이브*\ 파일 파일 (x86) \Microsoft  
  
### <a name="to-specify-pre-instrument-commands"></a>계측 전 명령을 지정하려면  
  
1. 다음 단계 중 하나를 수행합니다.  
  
    - 성능 세션에서 모든 이진 파일에 대한 계측 전 명령을 지정하려면 **성능 탐색기**에서 성능 세션을 선택하고 나서 마우스 오른쪽 단추를 클릭하고 **속성**을 선택합니다.  
  
    - 특정 이진 파일에 대한 계측 전 명령을 지정하려면 성능 세션의 **대상** 목록에서 이진 파일의 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
2. **속성 페이지**에서 **계측**을 클릭합니다.  
  
3. **계측 전 이벤트** 아래 **명령줄** 텍스트 상자에 명령을 입력합니다.  
  
    > [!NOTE]
    > **명령줄** 상자에 인접 한 줄임표 단추 **(...)** 를 클릭 하 여 해당 하는 .exe, .cmd 또는 .bat 파일을 찾아 선택할 수 있습니다.  
  
4. **확인**을 클릭합니다.  
  
     명령을 제거하지 않고 명령이 실행되지 않게 하려면 **계측에서 제외** 확인란을 선택합니다. 컴파일러 또는 링커 설정을 수정하려면 프로젝트 속성 페이지를 사용합니다.  
  
### <a name="to-specify-post-instrument-commands"></a>계측 후 명령을 지정하려면  
  
1. 다음 단계 중 하나를 수행합니다.  
  
    - 성능 세션에서 모든 이진 파일에 대한 계측 후 명령을 지정하려면 **성능 탐색기**에서 성능 세션을 선택하고 나서 마우스 오른쪽 단추를 클릭하고 **속성**을 선택합니다.  
  
    - 특정 이진 파일에 대한 계측 후 명령을 지정하려면 성능 세션의 **대상** 목록에서 이진 파일의 이름을 마우스 오른쪽 단추로 클릭하고 **속성**을 선택합니다.  
  
2. **속성 페이지**에서 **계측**을 클릭합니다.  
  
3. **계측 후 이벤트** 아래 **명령줄** 텍스트 상자에 명령을 입력합니다.  
  
    > [!NOTE]
    > **명령줄** 상자에 인접 한 줄임표 단추 **(...)** 를 클릭 하 여 해당 하는 .exe, .cmd 또는 .bat 파일을 찾아 선택할 수 있습니다.  
  
4. **확인**을 클릭합니다.  
  
     명령을 제거하지 않고 명령이 실행되지 않게 하려면 **계측에서 제외** 확인란을 선택합니다. 컴파일러 또는 링커 설정을 수정하려면 프로젝트 속성 페이지를 사용합니다.  
  
## <a name="see-also"></a>참고 항목  
 [성능 세션 구성](../profiling/configuring-performance-sessions.md)
