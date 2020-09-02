---
title: GuidSymbol 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, GuidSymbol
- GuidSymbol element (VSCT XML schema)
ms.assetid: 11fb3545-8974-4776-9a54-6b6e7739ae31
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5f11ed48d9dcf961228957cf15db3815c00d14d7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204218"
---
# <a name="guidsymbol-element"></a>GuidSymbol 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`GuidSymbol`요소는 메뉴, 그룹 또는 명령을 나타내는 guid: ID 쌍의 guid를 포함 합니다. 이 ID는 `IDSymbol` 요소의 요소에서 가져옵니다 `GuidSymbol` . 요소에는 `GuidSymbol` `name` 특성에 포함 된 GUID에 대 한 친숙 한 이름을 제공 하는 특성이 있습니다 `value` .  
  
## <a name="syntax"></a>구문  
  
```  
<GuidSymbol name="guidMyCommandSet" value="{xxxxxxxxxxxxx-xxxx-xxxx-xxxxxxxxxxxx}">  
  <IDSymbol>... </IDSymbol>  
  <IDSymbol>... </IDSymbol>  
</GuidSymbol>  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|name|필수 요소. GUID 기호의 이름입니다.|  
|값|필수 요소. GUID 기호의 GUID입니다.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[IDSymbol 요소](../extensibility/idsymbol-element.md)|메뉴, 그룹 또는 명령을 나타내는 GUID: ID 쌍의 ID를 포함 합니다.|  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[Symbols 요소](../extensibility/symbols-element.md)|`GuidSymbol`Vsct 파일의 요소를 그룹화 합니다.|  
  
## <a name="remarks"></a>설명  
 일반적으로. vsct 파일에는 해당 섹션에 세 개의 요소가 포함 되어 있습니다. 하나는 패키지 자체를 위한 것이 고, 다른 하나는 `GuidSymbol` `Symbols` 명령 집합 (패키지를 사용 하 여 사용 가능한 메뉴, 그룹 및 명령의 컬렉션) 및 단추와 기타 시각적 구성 요소에 대 한 아이콘을 제공 하는 비트맵에 대 한 것입니다. `IDSymbol`지정 된 요소의 모든 요소에 `GuidSymbol` 는 고유한가 있어야 합니다 `value` . 그러나 `IDSymbol` 동일한 값을 가진 요소는 부모 항목이 다른 경우 패키지에 있을 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
