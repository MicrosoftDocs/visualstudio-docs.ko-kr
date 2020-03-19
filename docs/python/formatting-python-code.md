---
title: Python 코드 서식 지정
description: Visual Studio는 간격, 명령문, 래핑 및 주석을 포함하여 Python 코드를 자동으로 다시 포맷할 수 있습니다.
ms.date: 03/13/2019
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: 6e95d05c3fbc0dd46d235c7480bd4a9caa48947e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "62957539"
---
# <a name="format-python-code"></a>Python 코드 서식 지정

Visual Studio에서는 미리 구성된 서식 옵션과 일치하도록 빠르게 코드 서식을 다시 지정할 수 있습니다.

- 선택 항목의 서식을 지정하려면 **편집** > **고급** > **선택 영역 서식 지정**을 선택하거나 **Ctrl**+**E** > **F**를 누릅니다.
- 전체 파일의 서식을 지정하려면 **편집** > **고급** > **문서 서식 지정**을 선택하거나 **Ctrl**+**E** > **D**를 누릅니다.

옵션은 **도구** > **옵션** > **텍스트 편집기** > **Python** > **서식 지정** 및 중첩된 탭을 통해 설정됩니다. 이러한 옵션을 표시하려면 **모든 설정 표시**를 선택해야 합니다.

![Visual Studio의 Python 서식 옵션](media/options-editor-formatting.png)

기본적으로 서식 옵션은 [PEP 8 스타일 가이드](https://www.python.org/dev/peps/pep-0008/)의 상위 집합과 일치하도록 설정됩니다. **일반** 탭은 서식을 적용할 시기를 결정하며, 다른 세 개의 탭에 대한 설정은 이 문서에서 설명합니다.

[Visual Studio의 Python 지원](installing-python-support-in-visual-studio.md)은 이후 섹션에 설명된 대로 **편집** > **고급** 메뉴에 유용한 [**주석 단락 채우기**](#fill-comment-paragraph-command) 명령도 추가합니다.

## <a name="spacing"></a>간격

**간격**은 다양한 언어 구문 주위에 공백이 삽입되거나 제거되는 위치를 제어합니다. 각 옵션에는 다음 세 가지 가능한 값이 있습니다.

- 선택한 상태: 간격을 적용합니다.
- 선택 취소됨: 모든 간격을 제거합니다.
- 비활성화 상태: 원래 서식을 그대로 유지합니다.

다양한 옵션에 대한 예제가 다음 표에 나와 있습니다.

| 클래스 정의 옵션 | 선택한 상태 | 선택 취소됨 |
| --- | --- | --- |
| **클래스 선언의 이름과 기본 목록 사이에 공백 삽입** | `class X (object): pass` | `class X(object): pass` |
| **기본 목록 괄호 내에 공백 삽입** | `class X( object ): pass` | `class X(object): pass` |
| **빈 기본 목록 괄호 내에 공백 삽입** | `class X( ): pass` | `class X(): pass` |

<br/>

| 함수 정의 옵션 | 선택한 상태 | 선택 취소됨 |
| --- | --- | --- |
| **함수 선언의 이름과 매개 변수 목록 사이에 공백 삽입** | `def X (): pass` | `def X(): pass` |
| **매개 변수 목록 괄호 내에 공백 삽입** | `def X( a, b ): pass` | `def X(a, b): pass` |
| **빈 매개 변수 목록 괄호 내에 공백 삽입** | `def X( ): pass` | `def X(): pass` |
| **기본 매개 변수 값의 '=' 주위에 공백 삽입** | `includes X(a = 42): pass` | `includes X(a=42): pass` |
| **반환 주석 연산자 앞뒤에 공백 삽입** | `includes X() -> 42: pass` | `includes X()->42: pass` |

<br/>

| 연산자 옵션 | 선택한 상태 | 선택 취소됨 |
| --- | --- | --- |
| **이진 연산자 주위에 공백 삽입** | `a + b` | `a+b` |
| **할당 주위에 공백 삽입** | `a = b` | `a=b` |

<br/>

| 식 간격 옵션 | 선택한 상태 | 선택 취소됨 |
| --- | --- | --- |
| **함수 호출의 이름과 인수 목록 사이에 공백 삽입** | `X ()` | `X()` |
| **빈 인수 목록 괄호 내부에 공백 삽입** | `X( )` | `X()` |
| **인수 목록 괄호의 내부에 공백 삽입** | `X( a, b )` | `X(a, b)` |
| **식 괄호 내에 공백 삽입** | `( a )` | `(a)` |
| **빈 튜플 괄호 내에 공백 삽입** | `( )` | `()` |
| **튜플 괄호 내에 공백 삽입** | `( a, b )` | `(a, b)` |
| **빈 대괄호 내에 공백 삽입** | `[ ]` | `[]` |
| **목록 대괄호 내에 공백 삽입** | `[ a, b ]` | `[a, b]` |
| **여는 대괄호 앞에 공백 삽입** | `x [i]` | `x[i]` |
| **대괄호 내에 공백 삽입** | `x[ i ]` | `x[i]` |

<br/>

## <a name="statements"></a>문

**문** 옵션은 다양한 문을 더 많은 Python 양식으로 자동으로 다시 작성하는 것을 제어합니다.

| 옵션 | 서식 지정 앞 | 서식 지정 뒤 |
| --- | --- | --- |
| **새 줄에 가져온 모듈 배치** | `import sys, pickle` | `import sys`<br/>`import pickle` |
| **불필요한 세미콜론 제거** | `x = 42;` | `x = 42` |
| **새 줄에 여러 명령문 배치** | `x = 42; y = 100` | `x = 42`<br/>`y = 100` |

## <a name="wrapping"></a>줄 바꿈

**줄 바꿈**을 사용하여 **최대 주석 너비**(기본값: 80)를 설정할 수 있습니다. **너무 넓은 주석 줄 바꿈** 옵션을 설정하는 경우 Visual Studio에서 최대 너비를 초과하지 않도록 주석의 서식을 다시 지정합니다.

```python
# Wrapped to 40 columns
# There should be one-- and preferably
# only one --obvious way to do it.
```

```python
# Not-wrapped:
# There should be one-- and preferably only one --obvious way to do it.
```

## <a name="fill-comment-paragraph-command"></a>주석 단락 채우기 명령

**편집** > **고급** > **주석 단락 채우기**(**Ctrl**+**E** > **P**)는 주석 텍스트를 다시 배치하고, 해당 서식을 지정하며, 짧은 줄을 결합하고, 긴 줄을 분리합니다.

예를 들어:

```python
# foo
# bar
# baz
```

다음으로 변경합니다.

```python
# foo bar baz
```

```python
# This is a very long long long long long long long long long long long long long long long long long long long comment
```

다음으로 변경합니다.

```python
# This is a very long long long long long long long long long long long long
# long long long long long long long comment
```
