---
title: '방법: XML 리터럴과 함께 XML 스키마 디자이너 사용'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: d11803e7-f81a-41a2-a145-ba494a45cc93
author: TerryGLee
ms.author: tglee
manager: jillfra
dev_langs:
- VB
ms.workload:
- multiple
ms.openlocfilehash: b4001e705cc69e07242abeeef5919573b264c5e8
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75592661"
---
# <a name="how-to-use-the-xml-schema-designer-with-xml-literals"></a>방법: XML 리터럴과 함께 XML 스키마 디자이너 사용

이 항목에서는 Visual Basic 프로젝트에서 XML 리터럴과 연결된 스키마를 보는 방법에 대해 설명합니다.

## <a name="create-a-new-visual-basic-project"></a>새 Visual Basic 프로젝트 만들기

1. Visual Studio를 엽니다.

2. **XMLLiterals**라는 새 Visual Basic **콘솔 앱** 프로젝트를 만듭니다.

     새 프로젝트에는 Visual Basic 소스 파일인 *Module1.vb*가 한 개 들어 있습니다.

## <a name="add-an-existing-xsd-file"></a>기존 XSD 파일 추가

1. 새 텍스트 파일을 메모장에서 엽니다. [구매 주문 스키마](../xml-tools/sample-xsd-file-simple-schema.md)에서 XML 스키마 샘플 코드를 복사하고 파일에 붙여넣습니다.

2. 일부 위치에 있는 파일을 이름 *PurchaseOrderSchema.xsd*로 저장합니다.

3. **솔루션 탐색기**에서 프로젝트의 이름을 마우스 오른쪽 단추로 클릭하고 **추가**를 선택한 다음, **기존 항목**을 선택합니다. **기존 항목 추가** 대화 상자가 나타납니다. *PurchaseOrderSchema.xsd* 파일을 찾아 선택한 다음, **추가**를 클릭합니다.

     이제 XMLLiterals 프로젝트에 두 파일(*Module1.vb* 및 *PurchaseOrderSchema.xsd*)이 있습니다.

## <a name="add-code"></a>코드 추가

프로젝트에 포함된 XSD 파일을 기반으로 XML 리터럴이 있는 Visual Basic 코드를 추가하려면 다음을 수행합니다.

1. *Module1.vb* 파일의 코드를 다음 코드로 바꿉니다.

   ```vb
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

   **XML 스키마 탐색기**는 XML 스키마 집합과 연결된 XML 리터럴이 있는 Visual Basic 파일과 나란히 표시됩니다.
