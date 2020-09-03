---
title: '방법: UML 모델의 변경 내용에 응답 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: f0300371-9cac-4def-a3f5-7d7b62dcd6f3
caps.latest.revision: 3
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: cf88661f9ec15e1a3a25e7eb6a40bbd82335a7f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75918715"
---
# <a name="how-to-respond-to-changes-in-a-uml-model"></a>방법: UML 모델의 변경 내용에 응답
Visual Studio의 UML 모델에서 변경이 발생할 때마다 실행되는 코드를 작성할 수 있습니다. 사용자 및 다른 Visual Studio 확장에 의해 직접 수행된 변경에 대해 똑같이 반응합니다. UML 모델을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

> [!WARNING]
> 이러한 방법은 UML API에서 지원되지 않습니다. Visual Studio의 이후 버전에서 작동하지 않을 수 있습니다.

## <a name="see-also"></a>관련 항목
 [UML 모델 탐색](../modeling/navigate-the-uml-model.md) [이벤트 처리기 모델 외부에서 변경 내용 전파](../modeling/event-handlers-propagate-changes-outside-the-model.md)
 