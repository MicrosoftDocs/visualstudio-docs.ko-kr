---
title: MSBuild를 사용하여 빌드 로그 가져오기 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, logging
- logging [MSBuild]
ms.assetid: 6ba9a754-9cc0-4fed-9fc8-4dcd3926a031
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f756d432d9ff4d3824c1f1165c63710e4d10c2e9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594892"
---
# <a name="obtain-build-logs-with-msbuild"></a>MSBuild를 사용하여 빌드 로그 가져오기

MSBuild에서 스위치를 사용하면 검토할 빌드 데이터의 양과 하나 이상의 파일에 빌드 데이터를 저장할지를 지정할 수 있습니다. 빌드 데이터를 수집하는 사용자 지정 로거를 지정할 수도 있습니다. 이 항목에서 다루지 않는 MSBuild 명령줄 스위치에 대한 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조하세요.

> [!NOTE]
> Visual Studio IDE를 사용하여 프로젝트를 빌드하는 경우 빌드 로그를 검토하여 해당 빌드의 문제를 해결할 수 있습니다. 자세한 내용은 [방법: 빌드 로그 파일 보기, 저장 및 구성](../ide/how-to-view-save-and-configure-build-log-files.md)을 참조하세요.

## <a name="set-the-level-of-detail"></a>세부 수준 설정

 정보 수준을 지정하지 않고 MSBuild를 사용하여 프로젝트를 빌드할 때는 출력 로그에 다음 정보가 표시됩니다.

- 매우 중요한 항목으로 분류된 오류, 경고 및 메시지

- 일부 상태 이벤트

- 빌드의 요약

**-verbosity**(**v**) 스위치를 사용하면 출력 로그에 표시되는 데이터의 양을 제어할 수 있습니다. 문제 해결에 사용하려는 경우 대부분의 정보를 제공하는 `detailed`(`d`) 또는 `diagnostic`(`diag`)를 세부 정보 표시 수준으로 사용합니다.

**-verbosity**를 `detailed`로 설정하면 빌드 프로세스의 속도가 느려질 수 있으며, **-verbosity**를 `diagnostic`으로 설정하면 속도가 더욱 느려집니다.

```cmd
msbuild MyProject.proj -t:go -v:diag
```

### <a name="verbosity-settings"></a>세부 정보 표시 설정

다음 표에서는 로그의 자세한 정도(열 값)가 기록되는 메시지 유형(행 값)에 미치는 영향을 보여줍니다.

|                                       | Quiet | 최소 | 정상 | Detailed | 진단 |
|---------------------------------------|:-----:|:-------:|:------:|:--------:|:----------:|
| 오류                                |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| 경고                              |   ✅   |    ✅    |    ✅   |     ✅    |      ✅     |
| 중요도 높은 메시지              |       |    ✅    |    ✅   |     ✅    |      ✅     |
| 중요도 보통인 메시지           |       |         |    ✅   |     ✅    |      ✅     |
| 중요도 낮은 메시지              |       |         |        |     ✅    |      ✅     |
| 추가 MSBuild 엔진 정보 |       |         |        |          |      ✅     |

## <a name="save-the-build-log-to-a-file"></a>파일에 빌드 로그 저장

**-fileLogger**(**fl**) 스위치를 사용하여 빌드 데이터를 파일에 저장할 수 있습니다. 다음 예제에서는 이름이 *msbuild.log*인 파일에 빌드 데이터를 저장합니다.

```cmd
msbuild MyProject.proj -t:go -fileLogger
```

 다음 예제에서 로그 파일의 이름은 *MyProjectOutput.log*이고 로그 출력의 자세한 표시 수준은 `diagnostic`으로 설정됩니다. **-filelogparameters**(`flp`) 스위치를 사용하여 이 두 설정을 지정합니다.

```cmd
msbuild MyProject.proj -t:go -fl -flp:logfile=MyProjectOutput.log;verbosity=diagnostic
```

 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조하세요.

## <a name="save-the-log-output-to-multiple-files"></a>여러 파일에 로그 출력 저장

 다음 예제에서는 *msbuild1.log*에 전체 로그를 저장하고 *JustErrors.log*에는 오류만, *JustWarnings.log*에는 경고만 저장합니다. 이 예제에서는 3개 파일에 대해 각각 파일 번호를 사용합니다. 파일 번호는 `-fl1` 및 `-flp1`과 같이 **fl** 및 **-flp** 스위치 바로 뒤에 지정됩니다.

 파일 2 및 3에 대한 **-filelogparameters**(`flp`) 스위치는 각 파일에 지정할 이름 및 포함할 내용을 지정합니다. 파일 1에는 이름이 지정되지 않았으므로 기본 이름인 *msbuild1.log*가 사용됩니다.

```cmd
msbuild MyProject.proj -t:go -fl1 -fl2 -fl3 -flp2:logfile=JustErrors.log;errorsonly -flp3:logfile=JustWarnings.log;warningsonly
```

 자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조하세요.

## <a name="save-a-binary-log"></a>이진 로그 저장

**-binaryLogger**(**bl**) 스위치를 사용하여 압축된 이진 형식으로 로그를 저장할 수 있습니다. 이 로그는 빌드 프로세스에 대한 자세한 설명을 포함하며, 특정 로그 분석 도구으로 읽을 수 있습니다.

다음 예제에서는 이진 로그 파일이 *binarylogfilename* 이름으로 만들어집니다.

```cmd
-bl:binarylogfilename.binlog
```

자세한 내용은 [명령줄 참조](../msbuild/msbuild-command-line-reference.md)를 참조하세요.

## <a name="use-a-custom-logger"></a>사용자 지정 로거 사용

 <xref:Microsoft.Build.Framework.ILogger> 인터페이스를 구현하는 관리되는 형식을 만들어 자체의 로거를 작성할 수 있습니다. 예를 들어 사용자 지정 로거를 사용하여 빌드 오류를 이메일로 보내거나 데이터베이스 또는 XML 파일에 기록할 수 있습니다. 자세한 내용은 [빌드 로거](../msbuild/build-loggers.md)를 참조하세요.

 MSBuild 명령줄에서 **-logger** 스위치를 통해 사용자 지정 로거를 지정합니다. **-noconsolelogger** 스위치를 사용하여 기본 콘솔 로거를 비활성화할 수도 있습니다.

## <a name="see-also"></a>참고 항목

- <xref:Microsoft.Build.Framework.LoggerVerbosity>
- [빌드 로거](../msbuild/build-loggers.md)
- [다중 프로세서 환경에서의 로그인](../msbuild/logging-in-a-multi-processor-environment.md)
- [전달 로거 만들기](../msbuild/creating-forwarding-loggers.md)
- [MSBuild 개념](../msbuild/msbuild-concepts.md)
