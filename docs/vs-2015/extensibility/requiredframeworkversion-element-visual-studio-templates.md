---
title: RequiredFrameworkVersion 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <RequiredFrameworkVersion> (Visual Studio Templates)
- RequiredFrameworkVersion (Visual Studio Templates)
ms.assetid: 08a4f609-51a5-4723-b89f-99277fb18871
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ce312d7951f4c1be720604c006f9afcd63f364d3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68163657"
---
# <a name="requiredframeworkversion-element-visual-studio-templates"></a>RequiredFrameworkVersion 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

템플릿에 필요한 최소 .NET Framework 버전을 지정 합니다. 스키마 계층 구조.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<RequiredFrameworkVersion>  
  
## <a name="syntax"></a>구문  
  
```  
<RequiredFrameworkVersion> .... </RequiredFrameworkVersion>  
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
  
 텍스트는 템플릿에 필요한 .NET Framework의 최소 버전 번호 여야 합니다.  
  
## <a name="remarks"></a>설명  
 `RequiredFrameworkVersion`는 선택적 요소입니다. 템플릿이 .NET Framework의 특정 최소 버전 및 이후 버전 (있는 경우)만 지 원하는 경우이 요소를 사용 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)   
 [특정 대상 .NET Framework 버전 지정](../ide/targeting-a-specific-dotnet-framework-version.md)
