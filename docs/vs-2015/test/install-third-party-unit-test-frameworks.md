---
title: 타사 단위 테스트 프레임워크 설치 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
ms.assetid: 47893b70-46f8-49dc-84bd-ec820178f683
caps.latest.revision: 12
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c2bd087dc0b06cbf8ffe4c08f84d819e8ef1c2f8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660521"
---
# <a name="install-third-party-unit-test-frameworks"></a>타사 단위 테스트 프레임워크 설치
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 테스트 탐색기는 탐색기의 어댑터 인터페이스를 개발한 단위 테스트 프레임워크를 실행할 수 있습니다. 프레임워크 설치 프로그램은 이진 파일을 설치하고, 지원하는 언어의 Visual Studio 프로젝트 템플릿을 추가합니다. 템플릿으로 프로젝트를 만들면 프레임워크가 테스트 탐색기에 등록됩니다. Visual Studio 솔루션에는 다양한 프레임워크를 사용하고 다양한 언어로 대상이 지정되는 단위 테스트 프로젝트가 포함될 수 있습니다. 테스트 탐색기는 이들 모두를 실행합니다.

 **요구 사항**

- Visual Studio Enterprise, Visual Studio Professional

## <a name="acquiring-third-party-frameworks"></a>타사 프레임워크 확보
 Visual Studio 확장 관리자 또는 MSDN 웹 사이트의 Visual Studio 갤러리를 통해 많은 타사 단위 테스트 프레임워크를 다운로드하고 설치할 수 있습니다. 프레임워크 웹 사이트와 같은 다른 사이트에서도 프레임워크를 다운로드할 수 있습니다.

### <a name="installing-from-visual-studio"></a>Visual Studio에서 설치

1. 표준 메뉴에서 **도구**를 선택하고 **확장명 및 업데이트**를 선택합니다.

2. **온라인**, **Visual Studio 갤러리**, **도구**를 확장합니다. **테스트**를 선택합니다.

3. 목록에서 프레임워크를 찾습니다.

4. 프레임워크를 선택하고 **다운로드**를 선택합니다.

   자세한 내용은 [Visual Studio 확장명 찾기 및 사용](../ide/finding-and-using-visual-studio-extensions.md)을 참조하세요.

### <a name="installing-from-the-web"></a>웹에서 설치
 관심 있는 프레임워크를 알고 있는 경우:

1. [Visual Studio Marketplace](https://marketplace.visualstudio.com)를 엽니다.

2. **찾기** 상자에 프레임워크 이름을 입력합니다.

3. 결과 목록에서 프레임워크를 선택하여 해당 도구의 Visual Studio 갤러리 페이지로 이동합니다.

   다른 테스트 도구와 프레임워크 목록을 찾아보려면:

4. [Visual Studio Marketplace](https://marketplace.visualstudio.com)를 엽니다.

5. **찾아보기**를 선택 합니다.

6. **범주** 목록에서 **도구** 노드를 확장하고 **테스트**를 선택합니다.

7. 결과 목록에서 프레임워크를 선택하여 해당 도구의 Visual Studio 갤러리 페이지로 이동합니다.

## <a name="see-also"></a>관련 항목
 [코드 단위 테스트](../test/unit-test-your-code.md)
