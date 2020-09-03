---
title: '방법: XSLT 디버깅 시작 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 09471b9e62b758e4e02e054494ed108532bbd301
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656324"
---
# <a name="how-to-start-debugging-xslt"></a>방법: XSLT 디버깅 시작
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XSLT 디버거를 사용하여 XSLT 스타일시트 또는 XSLT 애플리케이션을 디버깅할 수 있습니다. 디버깅할 때 코드를 한 단계씩 실행, 프로시저 단위로 실행 또는 코드를 종료하여 한 번에 한 줄씩 코드를 실행할 수 있습니다. XSLT 디버거와 다른 Visual Studio 디버거에서 코드를 단계별로 실행하는 기능을 사용하는 명령은 같습니다. 디버깅을 시작하면 XSLT 디버거에서 입력 문서와 XSLT 출력을 창에 표시합니다.

## <a name="xml-editor"></a>XML 편집기
 XML 편집기에서 디버거를 시작할 수 있습니다. 그러면 스타일시트를 디자인하면서 디버깅할 수 있습니다.

#### <a name="to-start-debugging-from-a-style-sheet"></a>스타일시트에서 디버깅을 시작하려면

1. XML 편집기에서 스타일시트를 엽니다.

2. **XML** 메뉴에서 **XSL 디버그** 를 선택 합니다.

#### <a name="to-start-debugging-from-an-xml-input-document"></a>XML 입력 문서에서 디버깅을 시작하려면

1. XML 편집기에서 XML 문서를 엽니다.

2. **XML** 메뉴에서 **XSL 디버그** 를 선택 합니다.

## <a name="xslt-from-other-languages"></a>다른 언어의 XSLT
 애플리케이션을 디버깅하는 동안 XSLT를 한 단계씩 실행할 수도 있습니다. <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> 호출에서 F11 키를 누르면 디버거에서 XSLT 코드를 한 단계씩 실행할 수 있습니다.

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> 클래스에서 XSLT를 한 단계씩 실행하는 것이 지원되지 않습니다. <xref:System.Xml.Xsl.XslCompiledTransform> 클래스는 디버깅하는 동안 XSLT를 한 단계씩 실행하도록 지원하는 유일한 XSLT 프로세서입니다.

#### <a name="to-start-debugging-an-xslt-application"></a>XSLT 애플리케이션 디버깅을 시작하려면

1. <xref:System.Xml.Xsl.XslCompiledTransform> 개체를 인스턴스화할 때 코드에서 `enableDebug` 매개 변수를 `true`로 설정합니다.

     그러면 XSLT 프로세서에서 코드를 컴파일할 때 디버그 정보가 생성됩니다.

2. F11 키를 눌러 XSLT 코드를 한 단계씩 실행합니다.

     XSLT 스타일시트가 새 문서 창에 로드되고 XSLT 디버거가 시작됩니다.

     또는 스타일시트에 중단점을 추가하고 애플리케이션을 실행할 수 있습니다.

### <a name="example"></a>예제
 다음은 C# XSLT 프로그램의 예로, XSLT 디버깅을 활성화하는 방법을 보여 줍니다.

```
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="see-also"></a>관련 항목
 [연습: XSLT 스타일 시트](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md) [코드 단계별 실행 개요](https://msdn.microsoft.com/8791dac9-64d1-4bb9-b59e-8d59af1833f9)
