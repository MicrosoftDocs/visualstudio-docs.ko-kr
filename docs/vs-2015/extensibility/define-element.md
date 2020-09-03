---
title: Define 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, Define
- Define element (VSCT XML schema)
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8cc543a07176f307641c53a2ef3e132881821ce7
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68162152"
---
# <a name="define-element"></a>Define 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

기호 이름 및 값 쌍을 정의 합니다. 이 기호는 조건부 특성으로 평가할 수 있습니다. 자세한 내용은 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요. 또한 [기호 요소](../extensibility/symbols-element.md)를 참조 하세요.  
  
## <a name="syntax"></a>구문  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|Description|  
|---------------|-----------------|  
|name|필수 요소. 기호의 이름입니다.<br /><br /> name = "모드"|  
|값|필수 요소. 기호의 값입니다.<br /><br /> value = "Standard"|  
|조건|선택 사항입니다. 자세한 내용은 [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|  
  
### <a name="child-elements"></a>자식 요소  
 없음  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[CommandTable 요소](../extensibility/commandtable-element.md)|VSPackage가 IDE (통합 개발 환경)에 제공 하는 명령을 나타내는 모든 요소를 정의 합니다. 예를 들어 메뉴 항목, 메뉴, 도구 모음 및 콤보 상자가 있습니다.|  
  
## <a name="example"></a>예제  
  
```  
<Define name="DEMO_UI"/>  
<Define name="MODE" value="Standard"/>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
