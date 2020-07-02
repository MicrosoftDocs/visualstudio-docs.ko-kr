---
title: 시각화 및 모델링 SDK에 대해 지원 되는 Visual Studio 버전
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3be233ce8730879c2f0406ec9cc180685992c6bf
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544939"
---
# <a name="supported-visual-studio-editions-for-visualization--modeling-sdk"></a>시각화 및 모델링 SDK에서 지원되는 Visual Studio 버전

다음은 [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] 제작 및 배포 환경에서에서 지원 되는 Visual Studio 버전의 목록입니다. 이러한 버전에 대 한 자세한 내용은 Microsoft Visual Studio [개발자 센터](https://visualstudio.microsoft.com/)를 참조 하세요.

## <a name="authoring-edition"></a>작성 버전

DSL을 정의하려면 다음 구성 요소를 설치해야 합니다.

|Product|다운로드 링크|
|-|-|
|Visual Studio|[http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/)|
|Visual Studio SDK|[http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index?view=azure-devops&viewFallbackFrom=vsts)|
|Visual Studio Visualization and Modeling SDK|[http://go.microsoft.com/fwlink/?LinkID=186128](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db)|

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="deployment-editions"></a>배포 버전

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)]는 사용자가 작성 하는 도메인별 언어를 배포 하기 위해 다음 구성을 지원 합니다.

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell(통합 모드) 재배포 가능 패키지

- Visual Studio Shell(격리 모드) 재배포 가능 패키지

> [!NOTE]
> 셸 제품에서 DSL을 실행할 수 있도록 하려면 확장 매니페스트에서 **지원 되는 VS Edition** 필드를 설정 해야 합니다. 자세한 내용은 [도메인 특정 언어 솔루션 배포](msi-and-vsix-deployment-of-a-dsl.md)를 참조하세요.

## <a name="see-also"></a>참고 항목

- [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
