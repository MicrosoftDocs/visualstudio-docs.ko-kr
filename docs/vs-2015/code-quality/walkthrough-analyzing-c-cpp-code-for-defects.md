---
title: '연습: 오류에 대 한 C + + 코드 분석 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 37
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: c822dbcc6a1ece2040da22a3442dd584c3926d97
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77272441"
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>연습: C/C++ 코드의 오류 분석
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 연습에서는 C/c + + 코드의 코드 분석 도구를 사용 하 여 잠재적 코드 오류에 대 한 C/c + + 코드를 분석 하는 방법을 보여 줍니다.  
  
 이 연습에서는 코드 분석을 사용 하 여 C/c + + 코드를 분석 하 여 잠재적 코드 오류를 처리 하는 과정을 단계별로 안내 합니다.  
  
 여기에서는 다음 단계를 완료하게 됩니다.  
  
- 네이티브 코드에 대해 코드 분석을 실행 합니다.  
  
- 코드 오류 경고를 분석 합니다.  
  
- 경고를 오류로 처리 합니다.  
  
- 코드 오류 분석을 향상 시키기 위해 소스 코드에 주석을 추가 합니다.  
  
## <a name="prerequisites"></a>필수 구성 요소  
  
- [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)] 또는 [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)]  
  
- [데모 샘플](../code-quality/demo-sample.md)의 복사본입니다.  
  
- C/c + +에 대 한 기본적인 이해  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>네이티브 코드에 대 한 코드 오류 분석을 실행 하려면  
  
1. 에서 데모 솔루션을 엽니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
     이제 Demo 솔루션이 **솔루션 탐색기**채워집니다.  
  
2. **빌드** 메뉴에서 **솔루션 다시 빌드**를 클릭합니다.  
  
     솔루션이 오류 또는 경고 없이 빌드됩니다.  
  
3. **솔루션 탐색기**에서 codedefects 있는 프로젝트를 선택 합니다.  
  
4. **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
     **Codedefects 속성 페이지** 대화 상자가 표시 됩니다.  
  
5. **코드 분석**을 클릭합니다.  
  
6. **빌드할 때 C/c + +에 코드 분석 사용** 확인란을 클릭 합니다.  
  
7. CodeDefects 있는 프로젝트를 다시 빌드합니다.  
  
     코드 분석 경고는 **오류 목록**표시 됩니다.  
  
### <a name="to-analyze-code-defect-warnings"></a>코드 오류 경고를 분석 하려면  
  
1. **보기** 메뉴에서 **오류 목록**을 클릭합니다.  
  
     에서 선택한 개발자 프로필에 따라 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **보기** 메뉴에서 **다른 창** 을 가리키고 **오류 목록**를 클릭 해야 할 수도 있습니다.  
  
2. **오류 목록**에서 다음 경고를 두 번 클릭 합니다.  
  
     경고 C6230: 의미 체계가 다른 형식 간의 암시적 캐스트입니다. 부울 컨텍스트에서 HRESULT를 사용 합니다.  
  
     코드 편집기는 함수에서 경고를 발생 시킨 줄을 표시 합니다 `bool``ProcessDomain()` . 이 경고는 HRESULT가 부울 결과가 필요한 ' if ' 문에서 사용 중임을 나타냅니다.  
  
3. SUCCEEDED 매크로를 사용 하 여이 경고를 수정 합니다. 코드는 다음 코드와 유사 해야 합니다.  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4. **오류 목록**에서 다음 경고를 두 번 클릭 합니다.  
  
     경고 C6282: 잘못 된 연산자: 테스트 컨텍스트의 상수에 할당이 있습니다. Was = = 예정 입니까?  
  
5. 같은지 테스트 하 여이 경고를 수정 합니다. 코드는 다음 코드와 유사 하 게 표시 됩니다.  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>경고를 오류로 처리 하려면  
  
1. 버그 .cpp 파일에서 다음 `#pragma` 문을 파일의 시작 부분에 추가 하 여 경고 C6001를 오류로 처리 합니다.  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2. CodeDefects 있는 프로젝트를 다시 빌드합니다.  
  
     **오류 목록**에서 이제 C6001이 오류로 나타납니다.  
  
3. 및를 0으로 초기화 하 여 **오류 목록** 에서 남은 두 C6001 오류를 수정 합니다 `i` `j` .  
  
4. CodeDefects 있는 프로젝트를 다시 빌드합니다.  
  
     프로젝트는 경고 또는 오류 없이 빌드됩니다.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>주석에서 소스 코드 주석 경고를 수정 하려면  
  
1. 솔루션 탐색기에서 주석 프로젝트를 선택 합니다.  
  
2. **프로젝트** 메뉴에서 **속성**을 클릭합니다.  
  
     **주석 속성 페이지** 대화 상자가 표시 됩니다.  
  
3. **코드 분석**을 클릭합니다.  
  
4. **빌드할 때 C/c + +에 코드 분석 사용** 확인란을 선택 합니다.  
  
5. 주석 프로젝트를 다시 빌드합니다.  
  
6. **오류 목록**에서 다음 경고를 두 번 클릭 합니다.  
  
     경고 C6011: NULL 포인터 ' newNode '를 역참조 하 고 있습니다.  
  
     이 경고는 호출자가 반환 값을 확인 하는 데 실패 했음을 나타냅니다. 이 경우 **AllocateNode** 에 대 한 호출에서 NULL 값을 반환할 수 있습니다. AllocateNode에 대 한 함수 선언에 대 한 헤더 파일을 참조 하세요.  
  
7. 주석의 .cpp 파일을 엽니다.  
  
8. 이 경고를 해결 하려면 ' if ' 문을 사용 하 여 반환 값을 테스트 합니다. 코드는 다음 코드와 유사 해야 합니다.  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. 주석 프로젝트를 다시 빌드합니다.  
  
     프로젝트는 경고 또는 오류 없이 빌드됩니다.  
  
### <a name="to-use-source-code-annotation"></a>소스 코드 주석을 사용 하려면  
  
1. 다음 `AddTail` 예제와 같이 사전 및 사후 조건을 사용 하 여 함수에 대 한 정식 매개 변수 및 반환 값에 주석을 추가 합니다.  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2. 주석 프로젝트를 다시 빌드합니다.  
  
3. **오류 목록**에서 다음 경고를 두 번 클릭 합니다.  
  
     경고 C6011: NULL 포인터 ' node '를 역참조 하 고 있습니다.  
  
     이 경고는 함수에 전달 된 노드가 null 일 수 있음을 나타내며 경고가 발생 한 줄 번호를 나타냅니다.  
  
4. 이 경고를 해결 하려면 ' if ' 문을 사용 하 여 반환 값을 테스트 합니다. 코드는 다음 코드와 유사 해야 합니다.  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5. 주석 프로젝트를 다시 빌드합니다.  
  
     프로젝트는 경고 또는 오류 없이 빌드됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [연습: 관리 코드의 코드 오류 분석](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)
