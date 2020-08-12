---
title: License 요소 (VSIX 언어 팩 스키마) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 57dac3b7-0cdd-405c-9af5-30ed9ca45e53
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 91f0792f64e09292836a3b2d60f669c67903b3a7
ms.sourcegitcommit: d9254e54079ae01cdf2d07b11f988faf688f80fc
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/11/2020
ms.locfileid: "88114180"
---
# <a name="license-element-vsix-language-pack-schema"></a>License 요소(VSIX 언어 팩 스키마)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

선택 사항입니다. 확장에 대 한 라이선스 파일의 지역화 된 버전 경로입니다.  
  
## <a name="syntax"></a>구문  
  
```  
<License>FilePath\license.txt</License>  
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
 표시할 지역화 된 라이선스 파일의 상대 경로입니다.  
  
## <a name="remarks"></a>설명  
 `License`요소가 정의 된 경우에는 설치 중에 지정 된 라이선스 파일의 텍스트가 표시 되 고 사용자는 계속 하려면 라이선스에 동의 해야 합니다.  
  
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
