---
title: FxCopCmd 오류
ms.date: 10/19/2016
description: FxCopCmd 명령에서 반환 하는 오류 코드에 대해 알아봅니다. 각 코드가 나타내는 오류 유형을 확인 하 고 오류를 인식 하는 방법을 알아보세요.
ms.custom: SEO-VS-2020
ms.topic: reference
helpviewer_keywords:
- FxCopCmd errors
ms.assetid: bb614ed0-1b7c-4b56-99ae-da50ef6cfef9
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 88c900ec10ea13e7f9d7092769565703bf52fe8c
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94348934"
---
# <a name="fxcopcmd-tool-errors"></a>FxCopCmd 도구 오류

FxCopCmd는 모든 오류가 치명적이 지는 것을 고려 하지 않습니다. FxCopCmd에 부분 분석을 수행 하는 데 충분 한 정보가 있는 경우 분석을 수행 하 고 발생 한 오류를 보고 합니다. 32 비트 정수인 오류 코드는 오류에 해당 하는 숫자 값의 비트 조합을 포함 합니다.

다음 표에서는 FxCopCmd에서 반환 하는 오류 코드에 대해 설명 합니다.

|오류|숫자 값|
|-----------|-------------------|
|오류 없음|0x0|
|분석 오류|0x1|
|규칙 예외|0x2|
|프로젝트 로드 오류|0x4|
|어셈블리 로드 오류|0x8|
|규칙 라이브러리 로드 오류|0x10|
|보고서 가져오기 로드 오류|0x20|
|출력 오류|0x40|
|명령줄 스위치 오류|0x80|
|초기화 오류|0x100|
|어셈블리 참조 오류|0x200|
|BuildBreakingMessage|0x400|
|알 수 없는 오류|0x1000000|

심각한 오류에 대 한 **분석 오류가** 반환 됩니다. 분석을 완료할 수 없음을 나타냅니다. 해당 하는 경우 오류 코드에도 심각한 오류의 근본 원인이 포함 됩니다. 다음 조건에서는 심각한 오류를 생성 합니다.

- 입력이 부족 하 여 분석을 수행할 수 없습니다.

- 분석이 FxCopCmd에서 처리 되지 않은 예외를 throw 했습니다.

- 지정한 프로젝트 파일을 찾을 수 없거나 손상 되었습니다.

- 출력 옵션을 지정 하지 않았거나 파일을 쓸 수 없습니다.

> [!NOTE]
> FxCopCmd 반환 코드 어셈블리는 오류를 제외 하 고 오류를 제외 하 고 오류 0x200를 **참조** 합니다. 이 반환 코드는 누락 된 간접 참조가 있음을 나타내지만 해당 FxCopCmd는이를 처리할 수 있었습니다. 경고는 일부 분석 결과가 손상 되었을 가능성이 있음을 의미 합니다. 다른 반환 코드와 결합 될 때 **어셈블리 참조 오류** 를 오류로 처리 합니다.

## <a name="see-also"></a>참고 항목

- [코드 분석 애플리케이션 오류](../code-quality/code-analysis-application-errors.md)
