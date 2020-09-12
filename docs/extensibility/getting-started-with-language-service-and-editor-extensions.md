---
title: 언어 서비스 및 편집기 확장 시작
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 55d9f018324c32a8b39c96037058593cebf52bc2
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/11/2020
ms.locfileid: "90037766"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>언어 서비스 및 편집기 확장 시작

편집기 확장을 사용 하 여 개요, 중괄호 일치, IntelliSense, light 전구 등의 언어 서비스 기능을 자체 프로그래밍 언어 또는 모든 콘텐츠 형식에 추가할 수 있습니다. 텍스트 색 지정, 여백, 장식 및 기타 시각적 요소와 같은 Visual Studio 편집기의 모양과 동작을 사용자 지정할 수도 있습니다. 사용자 고유의 콘텐츠 형식을 정의 하 고 콘텐츠가 표시 되는 텍스트 보기의 모양과 동작을 지정할 수도 있습니다.

 편집기 확장 작성을 시작 하려면 Visual Studio SDK의 일부로 설치 된 편집기 프로젝트 템플릿을 사용 합니다. Visual Studio SDK는 Vspackage을 사용 하거나 MEF (Managed Extensibility Framework)를 사용 하 여 Visual Studio 확장을 보다 쉽게 개발할 수 있도록 하는 다운로드 가능한 도구 집합입니다.

> [!NOTE]
> Visual Studio SDK에 대 한 자세한 내용은 [Visual STUDIO sdk](../extensibility/visual-studio-sdk.md)를 참조 하세요.

 편집기 확장을 직접 작성 하기 전에 다음 개념 및 기술에 대해 알아보는 것이 좋습니다.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) 및 편집기 확장

 Visual Studio 편집기 UI (사용자 인터페이스)는 Windows Presentation Foundation (WPF)를 사용 하 여 구현 됩니다. WPF는 비즈니스 논리와 코드의 시각적 측면을 분리 하는 일관적인 시각적 환경 및 일관적인 프로그래밍 모델을 제공 합니다. 편집기 확장을 만들 때 많은 WPF 요소 및 기능을 사용할 수 있습니다. 자세한 내용은 [Windows Presentation Foundation](/dotnet/framework/wpf/index)를 참조 하세요.

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) 및 편집기 확장

 Visual Studio 편집기는 MEF (Managed Extensibility Framework)를 사용 하 여 해당 구성 요소와 확장 프로그램을 관리 합니다. 또한 MEF를 사용 하면 개발자가 Visual Studio와 같은 호스트 응용 프로그램에 대 한 확장을 보다 쉽게 만들 수 있습니다. 이 프레임 워크에서는 MEF 계약에 따라 확장을 정의 하 고 MEF 구성 요소 파트로 내보냅니다. 호스트 응용 프로그램은 구성 요소를 찾아서 등록 하 고 올바른 컨텍스트에 적용 되는지 확인 하 여 구성 요소 부분을 관리 합니다.

> [!NOTE]
> 편집기의 MEF에 대 한 자세한 내용은 [편집기에서 Managed Extensibility Framework](../extensibility/managed-extensibility-framework-in-the-editor.md)를 참조 하세요.

## <a name="visual-studio-editor-extension-points-and-extensions"></a>Visual Studio 편집기 확장 지점과 확장

 편집기 확장 지점은 사용자 지정 하 고 확장할 수 있는 MEF 구성 요소 부분입니다. 일부 경우에는 인터페이스를 구현 하 고 올바른 메타 데이터와 함께 내보내 확장 지점을 확장 합니다. 다른 경우에는 확장을 선언 하 고 특정 형식으로 내보냅니다.

 다음은 편집기 확장의 몇 가지 기본 종류입니다.

- 여백 및 스크롤 막대

- Tags

- 도구 영역

- 옵션

- IntelliSense

  편집기 확장 요소에 대 한 자세한 내용은 [언어 서비스 및 편집기 확장 요소](../extensibility/language-service-and-editor-extension-points.md)를 참조 하세요.

## <a name="deploying-editor-extensions"></a>편집기 확장 배포

 Visual Studio에서 솔루션에 *source.extension.vsixmanifest* 이라는 메타 데이터 파일을 추가 하 고, 솔루션을 빌드한 다음, visual studio에 알려진 폴더에 이진 파일 및 매니페스트의 복사본을 추가 하 여 편집기 확장을 배포 합니다. 매니페스트 파일은 확장명에 대 한 기본 팩트 (예: 이름, 작성자, 버전 및 콘텐츠 형식)를 정의 합니다. VSIX 매니페스트 파일 및 확장을 배포 하는 방법에 대 한 자세한 내용은 [Visual Studio 확장 제공](../extensibility/shipping-visual-studio-extensions.md)을 참조 하세요.

 컴퓨터에 확장을 설치 하는 경우 Visual Studio에 알려진 폴더의 하위 폴더에 이진 파일 및 매니페스트를 포함 합니다.

> [!WARNING]
> Visual Studio에 포함 된 편집기 확장성 템플릿 중 하나를 사용 하는 경우 매니페스트 및 배포 위치에 대 한 세부 정보를 걱정 하지 않아도 됩니다. 템플릿에는 확장을 등록 하 고 배포 하는 데 필요한 모든 항목이 포함 되어 있습니다.

## <a name="run-extensions-in-the-experimental-instance"></a>실험적 인스턴스에서 확장 실행

 확장을 개발 하는 동안 Visual Studio의 작업 버전을 다음과 같은 실험적 폴더 (Windows Vista 및 Windows 7)에 배포할 수 있습니다.

 *{% LOCALAPPDATA%} \VisualStudio\10.0Exp\Extensions \\ {Company} \\ {extensionid}*

 여기서 *% LOCALAPPDATA%* 는 로그온 한 사용자의 이름이 고, *company* 는 확장을 소유 하는 회사의 이름이 고, *EXTENSIONID* 는 확장의 id입니다.

 실험적 위치에 확장을 배포 하는 경우 디버그 모드에서 실행 됩니다. Visual Studio의 두 번째 인스턴스가 시작 되 고 **Microsoft Visual Studio 실험적 인스턴스로**이름이 지정 됩니다.

## <a name="manage-extensions"></a>확장 관리

 Visual Studio에 대 한 확장은 **확장 및 업데이트** ( **도구** 메뉴)에 나열 되어 있습니다. 실험적 인스턴스에서 확장을 테스트 하는 경우 실험적 인스턴스의 **확장 및 업데이트** 에 나열 되지만 개발 인스턴스에는 나열 되지 않습니다.

 자세한 내용은 [Visual Studio 확장 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)을 참조 하세요.

## <a name="use-templates-to-create-editor-extensions"></a>템플릿을 사용 하 여 편집기 확장 만들기

 편집기 템플릿을 사용 하 여 분류자, 장식 및 여백을 사용자 지정 하는 MEF 확장을 만들 수 있습니다. C # 및 Visual Basic 프로젝트에 대 한 템플릿이 있습니다. 자세한 내용은 [편집기 항목 템플릿을 사용 하 여 확장 만들기](../extensibility/creating-an-extension-with-an-editor-item-template.md)를 참조 하세요.

 VSIX 프로젝트 템플릿을 사용 하 여 확장을 만들 수도 있습니다. 이 템플릿은 모든 종류의 확장을 배포 하는 데 필요한 요소만 제공 하며 *source.extension.vsixmanifest* 파일, 필요한 어셈블리 참조 및 확장을 배포할 수 있는 빌드 작업을 포함 하는 프로젝트 파일을 포함 합니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조하세요.

 Visual Studio 패키지 확장에서 편집기 MEF 구성 요소를 만들 수도 있습니다. 자세한 내용은 다음 연습을 참조 하세요.

- [연습: 편집기 확장에서 셸 명령 사용](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [연습: 편집기 확장을 사용 하 여 바로 가기 키 사용](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>참고 항목

- [언어 서비스 및 편집기 확장 위치](../extensibility/language-service-and-editor-extension-points.md)
