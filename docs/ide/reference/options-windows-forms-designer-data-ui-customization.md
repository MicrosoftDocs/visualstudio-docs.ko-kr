---
title: 옵션, Windows Forms 디자이너, 데이터 UI 사용자 지정
ms.date: 08/09/2019
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.WindowsFormsDesigner.Data_UI_Customization
helpviewer_keywords:
- Data UI customization options
- Options dialog box, Windows Forms Designer, Data UI Customization
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e48777a50ddf66a8e5493698fb401ff7201de03e
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114682"
---
# <a name="options-dialog-box-windows-forms-designer--data-ui-customization"></a>옵션 대화 상자: Windows Forms 디자이너 > 데이터 UI 사용자 지정

이 대화 상자는 데이터 소스 창에서 항목에 대해 사용할 수 있는 컨트롤 목록에 표시되는 컨트롤을 정의합니다. 이 대화 상자를 열려면 **도구** > **옵션**을 선택한 다음, **Windows Forms 디자이너** > **데이터 UI 사용자 지정**을 선택합니다.

데이터 소스 창의 항목에서 컨트롤을 선택하여 Windows Forms 앱의 폼으로 끌어올 수 있습니다. 사용 가능한 컨트롤은 항목의 데이터 형식에 따라 결정됩니다. 각 데이터 형식에는 기본 컨트롤을 포함하여 이 대화 상자에 정의된 유효한 관련 컨트롤 목록이 있습니다. 컨트롤을 선택하지 않고 데이터 소스 창에서 폼으로 항목을 끌어오면 선택한 항목의 데이터 형식에 대한 기본 컨트롤이 폼에 추가됩니다.

각 데이터 형식에 대해 사용 가능한 컨트롤의 확인란을 선택 및 선택 취소하여 관련 컨트롤 목록을 사용자 지정합니다. 컨트롤을 목록에 추가하려면 <xref:System.ComponentModel.DefaultBindingPropertyAttribute> 또는 <xref:System.ComponentModel.ComplexBindingPropertiesAttribute> 데이터 바인딩 특성을 구현하는 컨트롤을 도구 상자에 추가합니다. 그러면 컨트롤이 데이터 형식에 대한 컨트롤 목록에 표시됩니다. 자세한 내용은 [방법: 데이터 소스 창에 사용자 지정 컨트롤 추가](../..//data-tools/add-custom-controls-to-the-data-sources-window.md)를 참조하세요.

## <a name="data-type"></a>데이터 형식

컨트롤을 연결할 형식 목록을 표시합니다. 테이블은 `[List]` 데이터 형식으로 표시됩니다. 열은 기본 데이터 저장소에 있는 열의 실제 데이터 형식으로 표시됩니다.

## <a name="associated-controls"></a>연결된 컨트롤

선택한 데이터 형식에 연결된 컨트롤의 목록을 표시합니다. 컨트롤 옆에 있는 확인란을 선택하거나 선택 취소하여 연결하거나 연결을 해제합니다. 선택한 컨트롤은 연결된 데이터 형식에 바인딩된 데이터베이스 열에 대한 데이터 소스 창에 표시됩니다.

## <a name="set-default"></a>기본값 설정

선택한 데이터 형식의 기본값이 되도록 선택한 컨트롤 형식을 할당합니다. 기본 컨트롤은 데이터 소스 창에서 데이터베이스 열의 바로 가기 메뉴에 첫 번째 선택 항목으로 나타납니다. 컨트롤을 선택하지 않고 데이터 소스 창에서 폼으로 항목을 끌어오면 선택한 항목의 데이터 형식에 대한 기본 컨트롤이 폼에 추가됩니다.

하나의 컨트롤 유형만 데이터 형식의 기본값으로 할당할 수 있습니다.

## <a name="clear-default"></a>기본값 지우기

선택한 데이터 형식의 기본값으로 설정한 컨트롤 지정을 제거합니다. 선택한 데이터 형식의 기본 컨트롤이 없으면 `[None]`이 해당 형식의 데이터베이스 열에 대한 바로 가기 메뉴의 첫 번째 선택 항목으로 나타납니다.
