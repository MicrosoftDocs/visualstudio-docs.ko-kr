---
title: BC 텍스처 압축 변형 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
ms.assetid: 2d0f5305-585b-4b01-bc9a-7a32d6e991da
caps.latest.revision: 7
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f0758d9eb5a003b0353ceb4fee21996d90685fa5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161697"
---
# <a name="bc-texture-compression-variant"></a>BC 텍스처 압축 변형
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

B8G8R8X8, B8G8R8A8 또는 R8G8B8A8의 변형인 픽셀 형식이 있는 질감에 대한 블록 압축을 사용하도록 설정합니다.  
  
## <a name="interpretation"></a>해석  
 BC1, BC2 및 BC3과 같은 블록 기반 압축 형식은 압축되지 않은 이미지 형식보다 메모리를 훨씬 더 적게 차지하므로 메모리 대역폭도 상당히 적게 사용합니다. 픽셀당 32비트를 사용하는 압축되지 않은 형식과 비교하여 BC1(이전의 DXT1)의 압축률은 8:1이고 BC3(이전의 DXT5)의 압축률은 4:1입니다. BC1과 BC3 간의 차이점은 BC1은 알파 채널을 지원하지 않는 반면에 BC3은 블록 압축 알파 채널을 지원한다는 점입니다. 압축률이 높음에도 불구하고 일반적인 질감에 대한 이미지 품질은 약간만 떨어집니다. 그러나 특정 종류의 질감(예: 작은 영역에서 색상 변형이 상당한 질감)에 대한 블록 압축 결과는 허용치보다 떨어질 수 있습니다.  
  
 질감이 블록 기반 압축에 적절하고 완벽한 색 충실도가 필요 없는 경우 블록 압축 형식을 사용하여 메모리와 대역폭 사용량을 줄일 것을 고려해 보세요.  
  
## <a name="remarks"></a>설명  
 원본 질감을 만드는 `ID3DDevice::CreateTexture2D`를 호출할 때마다 블록 기반 압축 형식을 사용하여 질감을 압축합니다. 특히, 질감은 다음과 같은 경우 압축됩니다.  
  
- `D3D11_TEXTURE2D_DESC`에서 전달된 `pDesc` 개체가 변하지 않는 셰이더를 설명하는 경우, 즉 다음과 같은 경우입니다.  
  
  - BindFlags 멤버에 D3D11_BIND_SHADER_RESOURCE 플래그 집합만 있는 경우  
  
  - Usage 멤버가 D3D11_USAGE_DEFAULT 또는 D3D11_USAGE_IMMUTABLE로 설정된 경우  
  
  - CPUAccessFlags 멤버가 0으로 설정된 경우(CPU 액세스 없음)  
  
  - SamplerDesc 멤버에 1로 설정된 Count 멤버가 있는 경우(MSAA(MultiSample Anti-Aliasing) 없음)  
  
- 초기 데이터가 `CreateTexture2D`에 대한 호출에 제공된 경우  
  
  다음은 지원되는 원본 형식과 해당 형식의 블록 압축 형식입니다.  
  
|원래 형식(원본)|압축된 형식(대상)|  
|------------------------------|------------------------------|  
|`DXGI_FORMAT_B8G8R8X8_UNORM`|BC1(이전의 DXT1)|  
|`DXGI_FORMAT_B8G8R8X8_UNORM_SRGB`|BC1|  
|`DXGI_FORMAT_B8G8R8X8_TYPELESS`|BC1|  
|`DXGI_FORMAT_B8G8R8A8_UNORM`|BC3(이전의 DXT5)|  
|`DXGI_FORMAT_B8G8R8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_B8G8R8A8_TYPELESS`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_UNORM_SRGB`|BC3|  
|`DXGI_FORMAT_R8G8B8A8_TYPELESS`|BC3|  
  
 질감의 형식이 나열된 형식이 아닌 경우 해당 질감은 수정되지 않습니다.  
  
## <a name="restrictions-and-limitations"></a>제한 사항  
 B8G8R8A8 또는 R8G8B8A8 이미지 형식의 변형을 통해 만든 질감이 실제로 알파 채널을 사용하지 않는 경우가 있습니다. 그러나 이러한 변형에서 알파 채널의 사용 여부를 파악할 수 있는 방법은 없습니다. 알파 채널이 사용되는 경우 정확성을 유지하기 위해 변형은 항상 이러한 형식을 효율성이 떨어지는 BC3 형식으로 인코딩합니다. 알파 채널을 사용하지 않을 때 B8G8R8X8 이미지 형식의 변형을 사용함으로써 그래픽 프레임 분석에서 이러한 변형을 사용했을 때 앱의 잠재적인 렌더링 성능을 더욱 정확하게 파악하도록 할 수 있습니다. 따라서 변형이 효율성이 더욱 뛰어난 BC1 형식을 사용할 수 있습니다.  
  
## <a name="example"></a>예제  
 `CreateTexture2D` 호출 전 런타임 시 이 변형은 질감을 블록으로 압축합니다. 압축되지 않은 질감은 더 많은 디스크 공간을 사용하고, 블록 기반 압축에는 인코딩에 상당한 계산 리소스가 필요하므로 추가 단계에서 앱에서의 로드 시간이 상당히 길어질 수 있기 때문에 프로덕션 코드에는 이러한 접근 방식을 사용하는 것이 좋습니다. 대신 빌드 파이프라인의 일부인 이미지 편집기 또는 이미지 프로세서를 사용하여 질감을 오프라인으로 압축하는 것이 좋습니다. 이러한 접근 방식은 디스크 공간 요구 사항을 줄이고 앱에서 런타임 오버헤드를 없애며 더 긴 처리 시간을 허용하므로 최상의 이미지 품질을 유지할 수 있습니다.  
  
## <a name="see-also"></a>관련 항목  
 [반기/분기 텍스처 차원 변형](../debugger/half-quarter-texture-dimensions-variant.md)
