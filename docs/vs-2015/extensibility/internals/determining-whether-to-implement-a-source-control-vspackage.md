---
title: 소스 제어 VSPackage을 구현할지 여부 결정 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control packages, about source control packages
ms.assetid: 60b3326e-e7e2-4729-95fc-b682e7ad5c99
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cff53700dcd6a80f841108d5a2b486dcb0ba7a11
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196804"
---
# <a name="determining-whether-to-implement-a-source-control-vspackage"></a>소스 제어 VSPackage를 구현할지 여부 결정
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

이 섹션에서는 소스 제어 솔루션을 확장 하기 위해 소스 제어 플러그 인 및 소스 제어 Vspackage의 선택 항목을 대해 중점적 하 고 적절 한 통합 경로 선택에 대 한 광범위 한 지침을 제공 합니다.  
  
## <a name="small-source-control-solution-with-limited-resources"></a>리소스를 제한 하는 작은 소스 제어 솔루션  
 리소스를 제한 하 고 소스 제어 패키지를 작성 하는 오버 헤드로 부담이 수 없는 경우 소스 제어 플러그 인 API 기반 플러그 인을 만들 수 있습니다. 이를 통해 소스 제어 패키지와 함께 작업할 수 있으며 요청 시 소스 제어 플러그 인과 패키지 간을 전환할 수 있습니다. 자세한 내용은 [등록 및 선택](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)을 참조 하세요.  
  
## <a name="large-source-control-solution-with-a-rich-feature-set"></a>풍부한 기능 집합을 포함 하는 대량 소스 제어 솔루션  
 소스 제어 플러그 인 API를 사용 하 여 적절 하 게 캡처하지 않는 풍부한 소스 제어 모델을 제공 하는 소스 제어 솔루션을 구현 하려면 원본 제어 패키지를 통합 경로로 사용 하는 것이 좋습니다. 이는 소스 제어 이벤트를 사용자 지정 방식으로 처리할 수 있도록 소스 제어 어댑터 패키지를 (소스 제어 플러그 인과 통신 하 고 기본 소스 제어 UI를 제공 하는) 원하는 경우에 특히 적용 됩니다. 적절 한 소스 제어 UI가 이미 있고에서 해당 환경을 유지 하려는 경우 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 원본 제어 패키지 옵션을 사용 하면 됩니다. 소스 제어 패키지는 제네릭이 아니고 IDE 에서만 사용 하도록 디자인 되었습니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 소스 제어 논리 및 UI에 대해 유연 하 고 다양 한 제어를 제공 하는 소스 제어 솔루션을 구현 하려면 소스 제어 패키지 통합 경로를 사용 하는 것이 좋습니다. 다음과 같습니다.  
  
1. 사용자 고유의 소스 제어 VSPackage ( [등록 및 선택](../../extensibility/internals/registration-and-selection-source-control-vspackage.md)참조)를 등록 합니다.  
  
2. 기본 소스 제어 UI를 사용자 지정 UI로 바꿉니다 ( [사용자 지정 사용자 인터페이스](../../extensibility/internals/custom-user-interface-source-control-vspackage.md)참조).  
  
3. 사용할 문자 모양을 지정 하 고 솔루션 탐색기 문자 모양 이벤트를 처리 합니다 ( [문자 모양 컨트롤](../../extensibility/internals/glyph-control-source-control-vspackage.md)참조).  
  
4. 쿼리 편집 및 쿼리 저장 이벤트를 처리 합니다 (쿼리 [편집 쿼리 저장](../../extensibility/internals/query-edit-query-save-source-control-vspackage.md)참조).  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인 만들기](../../extensibility/internals/creating-a-source-control-plug-in.md)
