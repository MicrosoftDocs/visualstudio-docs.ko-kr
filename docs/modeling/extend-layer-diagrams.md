---
title: 종속성 다이어그램 확장
description: 종속성 다이어그램을 만들고 업데이트 하는 코드를 작성 하는 방법 및 Visual Studio의 종속성 다이어그램에 대해 프로그램 코드 구조의 유효성을 검사 하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dependency diagrams, creating extensions
- layer models
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c2ed8700cfb18aacf41464bfdfacaedac557bb00
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388908"
---
# <a name="extend-dependency-diagrams"></a>종속성 다이어그램 확장

종속성 다이어그램을 만들고 업데이트 하 고 Visual Studio의 종속성 다이어그램에 대해 프로그램 코드 구조의 유효성을 검사 하는 코드를 작성할 수 있습니다. 다이어그램의 바로 가기(상황에 맞는) 메뉴에 표시되는 명령을 추가하고, 끌어서 놓기 제스처를 사용자 지정하고, 텍스트 템플릿에서 레이어 모델에 액세스할 수 있습니다. 이러한 확장을 VSIX(Visual Studio Integration Extension)로 패키징하고 다른 Visual Studio 사용자에게 배포할 수 있습니다.

## <a name="requirements"></a>요구 사항

레이어 확장을 개발하려는 컴퓨터에 다음이 설치되어 있어야 합니다.

- Visual Studio

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)

- Visual Studio 용 모델링 SDK

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

레이어 확장을 실행 하려는 컴퓨터에 적합 한 버전의 Visual Studio가 설치 되어 있어야 합니다. 종속성 다이어그램을 지 원하는 Visual Studio 버전을 확인 하려면 [아키텍처 및 모델링 도구에 대 한 버전 지원](../modeling/analyze-and-model-your-architecture.md#VersionSupport)을 참조 하세요.

## <a name="see-also"></a>참조

- [종속성 다이어그램: 참조](../modeling/layer-diagrams-reference.md)
- [종속성 다이어그램: 지침](../modeling/layer-diagrams-guidelines.md)
- [코드에서 종속성 다이어그램 만들기](../modeling/create-layer-diagrams-from-your-code.md)
- [종속성 다이어그램을 사용하여 코드 유효성 검사](../modeling/validate-code-with-layer-diagrams.md)
