---
title: 워크플로 디자이너-.NET 유형 찾아보기 및 선택 대화 상자
description: .NET 형식 찾아보기 및 선택 대화 상자를 사용 하 여 어셈블리 및 프로젝트의 트리 뷰에서 형식을 선택 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- TypeBrowser.UI
- ActivityTypeResolver.UI
ms.assetid: 864b60b6-a070-4e5c-aa5b-a25341b57ea6
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7e887cf339647df9bca7fdc3d07a45dd44901c42
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94438180"
---
# <a name="browse-and-select-a-net-type-dialog-box"></a>.NET 유형 선택 대화 상자

데이터 형식 목록에서 **형식 찾아보기** 를 선택 하면 **속성** 창, 대화 상자 또는 변수 디자이너와 같은 디자이너에서 **.net 형식 찾아보기 및 선택** 대화 상자가 표시 됩니다 .이 대화 상자는 약식 형식으로 "형식 브라우저" 라고 합니다. 이 대화 상자의 어셈블리 및 프로젝트 트리 뷰에서 형식을 선택할 수 있습니다.

이 대화 상자는 다음을 비롯한 여러 가지 사용자 시나리오에서 사용됩니다.

- 변수 또는 인수의 형식을 설정할 때

- 제네릭 동작의 형식을 선택할 때

- <xref:System.Activities.Statements.TryCatch> 활동에 catch를 추가할 때

> [!NOTE]
> 형식 브라우저는 Visual Basic 가변 배열 형식을 표시할 수 있지만 다차원 배열 형식을 표시할 수 없습니다. 자세한 내용은 [가변 배열](/previous-versions/visualstudio/visual-studio-2008/hkhhsz9t(v=vs.90)) 및 [다차원 배열](/previous-versions/visualstudio/visual-studio-2008/d2de1t93(v=vs.90)) 을 참조 하세요.

## <a name="selecting-a-value-or-reference-type-from-the-type-browser"></a>형식 브라우저에서 값 또는 참조 형식 선택

### <a name="to-select-a-value-or-reference-type-from-the-type-browser"></a>형식 브라우저에서 값 또는 참조 형식을 선택하려면

1. **유형 이름** 상자에 사용 하려는 유형의 이름을 입력 합니다.

2. 다음 중 하나를 수행합니다.

    - 사용할 형식 이름이 **형식 이름** 상자의 트리에 표시 되 면 형식을 두 번 클릭 하 여 선택 합니다.

    - **유형 이름** 상자에 충분 한 문자를 입력 하 여 사용할 유형을 고유 하 게 식별 한 다음 enter 키를 눌러 유형을 선택 합니다.

### <a name="to-select-a-generic-type-from-the-type-browser"></a>형식 브라우저에서 제네릭 형식을 선택하려면

1. **유형 이름** 상자에 사용 하려는 유형의 이름을 입력 합니다.

2. 사용할 형식 이름이 **형식 이름** 상자의 트리에 표시 되 면 형식을 클릭 하 여이를 선택 하면 드롭다운 상자가 표시 됩니다.

     드롭다운 상자에서 제네릭를 닫는 데 사용할 형식을 선택 하 고 **확인** 을 클릭 합니다.

## <a name="types-displayed-in-the-type-browser"></a>형식 브라우저에 표시된 형식

형식 브라우저에 표시되는 형식은 형식 브라우저의 시작 방식에 따라 달라질 수 있습니다. **Vs2010** 내부의 워크플로 프로젝트에서 형식 브라우저를 시작한 경우에는 기본적으로 참조 되는 어셈블리 및 참조 된 프로젝트의 모든 형식이 표시 됩니다. **Vs2010** 프로젝트 시스템 외부에서 형식 브라우저가 시작 된 경우 (예: 다시 호스트 된 워크플로 응용 프로그램 또는 독립 실행형 워크플로 파일에서) AppDomain에 로드 된 모든 어셈블리의 형식이 기본적으로 표시 됩니다.

활동 디자이너 개발자는 형식 브라우저의 형식을 필터링할 수 있습니다. 특정 활동에서 형식의 하위 집합만 표시되는 경우가 있습니다. 예를 들어 <xref:System.Activities.Statements.TryCatch> 활동의 경우 <xref:System.Exception>에서 파생된 형식만 형식 브라우저에 표시됩니다.

## <a name="filtering-search-results-in-the-type-browser"></a>형식 브라우저에서 검색 결과 필터링

일치 항목을 찾기 위해 더 많은 문자를 입력 하면 **유형 이름** 상자의 유형 목록이 더 짧아집니다. Fullyqualified 이름이 입력 한 문자열로 시작 하는 형식 또는 약식 이름이 입력 한 문자열로 시작 하는 형식만 필터링 된 목록에 표시 됩니다.

예를 들면 다음과 같습니다.

1. 입력 **작업이** 일치 <xref:System.OperationCanceledException> 하지만 일치 하지 않습니다 <xref:System.InvalidOperationException> . <xref:System.InvalidOperationException>을 찾으려면 System.I 또는 Invalid를 입력해야 합니다.

2. 네임 스페이스에서 **제네릭** 일치 항목을 입력 <xref:System.GenericUriParser> 하지만 형식이 아닙니다 <xref:System.Collections.Generic> . 네임 스페이스에서 형식을 검색 하려면 <xref:System.Collections.Generic> 네임 스페이스의 정규화 된 이름을 입력 합니다.

## <a name="selecting-a-service-contract-using-the-type-browser-dialog"></a>형식 브라우저 대화 상자를 사용하여 서비스 계약 선택

서비스 계약 형식을 선택할 때 형식 브라우저는 <xref:System.ServiceModel.ServiceContractAttribute> 특성이 있는 형식만 보여줍니다.

## <a name="see-also"></a>참조

- [활동 디자이너 사용](control-flow-activity-designers.md)
