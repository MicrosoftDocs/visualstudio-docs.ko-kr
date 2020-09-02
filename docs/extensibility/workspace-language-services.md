---
title: Visual Studio의 작업 영역 및 언어 서비스 | Microsoft Docs
ms.date: 02/21/2018
ms.topic: conceptual
author: vukelich
ms.author: svukel
manager: viveis
ms.workload:
- vssdk
ms.openlocfilehash: 2893ae2bcd70ff317ba799fea6cfd2751c685731
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62952707"
---
# <a name="workspaces-and-language-services"></a>작업 영역 및 언어 서비스

언어 서비스는 솔루션 및 프로젝트를 사용할 때 사용 되는 것과 동일한 풍부한 언어 기능 [을 사용자에 게 제공할](../ide/develop-code-in-visual-studio-without-projects-or-solutions.md) 수 있습니다. 이 "느슨한 파일" 언어 서비스는 구문 강조 표시로 제한 되지만 파일 확장명 또는 열린 문서의 콘텐츠를 기반으로 언어 서비스가 자동으로 활성화 될 수 있습니다. 소스 코드를 편집/검토할 때 보다 풍부한 환경을 제공 하려면 추가 정보가 필요 합니다. 각 언어 서비스에는 문서의 추가 컨텍스트 데이터를 사용 하 여 초기화 하기 위한 자체 API가 있습니다. 이는 일반적으로 언어 서비스 및 빌드 시스템에 긴밀 하 게 결합 된 프로젝트 시스템에서 관리 됩니다.

## <a name="initialization"></a>초기화

[작업 영역](workspaces.md)에서 언어 서비스는 <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 해당 언어 서비스 에서만 전문적으로 사용할 수 있는 확장 지점에 의해 초기화 되며 빌드 제작을 전혀 인식 하지 못합니다. 이러한 방식으로 언어 서비스 소유자는 빌드 중에 컴파일러를 실행 하기 위해 폴더와 파일 내에 있는 패턴의 수에 관계 없이 단일 폴더 확장을 유지할 수 있습니다 (예: MSBuild, 메이크파일 등). 파일 컨텍스트가 만들어진 파일을 디스크에서 변경 하 고 파일 컨텍스트를 새로 고치면 언어 서비스 공급자에 게 업데이트 된 파일 컨텍스트 집합에 대 한 알림이 표시 됩니다. 그러면 언어 서비스 공급자가 해당 모델을 업데이트할 수 있습니다.

편집기에서 문서를 열 때 Visual Studio에서는 일치 하는 파일 컨텍스트 공급자를 찾을 수 있는 파일 컨텍스트 형식이 필요한 언어 서비스 공급자만 고려 합니다. 그런 다음를 통해 일치 하는 공급자의 파일 컨텍스트를 선택한 언어 서비스 공급자로 전달 `ILanguageServiceProvider.InitializeAsync` 합니다. 언어 서비스 공급자가 해당 파일 컨텍스트 데이터를 사용 하 여 수행 하는 작업은 언어 서비스 공급자의 구현 세부 정보 이지만 예상 사용자 환경은 해당 문서에 대 한 보다 다양 한 언어 서비스입니다.

## <a name="using-ilanguageserviceprovider"></a>ILanguageServiceProvider 사용

언어 `ContextType` `SupportedContextTypes` 서버 내보내기 특성의 값 중 하 나와 일치 하는를 사용 하 여 파일 컨텍스트를 만들 때 언어 서비스에 알림이 제공 됩니다.

언어 서비스를 지원 하려면 확장 프로그램이 필요 합니다.

- 고유한 `Guid` 입니다. 이는 `SupportedContextTypes` 특성 인수 및 개체에 사용 됩니다 `FileContext` .
- 언어 파일 컨텍스트
  - 공급자 팩터리
    - `ExportFileContextProviderAttribute` 위에서 고유 하 `Guid` 게 생성 된 특성 `SupportedContextTypes`
    - `IWorkspaceProviderFactory<IFileContextProvider>`을 구현합니다.
  - 의 공급자 구현 `IFileContextProvider.GetContextsForFileAsync`
    - `FileContext` `contextType` 고유 하 게 생성 된 생성자 인수를 사용 하 여 새를 생성 합니다.`Guid`
    - 의 속성을 사용 하 여에 `Context` `FileContext` 추가 데이터를 제공 합니다. `ILanguageServiceProvider`
- 언어 서비스
  - 공급자 팩터리
    - `ExportLanguageServiceProvider` 위에서 고유 하 `Guid` 게 생성 된 특성 `SupportedContextTypes`
    - `IWorkspaceProviderFactory<ILanguageServiceProvider>`을 구현합니다.
  - 공급자
    - `ILanguageServiceProvider`을 구현합니다.
    - `ILanguageServiceProvider.InitializeAsync`파일이 열릴 때 제공 된 인수에 대해 언어 서비스를 사용 하도록 설정 하려면를 사용 합니다.
    - `ILanguageServiceProvider.UninitializeAsync`파일이 닫힐 때 제공 된 인수에 대해 언어 서비스를 사용 하지 않도록 설정 하려면를 사용 합니다.

>[!WARNING]
>`ILanguageServiceProvider`메서드는 주 스레드의 작업 영역에 의해 호출 될 수 있습니다. UI 지연이 발생 하지 않도록 하려면 다른 스레드에서 작업을 예약 하는 것이 좋습니다.

## <a name="language-server-protocol"></a>언어 서버 프로토콜

`Microsoft.VisualStudio.Workspace.*`Api는 열린 폴더에서 언어 서비스를 사용 하도록 설정 하는 유일한 방법은 아닙니다. 또 다른 옵션은 언어 서버를 사용 하는 것입니다. 자세한 내용은 [언어 서버 프로토콜](language-server-protocol.md)을 참조 하세요.

## <a name="related-interfaces"></a>관련 인터페이스

- <xref:Microsoft.VisualStudio.Workspace.Intellisense.ILanguageServiceProvider> 편집을 위해 일치 하는 파일 형식의 파일을 열거나 닫을 때 호출 됩니다.

## <a name="next-steps"></a>다음 단계

* [작업 영역 빌드](workspace-build.md) -열기 폴더는 MSBuild 및 메이크파일과 같은 빌드 시스템을 지원 합니다.