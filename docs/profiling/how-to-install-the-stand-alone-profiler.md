---
title: '방법: 독립 실행형 프로파일러 설치 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- performance tools, installing stand-alone profiler
- profiling tools, stand-alone profiler
ms.assetid: cae81c95-83cd-4ab6-8a98-84ef977a2f6d
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: vs-2017
ms.workload:
- multiple
ms.openlocfilehash: ec0f211db3d9906d83d9bcf7c7a0ab79ec3e1b7f
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/22/2020
ms.locfileid: "77557836"
---
# <a name="how-to-install-the-stand-alone-profiler"></a>방법: 독립 실행형 프로파일러 설치
[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]은(는) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] IDE를 설치하지 않고 실행할 수 있는 명령줄 기반 독립 실행형 프로파일러를 제공합니다. 이 경우는 컴퓨터에 설치된 개발 환경이 없거나 설치할 수 없는 경우에 발생합니다. 예를 들어 프로덕션 웹 서버에 개발 환경을 설치하면 안 됩니다.

> [!NOTE]
> 독립 실행형 프로파일러를 사용하여 ASP.NET 웹 사이트에 대한 성능 데이터를 수집하는 경우 [VSPerfCmd](../profiling/vsperfcmd.md) 도구보다 [VSPerfASPNetCmd](../profiling/vsperfaspnetcmd.md) 선 도구를 권장합니다.

### <a name="to-install-the-stand-alone-profiler"></a>독립 실행형 프로파일러를 설치하려면

1. [Visual Studio용 성능 도구](https://visualstudio.microsoft.com/downloads/?q=performance+tools#performance-tools-for-visual-studio)를 다운로드합니다.

1. 성능 도구를 다운로드하고 실행한 독립 실행형 프로필 설치 관리자(*vs_standaloneprofiler.exe*)를 찾습니다.

2. *vsinstr.exe*의 경로를 시스템 경로에 추가합니다.

   > [!NOTE]
   > 프로파일링 도구에 대한 경로를 가져오려면 [명령줄 도구의 경로 지정](../profiling/specifying-the-path-to-profiling-tools-command-line-tools.md)을 참조하세요. 64비트 컴퓨터에서는 도구의 64비트 및 32비트 버전을 둘 다 사용할 수 있습니다. 프로파일러 명령줄 도구를 사용하려면 도구 경로를 명령 프롬프트 창의 PATH 환경 변수에 추가하거나 명령 자체에 추가해야 합니다.

3. 명령 프롬프트에서 **VSInstr**을 입력합니다.

   > [!NOTE]
   > vsinstr.exe에 대한 사용 정보가 표시되면 모든 것이 올바르게 설정된 것입니다. vsinstr.exe를 나타내는 오류가 표시되거나 해당 종속성 중 하나가 없는 경우 2단계에 설명된 대로 경로를 정확하게 설정했는지 확인합니다.

4. **_NT_SYMBOL_PATH** variable to **symsrv\*symsrv.dll\*c:\localcache\*https://msdl.microsoft.com/download/symbols** 를 설정하여 기호 서버를 설정합니다.

5. 시스템 환경 변수를 사용하여 기호 서버를 설정한 후 새 명령 프롬프트에서 명령줄 프로파일러 도구를 실행합니다. 그러면 새 환경 변수가 적용됩니다. 명령 프롬프트 창에서 다음 명령을 입력합니다.

    **start %COMSPEC%**

   > [!NOTE]
   > 기호 서버 패키지를 설정하는 방법에 대한 자세한 지침은 [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)를 참조하세요.

6. [VSPerfReport](../profiling/vsperfreport.md) 도구를 사용하여 기호를 프로파일링 데이터(.vsp) 파일로 직렬화합니다. **VSPerfReport /summary:all /packsymbols** 스위치를 사용합니다. 데이터 파일에 삽입된 기호가 없는 경우 _NT_SYMBOL_PATH 환경 변수를 설정했는지 확인합니다.

## <a name="see-also"></a>참조
- [명령줄에서 프로파일링](../profiling/using-the-profiling-tools-from-the-command-line.md)
- [연습: 계측을 사용하여 명령줄 프로파일링](command-line-profiling-of-stand-alone-applications.md)
- [방법: Windows 기호 정보 참조](../profiling/how-to-reference-windows-symbol-information.md)
- [VSPerfReport](../profiling/vsperfreport.md)
