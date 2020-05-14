---
title: 데모 샘플 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- demo sample [Visual Studio ALM]
- code analysis, samples
ms.assetid: 09e1b9f7-5916-4ed6-a001-5c2d7e710682
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 3a49859a8cd1c4ffb01f93bf2539fc16c42f8c4c
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77277889"
---
# <a name="demo-sample"></a>데모 샘플
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 절차에서는 [연습: 오류에 대 한 C/C++ 코드 분석](../code-quality/walkthrough-analyzing-c-cpp-code-for-defects.md)샘플을 만드는 방법을 보여 줍니다. 이 절차에서는 다음을 생성합니다.  
  
- CppDemo 라는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션  
  
- CodeDefects라는 정적 라이브러리 프로젝트  
  
- Annotations라는 정적 라이브러리 프로젝트  
  
  또한이 절차에서는 정적 라이브러리의 헤더 및 .cpp 파일에 대 한 코드를 제공 합니다.  
  
### <a name="create-the-cppdemo-solution-and-the-codedefects-project"></a>CppDemo 솔루션 및 CodeDefects 프로젝트 만들기  
  
1. **파일** 메뉴를 클릭하고, **새로 만들기**를 가리킨 다음, **새 프로젝트**를 클릭합니다.  
  
2. **프로젝트 형식** 트리 목록에서 Visual C++가 VS의 기본 언어가 아닌 경우 **다른 언어**를 확장합니다.  
  
3. **Visual C++** 를 확장한 다음, **일반**을 클릭합니다.  
  
4. **템플릿**에서 **빈 프로젝트**를 클릭합니다.  
  
5. **이름** 텍스트 상자에 **CodeDefects**를 입력합니다.  
  
6. **솔루션용 디렉터리 만들기** 확인란을 선택합니다.  
  
7. **솔루션 이름** 텍스트 상자에 **CppDemo**를 입력합니다.  
  
### <a name="configure-the-codedefects-project-as-a-static-library"></a>정적 라이브러리 형태로 CodeDefects 프로젝트 구성  
  
1. 솔루션 탐색기에서 **CodeDefects**를 마우스 오른쪽 단추로 클릭한 다음, **속성**을 클릭합니다.  
  
2. **구성 속성**을 확장한 다음, **일반**을 클릭합니다.  
  
3. **일반** 목록의 **대상 확장** 옆에 있는 열에서 텍스트를 선택한 다음, **.lib**를 입력합니다.  
  
4. **프로젝트 기본값**의 **구성 형식** 옆에 있는 열을 클릭한 다음, **정적 라이브러리(.lib)** 를 클릭합니다.  
  
### <a name="add-the-header-and-source-file-to-the-codedefects-project"></a>CodeDefects 프로젝트에 헤더 및 원본 파일 추가  
  
1. 솔루션 탐색기에서 **CodeDefects**를 확장하고, **헤더 파일**을 마우스 오른쪽 단추로 클릭하고, **추가**를 클릭한 다음, **새 항목**을 클릭합니다.  
  
2. **새 항목 추가** 대화 상자에서 **코드**를 클릭한 다음, **헤더 파일(.h)** 을 클릭합니다.  
  
3. **이름** 상자에 **Bug.cpp**를 입력한 다음, **추가**를 클릭합니다.  
  
4. 다음 코드를 복사 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기의 **버그 .cpp** 파일에 붙여넣습니다.  
  
    ```  
    #include <windows.h>  
  
    //    
    //These 3 functions are consumed by the sample  
    //  but are not defined. This project cannot be linked!  
    //  
  
    bool CheckDomain( LPCSTR );  
    HRESULT ReadUserAccount();  
  
    //  
    //These constants define the common sizes of the   
    //  user account information throughout the program  
    //  
  
    const int USER_ACCOUNT_LEN = 256;  
    const int ACCOUNT_DOMAIN_LEN = 128;  
    ```  
  
5. 솔루션 탐색기에서 **원본 파일**을 마우스 오른쪽 단추로 클릭하고, **새로 만들기**를 가리킨 다음, **새 항목**을 클릭합니다.  
  
6. **새 항목 추가** 대화 상자에서 **C++ 파일(.cpp)** 을 클릭합니다.  
  
7. **이름** 상자에 **Bug.cpp**를 입력한 다음, **추가**를 클릭합니다.  
  
8. 다음 코드를 복사 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기의 Bug .h 파일에 붙여넣습니다.  
  
    ```  
    #include <stdlib.h>  
    #include "Bug.h"  
  
    // the user account   
    TCHAR g_userAccount[USER_ACCOUNT_LEN] = "";  
    int len = 0;  
  
    bool ProcessDomain()  
    {  
        TCHAR* domain = new TCHAR[ACCOUNT_DOMAIN_LEN];  
        // ReadUserAccount gets a 'domain\user' input from   
        //the user into the global 'g_userAccount'  
        if (ReadUserAccount() )  
        {  
  
            // Copies part of the string prior to the '\'   
            // character onto the 'domain' buffer  
            for( len = 0 ; (len < ACCOUNT_DOMAIN_LEN) && (g_userAccount[len] != '\0') ; len++  )  
            {  
                if ( g_userAccount[len] == '\\' )   
                {  
                    // Stops copying on the domain and user separator ('\')   
                    break;  
                }  
                domain[len] = g_userAccount[len];          
            }  
            if((len= ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
            {  
                // '\' was not found. Invalid domain\user string.  
                delete [] domain;  
                return false;  
            }  
            else  
            {  
                domain[len]='\0';  
            }  
            // Process domain string  
            bool result = CheckDomain( domain );  
  
            delete[] domain;  
            return result;  
        }  
        return false;  
    }  
  
    int path_dependent(int n)  
    {  
        int i;  
        int j;  
        if (n == 0)  
            i = 1;  
        else  
            j = 1;  
        return i+j;   
    }  
    ```  
  
9. **파일** 메뉴를 클릭한 다음, **모두 저장**을 클릭합니다.  
  
### <a name="add-the-annotations-project-and-configure-it-as-a-static-library"></a>주석 프로젝트 추가 및 정적 라이브러리로 구성  
  
1. 솔루션 탐색기에서 **CppDemo**를 클릭하고, **추가**를 가리킨 다음, **새 프로젝트**를 클릭합니다.  
  
2. **새 프로젝트** 대화 상자에서 Visual C#을 확장하고, **일반**을 클릭한 다음, **빈 프로젝트**를 클릭합니다.  
  
3. **이름** 텍스트 상자에 **주석**을 입력한 다음, **추가**를 클릭합니다.  
  
4. 솔루션 탐색기에서 **주석**을 마우스 오른쪽 단추로 클릭한 다음, **속성**을 클릭합니다.  
  
5. **구성 속성**을 확장한 다음, **일반**을 클릭합니다.  
  
6. **일반** 목록의 **대상 확장** 옆에 있는 열에서 텍스트를 선택한 다음, **.lib**를 입력합니다.  
  
7. **프로젝트 기본값**의 **구성 형식** 옆에 있는 열을 클릭한 다음, **정적 라이브러리(.lib)** 를 클릭합니다.  
  
### <a name="add-the-header-file-and-source-file-to-the-annotations-project"></a>주석 프로젝트에 헤더 파일 및 원본 파일 추가  
  
1. 솔루션 탐색기에서 **주석**을 확장하고, **헤더 파일**을 마우스 오른쪽 단추로 클릭하고, **추가**를 클릭한 다음, **새 항목**을 클릭합니다.  
  
2. **새 항목 추가** 대화 상자에서 **헤더 파일(.h)** 을 클릭합니다.  
  
3. **이름** 상자에 **annotations.h**를 입력한 다음, **추가**를 클릭합니다.  
  
4. 다음 코드를 복사 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기의 **주석과** 파일에 붙여넣습니다.  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
  
    struct LinkedList  
    {  
        struct LinkedList* next;  
        int data;  
    };  
  
    typedef struct LinkedList LinkedList;  
  
    [returnvalue:SA_Post( Null=SA_Maybe )] LinkedList* AllocateNode();  
  
    ```  
  
5. 솔루션 탐색기에서 **원본 파일**을 마우스 오른쪽 단추로 클릭하고, **새로 만들기**를 가리킨 다음, **새 항목**을 클릭합니다.  
  
6. **새 항목 추가** 대화 상자에서 **코드**를 클릭한 다음, **C++ 파일(.cpp)** 을 클릭합니다.  
  
7. **이름** 상자에 **annotations.cpp**를 입력한 다음, **추가**를 클릭합니다.  
  
8. 다음 코드를 복사 하 여 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 편집기의 **annotation 파일에 붙여넣습니다.**  
  
    ```  
    #include <CodeAnalysis/SourceAnnotations.h>  
    #include <windows.h>  
    #include <stdlib.h>    
    #include "annotations.h"  
  
    LinkedList* AddTail( LinkedList *node, int value )  
    {  
        LinkedList *newNode = NULL;   
  
        // finds the last node  
        while ( node->next != NULL )   
        {  
            node = node->next;  
        }  
  
        // appends the new node  
        newNode = AllocateNode();   
        newNode->data = value;  
        newNode->next = 0;  
        node->next = newNode;  
  
        return newNode;  
    }  
  
    ```  
  
9. **파일** 메뉴를 클릭한 다음, **모두 저장**을 클릭합니다.
