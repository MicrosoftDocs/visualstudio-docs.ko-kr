---
title: 자동화 모델 개요 | Microsoft Docs
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
ms.openlocfilehash: 83df8926be9cd7217c514a2ed3f242bf8e121913
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584570"
---
# <a name="automation-model-overview"></a>자동화 모델 개요
자동화 모델은 Visual Studio 추가 기능 또는 확장을 작성할 수 있는 개체 집합으로 구성 됩니다. 추가 기능은 Visual Studio 환경을 조작 하 고 일반적인 작업을 자동화할 수 있는 응용 프로그램입니다. Visual Studio 확장은 사용자 지정 Visual Studio 구성 요소를 만들거나 텍스트 편집기와 같은 표준 구성 요소의 기능에 추가할 수 있습니다.

## <a name="objects-in-the-automation-model"></a>자동화 모델의 개체
 자동화 모델은 공통 환경의 주요 패싯을 제어 하는 개체의 관련 그룹으로 구성 됩니다. 다음 다이어그램에서는 자동화 모델을 구성 하는 다양 한 Visual Studio 개체 집합을 보여 줍니다.

 ![Visual Studio 자동화 개체 차트](../../extensibility/internals/media/vsvisualstudioautomationobjectchart.gif "vsVisualStudioAutomationObjectChart")

 자세한 내용은 [Visual Studio 환경 확장](/previous-versions/esk3eey8(v=vs.140))을 참조 하세요.

 환경은 다양 한 기능 영역에 대 한 모델을 제공 합니다. 예를 들어 코드에서 찾을 수 있는 다양 한 요소에 대 한 코드 모델이 있습니다. 다양 한 문서 요소에 대 한 문서 모델이 있습니다. 프로젝트 영역인 VSPackage 공급자에 게는 특정 한 영역이 있습니다. 자동화 모델에 적용 하는 것과 동일한 방식으로 새 프로젝트 형식이 자동화 모델에 기여 하 게 하려는 경우가 있습니다 [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] . 이 프로세스는 [vspackage에 대 한 자동화 제공](../../extensibility/internals/providing-automation-for-vspackages.md)에서 간략하게 설명 합니다.

 환경에 대 한 자동화 모델 확장을 고려할 수 있는 위치:

- Project

- 문서

- 코드

- 빌드

자동화에 대 한 자세한 내용은 [Visual Studio의 자동화 및 확장성](../../vs-2015/extensibility/extensibility-in-visual-studio.md?view=vs-2015&preserve-view=true)을 참조 하세요. 이 문서와이 문서에 링크를 제공 하는 문서는 VSPackage에 대 한 자동화를 제공 하는 방법에 대 한 의사 결정을 내리는 데 도움이 됩니다.

## <a name="see-also"></a>참고 항목
- [방법: 추가 기능 만들기](/previous-versions/80493a3w(v=vs.140))