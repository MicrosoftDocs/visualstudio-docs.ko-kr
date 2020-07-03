---
title: 방법 - 특정 함수로 계측 제한 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- performance tools, limiting instrumentation to functions
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: 0ca92b9f4b7594abc0815038799147ac44091cb3
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85327629"
---
# <a name="how-to-limit-instrumentation-to-specific-functions"></a>방법: 특정 함수로 계측 제한
**성능 세션**의 **고급** 페이지 또는 대상 이진 속성 페이지에서 옵션을 설정하여 계측 및 데이터 수집을 하나 이상의 함수로 제한할 수 있습니다.

- 성능 세션 속성 페이지에서 함수를 지정하면 세션의 모든 계측된 이진 파일에서 해당 함수만 계측됩니다.

- 대상 이진 파일의 속성 페이지에서 함수를 지정하면 해당하는 특정 이진 파일에 있는 함수만 계측됩니다. 성능에 대한 다른 이진 파일에 있는 함수는 일반적인 방식으로 계측됩니다.

  계측 프로파일링 방법을 선택할 경우에만 이 방식으로 데이터 수집을 제한할 수 있습니다.

> [!NOTE]
> **성능 세션** 속성 페이지의 **고급** 페이지를 사용하여 프로파일링 도구 [VSInstr](../profiling/vsinstr.md) 명령줄 계측 도구에 사용할 수 있는 기타 옵션을 설정할 수도 있습니다.

### <a name="to-limit-instrumentation-to-specific-functions-in-a-performance-session"></a>성능 세션의 특정 함수로 계측을 제한하려면

1. **성능 탐색기**에서 세션 이름을 마우스 오른쪽 단추로 클릭한 다음 **속성**을 클릭합니다.

    **속성 페이지** 대화 상자가 표시됩니다.

2. **속성 페이지** 대화 상자에서 **고급**을 클릭합니다.

3. **추가 계측 옵션** 텍스트 상자에서 다음 구문을 사용하여 계측할 함수의 이름을 입력합니다.

    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`

    `FuncSpec`는 네임스페이스 및 함수 이름입니다. 형식은 `Namespace` **::** `FunctionName`입니다. 세미콜론을 사용하여 여러 함수를 구분합니다. 별표(\*)를 사용하여 하나 이상의 문자에 대한 와일드 카드를 지정합니다. 예를 들어 **/include:MyNS::\\** *는 MyNS 네임스페이스에 있는 모든 함수를 지정합니다.

   > [!NOTE]
   > 이진 파일의 함수를 나열하려면 프로파일링 도구 설치 디렉터리([명령줄 도구 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 참조)에서 명령 프롬프트 창을 연 다음, **vsinstr /DumpFuncs**를 입력합니다.

### <a name="to-limit-instrumentation-to-specific-functions-in-a-binary"></a>이진 파일의 특정 함수로 계측을 제한하려면

1. **성능 탐색기**에 있는 성능 세션의 **대상** 노드에서 이진 파일 이름을 찾습니다.

2. 이진 파일 이름을 마우스 오른쪽 단추로 클릭한 후 **속성**을 클릭합니다.

    **속성 페이지** 대화 상자가 표시됩니다.

3. **속성 페이지** 대화 상자에서 **고급**을 클릭합니다.

4. **추가 계측 옵션** 텍스트 상자에서 다음 구문을 사용하여 계측할 함수의 이름을 입력합니다.

    **/include:** `FuncSpec` **[;** `FuncSpec` **]** `...`

    `FuncSpec`는 네임스페이스 및 함수 이름입니다. 형식은 `Namespace` **::** `FunctionName`입니다. 세미콜론을 사용하여 여러 함수를 구분합니다. 별표(\*)를 사용하여 하나 이상의 문자에 대한 와일드 카드를 지정합니다. 예를 들어 **/include:MyNS::\\** *는 MyNS 네임스페이스에 있는 모든 함수를 지정합니다.

   > [!NOTE]
   > 이진 파일의 함수를 나열하려면 프로파일링 도구 설치 디렉터리([명령줄 도구 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md) 참조)에서 명령 프롬프트 창을 연 다음, **vsinstr /DumpFuncs**를 입력합니다.

## <a name="see-also"></a>참조
- [데이터 수집 제어](../profiling/controlling-data-collection.md)
- [방법: 계측을 특정 DLL로 제한](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)
- [방법: 추가 계측 옵션 지정](../profiling/how-to-specify-additional-instrumentation-options.md)
