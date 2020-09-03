---
title: 소스 제어 플러그 인을 구현 하기 위한 모범 사례 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 99166c8bf9a76deaa3805bfd8f5ac6db35e5c0a0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184722"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>소스 제어 플러그 인 구현 모범 사례
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

다음 기술 세부 정보는에서 소스 제어 플러그 인을 안정적으로 구현 하는 데 도움이 될 수 있습니다 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .  
  
## <a name="memory-management-issues"></a>메모리 관리 문제  
 대부분의 경우 호출자 인 IDE (통합 개발 환경)는 메모리를 해제 하 고 할당 합니다. 소스 제어 플러그 인은 호출자가 할당 한 버퍼에서 문자열과 기타 항목을 반환 합니다. 예외는 발생 하는 특정 함수에 대 한 설명에 나와 있습니다.  
  
## <a name="arrays-of-file-names"></a>파일 이름 배열  
 파일의 배열이 전달 되 면 파일 이름의 연속 배열로 전달 되지 않습니다. 파일 이름에 대 한 포인터의 배열로 전달 됩니다. 예를 들어 [Sccget](../extensibility/sccget-function.md)에서 파일 이름은 `lpFileNames` 매개 변수로 전달 됩니다 `lpFileNames` . 여기서는 실제로에 대 한 포인터입니다 `char **` . `lpFileNames`[0]은 이름에 대 한 포인터입니다 `lpFileNames` . [1]은 (는) 두 번째 이름에 대 한 포인터입니다.  
  
## <a name="large-model"></a>모델 크게  
 모든 포인터는 16 비트 운영 체제 에서도 32 비트입니다.  
  
## <a name="fully-qualified-paths"></a>정규화 된 경로  
 파일 이름 또는 디렉터리가 인수로 지정 된 경우에는 백슬래시를 끝내 지 않고 정규화 된 경로 또는 UNC 경로 여야 합니다. 원본 제어 플러그 인은 기본 소스 제어 시스템의 요구 사항인 경우이를 상대 경로로 변환 합니다.  
  
## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>등록 된 DLL의 정규화 된 경로를 지정 합니다.  
 IDE는 더 이상 상대 경로에서 Dll을 로드 하지 않습니다 (예: .\NewProvider.dll). DLL의 전체 경로를 지정 해야 합니다 (예: C:\Providers\NewProvider.dll). 이 요구 사항은 권한이 없거나 가장 된 소스 제어 Dll의 로드를 방지 하 여 IDE의 보안을 강화 합니다.  
  
## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>원본 제어 플러그 인을 설치할 때 기존 VSSCI 플러그 인을 확인 합니다.  
 원본 제어 플러그 인을 설치할 계획인 사용자에 게 컴퓨터에 기존 원본 제어 플러그 인이 이미 설치 되어 있을 수 있습니다. 만든 플러그 인의 설치 (설치) 프로그램은 관련 레지스트리 키에 대 한 기존 값이 있는지 여부를 확인 해야 합니다. 이러한 키가 이미 설정 되어 있는 경우 설치 프로그램에서 사용자에 게 플러그 인을 기본 소스 제어 플러그 인으로 등록 하 고 이미 설치 된 플러그 인을 바꿀지 여부를 묻는 메시지를 표시 합니다.  
  
## <a name="error-result-codes-and-reporting"></a>오류 결과 코드 및 보고  
 `SCC_OK`소스 제어 함수의 반환 코드는 모든 파일에 대 한 작업이 성공 했음을 나타냅니다. 작업이 실패 하는 경우 마지막으로 발생 한 오류 코드를 반환 해야 합니다.  
  
 보고에 대 한 규칙은 IDE에서 오류가 발생 하는 경우 IDE에서이를 보고 해야 한다는 것입니다. 소스 제어 시스템에서 오류가 발생 하는 경우 소스 제어 플러그 인에서 보고를 담당 합니다. 예를 들어 "현재 선택 된 파일이 없습니다."는 IDE에서 보고 되는 반면, "이 파일은 이미 체크 아웃 되었습니다."는 플러그 인에서 보고 됩니다.  
  
## <a name="the-context-structure"></a>컨텍스트 구조  
 [Sccinitialize](../extensibility/sccinitialize-function.md)를 호출 하는 동안 호출자는 `ppvContext` void에 대해 초기화 되지 않은 핸들 인 매개 변수를 전달 합니다. 소스 제어 플러그 인은이 매개 변수를 무시 하거나 모든 종류의 구조체를 할당 하 고 해당 구조체에 대 한 포인터를 전달 된 포인터에 넣을 수 있습니다. IDE는이 구조체를 이해 하지 않지만이 구조체에 대 한 포인터를 플러그 인의 다른 모든 호출에 전달 합니다. 이는 전역 변수를 사용 하지 않고 함수 호출에서 지속 되는 전역 상태 정보를 유지 관리 하는 데 사용할 수 있는 플러그 인에 중요 한 컨텍스트 캐시 정보를 제공 합니다. 플러그 인은 [SccUninitialize](../extensibility/sccuninitialize-function.md)에 대 한 호출에서 구조를 해제 해야 합니다.  
  
 플러그 인이 `SCC_CAP_REENTRANT` [Sccinitialize](../extensibility/sccinitialize-function.md) (특히 매개 변수)에서 비트를 설정 하는 경우에는 `lpSccCaps` 열려 있는 모든 프로젝트를 추적 하기 위해 여러 컨텍스트 구조가 사용 됩니다.  
  
## <a name="bitflags-and-other-command-options"></a>Bitflags 및 기타 명령 옵션  
 IDE는 [Sccget](../extensibility/sccget-function.md)과 같은 각 명령에 대해 명령의 동작을 변경 하는 여러 옵션을 지정할 수 있습니다.  
  
 API는 매개 변수를 통해 IDE의 특정 옵션 설정을 지원 합니다 `fOptions` . 이러한 옵션은 영향을 주는 명령과 함께 [특정 명령에 사용 되는 Bitflags](../extensibility/bitflags-used-by-specific-commands.md) 에 설명 되어 있습니다. 일반적으로 사용자에 게 메시지가 표시 되지 않는 옵션입니다.  
  
 사용자가 구성할 수 있는 대부분의 설정 옵션은 원본 제어 플러그 인 간에 크게 다르므로 이러한 방식으로 정의 되지 않습니다. 따라서 권장 메커니즘은 **고급** 단추입니다. 예를 들어 **가져오기** 대화 상자에서 IDE는 이해 하는 정보만 표시 하지만 플러그 인에이 명령에 대 한 옵션이 있는 경우에도 **고급** 단추를 표시 합니다. 사용자가 **고급** 단추를 클릭 하면 IDE에서 [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) 를 호출 하 여 사용자에 게 bitflag 또는 date/time과 같은 정보를 묻는 메시지를 표시 하는 소스 제어 플러그 인을 사용 하도록 설정 합니다. 플러그 인은 명령 중에 다시 전달 되는 구조에이 정보를 반환 합니다 `SccGet` .  
  
## <a name="see-also"></a>관련 항목  
 [소스 제어 플러그 인](../extensibility/source-control-plug-ins.md)   
 [소스 제어 플러그 인 만들기](../extensibility/internals/creating-a-source-control-plug-in.md)
