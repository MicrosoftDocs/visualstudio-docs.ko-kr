---
title: VSTest.Console.exe 명령줄 옵션
description: 테스트를 실행하는 VSTest.Console.exe 명령줄 도구를 알아봅니다. 이 문서에는 일반 명령줄 옵션이 포함되어 있습니다.
ms.custom: SEO-VS-2020
ms.date: 07/17/2020
ms.topic: reference
helpviewer_keywords:
- vstest.console.exe
- command-line tests
ms.author: mikejo
author: mikejo5000
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 98d58b745b35870d287b6e81aa0a14fcdaeac921
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95598525"
---
# <a name="vstestconsoleexe-command-line-options"></a>VSTest.Console.exe 명령줄 옵션

*VSTest.Console.exe* 는 테스트를 실행하기 위한 명령줄 도구입니다. 명령줄에서 순서에 상관없이 여러 옵션을 지정할 수 있습니다. 이러한 옵션은 [일반 명령줄 옵션](#general-command-line-options)에 나와 있습니다.

> [!NOTE]
> Visual Studio의 MSTest 어댑터는 호환성 지원을 위해 레거시 모드(*mstest.exe* 를 포함하는 실행 테스트에 해당)로도 작동합니다. 레거시 모드에서는 TestCaseFilter 기능을 활용할 수 없습니다. *testsettings* 파일이 지정되거나, **forcelegacymode** 가 *runsettings* 파일에서 **true** 로 설정되거나, **HostType** 같은 특성을 사용하는 경우 어댑터를 레거시 모드로 전환할 수 있습니다.
>
> ARM 아키텍처 기반 머신에서 자동화된 테스트를 실행하려면 *VSTest.Console.exe* 를 사용해야 합니다.

[개발자 명령 프롬프트](/dotnet/framework/tools/developer-command-prompt-for-vs)를 열어 명령줄 도구를 사용하거나 *%Program Files(x86)%\Microsoft Visual Studio\\<version\>\\<edition\>\common7\ide\CommonExtensions\\<Platform | Microsoft>* 에서 도구를 찾을 수 있습니다.

## <a name="general-command-line-options"></a>일반 명령줄 옵션

다음 표에는 *VSTest.Console.exe* 와 관련된 모든 옵션과 이러한 옵션에 대한 간단한 설명이 나와 있습니다. 명령줄에서 `VSTest.Console/?`를 입력하면 비슷한 요약을 볼 수 있습니다.

| 옵션 | 설명 |
|---|---|
|**[*테스트 파일 이름*]**|지정한 파일에서 테스트를 실행합니다. 여러 테스트 파일 이름을 공백으로 구분합니다.<br />예제: `mytestproject.dll`, `mytestproject.dll myothertestproject.exe`|
|**/Settings:[*파일 이름*]**|데이터 수집기 등의 추가 설정을 사용하여 테스트를 실행합니다. 자세한 내용은 [.runsettings 파일을 사용하여 단위 테스트 구성](../test/configure-unit-tests-by-using-a-dot-runsettings-file.md)을 참조하세요.<br />예: `/Settings:local.runsettings`|
|**/Tests:[*테스트 이름*]**|제공된 값을 포함하는 이름의 테스트를 실행합니다. 다중 값을 제공하려면 각각의 값을 쉼표로 구분합니다.<br />예: `/Tests:TestMethod1,testMethod2`<br />**/Tests** 명령줄 옵션은 **/TestCaseFilter** 명령줄 옵션과 함께 사용할 수 없습니다.|
|**/Parallel**|테스트를 병렬로 실행하도록 지정합니다. 기본적으로 머신의 사용 가능한 모든 코어를 사용할 수 있습니다. 설정 파일에서 사용할 코어 수를 구성할 수 있습니다.|
|**/Enablecodecoverage**|테스트 실행에서 데이터 진단 어댑터 CodeCoverage를 활성화합니다.<br />설정 파일을 사용하여 지정하지 않은 경우 기본 설정이 사용됩니다.|
|**/InIsolation**|격리 모드에서 테스트를 실행합니다.<br />이 격리로 인해 *vstest.console.exe* 프로세스가 테스트 시 오류에서 중지될 가능성은 매우 적지만 테스트 속도가 느려질 수 있습니다.|
|**/UseVsixExtensions**|이 옵션은 *vstest.console.exe* 프로세스에서 테스트 실행에 설치된 VSIX 확장명(있는 경우)을 사용하거나 건너뜁니다.<br />이 옵션은 사용되지 않습니다. Visual Studio의 다음 주요 릴리스부터 시작되는 이 옵션은 제거할 수 있습니다. NuGet 패키지로 사용할 수 있게 된 사용 중인 확장으로 이동합니다.<br />예: `/UseVsixExtensions:true`|
|**/TestAdapterPath:[*경로*]**|*vstest.console.exe* 프로세스가 테스트 실행의 지정된 경로(있는 경우)에서 사용자 지정 테스트 어댑터를 사용하도록 적용합니다.<br />예: `/TestAdapterPath:[pathToCustomAdapters]`|
|**/Platform:[*플랫폼 형식*]**|테스트를 실행하는 데 사용할 대상 플랫폼 아키텍처입니다.<br />올바른 값은 x86, x64 및 ARM입니다.|
|**/Framework: [*프레임워크 버전*]**|테스트 실행에 사용될 .NET 버전을 대상 지정합니다.<br />예제 값은 `Framework35`, `Framework40`, `Framework45`, `FrameworkUap10`, `.NETCoreApp,Version=v1.1`입니다.<br />TargetFrameworkAttribute는 어셈블리에서 이 옵션을 자동으로 검색하는 데 사용되며, 이 특성이 없는 경우에는 기본적으로 `Framework40`이 사용됩니다. [TargetFrameworkAttribute](/dotnet/api/system.runtime.versioning.targetframeworkattribute)를 .NET Core 어셈블리에서 제거하는 경우 이 옵션을 명시적으로 지정해야 합니다.<br />대상 프레임워크가 **Framework35** 로 지정된 경우 테스트가 CLR 4.0 “호환성 모드”에서 실행됩니다.<br />예: `/Framework:framework40`|
|**/TestCaseFilter:[*식*]**|지정된 식과 일치하는 테스트를 실행합니다.<br /><Expression\>은 <property\>=<value\>[\|<Expression\>] 형식입니다.<br />예: `/TestCaseFilter:"Priority=1"`<br />예: `/TestCaseFilter:"TestCategory=Nightly|FullyQualifiedName=Namespace.ClassName.MethodName"`<br />**/TestCaseFilter** 명령줄 옵션은 **/Tests** 명령줄 옵션과 함께 사용할 수 없습니다. <br />식 만들기 및 사용에 대한 정보는 [TestCase 필터](https://github.com/Microsoft/vstest-docs/blob/master/docs/filter.md)를 참조하세요.|
|**/?**|사용 정보를 표시합니다.|
|**/Logger:[*uri/friendlyname*]**|테스트 결과에 대해 로거를 지정합니다. 매개 변수를 여러 번 지정하여 여러 로거를 활성화합니다.<br />예: Visual Studio 테스트 결과 파일(TRX)에 결과를 기록하려면 다음을 사용합니다.<br />**/Logger:trx**<br />**[;LogFileName=\<Defaults to unique file name>]**|
|**/ListTests:[*파일 이름*]**|지정된 테스트 컨테이너에서 검색된 테스트를 나열합니다.|
|**/ListDiscoverers**|설치된 테스트 Discoverer를 나열합니다.|
|**/ListExecutors**|설치된 테스트 Executor를 나열합니다.|
|**/ListLoggers**|설치된 테스트 로거를 나열합니다.|
|**/ListSettingsProviders**|설치된 테스트 설정 공급자를 나열합니다.|
|**/Blame**|테스트를 원인 모드로 실행합니다. 이 옵션은 테스트 호스트의 크래시를 유발하는 문제가 있는 테스트를 격리하는 데 유용합니다. 크래시가 감지되면 크래시 전에 실행된 테스트의 순서를 캡처하는 시퀀스 파일이 `TestResults/<Guid>/<Guid>_Sequence.xml`에 만들어집니다. 자세한 내용은 [원인 데이터 수집기](https://github.com/Microsoft/vstest-docs/blob/master/docs/extensions/blame-datacollector.md)를 참조하세요.|
|**/Diag:[*파일 이름*]**|지정된 파일에 진단 추적 로그를 기록합니다.|
|**/ResultsDirectory:[*path*]**|테스트 결과 디렉터리가 존재하지 않는 경우 지정된 경로에 생성됩니다.<br />예: `/ResultsDirectory:<pathToResultsDirectory>`|
|**/ParentProcessId:[*parentProcessId*]**|현재 프로세스를 시작하는 일을 담당하는 부모 프로세스의 프로세스 ID입니다.|
|**/Port:[*port*]**|소켓 연결 및 이벤트 메시지를 받기 위한 포트입니다.|
|**/Collect:[*dataCollector friendlyName*]**|테스트 실행에 대한 데이터 수집기를 사용하도록 설정합니다. [추가 정보](https://github.com/Microsoft/vstest-docs/blob/master/docs/analyze.md).|

> [!TIP]
> 옵션 및 값은 대/소문자를 구분하지 않습니다.

## <a name="examples"></a>예

*vstest.console.exe* 실행 구문은 다음과 같습니다.

`vstest.console.exe [TestFileNames] [Options]`

다음 명령은 테스트 라이브러리 *myTestProject.dll* 에 대해 *vstest.console.exe* 를 실행합니다.

```cmd
vstest.console.exe myTestProject.dll
```

다음 명령은 여러 테스트 파일을 통해 *vstest.console.exe* 를 실행합니다. 테스트 파일 이름을 공백으로 구분합니다.

```cmd
vstest.console.exe myTestFile.dll myOtherTestFile.dll
```

다음 명령은 여러 옵션을 통해 *vstest.console.exe* 를 실행합니다. 이 경우 격리된 프로세스의 *myTestFile.dll* 파일에서 테스트를 실행하고, *Local.RunSettings* 파일에서 지정된 설정을 사용합니다. 또한 “우선 순위=1”로 표시된 테스트만 실행하고, 결과를 *.trx* 파일에 기록합니다.

```cmd
vstest.console.exe myTestFile.dll /Settings:Local.RunSettings /InIsolation /TestCaseFilter:"Priority=1" /Logger:trx
```

다음 명령은 테스트 라이브러리 *myTestProject.dll* 에 대해 `/blame` 옵션을 사용하여 *vstest.console.exe* 를 실행합니다.

```cmd
vstest.console.exe myTestFile.dll /blame
```

테스트 호스트 크래시가 발생한 경우 *sequence.xml* 파일이 생성됩니다. 파일에는 크래시 발생 시 실행 중이던 특정 테스트를 포함하여 실행 시퀀스대로 테스트의 정규화된 이름이 포함됩니다.

테스트 호스트 크래시가 발생하지 않으면 *sequence.xml* 파일이 생성되지 않습니다.

생성된 *sequence.xml* 파일의 예: 

```xml
<?xml version="1.0"?>
<TestSequence>
  <Test Name="TestProject.UnitTest1.TestMethodB" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
  <Test Name="TestProject.UnitTest1.TestMethodA" Source="D:\repos\TestProject\TestProject\bin\Debug\TestProject.dll" />
</TestSequence>
```