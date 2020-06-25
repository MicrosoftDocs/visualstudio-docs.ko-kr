---
title: 데이터 세트를 XML로 저장
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- XML [Visual Basic], datasets
- data [Visual Studio], saving as XML
- datasets [Visual Basic], saving as XML
- saving data
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: cc8854581903ab58a327ff18be7b3b7c0f860a3b
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85281736"
---
# <a name="save-a-dataset-as-xml"></a>데이터 세트를 XML로 저장

데이터 집합에서 사용 가능한 XML 메서드를 호출 하 여 데이터 집합의 XML 데이터에 액세스 합니다. XML 형식으로 데이터를 저장 하기 위해의 메서드나 메서드를 호출할 수 있습니다 <xref:System.Data.DataSet.GetXml%2A> <xref:System.Data.DataSet.WriteXml%2A> <xref:System.Data.DataSet> .

메서드를 호출 하면 <xref:System.Data.DataSet.GetXml%2A> XML 형식의 데이터 집합에 있는 모든 데이터 테이블의 데이터를 포함 하는 문자열이 반환 됩니다.

메서드를 호출 하면 <xref:System.Data.DataSet.WriteXml%2A> XML 형식 데이터를 지정한 파일로 보냅니다.

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-variable"></a>데이터 집합의 데이터를 변수에 XML로 저장 하려면

- <xref:System.Data.DataSet.GetXml%2A> 메서드는 <xref:System.String>를 반환합니다. 형식의 변수를 선언 <xref:System.String> 하 고 메서드의 결과를 할당 합니다 <xref:System.Data.DataSet.GetXml%2A> .

     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-csharp[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]

## <a name="to-save-the-data-in-a-dataset-as-xml-to-a-file"></a>데이터 집합의 데이터를 파일에 XML로 저장 하려면

- <xref:System.Data.DataSet.WriteXml%2A> 메서드에 몇 가지 오버 로드가 있습니다. 변수를 선언 하 고 파일을 저장할 올바른 경로를 할당 합니다. 다음 코드에서는 데이터를 파일에 저장 하는 방법을 보여 줍니다.

     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-csharp[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]

## <a name="see-also"></a>참조

- [데이터를 다시 데이터베이스에 저장](../data-tools/save-data-back-to-the-database.md)
