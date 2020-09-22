---
title: 레거시 언어 Service1 구현 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- language services, managed
ms.assetid: df638f24-166d-4b80-be82-c9c39ca7a556
caps.latest.revision: 19
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 20493991d8e0740ca045f041e2ba94cf3735ad1a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841959"
---
# <a name="implementing-a-legacy-language-service"></a>레거시 언어 서비스 구현
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

MPF (관리 되는 패키지 프레임 워크)의 클래스를 사용 하 여 구문 강조 표시, 중괄호 일치 및 IntelliSense 완료와 같은 다양 한 기능을 지 원하는 레거시 언어 서비스를 구현할 수 있습니다.  
  
 레거시 언어 서비스는 VSPackage의 일부로 구현 되지만 언어 서비스 기능을 구현 하는 최신 방법은 MEF 확장을 사용 하는 것입니다. 언어 서비스를 구현 하는 새로운 방법에 대해 자세히 알아보려면 [편집기 및 언어 서비스 확장](../../extensibility/editor-and-language-service-extensions.md)을 참조 하세요.  
  
> [!NOTE]
> 가능한 한 빨리 새 편집기 API를 사용 하는 것이 좋습니다. 이렇게 하면 언어 서비스의 성능이 향상 되 고 새 편집기 기능을 활용할 수 있습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [레거시 언어 서비스 개요](../../extensibility/internals/legacy-language-service-overview.md)  
 MPF에서 지원 되는 언어 서비스 기능에 대 한 개요입니다.  
  
 [레거시 언어 서비스 구현](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 MPF를 사용 하 여 언어 서비스를 구현 하는 데 필요한 사항을 설명 합니다.  
  
 [레거시 언어 서비스 등록](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 에 MPF 기반 언어 서비스를 등록 하는 데 필요한 단계에 대해 설명 합니다 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] .  
  
 [레거시 언어 서비스 파서 및 검사기](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 MPF를 사용 하 여 언어 서비스의 모든 기능을 구현 하는 데 필요한 두 개의 파서를 설명 합니다.  
  
 [연습: 레거시 언어 서비스 만들기](../../extensibility/internals/walkthrough-creating-a-legacy-language-service.md)  
 VSPackage에서 MPF 언어 서비스를 구현 하는 데 필요한 기본 단계를 제공 합니다.  
  
 [연습: 설치된 코드 조각 목록 가져오기(레거시 구현)](../../extensibility/internals/walkthrough-getting-a-list-of-installed-code-snippets-legacy-implementation.md)  
 설치 된 코드 조각 목록을 검색 하는 방법을 보여 줍니다.  
  
 [레거시 언어 서비스 기능](../../extensibility/internals/legacy-language-service-features1.md)  
 MPF를 사용 하 여 언어 서비스의 모든 기능을 구현 하기 위해 수행 해야 하는 작업을 자세히 설명 하는 항목에 대 한 링크를 제공 합니다.
