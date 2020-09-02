---
title: AppliesTo 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
ms.assetid: 8fb1334b-d78c-405f-98b4-786e9f6b58d7
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f6622c4774be5188aced606ce4b73dffe544aea1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65698933"
---
# <a name="appliesto-element-visual-studio-templates"></a>AppliesTo 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

하나 이상의 기능에 맞게 선택적 식을 지정합니다. <xref:Microsoft.VisualStudio.Shell.Interop.VsProjectCapabilityExpressionMatcher>를 참조하십시오. 기능은 계층 구조를 통해 프로젝트 형식에 의해 <xref:Microsoft.VisualStudio.Shell.Interop.__VSHPROPID5> 속성으로 노출됩니다. 이렇게 하면 적용할 수 있는 일반적인 기능을 가진 여러 프로젝트 형식에서 템플릿을 공유할 수 있습니다.  
  
 이 요소는 선택적입니다. 템플릿 파일에는 최대 하나의 인스턴스만 있을 수 있습니다. 이 요소는 현재 선택된 활성 프로젝트의 기능에 따라 가능한 경우 옵트인하도록 항목 템플릿을 활성화합니다. 항목 템플릿을 적용할 수 없도록 만드는 데 사용할 수는 없습니다. `AppliesTo`가 없거나 식에 성공적으로 옵트인하지 못한 경우, `TemplateID` 또는 `TemplateGroupID`를 사용하여 템플릿을 제품의 이전 버전에 적용할 수 있게 합니다.  
  
 이 특성은 Visual Studio 2013 업데이트 2에서 도입되었습니다. 올바른 버전을 참조 하려면 [VISUAL STUDIO 2013 SDK 업데이트 2에서 제공 된 어셈블리 참조](https://msdn.microsoft.com/42b65c3e-e42b-4c39-98c8-bea285f25ffb)를 참조 하세요.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<AppliesTo>  
  
## <a name="syntax"></a>구문  
  
```  
<AppliesTo>Capability1</AppliesTo>   
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|템플릿을 분류합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 필수입니다. 이 텍스트는 프로젝트의 기능을 지정합니다.  
  
 올바른 식 구문은 다음과 같이 정의됩니다.  
  
- 기능 식입니다 (예: "(VisualC &#124; CSharp) + (MSTest &#124; NUnit)").  
  
- "&#124;"는 OR 연산자입니다.  
  
- "&" 및 "+" 문자는 모두 AND 연산자입니다.  
  
- "!" 문자는 NOT 연산자입니다.  
  
- 괄호는 계산 우선 순위를 강제 적용합니다.  
  
- Null 또는 비어 있는 식은 일치하는 항목으로 계산됩니다.  
  
- 프로젝트 기능에는 다음 예약 문자를 제외한 모든 문자 ("' ':;, +-*/ \\ ! ~&#124;&% $ @ ^ () = {} [] <>?)가 있을 수 있습니다. \t\b\n\r  
  
## <a name="example"></a>예  
 다음 예제에서는 세 개의 서로 다른 템플릿을 보여줍니다. `Template1` 모든 c # 프로젝트 형식 또는 기능을 지 원하는 다른 프로젝트 형식에 적용 됩니다 `WindowsAppContainer` . `Template2` 모든 종류의 c # 프로젝트에 적용 됩니다. `Template3`은 `WindowsAppContainer` 프로젝트가 아닌 C# 프로젝트에 적용됩니다.  
  
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
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
