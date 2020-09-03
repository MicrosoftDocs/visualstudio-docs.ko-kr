---
title: 프로젝트 모델의 요소 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80708532"
---
# <a name="elements-of-a-project-model"></a>프로젝트 모델의 요소
에서 모든 프로젝트의 인터페이스와 구현은 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 기본 구조를 공유 합니다. 프로젝트 형식에 대 한 프로젝트 모델입니다. 개발 중인 VSPackage 프로젝트 모델에서 디자인 결정을 따르고 IDE에서 제공 하는 전역 기능과 함께 작동 하는 개체를 만듭니다. 예를 들어 프로젝트 항목이 유지 되는 방식을 제어 하지만 파일을 유지 해야 한다는 알림을 제어 하지 않습니다. 사용자가 열린 프로젝트 항목에 포커스를 두고 메뉴 모음의 **파일** 메뉴에서 **저장** 을 선택 하는 경우 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 프로젝트 형식 코드는 ide에서 명령을 가로채서 파일을 저장 한 다음 파일을 더 이상 변경 하지 않는 것으로 ide에 알림을 다시 전송 해야 합니다.

 VSPackage는 IDE 인터페이스에 대 한 액세스를 제공 하는 서비스를 통해 IDE와 상호 작용 합니다. 예를 들어 특정 서비스를 통해 명령을 모니터링 및 라우팅하고 프로젝트에서 선택한 항목에 대 한 컨텍스트 정보를 제공 합니다. VSPackage에 필요한 모든 전역 IDE 기능은 서비스에서 제공 합니다. 서비스에 대 한 자세한 내용은 [방법: 서비스 가져오기](../../extensibility/how-to-get-a-service.md)를 참조 하세요.

 기타 구현 고려 사항:

- 단일 프로젝트 모델에는 두 개 이상의 프로젝트 형식이 포함 될 수 있습니다.

- 프로젝트 형식 및 수행자 프로젝트 팩터리는 Guid와 독립적으로 등록 됩니다.

- 사용자가 UI를 통해 새 프로젝트를 만들 때 새 프로젝트 파일을 초기화 하려면 각 프로젝트에 템플릿 파일이 나 마법사가 있어야 합니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . 예를 들어 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 템플릿에서는 궁극적으로 .vcproj 파일이 되도록 초기화 합니다.

  다음 그림에서는 일반적인 프로젝트 구현을 구성 하는 기본 인터페이스, 서비스 및 개체를 보여 줍니다. 응용 프로그램 도우미를 사용 하 여 `HierUtil7` 기본 개체와 기타 프로그래밍 상용구를 만들 수 있습니다. 응용 프로그램 도우미에 대 한 자세한 내용은 `HierUtil7` [HierUtil7 프로젝트 클래스를 사용 하 여 프로젝트 형식 구현 (c + +)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)을 참조 하세요.

  ![Visual Studio 프로젝트 모델 그래픽](../../extensibility/internals/media/vsprojectmodel.gif "vsProjectModel") 프로젝트 모델

  이전 다이어그램에 나열 된 인터페이스 및 서비스 및 다이어그램에 포함 되지 않은 다른 선택적 인터페이스에 대 한 자세한 내용은 [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)를 참조 하세요.

  프로젝트는 명령을 지원할 수 있으므로 명령 <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> 컨텍스트 guid를 통해 명령 라우팅에 참여 하기 위해 인터페이스를 구현 해야 합니다.

## <a name="see-also"></a>참조
- [검사 목록: 새 프로젝트 형식 만들기](../../extensibility/internals/checklist-creating-new-project-types.md)
- [HierUtil7 프로젝트 클래스를 사용 하 여 프로젝트 형식 구현 (c + +)](https://msdn.microsoft.com/library/a5c16a09-94a2-46ef-87b5-35b815e2f346)
- [프로젝트 모델 핵심 구성 요소](../../extensibility/internals/project-model-core-components.md)
- [프로젝트 팩터리를 사용 하 여 프로젝트 인스턴스 만들기](../../extensibility/internals/creating-project-instances-by-using-project-factories.md)
- [방법: 서비스 가져오기](../../extensibility/how-to-get-a-service.md)
- [프로젝트 형식 만들기](../../extensibility/internals/creating-project-types.md)
