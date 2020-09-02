---
title: 'PTVS 시작: 코드 편집 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: b412c87c-2f09-4e25-9cc8-ab54f4c44412
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 2e883970b4b265b1864d53ef6e1f347160e5aeb9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62550914"
---
# <a name="getting-started-with-ptvs-editing-code"></a>PTVS 시작: 코드 편집
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

PTVS는 Python에 대한 생산적인 Visual Studio 편집기 환경을 제공합니다.  
  
 짧은 [youtube 동영상](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)을 통해 이러한 지침을 확인할 수 있습니다.  
  
 비어 있는 기본 Python 애플리케이션 프로젝트 템플릿으로 시작합니다.  
  
 편집기에서 `from … import` 줄 입력을 시작합니다.  팝업 완성 목록에 가져올 수 있는 모듈의 전체 목록이 표시됩니다.  이 목록은 Python 버전 및 설치한 라이브러리에 따라 달라집니다.  한 예로 수식 라이브러리를 사용합니다.  입력 시 완성 목록이 입력된 문자를 포함하는 항목으로 필터링됩니다.  `sin` 식별자를 가져와서 문을 완성합니다.  
  
```python  
from math import sin  
  
```  
  
 코딩하는 동안 바인딩되지 않았지만 라이브러리에 있는 식별자를 사용할 경우 PTVS에서 필요한 적절한 import 문을 추가하는 팝업 빠른 수정을 제공합니다.  예를 들어 `cos`를 입력하면 **수학에서 가져오기**가 제공됨을 볼 수 있습니다.  
  
 코드 조각을 사용하여 코드를 생성할 수 있습니다.  편집 메뉴에서 IntelliSense, 코드 조각 삽입을 차례로 선택합니다.  이제 Python을 선택 하 고 def를 선택 합니다.  함수를 호출 `make_dot_string` 하 고 매개 변수 하나를 추가 `x` 합니다.  이제 테스트 기반 개발을 위해 파일에 어설션을 추가할 수 있으며, PTVS에서 이미 완성 목록에 새 함수를 제공할 수 있습니다.  
  
```python  
assert make_dot_string(90) == '          o'  
assert make_dot_string(180) == 'o'  
  
```  
  
 이제 새 함수로 돌아가서 다음 본문을 작성하기 시작합니다.  
  
```python  
return " " * int(10 * cos(radians(x)) + 10) + "o"  
  
```  
  
 PTVS는 이 함수에 대한 호출 사이트를 분석했기 때문에 매개 변수를 정수로 가정합니다.   또한 빠른 수정을 사용하여 `radians`를 가져와야 합니다.  
  
 다른 코드 조각에서 최상위 수준에 `main`을 입력하고 스마트 태그 UI를 호출한 다음 탭을 통해 "def main..."을 선택하여 main 블록을 만듭니다.  `make_dot_string`을 호출하는 기본 루프를 작성합니다.  마침표를 누르고 제공된 완성을 살펴보면 PTVS에서 함수가 문자열을 반환하는 것을 알고 있음을 확인할 수 있습니다.  이 형식 정보는 전체 프로그램에 전달되므로 값이 종료되는 위치마다 코드 이해와 작성에 도움이 되는 도구 설명 및 완성을 제공할 수 있습니다.  
  
 인쇄 호출을 추가하면 다음과 유사한 main이 작성됩니다.  
  
```python  
def main ():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
```  
  
 F5 키를 누르면 코드가 cmd.exe 창에서 실행되며, 점이 앞뒤로 움직입니다.  
  
 짧은 [youtube 동영상](https://www.youtube.com/watch?v=uZGZNEyyeKs&index=3&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)을 통해 이러한 지침을 확인할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Wiki 설명서](https://github.com/Microsoft/PTVS/wiki/Editor-Features)   
 [PTVS Getting Started and Deep Dive Videos](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)(PTVS 시작 및 자세히 알아보기 동영상)
