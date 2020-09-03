---
title: KeyBinding 요소 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- VSCT XML schema elements, KeyBindings
- KeyBinding element (VSCT XML schema)
ms.assetid: e55a1098-15df-42a9-9f87-e3a99cf437dd
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 75d96098e8444aac9a4fc6f895099435b54f640b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68180321"
---
# <a name="keybinding-element"></a>KeyBinding 요소
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

KeyBinding 요소는 명령에 대 한 바로 가기 키를 지정 합니다.  
  
 명령에는 연결 된 단일 및 이중 키 바인딩이 모두 포함 될 수 있습니다. 단일 키 바인딩의 예는 **Save** 명령에 대 한 CTRL + S입니다. 이중 키 바인딩에는 명령을 트리거하는 두 개의 연속 키 조합이 필요 합니다. 이중 키 바인딩의 예는 책갈피를 설정 하는 CTRL + K, CTRL + K입니다.  
  
## <a name="syntax"></a>구문  
  
```  
<Keybinding guid="MyGuid" id="MyId" Editor="MyEditor" key1="B" key2="x" mod1="Control" mod2="Alt" />  
```  
  
## <a name="attributes-and-elements"></a>특성 및 요소  
 다음 섹션에서는 특성, 자식 요소 및 부모 요소에 대해 설명합니다.  
  
### <a name="attributes"></a>특성  
  
|특성|설명|  
|---------------|-----------------|  
|guid|필수 요소.|  
|id|필수 요소.|  
|편집기|필수 요소. 편집기 GUID는이 바로 가기 키가 활성화 될 편집 컨텍스트를 나타냅니다. 전역 바인딩 범위 값은 "guidVSStd97"입니다.|  
|key1|필수 요소. 유효한 값은 모든 typable 영숫자를 포함 하 고 0x 및 VK_constants 앞에 오는 두 자리 16 진수 값을 포함 합니다.|  
|mod1|선택 사항입니다. 공백으로 구분 된 CTRL, ALT 및 SHIFT의 조합입니다.|  
|key2|선택 사항입니다. 유효한 값은 모든 typable 영숫자를 포함 하 고 0x 및 VK_constants 앞에 오는 두 자리 16 진수 값을 포함 합니다.|  
|mod2|선택 사항입니다. 공백으로 구분 된 CTRL, ALT 및 SHIFT의 조합입니다.|  
|에뮬레이터|선택 사항입니다.|  
|조건|선택 사항입니다. [조건부 특성](../extensibility/vsct-xml-schema-conditional-attributes.md)을 참조 하세요.|  
  
### <a name="child-elements"></a>자식 요소  
  
|요소|설명|  
|-------------|-----------------|  
|Parent||  
|주석||  
  
### <a name="parent-elements"></a>부모 요소  
  
|요소|설명|  
|-------------|-----------------|  
|[KeyBindings 요소](../extensibility/keybindings-element.md)|KeyBinding 요소 및 기타 키 바인딩 그룹을 그룹화 합니다.|  
  
## <a name="example"></a>예제  
  
```  
<KeyBindings>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget"   
    editor="guidWidgetEditor" key1="VK_F5"/>  
  <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget"   
    editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/>  
</KeyBindings>  
```  
  
## <a name="see-also"></a>참고 항목  
 [KeyBindings 요소](../extensibility/keybindings-element.md)   
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
