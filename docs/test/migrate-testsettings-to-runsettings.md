---
title: runsettings로 testsettings 마이그레이션
description: testsettings를 runsettings로 마이그레이션하는 방법을 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 03/18/2021
ms.topic: conceptual
f1_keywords:
- vs.UnitTest.Migrate
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab1cfe921777fa75d4f69251668934e8d78d9bec
ms.sourcegitcommit: 155d5f0fd54ac1d20df2f5b0245365924faa3565
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/31/2021
ms.locfileid: "106087199"
---
# <a name="upgrade-from--testsettings-to-runsettings"></a>*.testsettings* 에서 *.runsettings* 로 업그레이드

Visual Studio와 함께 설치되는 SettingsMigrator 도구를 사용하여 테스트 구성 파일을 *.testsettings* 에서 *.runsettings* 로 업그레이드할 수 있습니다. Visual Studio 설치 위치에 따라 다음 경로에서 SettingsMigrator 도구를 찾을 수 있습니다. `C:\Program Files (x86)\Microsoft Visual Studio\2019\Enterprise\Common7\IDE\Extensions\TestPlatform\SettingsMigrator.exe`

올바른 디렉터리 위치에서 아래 형식으로 도구를 실행할 수 있습니다.

```console
SettingsMigrator.exe <Full path to testsettings file to be migrated>
SettingsMigrator.exe <Full path to testsettings file to be migrated> <Full path to runsettings file to be created>
```

## <a name="examples"></a>예제
```console
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings
SettingsMigrator.exe E:\MyTest\MyTestSettings.testsettings E:\MyTest\MyNewRunSettings.runsettings
```

*.testsettings* 옵션을 *.runsettings* 로 변환하는 방법에 대한 자세한 내용을 알아보려면 GitHub의 [오픈 소스 테스트 플랫폼 리포지토리](https://github.com/microsoft/vstest-docs/blob/master/RFCs/0023-TestSettings-Deprecation.md#migration)에서 더 많은 구현 세부 정보를 확인할 수 있습니다.

## <a name="see-also"></a>참조

- [`.runsettings`를 사용하여 테스트 실행 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)
- [MSTestV1에서 MSTestV2로 업그레이드](../test/mstest-update-to-mstestv2.md)
- [코드 단위 테스트](../test/unit-test-your-code.md)
- [테스트 탐색기를 사용하여 단위 테스트 디버그](../test/debug-unit-tests-with-test-explorer.md)
