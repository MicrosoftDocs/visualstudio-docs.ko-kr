---
title: Vspackage 관리 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
caps.latest.revision: 36
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0b56ab490342cfbda9c16408aa0937abd80728c9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68194383"
---
# <a name="managing-vspackages"></a>VSPackage 관리
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

대부분의 경우 프로젝트 및 항목 템플릿이 자동으로 패키지를 등록 하 고 로드 하므로 Vspackage 관리에 대해 걱정할 필요가 없습니다. 그러나 일부 경우에는 패키지를 관리 하기 위해 약간 더 배워야 할 수도 있습니다.  
  
## <a name="using-the-experimental-instance"></a>실험적 인스턴스 사용  
 실험적 인스턴스에 대해 자세히 알아보려면 [실험적 인스턴스](../extensibility/the-experimental-instance.md)를 참조 하세요.  
  
## <a name="registering-and-unregistering-vspackages"></a>VSPackage 등록 및 등록 취소  
 Vspackage 및 다른 유형의 확장을 등록 하 고 등록을 취소 하는 방법을 알아보려면 [Vspackage 등록 및 등록 취소](../extensibility/registering-and-unregistering-vspackages.md)를 참조 하세요.  
  
## <a name="loading-a-vspackage"></a>VSPackage 로드  
 특정 CMDUICONTEXT GUID가 설정 되어 있으면 Vspackage을 autoload로 설정할 수 있습니다. 자세한 내용은 [Vspackage 로드](../extensibility/loading-vspackages.md)를 참조 하세요.  
  
## <a name="using-asyncpackage-to-load-vspackages-in-the-background"></a>AsyncPackage를 사용 하 여 백그라운드에서 Vspackage 로드  
 AsyncPackage 클래스를 사용 하 여 Visual Studio에서 UI 응답성을 개선 하기 위해 백그라운드 스레드에서 패키지를 로드할 수 있습니다. 자세한 내용은 [방법: AsyncPackage를 사용 하 여 배경에 Vspackage 로드를](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)참조 하세요.  
  
## <a name="rule-based-ui-context-for-extensions"></a>확장 프로그램에 대 한 규칙 기반 UI 컨텍스트  
 규칙 기반 UI 컨텍스트를 통해 확장 작성자는 UI 컨텍스트가 활성화 되 고 관련 Vspackage 로드 되는 정확한 조건을 정의할 수 있습니다. 자세한 내용은 [방법: Visual Studio 확장에 대 한 규칙 기반 UI 컨텍스트 사용](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)을 참조 하세요.  
  
## <a name="troubleshooting-vspackages"></a>VSPackage 문제 해결  
 로드 되지 않거나 오류가 발생 하는 Vspackage 문제를 해결 하는 방법에 대 한 자세한 정보 [vspackage](../extensibility/troubleshooting-vspackages.md) 를 확인 하세요.  
  
## <a name="see-also"></a>관련 항목  
 [VSPackages](../extensibility/internals/vspackages.md)
