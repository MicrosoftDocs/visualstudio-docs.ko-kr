---
title: 템플릿 정책 및 속성 창 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 08ed6f416441d06767661e63b5e32454dbe07f93
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704669"
---
# <a name="template-policy-and-the-properties-window"></a>템플릿 정책 및 속성 창
프로젝트가 엔터프라이즈 템플릿 프로젝트 내에 포함되어 있으면 해당 엔터프라이즈 템플릿 프로젝트가 정책을 적용할 수 있습니다. 템플릿 정책은 속성에 대한 기본값을 설정하고, 속성을 숨기고, 속성을 추가하는 등의 데 사용할 수 있는 구속 시스템이 됩니다.

 템플릿 정책을 사용하여 **속성** 창에서 정보 표시를 제어하는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>것은 을 구현하는 데 다릅니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>구성 요소 수준에서 개체 속성을 처리하는 반면 템플릿 정책을 사용하여 솔루션 또는 프로젝트 수준에서 개체 속성을 제한할 수 있습니다. 다른 말로 하면

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 메서드를 구현하여 특정 개체에 대한 **속성** 창에 표시되는 내용을 결정합니다.

- 솔루션 및 프로젝트 수준에서 템플릿 정책을 사용하여 이전에 지정된 개체의 **속성** 창에 표시되는 내용을 결정합니다.

  **솔루션 탐색기에서** 지정된 형식의 프로젝트 항목이 선택되어 있을 때 템플릿 정책을 사용하여 **속성** 창에서 특정 속성을 선택적으로 제한하면 프로젝트에서 작업하는 개발 팀의 모든 구성원에게 도움이 될 수 있습니다. 예를 들어 템플릿 정책을 사용하여 개발자를 위해 데이터베이스의 모든 연결 문자열 정보를 설정하고 연결 문자열을 읽기 전용으로 만들 수 있습니다. 이러한 방식으로 각 개발자가 데이터 액세스에 올바른 경로를 사용하도록 보장하는 간단한 방법을 제공할 수 있습니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>
- [속성 확장](../../extensibility/internals/extending-properties.md)
