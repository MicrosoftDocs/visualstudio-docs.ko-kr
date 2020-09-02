---
title: MaxFrameworkVersion 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <MaxFrameworkVersion> Element (Visual Studio Templates)
- MaxFrameworkVersion Element (Visual Studio Templates)
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4a1c27e42574429dbb6b2eaeb140db484bf29db5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194324"
---
# <a name="maxframeworkversion-element-visual-studio-templates"></a>MaxFrameworkVersion 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

템플릿에 필요한 .NET Framework의 최대 버전을 지정 합니다. **새 프로젝트 추가** 대화 상자의 **대상 프레임 워크 버전** 상자에서 선택한 값에 따라 **새 프로젝트 추가** 대화 상자의 **템플릿** 섹션에 템플릿이 표시 되는지 여부를 결정 합니다.  
  
 \<VSTemplate>  
 \<MaxFrameworkVersion>  
  
## <a name="syntax"></a>구문  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|필수적 요소입니다.<br /><br /> 템플릿을 분류 하 고 **새 프로젝트** 또는 **새 항목 추가** 대화 상자에 템플릿을 표시 하는 방법을 정의 합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 텍스트 값은 필수입니다.  
  
 텍스트는 템플릿에서 허용 하는 .NET Framework의 가장 높은 버전 번호 여야 합니다.  
  
## <a name="remarks"></a>설명  
 `MaxFrameworkVersion`는 선택적 요소입니다. `TemplateData`.Vstemplate 파일의 섹션에 있는 요소는 **새 프로젝트 추가** 대화 상자의 **템플릿** 섹션에 대 한 필터 역할을 합니다. `MaxFrameworkVersion` **새 프로젝트 추가** 대화 상자의 **대상 프레임 워크 버전** 상자에서 선택한 값에 따라 .NET Framework 요구 사항이 요소 값 보다 작은 템플릿만 표시 됩니다. `MaxFrameworkVersion`요소가 필요 하지 않은 경우 생략 해야 합니다. 따라서 새 버전의 .NET Framework 사용 하는 경우 실수로 템플릿이 표시 되지 않습니다.  
  
## <a name="example"></a>예  
 다음 예제에서는 표준 클래스 템플릿에 대 한 메타 데이터를 보여 줍니다 [!INCLUDE[csprcs](../includes/csprcs-md.md)] .  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 이 예제에서로 표시 되는 템플릿에 필요한 .NET Framework의 최대 버전 `MaxFrameworkVersion` 은 3.5입니다. 위의 템플릿은 **새 프로젝트 추가** 대화 상자의 **대상 프레임 워크 버전** 상자에서 3.0 또는 3.5를 선택 하는 경우에만 표시 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
