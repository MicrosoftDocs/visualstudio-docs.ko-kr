---
title: 코드 자동화 제공 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bd13b7db2065069ff1540dbfc921570c2b230b8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705987"
---
# <a name="providing-automation-for-code"></a>코드에 대한 자동화 제공
코드에 대한 자동화 모델을 만들 필요는 없습니다. 환경 SDK는 이를 위한 샘플을 제공하지 않습니다. 코드 모델에 대한 자세한 <xref:EnvDTE.CodeModel> 내용은 개체를 참조하십시오.

 코드 모델을 구현하려면 내부 데이터 구조에 의해 결정되는 모든 인터페이스를 구현해야 합니다. 개체는 `IDispatch` 클래스에서 파생되어야 합니다.

 <xref:EnvDTE.CodeModel> 확장중인 개체 및 <xref:EnvDTE.FileCodeModel>에서 사용할 수 <xref:EnvDTE.Project> 있으며 다음과 같습니다.

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 및 <xref:EnvDTE.ProjectItem> 개체에서 반환하는 `CodeModel` 개체의 `FileCodeModel` 인터페이스 또는 인터페이스만 `Project` 구현하도록 선택할 수 있습니다. 프로젝트 시스템에 적합한 이 인터페이스의 모든 기능을 제공합니다.

 표준 `CodeModel` 및 인터페이스에서 사용할 수 없는 메서드 또는 속성과 `FileCodeModel` 같은 기능을 추가하려면 표준에서 상속하는 고유한 인터페이스를 만듭니다. 최종 사용자가 이를 찾을 수 있도록 프로젝트 시스템으로 문서화해야 합니다. 표준 인터페이스를 반환하지만 사용자가 메서드를 `QueryInterface` 호출하거나 인터페이스에 캐스팅할 수 있는 경우 해당 인터페이스가 있는 것으로 알려져 있습니다.

## <a name="see-also"></a>참조
- [자동화 모델 개요](../../extensibility/internals/automation-model-overview.md)
