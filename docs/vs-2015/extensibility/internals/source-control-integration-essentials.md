---
title: 원본 제어 통합 Essentials | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- Source Control Integration, essentials
- Source Control Integration,overview
- essentials, Source Control Integration
ms.assetid: 442057cb-fd54-4283-96f8-2f6dc8bf2de7
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: b9189b647baa29d72975f84172696ecb54cd7f87
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68183428"
---
# <a name="source-control-integration-essentials"></a>소스 제어 통합 필수 항목
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 는 기본 기능을 제공 하 고 소스 제어 플러그 인 API (이전에는 MSSCCI API)를 사용 하 여 구축 된 소스 제어 플러그 인과, 보다 강력한 기능을 제공 하는 VSPackage 기반 소스 제어 통합 솔루션을 사용 하 여 두 가지 형식의 원본 제어 통합을 지원 합니다.  
  
## <a name="source-control-plug-in"></a>소스 제어 플러그 인  
 소스 제어 플러그 인은 소스 제어 플러그 인 API를 구현 하는 DLL로 작성 됩니다. 등록 및 소스 제어 통합 기능은 API를 통해 제공 됩니다. 이 방법은 소스 제어 VSPackage 구현 하기 쉬울 뿐만 아니라 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 대부분의 소스 제어 작업에 UI (사용자 인터페이스)를 사용 합니다.  
  
 소스 제어 플러그 인 API를 사용 하 여 소스 제어 플러그 인을 구현 하려면 다음 단계를 수행 합니다.  
  
1. [소스 제어 플러그](../../extensibility/source-control-plug-ins.md)인에 지정 된 함수를 구현 하는 DLL을 만듭니다.  
  
2. [방법: 소스 제어 플러그 인 설치](../../extensibility/internals/how-to-install-a-source-control-plug-in.md)에 설명 된 대로 적절 한 레지스트리 항목을 만들어 DLL을 등록 합니다.  
  
3. 도우미 UI를 만들고 소스 제어 어댑터 패키지 (소스 제어 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 플러그 인을 통해 소스 제어 기능을 처리 하는 구성 요소)에서 메시지가 표시 되 면 표시 합니다.  
  
   자세한 내용은 [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)를 참조 하세요.  
  
## <a name="source-control-vspackage"></a>소스 제어 VSPackage  
 소스 제어 VSPackage 구현을 사용 하 여 소스 제어 UI에 대 한 사용자 지정 대체를 개발할 수 있습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] . 이 방법은 소스 제어 통합에 대 한 완전 한 제어를 제공 하지만,이를 위해 UI 요소를 제공 하 고, 다른 경우에는 플러그 인 방식으로 제공 되는 소스 제어 인터페이스를 구현 해야 합니다.  
  
 소스 제어 VSPackage을 구현 하려면 다음을 수행 해야 합니다.  
  
1. [등록 및 선택](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)에 설명 된 대로 고유한 소스 제어 VSPackage을 만들고 등록 합니다.  
  
2. 기본 소스 컨트롤 UI를 사용자 지정 UI로 바꿉니다. [사용자 지정 사용자 인터페이스](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)를 참조 하세요.  
  
3. 사용할 문자 모양을 지정 하 고 **솔루션 탐색기** 문자 모양 이벤트를 처리 합니다. [문자 모양 컨트롤](../../extensibility/internals/glyph-control-source-control-vspackage.md)을 참조 하세요.  
  
4. 쿼리 편집 쿼리 [저장](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)에 표시 된 것 처럼 쿼리 편집 및 쿼리 저장 이벤트를 처리 합니다.  
  
   자세한 내용은 [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)를 참조 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [설명은](../../extensibility/internals/source-control-integration-overview.md)   
 [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)   
 [소스 제어 VSPackage 만들기](../../extensibility/internals/creating-a-source-control-vspackage.md)
