---
title: '방법: 라이브러리에서 기호 식별 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Call Browser tool, identifying symbols in the library
- Call Browser tool
ms.assetid: 8fb0de61-71e7-42d1-8b41-2ad915474384
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1fe920fabd05a875b336467fbba16e4229fa9613
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708011"
---
# <a name="how-to-identify-symbols-in-a-library"></a>방법: 라이브러리에서 기호 식별
기호 검색 도구는 기호의 계층적 보기를 표시합니다. 기호는 네임스페이스, 개체, 클래스, 클래스 멤버 및 기타 언어 요소를 나타냅니다.

 계층구조의 각 심볼은 기호 라이브러리를 통해 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 다음 인터페이스를 통해 개체 관리자에게 전달되는 탐색 정보로 식별할 수 있습니다.

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfoNode>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsEnumNavInfoNodes>.

 계층 구조에서 기호의 위치는 기호를 구분합니다. 심볼 브라우징 도구를 사용하여 특정 기호로 이동할 수 있습니다. 기호에 대한 고유하고 정규화된 경로가 위치를 결정합니다. 경로의 각 요소는 노드입니다. 경로는 최상위 노드로 시작하여 특정 기호로 끝납니다. 예를 들어 M1 메서드가 C1 클래스의 멤버이고 C1이 N1 네임스페이스에 있는 경우 M1 메서드의 전체 경로는 N1입니다. C1. M1. 이 경로에는 N1, C1 및 M1의 세 개의 노드가 포함됩니다.

 탐색 정보를 사용하면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 개체 관리자가 계층 구조에서 선택한 기호를 찾고 선택하고 유지할 수 있습니다. 그것은 다른 하나의 브라우징 도구에서 탐색 할 수 있습니다. 개체 **브라우저를** 사용하여 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 프로젝트에서 기호를 탐색하는 동안 메서드를 마우스 오른쪽 단추로 클릭하고 **브라우저 호출** 도구를 시작하여 호출 그래프에 메서드를 표시할 수 있습니다.

 두 가지 양식은 기호 위치를 설명합니다. 표준 형식은 기호의 정규화된 경로를 기반으로 합니다. 계층 구조에서 기호의 고유한 위치를 나타냅니다. 심볼 브라우징 도구와는 무관합니다. 표준 양식 정보를 얻으려면 개체 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 관리자가 <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 메서드를 호출합니다. 프레젠테이션 양식은 특정 심볼 검색 도구 내에서 기호의 위치를 설명합니다. 기호의 위치는 계층 구조의 다른 기호의 위치를 기준으로 합니다. 지정된 기호에는 여러 개의 프레젠테이션 경로가 있을 수 있지만 하나의 표준 경로만 있을 수 있습니다. 예를 들어 C1 클래스가 C2 클래스에서 상속되고 두 클래스가 모두 N1 네임스페이스에 있는 경우 **개체 브라우저는** 다음과 같은 계층 트리를 표시합니다.

```
N1
    C1
        Bases and Interfaces
            C2
    C2
        Bases and Interfaces
. . . . . . . . . . .

```

 이 예제에서 C2 클래스의 표준 경로는 N1 + C2입니다. C2의 프리젠 테이션 경로는 C1 및 "베이스 및 인터페이스"노드를 포함 : N1 + C1 + "베이스 및 인터페이스"+ C2.

 프레젠테이션 양식 정보를 얻으려면 개체 관리자가 메서드를 호출합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumPresentationNodes%2A>

## <a name="to-obtain-canonical-and-presentation-forms-information"></a>표준 및 프레젠테이션 양식 정보를 얻으려면

1. <xref:Microsoft.VisualStudio.Shell.Interop.IVsNavInfo.EnumCanonicalNodes%2A> 메서드를 구현합니다.

     개체 관리자는 기호의 표준 경로에 포함된 노드 목록을 얻기 위해 이 메서드를 호출합니다.

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

     개체 관리자는 기호의 프레젠테이션 경로에 포함된 노드 목록을 가져오려면 이 메서드를 호출합니다.

## <a name="see-also"></a>참조
- [심볼 브라우징 도구 지원](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [방법: 개체 관리자와 라이브러리 등록](../../extensibility/internals/how-to-register-a-library-with-the-object-manager.md)
- [방법: 라이브러리에서 제공하는 기호 목록을 개체 관리자에 노출](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
