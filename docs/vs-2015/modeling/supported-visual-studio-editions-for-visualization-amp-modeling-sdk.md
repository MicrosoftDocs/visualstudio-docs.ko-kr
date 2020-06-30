---
title: 시각화 및 모델링 SDK에 대해 지원 되는 Visual Studio 버전 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, supported Visual Studio editions
ms.assetid: 7c313ba0-031d-45b8-8220-eead61754747
caps.latest.revision: 29
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3eebefeab6b78955b03d4546a60dd811f5e9ae4e
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85547656"
---
# <a name="supported-visual-studio-editions-for-visualization-amp-modeling-sdk"></a>시각화 모델링 SDK에 대해 지원 되는 Visual Studio 버전 &amp;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음은 [!INCLUDE[dsl](../includes/dsl-md.md)] 제작 및 배포 환경에서에서 지원 되는 Visual Studio 버전의 목록입니다. 이러한 버전에 대 한 자세한 내용은 Microsoft [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [개발자 센터](https://msdn.microsoft.com/vstudio/products/)를 참조 하세요.

## <a name="authoring-edition"></a>작성 버전
 DSL을 정의하려면 다음 구성 요소를 설치해야 합니다.

|Product|다운로드 링크|
|-|-|
|[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]|[https://www.visualstudio.com/](https://www.visualstudio.com/)|
|[!INCLUDE[vssdk_current_short](../includes/vssdk-current-short-md.md)]|[Visual Studio SDK](../extensibility/visual-studio-sdk.md)|
|Visual Studio Visualization and Modeling SDK|[모델링 SDK 다운로드](https://www.microsoft.com/download/details.aspx?id=48148)|
## <a name="deployment-editions"></a>배포 버전
 [!INCLUDE[dsl](../includes/dsl-md.md)]는 사용자가 작성 하는 도메인별 언어를 배포 하기 위해 다음 구성을 지원 합니다.

- Visual Studio Enterprise

- Visual Studio Professional

- Visual Studio Shell(통합 모드) 재배포 가능 패키지

- Visual Studio Shell(격리 모드) 재배포 가능 패키지

> [!NOTE]
> 셸 제품에서 DSL을 실행할 수 있도록 하려면 확장 매니페스트에서 **지원 되는 VS Edition** 필드를 설정 해야 합니다. 자세한 내용은 [도메인 특정 언어 솔루션 배포](../modeling/deploying-domain-specific-language-solutions.md)를 참조하세요.

## <a name="see-also"></a>참고 항목
 [도메인 특정 언어 도구 용어집](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
