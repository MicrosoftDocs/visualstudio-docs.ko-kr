---
title: C++ 액세스 위반 디버그 | Microsoft Docs
description: 둘 이상의 포인터가 후보일 경우 액세스 위반 문제 해결에 대한 팁을 알아봅니다. 최신 버전의 Visual Studio는 잘못된 포인터를 지명합니다.
ms.custom: SEO-VS-2020
ms.date: 02/05/2019
ms.topic: how-to
f1_keywords:
- vs.debug.access
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- access violation debugging
- debugging [Visual Studio], access violations
ms.assetid: 9311d754-0ce9-4145-b147-88b6ca77ba63
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- cplusplus
ms.openlocfilehash: 3689942c9db9fde3598590cf30100fc590c50753
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112387036"
---
# <a name="how-can-i-debug-a-c-access-violation"></a>C++ 액세스 위반을 디버그하려면 어떻게 해야 하나요?

## <a name="problem-description"></a>문제 설명

프로그램에 액세스 위반이 발생합니다. 어떻게 디버깅할 수 있습니까?

## <a name="solution"></a>솔루션

여러 포인터를 역참조하는 코드 줄에서 액세스 위반이 발생하는 경우 액세스 위반을 유발한 포인터를 찾기 어려울 수 있습니다. Visual Studio 2015 업데이트 1부터 이제 예외 대화 상자가 액세스 위반을 유발한 포인터의 이름을 명시적으로 지정합니다.

예를 들어 다음과 같은 코드에서는 액세스 위반이 발생합니다.

```C++
#include <iostream>
using namespace std;

class ClassC {
public:
  void printHello() {
    cout << "hello world";
  }
};

class ClassB {
public:
  ClassC* C;
  ClassB() {
    C = new ClassC();
  }
};

class ClassA {
public:
  ClassB* B;
  ClassA() {
    // Uncomment to fix
    // B = new ClassB();
  }
};

int main() {
  ClassA* A = new ClassA();
  A->B->C->printHello();

}
```

Visual Studio 2015 업데이트 1에서 이 코드를 실행하는 경우 다음 예외 대화 상자가 표시됩니다.

![‘A->B가 nullptr이었습니다.’에 대한 읽기 권한 위반을 보여 주는 Microsoft Visual Studio 예외 대화 상자의 스크린샷 중단 단추가 선택되어 있습니다.](../debugger/media/accessviolationcplus.png)

포인터가 액세스 위반을 유발한 이유를 확인할 수 없는 경우 전체 코드를 추적하여 문제를 유발한 포인터가 올바르게 할당되었는지 확인합니다.  포인터가 매개 변수로 전달된 경우 제대로 전달되었는지, 실수로 [단순 복사](https://stackoverflow.com/questions/184710/what-is-the-difference-between-a-deep-copy-and-a-shallow-copy)를 만들지 않았는지 확인합니다. 그런 다음, 프로그램의 다른 곳에서 수정되지 않도록 문제가 되는 포인터에 대한 데이터 중단점을 만들어 프로그램의 어딘가에서 값이 실수로 변경되지 않는지 확인합니다. 데이터 중단점에 대한 자세한 내용은 [Using Breakpoints](../debugger/using-breakpoints.md)에서 데이터 중단점 섹션을 참조하세요.

## <a name="see-also"></a>참조
- [네이티브 코드 디버그 FAQ](../debugger/debugging-native-code-faqs.md)