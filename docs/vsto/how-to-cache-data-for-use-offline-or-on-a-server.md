---
title: '방법: 오프 라인 이나 서버에서 사용할 데이터 캐시'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: ce295e299e4accb2d79655675f6264a1497b8d69
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85546187"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>방법: 오프 라인 이나 서버에서 사용할 데이터 캐시
  문서에서 캐시 되도록 데이터 항목을 표시 하 여 오프 라인에서 사용할 수 있게 할 수 있습니다. 또한 문서를 서버에 저장할 때 문서에 있는 데이터를 다른 코드에서 조작할 수 있습니다.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 데이터 항목이 코드에서 선언 될 때 데이터 항목이 캐시 되도록 표시할 수 있으며,를 사용 하는 경우 <xref:System.Data.DataSet> **속성** 창에서 속성을 설정 하 여 표시할 수 있습니다. 또는가 아닌 데이터 항목을 캐시 하는 경우 <xref:System.Data.DataSet> <xref:System.Data.DataTable> 문서에 캐시 되는 조건을 충족 하는지 확인 합니다. 자세한 내용은 [데이터 캐시](../vsto/caching-data.md)를 참조 하세요.

> [!NOTE]
> **CacheInDocument** 속성이 **True**로 설정 된 **데이터 소스** 창 또는 **도구 상자** 에서 끌고 있는 데이터 집합을 포함 하 여 **, 캐시 된 및** **WithEvents** 로 표시 된 Visual Basic를 사용 하 여 만든 데이터 집합은 캐시에서 이름 앞에 밑줄을 붙입니다. 예를 들어, 데이터 집합을 만들고 이름을 **Customers**로 <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> 지정할 경우 이름이 캐시에 **_Customers** 됩니다. <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>를 사용 하 여이 캐시 된 항목에 액세스 하는 경우 **고객**대신 **_Customers** 를 지정 해야 합니다.

### <a name="to-cache-data-in-the-document-using-code"></a>코드를 사용 하 여 문서의 데이터를 캐시 하려면

1. 데이터 항목에 대 한 public 필드 또는 속성을 프로젝트의 호스트 항목 클래스 (예: `ThisDocumen` Word 프로젝트의 t 클래스 또는 Excel 프로젝트의 클래스)의 멤버로 선언 합니다 `ThisWorkbook` .

2. 특성을 <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> 멤버에 적용 하 여 데이터 항목이 문서의 데이터 캐시에 저장 되도록 표시 합니다. 다음 예제에서는이 특성을의 필드 선언에 적용 합니다 <xref:System.Data.DataSet> .

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. 데이터 항목의 인스턴스를 만드는 코드를 추가 하 고 해당 하는 경우 데이터베이스에서 로드 합니다.

     데이터 항목은 처음 생성 될 때만 로드 됩니다. 이후에 캐시는 문서와 함께 유지 되며 다른 코드를 작성 하 여 업데이트 해야 합니다.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>속성 창를 사용 하 여 문서에서 데이터 집합을 캐시 하려면

1. 예를 들어 **데이터** 소스 창을 사용 하 여 프로젝트에 데이터 소스를 추가 하는 등 Visual Studio 디자이너의 도구를 사용 하 여 프로젝트에 데이터 집합을 추가 합니다.

2. 아직 없는 경우 데이터 집합의 인스턴스를 만들고 디자이너에서 인스턴스를 선택 합니다.

3. **속성** 창에서 **CacheInDocument** 속성을 **True**로 설정 합니다.

     자세한 내용은 [Office 프로젝트의 속성](../vsto/properties-in-office-projects.md)을 참조 하세요.

4. **속성** 창에서 **Modifiers** 속성을 **Public** 으로 설정 합니다 (기본적으로 **내부**).

## <a name="see-also"></a>참고 항목
- [데이터 캐시](../vsto/caching-data.md)
- [방법: Office 문서에서 프로그래밍 방식으로 데이터 소스 캐시](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [방법: 암호로 보호 된 문서의 데이터 캐시](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [서버에 있는 문서의 데이터 액세스](../vsto/accessing-data-in-documents-on-the-server.md)
- [데이터 저장](../data-tools/save-data-back-to-the-database.md)
