---
title: 적용요소 (비주얼 스튜디오 템플릿) | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 39b5ee1e3cad0b4d8ddbe0fc2dfa1c2d478ec063
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740080"
---
# <a name="appliesto-element-visual-studio-templates"></a>적용토 요소(비주얼 스튜디오 템플릿)

하나 이상의 기능과 일치하도록 선택적 식을 <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>지정합니다(참조). 기능은 계층 구조를 통해 속성 __VSHPROPID5 통해 프로젝트 유형에 의해 [노출됩니다. VSHPROPID_ProjectCapabilities](<xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5.VSHPROPID_ProjectCapabilities>). 이렇게 하면 적용할 수 있는 일반적인 기능을 가진 여러 프로젝트 형식에서 템플릿을 공유할 수 있습니다.

이 요소는 선택적입니다. 템플릿 파일에는 최대 하나의 인스턴스만 있을 수 있습니다. 이 요소는 현재 선택된 활성 프로젝트의 기능에 따라 가능한 경우 옵트인하도록 항목 템플릿을 활성화합니다. 항목 템플릿을 적용할 수 없도록 만드는 데 사용할 수는 없습니다. `AppliesTo`가 없거나 식에 성공적으로 옵트인하지 못한 경우, `TemplateID` 또는 `TemplateGroupID`를 사용하여 템플릿을 제품의 이전 버전에 적용할 수 있게 합니다.

이 특성은 Visual Studio 2013 업데이트 2에서 도입되었습니다. 올바른 버전을 참조하려면 [Visual Studio 2013 SDK 업데이트 2에서 전달된 참조 어셈블리를](/previous-versions/dn632168(v=vs.120))참조하십시오.

```xml
<VSTemplate>
   <TemplateData>
      <AppliesTo>
```

## <a name="syntax"></a>구문

```xml
<AppliesTo>Capability1</AppliesTo>
```

## <a name="attributes-and-elements"></a>특성 및 요소

다음 단원에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.

### <a name="attributes"></a>특성

없음

### <a name="child-elements"></a>자식 요소

없음

### <a name="parent-elements"></a>부모 요소

|요소|Description|
|-------------|-----------------|
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|템플릿을 분류합니다.|

## <a name="text-value"></a>텍스트 값

텍스트 값은 필수입니다. 이 텍스트는 프로젝트의 기능을 지정합니다.

올바른 식 구문은 다음과 같이 정의됩니다.

- "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)"와 같은 기능 표현식입니다.

- "&#124;"은 OR 연산자입니다.

- "&" 및 "+" 문자는 모두 AND 연산자입니다.

- "!" 문자는 NOT 연산자입니다.

- 괄호는 계산 우선 순위를 강제 적용합니다.

- Null 또는 비어 있는 식은 일치하는 항목으로 계산됩니다.

- 프로젝트 기능은 이러한 예약 된 문자를 제외 하 고 모든 문자\\수 있습니다.: "'',,,--*/ !~&#124;&%@^()={}[]<>? \t\b\n\r

## <a name="example"></a>예제

다음 예제에서는 세 개의 서로 다른 템플릿을 보여줍니다. `Template1`은 모든 C# 프로젝트 유형 또는 `WindowsAppContainer` 기능을 지원하는 다른 프로젝트 유형에 적용됩니다. `Template2`모든 C# 프로젝트에 적용됩니다. `Template3`은 `WindowsAppContainer` 프로젝트가 아닌 C# 프로젝트에 적용됩니다.

```xml
<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp | WindowsAppContainer</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 2 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp</AppliesTo>
    </TemplateData>
</VSTemplate>

<!--  Template 1 -->
<?xml version="1.0" encoding="utf-8"?>
<VSTemplate Version="3.0.0" Type="Item" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <AppliesTo>CSharp_Class + (!WindowsAppContainer)</AppliesTo>
    </TemplateData>
</VSTemplate>
```

## <a name="see-also"></a>참조

- [비주얼 스튜디오 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
