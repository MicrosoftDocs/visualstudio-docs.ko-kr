---
title: 0x-2x-4x MSAA 변형 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 668a6603-5082-4c78-98e6-f3dc871aa55b
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f6cc62e4ba56cb7be461bbf3cee5435cb404b7fe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90841618"
---
# <a name="0x2x4x-msaa-variants"></a>0x/2x/4x MSAA 변형
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

모든 렌더링 대상 및 스왑 체인에서 MSAA(MultiSample Anti-Aliasing) 설정을 재정의합니다.  
  
## <a name="interpretation"></a>해석  
 MSAA는 각 픽셀의 여러 위치에 있는 샘플을 사용하여 시각적 품질을 향상시킵니다. 더 높은 수준의 MSAA는 더 많은 샘플을 사용합니다. 그러나 MSAA를 사용하지 않으면 픽셀 중심의 샘플 하나만 사용합니다. 앱에서 MSAA를 사용하도록 설정하면 일반적으로 렌더링 성능 비용이 약간이지만 눈에 띄게 됩니다. 그러나 특정 작업 부하 및 특정 GPU에는 거의 영향을 미치지 않을 수도 있습니다.  
  
 앱이 이미 MSAA를 사용하도록 설정되어 있는 경우 MSAA 변형이 적을수록 더 높은 수준의 기존 NSAA에서 상대적인 성능 저하를 일으킨 것이 됩니다. 특히 0x MSAA 변형은 MSAA를 사용하지 않는 앱의 상대적 성능을 나타냅니다.  
  
 앱이 MSAA를 사용하도록 아직 설정하지 않은 경우 2x MSAA 및 4x MSAA 변형은 앱에서 이러한 변형을 사용하도록 설정하는 경우에 발생하는 상대적 성능 저하를 나타냅니다. 성능 비용이 적절하게 낮은 경우 MSAA를 사용하도록 설정하여 앱의 이미지 품질 개선을 고려합니다.  
  
> [!NOTE]
> 하드웨어에서는 일부 형식에 대해 MSAA를 완전히 지원하지 않을 수 있습니다. 이러한 변형에서 해결할 수 없는 하드웨어 제한이 발생한 경우 성능 요약 테이블의 해당 열은 빈 칸이며 오류 메시지가 생성됩니다.  
  
## <a name="remarks"></a>설명  
 이러한 변형은 렌더링 대상을 생성하는 `ID3DDevice::CreateTexture2D`에 대한 호출 시 샘플 수 및 샘플 품질 인수를 재정의합니다. 특히 이러한 매개 변수는 다음과 같은 경우 재정의됩니다.  
  
- `D3D11_TEXTURE2D_DESC`에서 전달된 `pDesc` 개체가 렌더링 대상을 설명하는 경우, 즉 다음과 같은 경우입니다.  
  
  - BindFlags 멤버에는 D3D11_BIND_TARGET 플래그 또는 D3D11_BIND_DEPTH_STENCIL 플래그 집합이 있습니다.  
  
  - Usage 멤버가 D3D11_USAGE_DEFAULT로 설정된 경우  
  
  - CPUAccessFlags 멤버는 0으로 설정되어 있습니다.  
  
  - MipLevels 멤버는 1으로 설정되어 있습니다.  
  
- 디바이스에서는 `ID3D11Device::CheckMultisampleQualityLevels`이 결정한 대로 요청된 렌더링 대상 형식(D3D11_TEXTURE2D_DESC::Format 멤버)에 대한 요청된 샘플 수(0, 2 또는 4) 및 샘플 품질(0)을 지원합니다.  
  
  D3D11_TEXTURE2D_DESC::BindFlags 멤버에 D3D_BIND_SHADER_RESOURCE 또는 D3D11_BIND_UNORDERED_ACCESS 플래그 집합이 있는 경우 질감 버전이 두 개 생성됩니다. 첫 번째 버전에서 이러한 플래그는 렌더링 대상으로 사용하기 위해 지워지고 두 번째 버전은 첫 번째 버전의 확인 버퍼로 사용하기 위해 이러한 플래그를 그대로 남겨 두는 MSAA가 아닌 질감입니다. MSAA 질감을 셰이더 리소스로 사용하거나 순서가 지정되지 않은 액세스에 사용하는 것은 유효하지 않을 수 있기 때문에 이는 필수입니다. 예를 들어 MSAA 질감에 대해 작동하는 셰이더는 MSAA가 아닌 질감을 예상하므로 잘못된 결과를 생성할 수 있습니다. 변형이 MSAA가 아닌 보조 질감을 만든 경우 MSAA 렌더링 대상이 디바이스 컨텍스트에서 설정 해제될 때마다 이러한 대상의 콘텐츠가 MSAA가 아닌 질감으로 확인됩니다. 마찬가지로 MSAA 렌더링 대상이 셰이더 리소스로 바운딩되어야 하거나 순서가 지정되지 않은 액세스 보기에서 사용될 때마다 확인된 MSAA가 아닌 질감이 대신 바운딩됩니다.  
  
  또한 이러한 변형은 `IDXGIFactory::CreateSwapChain`, `IDXGIFactory2::CreateSwapChainForHwnd`, `IDXGIFactory2::CreateSwapChainForCoreWindow`, `IDXGIFactory2::CreateSwapChainForComposition` 및 `ID3D11CreateDeviceAndSwapChain`을 사용하여 만든 모든 스왑 체인에 대한 MSAA 설정을 재정의합니다.  
  
  이러한 변경에 대한 순수 효과는 MSAA 렌더링 대상에 대한 모든 렌더링이 완료되는 것입니다. 그러나 애플리케이션에서 이러한 렌더링 대상 또는 스왑 체인 버퍼 중 하나를 셰이더 리소스 뷰 또는 순서가 지정되지 않은 액세스 뷰로 사용하면 데이터는 렌더링 대상의 MSAA가 아닌 확인된 복사본에서 샘플링됩니다.  
  
## <a name="restrictions-and-limitations"></a>제한 사항  
 Direct3D11에서 MSAA 질감은 MSAA가 아닌 질감보다 더 제한적입니다. 예를 들어 MSAA 질감에 대해 `ID3D11DeviceContext::UpdateSubresource`를 호출할 수 있으며 원본 리소스와 대상 리소스의 샘플 계산 및 샘플 품질이 일치하지 않는 경우 `ID3D11DeviceContext::CopySubresourceRegion` 호출에 실패합니다. 이러한 문제는 이 변형이 다른 리소스는 제외하고 한 리소스의 MSAA 설정만 재정의하는 경우에 발생할 수 있습니다.  
  
 재생 시 이러한 종류의 충돌이 감지되면 의도된 동작을 복제하려고 최대한 시도하지만 결과가 정확하게 일치하지 않을 수도 있습니다. 이러한 변형의 영향을 잘못 표현하는 방식으로 이 문제가 해당 변형의 성능에 영향을 미치는 것이 일반적이지 않긴 하지만 복제된 질감의 콘텐츠가 동일하지 않을 수 있으므로 가능합니다. 예를 들어 픽셀 셰이더의 흐름 제어가 질감의 정확한 콘텐츠로 결정되는 경우가 여기에 해당됩니다.  
  
## <a name="example"></a>예제  
 `ID3D11Device::CreateTexture2D`를 사용하여 만든 렌더링 대상에 대해 다음과 같은 코드를 사용하여 이러한 변형을 재현할 수 있습니다.  
  
```  
D3D11_TEXTURE2D_DESC target_description;  
target_description.BindFlags = D3D11_BIND_RENDER_TARGET;  
target_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
target_description.SampleDesc.Quality = 0;  
d3d_device->CreateTexture2D(&target_description, nullptr, &render_target);  
```  
  
## <a name="example"></a>예제  
 또는 다음과 같은 코드를 사용하여 IDXGISwapChain::CreateSwapChain 또는 D3D11CreateDeviceAndSwapChain을 사용해 만든 스왑 체인에 대해서도 이러한 변형을 재현할 수 있습니다.  
  
```  
DXGI_SWAP_CHAIN_DESC chain_description;  
chain_description.SampleDesc.Count = 4; // 4x MSAA, can be 2 or 0 instead  
chain_description.SampleDesc.Quality = 0;  
  
// Call IDXGISwapChain::CreateSwapChain or D3D11CreateDeviceAndSwapChain, etc.  
```
