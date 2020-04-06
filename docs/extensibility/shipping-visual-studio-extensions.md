---
title: 비주얼 스튜디오 확장 배송 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700118"
---
# <a name="shipping-visual-studio-extensions"></a>Visual Studio 확장 전달
확장 프로그램을 완료한 후 다른 컴퓨터에 설치하거나 친구 및 동료와 공유하거나 Visual Studio 마켓플레이스에 게시할 수 있습니다. 이 섹션에서는 .vsix 파일 작업, 게시, 지역화 및 업데이트와 같은 확장프로그램을 게시하고 유지하기 위해 수행해야 하는 모든 작업에 대해 설명합니다.

## <a name="working-with-vsix-extensions"></a>VSIX 확장 작업
 빈 VSIX 프로젝트를 만든 다음 다른 항목 템플릿을 추가하여 VSIX 확장을 만들 수 있습니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조하십시오.

 VSIX 형식을 사용하여 프로젝트 템플릿, 항목 템플릿, VSPackage, MEF(관리되는 확장성 프레임워크) 구성 요소, **도구 상자** 컨트롤, 어셈블리 및 사용자 지정 형식을 패키징할 수 있습니다(Visual Studio 2017용 사용자 지정 시작 페이지 포함). VSIX 형식은 파일 기반 배포를 사용합니다. VSIX 패키지에 대한 자세한 내용은 [VSIX 패키지의 해부학을](../extensibility/anatomy-of-a-vsix-package.md)참조하십시오.

 VSIX 형식은 코드 조각 설치를 지원하지 않습니다. 또한 GAC(전역 어셈블리 캐시) 또는 시스템 레지스트리에 쓰기와 같은 특정 다른 시나리오도 지원하지 않습니다. 설치시 GAC 또는 레지스트리에 사용해야 하는 경우 Windows 설치 관리자를 사용해야 합니다. 자세한 내용은 [Windows 설치 관리자 배포에 대한 확장 준비 를](../extensibility/preparing-extensions-for-windows-installer-deployment.md)참조하십시오.

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>비주얼 스튜디오 마켓플레이스에 확장 게시
 .vsix 파일을 우편으로 보내거나 서버에 넣기만 하면 확장 프로그램을 다른 사람에게 배포할 수 있습니다. 그러나 많은 사람들의 손에 코드를 얻는 가장 좋은 방법은 Visual Studio [마켓 플레이스에](https://marketplace.visualstudio.com/vs)넣는 것입니다. 비주얼 스튜디오 마켓플레이스 확장은 확장 및 업데이트를 통해 Visual Studio 사용자가 사용할 수 **있습니다.** 자세한 내용은 [Visual Studio 확장 찾기 및 사용을](../ide/finding-and-using-visual-studio-extensions.md)참조하십시오.

 Visual Studio 마켓플레이스에 확장을 업로드하는 방법을 보여 주는 전체 예제는 [연습: Visual Studio 확장 게시를](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)참조하십시오.

## <a name="private-galleries"></a>Private Galleries
 컨트롤, 템플릿 및 도구를 개발할 때 인트라넷의 개인 갤러리에 게시하여 조직과 공유할 수 있습니다. 자세한 내용은 [개인 갤러리를](../extensibility/private-galleries.md)참조하십시오.

## <a name="localizing-your-extension"></a>확장 지역화
 다른 로캘에서 확장을 릴리스하려는 경우 지역화하는 것이 좋습니다. 관련된 내용에 대한 설명은 [VSIX 패키지 지역화를](../extensibility/localizing-vsix-packages.md)참조하십시오.

## <a name="updating-and-versioning-your-extension"></a>확장 프로그램 업데이트 및 버전 업데이트
 확장 프로그램을 게시한 후 업데이트해야 하는 시간이 있습니다. Visual Studio 마켓플레이스에 게시된 확장을 업데이트하는 방법을 알아보려면 [확장 업데이트 방법을 참조하세요.](../extensibility/how-to-update-a-visual-studio-extension.md)

 여러 버전의 Visual Studio를 지원하도록 확장을 설정할 수 있습니다. 자세한 내용은 [여러 버전의 Visual Studio 를 참조하세요.](../extensibility/supporting-multiple-versions-of-visual-studio.md)

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[VSIX 프로젝트 템플릿 으로 시작하기](../extensibility/getting-started-with-the-vsix-project-template.md)|VSIX 프로젝트 템플릿을 사용하여 사용자 지정 프로젝트 템플릿을 설치하는 방법을 설명합니다.|
|[VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)|VSIX 패키지의 구성 요소에 대해 설명합니다.|
|[VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)|확장을 패키징하고 게시하는 방법에 대한 단계별 지침을 제공합니다.|
|[VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)|extension.vsixlangpack 파일을 사용하여 설치 프로세스에 지역화된 텍스트를 제공하는 방법을 설명합니다.|
|[방법: 확장 업데이트](../extensibility/how-to-update-a-visual-studio-extension.md)|시스템에서 확장을 업데이트하는 방법과 기존 Visual Studio 확장에 업데이트를 배포하는 방법에 대해 설명합니다.|
|[방법: VSIX 패키지에 종속성 추가](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|VSIX 배포 패키지에 참조를 추가하는 방법을 설명합니다.|
|[Windows Installer 배포에 대한 확장 준비](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Windows 설치 관리자를 사용하여 확장을 배포하는 방법을 설명합니다.|
|[VSIX 패키지 서명](../extensibility/signing-vsix-packages.md)|VSIX 패키지에 서명하는 방법을 설명합니다.|
|[전용 갤러리](../extensibility/private-galleries.md)|확장을 위한 개인 갤러리를 만드는 방법을 설명합니다.|
|[여러 버전의 Visual Studio 지원](../extensibility/supporting-multiple-versions-of-visual-studio.md)|확장 프로그램이 여러 버전의 Visual Studio를 지원하도록 하는 방법을 보여 줍니다.|
|[Visual Studio 찾기](locating-visual-studio.md)|사용자 지정 확장 배포를 위해 Visual Studio 인스턴스를 찾는 방법을 설명합니다.|
