---
title: 레거시 언어 서비스의 코드 다시 포맷 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: eb0dac5e1282d544df9c04bf4c12303fb391739d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841926"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>레거시 언어 서비스의 코드 서식 다시 지정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

에서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 들여쓰기 및 공백 사용을 정규화 하 여 소스 코드의 서식을 다시 지정할 수 있습니다. 여기에는 각 줄의 시작 부분에 공백이 나 탭 삽입 또는 제거, 줄 사이에 새 줄 추가 또는 공백이 있는 탭 이나 탭으로 공백 바꾸기가 포함 될 수 있습니다.  
  
> [!NOTE]
> **참고** 줄 바꿈 문자를 삽입 하거나 삭제 하면 중단점과 책갈피와 같은 표식에 영향을 줄 수 있지만 공백 또는 탭을 추가 하거나 제거 해도 표식에는 영향을 주지 않습니다.  
  
 사용자는 **편집** 메뉴의 **고급** 메뉴에서 **선택 영역 서식** 또는 **문서 서식** 을 선택 하 여 다시 포맷 작업을 시작할 수 있습니다. 코드 조각 또는 특정 문자를 삽입 하는 경우에도 다시 포맷 작업을 트리거할 수 있습니다. 예를 들어 c #에서 닫는 중괄호를 입력 하는 경우 일치 하는 여는 중괄호와 닫는 중괄호 사이의 모든 항목은 적절 한 수준으로 자동으로 들여쓰기 됩니다.  
  
 에서 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **형식 선택** 또는 **문서 서식 지정** 명령을 언어 서비스로 보내면 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스는 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 클래스의 메서드를 호출 합니다 <xref:Microsoft.VisualStudio.Package.Source> . 형식을 지원 하려면 메서드를 재정의 하 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 고 사용자 고유의 서식 지정 코드를 제공 해야 합니다.  
  
## <a name="enabling-support-for-reformatting"></a>다시 포맷 지원 사용  
 서식 지정을 지원 하려면 `EnableFormatSelection` VSPackage을 등록할 때의 매개 변수를 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> 로 설정 해야 합니다 `true` . 이렇게 하면 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> 속성이로 설정 `true` 됩니다. <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A>메서드는이 속성의 값을 반환 합니다. True를 반환 하는 경우 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스는를 호출 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 합니다.  
  
## <a name="implementing-reformatting"></a>다시 포맷 구현  
 다시 포맷을 구현 하려면 클래스에서 클래스를 파생 시키고 <xref:Microsoft.VisualStudio.Package.Source> 메서드를 재정의 해야 합니다 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> . <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan>개체는 형식을 지정 하는 범위를 설명 하 고 <xref:Microsoft.VisualStudio.Package.EditArray> 개체는 범위에 대해 적용 된 편집 내용을 보유 합니다. 이 범위는 전체 문서 일 수 있습니다. 그러나 범위에 대 한 변경 내용이 여러 개 있을 가능성이 있으므로 모든 변경 내용을 단일 작업으로 되돌릴 수 있어야 합니다. 이렇게 하려면 개체의 모든 변경 내용을 래핑합니다 <xref:Microsoft.VisualStudio.Package.CompoundAction> .이 항목의 "CompoundAction 클래스 사용" 섹션을 참조 하십시오.  
  
### <a name="example"></a>예제  
 다음 예에서는 쉼표 뒤에 탭이 오거나 줄의 끝에 있는 경우를 제외 하 고 선택 영역에 있는 각 쉼표 뒤에 공백이 하나씩 있는지 확인 합니다. 줄에서 마지막 쉼표 뒤의 후행 공백이 삭제 됩니다. 메서드에서이 메서드를 호출 하는 방법에 대 한 자세한 내용은이 항목의 "CompoundAction 클래스 사용" 섹션을 참조 하세요 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> .  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        private void DoFormatting(EditArray mgr, TextSpan span)  
        {  
            // Make sure there is one space after every comma unless followed  
            // by a tab or comma is at end of line.  
            IVsTextLines pBuffer = GetTextLines();  
            if (pBuffer != null)  
            {  
                int    startIndex = span.iStartIndex;  
                int    endIndex   = 0;  
                string line       = "";  
                // Loop over all lines in span  
                for (int i = span.iStartLine; i <= span.iEndLine; i++)  
                {  
                    if (i < span.iEndLine)  
                    {  
                        pBuffer.GetLengthOfLine(i, out endIndex);  
                    }  
                    else  
                    {  
                        endIndex = span.iEndIndex;  
                    }  
                    pBuffer.GetLineText(i, startIndex, i, endIndex, out line);  
  
                    if (line.Length > 0)  
                    {  
                        int index = 0;  
                        // Loop over all commas in line  
                        while ((index = line.IndexOf(',', index)) != -1)  
                        {  
                            int spaceIndex = index + 1;  
                            // Determine how many spaces after comma  
                            while (spaceIndex < line.Length && line[spaceIndex] == ' ')  
                            {  
                                ++spaceIndex;  
                            }  
  
                            int      spaceCount      = spaceIndex - (index + 1);  
                            string   replacementText = " ";  
                            bool     fDoEdit         = true;  
                            TextSpan editTextSpan    = new TextSpan();  
  
                            editTextSpan.iStartLine  = i;  
                            editTextSpan.iEndLine    = i;  
                            editTextSpan.iStartIndex = index + 1;  
  
                            if (spaceIndex == line.Length)  
                            {  
                                if (spaceCount > 0)  
                                {  
                                    // Delete spaces after a comma at end of line  
                                    editTextSpan.iEndIndex = spaceIndex;  
                                    replacementText = "";  
                                }  
                                else  
                                {  
                                    // Otherwise, do not add spaces if comma is  
                                    // at end of line.  
                                    fDoEdit = false;  
                                }  
                            }  
                            else if (spaceCount == 0)  
                            {  
                                if (spaceIndex < line.Length && line[spaceIndex] == '\t')  
                                {  
                                    // Do not insert space if a tab follows  
                                    // a comma.  
                                    fDoEdit = false;  
                                }  
                                else  
                                {  
                                    // No space after comma so add a space.  
                                    editTextSpan.iEndIndex = index + 1;  
                                }  
                            }  
                            else if (spaceCount > 1)  
                            {  
                                // More than one space after comma, replace  
                                // with a single space.  
                                editTextSpan.iEndIndex = spaceIndex;  
                            }  
                            else  
                            {  
                                // Single space after a comma and not at end  
                                // of the line, leave it alone.  
                                fDoEdit = false;  
                            }  
                            if (fDoEdit)  
                            {  
                                // Add edit operation  
                                mgr.Add(new EditSpan(editTextSpan, replacementText));  
                            }  
                            index = spaceIndex;  
                        }  
                    }  
                    startIndex = 0; // All subsequent lines start at 0  
                }  
                // Apply all edits  
                mgr.ApplyEdits();  
            }  
        }  
    }  
}  
```  
  
## <a name="using-the-compoundaction-class"></a>CompoundAction 클래스 사용  
 코드 섹션에서 수행 되는 모든 서식 지정은 단일 작업으로 되돌릴 수 있어야 합니다. 클래스를 사용 하 여이를 수행할 수 있습니다 <xref:Microsoft.VisualStudio.Package.CompoundAction> . 이 클래스는 텍스트 버퍼에 대 한 편집 작업 집합을 단일 편집 작업으로 래핑합니다.  
  
### <a name="example"></a>예제  
 클래스를 사용 하는 방법에 대 한 예제는 다음과 같습니다 <xref:Microsoft.VisualStudio.Package.CompoundAction> . 메서드의 예제는이 항목의 "서식 지정 지원 구현" 섹션의 예제를 참조 하세요 `DoFormatting` .  
  
```csharp  
using Microsoft.VisualStudio.Package;  
using Microsoft VisualStudio.TextManager.Interop;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override void ReformatSpan(EditArray mgr, TextSpan span)  
        {  
            string description = "Reformat code";  
            CompoundAction ca = new CompoundAction(this, description);  
            using (ca)  
            {  
                ca.FlushEditActions();      // Flush any pending edits  
                DoFormatting(mgr, span);    // Format the span  
            }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>참고 항목  
 [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)
