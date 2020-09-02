---
title: Property 요소(MSBuild) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- <Property> Element [MSBuild]
- Property Element [MSBuild]
ms.assetid: 69ab08ab-3e76-41dd-a01b-49aa1d2e0cac
caps.latest.revision: 20
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: eefe0160328f1eb6b3fe841742547efe8be50ec1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158269"
---
# <a name="property-element-msbuild"></a>Property 요소(MSBuild)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 정의 속성 이름 및 값을 포함합니다. [!INCLUDE[vstecmsbuild](../includes/vstecmsbuild-md.md)] 프로젝트에서 사용되는 모든 속성은 `PropertyGroup` 요소의 자식으로 지정해야 합니다.  
  
 \<Project>  
 \<PropertyGroup>  
  
## <a name="syntax"></a>구문  
  
```  
<Property Condition="'String A' == 'String B'">  
    Property Value  
</Property>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`Condition`|선택적 특성입니다.<br /><br /> 평가할 조건입니다. 자세한 내용은 [조건](../msbuild/msbuild-conditions.md)을 참조하세요.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[PropertyGroup](../msbuild/propertygroup-element-msbuild.md)|속성에 대한 grouping 요소입니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 선택적입니다.  
  
 이 텍스트는 속성값을 지정하며 XML을 포함할 수 있습니다.  
  
## <a name="remarks"></a>설명  
 속성 이름에는 ASCII 문자만 사용할 수 있습니다. "`$(`" 및 "`)`" 사이에 속성 이름을 배치하여 프로젝트에서 속성값을 참조합니다. 예를 들어 `builddir` 속성값이 `build`이면 `$(builddir)\classes`는 "build\classes"로 해석됩니다. 속성에 대 한 자세한 내용은 [MSBuild 속성](msbuild-properties1.md)을 참조 하세요.  
  
## <a name="example"></a>예  
 다음 코드는 `Version` 속성이 비어 있으면 `Optimization` 속성을 `false`로, `DefaultVersion` 속성을 `1.0`로 설정합니다.  
  
```  
<PropertyGroup>  
    <Optimization>false</Optimization>  
    <DefaultVersion Condition="'$(Version)' == ''" >1.0</DefaultVersion>  
</PropertyGroup>  
```  
  
## <a name="see-also"></a>관련 항목
[MSBuild 속성](msbuild-properties1.md)  
 [프로젝트 파일 스키마 참조](../msbuild/msbuild-project-file-schema-reference.md)
