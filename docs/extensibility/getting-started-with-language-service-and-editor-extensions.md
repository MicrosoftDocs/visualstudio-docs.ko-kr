---
title: 언어 서비스 및 편집자 확장 시작하기 | 마이크로 소프트 문서
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
ms.openlocfilehash: 7894efc477e0c406cf8e85f4d3d31df4f2ef97c5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711305"
---
# <a name="get-started-with-language-service-and-editor-extensions"></a>언어 서비스 및 편집기 확장 시작
편집기 확장을 사용하여 개요, 중괄호 일치, IntelliSense 및 전구와 같은 언어 서비스 기능을 자체 프로그래밍 언어 또는 콘텐츠 유형에 추가할 수 있습니다. 텍스트 색칠, 여백, 장식 및 기타 시각적 요소와 같은 Visual Studio 편집기의 모양과 동작을 사용자 지정할 수도 있습니다. 사용자 고유의 콘텐츠 유형을 정의하고 콘텐츠가 표시되는 텍스트 보기의 모양과 동작을 지정할 수도 있습니다.

 편집기 확장 작성을 시작하려면 Visual Studio SDK의 일부로 설치된 편집기 프로젝트 템플릿을 사용합니다. Visual Studio SDK는 VSPackage를 사용하거나 MEF(관리되는 확장성 프레임워크)를 사용하여 Visual Studio 확장을 보다 쉽게 개발할 수 있는 다운로드 가능한 도구 집합입니다.

> [!NOTE]
> 비주얼 스튜디오 SDK에 대한 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

 직접 편집기 확장을 작성하기 전에 다음 개념과 기술에 대해 알아보는 것이 좋습니다.

## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>윈도우 프리젠 테이션 재단 (WPF) 및 편집기 확장
 비주얼 스튜디오 편집기 사용자 인터페이스(UI)는 WPF(Windows 프레젠테이션 파운데이션)를 사용하여 구현됩니다. WPF는 풍부한 시각적 환경과 코드의 시각적 측면을 비즈니스 논리와 구분하는 일관된 프로그래밍 모델을 제공합니다. 편집기 확장을 만들 때 많은 WPF 요소 및 기능을 사용할 수 있습니다. 자세한 내용은 [Windows 프레젠테이션 재단](/dotnet/framework/wpf/index)을 참조하십시오.

## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>관리되는 확장성 프레임워크(MEF) 및 편집기 확장
 Visual Studio 편집기는 관리되는 확장성 프레임워크(MEF)를 사용하여 구성 요소 및 확장을 관리합니다. 또한 MEF를 사용하면 개발자가 Visual Studio와 같은 호스트 응용 프로그램에 대한 확장을 보다 쉽게 만들 수 있습니다. 이 프레임워크에서는 MEF 계약에 따라 확장을 정의하고 MEF 구성 요소 부품으로 내보냅니다. 호스트 응용 프로그램은 구성 요소 부분을 찾고 등록하고 올바른 컨텍스트에 적용하여 구성 요소를 관리합니다.

> [!NOTE]
> 편집기의 MEF에 대한 자세한 내용은 [편집기의 관리되는 확장성 프레임워크를](../extensibility/managed-extensibility-framework-in-the-editor.md)참조하십시오.

## <a name="visual-studio-editor-extension-points-and-extensions"></a>비주얼 스튜디오 편집기 확장 지점 및 확장
 편집기 확장 점은 사용자 지정하고 확장할 수 있는 MEF 구성 요소 부품입니다. 경우에 따라 인터페이스를 구현 하 고 올바른 메타 데이터와 함께 내보내기 하 여 확장 점을 확장 합니다. 다른 경우에는 확장을 선언하고 특정 유형으로 내보내기만 하면 됩니다.

 다음은 편집기 확장의 기본 종류 중 일부입니다.

- 여백 및 스크롤 막대

- 태그들

- 장식

- 옵션

- IntelliSense

  편집기 확장 지점에 대한 자세한 내용은 [언어 서비스 및 편집기 확장 지점을](../extensibility/language-service-and-editor-extension-points.md)참조하십시오.

## <a name="deploying-editor-extensions"></a>편집기 확장 배포
 Visual Studio에서는 *source.extension.vsixmanifest라는* 메타데이터 파일을 솔루션에 추가하고 솔루션을 빌드한 다음 Visual Studio에 알려진 폴더에 이진 파일및 매니페스트의 복사본을 추가하여 편집기 확장을 배포합니다. 매니페스트 파일은 확장에 대한 기본 팩트(예: 이름, 작성자, 버전 및 콘텐츠 유형)를 정의합니다. VSIX 매니페스트 파일 및 확장 프로그램을 배포하는 방법에 대한 자세한 내용은 [Ship Visual Studio 확장프로그램을](../extensibility/shipping-visual-studio-extensions.md)참조하십시오.

 컴퓨터에 확장을 설치할 때 Visual Studio에 알려진 폴더의 하위 폴더에 바이너리와 매니페스트를 포함합니다.

> [!WARNING]
> Visual Studio에 포함된 편집기 확장성 템플릿 중 하나를 사용하는 경우 매니페스트 및 배포 위치에 대한 세부 정보에 대해 걱정할 필요가 없습니다. 템플릿에는 확장을 등록하고 배포하는 데 필요한 모든 것이 포함되어 있습니다.

## <a name="run-extensions-in-the-experimental-instance"></a>실험 인스턴스에서 확장 실행
 다음 실험 폴더(Windows Vista 및 Windows 7)에 배포하여 확장을 개발하는 동안 작업 버전의 Visual Studio를 절연할 수 있습니다.

 *{%LOCALAPPDATA%}\비주얼스튜디오\10.0Exp\확장\\{회사}\\{확장 ID}*

 *여기서 %LOCALAPPDATA%는* 로그온한 사용자의 이름이며, *회사는* 확장을 소유한 회사의 이름이며 *ExtensionID는* 확장의 ID입니다.

 실험 위치에 확장을 배포하면 디버그 모드에서 실행됩니다. Visual Studio의 두 번째 인스턴스가 시작되고 **Microsoft Visual Studio - 실험 인스턴스로**명명됩니다.

## <a name="manage-extensions"></a>확장 관리
 Visual Studio에 대한 확장은 **확장 및 업데이트(도구** 메뉴)에 나열됩니다. **Tools** 실험 인스턴스에서 확장을 테스트하는 경우 확장 **및 업데이트에** 실험 인스턴스에 나열되지만 개발 인스턴스에는 나열되지 않습니다.

 자세한 내용은 [Visual Studio 확장 찾기 및 사용을](../ide/finding-and-using-visual-studio-extensions.md)참조하십시오.

## <a name="use-templates-to-create-editor-extensions"></a>템플릿을 사용하여 편집기 확장 만들기
 편집기 템플릿을 사용하여 분류자, 장식 및 여백을 사용자 지정하는 MEF 확장을 만들 수 있습니다. C# 및 Visual Basic 프로젝트에 대한 템플릿이 있습니다. 자세한 내용은 [편집기 항목 템플릿을 사용하여 확장 만들기를](../extensibility/creating-an-extension-with-an-editor-item-template.md)참조하십시오.

 VSIX 프로젝트 템플릿을 사용하여 확장을 만들 수도 있습니다. 이 템플릿은 모든 종류의 확장을 배포하는 데 필요한 요소만 제공하며 *source.extension.vsixmanifest* 파일, 필요한 어셈블리 참조 및 확장프로그램을 배포할 수 있는 빌드 작업을 포함하는 프로젝트 파일을 포함합니다. 자세한 내용은 [VSIX 프로젝트 템플릿](../extensibility/vsix-project-template.md)을 참조하십시오.

 Visual Studio 패키지 확장에서 편집기 MEF 구성 요소를 만들 수도 있습니다. 자세한 내용은 다음 연습을 참조하십시오.

- [연습: 편집기 확장이 있는 셸 명령 사용](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)

- [연습: 편집기 확장이 있는 바로 가기 키 사용](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)

## <a name="see-also"></a>참조
- [언어 서비스 및 편집기 확장 지점](../extensibility/language-service-and-editor-extension-points.md)
