---
title: 템플릿 정책 및 속성 창 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Properties window, template policy
ms.assetid: 1d8019d3-5e57-47ba-b358-526b0796a63b
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1c67150c5a71a3d70df85669319795a405c60f4a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68156018"
---
# <a name="template-policy-and-the-properties-window"></a>템플릿 정책 및 속성 창
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

프로젝트가 엔터프라이즈 템플릿 프로젝트 내에 포함 되는 경우 해당 enterprise template 프로젝트는 정책을 적용할 수 있습니다. 템플릿 정책은 속성의 기본값을 설정 하 고 속성을 숨기 거 나 속성을 추가 하는 데 사용할 수 있는 제약 시스템이 됩니다.  
  
 템플릿 정책을 사용 하 여 **속성** 창에서 정보 표시를 제어 하는 것은 구현과 다릅니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> . <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 는 구성 요소 수준에서 개체 속성을 처리 하는 반면 템플릿 정책은 솔루션 또는 프로젝트 수준에서 개체 속성을 제한 하는 데 사용할 수 있습니다. 즉,  
  
- 에서 메서드를 구현 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing> 하 여 특정 개체에 대 한 **속성** 창에 표시 되는 내용을 확인 합니다.  
  
- 솔루션 및 프로젝트 수준에서 템플릿 정책을 사용 하 여 이전에 지정 된 개체에 대 한 **속성** 창에 표시 되는 내용을 확인 합니다.  
  
  **솔루션 탐색기** 에서 지정 된 형식의 프로젝트 항목을 선택 하는 경우 템플릿 정책을 사용 하 여 **속성** 창에서 특정 속성을 선택적으로 제한할 수 있습니다. 프로젝트에서 작업 하는 개발 팀의 모든 멤버에 게 유용할 수 있습니다. 예를 들어 템플릿 정책을 사용 하면 개발자에 대 한 모든 연결 문자열 정보를 데이터베이스에 설정 하 고 연결 문자열을 읽기 전용으로 설정할 수 있습니다. 이러한 방식으로 각 개발자가 데이터 액세스에 올바른 경로를 사용 하도록 하는 간단한 방법을 제공할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPerPropertyBrowsing>   
 [속성 확장](../../extensibility/internals/extending-properties.md)
