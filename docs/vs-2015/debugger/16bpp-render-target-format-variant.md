---
title: 16bpp 렌더링 대상 형식 변형 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 24b22ad9-5ad0-4161-809a-9b518eb924bf
caps.latest.revision: 8
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 7b315c7ab9bb10d039e81ba26b1beb9c4447a205
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68157567"
---
# <a name="16bpp-render-target-format-variant"></a>16bpp 렌더링 대상 형식 변형
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모든 렌더링 대상 및 백 버퍼에 대한 픽셀 형식을 DXGI_FORMAT_B5G6R5_UNORM으로 설정합니다.  
  
## <a name="interpretation"></a>해석  
 렌더링 대상 또는 백 버퍼는 일반적으로 32bpp(픽셀당 32비트) 형식(예: B8G8R8A8_UNORM)을 사용합니다. 32bpp 형식은 메모리 대역폭을 많이 사용할 수 있습니다. B5G6R5_UNORM 형식은 32bpp 형식의 절반 크기인 16bpp 형식이므로 이 형식을 사용하면 메모리 대역폭에 대한 부담을 줄일 수 있지만 색상 충실도는 떨어집니다.  
  
 이러한 변형으로 성능이 크게 향상되면 앱에서 메모리 대역폭을 너무 많이 사용함을 나타내는 것일 수 있습니다. 프로파일링된 프레임에 상당한 양의 overdraw가 발생하거나 알파 혼합이 많이 포함된 경우 특히 성능 향상이 두드러질 수 있습니다.  
  
 앱에서 렌더링한 장면에 색상 충실도가 높은 재현이 필요 없는 경우, 이러한 장면의 렌더링 대상에 알파 채널이 있을 필요가 없는 경우 그리고 이러한 장면에 일반적으로 부드러운 그라데이션이 없는 경우(색상 충실도가 떨어지면 밴딩 아티팩트로 나타날 수 있음) 16bpp 렌더링 대상 형식을 사용하여 메모리 대역폭 사용을 줄일 것을 고려하세요.  
  
 앱에서 렌더링된 장면에 색상 충실도가 높은 재현 또는 알파 채널이 필요하거나 부드러운 그라데이션이 공통적으로 필요한 경우 메모리 대역폭을 줄이기 위해 다른 전략을 고려하세요. 예를 들어 overdraw 또는 알파 혼합의 양을 줄이거나 프레임 버퍼의 차원 줄이거나 압축을 사용하거나 차원을 줄여 메모리 대역폭 사용을 줄이도록 질감 리소스를 수정할 수 있습니다. 일반적으로 이러한 최적화에 수반되는 이미지 품질 문제도 고려해야 합니다.  
  
 DXGI_FORMAT_B5G6R5_UNORM이 `D3D11CreateDeviceAndSwapChain` 또는 `IDXGIFactory::CreateSwapChain`을 사용하여 만든 스왑 체인에 대해 지원되는 백 버퍼 형식이 아니므로 16bpp 백 버퍼로 전환하면 앱에 이점이 있지만 이러한 백 버퍼가 스왑 체인의 일부인 경우 추가 단계를 수행해야 합니다. 대신 `CreateTexture2D`를 사용하여 B5G6R5_UNORM 형식 렌더링 대상을 만들어 이 대상에 대해 렌더링해야 합니다. 그런 다음 스왑 체인에서 Present를 호출하기 전에 렌더링 대상을 사용하여 전체 화면 쿼드를 원본 질감으로 그려 렌더링 대상을 스왑 체인 백 버퍼로 복사합니다. 이는 메모리 대역폭을 약간 사용하는 추가 단계이지만 대부분의 렌더링 작업은 16bpp 렌더링 대상에 영향을 미치므로 대역폭을 덜 사용합니다. 따라서 렌더링 대상을 스왑 체인 백 버퍼로 복사하는데 사용하는 것보다 대역폭을 적게 사용하면 렌더링 성능이 향상됩니다.  
  
 프레임 버퍼의 큰 부분이 각 타일의 로컬 프레임 버퍼 캐시에 맞을 수 있으므로 타일식 렌더링 기술을 사용하는 GPU 아키텍처는 16bpp 프레임 버퍼를 사용하여 상당한 성능상의 이점을 보여줄 수 있습니다. 타일식 렌더링 아키텍처는 경우에 따라 모바일 송수화기 및 태블릿 컴퓨터의 GPU에 있으므로 이 방식의 아키텍처가 이러한 위치 밖으로 드러나는 일은 거의 없습니다.  
  
## <a name="remarks"></a>설명  
 렌더링 대상을 만드는 `ID3D11Device::CreateTexture2D`에 대한 호출 시 마다 렌더링 대상 형식은 DXGI_FORMAT_B5G6R5_UNORM으로 다시 설정됩니다. 특히 이 형식은 pDesc에서 전달된 D3D11_TEXTURE2D_DESC 개체가 렌더링 대상을 설명하는 경우 재정의됩니다. 즉, 다음과 같은 경우입니다.  
  
- BindFlags 멤버에 D3D11_BIND_REDNER_TARGET 플래그 집합이 있는 경우  
  
- BindFlags 멤버에 D3D11_BIND_DEPTH_STENCIL 플래그가 지워진 경우  
  
- Usage 멤버가 D3D11_USAGE_DEFAULT로 설정된 경우  
  
## <a name="restrictions-and-limitations"></a>제한 사항  
 B5G6R5 형식에는 알파 채널이 없으므로 이 변형은 알파 콘텐츠를 유지하지 않습니다. 앱에서 렌더링하려면 렌더링 대상에 알파 채널이 있어야 하는 경우 간단히 B5G6R5 형식으로 전환할 수 있는 것이 아닙니다.  
  
## <a name="example"></a>예제  
 다음과 같은 코드를 사용 하 여를 사용 하 여 만든 렌더링 대상에 대해 **16bpp 렌더링 대상 형식** 변형을 재현할 수 있습니다 `CreateTexture2D` .  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.Format = DXGI_FORMAT_B5G6R5_UNORM;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```
