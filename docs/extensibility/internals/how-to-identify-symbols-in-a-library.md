---
title: '방법: 라이브러리에서 기호 식별 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fd091f003909110c696c2e42ad80d6c6ea4859d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905399"
---
# <a name="how-to-identify-symbols-in-a-library"></a>방법: 라이브러리에서 기호 식별
기호 검색 도구는 기호의 계층 뷰를 표시 합니다. 기호는 네임 스페이스, 개체, 클래스, 클래스 멤버 및 기타 언어 요소를 나타냅니다.

 계층의 각 기호는 다음 인터페이스를 통해 기호 라이브러리에서 개체 관리자로 전달 된 탐색 정보로 식별할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 계층에서 기호 위치는 기호를 구별 합니다. 기호 검색 도구를 사용 하 여 특정 기호로 이동할 수 있습니다. 기호에 대 한 정규화 된 고유 경로는 위치를 결정 합니다. 경로의 각 요소는 노드입니다. 경로는 최상위 노드로 시작 하 고 특정 기호로 끝납니다. 예를 들어 M1 메서드가 C1 클래스의 멤버이 고 C1이 N1 네임 스페이스에 있는 경우 M1 메서드의 전체 경로는 N1입니다. C1. M 1. 이 경로에는 세 개의 노드 N1, C1 및 M1이 포함 됩니다.

 개체 관리자는 탐색 정보를 사용 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 하 여 계층에서 기호를 찾고 선택 하 고 선택 된 상태로 유지할 수 있습니다. 탐색 도구를 사용 하 여 탐색 도구를 탐색할 수 있습니다. **개체 브라우저** 를 사용 하 여 프로젝트에서 기호를 검색 하는 동안 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 메서드를 마우스 오른쪽 단추로 클릭 하 고 **호출 브라우저** 도구를 시작 하 여 호출 그래프에 메서드를 표시할 수 있습니다.

 기호 위치를 설명 하는 두 가지 폼입니다. 정규 형식은 기호의 정규화 된 경로를 기반으로 합니다. 계층 구조에 있는 기호의 고유한 위치를 나타냅니다. 기호 검색 도구와는 독립적입니다. 정식 폼 정보를 가져오기 위해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체 관리자는 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> . 프레젠테이션 폼은 특정 기호 검색 도구에서 기호 위치를 설명 합니다. 기호의 위치는 계층에서 다른 기호의 위치를 기준으로 합니다. 지정 된 기호에는 여러 개의 프레젠테이션 경로를 포함할 수 있지만 정식 경로는 하나만 있을 수 있습니다. 예를 들어, C1 클래스가 C2 클래스에서 상속 되 고 두 클래스가 모두 N1 네임 스페이스에 있는 경우 **개체 브라우저** 는 다음과 같은 계층 구조 트리를 표시 합니다.

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 이 예제에서 C2 클래스의 정식 경로는 N1 + C2입니다. C2의 프레젠테이션 경로에는 C1 및 "기본 및 인터페이스" 노드가 포함 되어 있습니다. N1 + C1 + "기본 및 인터페이스" + C2.

 프레젠테이션 양식 정보를 가져오기 위해 개체 관리자는 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> .

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>정식 및 프레젠테이션 양식 정보를 가져오려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 메서드를 구현합니다.

     개체 관리자는이 메서드를 호출 하 여 기호의 정식 경로에 포함 된 노드의 목록을 가져옵니다.

    ```vb
    Public Function EnumCanonicalNodes(ByRef ppEnum As Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes) As Integer
        Dim EnumNavInfoNodes As CallBrowserEnumNavInfoNodes = _New CallBrowserEnumNavInfoNodes(m_strMethod)
        ppEnum = CType(EnumNavInfoNodes, IVsEnumNavInfoNodes)
        Return 0
    End Function
    ```

    ```csharp
    public int EnumCanonicalNodes(out Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes ppEnum)
    {
        CallBrowserEnumNavInfoNodes EnumNavInfoNodes =
            new CallBrowserEnumNavInfoNodes(m_strMethod);
        ppEnum = (IVsEnumNavInfoNodes)(EnumNavInfoNodes);
        return 0;
    }

    ```

2. <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A> 메서드를 구현합니다.

     개체 관리자는이 메서드를 호출 하 여 기호의 프레젠테이션 경로에 포함 된 노드의 목록을 가져옵니다.

## <a name="see-also"></a>추가 정보
- [기호 검색 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [방법: 개체 관리자를 사용 하 여 라이브러리 등록](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [방법: 라이브러리에서 제공 하는 기호 목록을 개체 관리자에 게 노출](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
