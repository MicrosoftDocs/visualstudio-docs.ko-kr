---
title: .NET 형식 찾아보기 및 선택 대화 상자 (레거시) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Workflow.ComponentModel.Design.TypeBrowserDialog.UI
helpviewer_keywords:
- Browse and Select a .NET Type dialog box
ms.assetid: 1e66c9bc-94b2-46e2-bedf-871752e5f917
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1e5045a62d0a654af968d50e0c309bcf8104b5cc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668982"
---
# <a name="browse-and-select-a-net-type-dialog-box-legacy"></a>.NET 유형 선택 대화 상자(레거시)
이 항목에서는 레거시에서 **.Net 유형 찾아보기 및 선택** 대화 상자를 사용 하는 방법에 대해 설명 합니다 [!INCLUDE[wfd1](../includes/wfd1-md.md)] . 레거시 [!INCLUDE[wfd2](../includes/wfd2-md.md)]는 [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] 또는 [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)]를 대상으로 해야 하는 경우에 사용합니다.

 **속성** 창에서 참조 된 어셈블리에 .NET Framework 유형을 사용 하는 속성을 선택 하면 속성의 텍스트 상자 끝에 줄임표 **(...)** 가 나타납니다. **[...]** 를 클릭 하면 **.net 유형 찾아보기 및 선택** 대화 상자가 열립니다. 이 대화 상자에서 참조된 어셈블리의 트리 뷰에서 형식을 선택할 수 있습니다. 예를 들어 활동 디자이너를 사용 하는 경우 **속성** 창에서 **기본 클래스** 줄임표 **[...]** 를 클릭 하 여 참조 된 어셈블리 트리에서 활동에 대 한 다른 기본 클래스를 선택 합니다.

 다음 표에서는 **.Net 형식 찾아보기 및 선택** 대화 상자의 UI (사용자 인터페이스) 요소에 대해 설명 합니다.

|UI 요소|설명|
|----------------|-----------------|
|**유형 이름:**|현재 선택한 형식의 이름입니다.|
|**유형**|왼쪽 창에는 참조된 어셈블리의 트리 뷰가 나타나고, 오른쪽 창에는 왼쪽 창에서 선택한 참조된 어셈블리 선택 항목에 대해 사용 가능한 형식이 표시됩니다.|

## <a name="see-also"></a>관련 항목
 [레거시 활동 디자이너 사용](../workflow-designer/using-the-legacy-activity-designer.md)