---
title: '연습: 사용자 지정 편집기 만들기 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4713931d70fd91dd57b85bc6fc749e62e03eb20b
ms.sourcegitcommit: 05487d286ed891a04196aacd965870e2ceaadb68
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85905919"
---
# <a name="walkthrough-create-a-custom-editor"></a>연습: 사용자 지정 편집기 만들기
VSPackage 프로젝트 템플릿은 c + +로 간단한 사용자 지정 편집기를 만들 수 있습니다. VSPackage 프로젝트 템플릿은 c # 또는 Visual Basic 프로젝트를 더 이상 지원 하지 않습니다. 자세한 내용은 [Visual STUDIO SDK](../extensibility/visual-studio-sdk.md)를 참조 하세요.

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual STUDIO SDK 설치](../extensibility/installing-the-visual-studio-sdk.md)를 참조 하세요.

## <a name="the-visual-studio-package-project-template"></a>Visual Studio 패키지 프로젝트 템플릿
 Visual Studio 패키지 프로젝트 템플릿은 **c + + 확장성** 폴더 아래의 **새 프로젝트** 대화 상자에서 찾을 수 있습니다.

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Visual Studio 패키지 템플릿을 사용 하 여 VSPackage를 만들려면

1. Visual Studio 패키지 템플릿을 사용 하 여 프로젝트를 만듭니다.

2. **사용자 지정 편집기** 옵션을 선택 하 고 **다음**을 클릭 합니다. **편집기 옵션** 페이지가 나타납니다.

3. 편집기 **이름** 상자에 편집기의 이름을 입력 합니다. **파일 확장명** 상자에서 편집기와 연결 하려는 파일 확장명을 입력 합니다. 이 확장명을 가진 파일에 편집기를 사용할 수 있습니다. 파일 확장명은 Windows가 아닌 Visual Studio에만 등록 됩니다. 편집기를 사용 하 여 만든 새 문서의 기본 파일 이름을 **기본 파일 이름** 상자에 입력 합니다.

4. 지정한 폴더에 VSPackage를 만들려면 **마침** 을 클릭합니다.

### <a name="to-test-your-custom-editor"></a>사용자 지정 편집기를 테스트 하려면

1. **파일** 메뉴에서 **새로 만들기** 를 가리킨 다음 **파일**을 클릭 합니다.

2. **새 파일** 대화 상자의 **설치 된 템플릿** 창에서 파일 템플릿을 선택 하 고 등록 한 파일 형식을 선택 합니다.

3. **열기** 를 클릭 하 여 문서를 보고 편집 합니다.

     편집기는 잘라내기 및 붙여넣기, 찾기 및 바꾸기, 열기 및 로드 작업을 지원 합니다.

## <a name="see-also"></a>참조
- [VSPackage](../extensibility/internals/vspackages.md)
