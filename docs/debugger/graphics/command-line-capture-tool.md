---
title: 명령줄 캡처 도구 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: db75b3a7-80b2-4a74-91d2-fd6e0f73b45d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c4d88e62b1520677ddac3ff66a6891eb805af30d
ms.sourcegitcommit: 3fe6bed9ef8fb1478106645f655c7472009ae43a
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64808463"
---
# <a name="command-line-capture-tool"></a>명령줄 캡처 도구
DXCap.exe는 그래픽 진단 캡처 및 재생을 위한 명령줄 도구로, 모든 기능 수준에서 Direct3D 10 - Direct3D 12를 지원합니다.

## <a name="syntax"></a>구문

```cmd
DXCap.exe [-file filename] [-frame frames | -period periods | -manual] -c app [args...]
DXCap.exe -p [filename] [-debug | -warp | -hw] [-config] [-rawmode]
DXCap.exe -p [filename] -screenshot [-frame frames]
DXCap.exe -p [filename] -toXML [xml_filename]
DXCap.exe -v [-file filename] [-examine events] [-haltonfail | -exitonfail] [-showprogress]
DXCap.exe -e [search_string]
DXCap.exe -info
```

#### <a name="parameters"></a>매개 변수
 `-file` `filename`: 캡처 모드(`-c`)에서 `filename`은 그래픽 정보가 기록되는 그래픽 로그 파일의 이름을 지정합니다. `filename`을 지정하지 않으면 그래픽 정보는 기본적으로 `<appname>-<date>-<time>.vsglog` 파일에 기록됩니다.

 유효성 검사(-v) 모드에서 `filename`은 유효성을 검사할 그래픽 로그 파일의 이름을 지정합니다. `filename`을 지정하지 않으면 마지막으로 유효성을 검사한 그래픽 로그를 다시 사용합니다.

 `-frame` `frames`: 캡처 모드에서 `frames`는 캡처하려는 프레임을 지정합니다. 첫 번째 프레임은 1입니다. 쉼표 및 범위를 사용하여 몇 개의 프레임을 지정할 수 있습니다. 예를 들어 `frames`가 `2, 5, 7-9, 15`인 경우 프레임 `2`, `5`, `7`, `8`, `9`, `15`가 캡처됩니다.

> [!TIP]
> Print Screen 키를 눌러 프레임을 수동으로 캡처하도록 지정하려면 `-frame` `manual`을 사용합니다. 앱이 시작될 때 프레임을 캡처할 수 있습니다. 프레임 캡처를 중지하려면 명령줄 인터페이스로 돌아가서 Enter 키를 누릅니다.

 `-period` `periods`: 캡처 모드에서 `periods`는 프레임을 캡처할 시간 범위를 초 단위로 지정합니다. 쉼표와 범위를 사용하여 몇 개의 기간을 지정할 수 있습니다. 예를 들어 `periods`가 `2.1-5, 7.0-9.3`인 경우 `2.1` ~ `5`초 사이 및 `7` ~ `9.3`초 사이에 렌더링된 프레임을 캡처합니다.

 `-c` `app` [`args...`]: 캡처 모드입니다. 캡처 모드에서 `app`은 그래픽 정보를 캡처할 앱의 이름을 지정하고 `args...`는 해당 앱에 대한 추가 명령줄 매개 변수를 지정합니다.

 `-p` [`filename`]: 재생 모드(`-p`)입니다. 재생 모드에서 `filename`은 재생할 그래픽 로그 파일의 이름을 지정합니다. `filename`을 지정하지 않으면 마지막으로 재생한 그래픽 로그가 다시 사용됩니다.

 `-debug`: 재생 모드에서 `-debug`는 Direct3D 디버그 레이어를 사용하도록 설정한 상태로 재생하도록 지정합니다.

 `-warp`: 재생 모드에서 `-warp`는 WARP 소프트웨어 렌더러를 사용하여 재생하도록 지정합니다.

 `-hw` 재생 모드에서 `-hw`는 GPU 하드웨어를 사용하여 재생하도록 지정합니다.

 `-config` 재생 모드에서 `-config`는 그래픽 로그 파일을 캡처하는 데 사용된 머신에 대한 정보를 표시합니다.

 `-rawmode`: 재생 모드에서 `-rawmode`는 기록된 이벤트를 수정하지 않고 재생을 수행하도록 지정합니다. 일반 작업 시 재생 모드에서는 디버깅을 간소화하고 재생 속도를 높이기 위해 약간의 변경이 수행될 수 있습니다. 예를 들어 스왑 체인 명령을 실행하지 않고 스왑 체인 출력을 시뮬레이트할 수 있습니다. 일반적으로 이러한 재생은 문제가 되지 않지만, 기록된 이벤트에 보다 적합한 방식으로 재생해야 할 수도 있습니다. 예를 들어 이 옵션을 사용하면 전체 화면 모드로 실행하는 동안 캡처된 전체 화면 렌더링 동작을 앱에 복원할 수 있습니다.

 `-toXML` [`xml_filename`] 재생 모드에서 `xml_filename`은 재생의 XML 표현이 기록되는 파일의 이름을 지정합니다. `xml_filename`을 지정하지 않으면 XML 표현은 재생 중인 파일과 이름이 같은 파일에 기록되며 `.xml` 확장명이 지정됩니다.

 `-v` 유효성 검사 모드입니다. 유효성 검사 모드에서 캡처된 프레임은 하드웨어와 WARP 둘 다에서 재생되며 이미지 비교 기능을 통해 해당 결과를 비교합니다. 이 기능을 사용하여 렌더링에 영향을 주는 드라이버 문제를 신속하게 파악할 수 있습니다.

 `-examine` `events`: 유효성 검사 모드에서 `events`는 즉각적인 결과를 비교할 그래픽 이벤트 집합을 지정합니다. 예를 들어 `-examine present,draw,copy,clear`는 비교를 해당 범주에 속하는 이벤트로만 제한합니다.

> [!TIP]
> 처음에는 `-examine present,draw,copy,clear`를 사용하는 것이 좋습니다. 그러면 대부분의 문제는 표시되면서 보다 포괄적인 이벤트 집합에 비해 시간은 훨씬 적게 걸립니다. 필요한 경우 더 많은 이벤트 집합 또는 다른 이벤트 집합을 지정하여 해당 이벤트의 유효성을 검사하고 다른 종류의 문제를 확인할 수 있습니다.

 `-haltonfail`: 유효성 검사 모드에서 `-haltonfail`은 하드웨어와 WARP 렌더러 간에 차이점이 검색되면 유효성 검사를 중지합니다. 키를 누르면 유효성 검사를 다시 시작합니다.

 `-exitonfail`: 유효성 검사 모드에서 `-exitonfail`은 하드웨어와 WARP 렌더러 간에 차이점이 검색되면 유효성 검사를 즉시 종료합니다. 이러한 방식으로 종료된 프로그램은 환경에 `0`을 반환하고 그 외의 경우에는 `1`을 반환합니다.

 `-showprogress`: 유효성 검사 모드에서 `-showprogress`는 유효성 검사 세션에 대한 진행률 정보를 표시합니다. 왼쪽에는 WARP 진행률이 표시되고 오른쪽에는 하드웨어 진행률이 표시됩니다.

 `-e` `search_string`: 설치된 UWP 앱을 열거합니다. 이 정보를 사용하여 UWP 앱으로 명령줄 캡처를 수행할 수 있습니다.

 `-info` 머신 및 캡처 DLL에 대한 정보를 표시합니다.

## <a name="remarks"></a>설명
 DXCap.exe는 다음의 세 가지 모드로 작동합니다.

 캡처 모드(-c): 실행 중인 앱에서 그래픽 정보를 캡처하여 그래픽 로그 파일에 기록합니다. 캡처 기능 및 파일 형식은 Visual Studio와 같습니다.

 재생 모드(-p): 기존 그래픽 로그 파일에서 이전에 캡처한 그래픽 이벤트를 재생합니다. 기본적으로는 전체 화면 앱에서 그래픽 로그 파일을 캡처했더라도 재생은 창에서 수행됩니다. 그래픽 로그 파일을 전체 화면 앱에서 캡처했으며 `-rawmode`가 지정된 경우에만 전체 화면에서 재생이 수행됩니다.

 유효성 검사 모드(`-v`): 하드웨어와 WARP 둘 다에서 캡처된 프레임을 재생한 다음, 이미지 비교 기능을 사용하여 해당 결과를 비교하는 방법으로 렌더링 동작의 유효성을 검사합니다. 이 기능을 사용하여 렌더링에 영향을 주는 드라이버 문제를 신속하게 파악할 수 있습니다.

 이러한 모드 이외에 dxcap.exe는 그래픽 정보 캡처 또는 재생을 수행하지 않는 두 가지 기타 기능을 수행합니다.

 열거 기능(`-e`): 머신에 설치되어 있는 UWP 앱에 대한 세부 정보를 표시합니다. 이러한 세부 정보로는 UWP 앱의 실행 파일을 식별하는 appid 및 패키지 이름이 포함됩니다. DXCap.exe를 사용하여 windows 스토어 앱에서 그래픽 정보를 캡처하려면 데스크톱 앱을 캡처할 때 사용한 실행 파일 이름 대신 패키지 이름과 appid를 사용합니다.

 정보 기능(`-info)`): 머신 및 캡처 DLL에 대한 세부 정보를 표시합니다.

## <a name="examples"></a>예

### <a name="capture-graphics-information-from-a-desktop-app"></a>데스크톱 앱에서 그래픽 정보 캡처
 그래픽 정보를 캡처할 앱을 지정하려면 `-c`를 사용합니다.

```cmd
DXCap.exe -c BasicHLSL11.exe
```

 그래픽 정보는 기본적으로 `<appname>-<date>-<time>.vsglog` 파일에 기록됩니다. 정보를 기록할 다른 파일을 지정하려면 `-file`을 사용합니다.

```cmd
DXCap.exe -file regression_test_12.vsglog -c BasicHLSL11.exe
```

 캡처할 앱에 대해 추가 명령줄 매개 변수를 지정하려면 앱 파일 이름 뒤에 해당 매개 변수를 포함합니다.

```cmd
DXCap.exe -c "C:\Program Files\Internet Explorer\iexplorer.exe" "www.fishgl.com"
```

 위 예제의 명령은 WebGL API를 사용하여 3D 콘텐츠를 렌더링하는 www.fishgl.com 의 웹 페이지를 보는 동안 데스크톱 버전 Internet Explorer에서 그래픽 정보를 캡처합니다.

> [!NOTE]
> 앱 다음에 표시되는 명령줄 인수는 앱에 전달되므로 `-c` 옵션을 사용하기 전에 DXCap.exe용 인수를 지정해야 합니다.

### <a name="capture-graphics-information-from-a-uwp-app"></a>UWP 앱에서 그래픽 정보 캡처
 UWP 앱에서 그래픽 정보를 캡처할 수 있습니다.

```cmd
DXCap.exe -c Microsof.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps
```

 DXCap.exe를 사용하여 UWP 앱에서 정보를 캡처하는 것은 해당 파일을 사용하여 Windows 데스크톱 앱에서 캡처하는 것과 비슷합니다. 그러나 데스크톱 앱의 경우 파일 이름으로 식별하는 방식과는 달리, UWP 앱은 해당 패키지 이름과 정보를 캡처할 패키지 내의 실행 파일 이름이나 ID로 식별합니다. 머신에 설치되어 있는 UWP 앱을 식별하는 방법을 쉽게 확인하려면 DXCap.exe에서 `-e` 옵션을 사용하여 해당 앱을 열거합니다.

```cmd
DXCap.exe -e
```

 원하는 앱을 찾기 위해 선택적 검색 문자열을 입력할 수 있습니다. 검색 문자열을 입력하면 DXCap.exe는 해당 패키지 이름, 앱 이름 또는 앱 ID가 검색 문자열과 일치하는 UWP 앱을 열거합니다. 검색은 대/소문자를 구분합니다.

```cmd
DXCap.exe -e map
```

 위의 명령은 “map”과 일치하는 UWP 앱을 열거합니다. 해당 출력은 다음과 같습니다.

 **Package "Microsoft.BingMaps":** **InstallDirectory : C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **전체 이름         : Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe** **UserSID          : S-1-5-21-2127521184-1604012920-1887927527-5603533** **이름             : Microsoft.BingMaps** **게시자        : CN=Microsoft Corporation, O=Microsoft Corporation, L=Redmond, S=Washington, C=US** **버전          : 2.1.2914.1734** **시작 가능한 애플리케이션:** **Id: AppexMaps** **Exe: C:\Program Files\WindowsApps\Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe\Map.exe** **IsWWA: No** **AppSpec(시작): DXCap.exe -c Microsoft.BingMaps_2.1.2914.1734_x64__8wekyb3d8bbwe,AppexMaps** 열거된 각 앱에 대한 출력의 마지막 줄에는 해당 앱에서 그래픽 정보를 캡처하는 데 사용할 수 있는 명령이 표시됩니다.

### <a name="capture-specific-frames-or-frames-between-specific-times"></a>특정 프레임 또는 특정 시간 사이의 프레임 캡처
 쉼표와 범위를 사용하여 캡처할 프레임을 지정하려면 `-frame`을 사용합니다.

```cmd
DXCap.exe -frame 2,5,7-9,15 -c SimpleBezier11.exe
```

 또는 `-period`를 사용하여 프레임을 캡처할 시간 범위 집합을 지정합니다. 시간 범위는 초로 지정되며 여러 범위를 지정할 수 있습니다.

```cmd
DXCap.exe -period 2.1-5, 7.0-9.3 -c SimpleBezier11.exe
```

### <a name="capture-frames-interactively"></a>대화형으로 프레임 캡처
 대화형으로 프레임을 캡처하려면 `-manual`을 사용합니다. 캡처를 시작하려면 Enter 키를 누릅니다. Enter 키를 다시 누르면 캡처가 중지됩니다.

```cmd
DXCap.exe -manual -c SimpleBezier11.exe
```

### <a name="play-back-a-graphic-log-file"></a>그래픽 로그 파일 재생
 이전에 캡처한 그래픽 로그 파일을 재생하려면 `-p`를 사용합니다.

```cmd
DXCap.exe -p regression_test_12.vsglog
```

 가장 최근에 캡처한 그래픽 로그를 재생하려면 파일 이름을 생략합니다.

```cmd
DXCap.exe -p
```

### <a name="play-back-in-raw-mode"></a>원시 모드에서 재생
 캡처된 명령을 실행된 그대로 정확히 재생하려면 `-rawmode`를 사용합니다. 일반 재생 시 특정 명령은 에뮬레이트됩니다. 예를 들어 전체 화면 앱에서 캡처한 그래픽 로그 파일이 창에서 재생됩니다. 그러나 원시 모드를 사용하도록 설정하면 동일한 파일이 전체 화면에서 재생됩니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -rawmode
```

### <a name="play-back-using-warp-or-a-hardware-device"></a>WARP 또는 하드웨어 디바이스를 사용하여 재생
 하드웨어 디바이스에서 캡처된 그래픽 로그 파일 재생 시 WARP를 사용하거나 WARP에서 캡처된 로그 재생 시 하드웨어 디바이스를 사용하도록 강제 지정할 수 있습니다. WARP를 사용하여 재생하려면 `-warp`를 사용합니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -warp
```

 하드웨어를 사용하여 재생하려면 `-hw`를 사용합니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -hw
```

### <a name="validate-a-graphics-log-file-against-warp"></a>WARP에 대해 그래픽 로그 파일 유효성 검사
 유효성 검사 모드에서는 그래픽 로그 파일을 하드웨어와 WARP 둘 다에서 재생한 다음 해당 결과를 비교합니다. 따라서 드라이버에 의해 발생하는 렌더링 오류를 파악할 수 있습니다. WARP에 대해 그래픽 하드웨어의 올바른 동작 유효성을 검사하려면 -v를 사용합니다.

```cmd
DXCap.exe -v regression_test_12.vsglog
```

 비교되는 결과의 양을 줄이려면 유효성 검사에 대해 비교할 명령 하위 집합을 지정할 수 있습니다. 그러면 다른 명령은 무시됩니다. 결과를 비교할 명령을 지정하려면 -examine을 사용합니다.

```cmd
DXCap.exe -v regression_test_12.vsglog -examine present,draw,copy,clear
```

### <a name="convert-a-graphics-log-file-to-pngs"></a>그래픽 로그 파일을 PNG로 변환
 그래픽 로그 파일에서 프레임을 확인하거나 분석하려는 경우 DXCap.exe에서 캡처한 프레임을 .png(이동식 네트워크 그래픽) 이미지 파일로 저장할 수 있습니다. 재생 모드에서 캡처된 프레임을 .png 파일로 출력하려면 `-screenshot`을 사용합니다.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot
```

 출력할 프레임을 지정하려면 `-frame`과 `-screenshot`을 함께 사용합니다.

```cmd
DXCap.exe -p BasicHLSL11.vsglog -screenshot -frame 5, 7-9
```

### <a name="convert-a-graphics-log-file-to-xml"></a>그래픽 로그 파일을 XML로 변환
 FindStr, XSLT 등의 익숙한 도구를 사용하여 그래픽 로그를 처리 및 분석하려는 경우 DXCap.exe에서 그래픽 로그 파일을 XML로 변환할 수 있습니다. 재생 모드에서 로그를 재생하는 대신 XML로 변환하려면 `-toXML`을 사용합니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML
```

 기본적으로 XML 출력은 그래픽 로그와 이름이 같은 파일에 기록되지만 확장명이 .xml로 지정됩니다. 위 예제에서 XML 파일의 이름은 **regression_test_12.xml**입니다. XML 파일에 다른 이름을 지정하려면 `-toXML` 뒤에 원하는 이름을 지정합니다.

```cmd
DXCap.exe -p regression_test_12.vsglog -toXML temp.xml
```

 결과 파일에는 다음과 같은 XML이 포함됩니다.

```xml
<Moment value="67"/>
<Method name="CreateDXGIFactory1" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="riid" type="IID" value="770AAE78-F26F-4DBA-A829-253C83D1B387" />
    <Parameter name="ppFactory" type="void" handle="1" isOutput="true" />
</Method>

<Moment value="167"/>
<Method name="D3D11CreateDevice" >
    <Return type="HRESULT" value="S_OK" />
    <Parameter name="pAdapter" type="IDXGIAdapter" handle="34" />
    <Parameter name="DriverType" type="D3D_DRIVER_TYPE" value="D3D_DRIVER_TYPE_UNKNOWN" />
    <Parameter name="Software" type="HMODULE" value="pointer" />
    <Parameter name="Flags" type="UINT" value="0" />
    <Parameter name="pFeatureLevels" type="D3D_FEATURE_LEVEL" arrSize="1" >
        <Element value="D3D_FEATURE_LEVEL_11_0" />
    </Parameter>
    <Parameter name="FeatureLevels" type="UINT" value="1" />
    <Parameter name="SDKVersion" type="UINT" value="7" />
    <Parameter name="ppDevice" type="ID3D11Device" handle="35" isOutput="true" />
    <Parameter name="pFeatureLevel" type="D3D_FEATURE_LEVEL" value="D3D_FEATURE_LEVEL_11_0" isOutput="true" />
    <Parameter name="ppImmediateContext" type="ID3D11DeviceContext" value="nullptr" isOutput="true" />
</Method>
```

## <a name="requirements"></a>요구 사항