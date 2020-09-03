---
title: Point, 선형, 3 중 선형 및 이방성 질감 필터링 변형 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 57d14fc9-b5f7-45ee-9717-48086886742d
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5c53f3b0633ec8938de210cb518d9fae1937eb2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185398"
---
# <a name="point-bilinear-trilinear-and-anisotropic-texture-filtering-variants"></a>Point, Bilinear, Trilinear 및 Anisotropic 텍스처 필터링 변형
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

적절한 질감 샘플러에 대한 필터링 모드를 재정의합니다.  
  
## <a name="interpretation"></a>해석  
 질감 샘플링 방법마다 성능 비용 및 이미지 품질이 다릅니다. 성능 비용이 커지면서 시각적 품질이 높아지는 순으로 필터 모드는 다음과 같습니다.  
  
1. 점 필터링(성능이 가장 적게 저하되지만 시각적 품질은 가장 나쁨)  
  
2. 쌍선형 필터링  
  
3. 3중 선형 필터링  
  
4. 이방성 필터링(성능이 가장 크게 저하되지만 시각적 품질은 가장 좋음)  
  
   각 변형의 성능 비용이 상당하거나 더욱 집약적인 필터링 모드에서 커지는 경우 향상된 이미지 품질에 대비한 성능 비용을 따져볼 수 있습니다. 평가를 바탕으로 추가 성능 비용을 허용하여 시각적 품질을 향상시키거나 저하된 시각적 품질을 허용하여 더 빠른 프레임 속도를 얻거나 다른 방법에 사용할 수 있는 성능을 회수할 수 있습니다.  
  
   필터링 모드에 상관없이 성능 비용이 미미하거나 일정한 경우(예: 대상으로 하는 GUP에 풍부한 셰이더 처리량과 메모리 대역폭이 있는 경우) 앱에서 최상의 이미지 품질을 얻으려면 이방성 필터링 사용을 고려하세요.  
  
## <a name="remarks"></a>설명  
 앱에서 제공하는 샘플러의 필터 모드가 다음 중 하나인 경우 이러한 변형은 `ID3D11DeviceContext::PSSetSamplers` 호출 시 샘플러 상태를 재정의합니다.  
  
- `D3D11_FILTER_MIN_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_POINT_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_POINT_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_MIP_POINT`  
  
- `D3D11_FILTER_MIN_LINEAR_MAG_POINT_MIP_LINEAR`  
  
- `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`  
  
- `D3D11_FILTER_MIN_MAG_MIP_LINEAR`  
  
- `D3D11_FILTER_ANISOTROPIC`  
  
  **점 질감 필터링** 변형의 경우 애플리케이션에서 제공하는 필터 모드는 `D3D11_FILTER_MIN_MAG_MIP_POINT`로 대체되었고 **쌍선형 질감 필터링** 변형의 경우 `D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT`로 대체되었으며 **3중 선형 질감 필터링** 변형의 경우 `D3D11_FILTER_MIN_MAG_MIP_LINEAR`로 대체되었습니다.  
  
  **이방성 질감 필터링** 변형의 경우 애플리케이션에서 제공하는 필터 모드는 `D3D11_FILTER_ANISOTROPIC`으로 대체되었고 최대 이방성이 16으로 설정됩니다.  
  
## <a name="restrictions-and-limitations"></a>제한 사항  
 Direct3D에서 기능 수준 9.1은 최대 2배의 이방성을 지정합니다. **이방성 질감 필터링** 변형은 16배 이방성 사용만을 시도하므로 프레임 분석이 기능 수준 9.1 디바이스에서 실행되면 재생에 실패합니다. 이러한 제한에 영향을 받는 현대식 디바이스에는 ARM 기반 Surface RT 및 Surface 2 Windows 태블릿이 포함됩니다. 일부 컴퓨터에서 아직도 찾아볼 수 있는 이전 GPU에도 적용될 수 있지만 이러한 GPU는 사용되지 않으며 점점 사라져 간다고 널리 간주되고 있습니다.  
  
## <a name="example"></a>예제  
 **점 질감 필터링** 변형은 다음과 같은 코드를 사용하여 재현할 수 있습니다.  
  
```  
D3D11_SAMPLER_DESC sampler_description;  
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>예제  
 **쌍선형 질감 필터링** 변형은 다음과 같은 코드를 사용하여 재현할 수 있습니다.  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_LINEAR_MIP_POINT;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>예제  
 **3중 선형 질감 필터링** 변형은 다음과 같은 코드를 사용하여 재현할 수 있습니다.  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_MIN_MAG_MIP_LINEAR;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```  
  
## <a name="example"></a>예제  
 **이방성 질감 필터링** 변수는 다음과 같은 코드를 사용하여 재현할 수 있습니다.  
  
```  
D3D11_SAMPLER_DESC sampler_description;   
  
// ... other sampler description setup ...  
  
sampler_description.Filter = D3D11_FILTER_ANISOTROPIC;  
sampler_description.MaxAnisotropy = 16;  
  
d3d_device->CreateSamplerState(&sampler_desc, &sampler);  
d3d_context->PSSetSamplers(0, 1, &sampler  
```
