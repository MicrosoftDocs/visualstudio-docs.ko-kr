---
title: Windows Forms 응용 프로그램에서 조회 테이블 만들기 | Microsoft Docs
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
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3979d08757445e9df5fc159fe7642b04bf74b995
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72630931"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Windows Forms 애플리케이션에서 조회 테이블 만들기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

용어 *조회 표에서* 는 두 개의 관련 된 데이터 테이블에 바인딩된 컨트롤을 설명 합니다. 이러한 조회 컨트롤은 두 번째 테이블에서 선택한 값에 따라 첫 번째 테이블의 데이터를 표시 합니다.

 부모 테이블의 주 노드 ( [데이터 소스 창](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)에서)를 연결 된 자식 테이블의 열에 이미 바인딩되어 있는 폼의 컨트롤로 끌어 조회 테이블을 만들 수 있습니다.

 예를 들어 sales 데이터베이스의 테이블을 생각해 보겠습니다 `Orders` . 테이블의 각 레코드에 `Orders` 는 주문에 배치 된 고객을 나타내는가 포함 됩니다 `CustomerID` . 는 `CustomerID` 테이블의 고객 레코드를 가리키는 외래 키입니다 `Customers` . 이 시나리오에서는 `Orders` **데이터 소스** 창에서 테이블을 확장 하 고 주 노드를 **자세히**로 설정 합니다. 그런 다음 `CustomerID` <xref:System.Windows.Forms.ComboBox> (또는 조회 바인딩을 지 원하는 다른 컨트롤)를 사용 하도록 열을 설정 하 고 노드를 `Orders` 폼으로 끕니다. 마지막으로, `Customers` 관련 열 (이 경우에는 <xref:System.Windows.Forms.ComboBox> 열에 바인딩된)에 바인딩된 컨트롤로 노드를 끌어 옵니다 `CustomerID` .

## <a name="to-databind-a-lookup-control"></a>조회 컨트롤을 바인딩하려면

1. **데이터 원본** 창을 엽니다.

    > [!NOTE]
    > 조회 테이블을 사용 하려면 **데이터 소스** 창에서 두 개의 관련 테이블이 나 개체를 사용할 수 있어야 합니다.

2. 부모 테이블 및 모든 열과 관련 자식 테이블 및 모든 열을 볼 수 있을 때까지 **데이터 소스** 창에서 노드를 확장 합니다.

    > [!NOTE]
    > 자식 테이블 노드는 부모 테이블에서 확장 가능한 자식 노드로 표시 되는 노드입니다.

3. 자식 테이블의 노드에 있는 컨트롤 목록에서 **세부 정보** 를 선택 하 여 자식 테이블의 놓기 형식을 **자세히** 로 변경 합니다. 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

4. 두 테이블 ( `CustomerID` 이전 예제의 노드)을 연결 하는 노드를 찾습니다. <xref:System.Windows.Forms.ComboBox> 컨트롤 목록에서 **ComboBox** 를 선택 하 여 놓기 형식을로 변경 합니다.

5. 주 자식 테이블 노드를 **데이터 소스** 창에서 폼으로 끌어 옵니다.

     데이터 바인딩된 컨트롤 (설명 레이블 포함)과 도구 스트립 ( <xref:System.Windows.Forms.BindingNavigator> )이 폼에 나타납니다. [데이터 집합](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter <xref:System.Windows.Forms.BindingSource> 및가 <xref:System.Windows.Forms.BindingNavigator> 구성 요소 트레이에 나타납니다.

6. 이제 **데이터 소스** 창에서 조회 컨트롤 ()로 직접 주 부모 테이블 노드를 끌어 옵니다 <xref:System.Windows.Forms.ComboBox> .

     이제 조회 바인딩이 설정 됩니다. 컨트롤에 설정 된 특정 속성은 아래 표를 참조 하세요.

    |속성|설정 설명|
    |--------------|----------------------------|
    |**DataSource**|Visual Studio는 사용자가 컨트롤로 끌어 온 테이블에 대해 작성된 <xref:System.Windows.Forms.BindingSource>로 이 속성을 설정합니다. 컨트롤을 만들 때 작성된 <xref:System.Windows.Forms.BindingSource>가 아닙니다.<br /><br /> 조정 해야 하는 경우 <xref:System.Windows.Forms.BindingSource> 표시 하려는 열이 포함 된 테이블의로 설정 합니다.|
    |**DisplayMember**|Visual Studio는 컨트롤로 끄는 테이블에 대해 문자열 데이터 형식을 포함하는 기본 키 다음의 첫 번째 열로 이 속성을 설정합니다.<br /><br /> 조정 해야 하는 경우 표시 하려는 열 이름으로 설정 합니다.|
    |**ValueMember**|Visual Studio는 이 속성을 기본 키에 포함되는 첫 번째 열로 설정하거나 키가 정의되어 있지 않으면 테이블의 첫 번째 열로 설정합니다.<br /><br /> 조정 해야 하는 경우 표시 하려는 열이 포함 된 테이블의 기본 키로 설정 합니다.|
    |**SelectedValue**|Visual Studio는이 속성을 **데이터 소스** 창에서 삭제 된 원래 열로 설정 합니다.<br /><br /> 조정 해야 하는 경우 관련 테이블의 외래 키 열로 설정 합니다.|

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 데이터에 Windows Forms 컨트롤 바인딩](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
