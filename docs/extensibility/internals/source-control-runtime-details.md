---
title: 소스 제어 런타임 세부 정보 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 92ce5e822ec7360b3b1a4010d250a4349443c142
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705047"
---
# <a name="source-control-runtime-details"></a>소스 제어 런타임 세부 정보
사용자가 프로젝트에 파일을 소스 제어에 추가하거나 마법사와 같은 자동화 컨트롤러를 통해 프로젝트를 소스 제어에 추가할 때 프로젝트가 소스 제어에 추가됩니다. 프로젝트는 소스 제어하에 있음을 자체적으로 지정하지 않습니다. 소스 제어를 지원하지만 수동으로 추가해야 합니다.

## <a name="registering-with-a-source-control-package"></a>소스 제어 패키지에 등록
 프로젝트의 파일이 소스 제어에 추가되면 환경은 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> 소스 제어 시스템에서 쿠키로 사용되는 네 개의 불투명 문자열을 제공하도록 호출합니다. 이러한 문자열을 프로젝트 파일에 저장합니다. 이러한 문자열은 를 호출하여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>프로젝트 형식을 시작할 때 소스 제어 스텁(소스 제어 패키지를 관리하는 Visual Studio 구성 요소)에 전달되어야 합니다. 그러면 적절한 소스 제어 패키지를 로드하고 `IVsSccManager2::RegisterSccProject`호출을 의 구현으로 전달합니다.

## <a name="see-also"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>
- [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
