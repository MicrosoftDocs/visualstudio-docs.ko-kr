---
title: 끊어진 참조 문제 해결
ms.date: 03/21/2017
ms.topic: troubleshooting
helpviewer_keywords:
- C# projects, references
- Visual Basic projects, references
- troubleshooting references
- referencing files from projects
- referencing components, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a5116d2487ca9f53c460e1cae8f362f3ff1bcdf8
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75565918"
---
# <a name="troubleshoot-broken-references"></a>끊어진 참조 문제 해결

애플리케이션에서 끊어진 참조를 사용하려고 하면 예외 오류가 생성됩니다. 참조된 구성 요소를 찾을 수 없는 것이 오류의 주된 원인이지만, 참조가 끊어진 것으로 간주되는 여러 상황이 있습니다. 다음 목록에 이러한 경우가 나와 있습니다.

- 프로젝트의 참조 경로가 잘못되었거나 불완전합니다.

- 참조되는 파일이 삭제되었습니다.

- 참조되는 파일의 이름이 바뀌었습니다.

- 네트워크 연결 또는 인증에 실패했습니다.

- 컴퓨터에 설치되지 않은 COM 구성 요소에 대한 참조입니다.

이러한 문제에 대한 해결 방법은 다음과 같습니다.

> [!NOTE]
> 어셈블리의 파일이 프로젝트 파일의 절대 경로를 사용하여 참조됩니다. 따라서 복수 개발자 환경에서 작업하는 사용자는 로컬 환경에서 참조되는 어셈블리를 놓치고 있을 수 있습니다. 이 오류를 피하려면 이러한 경우에 프로젝트 간 참조를 추가하는 것이 좋습니다. 자세한 내용은 [어셈블리를 사용한 프로그래밍](/dotnet/framework/app-domains/programming-with-assemblies)을 참조하세요.

## <a name="reference-path-is-incorrect"></a>참조 경로가 잘못됨

프로젝트가 여러 컴퓨터에서 공유될 경우 구성 요소가 각 컴퓨터에서 서로 다른 디렉터리에 있으면 일부 참조를 찾지 못할 수 있습니다. 참조는 구성 요소 파일 이름으로 저장됩니다(예: *MyComponent*). 참조가 프로젝트에 추가되면 구성 요소 파일의 폴더 위치(예: *C:\MyComponents*)가 **ReferencePath** 프로젝트 속성에 추가됩니다.

프로젝트가 열리면 참조 경로에서 디렉터리를 확인하여 이러한 참조된 구성 요소 파일을 찾으려고 합니다. 구성 요소가 다른 디렉터리(예: *D:\MyComponents*)에 저장된 컴퓨터에서 프로젝트가 열리면 참조를 찾을 수 없고 오류가 **작업 목록**에 표시됩니다.

이 문제를 해결하려면 끊어진 참조를 삭제하고 나서 **참조 추가** 대화 상자를 사용하여 바꿀 수 있습니다. 또 다른 해결 방법은 프로젝트의 속성 페이지에서 **참조 경로** 항목을 사용하고 목록에서 폴더를 수정하여 올바른 위치를 가리키는 것입니다. **참조 경로** 속성은 각 컴퓨터에서 사용자별로 유지됩니다. 따라서 참조 경로를 수정해도 프로젝트의 다른 사용자에게 영향을 미치지 않습니다.

> [!TIP]
> 프로젝트 간 참조에는 이러한 문제가 없습니다. 이런 이유로, 가능한 경우 파일 참조 대신 프로젝트 간 참조를 사용하세요.

### <a name="to-fix-a-broken-project-reference-by-correcting-the-reference-path"></a>참조 경로를 수정하여 끊어진 프로젝트 문제를 해결하려면

1. **솔루션 탐색기**에서 프로젝트 노드를 마우스 오른쪽 단추로 클릭하고 **속성**을 클릭합니다.

   **프로젝트 디자이너**가 표시됩니다.

1. Visual Basic을 사용할 경우 **참조** 페이지를 선택하고 **참조 경로** 단추를 클릭합니다. **참조 경로** 대화 상자에서 참조할 항목이 포함된 폴더의 경로를 **폴더** 필드에 입력하고 **폴더 추가** 단추를 클릭합니다.

    C#을 사용할 경우 **참조 경로** 페이지를 선택합니다. **폴더** 필드에 참조할 항목이 포함된 폴더의 경로를 입력하고 **폴더 추가** 단추를 클릭합니다.

## <a name="referenced-file-has-been-deleted"></a>참조된 파일이 삭제됨

참조되는 파일이 삭제되었고 더 이상 드라이브에 없을 수 있습니다.

### <a name="to-fix-a-broken-project-reference-for-a-file-that-no-longer-exists-on-your-drive"></a>더 이상 드라이브에 없는 파일에 대한 끊어진 프로젝트 참조를 해결하려면

- 참조를 삭제합니다.

- 참조가 컴퓨터의 또 다른 위치에 있으면 이 위치에서 참조를 읽으세요.

## <a name="referenced-file-has-been-renamed"></a>참조된 파일의 이름이 바뀜

참조되는 파일의 이름이 바뀌었을 수 있습니다.

### <a name="to-fix-a-broken-reference-for-a-file-that-has-been-renamed"></a>이름이 바뀐 파일에 대한 끊어진 참조를 해결하려면

- 참조를 삭제하고 나서 이름이 바뀐 파일에 참조를 추가합니다.

- 참조가 컴퓨터의 또 다른 위치에 있으면 이 위치에서 참조를 읽어야 합니다.

## <a name="network-connection-or-authentication-has-failed"></a>네트워크 연결 또는 인증에 실패함

파일에 액세스할 수 없는 경우 네트워크 연결 실패 또는 인증 실패 등의 다양한 원인이 있을 수 있습니다. 각 원인에는 고유한 복구 방법이 있습니다. 예를 들어 필요한 리소스에 액세스하려면 로컬 관리자에게 문의해야 합니다. 하지만 참조를 삭제하고 참조를 사용한 코드를 수정할 수도 있습니다.

## <a name="com-component-is-not-installed-on-computer"></a>COM 구성 요소가 컴퓨터에 설치되지 않음

사용자가 COM 구성 요소에 대한 참조를 추가했고 두 번째 사용자가 이 구성 요소가 설치되지 않은 컴퓨터에서 코드를 실행하려고 하면 두 번째 사용자에게 참조가 끊어졌다는 오류 메시지가 표시됩니다. 두 번째 컴퓨터에 구성 요소를 설치하면 오류가 수정됩니다. 프로젝트에서 COM 구성 요소 참조를 사용하는 방법에 대한 자세한 내용은 [.NET Framework 애플리케이션의 COM 상호 운용성](/dotnet/visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications)을 참조하세요.

## <a name="see-also"></a>참고 항목

- [프로젝트 디자이너, 참조 페이지(Visual Basic)](../ide/reference/references-page-project-designer-visual-basic.md)
