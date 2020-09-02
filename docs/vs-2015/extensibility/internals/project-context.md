---
title: 프로젝트 컨텍스트 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], opening items
ms.assetid: d1803f4a-24eb-44b0-b5d2-cb40c15534be
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d4ee4da5fdea63cf1bdd33554c72f6dac30d0334
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62429940"
---
# <a name="project-context"></a>프로젝트 컨텍스트
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

사용자가 프로젝트 및 프로젝트 항목을 추가 하거나 사용할 때 IDE는 프로젝트 컨텍스트의 개념을 사용 하 여 다양 한 작업을 수행 해야 하는 방법을 결정 합니다.  
  
 일반적으로 파일은 사용자가 **새 프로젝트** 명령을 선택 하거나 **파일** 메뉴에서 **프로젝트 열기** 명령을 선택 하 여 명시적으로 만드는 표준 프로젝트 개체입니다. 이러한 경우 파일은 프로젝트의 컨텍스트에서 만들어지고 열리며 프로젝트 형식은 문서 편집을 위한 컨텍스트를 정의 합니다.  
  
 일부 프로젝트는 매우 다양 한 컨텍스트를 제공 합니다. 예를 들어 프로젝트는 데이터 바인딩에 대해 프로젝트 범위, 프로그래밍 방식 네임 스페이스 또는 프로젝트 범위 데이터베이스 연결을 관리 합니다. 사용자는 솔루션 탐색기에 표시 되는 프로젝트 항목과 같은 특정 프로젝트 개체를 사용 하 여 파일 또는 데이터베이스 연결을 직접 열 수 있습니다.  
  
 다른 경우에는 항목의 프로젝트 컨텍스트가 명시적으로 지정 되지 않습니다. 예를 들어 사용자가 **파일 메뉴에서** **기존 파일 열기** 명령을 선택 하 여 파일을 열거나, 디버거가 파일에 대해 작동 하거나, 사용자가 **찾기 및 바꾸기** 대화 상자에서 **파일에서 찾기** 명령을 클릭할 때 항목의 컨텍스트를 사용할 수 없습니다. 이러한 상황을 처리 하기 위해 IDE는를 호출 하 여 문서를 여는 데 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument> 가장 적합 한 프로젝트를 찾는 프로세스를 관리 합니다.  
  
## <a name="see-also"></a>관련 항목  
 [프로젝트 우선 순위](../../extensibility/internals/project-priority.md)   
 [프로젝트 및 프로젝트 항목 템플릿 추가](../../extensibility/internals/adding-project-and-project-item-templates.md)
