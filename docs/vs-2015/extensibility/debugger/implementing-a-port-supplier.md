---
title: 포트 공급자 구현 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ffa6daa20c08bd236657c88e762b2f453554cb74
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152681"
---
# <a name="implementing-a-port-supplier"></a>포트 공급자 구현
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

포트 공급자는 요청 시 포트를 SDM (세션 디버그 관리자)에 제공 합니다. 비 DCOM 컴퓨터를 디버깅할 때 또는 새 장치를 지원 해야 하는 경우 포트 공급자를 구현 해야 합니다. 예를 들어 휴대폰에 대 한 디버깅을 제공 하기 위해 휴대폰에서 실행 되는 프로세스와 프로그램을 열거 하 고 휴대폰에 연결 되는 포트를 제공 하는 포트 공급자를 구현할 수 있습니다.  
  
 Windows 기반 컴퓨터 (원격 디버깅 포함)에서 프로그램을 디버깅 하는 경우 Visual Studio는 네이티브 및 CLR (공용 언어 런타임) 프로세스를 위한 포트 공급자를 제공 하므로 이러한 경우에 자체 포트 공급자를 구현할 필요가 없습니다.  
  
## <a name="in-this-section"></a>섹션 내용  
 [포트 공급자 구현 및 등록](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 SDM이 포트 공급자 및 해당 포트와 상호 작용 하는 방법에 대해 설명 합니다.  
  
 [필요한 포트 공급자 인터페이스](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 포트 공급자를 얻기 위해 구현 해야 하는 인터페이스를 문서화 합니다.  
  
## <a name="related-sections"></a>관련 섹션  
 [디버거 개념](../../extensibility/debugger/debugger-concepts.md)  
 주요 디버깅 아키텍처 개념을 설명 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [Visual Studio 디버거 확장성](../../extensibility/debugger/visual-studio-debugger-extensibility.md)
