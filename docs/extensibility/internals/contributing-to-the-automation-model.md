---
title: 자동화 모델에 기여 | 마이크로 소프트 문서
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709264"
---
# <a name="contribute-to-the-automation-model"></a>자동화 모델에 기여
Visual Studio는 환경을 사용자 지정하기 위한 자동화 인터페이스 집합을 제공합니다. 자동화 모델은 최종 사용자가 Visual Studio 추가 기능 및 확장을 만들 수 있는 개체 모델입니다.

 또한 VSPackage 개발자는 자동화 모델에 기여하는 것이 적절합니다. 이렇게 하면 VSPackage의 최종 사용자가 추가 기능을 만들 수 있도록 활성화하 고 일반적으로 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 VSPackage를 사용할 때 일관 된 사용자 모델 환경을 제공 합니다.

 최종 사용자 환경을 일관되게 유지하려면 VSPackage의 자동화 모델이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 아이디어를 따르도록 VSPackage를 디자인할 때 일련의 지침을 따를 수 있습니다.

## <a name="in-this-section"></a>섹션 내용
- [자동화 모델 개요](../../extensibility/internals/automation-model-overview.md)

 자동화 모델을 공통 환경의 주요 측면을 제어하는 관련 개체 그룹으로 정의합니다. 이 개체 집합은 자동화 모델다이어그램에 표시됩니다.

- [VS패키지에 대한 자동화 제공](../../extensibility/internals/providing-automation-for-vspackages.md)

 VSPackage에 자동화를 제공하는 두 가지 주요 방법에 대해 설명합니다.

- [프로젝트 객체 노출](../../extensibility/internals/exposing-project-objects.md)

 VSPackage 관련 개체를 만들기 위한 단계별 지침을 제공합니다.

- [프로젝트 모델링](../../extensibility/internals/project-modeling.md)

 새 프로젝트 유형에 대한 자동화를 만드는 데 필요한 표준 프로젝트 개체를 설명하고 프로젝트 자동화가 따르는 경로를 보여 줍니다. 이 항목에서는 클래스에 대한 선언 및 구현 목록도 제공합니다.

- [이벤트 노출](../../extensibility/internals/exposing-events-in-the-visual-studio-sdk.md)

 자동화 모델에 대한 이벤트를 만들기 위한 단계별 지침을 제공합니다.

- [옵션 페이지에 대한 자동화 지원](../../extensibility/internals/automation-support-for-options-pages.md)

 도구 메뉴에서 VSPackage의 사용자 지정 **옵션** 대화 상자의 속성을 지원하기 위한 자동화 개체를 반환하는 방법을 설명합니다. **Tool** `DTE.Properties`

- [코드에 대한 자동화 제공](../../extensibility/internals/providing-automation-for-code.md)

 코드에 대한 자동화 모델을 만들 필요는 없다고 설명합니다. 그러나 이 항목에서는 코드 모델에 대한 통찰력 있는 정보를 제공하는 링크가 제공됩니다.

- [방법: Windows에 대한 자동화 제공](../../extensibility/internals/how-to-provide-automation-for-windows.md)

 자동화를 제공하는 것은 창에서 자동화 개체를 사용할 수 있도록 하려는 경우 좋은 생각이며 환경은 이미 준비된 자동화 개체를 제공하지 않습니다. 도구 창 및 문서 창에 대한 자동화에 대해 설명합니다.

- [자동화 모델 사용](../../extensibility/internals/using-the-automation-model.md)

 자동화 소비자가 초기 프로젝트 자동화 개체를 가져오는 방법을 보여 주는 두 가지 코드 예제를 제공합니다.

- [구성 및 선택항목 개체에 대한 자동화](../../extensibility/internals/automation-for-configuration-and-selecteditem-objects.md)

 구성 및 선택항목 개체에 대한 자동화에 대한 정보를 제공합니다.

## <a name="reference"></a>참조
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.GetAutomationObject%2A>VSPackage가 DTE 자동화 개체 모델에 참여하는 방법을 보여 주는 코드 샘플을 제공합니다. 매개 변수, 반환 값 및 선택한 설명/을 나열합니다.
