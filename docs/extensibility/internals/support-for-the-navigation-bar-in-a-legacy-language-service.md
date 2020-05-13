---
title: 레거시 언어 서비스의 탐색 모음 지원 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Navigation bar, supporting in language services [managed package framework]
- language services [managed package framework], Navigation bar
ms.assetid: 2d301ee6-4523-4b82-aedb-be43f352978e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f86dabb0594b1e33c45808efb387fcbe313e3de3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704859"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>레거시 언어 서비스의 탐색 모음 지원
편집기 뷰 상단의 탐색 모음에는 파일의 형식과 멤버가 표시됩니다. 형식은 왼쪽 드롭다운에 표시되고 멤버는 오른쪽 드롭다운에 표시됩니다. 사용자가 유형을 선택하면 카포트가 형식의 첫 번째 줄에 배치됩니다. 사용자가 멤버를 선택하면 카포트가 멤버의 정의에 배치됩니다. 드롭다운 상자는 캐리트의 현재 위치를 반영하도록 업데이트됩니다.

## <a name="displaying-and-updating-the-navigation-bar"></a>탐색 모음 표시 및 업데이트
 탐색 모음을 지원하려면 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 클래스에서 클래스를 파생하고 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 메서드를 구현해야 합니다. 언어 서비스에 코드 창이 지정되면 <xref:Microsoft.VisualStudio.Package.LanguageService> 기본 클래스는 코드 <xref:Microsoft.VisualStudio.Package.CodeWindowManager>창을 나타내는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 개체를 포함하는 를 인스턴스화합니다. 그러면 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 개체에 새 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 개체가 지정됩니다. 메서드는 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> 개체를 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 가져옵니다. <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 클래스의 인스턴스를 반환하는 경우 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 메서드를 호출하여 내부 목록을 채우고 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 개체를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 드롭다운 막대 관리자에게 전달합니다. 드롭다운 막대 관리자는 개체의 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> 메서드를 호출하여 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 두 개의 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> 드롭다운 막대를 포함하는 개체를 설정합니다.

 카를트가 이동하면 <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> 메서드가 <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> 메서드를 호출합니다. 기본 <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 클래스의 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 메서드를 호출하여 탐색 모음의 상태를 업데이트합니다. 개체 집합을 <xref:Microsoft.VisualStudio.Package.DropDownMember> 이 메서드에 전달합니다. 각 개체는 드롭다운의 항목을 나타냅니다.

## <a name="the-contents-of-the-navigation-bar"></a>탐색 모음의 내용
 탐색 모음에는 일반적으로 형식 목록과 구성원 목록이 포함되어 있습니다. 형식 목록에는 현재 원본 파일에서 사용할 수 있는 모든 형식이 포함됩니다. 형식 이름에는 전체 네임스페이스 정보가 포함됩니다. 다음은 두 가지 유형이 있는 C# 코드의 예입니다.

```csharp
namespace TestLanguagePackage
{
    public class TestLanguageService
    {
        internal struct Token
        {
            int tokenID;
        }
        private Tokens[] tokens;
        private string serviceName;
    }
}
```

 유형 목록이 `TestLanguagePackage.TestLanguageService` 표시되고 `TestLanguagePackage.TestLanguageService.Tokens`.

 멤버 목록에는 형식 목록에서 선택한 형식의 사용 가능한 멤버가 표시됩니다. 위의 코드 예제를 `TestLanguagePackage.TestLanguageService` 사용하여 선택된 형식인 경우 멤버 목록에는 `tokens` 개인 `serviceName`멤버와 . 내부 구조가 `Token` 표시되지 않습니다.

 멤버 목록을 구현하여 캐릿이 그 안에 배치될 때 멤버 이름을 굵게 만들 수 있습니다. 멤버는 회색으로 표시된 텍스트로 표시할 수 있으며, 이는 캐번이 현재 배치된 범위 내에 있지 않음을 나타냅니다.

## <a name="enabling-support-for-the-navigation-bar"></a>탐색 모음에 대한 지원 사용
 탐색 모음에 대한 지원을 사용하려면 `ShowDropdownBarOption` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 특성의 매개 `true`변수를 로 설정해야 합니다. 이 매개 변수는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 속성을 설정합니다. 탐색 모음을 지원하려면 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스의 메서드에서 개체를 구현해야 합니다.

 메서드를 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> 구현할 때 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 속성이 로 `true`설정된 경우 개체를 반환할 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 수 있습니다. 개체를 반환하지 않으면 탐색 막대가 표시되지 않습니다.

 탐색 모음을 표시하는 옵션은 사용자가 설정할 수 있으므로 편집기 보기가 열려 있는 동안 이 컨트롤을 다시 설정할 수 있습니다. 변경이 발생하기 전에 사용자는 편집기 창을 닫고 다시 열어야 합니다.

## <a name="implementing-support-for-the-navigation-bar"></a>탐색 모음에 대한 지원 구현
 메서드는 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 두 개의 목록(각 드롭다운에 대해 하나씩)과 각 목록의 현재 선택을 나타내는 두 개의 값을 사용합니다. 목록 및 선택 값을 업데이트할 수 있으며, 이 경우 메서드를 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 반환하여 `true` 목록이 변경되었음을 나타냅니다.

 형식 드롭다운에서 선택 영역이 변경되면 새 형식을 반영하도록 멤버 목록을 업데이트해야 합니다. 구성원 목록에 표시되는 내용은 다음 중 하나일 수 있습니다.

- 현재 형식의 멤버 목록입니다.

- 원본 파일에서 사용할 수 있지만 현재 형식에 없는 모든 멤버는 회색으로 표시된 텍스트로 표시됩니다. 사용자는 여전히 회색으로 된 멤버를 선택할 수 있으므로 빠른 탐색에 사용할 수 있지만 색상은 현재 선택한 형식의 일부가 아님을 나타냅니다.

  메서드의 구현은 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 일반적으로 다음 단계를 수행합니다.

1. 소스 파일에 대한 현재 선언 목록을 가져옵니다.

     목록을 채우는 방법에는 여러 가지가 있습니다. 한 가지 방법은 모든 선언 목록을 반환하는 사용자 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 지정 구문 분석 이유로 메서드를 호출하는 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스 버전에 사용자 지정 메서드를 만드는 것입니다. 또 다른 방법은 사용자 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 지정 구문 분석 이유를 사용하여 메서드에서 직접 메서드를 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 호출하는 것입니다. 세 번째 방법은 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 클래스의 마지막 전체 구문 분석 작업에서 반환되는 <xref:Microsoft.VisualStudio.Package.LanguageService> 클래스의 선언을 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 캐시하고 메서드에서 해당 선언을 검색하는 것입니다.

2. 형식 목록을 채우거나 업데이트합니다.

     원본이 변경되었거나 현재 카를트 위치에 따라 형식의 텍스트 스타일 지정을 변경하도록 선택한 경우 형식 목록의 내용을 업데이트할 수 있습니다. 이 위치는 메서드에 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 전달됩니다.

3. 현재 카포트 위치에 따라 형식 목록에서 선택할 유형을 결정합니다.

     1단계에서 얻은 선언을 검색하여 현재 캐런트 위치를 둘러싸는 형식을 찾은 다음 해당 형식의 형식 목록을 검색하여 해당 인덱스를 형식 목록으로 확인할 수 있습니다.

4. 선택한 형식에 따라 멤버 목록을 채우거나 업데이트합니다.

     멤버 목록에는 현재 **멤버** 드롭다운에 표시되는 내용이 반영됩니다. 원본이 변경되었거나 선택한 형식의 멤버만 표시하고 선택한 형식이 변경된 경우 멤버 목록의 내용을 업데이트해야 할 수 있습니다. 원본 파일에 모든 멤버를 표시하도록 선택한 경우 현재 선택한 유형이 변경된 경우 목록의 각 멤버의 텍스트 스타일을 업데이트해야 합니다.

5. 현재 카포트 위치에 따라 멤버 목록에서 선택할 멤버를 결정합니다.

     1단계에서 얻은 선언을 검색하여 현재 캐런트 위치가 포함된 멤버를 검색한 다음 해당 멤버의 멤버 목록을 검색하여 구성원 목록에 대한 인덱스를 확인합니다.

6. 목록 `true` 또는 목록 중 하나에서 선택 사항이 변경된 경우 반환합니다.
