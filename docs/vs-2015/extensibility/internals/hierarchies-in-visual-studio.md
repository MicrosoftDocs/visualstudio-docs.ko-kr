---
title: 계층 구조
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 22943d3049ff0e24d00c7c29750e7dcd0efaf846
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158365"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio의 계층 구조
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]IDE (통합 개발 환경)는 프로젝트를 *계층 구조로*표시 합니다. IDE에서 계층은 노드 트리로, 각 노드에는 연관 된 속성 집합이 있습니다. *프로젝트 계층 구조* 는 프로젝트의 항목, 항목의 관계 및 항목의 관련 속성 및 명령을 포함 하는 컨테이너입니다.

 에서는 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 계층 인터페이스를 사용 하 여 프로젝트 계층 구조를 관리 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> 합니다. <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy>인터페이스는 프로젝트 항목에서 호출 하는 명령을 표준 명령 처리기 대신 적절 한 계층 창으로 리디렉션합니다.

## <a name="project-hierarchies"></a>프로젝트 계층 구조
 각 프로젝트 계층에는 보고 편집할 수 있는 항목이 포함 되어 있습니다. 이러한 항목은 프로젝트 형식에 따라 달라 집니다. 예를 들어 데이터베이스 프로젝트에는 저장 프로시저, 데이터베이스 뷰 및 데이터베이스 테이블이 포함 될 수 있습니다. 반면, 프로그래밍 언어 프로젝트에는 비트맵 및 대화 상자에 대 한 소스 파일 및 리소스 파일이 포함 될 가능성이 높습니다. 계층은 중첩 될 수 있으므로 프로젝트 계층 구조를 만들 때 유연성을 추가할 수 있습니다.

 새 프로젝트 형식을 만들면 프로젝트 형식에서 편집할 수 있는 전체 항목 집합을 제어 합니다. 그러나 프로젝트에는 편집 지원이 없는 항목이 포함 될 수 있습니다. 예를 들어 Visual C++ HTML 파일 형식에 대 한 사용자 지정 편집기를 제공 하지 않는 경우에도 Visual C++ 프로젝트는 HTML 파일을 포함할 수 있습니다.

 계층은 포함 된 항목의 지 속성을 관리 합니다. 계층 구조를 구현 하려면 계층 내에 있는 항목의 지 속성에 영향을 주는 특수 속성을 제어 해야 합니다. 예를 들어 항목이 파일 대신 리포지토리에 있는 개체를 나타내는 경우 계층 구조 구현은 해당 개체의 지 속성을 제어 해야 합니다. IDE 자체는 계층에서 사용자 입력에 대 한 준수 항목을 저장 하도록 지시 하지만 IDE는 해당 항목을 저장 하는 데 필요한 작업을 제어 하지 않습니다. 대신 프로젝트를 제어 합니다.

 사용자가 편집기에서 항목을 열면 해당 항목을 제어 하는 계층이 선택 되 고 활성 계층이 됩니다. 선택한 계층은 항목에 대해 작업을 수행할 수 있는 명령 집합을 결정 합니다. 이러한 방식으로 사용자 포커스를 추적 하면 계층 구조에서 사용자의 현재 컨텍스트를 반영할 수 있습니다.

## <a name="see-also"></a>관련 항목
 IDE의 [프로젝트 형식](../../extensibility/internals/project-types.md) [선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md) [VSSDK Samples](../../misc/vssdk-samples.md) .
