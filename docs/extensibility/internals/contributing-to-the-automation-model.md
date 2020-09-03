---
title: 자동화 모델에 기여 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK]
ms.assetid: 44de482d-93c8-41a4-843c-cefda995a03e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d660edc740229c3e91b99e1f59eb37b4e9312098
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80709264"
---
# <a name="contribute-to-the-automation-model"></a>자동화 모델에 기여
Visual Studio는 환경을 사용자 지정 하기 위한 자동화 인터페이스 집합을 제공 합니다. 자동화 모델은 최종 사용자가 Visual Studio 추가 기능 및 확장을 만들 수 있도록 하는 개체 모델입니다.

 또한 자동화 모델에 기여 하기 위해 VSPackage 개발자에 게 적합 합니다. 이렇게 하면 VSPackage의 최종 사용자가 추가 기능을 만들 수 있으며 일반적으로의 VSPackage를 사용할 때 일관 된 사용자 모델 환경을 제공할 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

 최종 사용자에 게 일관 된 환경을 제공 하기 위해 VSPackage을 디자인할 때 지침 집합을 따라 VSPackage에 대 한 자동화 모델이의 아이디어를 따를 수 있습니다 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

## <a name="in-this-section"></a>섹션 내용
- [자동화 모델 개요](../../extensibility/internals/automation-model-overview.md)

 자동화 모델을 공통 환경의 주요 패싯을 제어 하는 개체의 관련 그룹으로 정의 합니다. 이 개체 집합은 자동화 모델의 다이어그램에 나와 있습니다.

- [Vspackage에 대 한 자동화 제공](../../extensibility/internals/providing-automation-for-vspackages.md)

 VSPackage에 대 한 자동화를 제공 하는 두 가지 주요 방법을 설명 합니다.

- [프로젝트 개체 노출](../../extensibility/internals/exposing-project-objects.md)

 VSPackage 관련 개체를 만드는 방법에 대 한 단계별 지침을 제공 합니다.

- [프로젝트 모델링](../../extensibility/internals/project-modeling.md)

 새 프로젝트 형식에 대 한 자동화를 만드는 데 필요한 표준 프로젝트 개체에 대해 설명 하 고, 프로젝트 자동화에서 따르는 경로를 보여 줍니다. 이 항목에서는 클래스에 대 한 선언 및 구현 목록도 제공 합니다.

- [이벤트 노출](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 자동화 모델에 대 한 이벤트를 만드는 단계별 지침을 제공 합니다.

- [옵션 페이지에 대 한 자동화 지원](../../extensibility/internals/automation-support-for-options-pages.md)

 개체를 확장 하 여 **도구** 메뉴에서 VSPackage의 사용자 지정 **옵션** 대화 상자를 지 원하는 속성에 대 한 자동화 개체를 반환 하는 방법을 설명 합니다 `DTE.Properties` .

- [코드에 대 한 자동화 제공](../../extensibility/internals/providing-automation-for-code.md)

 코드에 대 한 자동화 모델을 만드는 것은 필요 하지 않습니다. 그러나이 항목에서는 통찰력 있는 정보를 코드 모델에 제공 하는 링크를 제공 합니다.

- [방법: Windows에 대 한 자동화 제공](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 자동화를 제공 하는 것은 창에서 자동화 개체를 사용할 수 있도록 하 고 환경에서 미리 만들어진 자동화 개체를 아직 제공 하지 않을 때마다 유용 하 게 사용할 수 있다는 것을 설명 합니다. 도구 창 및 문서 창의 자동화에 대해 설명 합니다.

- [자동화 모델 사용](../../extensibility/internals/using-the-automation-model.md)

 자동화 소비자가 초기 프로젝트 자동화 개체를 가져오는 방법을 보여 주는 두 가지 코드 예제를 제공 합니다.

- [구성 및 SelectedItem 개체에 대 한 자동화](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 구성 및 SelectedItems 개체에 대 한 자동화 정보를 제공 합니다.

## <a name="reference"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A> VSPackage가 DTE 자동화 개체 모델에 참여 하는 방법을 보여 주는 코드 샘플을 제공 합니다. 매개 변수, 반환 값 및 선택한 설명을 나열 합니다.
