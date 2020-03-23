---
title: 도메인 특정 언어 도구 개요 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: overview
helpviewer_keywords:
- Domain-Specific Language
ms.assetid: 50d93ea2-8c88-4522-853b-40ab194953db
caps.latest.revision: 56
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d38aed17d7fdaa694c8c5753705b28b0390dedfc
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/20/2020
ms.locfileid: "72652142"
---
# <a name="overview-of-domain-specific-language-tools"></a>도메인별 언어 도구 개요
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 호스팅되는 도메인 특정 언어 도구(DSL 도구)를 사용하면 도메인 특정 언어를 설계한 후 사용자가 해당 언어를 기반으로 모델을 만드는 데 필요한 모든 것을 생성할 수 있습니다.

 DSL 도구에 포함된 도구는 다음과 같습니다.

- 도메인 특정 언어 개발을 시작하는 데 도움이 되는 여러 솔루션 템플릿을 사용하는 프로젝트 마법사.

- 도메인 특정 언어 정의를 만들고 편집하는 데 사용되는 그래픽 디자이너.

- 도메인 특정 언어 정의가 잘 구성되어 있는지 확인하고 문제가 있을 경우 오류와 경고를 표시하는 유효성 검사 엔진.

- 도메인 특정 언어 정의를 입력으로 사용하고 소스 코드를 출력으로 생성하는 코드 생성기.

## <a name="the-dsl-tools-solution"></a>DSL 도구 솔루션
 도메인 특정 디자이너 마법사는 다음과 같은 솔루션 템플릿을 제공합니다.

- 작업 흐름

- 클래스 다이어그램

- 최소 언어

- 구성 요소 모델

- 최소 WPF

- 최소 Windows.Forms

- DSL 라이브러리

  자세한 내용은 [도메인 특정 언어 솔루션 템플릿 선택](../modeling/choosing-a-domain-specific-language-solution-template.md)을 참조하세요.

  이 마법사는 다음과 같은 프로젝트가 있는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 솔루션을 만듭니다.

- Dsl

   Dsl 프로젝트는 도메인 특정 언어와 해당 편집 및 처리 도구를 정의합니다.

- **DslPackage**

   DslPackage 프로젝트는 언어 도구가 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]와 통합되는 방법을 결정합니다.

## <a name="the-dsl-tools-graphical-interface"></a>DSL 도구 그래픽 인터페이스
 DSL 도구 그래픽 인터페이스를 사용하여 도메인 특정 언어에 요소 및 관계를 추가할 수 있습니다. 요소를 추가한 후 도형에 매핑하고, 색상을 사용자 지정하고, 데코레이터를 추가하여 모양을 정의할 수 있습니다. 또한 도구 상자에 요소를 추가할 수도 있습니다.

## <a name="validation-in-dsl-tools"></a>DSL 도구의 유효성 검사
 Dsl은 도메인 모델이 코드 생성에 대한 기본 요구 사항을 충족하는지 확인하는 한 가지 수준의 유효성 검사를 제공합니다. 일반적으로 고유한 도메인 특정 언어를 만들 때는 비즈니스 논리 규칙을 표현하는 고유한 유효성 검사를 추가합니다. 사용자 지정 유효성 검사에 대한 자세한 내용은 [도메인 특정 언어의 유효성 검사](../modeling/validation-in-a-domain-specific-language.md)를 참조하세요.

 도메인 특정 언어를 설계할 때는 유효성 검사를 자주 수행하는 것이 좋습니다. 도메인 특정 언어에 유효성 검사 오류가 있을 경우 소스 코드를 생성할 수 없습니다. 템플릿으로 소스 코드를 생성하는 프로세스는 솔루션 탐색기의 도구 모음에서 **모든 템플릿 변환**을 클릭하면 수행할 수 있습니다. 언어 정의를 수정할 때마다 **모든 템플릿 변환**을 수행해야 합니다. 자세한 내용은 [방법: 도메인 특정 언어 솔루션 만들기](../modeling/how-to-create-a-domain-specific-language-solution.md)를 참조하세요.

## <a name="customization-of-dsl-tools"></a>DSL 도구 사용자 지정
 모델의 동작을 구체화하고 언어에 대한 제약 조건을 정의하는 추가 코드를 제공할 수 있습니다. 필요한 경우 텍스트 템플릿을 수정하여 중요한 변경 작업을 수행할 수 있습니다.

## <a name="distributing-your-dsl-solution"></a>DSL 솔루션 배포
 DSL 도구는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 호스팅되는 패키지를 생성합니다. 이 패키지는 도구 상자, DSL 탐색기, 그리고 사용자가 도메인 특정 언어를 사용하여 모델을 만드는 데 사용되는 다른 UI 요소를 표시합니다.

 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]에서 DSL 도구 솔루션을 빌드하고 실행하면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 두 번째 인스턴스가 언어 사용자에게 도메인 특정 언어가 어떻게 보이는지 보여줍니다. 모든 항목이 올바르게 작동하는 것을 확인한 후에는 DslPackage 프로젝트의 빌드 폴더에 있는 `.vsix` 파일을 배포할 수 있습니다. 이 파일은 다른 컴퓨터에서 DSL을 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 확장 프로그램으로 설치하는 데 사용할 수 있습니다.  자세한 내용은 [도메인 특정 언어 솔루션 배포](../modeling/deploying-domain-specific-language-solutions.md)를 참조하세요.

## <a name="see-also"></a>관련 항목
 [실험적 인스턴스](../extensibility/the-experimental-instance.md) [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
