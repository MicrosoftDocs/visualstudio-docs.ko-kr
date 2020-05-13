---
title: 비주얼 스튜디오의 계층 구조 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- hierarchies, Visual Studio IDE
- IDE, hierarchies
ms.assetid: 0a029a7c-79fd-4b54-bd63-bd0f21aa8d30
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cdbb8a0e58f6b1e5bc6e32f8c319d1480c4db4b5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708186"
---
# <a name="hierarchies-in-visual-studio"></a>Visual Studio의 계층 구조
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 통합 개발 환경(IDE)은 프로젝트를 *계층 구조로*표시합니다. IDE에서 계층 구조는 각 노드에 연결된 속성 집합이 있는 노드 트리입니다. *프로젝트 계층 구조는* 프로젝트의 항목, 항목의 관계 및 항목의 관련 속성 및 명령을 포함하는 컨테이너입니다.

 에서 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]계층 인터페이스를 사용하여 프로젝트 계층 구조를 <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>관리 합니다. 인터페이스는 <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> 프로젝트 항목에서 호출하는 명령을 표준 명령 처리기 대신 적절한 계층 창으로 리디렉션합니다.

## <a name="project-hierarchies"></a>프로젝트 계층 구조
 각 프로젝트 계층에는 보고 편집할 수 있는 항목이 포함되어 있습니다. 이러한 항목은 프로젝트 유형에 따라 다릅니다. 예를 들어 데이터베이스 프로젝트에는 저장된 프로시저, 데이터베이스 뷰 및 데이터베이스 테이블이 포함될 수 있습니다. 반면 프로그래밍 언어 프로젝트에는 비트맵 및 대화 상자에 대한 소스 파일및 리소스 파일이 포함될 수 있습니다. 계층구조를 중첩할 수 있으므로 프로젝트 계층 구조를 만들 때 유연성을 추가할 수 있습니다.

 새 프로젝트 유형을 만들 때 프로젝트 유형은 편집할 수 있는 전체 항목 집합을 제어합니다. 그러나 프로젝트에는 편집 지원이 없는 항목이 포함될 수 있습니다. 예를 들어 Visual C++ 프로젝트에는 HTML 파일 형식에 대한 사용자 지정 편집기도 제공하지 않더라도 Visual C++ 프로젝트에 HTML 파일이 포함될 수 있습니다.

 계층구조는 포함된 항목의 지속성을 관리합니다. 계층 구조의 구현은 계층 내의 항목의 지속성에 영향을 주는 특수 속성을 제어해야 합니다. 예를 들어 항목이 파일 대신 리포지토리의 개체를 나타내는 경우 계층 구현은 해당 개체의 지속성을 제어해야 합니다. IDE 자체는 사용자 입력에 따라 항목을 저장하도록 계층 구조를 지시하지만 IDE는 해당 항목을 저장하는 데 필요한 작업을 제어하지 않습니다. 대신 프로젝트가 제어됩니다.

 사용자가 편집기에서 항목을 열면 해당 항목을 제어하고 활성 계층이 되는 계층이 됩니다. 선택한 계층 구조는 항목에 대해 작동할 수 있는 명령 집합을 결정합니다. 이러한 방식으로 사용자 포커스를 추적하면 계층 구조가 사용자의 현재 컨텍스트를 반영할 수 있습니다.

## <a name="see-also"></a>참조
- [프로젝트 형식](../../extensibility/internals/project-types.md)
- [IDE의 선택 및 통화](../../extensibility/internals/selection-and-currency-in-the-ide.md)
- [VSSDK 샘플](https://github.com/Microsoft/VSSDK-Extensibility-Samples)
