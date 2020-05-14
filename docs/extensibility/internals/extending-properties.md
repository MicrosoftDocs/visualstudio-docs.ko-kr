---
title: 속성 확장 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Properties window, providing support
ms.assetid: 68e2cbd4-861c-453f-8c9f-4ab6afc80e67
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7064128c54434b0a7bb8799e62b751e765511c48
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708422"
---
# <a name="extend-properties"></a>속성 확장
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **속성** 창은 COM 및 COM+ 구성 요소에 대 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 한 범용 속성 브라우저이며 모든 제품을 지원 합니다. **속성** 창은 `ITypeInfo` 형식 정보 및 COM+ 메타데이터로 작동하여 IDE(통합 개발 환경)의 다른 창에 현재 선택된 개체에 대한 디자인 타임 속성을 나열합니다.

 키보드에서 **F4를** 누르거나 **보기** 메뉴에서 **속성 창을** 선택하여 열 수 있는 **속성** 창은 선택한 개체의 구성 독립적인 디자인 시간 속성 및 이벤트를 보고 편집하는 데 사용됩니다. 솔루션 및 프로젝트와 연결된 구성 종속 속성이 [속성 페이지에](../../extensibility/internals/property-pages.md)표시됩니다. 자세한 내용은 [구성 옵션 관리.](../../extensibility/internals/managing-configuration-options.md)

 ![속성 창 개요](../../extensibility/internals/media/vspropertieswindow.png "대 프로퍼티 윈도우") 속성 창

 이 섹션에서는 **Properties** 창의 개별 영역 및 창을 채우기 위해 구현하고 호출해야 하는 인터페이스와 관련된 자세한 정보를 제공합니다.

## <a name="in-this-section"></a>섹션 내용
- [속성 창 개요](../../extensibility/internals/properties-window-overview.md)

 도구 창 및 문서 창을 기준으로 **속성** 창의 용도를 설명합니다.

- [템플릿 정책 및 속성 창](../../extensibility/internals/template-policy-and-the-properties-window.md)

 프로젝트가 엔터프라이즈 템플릿 프로젝트에 포함되는 방법과 해당 엔터프라이즈 템플릿 프로젝트가 정책을 적용하는 방법에 대해 설명합니다.

- [속성 창 필드 및 인터페이스](../../extensibility/internals/properties-window-fields-and-interfaces.md)

 **속성** 창에 표시되는 정보를 결정하는 선택 의 기초를 설명합니다.

- [속성 창 개체 목록](../../extensibility/internals/properties-window-object-list.md)

 **속성** 창 개체 목록의 목적을 설명 하며 이 목록에서 다른 개체가 호출을 트리거하는 경우 환경에 새 개체가 선택되었음을 알리는 방법을 설명합니다.

- [속성 창 단추](../../extensibility/internals/properties-window-buttons.md)

 **속성** 창 도구 모음에 표시되는 네 개의 기본 단추의 용도를 설명합니다.

- [속성 표시 표](../../extensibility/internals/properties-display-grid.md)

 속성 이름 및 속성 값 필드가 그리드에서 발견되는 위치를 설명합니다.

## <a name="related-sections"></a>관련 단원
- [프로젝트 형식](../../extensibility/internals/project-types.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE의 구성 요소로 프로젝트를 설명합니다.

- [컴파일 및 빌드](../../ide/compiling-and-building-in-visual-studio.md)

 응용 프로그램을 빌드할 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 때 응용 프로그램을 지속적으로 테스트하고 디버깅하는 데 플랫폼을 사용하는 방법에 대해 설명합니다.

- [Idispatch](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch)

 자동화를 `IDispatch` 지원하도록 처음 설계된 인터페이스에 대해 설명하며, 개체의 메서드 및 속성에 대한 정보에 액세스하고 검색하는 라시 바인딩된 메커니즘을 제공합니다.

- [애플리케이션 설정 관리(.NET)](../../ide/managing-application-settings-dotnet.md)

 속성 값이 응용 프로그램의 컴파일된 코드 대신 외부 구성 파일에 저장되도록 응용 프로그램을 구성할 수 있는 응용 프로그램 설정에 대한 개요를 제공합니다.

- [솔루션 및 프로젝트](../../ide/solutions-and-projects-in-visual-studio.md)

 솔루션 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 및 프로젝트를 통해 개발 노력에 필요한 참조, 데이터 연결, 폴더 및 파일과 같은 항목을 효율적으로 관리하는 방법을 설명합니다.

- [비주얼 스튜디오의 다른 부분 확장](../../extensibility/extending-other-parts-of-visual-studio.md)

 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 서비스를 사용하여 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]의 나머지와 일치하는 UI 요소를 만드는 방법을 설명합니다.
