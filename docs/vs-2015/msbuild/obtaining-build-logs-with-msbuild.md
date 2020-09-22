---
title: MSBuild를 사용하여 빌드 로그 가져오기 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
caps.latest.revision: 30
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c88288a7bed453ca14e9c14fd43706b97be04044
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841510"
---
# <a name="obtaining-build-logs-with-msbuild"></a>MSBuild를 사용하여 빌드 로그 가져오기
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

MSBuild에서 스위치를 사용하면 검토할 빌드 데이터의 양과 하나 이상의 파일에 빌드 데이터를 저장할지를 지정할 수 있습니다. 빌드 데이터를 수집하는 사용자 지정 로거를 지정할 수도 있습니다. 이 항목이 다루지 않는 MSBuild 명령줄 스위치에 대 한 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조 하세요.  
  
> [!NOTE]
> Visual Studio IDE를 사용하여 프로젝트를 빌드하는 경우 빌드 로그를 검토하여 해당 빌드의 문제를 해결할 수 있습니다. 자세한 내용은 [방법: 빌드 로그 파일 보기, 저장 및 구성](../ide/how-to-view-save-and-configure-build-log-files.md)을 참조하세요.  
  
## <a name="setting-the-level-of-detail"></a>세부 수준 설정  
 정보 수준을 지정하지 않고 MSBuild를 사용하여 프로젝트를 빌드할 때는 출력 로그에 다음 정보가 표시됩니다.  
  
- 매우 중요한 항목으로 분류된 오류, 경고 및 메시지  
  
- 일부 상태 이벤트  
  
- 빌드의 요약  
  
  **/Verbosity** (**/v**) 스위치를 사용 하 여 출력 로그에 표시 되는 데이터의 양을 제어할 수 있습니다. 문제 해결에 사용하려는 경우 대부분의 정보를 제공하는 `detailed`(`d`) 또는 `diagnostic`(`diag`)를 세부 정보 표시 수준으로 사용합니다.  
  
  **/Verbosity** 을로 설정 하 `detailed` 고 **/verbosity** 를로 설정 하면 빌드 프로세스의 속도가 느려질 수 있습니다 `diagnostic` .  
  
```  
msbuild MyProject.proj /t:go /v:diag  
```  
  
## <a name="saving-the-build-log-to-a-file"></a>파일에 빌드 로그 저장  
 **/Filelogger** (**fl**) 스위치를 사용 하 여 빌드 데이터를 파일에 저장할 수 있습니다. 다음 예제에서는 이름이 `msbuild.log`인 파일에 빌드 데이터를 저장합니다.  
  
```  
msbuild MyProject.proj /t:go /fileLogger  
```  
  
 다음 예제에서 로그 파일의 이름은 `MyProjectOutput.log`이고 로그 출력의 자세한 표시 수준은 `diagnostic`으로 설정됩니다. **/Filelogparameters** () 스위치를 사용 하 여 이러한 두 설정을 지정 `flp` 합니다.  
  
```  
msbuild MyProject.proj /t:go /fl /flp:logfile=MyProjectOutput.log;verbosity=diagnostic  
```  
  
 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조 하세요.  
  
## <a name="saving-the-log-output-to-multiple-files"></a>여러 파일에 로그 출력 저장  
 다음 예제에서는 `msbuild1.log`에 전체 로그를 저장하고 `JustErrors.log`에는 오류만, `JustWarnings.log`에는 경고만 저장합니다. 이 예제에서는 3개 파일에 대해 각각 파일 번호를 사용합니다. 파일 번호는 **/sourceand** **/flp** 스위치 바로 뒤에 지정 됩니다 (예: `/fl1` 및 `/flp1` ).  
  
 파일 2와 3에 대 한 **/filelogparameters** ( `flp` ) 스위치는 각 파일의 이름을 지정할 대상과 각 파일에 포함할 항목을 지정 합니다. 파일 1에는 이름이 지정되지 않았으므로 기본 이름인 `msbuild1.log`가 사용됩니다.  
  
```  
msbuild MyProject.proj /t:go /fl1 /fl2 /fl3 /flp2:logfile=JustErrors.log;errorsonly /flp3:logfile=JustWarnings.log;warningsonly  
  
```  
  
 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조 하세요.  
  
## <a name="using-a-custom-logger"></a>사용자 지정 로거 사용  
 <xref:Microsoft.Build.Framework.ILogger> 인터페이스를 구현하는 관리되는 형식을 만들어 자체의 로거를 작성할 수 있습니다. 예를 들어 사용자 지정 로거를 사용하여 빌드 오류를 이메일로 보내거나 데이터베이스 또는 XML 파일에 기록할 수 있습니다. 자세한 내용은 [빌드로 거](../msbuild/build-loggers.md)를 참조 하세요.  
  
 MSBuild 명령줄에서 **/logger** 스위치를 사용 하 여 사용자 지정로 거를 지정 합니다. **/Noconsolelogger** 스위치를 사용 하 여 기본 콘솔로 거를 사용 하지 않도록 설정할 수도 있습니다.  
  
## <a name="see-also"></a>참고 항목  
 <xref:Microsoft.Build.Framework.LoggerVerbosity>   
 [빌드로 거](../msbuild/build-loggers.md)   
 [다중 프로세서 환경에서의 로깅](../msbuild/logging-in-a-multi-processor-environment.md)   
 [전달로 거 만들기](../msbuild/creating-forwarding-loggers.md)   
 [MSBuild 개념](../msbuild/msbuild-concepts.md)
