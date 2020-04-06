---
title: VS패키지 관리 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, autoloading
- VSPackages, delayed loading
- delay loading
- VSPackages, loading
ms.assetid: 386e0ce5-4107-4164-b0cd-1cf43eb5e7cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 60745d07679ae53b85d169473ed37ab314b67624
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702647"
---
# <a name="manage-vspackages"></a>VSPackage 관리
대부분의 경우 프로젝트 및 항목 템플릿이 패키지를 자동으로 등록하고 로드하므로 VSPackage 관리에 대해 걱정할 필요가 없습니다. 그러나 경우에 따라 패키지를 관리하기 위해 좀 더 많은 것을 배워야 할 수도 있습니다.

## <a name="use-the-experimental-instance"></a>실험 인스턴스 사용
 실험 인스턴스에 대한 자세한 내용은 [실험 인스턴스 를](../extensibility/the-experimental-instance.md)참조하십시오.

## <a name="register-and-unregister-vspackages"></a>VS패키지 등록 및 등록 취소
 VSPackage 및 기타 유형의 확장을 등록하고 등록 취소하는 방법을 알아보려면 [VSPackage 등록 및 등록 취소를](../extensibility/registering-and-unregistering-vspackages.md)참조하십시오.

## <a name="load-a-vspackage"></a>VS패키지 로드
 VS패키지는 특정 CMDUICONTEXT GUID가 켜져 있을 때 자동 로드하도록 설정할 수 있습니다. 자세한 내용은 [VS패키지 로드 를](../extensibility/loading-vspackages.md)참조하십시오.

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>비동기 패키지를 사용하여 백그라운드에서 VSPackage로드
 클래스는 `AsyncPackage` Visual Studio에서 더 나은 UI 응답성을 위해 백그라운드 스레드에서 패키지를 로드할 수 있도록 합니다. 자세한 내용은 [사용 방법: 비동기 패키지를 사용하여 VSPackage를 백그라운드에서 로드하는](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)방법을 참조하십시오.

## <a name="rule-based-ui-context-for-extensions"></a>확장에 대한 규칙 기반 UI 컨텍스트
 규칙 기반 UI 컨텍스트를 사용하면 확장 작성자가 UI 컨텍스트가 활성화되고 연결된 VSPackage가 로드되는 정확한 조건을 정의할 수 있습니다. 자세한 내용은 [Visual Studio 확장에 규칙 기반 UI 컨텍스트를 사용하는 방법을 참조하세요.](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)

## <a name="diagnose-extension-performance"></a>확장 성능 진단
확장은 시작 및 솔루션 로드 성능에 영향을 미칠 수 있습니다. Visual Studio 확장 영향이 계산되는 방법과 확장이 성능에 영향을 미치는 확장으로 표시될 수 있는지 테스트하기 위해 로컬로 분석하는 방법을 알아봅니다. 자세한 내용은 [방법: 확장 성능 진단을](how-to-diagnose-extension-performance.md)참조하십시오.

## <a name="troubleshoot-vspackages"></a>VS패키지 문제 해결
 로드되지 않거나 오류가 발생하는 VSPackage 트러블슈팅 기술 알아보기: [VSPackage 문제 해결](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>참조
- [VSPackage](../extensibility/internals/vspackages.md)
