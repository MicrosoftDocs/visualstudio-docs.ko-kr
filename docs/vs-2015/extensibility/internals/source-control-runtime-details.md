---
title: 소스 제어 런타임 세부 정보 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control [Visual Studio SDK], runtime details
ms.assetid: 1acd30e0-f98c-4bde-b9cd-4076845887df
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bb52770557fa37a14040b686dcdfbf345a713a2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183362"
---
# <a name="source-control-runtime-details"></a>소스 제어 런타임 세부 정보
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자가 프로젝트에서 소스 제어에 파일을 추가 하거나 마법사와 같은 자동화 컨트롤러를 통해 프로젝트를 소스 제어에 추가 합니다. 프로젝트가 소스 제어에서 사용할 수 있도록 지정 되지 않습니다. 원본 제어를 지원 하지만 수동으로 추가 해야 합니다.  
  
## <a name="registering-with-a-source-control-package"></a>소스 제어 패키지에 등록  
 프로젝트의 파일이 소스 제어에 추가 되 면 환경에서는를 호출 하 여 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A> 소스 제어 시스템에서 쿠키로 사용 되는 4 개의 불투명 문자열을 제공 합니다. 이러한 문자열을 프로젝트 파일에 저장 합니다. 이러한 문자열은를 호출 하 여 프로젝트 형식을 시작할 때 소스 제어 스텁 (소스 제어 패키지를 관리 하는 Visual Studio 구성 요소)에 전달 되어야 합니다 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A> . 그러면 적절 한 소스 제어 패키지가 로드 되 고의 구현에 대 한 호출이 전달 `IVsSccManager2::RegisterSccProject` 됩니다.  
  
## <a name="see-also"></a>관련 항목  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccManager2.RegisterSccProject%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsSccProject2.SetSccLocation%2A>   
 [소스 제어 지원](../../extensibility/internals/supporting-source-control.md)
