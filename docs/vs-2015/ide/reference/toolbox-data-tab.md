---
title: 도구 상자, 데이터 탭 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Toolbox, Data tab
- Data tab, Toolbox
- data [Visual Studio], Toolbox
ms.assetid: 2ae38b2a-29d2-461c-a67d-29dad274bf45
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9349745eeee24f2f8b1e62eb2b01bd75273c86d8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658592"
---
# <a name="toolbox-data-tab"></a>도구 상자, 데이터 탭
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

폼 및 구성 요소에 추가할 수 있는 데이터 개체를 표시합니다. 연결된 디자이너가 있는 프로젝트를 만들 경우 **도구 상자**의 **데이터** 탭이 표시됩니다. Visual Studio 통합 개발 환경에는 기본적으로 **도구 상자**가 표시됩니다. **도구 상자**를 표시해야 할 경우 **보기** 메뉴에서 **도구 상자**를 선택합니다.

> [!TIP]
> 데이터 소스 구성 마법사를 실행하면 대부분의 데이터 항목이 자동으로 생성 및 구성됩니다. 자세한 내용은 [Creating Data Applications with Visual Studio](https://msdn.microsoft.com/28edce21-220a-484c-b461-a75b0232d293)(Visual Studio를 사용하여 데이터 애플리케이션 만들기)를 참조하세요.

## <a name="ui-element-list"></a>UI 요소 목록
 구성 요소에 대한 .NET Framework 참조 페이지로 직접 이동하려면 **도구 상자**의 항목 또는 디자이너 트레이의 구성 요소 항목에서 **F1** 키를 누릅니다.

|속성|Description|
|----------|-----------------|
|<xref:System.Data.DataSet>|형식화된 데이터 세트 또는 형식화되지 않은 데이터 세트의 인스턴스를 폼 또는 구성 요소에 추가합니다. 이 개체를 디자이너로 끌면 기존 형식화된 데이터 세트 클래스를 선택하거나 새로운 빈 형식화되지 않은 데이터 세트를 만들도록 지정할 수 있는 대화 상자가 표시됩니다. **참고:****도구 상자**에서는 새 형식화된 데이터 세트 스키마 및 클래스를 만드는 데 <xref:System.Data.DataSet> 개체를 사용하지 않습니다. 자세한 내용은 [데이터 세트 만들기 및 구성](../../data-tools/create-and-configure-datasets-in-visual-studio.md)을 참조하세요.|
|<xref:System.Windows.Forms.DataGridView>|데이터를 표 형식으로 효과적이고 유연하게 표시할 수 있습니다.|
|<xref:System.Windows.Forms.BindingSource>|내부 데이터 소스에 컨트롤을 바인딩하는 프로세스를 간소화합니다.|
|<xref:System.Windows.Forms.BindingNavigator>|데이터에 바인딩된 폼의 컨트롤에 대한 탐색 및 조작 UI(사용자 인터페이스)를 나타냅니다.|

## <a name="see-also"></a>관련 항목
 [데이터 연습](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) [visual studio에서 데이터에 컨트롤 Windows Forms 바인딩](../../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) [visual studio](../../data-tools/bind-controls-to-data-in-visual-studio.md) 에서 데이터에 데이터 바인딩을 [수신 하도록 응용 프로그램 준비](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) [데이터 유효성 검사](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)