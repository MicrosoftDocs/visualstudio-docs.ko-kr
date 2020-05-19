---
title: XSLT 코드를 디버그하는 방법
ms.date: 03/05/2019
ms.topic: conceptual
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: f6f4a1ce60f04bcea6e21b52db9347a95292dab2
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592856"
---
# <a name="debugging-xslt"></a>XSLT 디버깅

Visual Studio에서 XSLT 코드를 디버그할 수 있습니다. XSLT 디버거에서는 중단점 설정, XSLT 실행 상태 보기 등을 지원합니다. XSLT 디버거를 사용하여 XSLT 스타일시트 또는 XSLT 애플리케이션을 디버그할 수 있습니다.

코드를 한 단계씩 실행, 프로시저 단위로 실행 또는 코드를 종료하여 한 번에 한 줄씩 코드를 실행할 수 있습니다. XSLT 디버거와 다른 Visual Studio 디버거에서 코드를 단계별로 실행하는 기능을 사용하는 명령은 같습니다.

디버깅을 시작하면 XSLT 디버거에서 입력 문서와 XSLT 출력을 창에 표시합니다.

> [!NOTE]
> XSLT 디버거는 Visual Studio의 Professional 및 Enterprise Edition에서만 사용할 수 있습니다.

## <a name="debug-from-the-xml-editor"></a>XML 편집기에서 디버그

편집기에서 스타일시트 또는 입력 XML 파일을 연 경우 디버거를 시작할 수 있습니다. 그러면 스타일시트를 디자인하면서 디버그할 수 있습니다.

1. Visual Studio에서 스타일시트 또는 XML 파일을 엽니다.

1. **XML** 메뉴에서 **XSLT 디버깅 시작**을 선택하거나 **Alt**+**F5**를 누릅니다.

## <a name="debug-from-an-app-that-uses-xslt"></a>XSLT를 사용하는 앱에서 디버그

애플리케이션을 디버그하는 동안 한 단계씩 XSLT를 실행할 수 있습니다. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> 호출에서 **F11** 키를 누르면 디버거에서 한 단계씩 XSLT 코드를 실행할 수 있습니다.

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> 클래스에서 XSLT를 한 단계씩 실행하는 것이 지원되지 않습니다. <xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 디버깅하는 동안 XSLT를 한 단계씩 실행하도록 지원하는 유일한 XSLT 프로세서입니다.

### <a name="to-start-debugging-an-xslt-application"></a>XSLT 애플리케이션 디버깅을 시작하려면

1. <xref:System.Xml.Xsl.XslCompiledTransform> 개체를 인스턴스화할 때 코드에서 `enableDebug` 매개 변수를 `true`로 설정합니다. 그러면 XSLT 프로세서에서 코드를 컴파일할 때 디버그 정보가 생성됩니다.

1. **F11** 키를 눌러 한 단계씩 XSLT 코드를 실행합니다.

   XSLT 스타일시트가 새 문서 창에 로드되고 XSLT 디버거가 시작됩니다.

   또는 스타일시트에 중단점을 추가하고 애플리케이션을 실행할 수 있습니다.

### <a name="example"></a>예제

다음은 C# XSLT 프로그램의 예로, XSLT 디버깅을 활성화하는 방법을 보여 줍니다.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet);

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>XSLT 프로파일러

[XSLT 프로파일러](../xml-tools/xslt-profiler.md)는 개발자가 자세한 XSLT 성능 보고서를 만들어 XSLT 코드의 성능 관련 문제를 측정 및 평가하고, 대상으로 지정할 수 있는 도구입니다. 자세한 내용은 [XSLT 프로파일러](../xml-tools/xslt-profiler.md)를 참조하세요.

## <a name="see-also"></a>참조

- [연습: XSLT 스타일시트 디버그](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [먼저 Visual Studio 디버거 살펴보기](../debugger/debugger-feature-tour.md)
- [디버깅 기본 사항: 중단점](../debugger/using-breakpoints.md)
