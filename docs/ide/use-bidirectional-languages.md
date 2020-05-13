---
title: 아랍어 및 히브리어 지원
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- Hebrew character display [Visual Studio]
- bidirectional language support
- Arabic, creating applications
ms.assetid: b56f9795-ed8d-4452-9d49-8ca0b0145d86
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 57bccfccb77c5a80fd2630680564f88f08d7ca5b
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591998"
---
# <a name="support-for-bidirectional-languages-in-visual-studio"></a>Visual Studio에서 양방향 언어에 대한 지원

Visual Studio는 아랍어 및 히브리어 텍스트를 올바르게 표시할 수 있으며 개체 이름 및 값에 양방향 텍스트를 입력할 수 있습니다.

> [!NOTE]
> 양방향 언어를 입력 및 표시하려면 적절한 언어로 구성된 Windows 버전을 사용해야 합니다. 적절한 언어 팩이 설치된 Windows 영어 버전 또는 적절히 지역화된 Windows 버전 중 하나일 수 있습니다.

## <a name="fully-supported-features"></a>완전히 지원되는 기능

Visual Studio에서 디자인 시 텍스트를 입력하고 개체 이름을 지정하거나 파일을 저장하고 열 때 양방향 언어를 사용할 수 있습니다.

### <a name="text-entry"></a>텍스트 항목

Visual Studio는 유니코드를 지원하므로 시스템이 적절한 로캘 및 입력 언어로 설정되면 아랍어 또는 히브리어로 텍스트를 입력할 수 있습니다. 아랍어 지원에는 Kashida 및 분음 부호가 포함됩니다.

### <a name="arabic-or-hebrew-object-names"></a>아랍어 또는 히브리어 개체 이름

양방향 언어를 사용하여 솔루션, 프로젝트, 파일, 폴더 등에 이름을 할당할 수 있습니다. 코드에서 변수, 클래스, 개체, 특성, 메타데이터 및 기타 요소의 이름에 양방향 언어를 사용할 수 있습니다. 아랍어를 사용할 경우 Kashida 및 분음 부호를 비롯한 아랍어 문자를 사용할 수 있습니다.

다음 요소는 아랍어 또는 히브리어를 사용하여 이름을 지정할 수 있고 Visual Studio에서 올바르게 처리됩니다.

- 프로젝트 경로에 포함하는 폴더를 비롯한 솔루션, 프로젝트 및 파일 이름.

   **솔루션 탐색기**에는 솔루션 및 요소 이름이 제대로 표시됩니다.

- 파일 콘텐츠.

   유니코드 인코딩 또는 선택된 코드 페이지를 사용하여 파일을 열거나 저장할 수 있습니다.

- 데이터 요소.

   **서버 탐색기**는 이러한 요소를 제대로 표시하고 편집할 수 있습니다.

- Windows 클립보드에 복사된 요소.

- 특성 및 메타데이터.

- 속성 값

   **속성** 창에서 아랍어 또는 히브리어 텍스트를 사용할 수 있습니다. 이 창에서 표준 Windows 키 입력(오른쪽에서 왼쪽의 경우 **Ctrl**+**RightShift**, 왼쪽에서 오른쪽의 경우 **Ctrl**+**LeftShift**)을 사용하여 오른쪽에서 왼쪽 순서와 왼쪽에서 오른쪽 순서 간에 전환할 수 있습니다.

- 코드 및 리터럴 텍스트.

   코드 편집기에서 아랍어 또는 히브리어를 사용하여 클래스, 함수, 변수, 속성, 문자열, 리터럴, 특성 등의 이름을 지정할 수 있습니다. 그러나 이 편집기는 오른쪽에서 왼쪽 읽기 순서를 지원하지 않고 텍스트는 항상 왼쪽 여백에서 시작됩니다.

   > [!TIP]
   > 문자열 리터럴을 프로그램에 하드 코딩하는 대신 리소스 파일에 배치해야 합니다. 자세한 내용은 [데스크톱 앱의 리소스(.NET Framework)](/dotnet/framework/resources/index)를 참조하세요.

   > [!NOTE]
   > 아랍어 및 히브리어로 명명된 개체를 참조하는 방법에 일관성이 있어야 합니다. 예를 들어 아랍어 변수 이름을 지정하는 데 Kashida를 사용할 경우 해당 변수를 참조할 때 항상 Kashida를 사용해야 합니다. 그렇지 않으면 오류가 발생합니다.

- 코드 주석입니다. 아랍어 또는 히브리어로 주석을 만들 수 있습니다. 주석 작성기 도구에서도 이러한 언어를 사용할 수 있습니다.

### <a name="file-encoding"></a>파일 인코딩

언어별 또는 유니코드 인코딩을 사용하여 파일을 저장하고 열 수 있습니다. 자세한 내용은 [방법: 인코딩을 사용하여 파일 저장 및 열기](../ide/how-to-save-and-open-files-with-encoding.md)를 참조하세요.

## <a name="right-to-left-reading-order"></a>오른쪽에서 왼쪽 읽기 순서

Visual Studio에서는 오른쪽에서 왼쪽 읽기 순서가 제한적으로 지원됩니다. 기본적으로 Visual Studio의 텍스트 입력 컨트롤에는 왼쪽에서 오른쪽 읽기 순서가 사용됩니다. 대부분의 경우 표준 Windows 제스처를 사용하여 읽기 순서를 전환할 수 있습니다. 예를 들어 **Ctrl**+**RightShift**를 눌러 속성 값에 대한 오른쪽에서 왼쪽 읽기 순서를 지원하도록 **속성** 창을 전환할 수 있습니다.

Visual Studio에서 다음 경우에는 오른쪽에서 왼쪽 읽기 순서가 지원되지 않습니다.

- Visual Studio 대화 상자의 확인란, 드롭다운 목록 및 기타 컨트롤에는 항상 왼쪽에서 오른쪽 읽기 순서가 사용됩니다.

- 코드 편집기(및 텍스트 편집기)는 오른쪽에서 왼쪽 읽기 순서를 지원하지 않습니다. 양방향 언어로 텍스트를 입력할 수 있지만 읽기 순서는 항상 왼쪽에서 오른쪽입니다.

## <a name="see-also"></a>참고 항목

- [세계화 및 지역화된 앱 개발](globalizing-and-localizing-applications.md)
