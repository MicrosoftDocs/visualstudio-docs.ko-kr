---
title: 레거시 언어 서비스에서 코드 주석 달기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709434"
---
# <a name="comment-code-in-a-legacy-language-service"></a>레거시 언어 서비스의 주석 코드
프로그래밍 언어는 일반적으로 코드에 주석을 달거나 주석을 달 수 있는 수단을 제공합니다. 주석은 코드에 대한 추가 정보를 제공하지만 컴파일 또는 해석 중에 무시되는 텍스트 섹션입니다.

 MPF(관리되는 패키지 프레임워크) 클래스는 선택한 텍스트에 주석 을 달고 주석을 달지 않는 지원을 제공합니다.

## <a name="comment-styles"></a>주석 스타일
주석에는 두 가지 일반적인 스타일이 있습니다.

1. 주석이 한 줄에 있는 줄 주석입니다.

2. 주석에 여러 줄이 포함될 수 있는 주석을 차단합니다.

Line 주석에는 일반적으로 시작 문자(또는 문자)가 있는 반면 블록 주석에는 시작 문자와 끝 문자가 모두 있습니다. 예를 들어 C#에서 줄 주석은 `//`에서 시작하고 블록 `/*` 주석은 `*/`에서 시작하고 로 끝납니다.

사용자가**고급** **편집** > 메뉴에서 **주석 선택** 명령을 선택하면 명령이 <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> <xref:Microsoft.VisualStudio.Package.Source> 클래스의 메서드로 라우팅됩니다. 사용자가 **주석 해제 선택**명령을 선택하면 명령이 <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> 메서드로 라우팅됩니다.

## <a name="support-code-comments"></a>지원 코드 주석
 의 명명된 매개 변수를 통해 언어 `EnableCommenting` 서비스 지원 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 코드 주석을 가질 수 있습니다. 이렇게 하면 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> 클래스의 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> 속성이 설정됩니다. 언어 서비스 기능 설정에 대한 자세한 내용은 [레거시 언어 서비스 등록을](../../extensibility/internals/registering-a-legacy-language-service1.md)참조하십시오.

 또한 해당 언어에 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> 대한 주석 <xref:Microsoft.VisualStudio.Package.CommentInfo> 문자가 있는 구조를 반환하는 메서드를 재정의해야 합니다. C#스타일 선 주석 문자가 기본값입니다.

### <a name="example"></a>예제
 메서드의 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> 예제 구현은 다음과 같습니다.

```csharp
using Microsoft.VisualStudio.Package;

namespace MyLanguagePackage
{
    class MySource : Source
    {
        public override CommentInfo GetCommentFormat() {
            CommentInfo info = new CommentInfo();
            info.LineStart       = "//";
            info.BlockStart      = "/*";
            info.BlockEnd        = "*/";
            info.UseLineComments = true;
            return info;
        }
    }
}
```

## <a name="see-also"></a>참조
- [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
- [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
