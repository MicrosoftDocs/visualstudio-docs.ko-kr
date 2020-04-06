---
title: 프로젝트 모델의 요소 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], implementation considerations
- project models
- projects [Visual Studio SDK], elements
ms.assetid: a1dbe0dc-68da-45d7-8704-5b43ff7e4fc4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cf847e35878dc84bb32fe81053c01c23e565fc4c
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708532"
---
# <a name="elements-of-a-project-model"></a>프로젝트 모델의 요소
모든 프로젝트의 인터페이스와 구현은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 기본 구조인 프로젝트 유형에 대한 프로젝트 모델을 공유합니다. 개발 중인 VSPackage인 프로젝트 모델에서 설계 결정을 준수하고 IDE에서 제공하는 전역 기능과 함께 작동하는 개체를 만듭니다. 예를 들어 프로젝트 항목이 유지되는 방법을 제어하지만 파일을 유지해야 한다는 알림은 제어하지 않습니다. 사용자가 열린 프로젝트 항목에 포커스를 배치하고 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 메뉴 모음의 **파일** 메뉴에서 **저장을** 선택하면 프로젝트 유형 코드는 IDE에서 명령을 가로채 파일을 유지한 다음 파일이 더 이상 변경되지 않는다는 알림을 IDE로 다시 보내야 합니다.

 VSPackage는 IDE 인터페이스에 대한 액세스를 제공하는 서비스를 통해 IDE와 상호 작용합니다. 예를 들어 특정 서비스를 통해 명령을 모니터링하고 라우팅하고 프로젝트에서 선택한 항목에 대한 컨텍스트 정보를 제공합니다. VSPackage에 필요한 모든 전역 IDE 기능은 서비스에서 제공됩니다. 서비스에 대한 자세한 내용은 [서비스 받기 방법을](../../extensibility/how-to-get-a-service.md)참조하십시오.

 기타 구현 고려 사항:

- 단일 프로젝트 모델에는 두 개 이상의 프로젝트 유형이 포함될 수 있습니다.

- 프로젝트 유형 및 수행 프로젝트 팩터는 GUID에 독립적으로 등록됩니다.

- 사용자가 UI를 통해 새 프로젝트를 만들 때 새 프로젝트 파일을 초기화하려면 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 각 프로젝트에 템플릿 파일 또는 마법사가 있어야 합니다. 예를 들어 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 템플릿은 결국 .vcproj 파일이 되는 것을 초기화합니다.

  다음 그림에서는 일반적인 프로젝트 구현을 구성하는 기본 인터페이스, 서비스 및 개체를 보여 줍니다. 응용 프로그램 도우미, `HierUtil7`을 사용하여 기본 개체 및 기타 프로그래밍 상용구를 만들 수 있습니다. 응용 프로그램 도우미에 `HierUtil7` 대한 자세한 내용은 [HierUtil7 프로젝트 클래스 를 사용하여 프로젝트 유형(C++)을 구현합니다.](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)

  ![비주얼 스튜디오 프로젝트 모델 그래픽](../../extensibility/internals/media/vsprojectmodel.gif "대 프로젝트 모델") 프로젝트 모델

  이전 다이어그램에 나열된 인터페이스 및 서비스 및 다이어그램에 포함되지 않은 기타 선택적 인터페이스에 대한 자세한 내용은 [프로젝트 모델 핵심 구성 요소를](../../extensibility/internals/project-model-core-components.md)참조하십시오.

  프로젝트는 명령을 지원할 수 있으므로 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 명령 컨텍스트 GUID를 통해 명령 라우팅에 참여할 인터페이스를 구현해야 합니다.

## <a name="see-also"></a>참조
- [검사 목록: 새 프로젝트 유형 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [HierUtil7 프로젝트 클래스를 사용하여 프로젝트 유형(C++)을 구현합니다.](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [프로젝트 모델 핵심 구성요소](../../extensibility/internals/project-model-core-components.md)
- [프로젝트 팩터리를 사용하여 프로젝트 인스턴스 생성](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [방법: 서비스 받기](../../extensibility/how-to-get-a-service.md)
- [프로젝트 유형 만들기](../../extensibility/internals/creating-project-types.md)
