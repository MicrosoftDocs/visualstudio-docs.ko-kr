---
title: 레이어 다이어그램 확장 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- layer diagrams, creating extensions
- layer models
ms.assetid: 83fca301-b008-485a-87eb-218050e71451
caps.latest.revision: 41
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bfcec64f9401fdbf79e67bee5fe8430452632fbc
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409609"
---
# <a name="extend-layer-diagrams"></a>Extend layer diagrams
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

레이어 다이어그램을 만들고 업데이트한 다음 Visual Studio에서 레이어 다이어그램에 대해 프로그램 코드 구조의 유효성을 검사하는 코드를 작성할 수 있습니다. 다이어그램의 바로 가기(상황에 맞는) 메뉴에 표시되는 명령을 추가하고, 끌어서 놓기 제스처를 사용자 지정하고, 텍스트 템플릿에서 레이어 모델에 액세스할 수 있습니다. 이러한 확장을 VSIX(Visual Studio Integration Extension)로 패키징하고 다른 Visual Studio 사용자에게 배포할 수 있습니다.

 레이어 다이어그램에 대한 자세한 내용은 다음을 참조하세요.

- [레이어 다이어그램: 참조](../modeling/layer-diagrams-reference.md)

- [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)

- [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)

- [레이어 다이어그램에 대해 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)

## <a name="prereqs"></a> 요구 사항
 레이어 확장을 개발하려는 컴퓨터에 다음이 설치되어 있어야 합니다.

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- [Visual Studio 2015 용 SDK 모델링](https://www.microsoft.com/download/details.aspx?id=48148)

  레이어 확장을 실행하려는 컴퓨터에 적합한 버전의 Visual Studio가 설치되어 있어야 합니다. 자세한 내용은 [레이어 모델 확장 배포](../modeling/deploy-a-layer-model-extension.md)를 참조 하세요.

  레이어 다이어그램을 지원하는 Visual Studio 버전을 확인하려면 [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)을 참조하세요.

## <a name="in-this-section"></a>섹션 내용
 [레이어 다이어그램에 명령 및 제스처 추가](../modeling/add-commands-and-gestures-to-layer-diagrams.md)

 [레이어 다이어그램에 사용자 지정 아키텍처 유효성 검사 추가](../modeling/add-custom-architecture-validation-to-layer-diagrams.md)

 [레이어 다이어그램에 사용자 지정 속성 추가](../modeling/add-custom-properties-to-layer-diagrams.md)

 [프로그램 코드에서 레이어 모델 탐색 및 업데이트](../modeling/navigate-and-update-layer-models-in-program-code.md)

 [레이어 모델 확장 배포](../modeling/deploy-a-layer-model-extension.md)

 [레이어 다이어그램의 확장 문제 해결](../modeling/troubleshoot-extensions-for-layer-diagrams.md)

## <a name="see-also"></a>참고 항목
 [모델링 확장 레이어 다이어그램 정의 및 설치](../modeling/define-and-install-a-modeling-extension.md) [: 참조](../modeling/layer-diagrams-reference.md) [레이어 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md) [코드에서 레이어 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md) [레이어 다이어그램을 사용 하 여 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md) [uml 모델에서 파일 생성](../modeling/generate-files-from-a-uml-model.md) [Visual Studio API를 사용 하 여 uml 모델 열기](../modeling/open-a-uml-model-by-using-the-visual-studio-api.md)
