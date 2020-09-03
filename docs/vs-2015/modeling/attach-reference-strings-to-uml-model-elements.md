---
title: UML 모델 요소에 참조 문자열 연결 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
helpviewer_keywords:
- UML - extending, reference strings
ms.assetid: 15dbed99-efce-42fe-a768-714a5804e7d1
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7726379258ef474b57f1ca4a924413cd93cf80bb
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72672787"
---
# <a name="attach-reference-strings-to-uml-model-elements"></a>UML 모델 요소에 참조 문자열 연결
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모델 요소에 임의 문자열을 연결하는 코드를 작성할 수 있습니다. 예를 들어 문자열은 URI, 캐시된 계산 결과 또는 다른 모델의 요소에 대한 ModelBus 참조일 수 있습니다. 각 문자열은 IReference 개체에 포함됩니다. 개수에 관계없이 IReference 개체를 각 모델 요소에 연결할 수 있습니다.

 각 IReference 개체에는 이름이 있습니다. 이 이름을 사용하여 참조 값을 해석하는 방법을 나타낼 수 있습니다. 예를 들어 이름을 "URI"로 설정하여 값이 URI로 해석되어야 함을 나타낼 수 있습니다. 모델링 도구에서 사용하는 몇 가지 미리 정의된 참조 이름 값이 있습니다.

## <a name="attaching-a-reference-to-an-ielement"></a>IElement에 참조 연결
 다음 메서드를 사용하려면 아래 항목에 대한 참조를 추가해야 합니다.

 Microsoft.VisualStudio.ArchitectureTools.Extensibility.dll

 코드에 다음 지시어를 삽입해야 합니다.

 `using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Uml;`

|메서드 호출|설명|
|-----------------|-----------------|
|`element.AddReference (nameString, valueString, duplicatesAllowed)`|지정된 이름 및 값 문자열을 사용하여 `IReference`를 만들고 `element`에 연결합니다. `IReference`를 반환합니다.<br /><br /> `duplicatesAllowed`가 false이고 동일한 이름을 가진 `IReference`가 이미 `element`에 연결되어 있으면 예외가 발생합니다.|
|`element.GetReferences(name)`|지정된 `IReference`을 가진, `element`에 연결된 `name` 개체를 모두 반환합니다.|
|`element.DeleteAllReferences(name)`|지정된 이름을 가진, 요소에 연결된 `IReference` 개체를 모두 삭제합니다.|
|`reference.Delete()`|이 `IReference`를 삭제합니다.|
|`ReferenceConstants.WorkItem`|작업 항목 참조에 이름을 지정하는 데 사용되는 값입니다.|

## <a name="see-also"></a>관련 항목
 [작업 항목 링크 처리기 정의](../modeling/define-a-work-item-link-handler.md) [UML API를 사용 하 여](../modeling/programming-with-the-uml-api.md) [모델링 확장 프로그램 정의 및 설치](../modeling/define-and-install-a-modeling-extension.md)
