---
title: 코드 조각 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.ExpansionManagerImport
- vs.codesnippetmanager
helpviewer_keywords:
- code snippets, replacement parameters
- code snippets, surround with
- replacement parameters
- code snippets, expansion
- surround with
- code snippets
ms.assetid: 85976ad9-4c9a-4e7b-896e-66ec6f955199
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 5b41b6e4d4a7635b32edb5697c89ecb1249fb9da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72619721"
---
# <a name="code-snippets"></a>코드 조각
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

코드 조각은 상황에 맞는 메뉴 명령이나 바로 가기 키 조합을 사용하여 코드 파일에 삽입할 수 있는 다시 사용 가능한 작은 블록입니다. 일반적으로 try-finally 또는 if-else 블록과 같이 자주 사용되는 코드 블록을 포함하지만 전체 클래스나 메서드를 삽입하는 데 사용할 수 있습니다.

## <a name="expansion-snippets-and-surround-with-snippets"></a>확장 조각 및 코드 감싸기 조각
 Visual Studio에는 다음 두 종류의 코드 조각이 있습니다. 확장 조각은 지정된 삽입 지점에 추가되고 조각 바로 가기를 대체할 수 있으며, 코드 감싸기 조각(C# 및 C++만 해당)은 선택한 코드 블록 주위에 추가됩니다.

 삽입 조각의 예: C#에서 바로 가기 tryf는 try-finally 블록을 삽입하는 데 사용됩니다.

```
try
{

}
finally
{

}

```

 코드 창의 상황에 맞는 메뉴에서 **조각 삽입**을 클릭하여 이 조각을 삽입하고 **Visual C#**, 형식 `tryf`를 차례로 입력하고 TAB를 누르거나, `tryf`를 입력하고 TAB+TAB을 누릅니다.

 코드 감싸기 조각의 예: C++에서 바로 가기 `if`는 삽입 조각 또는 코드 감싸기 조각으로 사용할 수 있습니다. 코드 줄(예: `return FALSE;`)을 선택하고 **코드 감싸기**, **if**를 차례로 클릭하면 해당 줄 주위에서 조각이 확장됩니다.

```
if (true)
{
    return FALSE;
}

```

## <a name="snippet-replacement-parameters"></a>조각 대체 매개 변수
 조각은 작성 중인 정확한 코드에 맞게 바꿔야 하는 자리 표시자인 대체 매개 변수를 포함할 수 있습니다. 이전 예제에서 `true`는 적절한 조건으로 바꿀 대체 매개 변수입니다. 조각에서 같은 매개 변수의 모든 인스턴스에 대해 반복해서 대체를 수행합니다.

 예를 들어 Visual Basic에는 속성을 삽입하는 코드 조각이 있습니다. 코드 창의 상황에 맞는 메뉴에서 **조각 삽입**을 클릭하고 **코드 패턴**, **속성, 프로시저, 이벤트**, 속성 정의를 차례로 클릭합니다. 다음 코드가 삽입됩니다.

```
Private newPropertyValue As String
Public Property NewProperty() As String
    Get
        Return newPropertyValue
    End Get
    Set(ByVal value As String)
        newPropertyValue = value
    End Set
End Property

```

 `newPropertyValue`를 `m_property`로 변경하면 `newPropertyValue`의 모든 인스턴스가 변경됩니다. 속성 선언에서 `String`을 `Int`로 변경하면 set 메서드의 값도 `Int`로 변경됩니다.

## <a name="code-snippet-manager"></a>코드 조각 관리자
 **도구/코드 조각 관리자**를 클릭하여 현재 설치된 모든 코드 조각과 디스크에서의 위치를 확인할 수 있습니다. 조각은 언어별로 표시됩니다.

 **코드 조각 관리자** 대화 상자에서 **추가** 및 **제거** 단추를 사용하여 조각 디렉터리를 추가 및 제거할 수 있습니다. 개별 코드 조각을 추가하려면 **가져오기** 단추를 사용합니다.

## <a name="see-also"></a>관련 항목
 [연습: 코드 조각 만들기](../ide/walkthrough-creating-a-code-snippet.md) [방법: 코드 조각 배포](../ide/how-to-distribute-code-snippets.md) [코드 조각 사용에 대 한 모범 사례 코드](../ide/best-practices-for-using-code-snippets.md) [조각 문제 해결](../ide/troubleshooting-snippets.md) 코드 조각 자습서 [Visual c # 코드 조각](../ide/visual-csharp-code-snippets.md) [Visual C++ 코드 조각](../ide/visual-cpp-code-snippets.md) [코드 조각 스키마 참조](../ide/code-snippets-schema-reference.md)
