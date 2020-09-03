---
title: '방법: xml 리터럴과 함께 XML 스키마 디자이너 사용 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a9e82cf8387756cb4a4abe8b4c41d082485cdcdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656286"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>방법: XML 리터럴과 함께 XML 스키마 디자이너 사용
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에서는 Visual Basic 프로젝트에서 XML 리터럴과 연결된 스키마를 보는 방법에 대해 설명합니다.

### <a name="to-create-a-new-visual-basic-console-application-project"></a>새 Visual Basic 콘솔 애플리케이션 프로젝트를 만들려면

1. Visual Studio 2010을 시작합니다.

2. **파일** 메뉴에서 **새로 만들기**를 선택한 다음 **프로젝트**를 선택합니다. **새 프로젝트** 대화 상자가 나타납니다. **프로젝트 형식**에서 **다른 언어를** 선택 하 고 **Visual Basic**를 선택 합니다. **템플릿의**경우 콘솔 응용 프로그램을 선택 합니다. 그런 다음 `XMLLiterals` **이름** 필드에를 입력 하 고 **위치** 필드에 프로젝트 위치를 입력 합니다. **확인**을 클릭합니다.

     새 프로젝트가 만들어집니다. XMLLiterals 프로젝트에는 Visual Basic 소스 파일인 Module1.vb가 한 개 들어 있습니다.

### <a name="to-add-an-existing-xsd-file-to-the-project"></a>기존 XSD 파일을 프로젝트에 추가하려면

1. 새 텍스트 파일을 메모장에서 엽니다. [구매 주문 스키마](../xml-tools/sample-xsd-file-simple-schema.md) 에서 XML 스키마 샘플 코드를 복사 하 여 파일에 붙여넣습니다.

2. 일부 위치에 있는 파일을 이름 PurchaseOrderSchema.xsd로 저장합니다.

3. 솔루션 탐색기에서 프로젝트의 이름을 마우스 오른쪽 단추로 클릭 하 고 **추가**를 선택한 다음 **기존 항목**...을 선택 합니다. **기존 항목 추가** 대화 상자가 나타납니다. PurchaseOrderSchema.xsd 파일을 찾아 선택한 다음, **추가**를 클릭합니다.

     XMLLiterals 프로젝트에는 이제 두 파일인 Module1.vb와 PurchaseOrderSchema.xsd가 들어 있습니다.

### <a name="to-add-visual-basic-code-with-an-xml-literal-based-on-the-xsd-file-included-in-the-project"></a>프로젝트에 포함된 XSD 파일을 기반으로 XML 리터럴이 있는 Visual Basic 코드를 추가하려면

1. Module1.vb 파일의 코드를 다음 코드로 바꿉니다.

    ```
    Imports <xmlns:ns="http://tempuri.org/PurchaseOrderSchema.xsd">

    Module Module1
        Sub Main()

            Dim XMLLiteral = <ns:PurchaseOrder OrderDate="1900-01-01">
                                 <ns:ShipTo country="US">
                                     <ns:name>name1</ns:name>
                                     <ns:street>street1</ns:street>
                                     <ns:city>city1</ns:city>
                                     <ns:state>state1</ns:state>
                                     <ns:zip>1</ns:zip>
                                 </ns:ShipTo>
                                 <ns:BillTo country="US">
                                     <ns:name>name1</ns:name>
                                     <ns:street>street1</ns:street>
                                     <ns:city>city1</ns:city>
                                     <ns:state>state1</ns:state>
                                     <ns:zip>1</ns:zip>
                                 </ns:BillTo>
                             </ns:PurchaseOrder>

        End Sub
    End Module
    ```

2. XML 리터럴 또는 XML 네임스페이스 가져오기에서 XML 노드를 마우스 오른쪽 단추로 클릭하고 **스키마 탐색기에 표시**를 선택합니다.

     XML 스키마 탐색기는 XML 스키마 집합과 연결된 XML 리터럴이 있는 Visual Basic 파일과 나란히 표시됩니다.
