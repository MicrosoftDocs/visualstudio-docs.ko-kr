---
title: 모델링 SDK에 대 한 API 참조
description: Visual Studio 시각화 및 모델링 SDK에서 Dsl (도메인별 언어) 도구가 빌드되는 플랫폼을 제공 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9603ace5751443c04d0a7503a43e08c044269817
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385463"
---
# <a name="api-reference-for-modeling-sdk-for-visual-studio"></a>Visual Studio용 모델링 SDK에 대한 API 참조

Visual Studio 시각화 및 모델링 SDK는 DSL (도메인별 언어) 도구를 빌드하는 데 사용할 수 있는 플랫폼을 제공 합니다.

이 섹션에는 이름이 "VisualStudio"로 시작 하는 네임 스페이스에 대 한 참조 자료가 포함 되어 있습니다.

|네임스페이스|콘텐츠|
|-|-|
|<xref:Microsoft.VisualStudio.Modeling?displayProperty=fullName>|ModelElement와 같은 클래스-DSL에서 정의 하는 모든 도메인 클래스의 기본 클래스입니다.|
|<xref:Microsoft.VisualStudio.Modeling.Design?displayProperty=fullName>|DSL 정의의 일부를 구성 하는 클래스입니다.|
|<xref:Microsoft.VisualStudio.Modeling.Diagnostics?displayProperty=fullName>|모델 저장소 뷰어 및 성능 측정 도구입니다.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams?displayProperty=fullName>|ShapeElement와 같은 클래스-DSL에서 정의 하는 모든 셰이프의 기본 클래스입니다.|
|<xref:Microsoft.VisualStudio.Modeling.Diagrams.ExtensionEnablement?displayProperty=fullName>|제스처 및 선택 방법|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition?displayProperty=fullName>|DSL 정의 디자이너의 API입니다.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.Design?displayProperty=fullName>|DSL 정의 디자이너의 내부 클래스입니다.|
|<xref:Microsoft.VisualStudio.Modeling.DslDefinition.ExtensionEnablement?displayProperty=fullName>|명령, 제스처 및 유효성 검사를 사용 하 여 DSL 디자이너를 확장할 수 있는 특성입니다.|
|<xref:Microsoft.VisualStudio.Modeling.Extensibility?displayProperty=fullName>|DSL 확장성을 구현 하는 ModelElement에 대 한 확장 메서드입니다.|
|<xref:Microsoft.VisualStudio.Modeling.ExtensionEnablement?displayProperty=fullName>|확장성 특성|
|<xref:Microsoft.VisualStudio.Modeling.Immutability?displayProperty=fullName>|모델의 일부를 읽기 전용으로 만들 수 있습니다.|
|[VisualStudio. 통합](/previous-versions/ee904412(v=vs.140))|Modelbus API는 여러 모델을 통합 하는 데 도움이 됩니다.|
|[VisualStudio를 선택 합니다.](/previous-versions/ee904394(v=vs.140))|사용자가 모델 및 요소로 이동 하 여 Modelbus 참조를 만들 수 있는 대화 상자입니다.|
|`Microsoft.VisualStudio.Modeling.Integration.Picker.Hosting`|선택 서비스입니다.|
|[VisualStudio입니다.](/previous-versions/ee869435(v=vs.140))|Visual Studio 용 Modelbus adapter 프레임 워크.|
|[VisualStudio를 선택 합니다.](/previous-versions/ee886769(v=vs.140))|사용자가 모델 및 요소로 이동 하 여 Modelbus 참조를 만들 수 있는 선택 대화 상자입니다.|
|<xref:Microsoft.VisualStudio.Modeling.Shell?displayProperty=fullName>|Dsl과 Visual Studio 간의 인터페이스입니다.|
|<xref:Microsoft.VisualStudio.Modeling.Shell.ExtensionEnablement?displayProperty=fullName>|바로 가기 (상황에 맞는) 메뉴 명령을 정의할 수 있습니다.|
|<xref:Microsoft.VisualStudio.Modeling.Validation?displayProperty=fullName>|유효성 검사 제약 조건을 정의할 수 있습니다.|

## <a name="see-also"></a>참조

- [T4 텍스트 변환 사용자 지정](../modeling/customizing-t4-text-transformation.md)
