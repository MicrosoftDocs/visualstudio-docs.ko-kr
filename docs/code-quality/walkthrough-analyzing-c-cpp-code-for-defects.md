---
title: '연습: C/C++ 코드의 오류 분석'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
author: mikeblome
ms.author: mblome
manager: markl
ms.workload:
- cplusplus
ms.openlocfilehash: e2154a07d498012c9c45f992ebed51b0218e823a
ms.sourcegitcommit: 8e123bcb21279f2770b28696995450270b4ec0e9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75401014"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>연습: C/C++ 코드의 오류 분석

이 연습에서는 C/C++ 코드에 대 한 코드 분석 도구를 사용 하 여 C/C++ 코드에 잠재적 코드 오류를 분석 하는 방법을 보여 줍니다.

- 네이티브 코드에 대해 코드 분석을 실행 합니다.
- 코드 오류 경고를 분석 합니다.
- 경고를 오류로 처리 합니다.
- 코드 오류 분석을 향상 시키기 위해 소스 코드에 주석을 추가 합니다.

## <a name="prerequisites"></a>전제 조건

- [데모 샘플](../code-quality/demo-sample.md)의 복사본입니다.
- C/C++의 기본적인 이해 해야 합니다.

### <a name="to-run-code-defect-analysis-on-native-code"></a>네이티브 코드에 대 한 코드 오류 분석을 실행 하려면

1. [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 데모 솔루션을 엽니다.

     이제 Demo 솔루션이 **솔루션 탐색기**채워집니다.

2. **빌드** 메뉴에서 **솔루션 다시 빌드**를 클릭합니다.

     솔루션이 오류 또는 경고 없이 빌드됩니다.

3. **솔루션 탐색기**에서 codedefects 있는 프로젝트를 선택 합니다.

4. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

     **Codedefects 속성 페이지** 대화 상자가 표시 됩니다.

5. **코드 분석**을 클릭합니다.

6. 클릭는 **C/C++ 빌드에 코드 분석 사용** 확인란 합니다.

7. CodeDefects 있는 프로젝트를 다시 빌드합니다.

     코드 분석 경고는 **오류 목록**표시 됩니다.

### <a name="to-analyze-code-defect-warnings"></a>코드 오류 경고를 분석 하려면

1. **보기** 메뉴에서 **오류 목록**을 클릭합니다.

     [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]에서 선택한 개발자 프로필에 따라 **보기** 메뉴에서 **다른 창** 을 가리킨 다음 **오류 목록**를 클릭 해야 할 수도 있습니다.

2. **오류 목록**에서 다음 경고를 두 번 클릭 합니다.

     경고 C6230: 의미 체계가 다른 형식 간의 암시적 캐스트입니다. 부울 컨텍스트에서 HRESULT를 사용 합니다.

     코드 편집기는 함수 `bool ProcessDomain()`에 경고를 발생 시킨 줄을 표시 합니다. 이 경고는 `HRESULT` 부울 결과가 필요한 ' if ' 문에서 사용 중임을 나타냅니다.  이 오류는 일반적으로이 함수에서 `S_OK` HRESULT가 반환 될 때 success를 나타내지만 부울 값으로 변환 될 때 `false`로 계산 되기 때문에 발생 합니다.

3. `SUCCEEDED` 매크로를 사용 하 여이 경고를 수정 합니다 .이 매크로는 `HRESULT` 반환 값이 성공을 나타내는 경우 `true`으로 변환 됩니다. 코드는 다음 코드와 유사 해야 합니다.

   ```cpp
   if (SUCCEEDED (ReadUserAccount()) )
   ```

4. **오류 목록**에서 다음 경고를 두 번 클릭 합니다.

     경고 C6282: 잘못 된 연산자: 테스트 컨텍스트의 상수에 할당이 있습니다. Was = = 예정 입니까?

5. 같은지 테스트 하 여이 경고를 수정 합니다. 코드는 다음 코드와 유사 하 게 표시 됩니다.

   ```cpp
   if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))
   ```

### <a name="to-treat-warning-as-an-error"></a>경고를 오류로 처리 하려면

1. 버그 .cpp 파일에서 다음 `#pragma` 문을 파일의 시작 부분에 추가 하 여 경고 C6001를 오류로 처리 합니다.

   ```cpp
   #pragma warning (error: 6001)
   ```

2. CodeDefects 있는 프로젝트를 다시 빌드합니다.

     에 **오류 목록**, C6001이 초기화를 오류로 표시 합니다.

3. `i`를 초기화 하 여 **오류 목록** 에서 남은 두 C6001 오류를 수정 하 고 `j` 0으로 수정 합니다.

4. CodeDefects 있는 프로젝트를 다시 빌드합니다.

     프로젝트는 경고 또는 오류 없이 빌드됩니다.

### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>주석에서 소스 코드 주석 경고를 수정 하려면

1. 솔루션 탐색기에서 주석 프로젝트를 선택 합니다.

2. **프로젝트** 메뉴에서 **속성**을 클릭합니다.

     **주석 속성 페이지** 대화 상자가 표시 됩니다.

3. **코드 분석**을 클릭합니다.

4. 선택 된 **C/C++ 빌드에 코드 분석 사용** 확인란 합니다.

5. 주석 프로젝트를 다시 빌드합니다.

6. **오류 목록**에서 다음 경고를 두 번 클릭 합니다.

     경고 C6011: 'newNode' NULL 포인터를 역참조 하 고 있습니다.

     이 경고는 호출자가 반환 값을 확인 하는 데 실패 했음을 나타냅니다. 이 경우 **AllocateNode** 에 대 한 호출에서 NULL 값을 반환할 수 있습니다. AllocateNode에 대 한 함수 선언에 대 한 헤더 파일을 참조 하세요.

7. 주석의 .cpp 파일을 엽니다.

8. 이 경고를 해결 하려면 ' if ' 문을 사용 하 여 반환 값을 테스트 합니다. 코드는 다음 코드와 유사 해야 합니다.

   ```cpp
   if (nullptr != newNode)
   {
       newNode->data = value;
       newNode->next = 0;
       node->next = newNode;
   }
   ```

9. 주석 프로젝트를 다시 빌드합니다.

     프로젝트는 경고 또는 오류 없이 빌드됩니다.

### <a name="to-use-source-code-annotation"></a>소스 코드 주석을 사용 하려면

1. `AddTail` 함수에 대 한 정식 매개 변수 및 반환 값에 주석을 추가 하 여 포인터 값이 null 일 수 있음을 표시 합니다.

   ```cpp
   _Ret_maybenull_ LinkedList* AddTail(_Maybenull_ LinkedList* node, int value)
   ```

2. 주석 프로젝트를 다시 빌드합니다.

3. **오류 목록**에서 다음 경고를 두 번 클릭 합니다.

     경고 C6011: NULL 포인터 역참조 'node'.

     이 경고는 함수에 전달 된 노드가 null 일 수 있음을 나타내며 경고가 발생 한 줄 번호를 나타냅니다.

4. 이 경고를 해결 하려면 함수 시작 부분에 ' if ' 문을 사용 하 여 전달 된 값을 테스트 합니다. 코드는 다음 코드와 유사 해야 합니다.

   ```cpp
   if (nullptr == node)
   {
        return nullptr;
   }
   ```

5. 주석 프로젝트를 다시 빌드합니다.

     이제 프로젝트는 경고 또는 오류 없이 빌드됩니다.

## <a name="see-also"></a>참조

[연습: 코드 오류에 대 한 관리되는 코드를 분석](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
[C/C++ 코드 분석](../code-quality/code-analysis-for-c-cpp-overview.md)
