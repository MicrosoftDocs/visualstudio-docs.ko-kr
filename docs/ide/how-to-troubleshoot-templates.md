---
title: 프로젝트 템플릿 및 항목 템플릿의 로드 문제 해결
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bef6a460f1a59823930597565b955b591ab48a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591387"
---
# <a name="how-to-troubleshoot-templates"></a>방법: 템플릿 문제 해결

개발 환경에서 템플릿을 로드할 수 없는 경우 여러 가지 방법으로 문제를 찾을 수 있습니다.

## <a name="validate-the-vstemplate-file"></a>vstemplate 파일의 유효성 검사

::: moniker range="vs-2017"

템플릿에서 *vstemplate* 파일이 Visual Studio 템플릿 스키마를 따르지 않으면 해당 템플릿은 **새 프로젝트** 대화 상자에 표시되지 않을 수 있습니다.

::: moniker-end

::: moniker range=">=vs-2019"

템플릿의 *vstemplate* 파일이 Visual Studio 템플릿 스키마를 따르지 않으면 새 프로젝트를 만드는 대화 상자에 템플릿이 표시되지 않을 수 있습니다.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>vstemplate 파일의 유효성을 검사하려면

1. 템플릿을 포함하는 *.zip* 파일을 찾습니다.

1. *.zip* 파일의 압축을 풉니다.

1. Visual Studio의 **파일** 메뉴에서 **열기** > **파일**을 선택합니다.

1. 템플릿에 대한 *vstemplate* 파일을 선택하고 **열기**를 선택합니다.

1. *vstemplate* 파일의 XML이 템플릿 스키마를 따르는지 확인합니다. *vstemplate* 스키마에 대한 자세한 내용은 [템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)를 참조하세요.

    > [!NOTE]
    > *vstemplate* 파일을 제작하는 동안 IntelliSense 지원을 가져오려면 `xmlns` 특성을 `VSTemplate` 요소에 추가하고 `http://schemas.microsoft.com/developer/vstemplate/2005`의 값을 할당합니다.

1. *vstemplate* 파일을 저장한 다음, 닫습니다.

1. 템플릿에 포함되어 있는 파일을 선택하고 마우스 오른쪽 단추를 클릭한 다음 **보내기** > **압축(ZIP) 폴더**를 선택합니다. 선택한 파일이 *.zip* 파일로 압축됩니다.

1. 새 *.zip* 파일을 이전 *.zip* 파일과 같은 디렉터리에 배치합니다.

1. 추출된 템플릿 파일과 이전 템플릿 *.zip* 파일을 삭제합니다.

## <a name="enable-diagnostic-logging"></a>진단 로깅 사용

[템플릿 검색 문제 해결(확장성)](../extensibility/troubleshooting-template-discovery.md)의 단계를 수행하여 템플릿 검색에 대한 진단 로그를 사용할 수 있습니다.

## <a name="see-also"></a>참고 항목

- [템플릿 검색 문제 해결(확장성)](../extensibility/troubleshooting-template-discovery.md)
- [템플릿 사용자 지정](../ide/customizing-project-and-item-templates.md)
- [프로젝트 및 항목 템플릿 만들기](../ide/creating-project-and-item-templates.md)
- [템플릿 스키마 참조](../extensibility/visual-studio-template-schema-reference.md)
