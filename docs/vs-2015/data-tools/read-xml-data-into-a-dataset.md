---
title: XML 데이터를 데이터 집합으로 읽기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c34fb87c02ff60d9b28c43130d6fbf3a12e70349
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652898"
---
# <a name="read-xml-data-into-a-dataset"></a>XML 데이터를 데이터 세트에 읽어오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET는 XML 데이터 작업을 위한 간단한 메서드를 제공 합니다. 이 연습에서는 XML 데이터를 데이터 집합에 로드 하는 Windows 응용 프로그램을 만듭니다. 그러면 데이터 집합이 컨트롤에 표시 됩니다 <xref:System.Windows.Forms.DataGridView> . 마지막으로 XML 파일의 내용을 기반으로 하는 XML 스키마가 텍스트 상자에 표시 됩니다.

 이 연습은 다음과 같은 5 가지 주요 단계로 구성 됩니다.

1. 새 프로젝트 만들기

2. 데이터 집합으로 읽을 XML 파일 만들기

3. 사용자 인터페이스 만들기

4. 데이터 집합 만들기, XML 파일 읽기 및 컨트롤에 표시 <xref:System.Windows.Forms.DataGridView>

5. 컨트롤의 XML 파일을 기반으로 XML 스키마를 표시 하는 코드 추가 <xref:System.Windows.Forms.TextBox>

> [!NOTE]
> 표시 되는 대화 상자와 메뉴 명령은 사용 중인 활성 설정 또는 버전에 따라 도움말에 설명 된 것과 다를 수 있습니다. 설정을 변경 하려면  **도구** 메뉴에서**설정 가져오기 및 내보내기**를 선택 합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

## <a name="create-a-new-project"></a>새 프로젝트 만들기
 이 단계에서는이 연습을 포함 하는 Visual Basic 또는 Visual c # 프로젝트를 만듭니다.

#### <a name="to-create-the-new-windows-project"></a>새 Windows 프로젝트를 만들려면

1. **파일** 메뉴에서 새 프로젝트를 만듭니다.

2. 프로젝트 이름을 `ReadingXML`로 지정합니다.

3. **Windows 응용 프로그램**을 선택 하 고 **확인**을 선택 합니다. 자세한 내용은 [클라이언트 응용 프로그램](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68)을 참조 하세요.

     **ReadingXML** 프로젝트가 만들어지고 **솔루션 탐색기**에 추가 됩니다.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>데이터 집합으로 읽어올 XML 파일 생성
 이 연습에서는 XML 데이터를 데이터 집합으로 읽는 방법을 중점적으로 설명 하므로 XML 파일의 내용이 제공 됩니다.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>데이터 집합으로 읽어올 XML 파일을 만들려면

1. **프로젝트** 메뉴에서**새 항목 추가**를 선택 합니다.

2. **XML 파일**을 선택 하 고 파일 이름을 `authors.xml` 지정한 다음 **추가**를 선택 합니다.

     XML 파일이 디자이너로 로드 되 고 편집할 준비가 됩니다.

3. XML 선언 아래에 다음 코드를 편집기에 붙여 넣습니다.

    ```xml
    <Authors_Table>
      <authors>
        <au_id>172-32-1176</au_id>
        <au_lname>White</au_lname>
        <au_fname>Johnson</au_fname>
        <phone>408 496-7223</phone>
        <address>10932 Bigge Rd.</address>
        <city>Menlo Park</city>
        <state>CA</state>
        <zip>94025</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>213-46-8915</au_id>
        <au_lname>Green</au_lname>
        <au_fname>Margie</au_fname>
        <phone>415 986-7020</phone>
        <address>309 63rd St. #411</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94618</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>238-95-7766</au_id>
        <au_lname>Carson</au_lname>
        <au_fname>Cheryl</au_fname>
        <phone>415 548-7723</phone>
        <address>589 Darwin Ln.</address>
        <city>Berkeley</city>
        <state>CA</state>
        <zip>94705</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>267-41-2394</au_id>
        <au_lname>Hunter</au_lname>
        <au_fname>Anne</au_fname>
        <phone>408 286-2428</phone>
        <address>22 Cleveland Av. #14</address>
        <city>San Jose</city>
        <state>CA</state>
        <zip>95128</zip>
        <contract>true</contract>
      </authors>
      <authors>
        <au_id>274-80-9391</au_id>
        <au_lname>Straight</au_lname>
        <au_fname>Dean</au_fname>
        <phone>415 834-2919</phone>
        <address>5420 College Av.</address>
        <city>Oakland</city>
        <state>CA</state>
        <zip>94609</zip>
        <contract>true</contract>
      </authors>
    </Authors_Table>
    ```

4. **파일** 메뉴에서**authors.xml저장 **을 선택 합니다.

## <a name="create-the-user-interface"></a>사용자 인터페이스 만들기
 이 응용 프로그램에 대 한 사용자 인터페이스는 다음과 같이 구성 됩니다.

- <xref:System.Windows.Forms.DataGridView>XML 파일의 내용을 데이터로 표시 하는 컨트롤입니다.

- <xref:System.Windows.Forms.TextBox>Xml 파일에 대 한 xml 스키마를 표시 하는 컨트롤입니다.

- 두 <xref:System.Windows.Forms.Button> 컨트롤.

  - 한 단추는 XML 파일을 데이터 집합으로 읽어 컨트롤에 표시 <xref:System.Windows.Forms.DataGridView> 합니다.

  - 두 번째 단추는 데이터 집합에서 스키마를 추출 하 고를 통해 <xref:System.IO.StringWriter> 컨트롤에 해당 스키마를 표시 <xref:System.Windows.Forms.TextBox> 합니다.

#### <a name="to-add-controls-to-the-form"></a>컨트롤을 폼에 추가하려면

1. `Form1`디자인 뷰에서를 엽니다.

2. **도구 상자**에서 다음 컨트롤을 폼으로 끌어옵니다.

    - 한 <xref:System.Windows.Forms.DataGridView> 컨트롤

    - 한 <xref:System.Windows.Forms.TextBox> 컨트롤

    - 두 <xref:System.Windows.Forms.Button> 컨트롤

3. 다음 속성을 설정합니다.

    |제어|속성|설정|
    |-------------|--------------|-------------|
    |`TextBox1`|**여러 줄**|`true`|
    ||**ScrollBars**|**세로**|
    |`Button1`|**이름**|`ReadXmlButton`|
    ||**Text**|`Read XML`|
    |`Button2`|**이름**|`ShowSchemaButton`|
    ||**Text**|`Show Schema`|

## <a name="create-the-dataset-thatreceives-the-xml-data"></a>XML 데이터를 thatreceives 하는 데이터 집합 만들기
 이 단계에서는 라는 새 데이터 집합을 만듭니다 `authors` . 데이터 집합에 대 한 자세한 내용은 [Visual Studio의 데이터 집합 도구](../data-tools/dataset-tools-in-visual-studio.md)를 참조 하세요.

#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>XML 데이터를 수신 하는 새 데이터 집합을 만들려면

1. **솔루션 탐색기**에서 **Form1**의 원본 파일을 선택한 다음 **솔루션 탐색기** 도구 모음에서 **디자이너 보기** 단추를 선택 합니다.

2. [도구 상자, 데이터 탭](../ide/reference/toolbox-data-tab.md)에서 **데이터 집합** 을 **Form1**로 끌어 옵니다.

3. **데이터 집합 추가** 대화 상자에서 **형식화 되지 않은 데이터 집합**을 선택 하 고 **확인**을 선택 합니다.

     **DataSet1** 가 구성 요소 트레이에 추가 됩니다.

4. **속성** 창에서의 **이름** 및 속성을 설정 합니다 <xref:System.Data.DataSet.DataSetName%2A> `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>XML 파일을 데이터 집합으로 읽도록 이벤트 처리기를 만듭니다.
 **Xml 읽기** 단추를 클릭 하면 xml 파일이 데이터 집합으로 읽혀집니다. 그런 다음 데이터 집합에 바인딩하는 컨트롤에 대 한 속성을 설정 <xref:System.Windows.Forms.DataGridView> 합니다.

#### <a name="to-add-code-to-the-readxmlbutton_click-event-handler"></a>ReadXmlButton_Click 이벤트 처리기에 코드를 추가 하려면

1. **솔루션 탐색기**에서 **Form1**을 선택 하 고 **솔루션 탐색기** 도구 모음에서 **디자이너 보기** 단추를 선택 합니다.

2. **XML 읽기** 단추를 선택 합니다.

     이벤트 처리기에서 **코드 편집기** 가 열립니다 `ReadXmlButton_Click` .

3. 이벤트 처리기에 다음 코드를 입력 합니다 `ReadXmlButton_Click` .

     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]

4. `ReadXMLButton_Click`이벤트 처리기 코드에서 `filepath =` 항목을 올바른 경로로 변경 합니다.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>텍스트 상자에 스키마를 표시 하는 이벤트 처리기를 만듭니다.
 **스키마 표시** 단추를 클릭 하면 <xref:System.IO.StringWriter> 스키마를 사용 하 여 채워진 개체가 생성 되 고 컨트롤에 표시 됩니다 <xref:System.Windows.Forms.TextBox> .

#### <a name="to-add-code-to-the-showschemabutton_click-event-handler"></a>ShowSchemaButton_Click 이벤트 처리기에 코드를 추가 하려면

1. **솔루션 탐색기**에서 **Form1**을 선택 하 고 **디자이너 보기** 단추를 선택 합니다.

2. **스키마 표시** 단추를 선택 합니다.

     이벤트 처리기에서 **코드 편집기** 가 열립니다 `ShowSchemaButton_Click` .

3. 이벤트 처리기에 다음 코드를 입력 합니다 `ShowSchemaButton_Click` .

     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]

## <a name="test-the-form"></a>양식 테스트

이제 폼을 테스트 하 여 예상 대로 동작 하는지 확인할 수 있습니다.

1. **F5 키** 를 선택 하 여 응용 프로그램을 실행 합니다.

2. **XML 읽기** 단추를 선택 합니다.

     DataGridView는 XML 파일의 내용을 표시 합니다.

3. **스키마 표시** 단추를 선택 합니다.

     텍스트 상자에 XML 파일에 대 한 XML 스키마가 표시 됩니다.

## <a name="next-steps"></a>다음 단계

이 연습에서는 xml 파일을 데이터 집합으로 읽는 방법 뿐만 아니라 XML 파일의 내용에 따라 스키마를 만들 수 있는 기본 사항을 배웁니다. 다음 작업을 수행할 수 있는 몇 가지 작업은 다음과 같습니다.

- 데이터 집합의 데이터를 편집 하 고 XML로 다시 작성 합니다. 자세한 내용은 <xref:System.Data.DataSet.WriteXml%2A>를 참조하세요.

- 데이터 집합의 데이터를 편집 하 고 데이터베이스에 기록 합니다.

## <a name="see-also"></a>관련 항목
 [데이터 연습](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) [visual studio에서 데이터에 액세스](../data-tools/accessing-data-in-visual-studio.md) [Visual studio에서 데이터 XML 도구](../xml-tools/xml-tools-in-visual-studio.md) [를 수신 하도록 응용 프로그램 준비](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)
