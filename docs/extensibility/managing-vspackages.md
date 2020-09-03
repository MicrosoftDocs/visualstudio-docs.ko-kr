---
title: Vspackage 관리 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80702647"
---
# <a name="manage-vspackages"></a>VSPackage 관리
대부분의 경우 프로젝트 및 항목 템플릿이 자동으로 패키지를 등록 하 고 로드 하므로 Vspackage 관리에 대해 걱정할 필요가 없습니다. 그러나 일부 경우에는 패키지를 관리 하기 위해 약간 더 배워야 할 수도 있습니다.

## <a name="use-the-experimental-instance"></a>실험적 인스턴스 사용
 실험적 인스턴스에 대해 자세히 알아보려면 [실험적 인스턴스](../extensibility/the-experimental-instance.md)를 참조 하세요.

## <a name="register-and-unregister-vspackages"></a>Vspackage 등록 및 등록 취소
 Vspackage 및 다른 유형의 확장을 등록 하 고 등록을 취소 하는 방법을 알아보려면 [Vspackage 등록 및 등록 취소](../extensibility/registering-and-unregistering-vspackages.md)를 참조 하세요.

## <a name="load-a-vspackage"></a>VSPackage 로드
 특정 CMDUICONTEXT GUID가 설정 되어 있으면 Vspackage을 autoload로 설정할 수 있습니다. 자세한 내용은 [Load vspackage](../extensibility/loading-vspackages.md)을 (를) 참조 하세요.

## <a name="use-asyncpackage-to-load-vspackages-in-the-background"></a>AsyncPackage를 사용 하 여 백그라운드에서 Vspackage 로드
 `AsyncPackage`클래스를 사용 하면 Visual Studio에서 UI 응답성을 개선 하기 위해 백그라운드 스레드에서 패키지를 로드할 수 있습니다. 자세한 내용은 [방법: AsyncPackage를 사용 하 여 배경에 vspackage 로드를](../extensibility/how-to-use-asyncpackage-to-load-vspackages-in-the-background.md)참조 하세요.

## <a name="rule-based-ui-context-for-extensions"></a>확장 프로그램에 대 한 규칙 기반 UI 컨텍스트
 규칙 기반 UI 컨텍스트를 통해 확장 작성자는 UI 컨텍스트가 활성화 되 고 관련 Vspackage 로드 되는 정확한 조건을 정의할 수 있습니다. 자세한 내용은 [방법: Visual Studio 확장에 대 한 규칙 기반 UI 컨텍스트 사용](../extensibility/how-to-use-rule-based-ui-context-for-visual-studio-extensions.md)을 참조 하세요.

## <a name="diagnose-extension-performance"></a>확장 성능 진단
확장은 시작 및 솔루션 로드 성능에 영향을 줄 수 있습니다. Visual Studio 확장 영향을 계산 하는 방법 및 확장이 성능에 영향을 주는 확장으로 표시 될 수 있는지 여부를 테스트 하기 위해 로컬로 분석 하는 방법에 대해 알아봅니다. 자세한 내용은 [방법: 확장 성능 진단](how-to-diagnose-extension-performance.md)을 참조 하세요.

## <a name="troubleshoot-vspackages"></a>Vspackage 문제 해결
 로드 되지 않거나 오류가 발생 하는 Vspackage 문제를 해결 하는 방법에 대 한 자세한 정보: [문제 해결 vspackage](../extensibility/troubleshooting-vspackages.md)

## <a name="see-also"></a>추가 정보
- [VSPackages](../extensibility/internals/vspackages.md)
