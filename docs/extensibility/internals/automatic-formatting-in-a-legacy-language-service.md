---
title: 레거시 언어 서비스의 자동 서식 지정 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services, automatic formatting
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a11e9c1fdef60e71f46cee9986d925e876dcac35
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709986"
---
# <a name="automatic-formatting-in-a-legacy-language-service"></a>레거시 언어 서비스의 자동 서식 지정
자동 서식을 사용하면 사용자가 알려진 코드 구문 입력을 시작할 때 언어 서비스가 코드 조각을 자동으로 삽입합니다.

## <a name="automatic-formatting-behavior"></a>자동 서식 지정 동작
 예를 들어 *if를*입력할 때 언어 서비스가 일치하는 중괄호를 자동으로 삽입하거나 ENTER 키를 누르면 언어 서비스는 앞줄이 새 범위를 열어주는지 여부에 따라 새 줄에 삽입 지점을 적절한 들여쓰기 수준으로 강제합니다.

 언어 서비스의 나머지 부분에 사용되는 명령 필터는 자동 서식 지정에도 사용할 수 있습니다. 을 호출하여 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace%2A>일치하는 중괄호를 강조 표시할 수도 있습니다.

## <a name="see-also"></a>참조
- [레거시 언어 서비스 개발](../../extensibility/internals/developing-a-legacy-language-service.md)
