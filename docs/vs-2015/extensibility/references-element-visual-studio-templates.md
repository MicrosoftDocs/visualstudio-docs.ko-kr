---
title: References 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#References
helpviewer_keywords:
- <References> element [Visual Studio Templates]
- References element [Visual Studio Templates]
ms.assetid: 1969146d-46bf-422d-8d46-0e9493925003
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 19fd3e260e6c7079ccfb98f520858a31191cc112
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62538215"
---
# <a name="references-element-visual-studio-templates"></a>References 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

템플릿이 프로젝트에 추가 하는 어셈블리 참조를 그룹화 합니다.  
  
 \<VSTemplate>  
 \<TemplateContent>  
 \<References>  
  
## <a name="syntax"></a>구문  
  
```  
<References>  
    <Reference>... </Reference>  
    <Reference>... </Reference>  
    ...  
</References>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
 없음  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[참조](../extensibility/reference-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 항목이 프로젝트에 추가될 때 추가할 어셈블리 참조를 지정합니다. `Reference`요소에는 요소가 하나 이상 있어야 합니다 `References` .|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|템플릿의 내용을 지정 합니다.|  
  
## <a name="remarks"></a>설명  
 `References`은 `TemplateContent`의 선택적 자식 요소입니다.  
  
 `Reference`및 `References` 요소는 `Type` 특성 값이 인 .vstemplate 파일에만 사용할 수 있습니다 `Item` .  
  
## <a name="example"></a>예  
 다음 예제에서는 `TemplateContent` 항목 템플릿의 요소를 보여 줍니다. 이 XML은 System.dll 및 System.Data.dll 어셈블리에 대 한 참조를 추가 합니다.  
  
```  
<TemplateContent>  
    <References>  
        <Reference>  
            <Assembly>  
                System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
        <Reference>  
            <Assembly>  
                System.Data, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089  
            </Assembly>  
        </Reference>  
    </References>  
    ...  
</TemplateContent>  
```  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
