---
title: 코드에 대 한 자동화 제공 | Microsoft Docs
description: 내부 데이터 구조에 따라 결정 되는 인터페이스를 구현 해야 하는 코드 모델을 구현 하는 방법에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- CodeModel object
ms.assetid: 21cb3e63-f25c-404b-bc1d-a32ad0fdd4d5
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 41dca5d7a3d2a95ae9b89feb73fb7655b8923eb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99837218"
---
# <a name="providing-automation-for-code"></a>코드에 대한 자동화 제공
코드에 대 한 자동화 모델을 만들 필요는 없습니다. 환경 SDK는이 작업에 대 한 샘플을 제공 하지 않습니다. 코드 모델에 대 한 자세한 내용은 개체를 참조 하세요 <xref:EnvDTE.CodeModel> .

 코드 모델을 구현 하려면 내부 데이터 구조에 따라 결정 되는 모든 인터페이스를 구현 해야 합니다. 개체는 클래스에서 파생 되어야 합니다 `IDispatch` .

 확장 하는 개체와는 <xref:EnvDTE.CodeModel> <xref:EnvDTE.FileCodeModel> 개체에서 사용할 수 <xref:EnvDTE.Project> 있으며 다음과 같습니다.

- <xref:EnvDTE.Project.CodeModel%2A>

- <xref:EnvDTE.ProjectItem.FileCodeModel%2A>

 `CodeModel` `FileCodeModel` 및 개체에서 반환 하는 개체에만 또는 인터페이스를 구현 하도록 선택할 수 있습니다 `Project` <xref:EnvDTE.ProjectItem> . 이 인터페이스에서 프로젝트 시스템에 적합 한 기능을 제공 합니다.

 표준 및 인터페이스에서 사용할 수 없는 기능 (예: 메서드 또는 속성)을 추가 하려면 `CodeModel` `FileCodeModel` 표준에서 상속 하는 고유한 인터페이스를 만듭니다. 최종 사용자가 찾을 수 있도록 프로젝트 시스템에 문서를 문서화 해야 합니다. 표준 인터페이스를 반환 하지만 사용자가 메서드를 호출 `QueryInterface` 하거나 인터페이스가 있는 경우 인터페이스로 캐스팅할 수 있습니다.

## <a name="see-also"></a>참고 항목
- [자동화 모델 개요](../../extensibility/internals/automation-model-overview.md)
