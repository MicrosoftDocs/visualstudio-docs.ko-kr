---
title: 'PTVS 시작: 대화형 Python | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: fa594314-bdd0-4da5-874a-57b03414b675
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 4fba8bf658a50a7a7e28abace1eb622ab14f5f26
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550989"
---
# <a name="getting-started-with-ptvs-interactive-python"></a>PTVS 시작: 대화형 Python
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

대화형 프롬프트 또는 REPL(읽기-평가-인쇄 루프)은 생산적인 프로그래밍 언어의 핵심 도구입니다.  이러한 도구를 통해 코드 조각을 실행하여 API를 검색 및 학습하고, API 사용 방법을 실험하고, 프로젝트 또는 프로그램에 포함할 작업 코드를 대화형으로 개발할 수 있습니다.  
  
 짧은 [youtube 동영상](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)을 통해 이러한 지침을 확인할 수 있습니다.  
  
 Python 환경 창에는 모든 Python 환경 목록이 표시됩니다.  하나를 선택하여 대화형 창 또는 REPL을 열 수 있습니다.  명령 프롬프트에서 Python.exe를 실행한 적이 있으면 이전에 python REPL을 보았을 것입니다.  REPL이 메시지를 표시하면 코드를 입력하고 Enter 키를 눌러 코드 결과를 즉시 확인할 수 있습니다.  모든 실행의 모든 상태, 변수 할당 등을 포함 하는 라이브 실행 컨텍스트입니다.  나중에 REPL 프롬프트에 제출할 때 결과를 포함 하는 변수를 참조할 수 있습니다.  여러 줄의 코드를 작성하고 동시에 모두 실행할 수 있습니다(예: 메서드 선언 또는 여러 문).  
  
 새 라이브러리를 사용하는 경우 REPL을 통해 라이브러리를 효과적으로 체험할 수 있습니다.  라이브러리를 가져오고 하위 패키지, 클래스 및 함수를 검사할 수 있습니다.  Python은 `help()` 함수를 통해 이 모든 정보를 전달할 수 있습니다.  또한 PTVS(Python Tools for Visual Studio)는 라이브러리를 실행하지 않고도 편집기에서 사용된 코드 모델링에 따라 제안 및 설명서를 제공합니다.  코드를 실행할 때 PTVS는 Python 런타임의 정보를 사용하여 PTVS 제안을 향상시킵니다.  
  
 대화형 창은 코드 개발 중 테스트를 포함하여 반복적이거나 발전적인 코드 개발에도 유용합니다.  편집기 창에서 함수를 선택하고 오른쪽 포인터 단추를 누른 다음 Interactive로 보내기를 선택할 수 있습니다.  이 명령은 선택 내용을 대화형 창에 다음 입력으로 복사하고 실행합니다.  결과가 즉시 표시됩니다.  이전 입력을 변경해야 하는 경우 위쪽 화살표를 눌러 코드를 다시 가져오고 수정한 다음 Ctrl+Enter를 눌러 코드를 실행할 수 있습니다.  입력의 끝에서 Enter 키를 누르면 코드가 실행되지만 입력 중에 Enter 키를 누르면 줄 바꿈이 삽입됩니다.  
  
 각 Python 설치에 대해 대화형 창을 원하는 개수만큼 열 수 있습니다.  창 위쪽에는 디스플레이를 지우고 실행 컨텍스트를 다시 설정 하는 등의 단추가 있습니다.  기록은 그대로 유지 됩니다.  
  
 짧은 [youtube 동영상](https://www.youtube.com/watch?v=yc2CROtTsC0&index=5&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)을 통해 이러한 지침을 확인할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Wiki 설명서](https://github.com/Microsoft/PTVS/wiki/Interactive-REPL)   
 [PTVS Getting Started and Deep Dive Videos](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)(PTVS 시작 및 자세히 알아보기 동영상)
