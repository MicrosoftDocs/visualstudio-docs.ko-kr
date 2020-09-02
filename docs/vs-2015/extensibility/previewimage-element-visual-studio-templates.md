---
title: PreviewImage 요소 (Visual Studio 템플릿) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- <PreviewImage> Element (Visual Studio Templates)
- PreviewImage Element (Visual Studio Templates)
ms.assetid: d1796f20-523b-4e0d-8ac3-ca87f3b5a9b6
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 90521b5ea05aae2f54e56f21b65933a93580da85
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194061"
---
# <a name="previewimage-element-visual-studio-templates"></a>PreviewImage 요소(Visual Studio 템플릿)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**새 프로젝트** 또는 **새 항목 추가** 대화 상자에 표시 되는 미리 보기 이미지에 대 한 미리 보기 이미지를 파일 이름으로 지정 합니다.  
  
 \<VSTemplate>  
 \<TemplateData>  
 \<PreviewImage>  
  
## <a name="syntax"></a>구문  
  
```  
<PreviewImage>"filename"</PreviewImage>  
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
  
 텍스트는 파일 이름을 나타내는 문자열 이어야 합니다.  
  
## <a name="remarks"></a>설명  
 `PreviewImage`는 선택적 요소입니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)   
 [프로젝트 템플릿 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
