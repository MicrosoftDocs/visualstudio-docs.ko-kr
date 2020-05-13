---
title: 레거시 언어 서비스에서 코드 다시 포답 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- reformatting code, supporting in language services [managed package framework]
- language services [managed package framework], reformatting code
ms.assetid: 08bb3375-8fef-4f4e-9efa-0d7333bab0eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dd3e83c7299298b16a6fb3178b189479a80e1728
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705919"
---
# <a name="reformatting-code-in-a-legacy-language-service"></a>레거시 언어 서비스의 코드 서식 다시 지정

소스 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 코드에서 들여쓰기 및 공백 사용을 정규화하여 다시 포식할 수 있습니다. 여기에는 각 줄의 시작 부분에 공백이나 탭을 삽입 또는 제거하거나, 줄 사이에 새 선을 추가하거나, 공백을 탭이나 탭으로 대체하는 것이 포함될 수 있습니다.

> [!NOTE]
> 줄 바표지 문자를 삽입하거나 삭제하면 중단점 및 책갈피와 같은 마커에 영향을 줄 수 있지만 공백이나 탭을 추가하거나 제거해도 마커에는 영향을 주지 않습니다.

사용자는 **편집** 메뉴의 **고급** 메뉴에서 **형식 선택** 또는 **문서 형식** 지정을 선택하여 다시 포맷 작업을 시작할 수 있습니다. 코드 조각 이나 특정 문자를 삽입 하는 경우 다시 포식 작업을 트리거할 수도 있습니다. 예를 들어 C#에서 닫는 중괄호를 입력하면 일치하는 열린 중괄호와 가까운 중괄호 사이의 모든 것이 자동으로 적절한 수준으로 들여쓰기됩니다.

**형식 선택** 또는 **형식 문서** 명령을 언어 서비스에 <xref:Microsoft.VisualStudio.Package.ViewFilter> 보내면 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 클래스는 <xref:Microsoft.VisualStudio.Package.Source> 클래스의 메서드를 호출합니다. 서식 지정을 지원하려면 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 메서드를 재정의하고 고유한 서식 지정 코드를 제공해야 합니다.

## <a name="enabling-support-for-reformatting"></a>다시 포질화지원 지원

서식지정을 지원하려면 VSPackage를 `EnableFormatSelection` 등록할 때 의 매개 변수를 <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> `true` 설정해야 합니다. 그러면 <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableFormatSelection%2A> 속성이 `true`로 설정됩니다. 메서드는 <xref:Microsoft.VisualStudio.Package.ViewFilter.CanReformat%2A> 이 속성의 값을 반환합니다. true를 반환하면 <xref:Microsoft.VisualStudio.Package.ViewFilter> 클래스는 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A>을 호출합니다.

## <a name="implementing-reformatting"></a>다시 포질화 구현

다시 포식을 구현하려면 <xref:Microsoft.VisualStudio.Package.Source> 클래스에서 클래스를 파생하고 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 메서드를 재정의해야 합니다. 개체는 <xref:Microsoft.VisualStudio.TextManager.Interop.TextSpan> 포맷할 범위를 설명하고 <xref:Microsoft.VisualStudio.Package.EditArray> 개체는 범위에서 만든 편집을 보유합니다. 이 범위는 전체 문서가 될 수 있습니다. 그러나 범위에 여러 번 변경될 수 있기 때문에 모든 변경 내용은 단일 작업에서 되돌릴 수 있어야 합니다. 이렇게 하려면 <xref:Microsoft.VisualStudio.Package.CompoundAction> 개체의 모든 변경 내용을 래핑합니다(이 항목의 "CompoundAction 클래스 사용" 섹션 참조).

### <a name="example"></a>예제

다음 예제에서는 쉼표 뒤에 탭이 있거나 줄끝에 있는 경우가 아니면 선택 영역의 모든 쉼표 뒤에 단일 공백이 있는지 확인합니다. 줄의 마지막 쉼표 이후의 후행 공백이 삭제됩니다. 이 항목의 "CompoundAction 클래스 사용" 섹션을 참조하여 <xref:Microsoft.VisualStudio.Package.Source.ReformatSpan%2A> 메서드에서 이 메서드를 호출하는 방법을 확인합니다.

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

## <a name="using-the-compoundaction-class"></a>컴파운드액션 클래스 사용

코드 섹션에서 수행되는 모든 다시 포식은 단일 작업에서 되돌릴 수 있어야 합니다. 이 작업은 클래스를 <xref:Microsoft.VisualStudio.Package.CompoundAction> 사용하여 수행할 수 있습니다. 이 클래스는 텍스트 버퍼에 대한 편집 작업 집합을 단일 편집 작업으로 래핑합니다.

### <a name="example"></a>예제

다음은 <xref:Microsoft.VisualStudio.Package.CompoundAction> 클래스를 사용하는 방법의 예입니다. `DoFormatting` 메서드의 예는 이 항목의 "서식 지정 지원 구현" 절의 예제를 참조하십시오.

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

## <a name="see-also"></a>참조

- [레거시 언어 서비스 기능](legacy-language-service-features1.md)
