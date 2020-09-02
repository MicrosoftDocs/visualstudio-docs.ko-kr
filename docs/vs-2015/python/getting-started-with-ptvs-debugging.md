---
title: 'PTVS 시작: 디버깅 | Microsoft 문서'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-python
ms.topic: conceptual
ms.assetid: 82803559-1d60-4c57-98fb-2dc1e0182b42
caps.latest.revision: 5
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: b636dd4f3a5c5265231898573bfdf52de2dff84e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68197707"
---
# <a name="getting-started-with-ptvs-debugging"></a>PTVS 시작: 디버깅
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio의 대화형 디버거를 사용하면 Python 코드의 문제를 쉽게 진단하고 해결할 수 있습니다.  
  
 짧은 [youtube 동영상](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4)을 통해 이러한 지침을 확인할 수 있습니다.  
  
 앞의 시작 항목에서는 빈 Python 애플리케이션 프로젝트 만들고 PythonApplication1.py에 다음 코드를 입력했습니다.  
  
```python  
from math import sin, cos, radians  
import sys  
  
def make_dot_string(x):  
    return ' ' * int(10 * cos(radians(x)) + 10) + 'o'  
  
assert make_dot_string(90) == "          o"  
assert make_dot_string(180) == "o"  
  
def main():  
    for i in range(10000000):  
        s = make_dot_string(i)  
        print(s)  
  
if __name__ == "__main__":  
    sys.exit(int(main() or 0))  
```  
  
 일반적으로 Visual Studio에서 코드로 작업하는 경우 F5 키를 눌러 코드 실행을 시작합니다.  이 명령은 빌드해야 하는 프로젝트 부분을 모두 빌드하고 디버거에서 코드 실행을 시작합니다.  Ctrl+F5를 누르면 디버거 없이 코드를 빌드하고 실행할 수 있습니다.  디버거를 사용할 경우 코드 실행 속도가 약간 느려지지만 비용에 비해 뛰어난 디버깅 기능을 사용할 수 있습니다.  
  
 코드를 실행하는 다른 방법은 한 단계씩 코드 실행 명령(일반적으로 F11 키에 바인딩됨)을 사용하는 것입니다.  F5 키와 비슷하지만 각 문에서 실행을 일시 중지합니다.  특정 지점에서 프로그램을 중단하려는 경우 코드 편집기의 왼쪽 여백에서 왼쪽 포인터 단추를 눌러 중단점을 설정할 수 있습니다.  F5 키를 누르면 중단점이 설정된 줄에서 프로그램 실행이 중단되거나 중지됩니다.  디버그 메뉴에는 한 단계씩 코드 실행에 대한 추가 옵션이 있습니다. 예를 들어 함수 호출 단위 실행(F10), 한 단계씩 함수 호출 실행(F11) 또는 함수의 끝에서 건너뛰기(Shift-F11)가 있습니다.  
  
 디버거에서 중단될 때 수행할 수 있는 추가 작업이 있습니다.  지역 창에는 지역 변수의 현재 값이 표시됩니다.  한 단계씩 코드를 실행하면 지역 표시가 자동으로 업데이트됩니다.  자동 창에는 실행이 중지된 현재 줄 근처의 변수가 표시됩니다.  조사식 창에서 실행이 중지될 때마다 디버거가 자동으로 업데이트하는 Python 식을 입력할 수 있습니다.  편집기 창에서 변수 위에 포인터를 가져가 변수 값의 팝업 표시를 볼 수도 있으며, 이 데이터 팁 표시를 통해 개체를 검사할 수 있습니다.  일부 데이터 형식에는 데이터 팁 표시에서 액세스할 수 있는 특수 시각화 도우미가 있습니다(예: HTML, XML 또는 JSON과 같은 특수 형식을 가진 문자열).  
  
 호출 스택 창에는 디버거가 중지된 현재 문을 초래한 보류 중인 함수 호출이 표시됩니다.  다른 스택 프레임(호출 스택의 줄)을 선택하여 코드가 각 함수에서 계속 실행되는 위치로 이동한 다음 변수 값을 확인할 수 있습니다.  
  
 짧은 [youtube 동영상](https://www.youtube.com/watch?v=bO7wpzgy74A&list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff&index=4)을 통해 이러한 지침을 확인할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Wiki 설명서](https://github.com/Microsoft/PTVS/wiki/Debugging)   
 [PTVS Getting Started and Deep Dive Videos](https://www.youtube.com/playlist?list=PLReL099Y5nRdLgGAdrb_YeTdEnd23s6Ff)(PTVS 시작 및 자세히 알아보기 동영상)
