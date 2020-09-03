---
title: 레거시 언어 서비스의 탐색 모음에 대 한 지원 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80704859"
---
# <a name="support-for-the-navigation-bar-in-a-legacy-language-service"></a>레거시 언어 서비스의 탐색 모음 지원
편집기 뷰 위쪽의 탐색 모음에는 파일의 형식과 멤버가 표시 됩니다. 왼쪽 드롭다운에서 형식이 표시 되 고 오른쪽 드롭다운에서 멤버가 표시 됩니다. 사용자가 형식을 선택 하면 캐럿이 형식의 첫 번째 줄에 배치 됩니다. 사용자가 멤버를 선택 하면 캐럿이 멤버 정의에 배치 됩니다. 드롭다운 상자는 캐럿의 현재 위치를 반영 하도록 업데이트 됩니다.

## <a name="displaying-and-updating-the-navigation-bar"></a>탐색 모음 표시 및 업데이트
 탐색 모음을 지원 하려면 클래스에서 클래스를 파생 시키고 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 메서드를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> . 언어 서비스에 코드 창이 제공 되는 경우 기본 클래스는 <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.CodeWindowManager> <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindow> 코드 창을 나타내는 개체가 포함 된를 인스턴스화합니다. <xref:Microsoft.VisualStudio.Package.CodeWindowManager>그러면 개체에 새 개체가 제공 됩니다 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> . <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A>메서드는 개체를 가져옵니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> . 클래스의 인스턴스를 반환 하 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 는 경우는 <xref:Microsoft.VisualStudio.Package.CodeWindowManager> 메서드를 호출 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 하 여 내부 목록을 채우고 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 개체를 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 드롭다운 모음 관리자에 전달 합니다. 그러면 드롭다운 막대 관리자가 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.SetDropdownBar%2A> 개체의 메서드를 호출 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 하 여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsDropdownBar> 두 개의 드롭다운 막대가 포함 된 개체를 설정 합니다.

 캐럿이 이동 하면 <xref:Microsoft.VisualStudio.Package.LanguageService.OnIdle%2A> 메서드가 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> . 기본 <xref:Microsoft.VisualStudio.Package.LanguageService.OnCaretMoved%2A> 메서드는 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 클래스의 메서드를 호출 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> 하 여 탐색 모음의 상태를 업데이트 합니다. 개체 집합을 <xref:Microsoft.VisualStudio.Package.DropDownMember> 이 메서드에 전달 합니다. 각 개체는 드롭다운의 항목을 나타냅니다.

## <a name="the-contents-of-the-navigation-bar"></a>탐색 모음의 내용
 탐색 모음은 일반적으로 형식 목록과 멤버 목록을 포함 합니다. 형식 목록에는 현재 원본 파일에서 사용할 수 있는 모든 형식이 포함 되어 있습니다. 형식 이름에는 전체 네임 스페이스 정보가 포함 됩니다. 다음은 두 가지 형식의 c # 코드 예제입니다.

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

 형식 목록에 및이 표시 됩니다 `TestLanguagePackage.TestLanguageService` `TestLanguagePackage.TestLanguageService.Tokens` .

 멤버 목록에는 형식 목록에서 선택한 형식의 사용 가능한 멤버가 표시 됩니다. 위의 코드 예제를 사용 하 여 `TestLanguagePackage.TestLanguageService` 가 선택 된 형식이 면 멤버 목록에 전용 멤버 및이 포함 됩니다 `tokens` `serviceName` . 내부 구조는 `Token` 표시 되지 않습니다.

 멤버 목록을 구현 하 여 캐럿이 내부에 배치 될 때 멤버의 이름을 굵게 표시할 수 있습니다. 또한 멤버를 회색으로 표시 하 여 캐럿이 현재 위치 하는 범위에 포함 되지 않음을 나타낼 수 있습니다.

## <a name="enabling-support-for-the-navigation-bar"></a>탐색 모음에 대 한 지원 사용
 탐색 모음에 대 한 지원을 사용 하도록 설정 하려면 `ShowDropdownBarOption` 특성의 매개 변수를로 설정 해야 합니다 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true` . 이 매개 변수는 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 속성을 설정합니다. 탐색 모음을 지원 하려면 클래스의 메서드에서 개체를 구현 해야 합니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> <xref:Microsoft.VisualStudio.Package.LanguageService> .

 메서드 구현에서 <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDropDownHelper%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences.ShowNavigationBar%2A> 속성이로 설정 된 경우 `true` 개체를 반환할 수 있습니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars> . 개체를 반환 하지 않으면 탐색 모음이 표시 되지 않습니다.

 탐색 모음을 표시 하는 옵션은 사용자가 설정할 수 있으므로 편집기 뷰가 열려 있는 동안이 컨트롤을 다시 설정할 수 있습니다. 사용자는 변경 내용을 적용 하기 전에 편집기 창을 닫았다가 다시 열어야 합니다.

## <a name="implementing-support-for-the-navigation-bar"></a>탐색 모음에 대 한 지원 구현
 메서드는 각 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 드롭다운에 대해 하나씩 두 개의 목록을 사용 하 고 각 목록에서 현재 선택 영역을 나타내는 두 개의 값을 사용 합니다. 목록 및 선택 값을 업데이트할 수 있습니다 .이 경우에는 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 목록이 변경 되었음을 나타내는 메서드가를 반환 해야 합니다 `true` .

 유형 드롭다운에서 선택이 변경 되 면 새 유형을 반영 하도록 멤버 목록을 업데이트 해야 합니다. 멤버 목록에 표시 되는 내용은 다음 중 하나일 수 있습니다.

- 현재 형식에 대 한 멤버의 목록입니다.

- 소스 파일에서 사용할 수 있는 모든 멤버를 포함 하지만 현재 형식에 포함 되지 않은 모든 멤버는 회색으로 표시 된 텍스트로 표시 됩니다. 사용자는 계속 해 서 회색으로 표시 된 멤버를 선택할 수 있으므로 빠른 탐색에 사용할 수 있지만 색은 현재 선택 된 형식의 일부가 아님을 나타냅니다.

  메서드를 구현 하는 경우 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 일반적으로 다음 단계를 수행 합니다.

1. 소스 파일에 대 한 현재 선언 목록을 가져옵니다.

     여러 가지 방법으로 목록을 채울 수 있습니다. 한 가지 방법은 <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> 모든 선언 목록을 반환 하는 사용자 지정 구문 분석 이유를 사용 하 여 메서드를 호출 하는 클래스의 버전에 사용자 지정 메서드를 만드는 것입니다. 또 다른 방법은 <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> 사용자 지정 구문 분석 이유를 사용 하 여 메서드에서 직접 메서드를 호출 하는 것입니다. 세 번째 방법은 <xref:Microsoft.VisualStudio.Package.AuthoringScope> 클래스의 마지막 전체 구문 분석 작업에서 반환 된 클래스의 선언을 캐시 하 <xref:Microsoft.VisualStudio.Package.LanguageService> 고 메서드에서 검색 하는 것입니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> .

2. 형식 목록을 채우거 나 업데이트 합니다.

     소스가 변경 될 때 또는 현재 캐럿 위치에 따라 형식의 텍스트 스타일을 변경 하도록 선택한 경우에는 형식 목록의 내용을 업데이트할 수 있습니다. 이 위치는 메서드에 전달 됩니다 <xref:Microsoft.VisualStudio.Package.TypeAndMemberDropdownBars.OnSynchronizeDropdowns%2A> .

3. 현재 캐럿 위치를 기준으로 형식 목록에서 선택할 형식을 결정 합니다.

     1 단계에서 얻은 선언을 검색 하 여 현재 캐럿 위치를 포함 하는 형식을 찾은 다음 해당 형식에 대 한 형식 목록을 검색 하 여 형식 목록에 해당 인덱스를 확인할 수 있습니다.

4. 선택한 형식에 따라 멤버 목록을 채우거 나 업데이트 합니다.

     멤버 목록에는 **멤버** 드롭다운에서 현재 표시 된 항목이 반영 됩니다. 원본이 변경 되었거나 선택한 유형의 멤버만 표시 하 고 선택한 유형이 변경 된 경우 멤버 목록의 내용을 업데이트 해야 할 수 있습니다. 원본 파일의 모든 멤버를 표시 하도록 선택 하면 현재 선택한 형식이 변경 된 경우 목록에 있는 각 멤버의 텍스트 스타일을 업데이트 해야 합니다.

5. 현재 캐럿 위치에 따라 멤버 목록에서 선택할 멤버를 결정 합니다.

     1 단계에서 얻은 선언에서 현재 캐럿 위치를 포함 하는 멤버를 검색 한 다음 해당 멤버의 멤버 목록을 검색 하 여 해당 멤버 목록에 대 한 인덱스를 확인 합니다.

6. `true`목록 또는 목록에서 선택 항목이 변경 된 경우를 반환 합니다.
