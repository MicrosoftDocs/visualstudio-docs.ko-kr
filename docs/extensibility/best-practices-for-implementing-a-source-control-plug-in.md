---
title: 소스 제어 플러그인 구현을 위한 모범 사례 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740046"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>소스 제어 플러그인 구현을 위한 모범 사례
다음 기술 세부 정보를 통해 소스 제어 플러그인을 안정적으로 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]구현할 수 있습니다.

## <a name="memory-management-issues"></a>메모리 관리 문제
 대부분의 경우 호출자인 통합 개발 환경(IDE)은 메모리를 해제하고 할당합니다. 소스 제어 플러그인은 호출자 할당 버퍼의 문자열 및 기타 항목을 반환합니다. 예외는 특정 함수가 발생하는 위치에 대한 설명에 기록됩니다.

## <a name="arrays-of-file-names"></a>파일 이름 배열
 파일 배열이 전달되면 파일 이름의 연속 배열로 전달되지 않습니다. 파일 이름에 대한 포인터 배열로 전달됩니다. 예를 들어 [SccGet에서](../extensibility/sccget-function.md)파일 이름은 매개 변수에 `lpFileNames` 의해 `lpFileNames` 전달되며 실제로 `char **`는 에 대한 포인터입니다. `lpFileNames`[0]은 이름에 대한 포인터이고[1]은 `lpFileNames`두 번째 이름에 대한 포인터입니다.

## <a name="large-model"></a>대형 모델
 모든 포인터는 16비트 운영 체제에서도 32비트입니다.

## <a name="fully-qualified-paths"></a>정규화된 경로
 파일 이름이나 디렉터리가 인수로 지정된 경우 끝 백슬래시 없이 완전히 정규화된 경로 또는 UNC 경로여야 합니다. 기본 소스 제어 시스템의 요구 사항인 경우 소스 제어 플러그인을 상대 경로로 변환하는 것은 소스 제어 플러그인의 책임입니다.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>등록된 DLL에 대해 정규화된 경로 지정
 IDE는 더 이상 상대 경로(예: *.\NewProvider.dll)에서*DLL을 로드하지 않습니다. DLL의 전체 경로를 지정해야 합니다(예: *C:\Providers\NewProvider.dll).* 이 요구 사항은 승인되지 않았거나 가장된 소스 제어 DLL의 로드를 방지하여 IDE의 보안을 강화합니다.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>소스 제어 플러그인을 설치할 때 기존 VSSCI 플러그인이 있는지 확인합니다.
 소스 제어 플러그인을 설치하려는 사용자는 이미 컴퓨터에 기존 소스 제어 플러그인이 설치되어 있을 수 있습니다. 만드는 플러그인에 대한 설치(설치) 프로그램은 관련 레지스트리 키에 대한 기존 값이 있는지 여부를 결정해야 합니다. 이러한 키가 이미 설정되어 있는 경우 설치 프로그램에서 사용자에게 플러그인을 기본 소스 제어 플러그인으로 등록하고 이미 설치된 키를 교체할지 여부를 물어봐야 합니다.

## <a name="error-result-codes-and-reporting"></a>오류 결과 코드 및 보고
 소스 `SCC_OK` 제어 함수에 대한 반환 코드는 모든 파일에 대해 작업이 성공했음을 나타냅니다. 작업이 실패하면 마지막으로 발생한 오류 코드를 반환해야 합니다.

 보고 규칙은 IDE에서 오류가 발생하면 IDE가 보고할 책임이 있다는 것입니다. 소스 제어 시스템에서 오류가 발생하면 소스 제어 플러그인이 보고해야 합니다. 예를 들어 **현재 선택된 파일은** IDE에 의해 보고되지만 **이 파일은 이미 체크 아웃된 파일은** 플러그인에 의해 보고됩니다.

## <a name="the-context-structure"></a>컨텍스트 구조
 [SccInitialize를](../extensibility/sccinitialize-function.md)호출하는 동안 호출자는 `ppvContext` 초기화되지 않은 핸들인 매개 변수를 void에 전달합니다. 소스 제어 플러그인은 이 매개 변수를 무시하거나 모든 종류의 구조를 할당하고 해당 구조에 대한 포인터를 전달된 포인터에 넣을 수 있습니다. IDE는 이 구조를 이해하지 못하지만 이 구조에 대한 포인터를 플러그인의 다른 모든 호출에 전달합니다. 이렇게 하면 전역 변수를 사용하지 않고 함수 호출 간에 지속되는 전역 상태 정보를 유지하는 데 사용할 수 있는 플러그인에 유용한 컨텍스트 캐시 정보를 제공합니다. 플러그인은 [SccUninitialize에](../extensibility/sccuninitialize-function.md)대한 호출시 구조를 해제하는 책임을 집니다.

 플러그인이 `SCC_CAP_REENTRANT` [SccInitialize(특히](../extensibility/sccinitialize-function.md) `lpSccCaps` 매개 변수)에서 비트를 설정하는 경우 열려 있는 모든 프로젝트를 추적하는 데 여러 컨텍스트 구조가 사용됩니다.

## <a name="bitflags-and-other-command-options"></a>비트 플래그 및 기타 명령 옵션
 [SccGet과](../extensibility/sccget-function.md)같은 각 명령에 대해 IDE는 명령의 동작을 변경하는 많은 옵션을 지정할 수 있습니다.

 API는 매개 변수를 통해 IDE에 `fOptions` 의해 특정 옵션의 설정을 지원합니다. 이러한 옵션은 영향을 주는 명령과 함께 [특정 명령에서 사용되는 BitFlags에](../extensibility/bitflags-used-by-specific-commands.md) 설명되어 있습니다. 일반적으로 이러한 옵션은 사용자에게 프롬프트가 표시되지 않는 옵션입니다.

 대부분의 사용자 구성 가능한 설정 옵션은 소스 제어 플러그인마다 매우 다양하기 때문에 이러한 방식으로 정의되지 않습니다. 따라서 권장되는 메커니즘은 **고급** 단추입니다. 예를 들어 대화 **상자에서** IDE는 이해한 정보만 표시하지만 플러그인에 이 명령에 대한 옵션이 있는 경우 **고급** 단추도 표시됩니다. 사용자가 **고급** 단추를 클릭하면 IDE는 [SccGetCommandOptions를](../extensibility/sccgetcommandoptions-function.md) 호출하여 소스 제어 플러그인을 활성화하여 비트 플래그 또는 날짜/시간과 같은 정보를 사용자에게 요청합니다. 플러그인은 명령 중에 다시 전달되는 구조에서 이 `SccGet` 정보를 반환합니다.

## <a name="see-also"></a>참조
- [소스 제어 플러그인](../extensibility/source-control-plug-ins.md)
- [소스 제어 플러그인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md)
