---
title: VSCT XML 스키마 조건부 특성 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT XML schema elements, conditional attributes
- conditional attributes (VSCT XML schema)
ms.assetid: 754d4f32-319b-44c9-915f-f7c60e53222e
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6294ee8027b61840149096561efc91b8a4a3c3ec
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62422164"
---
# <a name="vsct-xml-schema-conditional-attributes"></a>VSCT XML 스키마 조건부 특성
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모든 목록 및 항목에 조건부 특성을 적용할 수 있습니다. 논리 연산자 및 기호 확장 식은 true 또는 false로 계산 됩니다. True 이면 연결 된 목록 또는 항목이 결과 출력에 포함 됩니다.  
  
 토큰 확장은 다른 토큰 확장 또는 상수에 대해 테스트할 수 있습니다. 정의 된 함수 ()는 값이 없는 경우에도 특정 이름이 정의 되었는지 여부를 테스트 하는 데 사용 됩니다.  
  
 조건 특성이 목록에 적용 되 면 해당 조건이 목록의 모든 자식 요소에 적용 됩니다. 자식 요소 자체에 조건 특성이 포함 된 경우 해당 조건이 AND 연산에 의해 부모 식과 결합 됩니다.  
  
 값 1, ' 1 ' 및 ' t r u e '는 true로 평가 되 고 0, ' 0 ' 및 ' f a l s e '는 false로 평가 됩니다.  
  
## <a name="operators"></a>연산자  
 다음 연산자는 조건식을 평가 하는 데 사용할 수 있습니다.  
  
|연산자|정의|  
|--------------|----------------|  
|(,)|그룹화|  
|!|논리 NOT|  
|\<, >, \<=, >=, ==, !=|관계형 및 같음|  
|및|부울|  
|또는|부울|  
  
## <a name="examples"></a>예제  
  
```  
<Menu Condition="Defined(DEBUG)" …  
</Menu>  
  
<Menu Condition="%(SKU_MODE) = 'Demo'" …  
</Menu>  
  
<Menus Condition="Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="Defined(DEMO_SKU)">  
    <Menus Condition="!Defined(DEBUG)">  
        <Menu …  
        </Menu>  
    </Menus>  
  
    <Menu …  
    </Menu>  
</Menus>  
  
<Menus Condition="(Defined(DEMO_SKU) or Defined(SAMPLE_SKU))   
and !Defined(DEBUG)">  
    <Menu …  
    </Menu>  
</Menus>  
```  
  
## <a name="see-also"></a>참고 항목  
 [Visual Studio 명령 테이블(.Vsct) 파일](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
