---
title: 레거시 언어 서비스의 코드 주석 달기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1405456ca9a6ba00926c82bcc7959ea36d26c2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160912"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>레거시 언어 서비스의 코드 주석 처리
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로그래밍 언어는 일반적으로 코드에 주석을 달고 주석을 추가할 수 있는 수단을 제공 합니다. 주석은 코드에 대 한 추가 정보를 제공 하는 텍스트 섹션 이지만 컴파일 또는 해석 중에는 무시 됩니다.  
  
 MPF (관리 되는 패키지 프레임 워크) 클래스는 선택한 텍스트를 주석으로 처리 하 고 주석 처리 수 있도록 지원 합니다.  
  
## <a name="comment-styles"></a>주석 스타일  
 설명에는 다음과 같은 두 가지 일반적인 스타일이 있습니다.  
  
1. 줄 주석-주석이 한 줄에 있습니다.  
  
2. 주석이 여러 줄을 포함할 수 있는 블록입니다.  
  
   일반적으로 줄 주석에는 시작 문자 (또는 문자)가 있으며, 블록 주석에는 시작과 끝 문자가 모두 있습니다. 예를 들어 c #에서 줄 주석은//로 시작 하 고, 블록 주석은/*로 시작 하 고/로 끝납니다 \* .  
  
   사용자가 고급 **편집**메뉴에서 명령 **주석 선택 항목** 을 선택 하면  ->  **Advanced** 명령은 <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> 클래스의 메서드로 라우팅됩니다 <xref:Microsoft.VisualStudio.Package.Source> . 사용자가 명령 **주석 제거**를 선택 하면 명령이 <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> 메서드로 라우팅됩니다.  
  
## <a name="supporting-code-comments"></a>지원 코드 주석  
 의 명명 된 매개 변수를 통해 언어 서비스에서 코드 주석을 지원할 수 있습니다 `EnableCommenting` <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . 이 속성은 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> 클래스의 속성을 설정 합니다 <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . 언어 servicce 기능을 설정 하는 방법에 대 한 자세한 내용은 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)을 참조 하세요.  
  
 또한 메서드를 재정의 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> 하 여 <xref:Microsoft.VisualStudio.Package.CommentInfo> 언어에 대 한 주석 문자를 포함 하는 구조체를 반환 해야 합니다. C # 스타일 줄 주석 문자는 기본값입니다.  
  
### <a name="example"></a>예  
 다음은 메서드의 구현 예제입니다 <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> .  
  
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
  
## <a name="see-also"></a>관련 항목  
 [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)   
 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)
