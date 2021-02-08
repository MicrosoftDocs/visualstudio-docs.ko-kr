---
title: 레거시 언어 서비스 명령 가로채기 | Microsoft Docs
description: Visual Studio에서 명령 필터를 사용 하 여 레거시 언어 서비스 명령을 가로채서 언어별 동작을 추가 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, intercepting language service
- language services, intercepting commands
ms.assetid: eea69f03-349c-44bb-bd4f-4925c0dc3e55
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: c6a759f0cef7329d14d7d1472d38f662c0206448
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99839796"
---
# <a name="intercepting-legacy-language-service-commands"></a>레거시 언어 서비스 명령 가로채기
를 사용 하 여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 언어 서비스에서 텍스트 뷰가 처리 하는 명령을 가로챌 수 있습니다. 이는 텍스트 뷰에서 관리 하지 않는 언어 관련 동작에 유용 합니다. 언어 서비스의 텍스트 뷰에 하나 이상의 명령 필터를 추가 하 여 이러한 명령을 가로챌 수 있습니다.

## <a name="getting-and-routing-the-command"></a>명령 가져오기 및 라우팅
 명령 필터는 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 특정 문자 시퀀스 또는 키 명령을 모니터링 하는 개체입니다. 단일 텍스트 뷰를 사용 하 여 둘 이상의 명령 필터를 연결할 수 있습니다. 각 텍스트 보기는 명령 필터 체인을 유지 합니다. 새 명령 필터를 만든 후에는 해당 텍스트 보기의 체인에 필터를 추가 합니다.

 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>에서 메서드를 호출 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> 하 여 명령 필터를 체인에 추가 합니다. 를 호출 하는 경우는 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 명령 필터가 처리 하지 않는 명령을 전달할 수 있는 다른 명령 필터를 반환 합니다.

 명령 처리에 대해 다음과 같은 옵션을 사용할 수 있습니다.

- 명령을 처리 한 다음 체인의 다음 명령 필터에 명령을 전달 합니다.

- 명령을 처리 하 고 명령을 다음 명령 필터로 전달 하지 않습니다.

- 명령을 처리 하지 않고 명령을 다음 명령 필터에 전달 합니다.

- 명령을 무시 합니다. 현재 필터에서이를 처리 하지 않고 다음 필터에 전달 하지 않습니다.

  언어 서비스에서 처리 해야 하는 명령에 대 한 자세한 내용은 [언어 서비스 필터에 대 한 중요 한 명령](../../extensibility/internals/important-commands-for-language-service-filters.md)을 참조 하세요.
