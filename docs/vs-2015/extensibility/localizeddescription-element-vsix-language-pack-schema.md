---
title: LocalizedDescription 요소 (VSIX 언어 팩 스키마) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 766a1732-bbaf-4875-b276-feb42169633a
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3b4eb077ba8c957466568967804487929254117e
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114203"
---
# <a name="localizeddescription-element-vsix-language-pack-schema"></a>LocalizedDescription 요소(VSIX 언어 팩 스키마)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

필수 사항입니다. 확장에 대 한 지역화 된 설명을 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<LocalizedDescription>Localized description of the extension</LocalizedDescription>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|없음||  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|Description|  
|-------------|-----------------|  
|없음||  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|Description|  
|-------------|-----------------|  
|[VSIX LanguagePack 요소](../extensibility/vsixlanguagepack-element-vsix-language-pack-schema.md)|필수 사항입니다. VSIX 언어 팩의 루트 요소를 제공 합니다.|  
  
## <a name="text-value"></a>텍스트 값  
 필수 사항입니다. 대상 언어의 확장에 대 한 텍스트 설명입니다.  
  
## <a name="element-information"></a>요소 정보  

:::row:::
    :::column:::
        네임스페이스
    :::column-end:::
    :::column:::
        `http://schemas.microsoft.com/developer/vsx-schema-lp/2010`
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        Schema Name
    :::column-end:::
    :::column:::
        VSIX 언어 팩 스키마
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        유효성 검사 파일
    :::column-end:::
    :::column:::
        VSIXLanguagePackSchema
    :::column-end:::
:::row-end:::
:::row:::
    :::column:::
        비워 둘 수 있음
    :::column-end:::
    :::column:::
        해당 없음
    :::column-end:::
:::row-end:::
  
## <a name="see-also"></a>참고 항목  
 [VSX 언어 팩 스키마 참조](../extensibility/vsx-language-pack-schema-reference.md)   
 [VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)   
 [VSIX 확장 스키마 1.0 참조](/previous-versions/dd393700(v=vs.110))
