---
title: 레거시 언어 서비스 명령 가로채기 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5206bced8b4bfae32498434765e5c3f61801b386
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707446"
---
# <a name="intercepting-legacy-language-service-commands"></a>레거시 언어 서비스 명령 가로채기
을 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]사용하면 텍스트 뷰가 달리 처리할 언어 서비스 가로채기 명령을 사용할 수 있습니다. 이 기능은 텍스트 보기에서 관리하지 않는 언어별 동작에 유용합니다. 언어 서비스에서 텍스트 보기에 하나 이상의 명령 필터를 추가하여 이러한 명령을 가로챌 수 있습니다.

## <a name="getting-and-routing-the-command"></a>명령 얻기 및 라우팅
 명령 필터는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 특정 문자 시퀀스 또는 키 명령을 모니터링하는 개체입니다. 두 개 이상의 명령 필터를 단일 텍스트 뷰와 연결할 수 있습니다. 각 텍스트 보기는 명령 필터 체인을 유지 관리합니다. 새 명령 필터를 만든 후 해당 텍스트 뷰에 대한 필터를 체인에 추가합니다.

 체인에 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> 명령 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 필터를 추가하려면 에 메서드를 호출합니다. 호출할 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 때 명령 필터가 처리하지 않는 명령을 전달할 수 있는 다른 명령 필터를 반환합니다.

 명령 처리에 대한 다음 옵션이 있습니다.

- 명령을 처리한 다음 체인의 다음 명령 필터에 명령을 전달합니다.

- 명령을 처리하고 명령을 다음 명령 필터에 전달하지 않습니다.

- 명령을 처리하지 말고 명령을 다음 명령 필터에 전달합니다.

- 명령을 무시합니다. 현재 필터에서 처리하지 말고 다음 필터에 전달하지 마십시오.

  언어 서비스가 처리해야 하는 명령에 대한 자세한 내용은 [언어 서비스 필터에 대한 중요 명령을](../../extensibility/internals/important-commands-for-language-service-filters.md)참조하십시오.
