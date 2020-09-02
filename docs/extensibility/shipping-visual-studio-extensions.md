---
title: Visual Studio 확장 전달 | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80700118"
---
# <a name="shipping-visual-studio-extensions"></a>Visual Studio 확장 전달
확장 개발을 마친 후에는 다른 컴퓨터에 설치 하거나, 친구 및 동료와 공유 하거나, Visual Studio Marketplace에 게시할 수 있습니다. 이 섹션에서는 확장명을 게시 하 고 유지 관리 하기 위해 수행 해야 하는 모든 작업을 설명 합니다. .vsix 파일 작업, 게시, 지역화, 업데이트 등이 있습니다.

## <a name="working-with-vsix-extensions"></a>VSIX 확장 작업
 빈 VSIX 프로젝트를 만든 다음 다른 항목 템플릿을 추가 하 여 VSIX 확장을 만들 수 있습니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조 하세요.

 VSIX 형식을 사용 하 여 프로젝트 템플릿, 항목 템플릿, Vspackage, Managed Extensibility Framework (MEF) 구성 요소, **도구 상자** 컨트롤, 어셈블리 및 사용자 지정 형식 (Visual Studio 2017에 대 한 사용자 지정 시작 페이지 포함)을 패키지할 수 있습니다. VSIX 형식은 파일 기반 배포를 사용 합니다. VSIX 패키지에 대 한 자세한 내용은 [Vsix 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)을 참조 하세요.

 VSIX 형식은 코드 조각의 설치를 지원 하지 않습니다. 또한 GAC (전역 어셈블리 캐시) 또는 시스템 레지스트리에 쓰는 등의 다른 시나리오는 지원 하지 않습니다. 설치에서 GAC 또는 레지스트리에 써야 하는 경우 Windows Installer를 사용 해야 합니다. 자세한 내용은 [Windows Installer 배포를 위한 확장 준비](../extensibility/preparing-extensions-for-windows-installer-deployment.md)를 참조 하세요.

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Visual Studio Marketplace에 확장 게시
 Vsix 파일을 메일로 전송 하거나 서버에 배치 하 여 다른 사람에 게 확장을 배포할 수 있습니다. 그러나 많은 사람들에 게 코드를 제공 하는 가장 좋은 방법은 [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs)에 배치 하는 것입니다. **확장 및 업데이트**를 통해 Visual Studio 사용자가 Visual Studio Marketplace 확장을 사용할 수 있습니다. 자세한 내용은 [Visual Studio 확장 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)을 참조 하세요.

 Visual Studio Marketplace 확장을 업로드 하는 방법을 보여 주는 전체 예제는 [연습: Visual Studio 확장 게시](../extensibility/walkthrough-publishing-a-visual-studio-extension.md)를 참조 하세요.

## <a name="private-galleries"></a>Private Galleries
 컨트롤, 템플릿 및 도구를 개발 하는 경우 인트라넷의 전용 갤러리에 게시 하 여 조직과 공유할 수 있습니다. 자세한 내용은 [개인 갤러리](../extensibility/private-galleries.md)를 참조 하세요.

## <a name="localizing-your-extension"></a>확장 지역화
 확장을 다른 로캘로 릴리스할 계획인 경우 지역화를 고려해 야 합니다. 관련 내용에 대 한 설명은 [VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)를 참조 하세요.

## <a name="updating-and-versioning-your-extension"></a>확장 업데이트 및 버전 관리
 확장을 게시 한 후에는 업데이트 해야 하는 시간이 발생 합니다. Visual Studio Marketplace에 게시 된 확장을 업데이트 하는 방법을 알아보려면 [방법: 확장 업데이트](../extensibility/how-to-update-a-visual-studio-extension.md)를 참조 하세요.

 여러 버전의 Visual Studio를 지원 하도록 확장을 설정할 수 있습니다. 자세한 내용은 [여러 버전의 Visual Studio 지원](../extensibility/supporting-multiple-versions-of-visual-studio.md)을 참조 하세요.

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[VSIX 프로젝트 템플릿 시작](../extensibility/getting-started-with-the-vsix-project-template.md)|VSIX 프로젝트 템플릿을 사용 하 여 사용자 지정 프로젝트 템플릿을 설치 하는 방법을 설명 합니다.|
|[VSIX 패키지 분석](../extensibility/anatomy-of-a-vsix-package.md)|VSIX 패키지의 구성 요소에 대해 설명 합니다.|
|[VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)|확장을 패키지 하 고 게시 하는 방법에 대 한 단계별 지침을 제공 합니다.|
|[VSIX 패키지 지역화](../extensibility/localizing-vsix-packages.md)|Vsixlangpack 파일 확장명을 사용 하 여 설치 프로세스에 대 한 지역화 된 텍스트를 제공 하는 방법을 설명 합니다.|
|[방법: 확장 업데이트](../extensibility/how-to-update-a-visual-studio-extension.md)|시스템에서 확장을 업데이트 하는 방법 및 기존 Visual Studio 확장에 업데이트를 배포 하는 방법을 설명 합니다.|
|[방법: VSIX 패키지에 종속성 추가](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|VSIX 배포 패키지에 대 한 참조를 추가 하는 방법을 설명 합니다.|
|[Windows Installer 배포에 대한 확장 준비](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Windows Installer를 사용 하 여 확장을 배포 하는 방법을 설명 합니다.|
|[VSIX 패키지 서명](../extensibility/signing-vsix-packages.md)|VSIX 패키지에 서명 하는 방법을 설명 합니다.|
|[전용 갤러리](../extensibility/private-galleries.md)|확장에 대 한 개인 갤러리를 만드는 방법을 설명 합니다.|
|[여러 버전의 Visual Studio 지원](../extensibility/supporting-multiple-versions-of-visual-studio.md)|확장에서 여러 버전의 Visual Studio를 지 원하는 방법을 보여 줍니다.|
|[Visual Studio 찾기](locating-visual-studio.md)|사용자 지정 확장 배포를 위한 Visual Studio 인스턴스를 찾는 방법을 설명 합니다.|
