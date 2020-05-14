---
title: 자동화 모델 개요 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- automation [Visual Studio SDK], about automation
- extensibility
ms.assetid: 12b6d6db-0d22-4aaa-aa7d-1365f759b7b0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b940677c370106ebdcc63c7984d553003251e8a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710003"
---
# <a name="automation-model-overview"></a>자동화 모델 개요
자동화 모델은 Visual Studio 추가 기능 또는 확장을 작성할 수 있는 개체 집합으로 구성됩니다. 추가 프로그램은 Visual Studio 환경을 조작하고 일반적인 작업을 자동화할 수 있는 응용 프로그램입니다. Visual Studio 확장프로그램은 사용자 지정 Visual Studio 구성 요소를 만들거나 텍스트 편집기와 같은 표준 구성 요소의 기능에 추가할 수 있습니다.

## <a name="objects-in-the-automation-model"></a>자동화 모델의 개체
 자동화 모델은 공통 환경의 주요 측면을 제어하는 관련 개체 그룹으로 구성됩니다. 다음 다이어그램에서는 자동화 모델을 구성하는 광범위한 Visual Studio 개체 집합을 보여 주며 있습니다.

 ![비주얼 스튜디오 자동화 개체 차트](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vs비주얼스튜디오자동화개체차트")

 자세한 내용은 [Visual Studio 환경 확장을](https://msdn.microsoft.com/Library/4173a963-7ac7-4966-9bb7-e28a9d9f6792)참조하십시오.

 환경은 서로 다른 기능 영역에 대한 모델을 제공합니다. 예를 들어 코드에서 찾을 수 있는 다양한 요소에 대한 코드 모델이 있습니다. 다양한 문서 요소에 대한 문서 모델이 있습니다. 프로젝트 영역 중 하나는 VSPackage 공급자에게 특히 관심이 있습니다. 새 프로젝트 유형이 자동화 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] 모델과 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] 거의 동일한 방식으로 자동화 모델에 기여하고 자동화 모델에 기여하기를 원할 것입니다. 이 프로세스는 [VSPackage에 대한 자동화 제공에 설명되어 있습니다.](../../extensibility/internals/providing-automation-for-vspackages.md)

 환경의 자동화 모델을 확장할 수 있는 위치:

- Project

- 문서

- 코드

- 빌드

자동화에 대한 자세한 내용은 [Visual Studio의 자동화 및 확장성을](/visualstudio/extensibility/extensibility-in-visual-studio?view=vs-2015)참조하십시오. 이 문서와 링크에 대한 문서는 VSPackage에 대한 자동화를 제공하는 방법에 대한 결정을 내리는 데 도움이 됩니다.

## <a name="see-also"></a>참조
- [방법: 추가 기능 만들기](https://msdn.microsoft.com/Library/50be56d2-e3a5-4cd2-8569-2a0666b268ce)
