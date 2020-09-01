---
title: VSIXLanguagePack 요소 (VSIX 언어 팩 스키마) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
ms.assetid: 767f5c22-8b87-49ca-92aa-a7a3f026469f
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e2e1df362fddeab5be98ff90460a8a1a7d4b7876
ms.sourcegitcommit: 26178b116cbf7353fee6ca989b8d872114f7b405
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/01/2020
ms.locfileid: "89284349"
---
# <a name="vsixlanguagepack-element-vsix-language-pack-schema"></a>VSIXLanguagePack 요소(VSIX 언어 팩 스키마)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

필수 요소. VSIX 언어 팩의 루트 요소를 제공 합니다. VSIX 언어 팩은 VSIX 패키지에 대 한 지역화 된 설치 정보를 제공 합니다.  
  
## <a name="syntax"></a>구문  
  
```  
<VSIXLanguagePack>  
  <LocalizedName>...</LocalizedName>  
  <LocalizedDescription>...</LocalizedDescription>  
  <MoreInfoURL>...</MoreInfoURL>  
  <License>...</License>  
</VSIXLanguagePack>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|`xmlns`|VSIX 언어 팩 스키마가 정의 된 XML 네임 스페이스입니다.|  
  
## <a name="xmlns-attribute"></a>xmlns 특성  
  
|값|설명|  
|-----------|-----------------|  
|`http://schemas.microsoft.com/developer/vsx-schema-lp/2010`|필수 요소. 언어 팩에 대 한 스키마를 정의 하는 파일의 위치입니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[LocalizedName 요소](../extensibility/localizedname-element-vsix-language-pack-schema.md)|필수 요소. 설치할 확장의 지역화 된 이름입니다.|  
|[LocalizedDescription 요소](../extensibility/localizeddescription-element-vsix-language-pack-schema.md)|필수 요소. 설치할 확장에 대 한 지역화 된 설명입니다.|  
|[MoreInfoURL 요소](../extensibility/moreinfourl-element-vsix-language-pack-schema.md)|선택 사항입니다. 확장에 대 한 지역화 된 정보에 대 한 링크입니다.|  
|[라이선스 요소](../extensibility/license-element-vsix-language-pack-schema.md)|선택 사항입니다. 확장에 대 한 라이선스 파일의 지역화 된 버전 경로입니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|없음||  
  
## <a name="element-information"></a>요소 정보  
  
|                 |                                                           |
|-----------------|-----------------------------------------------------------|
|    네임스페이스    | `http://schemas.microsoft.com/developer/vsx-schema-lp/2010` |
|   Schema Name   |                 VSIX 언어 팩 스키마                 |
| 유효성 검사 파일 |                VSIXLanguagePackSchema                 |
|  비워 둘 수 있음   |                            예                             |
  
## <a name="see-also"></a>관련 항목  
 [VSX 언어 팩 스키마 참조](../extensibility/vsx-language-pack-schema-reference.md) [vsix 패키지 지역화](../extensibility/localizing-vsix-packages.md) [vsix 확장 스키마 1.0 참조](/previous-versions/dd393700(v=vs.110))
