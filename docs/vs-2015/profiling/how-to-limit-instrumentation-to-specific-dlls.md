---
title: '방법: 계측을 특정 DLL로 제한 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- performance tools, runtime profiling control window
ms.assetid: 17c5996f-e3d0-4e44-b175-52b401b0f2d5
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5dc2fe8e6f9b0ed1e6970943ab5eedf1b62eb961
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841814"
---
# <a name="how-to-limit-instrumentation-to-specific-dlls"></a>방법: 계측을 특정 DLL로 제한
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

계측 프로파일링 방법을 사용하여 프로파일링 데이터 수집을 애플리케이션의 DLL 하나 이상으로 제한할 수 있습니다. 애플리케이션에서 하나 이상의 DLL을 프로파일링하려면 .dll 파일이 대상으로 포함된 성능 세션을 만듭니다. 프로파일링할 DLL을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션의 프로젝트로 또는 독립 이진 파일로 지정할 수 있습니다.  
  
### <a name="to-limit-instrumentation-to-specific-dlls-in-a-visual-studio-solution"></a>Visual Studio 솔루션에서 계측을 특정 DLL로 제한하려면  
  
1. [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]에서 DLL이 포함된 솔루션을 엽니다.  
  
2. **분석** 메뉴에서 **성능 마법사 시작**을 선택합니다.  
  
3. **계측**을 프로파일링 방법으로 선택하고 **다음**을 클릭합니다.  
  
4. **다음 사용 가능한 대상 중에서 프로 파일링 할 대상을**선택 하십시오 .에서 .dll 프로젝트의 이름을 선택 하 고 **다음**을 클릭 합니다.  
  
5. **마침**을 클릭하여 마법사를 종료하고 **성능 탐색기** 창에 새 성능 세션을 표시합니다.  
  
6. **대상**을 마우스 오른쪽 단추로 클릭하고 **대상 프로젝트 추가**를 선택합니다.  
  
7. **대상 프로젝트 추가** 목록에서 DLL을 실행하는 데 사용할 실행 가능한 프로젝트를 선택합니다.  
  
     선택 사항입니다. 프로파일링하려는 모든 DLL 프로젝트를 추가할 수 있습니다.  
  
8. 추가된 프로젝트에 대한 데이터 수집을 차단하려면 프로젝트 이름을 마우스 오른쪽 단추로 클릭하고 **계측** 확인란의 선택을 취소합니다.  
  
### <a name="to-specify-specific-dlls-to-profile-as-independent-binaries"></a>특정 DLL을 독립 이진 파일로 프로파일링하도록 지정하려면  
  
1. [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)]를 엽니다.  
  
2. **분석** 메뉴에서 **성능 마법사 시작**을 선택합니다.  
  
3. **다음 사용 가능한 대상 중 프로파일링할 대상을 선택하세요.** 에서 **동적 연결 라이브러리 프로파일링(.DLL)** 을 선택하고 **다음**을 클릭합니다.  
  
4. 마법사의 두 번째 페이지에서 다음 단계를 수행합니다.  
  
    - **Dll 경로**에서 프로 파일링 할 .dll 파일의 경로 및 파일 이름을 입력 합니다. 줄임표 단추(...)를 클릭하여 **프로파일링할 동적 연결 라이브러리** 대화 상자에서 파일을 찾을 수도 있습니다. 다음에 선택할 실행 파일(.exe)을 통해 시작할 .dll 파일의 복사본을 지정해야 합니다.  
  
    - **실행 파일 경로**에서 .dll을 실행 하는 실행 파일 (.exe)의 경로와 파일 이름을 입력 합니다. 줄임표 단추(...)를 클릭하여 **시작할 실행 파일** 대화 상자에서 파일을 찾을 수도 있습니다.  
  
    - 선택 사항입니다. **명령줄 인수**로 실행 파일에 전달할 명령줄 인수를 입력합니다. 필요한 경우 **작업 디렉터리**에서 애플리케이션의 작업 디렉터리를 지정합니다.  
  
    - **다음**을 클릭합니다.  
  
5. **계측**을 프로파일링 방법으로 선택하고 **다음**을 클릭합니다.  
  
6. **마침**을 클릭하여 마법사를 종료하고 **성능 탐색기** 창에 새 성능 세션을 표시합니다.  
  
7. 선택 사항입니다. .Dll 파일을 더 추가 하려면 **대상** 을 마우스 오른쪽 단추로 클릭 하 고 **대상 이진 파일 추가**를 선택 합니다. **대상 이진 파일 추가** 대화 상자에서 파일을 선택합니다.  
  
    > [!NOTE]
    > DLL을 실행하는 실행 파일(.exe)을 지정하지 마세요.  
  
## <a name="see-also"></a>참고 항목  
 [데이터 수집 제어](../profiling/controlling-data-collection.md)   
 [방법: 특정 함수로 계측 제한](../profiling/how-to-limit-instrumentation-to-specific-functions.md)
