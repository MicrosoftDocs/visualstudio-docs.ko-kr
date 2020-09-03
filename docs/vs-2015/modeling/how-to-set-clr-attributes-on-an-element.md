---
title: '방법: 요소에 CLR 특성 설정 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
ms.assetid: b3db3c74-920c-4701-9544-6f75cbe8b7c9
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ad9175729451c82fca3b61d06e449edaf8cf38
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662547"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>방법: 요소에 CLR 특성 설정
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

사용자 지정 특성은 도메인 요소, 도형, 연결선 및 다이어그램에 추가할 수 있는 특수 한 특성입니다. 클래스에서 상속 되는 특성을 추가할 수 있습니다 `System.Attribute` .

### <a name="to-add-a-custom-attribute"></a>사용자 지정 특성을 추가 하려면

1. **DSL 탐색기**에서 사용자 지정 특성을 추가 하려는 요소를 선택 합니다.

2. **속성** 창에서 **사용자 지정 특성** 속성 옆에 있는 찾아보기 (**...**) 아이콘을 클릭 합니다.

     **특성 편집** 대화 상자가 열립니다.

3. **이름** 열에서을 클릭 **\<add attribute>** 하 고 특성의 이름을 입력 합니다. Enter 키를 누릅니다.

4. 특성 이름 아래의 줄에 괄호가 표시 됩니다. 이 줄에서 특성에 대 한 매개 변수 형식 (예:)을 입력 한 `string` 다음 enter 키를 누릅니다.

5. **이름 속성** 열에 적절 한 이름 (예:)을 입력 `MyString` 합니다.

6. **확인**을 클릭합니다.

     이제 **사용자 지정 특성** 속성이 다음 형식으로 특성을 표시 합니다.

     `[`*AttributeName* `(` *ParameterName* `=` *유형*`)]`

## <a name="see-also"></a>관련 항목
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
