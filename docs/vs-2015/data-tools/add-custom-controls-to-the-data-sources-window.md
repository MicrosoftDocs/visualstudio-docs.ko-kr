---
title: 데이터 소스 창에 사용자 지정 컨트롤 추가 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
f1_keywords:
- vs.datasource.howtoaddcustomcontrol
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Data Sources Window, adding controls
- controls [Visual Studio], adding to Data Sources Window
- DefaultBindingPropertyAttribute class, using
- LookupBindingPropertiesAttribute class, using
- ComplexBindingPropertiesAttribute class, using
- Data Sources Window, selecting controls
ms.assetid: 8c43e7d2-ba94-4d9b-96de-3aa971955afd
caps.latest.revision: 45
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 402e62602d99492730d3094965e76964cd5f8218
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673090"
---
# <a name="add-custom-controls-to-the-data-sources-window"></a>데이터 소스 창에 사용자 지정 컨트롤 추가
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

데이터 **소스** 창에서 디자인 화면으로 항목을 끌어 데이터 바인딩된 컨트롤을 만들 때 사용자가 만드는 컨트롤의 형식을 선택할 수 있습니다. 창의 각 항목에는 선택할 수 있는 컨트롤을 표시 하는 드롭다운 목록이 있습니다. 각 항목과 연결 된 컨트롤 집합은 항목의 데이터 형식에 따라 결정 됩니다. 만들려는 컨트롤이 목록에 표시 되지 않는 경우이 항목의 지침에 따라 컨트롤을 목록에 추가할 수 있습니다.

 데이터 **소스** 창에서 항목에 대해 만들 데이터 바인딩된 컨트롤을 선택 하는 방법에 대 한 자세한 내용은 [데이터 소스 창에서 끌어올 때 만들 컨트롤 설정](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)을 참조 하세요.

> [!NOTE]
> 표시되는 대화 상자와 메뉴 명령은 실제 설정이나 버전에 따라 도움말에서 설명하는 것과 다를 수 있습니다. 설정을 변경 하려면 **도구** 메뉴에서 **설정 가져오기 및 내보내기**를 선택 합니다. 자세한 내용은 [Visual Studio에서 개발 설정 사용자 지정](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3)을 참조 하세요.

## <a name="customize-the-list-of-bindable-controls-for-a-data-type"></a><a name="customizinglist"></a> 데이터 형식에 대 한 바인딩 가능한 컨트롤 목록 사용자 지정
 **데이터 소스** 창에서 특정 데이터 형식의 항목에 대해 사용 가능한 컨트롤 목록에서 컨트롤을 추가 하거나 제거 하려면 다음 단계를 수행 합니다.

#### <a name="to-select-the-controls-to-be-listed-for-a-data-type"></a>데이터 형식에 대해 나열할 컨트롤을 선택 하려면

1. WPF 디자이너나 Windows Forms 디자이너이 열려 있는지 확인 합니다.

2. **데이터 소스** 창에서 창에 추가한 데이터 원본의 일부인 항목을 클릭 한 다음 해당 항목에 대 한 드롭다운 메뉴를 클릭 합니다.

3. 드롭다운 메뉴에서 **사용자 지정**을 클릭 합니다. 다음 대화 상자 중 하나가 열립니다.

    - Windows Forms 디자이너 열려 있으면 **옵션** 대화 상자의 **데이터 UI 사용자 지정** 페이지가 열립니다.

    - WPF Designer가 열려 있으면 **컨트롤 바인딩 사용자 지정** 대화 상자가 열립니다.

4. 대화 상자의 **데이터 형식** 드롭다운 목록에서 데이터 형식을 선택 합니다.

    - 테이블 또는 개체의 컨트롤 목록을 사용자 지정 하려면 **[목록]** 을 선택 합니다.

    - 테이블의 열 또는 개체의 속성에 대 한 컨트롤 목록을 사용자 지정 하려면 기본 데이터 저장소에서 열 또는 속성의 데이터 형식을 선택 합니다.

    - 사용자 정의 셰이프가 있는 데이터 개체를 표시 하는 컨트롤 목록을 사용자 지정 하려면 **[기타]** 를 선택 합니다. 예를 들어 응용 프로그램에 특정 개체의 둘 이상의 속성 데이터를 표시 하는 사용자 지정 컨트롤이 있는 경우 **[기타]** 를 선택 합니다.

5. **연결 된 컨트롤** 상자에서 선택한 데이터 형식에 대해 사용할 수 있는 각 컨트롤을 선택 하거나 목록에서 제거 하려는 컨트롤의 선택을 취소 합니다.

    > [!NOTE]
    > 선택 하려는 컨트롤이 **연결 된 컨트롤** 상자에 표시 되지 않는 경우 컨트롤을 목록에 추가 해야 합니다. 자세한 내용은 [데이터 형식에 대 한 연결 된 컨트롤 목록에 컨트롤 추가](#addingcontrols)를 참조 하세요.

6. **확인**을 클릭합니다.

7. **데이터 소스** 창에서 하나 이상의 컨트롤과 연결 된 데이터 형식의 항목을 클릭 한 다음 항목에 대 한 드롭다운 메뉴를 클릭 합니다.

     **연결 된 컨트롤** 상자에서 선택한 컨트롤이 이제 해당 항목의 드롭다운 메뉴에 표시 됩니다.

## <a name="addcontrols-to-the-list-of-associated-controls-for-a-data-type"></a><a name="addingcontrols"></a> 데이터 형식에 대 한 연결 된 컨트롤 목록에 컨트롤 추가
 컨트롤을 데이터 형식과 연결 하려고 하지만 컨트롤이 **연결 된 컨트롤** 상자에 표시 되지 않는 경우 컨트롤을 목록에 추가 해야 합니다. 컨트롤이 현재 솔루션 또는 참조 된 어셈블리에 있어야 합니다. 또한 **도구 상자**에서 사용할 수 있어야 하 고 컨트롤의 데이터 바인딩 동작을 지정 하는 특성이 있어야 합니다.

#### <a name="to-add-controls-to-the-list-of-associated-controls"></a>연결 된 컨트롤 목록에 컨트롤을 추가 하려면

1. **도구 상자** 를 마우스 오른쪽 단추로 클릭 하 고 **항목 선택**을 선택 하 여 원하는 컨트롤을 **도구 상자** 에 추가 합니다.

     컨트롤에는 다음 특성 중 하나가 있어야 합니다.

    |특성|설명|
    |---------------|-----------------|
    |<xref:System.ComponentModel.DefaultBindingPropertyAttribute>|와 같은 데이터의 단일 열 또는 속성을 표시 하는 간단한 컨트롤에 대해이 특성을 구현 <xref:System.Windows.Forms.TextBox> 합니다.|
    |<xref:System.ComponentModel.ComplexBindingPropertiesAttribute>|와 같은 데이터의 목록 (또는 테이블)을 표시 하는 컨트롤에 대해이 특성을 구현 <xref:System.Windows.Forms.DataGridView> 합니다.|
    |<xref:System.ComponentModel.LookupBindingPropertiesAttribute>|데이터의 목록이 나 테이블을 표시 하는 컨트롤에 대해이 특성을 구현 합니다. 단, 단일 열 또는 속성 (예:)도 제공 해야 <xref:System.Windows.Forms.ComboBox> 합니다.|

2. Windows Forms의 경우      **옵션** 대화 상자에서 **데이터 UI 사용자 지정** 페이지를 엽니다. 또는 WPF의 경우 **컨트롤 바인딩 사용자 지정** 대화 상자를 엽니다. 자세한 내용은 [데이터 형식에 대 한 바인딩 가능한 컨트롤 목록 사용자 지정](#customizinglist)을 참조 하세요.

3. 연결 된 **컨트롤** 상자에 방금 **도구 상자** 에 추가한 컨트롤이 표시 됩니다.

    > [!NOTE]
    > 현재 솔루션 또는 참조 되는 어셈블리 내에 있는 컨트롤만 연결 된 컨트롤의 목록에 추가할 수 있습니다. 또한 컨트롤은 위의 표에 있는 데이터 바인딩 특성 중 하나를 구현 해야 합니다. 데이터 **소스** 창에서 사용할 수 없는 사용자 지정 컨트롤에 데이터를 바인딩하려면 컨트롤을 **도구 상자** 에서 디자인 화면으로 끌어 온 다음 바인딩할 항목을 **데이터 소스** 창에서 컨트롤로 끌어 옵니다.

## <a name="see-also"></a>관련 항목
 [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
