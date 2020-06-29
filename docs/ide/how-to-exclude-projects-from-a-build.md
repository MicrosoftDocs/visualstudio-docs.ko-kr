---
title: '방법: 빌드에서 프로젝트 제외'
ms.date: 11/04/2016
ms.technology: vs-ide-compile
ms.topic: how-to
ms.assetid: 17a837ca-5db9-46cd-b5a7-b14ad1d2c47d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c30dd912378fd933d29bff1d8828f31de58f9afa
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85284323"
---
# <a name="how-to-exclude-projects-from-a-build"></a>방법: 빌드에서 프로젝트 제외

포함된 일부 프로젝트를 빌드하지 않고도 솔루션을 빌드할 수 있습니다. 예를 들어, 빌드를 중단하는 프로젝트를 제외할 수 있습니다. 그런 다음 문제를 조사하고 해결한 후 프로젝트를 빌드할 수 있습니다.

다음 방법을 사용하여 프로젝트를 제외할 수 있습니다.

- 활성 솔루션 구성에서 일시적으로 제거

- 해당 프로젝트를 포함하지 않는 솔루션 구성 만들기

자세한 내용은 [빌드 구성 이해](../ide/understanding-build-configurations.md)를 참조하세요.

## <a name="to-temporarily-remove-a-project-from-the-active-solution-configuration"></a>활성 솔루션 구성에서 프로젝트를 일시적으로 제거하려면

1. 메뉴 모음에서 **빌드** > **구성 관리자**를 선택합니다.

2. **프로젝트 컨텍스트** 테이블에서 빌드에서 제외할 프로젝트를 찾습니다.

3. 해당 프로젝트의 **빌드** 열에서 확인란의 선택을 취소합니다.

4. **닫기** 단추를 선택한 후 솔루션을 다시 빌드합니다.

## <a name="to-create-a-solution-configuration-that-excludes-a-project"></a>프로젝트가 제외된 솔루션 구성을 만들려면

1. 메뉴 모음에서 **빌드** > **구성 관리자**를 선택합니다.

2. **활성 솔루션 구성** 목록에서 **\<New>** 를 선택합니다.

3. **이름** 상자에 솔루션 구성의 이름을 입력합니다.

4. **다음에서 설정 복사** 목록에서 새 구성의 기반으로 사용할 솔루션 구성(예: **디버그**)을 선택한 다음 **확인** 단추를 선택합니다.

5. **구성 관리자** 대화 상자에서 제외할 프로젝트에 대한 **빌드** 열의 확인란을 선택 취소하고 **닫기** 단추를 선택합니다.

6. **표준** 도구 모음에서 새 솔루션 구성이 **솔루션 구성** 상자의 활성 구성인지 확인합니다.

7. 메뉴 모음에서 **빌드** > **솔루션 다시 빌드**를 선택합니다.

## <a name="skipped-projects"></a>건너뛴 프로젝트

프로젝트가 최신이 아니기 때문이거나 구성에서 제외되었기 때문에 빌드하는 동안 프로젝트를 건너뛸 수 있습니다. Visual Studio는 MSBuild를 사용하여 프로젝트를 빌드합니다. MSBuild는 파일 타임스탬프에 의해 결정된 대로 출력이 입력보다 오래된 경우에만 대상을 빌드합니다. 다시 빌드를 강제로 수행하려면 **빌드** > **다시 빌드 솔루션** 명령을 사용하세요.

**출력** 창의 **빌드** 창에서 Visual Studio는 최신 상태였던 프로젝트 수, 성공적으로 빌드된 횟수, 실패했던 횟수 및 건너뛴 횟수를 보고합니다. 건너뛴 횟수에는 프로젝트가 최신 상태였기 때문에 빌드되지 않은 프로젝트는 포함되지 않습니다. 프로젝트가 활성 구성에서 제외된 경우 빌드하는 동안 건너뜁니다. 빌드 출력에 프로젝트를 건너뛴다는 메시지가 표시됩니다.

```output
2>------ Skipped Build: Project: ConsoleApp2, Configuration: Debug x86 ------
2>Project not selected to build for this solution configuration
```

프로젝트를 건너뛴 이유를 확인하려면 활성 구성(이전 예시의 `Debug x86`)을 확인하고 **빌드** > **구성 관리자**를 선택합니다. 이 문서에서 설명한 대로 각 구성에 대해 건너뛰는 프로젝트를 보거나 변경할 수 있습니다.

## <a name="see-also"></a>참조

- [빌드 구성 이해](../ide/understanding-build-configurations.md)
- [방법: 구성 만들기 및 편집](../ide/how-to-create-and-edit-configurations.md)
- [방법: 여러 구성 동시 빌드](../ide/how-to-build-multiple-configurations-simultaneously.md)
