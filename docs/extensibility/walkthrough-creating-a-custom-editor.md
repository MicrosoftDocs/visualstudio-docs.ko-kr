---
title: '연습: 사용자 지정 편집기 만들기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697677"
---
# <a name="walkthrough-create-a-custom-editor"></a>연습: 사용자 지정 편집기 만들기
VSPackage 프로젝트 템플릿은 C++에서 간단한 사용자 지정 편집기를 만들 수 있습니다. VSPackage 프로젝트 템플릿은 더 이상 C# 또는 시각적 기본 프로젝트를 지원하지 않습니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK 설치를](../extensibility/installing-the-visual-studio-sdk.md)참조하십시오.

## <a name="the-visual-studio-package-project-template"></a>비주얼 스튜디오 패키지 프로젝트 템플릿
 **C++ 확장성** 폴더 아래의 **새 프로젝트** 대화 상자에서 Visual Studio 패키지 프로젝트 템플릿을 찾을 수 있습니다.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Visual Studio 패키지 템플릿을 사용하여 VSPackage를 만들려면

1. Visual Studio 패키지 템플릿을 사용하여 프로젝트를 만듭니다.

2. 사용자 **지정 편집기** 옵션을 선택하고 다음 을 **클릭합니다.** **편집기 옵션** 페이지가 나타납니다.

3. **편집기 이름** 상자에 편집기 이름을 입력합니다. 파일 확장자 상자에 편집기와 연결하려는 **파일** 확장명익을 입력합니다. 이 확장자 파일에서 편집기에서 사용할 수 있습니다. 파일 확장은 Windows용이 아닌 Visual Studio에만 등록됩니다. 기본 파일 이름 상자에 편집기와 함께 만든 새 문서의 **기본 파일 이름을** 입력합니다.

4. 지정한 폴더에 VSPackage를 만들려면 **마침** 을 클릭합니다.

### <a name="to-test-your-custom-editor"></a>사용자 지정 편집기를 테스트하려면

1. **파일** 메뉴에서 **새로** 를 가리킨 다음 **파일**을 클릭합니다.

2. **새 파일** 대화 상자의 **설치된 템플릿** 창에서 파일 템플릿을 선택한 다음 등록한 파일 형식을 선택합니다.

3. **열기를** 클릭하여 문서를 보고 편집합니다.

     편집기는 잘라내기 및 붙여넣기, 찾기 및 바꾸기 및 오픈 및 로드 작업을 지원합니다.

## <a name="see-also"></a>참조
- [VSPackage](../extensibility/internals/vspackages.md)
