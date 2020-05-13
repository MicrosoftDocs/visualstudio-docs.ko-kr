---
title: 비주얼 스튜디오 SDK | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VSSDK.v90.StartPage
helpviewer_keywords:
- Visual Studio SDK
- VS SDK (see Visual Studio SDK)
- Visual Studio, SDK
ms.assetid: 1f7c348a-114c-4243-b392-3531e9c9c6fd
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 56f772d7d27f11318cdeb0bf365373d5f7c1294b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80698070"
---
# <a name="visual-studio-sdk"></a>Visual Studio SDK
Visual Studio SDK를 사용하면 Visual Studio 기능을 확장하거나 새로운 기능을 Visual Studio에 통합할 수 있습니다. 확장 프로그램을 다른 사용자와 Visual Studio 마켓플레이스에 배포할 수 있습니다. 다음은 Visual Studio를 확장할 수 있는 몇 가지 방법입니다.

- IDE에 명령, 단추, 메뉴 및 기타 UI 요소를 추가합니다.

- 새로운 기능을 위한 도구 창 추가

- 지정된 언어에 대해 IntelliSense를 확장하거나 새로운 프로그래밍 언어에 대한 IntelliSense를 제공합니다.

- 전구를 사용하여 개발자가 더 나은 코드를 작성하는 데 도움이 되는 힌트와 제안 제공

- 새 언어에 대한 지원 사용

- 사용자 지정 프로젝트 유형 추가

- 비주얼 스튜디오 마켓플레이스를 통해 수백만 명의 개발자에게 도달

  이전에 Visual Studio 확장을 작성한 적이 없는 경우 이러한 기능에 대한 자세한 정보와 [Visual Studio 확장 개발 시작시](../extensibility/starting-to-develop-visual-studio-extensions.md)에 대한 자세한 정보를 찾아야 합니다.

## <a name="install-the-visual-studio-sdk"></a>Visual Studio SDK 설치
 비주얼 스튜디오 SDK는 비주얼 스튜디오 설정에서 선택적 기능입니다. 나중에 VS SDK를 설치할 수도 있습니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="whats-new-in-the-visual-studio-2017-sdk"></a>비주얼 스튜디오 2017 SDK의 새로운 내용
 Visual Studio SDK에는 VSIX v3 형식과 같은 몇 가지 새로운 기능과 주요 변경 내용이 포함되어 있어 확장을 업데이트해야 할 수 있습니다. 자세한 내용은 [Visual Studio 2017 SDK의 새로운 정보를](../extensibility/what-s-new-in-the-visual-studio-2017-sdk.md)참조하십시오.

## <a name="visual-studio-user-experience-guidelines"></a>비주얼 스튜디오 사용자 환경 지침
 [Visual Studio 사용자 환경 지침에서](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md)확장을 위한 UI를 디자인하기 위한 훌륭한 팁을 얻을 수 있습니다.

 [주소 DPI 문제](../extensibility/addressing-dpi-issues2.md) 문서를 사용하여 높은 DPI 장치에서 확장 프로그램을 멋지게 보이게 하는 방법도 알아볼 수 있습니다.

 이미지 서비스 [및 카탈로그를](../extensibility/image-service-and-catalog.md) 활용하여 뛰어난 이미지 관리 및 높은 DPI 및 테마를 지원합니다.

## <a name="find-and-install-existing-visual-studio-extensions"></a>기존 Visual Studio 확장 프로그램 찾기 및 설치
 **도구** 메뉴에서 확장 및 **업데이트** 대화 상자에서 Visual Studio 확장을 찾을 수 있습니다. 자세한 내용은 [시각적 스튜디오 확장 찾기 및 사용을](../ide/finding-and-using-visual-studio-extensions.md)참조하십시오. [또한 비주얼 스튜디오 마켓플레이스에서](https://marketplace.visualstudio.com/) 확장을 찾을 수 있습니다.

## <a name="visual-studio-sdk-reference"></a>비주얼 스튜디오 SDK 참조
 비주얼 스튜디오 SDK API 참조는 [Visual Studio SDK 참조에서](../extensibility/visual-studio-sdk-reference.md)찾을 수 있습니다.

## <a name="visual-studio-sdk-samples"></a>비주얼 스튜디오 SDK 샘플
 [비주얼 스튜디오 샘플에서](https://github.com/Microsoft/VSSDK-Extensibility-Samples)GitHub에서 VS SDK 확장의 오픈 소스 예제를 찾을 수 있습니다. 이 GitHub 리포지토리에는 Visual Studio의 다양한 확장 가능한 기능을 보여 주는 샘플이 포함되어 있습니다.

## <a name="other-visual-studio-sdk-resources"></a>기타 비주얼 스튜디오 SDK 리소스
 VSSDK에 대한 질문이 있거나 확장 프로그램을 개발한 경험을 공유하려면 [Visual Studio 확장성 포럼](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vsx) 또는 [ExtendVS Gitter 채팅방을](https://gitter.im/Microsoft/extendvs)사용할 수 있습니다.

 자세한 내용은 [VSX Arcana 블로그와](https://blogs.msdn.microsoft.com/vsx/) Microsoft MVP가 작성한 여러 블로그에서 확인할 수 있습니다.

- [즐겨찾는 비주얼 스튜디오 확장](https://scottdorman.blog/2014/10/05/favorite-visual-studio-extensions/)

- [비주얼 스튜디오 확장성](http://www.visualstudioextensibility.com/overview/vs/)

- [확장 비주얼 스튜디오](https://blog.slaks.net/2013-10-18/extending-visual-studio-part-1-getting-started/)

## <a name="see-also"></a>참조

- [메뉴 명령으로 확장 만들기](../extensibility/creating-an-extension-with-a-menu-command.md)
- [방법: 확장성 프로젝트를 Visual Studio 2017로 마이그레이션](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md)
- [자주 묻는 질문: 추가 기능을 VS패키지 확장으로 변환](/visualstudio/extensibility/faq-converting-add-ins-to-vspackage-extensions?view=vs-2015)
- [관리 코드에서 여러 스레드 관리](../extensibility/managing-multiple-threads-in-managed-code.md)
- [메뉴 및 명령 확장](../extensibility/extending-menus-and-commands.md)
- [도구 모음에 명령 추가](../extensibility/adding-commands-to-toolbars.md)
- [공구 창 확장 및 사용자 지정](../extensibility/extending-and-customizing-tool-windows.md)
- [편집기 및 언어 서비스 확장](../extensibility/editor-and-language-service-extensions.md)
- [프로젝트 확장](../extensibility/extending-projects.md)
- [사용자 설정 및 옵션 확장](../extensibility/extending-user-settings-and-options.md)
- [사용자 지정 프로젝트 및 항목 템플릿 만들기](../extensibility/creating-custom-project-and-item-templates.md)
- [속성 및 속성 창 확장](../extensibility/extending-properties-and-the-property-window.md)
- [비주얼 스튜디오의 다른 부분 확장](../extensibility/extending-other-parts-of-visual-studio.md)
- [서비스 이용 및 제공](../extensibility/using-and-providing-services.md)
- [VSPackage 관리](../extensibility/managing-vspackages.md)
- [비주얼 스튜디오 절연 쉘](https://visualstudio.microsoft.com/vs/older-downloads/isolated-shell/)
- [선박 비주얼 스튜디오 확장](../extensibility/shipping-visual-studio-extensions.md)
- [Visual Studio SDK 기본 사항](../extensibility/internals/inside-the-visual-studio-sdk.md)
- [Visual Studio SDK 지원](../extensibility/support-for-the-visual-studio-sdk.md)
- [비주얼 스튜디오 SDK 참조](../extensibility/visual-studio-sdk-reference.md)
