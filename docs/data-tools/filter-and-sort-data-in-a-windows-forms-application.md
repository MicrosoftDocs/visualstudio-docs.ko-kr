---
title: Windows Forms 애플리케이션에서 데이터 필터링 및 정렬
description: Windows Forms 응용 프로그램에서 데이터를 필터링 하 고 정렬 합니다. 필터 속성을 원하는 레코드를 반환 하는 문자열 식으로 설정 합니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- row states, filtering
- data views, sorting
- row version, filtering
- row states
- data views, filtering
- sorting datasets, using data views
- dataset filtering, using data views
ms.assetid: f4f100f1-776d-46dc-b2fd-5b35b98d9561
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 045da0ade1ce60e2a8d21c24238c8e2b061e8612
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/02/2021
ms.locfileid: "106215827"
---
# <a name="filter-and-sort-data-in-a-windows-forms-application"></a>Windows Forms 애플리케이션에서 데이터 필터링 및 정렬

<xref:System.Windows.Forms.BindingSource.Filter%2A>속성을 원하는 레코드를 반환 하는 문자열 식으로 설정 하 여 데이터를 필터링 합니다.

속성을 정렬할 열 이름으로 설정 하 여 데이터를 정렬 <xref:System.Windows.Forms.BindingSource.Sort%2A> `DESC` 합니다. 오름차순으로 정렬 하려면 추가를, 오름차순으로 정렬 하려면 추가를 선택 `ASC` 합니다.

> [!NOTE]
> 응용 프로그램에서 구성 요소를 사용 하지 않는 경우 <xref:System.Windows.Forms.BindingSource> 개체를 사용 하 여 데이터를 필터링 하 고 정렬할 수 있습니다 <xref:System.Data.DataView> . 자세한 내용은 [Dataviews](/dotnet/framework/data/adonet/dataset-datatable-dataview/dataviews)를 참조 하세요.

## <a name="to-filter-data-by-using-a-bindingsource-component"></a>BindingSource 구성 요소를 사용 하 여 데이터를 필터링 하려면

- 반환 하려는 <xref:System.Windows.Forms.BindingSource.Filter%2A> 식으로 속성을 설정 합니다. 예를 들어, 다음 코드는 `CompanyName` "B"로 시작 하는가 있는 고객을 반환 합니다.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet6":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet6":::

## <a name="to-sort-data-by-using-a-bindingsource-component"></a>BindingSource 구성 요소를 사용 하 여 데이터를 정렬 하려면

- 속성을 <xref:System.Windows.Forms.BindingSource.Sort%2A> 정렬 기준이 되는 열로 설정 합니다. 예를 들어 다음 코드는 열에서 고객을 `CompanyName` 내림차순으로 정렬 합니다.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDisplaying/CS/Form1.cs" id="Snippet7":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDisplaying/VB/Form1.vb" id="Snippet7":::

## <a name="see-also"></a>참고 항목

- [Visual Studio에서 데이터에 컨트롤 바인딩](../data-tools/bind-controls-to-data-in-visual-studio.md)
