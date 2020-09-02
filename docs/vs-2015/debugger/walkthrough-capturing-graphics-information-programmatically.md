---
title: '연습: 프로그래밍 방식으로 그래픽 정보 캡처 | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: a5adeff9-afaf-4047-b5ce-ef0aefe710eb
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9de8e2a2ee69911f5505937494d2912c724326e9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75847818"
---
# <a name="walkthrough-capturing-graphics-information-programmatically"></a>연습: 프로그래밍 방식으로 그래픽 정보 캡처
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 그래픽 진단을 사용하여 Direct3D 앱에서 그래픽 정보를 프로그래밍 방식으로 캡처할 수 있습니다.  
  
 프로그래밍 방식 캡처는 다음과 같은 시나리오에서 유용합니다.  
  
- 그래픽 앱이 swapchain present를 사용하지 않는 경우(예: 텍스처로 렌더링하는 경우) 프로그래밍 방식으로 캡처를 시작합니다.  
  
- 앱이 렌더링되지 않는 경우(예: DirectCompute를 사용하여 계산을 수행하는 경우) 프로그래밍 방식으로 캡처를 시작합니다.  
  
- 수동 테스트로는 렌더링 문제를 예측하고 캡처하기 어려워도 런타임의 앱 상태에 대한 정보를 사용하여 프로그래밍 방식으로 예측할 수 있는 경우 `CaptureCurrentFrame`을 호출합니다.  
  
## <a name="programmatic-capture-in-windows-81"></a><a name="CaptureDX11_2"></a> Windows 8.1에서 프로그래밍 방식 캡처  
 이 연습 부분에서는 Windows 8.1에서 DirectX 11.2 API를 사용하는 앱의 프로그래밍 방식 캡처를 보여 줍니다. 이 API는 강력한 캡처 방법을 사용합니다. Windows 8.0에서 이전 버전의 DirectX를 사용하는 앱에서 프로그래밍 캡처를 사용하는 방법에 대한 자세한 내용은 이 연습 뒷부분의 [Programmatic capture in Windows 8.0 and earlier](#CaptureDX11_1) 를 참조하세요.  
  
 이 섹션에서는 다음 작업을 수행하는 방법을 보여줍니다.  
  
- 프로그래밍 캡처를 사용하도록 앱 준비  
  
- IDXGraphicsAnalysis 인터페이스 가져오기  
  
- 그래픽 정보 캡처  
  
> [!NOTE]
> 프로그래밍 방식 캡처의 이전 구현에서는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 용 원격 도구를 사용하여 캡처 기능을 제공했으나 Windows 8.1에서는 Direct3D 11.2를 통해 캡처 기능을 직접 지원합니다. 따라서 Windows 8.1에서는 더 이상 프로그래밍 캡처를 위해 원격 도구를 설치할 필요가 없습니다.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>프로그래밍 캡처를 사용하도록 앱 준비  
 앱에서 프로그래밍 방식 캡처를 사용하려면 필요한 헤더를 포함해야 합니다. 이러한 헤더는 Windows 8.1 SDK의 일부입니다.  
  
##### <a name="to-include-programmatic-capture-headers"></a>프로그래밍 캡처 헤더를 포함하려면  
  
- IDXGraphicsAnalysis 인터페이스를 정의할 소스 파일에 다음 헤더 파일을 포함합니다.  
  
    ```  
    #include <DXGItype.h>  
    #include <dxgi1_2.h>  
    #include <dxgi1_3.h>  
    #include <DXProgrammableCapture.h>  
    ```  
  
    > [!IMPORTANT]
    > Windows 8.1 앱에서 프로그래밍 방식 캡처를 수행하기 위해 Windows 8.0 및 이전 버전에서 프로그래밍 방식 캡처를 지원하는 헤더 파일인 vsgcapture.h를 포함하지 마세요. 이 헤더는 DirectX 11.2와 호환되지 않습니다. d3d11_2.h 헤더를 포함한 후 이 파일을 포함하면 컴파일러에 경고가 표시됩니다. d3d11_2.h 앞에 vsgcapture.h를 포함하면 앱이 시작되지 않습니다.  
  
    > [!NOTE]
    > 컴퓨터에 June 2010 DirectX SDK가 설치되어 있고 프로젝트의 포함 경로에 `%DXSDK_DIR%includex86`이 포함되어 있으면 이 부분을 포함 경로의 끝으로 옮깁니다. 라이브러리 경로에 대해서도 동일하게 수행합니다.  
  
#### <a name="windows-phone-81"></a>Windows Phone 8.1  
 Windows Phone 8.1 SDK는 DXProgrammableCapture 헤더를 포함 하지 않기 때문에 `IDXGraphicsAnalysis` 및 메서드를 사용할 수 있도록 인터페이스를 직접 정의 해야 합니다 `BeginCapture()` `EndCapture()` . 이전 섹션에서 설명한 대로 다른 헤더를 포함합니다.  
  
###### <a name="to-define-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis 인터페이스를 정의하려면  
  
- 헤더 파일을 포함한 것과 동일한 파일에 IDXGraphicsAnalysis 인터페이스를 정의합니다.  
  
  ```  
  interface DECLSPEC_UUID("9f251514-9d4d-4902-9d60-18988ab7d4b5") DECLSPEC_NOVTABLE  
  IDXGraphicsAnalysis : public IUnknown  
  {  
      STDMETHOD_(void, BeginCapture)() PURE;  
      STDMETHOD_(void, EndCapture)() PURE;  
  };  
  ```  
  
  편의를 위해 새 헤더 파일에서 이러한 단계를 수행한 다음 앱에서 필요한 위치에 이 파일을 포함할 수 있습니다.  
  
### <a name="getting-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis 인터페이스 가져오기  
 DirectX 11.2에서 그래픽 정보를 캡처하려면 DXGI 디버그 인터페이스를 가져와야 합니다.  
  
> [!IMPORTANT]
> 프로그래밍 방식 캡처를 사용하는 경우 여전히 그래픽 진단([!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 경우 Alt+F5) 또는 [명령줄 캡처 도구](../debugger/command-line-capture-tool.md)에서 앱을 실행해야 합니다.  
  
##### <a name="to-get-the-idxgraphicsanalysis-interface"></a>IDXGraphicsAnalysis 인터페이스를 가져오려면  
  
- 다음 코드를 사용하여 IDXGraphicsAnalysis 인터페이스를 DXGI 디버그 인터페이스에 연결합니다.  
  
    ```  
    IDXGraphicsAnalysis* pGraphicsAnalysis;  
    HRESULT getAnalysis = DXGIGetDebugInterface1(0, __uuidof(pGraphicsAnalysis), reinterpret_cast<void**>(&pGraphicsAnalysis));  
    ```  
  
     `HRESULT` 이 반환한 `DXGIGetDebugInterface1` 를 확인하여 인터페이스를 사용하기 전에 유효한지 확인해야 합니다.  
  
    ```  
    if (FAILED(getAnalysis))  
    {  
        // Abort program or disable programmatic capture in your app.  
    }  
    ```  
  
    > [!NOTE]
    > `DXGIGetDebugInterface1` 이 `E_NOINTERFACE` (`error: E_NOINTERFACE No such interface supported`)를 반환하는 경우 앱이 그래픽 진단에서 실행되고 있는지 확인합니다( [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]의 Alt+F5)로 앱을 실행해야 합니다.  
  
### <a name="capturing-graphics-information"></a>그래픽 정보 캡처  
 이제 유효한 `IDXGraphicsAnalysis` 인터페이스가 있으므로 `BeginCapture` 및 `EndCapture` 를 사용하여 그래픽 정보를 캡처할 수 있습니다.  
  
##### <a name="to-capture-graphics-information"></a>그래픽 정보를 캡처하려면  
  
- 그래픽 정보 캡처를 시작하려면 다음과 같이 `BeginCapture`를 사용합니다.  
  
    ```  
    ...  
    pGraphicsAnalysis->BeginCapture();  
    ...  
    ```  
  
     `BeginCapture` 가 호출되면 즉시 캡처가 시작됩니다. 다른 프레임이 시작되도록 기다리지 않습니다. 현재 프레임이 표시되거나 다음과 같이 `EndCapture`를 호출하면 캡처가 중지됩니다.  
  
    ```  
    ...  
    pGraphicsAnalysis->EndCapture();  
    ...  
    ```  
  
## <a name="programmatic-capture-in-windows-80-and-earlier"></a><a name="CaptureDX11_1"></a> Programmatic capture in Windows 8.0 and earlier  
 이 연습 부분에서는 DirectX 11.1 API를 사용하는 Windows 8.0 및 이전 버전용 앱의 프로그래밍 방식 캡처를 보여 줍니다. 이 API는 레거시 캡처 방법을 사용합니다. Windows 8.1에서 DirectX 11.2를 사용하는 앱에서 프로그래밍 캡처를 사용하는 방법에 대한 자세한 내용은 이 연습 뒷부분의 [Windows 8.1의 프로그래밍 방식 캡처](#CaptureDX11_2) 를 참조하세요.  
  
 이 부분에서는 다음 작업을 수행하는 방법을 보여줍니다.  
  
- 프로그래밍 캡처를 사용하도록 컴퓨터 준비  
  
- 프로그래밍 캡처를 사용하도록 앱 준비  
  
- 그래픽 로그 파일의 이름 및 위치 구성  
  
- `CaptureCurrentFrame` API 사용  
  
### <a name="preparing-your-computer-to-use-programmatic-capture"></a>프로그래밍 캡처를 사용하도록 컴퓨터 준비  
 프로그래밍 캡처 API는 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 용 원격 도구를 사용하여 캡처 기능을 제공합니다. 로컬 컴퓨터에서 프로그래밍 캡처를 사용하더라도 앱을 실행할 컴퓨터에는 원격 도구가 설치되어 있어야 합니다. 로컬 컴퓨터에서 프로그래밍 캡처를 수행하는 경우[!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 를 실행 중일 필요는 없습니다.  
  
 컴퓨터에서 실행 중인 앱에서 원격 캡처 API를 사용하려면 먼저 해당 컴퓨터에 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 용 원격 도구를 설치해야 합니다. 원격 도구 버전마다 지원하는 하드웨어 플랫폼이 다릅니다. 원격 도구 설치 방법에 대한 자세한 내용은 Microsoft 다운로드 웹 사이트에서 [원격 도구 다운로드 페이지](https://visualstudio.microsoft.com/downloads#remote-tools) 를 참조하세요.  
  
 그렇지 않으면 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서는 32비트 앱용 원격 캡처를 수행하기 위한 필수 구성 요소를 설치합니다.  
  
> [!NOTE]
> [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]를 비롯한 대부분의 Windows 데스크톱 앱이 ARM 디바이스용 [!INCLUDE[win8](../includes/win8-md.md)] 에서 지원되지 않으므로 ARM 디바이스에서 그래픽 진단을 캡처하는 유일한 방법은 프로그래밍 캡처 API와 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 용 원격 도구를 함께 사용하는 것입니다.  
  
### <a name="preparing-your-app-to-use-programmatic-capture"></a>프로그래밍 캡처를 사용하도록 앱 준비  
 그래픽 진단 도구를 사용하려면 먼저, 이 도구에서 사용하는 그래픽 정보를 캡처해야 합니다. `CaptureCurrentFrame` API를 사용하여 정보를 프로그래밍 방식으로 캡처할 수 있습니다.  
  
##### <a name="to-prepare-your-app-to-capture-graphics-information-programmatically"></a>그래픽 정보를 프로그래밍 방식으로 캡처하도록 앱을 준비하려면  
  
1. `vsgcapture.h` 헤더가 앱의 소스 코드에 포함되어 있는지 확인합니다. 헤더는 단 한 곳, 예를 들어 프로그래밍 캡처 API를 호출할 소스 코드 파일에 포함하거나 여러 소스 코드 파일에서 API를 호출하기 위해 미리 컴파일된 헤더 파일에 포함할 수 있습니다.  
  
2. 현재 프레임의 나머지를 캡처하려고 할 때마다 앱의 소스 코드에서 `g_pVsgDbg->CaptureCurrentFrame()`을 호출합니다. 이 방법은 매개 변수를 사용하지 않고 값을 반환하지 않습니다.  
  
### <a name="configuring-the-name-and-location-of-the-graphics-log-file"></a>그래픽 로그 파일의 이름 및 위치 구성  
 그래픽 로그는 `DONT_SAVE_VSGLOG_TO_TEMP` 및 `VSG_DEFAULT_RUN_FILENAME` 매크로가 정의한 위치에 생성됩니다.  
  
##### <a name="to-configure-the-name-and-location-of-the-graphics-log-file"></a>그래픽 로그 파일의 이름 및 위치를 구성하려면  
  
- 그래픽 로그가 임시 디렉터리에 기록되지 않도록 하려면 `#include <vsgcapture.h>` 줄 앞에 다음과 같이 추가합니다.  
  
  ```  
  #define DONT_SAVE_VSGLOG_TO_TEMP  
  ```  
  
   작업 디렉터리에 상대적인 위치 또는 `VSG_DEFAULT_RUN_FILENAME` 의 정의가 절대 경로인 경우에는 절대 경로에 그래픽 로그를 쓰도록 이 값을 정의할 수 있습니다.  
  
- 그래픽 로그를 다른 위치에 저장하거나 그래픽 로그에 다른 파일 이름을 지정하려면 `#include <vsgcapture.h>` 줄 앞에 다음과 같이 추가합니다.  
  
  ```  
  #define VSG_DEFAULT_RUN_FILENAME <filename>  
  ```  
  
   이 단계를 수행하지 않으면 파일 이름은 default.vsglog가 됩니다. `DONT_SAVE_VSGLOG_TO_TEMP`를 정의하지 않으면 로그 파일의 위치는 임시 디렉터리에 대해 상대적입니다. 그렇지 않은 경우에는 작업 디렉터리에 대해 상대적이고 절대 파일 이름을 지정한 경우에는 다른 위치에 있습니다.  
  
  앱의 경우 [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 임시 디렉터리의 위치는 각 사용자 및 앱에만 해당 되며 일반적으로 C:\users \\ *username*\AppData\Local\Packages \\ *package family name*\tempstate와 같은 위치에서 찾을 수 \\ 있습니다. 데스크톱 앱의 경우 임시 디렉터리의 위치는 각 사용자와 관련이 있으며 일반적으로 C:\Users username \AppData\Local\Temp과 같은 위치에 있습니다 \\ *username* \\ .  
  
> [!NOTE]
> 특정 위치에 기록하려면 해당 위치에 대한 쓰기 권한이 있어야 합니다. 그렇지 않으면 오류가 발생합니다. [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] 앱은 데이터를 쓸 수 있는 위치에 대해 데스크톱 앱보다 더욱 제한적입니다. 그러므로 특정 위치에 쓰려면 추가 구성이 필요할 수 있습니다.  
  
### <a name="capturing-the-graphics-information"></a>그래픽 정보 캡처  
 프로그래밍 캡처를 위해 앱을 준비하고 그래픽 로그 파일의 위치 및 이름을 선택적으로 구성한 후 앱을 빌드한 다음 실행하거나 디버그하여 데이터를 캡처합니다. 그러나 프로그래밍 캡처 API를 사용하는 경우 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 에서 그래픽 진단을 시작하지 마세요. 그래픽 로그는 지정한 위치에 기록됩니다. 이 로그 버전을 보관하려면 다른 위치로 이동합니다. 그렇지 않으면 앱을 다시 시작할 때 덮어씁니다.  
  
> [!TIP]
> 프로그래밍 캡처를 사용 중에도 그래픽 정보를 수동으로 캡처할 수 있습니다. 앱에 포커스를 둔 상태에서 **Print Screen**키를 누르기만 하면 됩니다. 이 기술을 사용하여 프로그래밍 캡처 API로 캡처되지 않는 추가 그래픽 정보를 캡처할 수 있습니다.  
  
## <a name="next-steps"></a>다음 단계  
 이 연습에서는 그래픽 정보를 프로그래밍 방식으로 캡처하는 방법을 보여주었습니다. 다음 단계로 아래 옵션을 고려해 보세요.  
  
- 그래픽 진단 도구를 사용하여 캡처한 그래픽 정보를 분석하는 방법에 대해 알아봅니다. [개요](../debugger/overview-of-visual-studio-graphics-diagnostics.md)를 참조하세요.  
  
## <a name="see-also"></a>관련 항목  
 [연습: 그래픽 정보 캡처](../debugger/walkthrough-capturing-graphics-information.md)   
 [그래픽 정보 캡처](../debugger/capturing-graphics-information.md)   
 [명령줄 캡처 도구](../debugger/command-line-capture-tool.md)
