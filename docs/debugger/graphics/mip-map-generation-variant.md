---
title: Mip 맵 생성 변형 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3b4b3583-0b01-4f5d-aacb-3f96d19111d9
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 422a68f4e33733aa2874c639f0dcc799cd3ec795
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72734897"
---
# <a name="mip-map-generation-variant"></a>MIP 맵 생성 변형
렌더링 대상이 아닌 질감에 대해 Mip 맵을 사용합니다.

## <a name="interpretation"></a>해석
Mip 맵은 더 작은 버전의 질감을 미리 계산하여 최소화한 질감에서 앨리어싱 아티팩트를 제거하는 데 주로 사용됩니다. 이러한 추가 질감은 원래 질감보다 약 33%나 더 많은 GPU 메모리를 사용하지만 노출 영역의 더 많은 부분이 GPU 질감 캐시에 적합하고 콘텐츠의 사용률이 높아지므로 보다 효율적입니다.

3-D 장면의 경우 추가 질감이 렌더링 성능 및 이미지 품질을 향상시키기 때문에 메모리에 추가 질감을 저장할 수 있는 경우 Mip 맵을 사용하는 것이 좋습니다.

이러한 변형이 성능을 상당히 개선하면 Mip 맵을 사용하지 않음을 나타내므로 질감 캐시를 최대한 활용하지 않는 것입니다.

## <a name="remarks"></a>설명
원본 질감을 생성하는 `ID3D11Device::CreateTexture2D`를 호출할 때마다 Mip 맵이 강제로 생성됩니다. 특히 다음과 같이 `pDesc`에서 전달되는 D3D11_TEXTURE2D_DESC 개체가 변경되지 않는 셰이더 리소스를 설명하는 경우 Mip 맵이 강제로 생성됩니다.

- BindFlags 멤버에 D3D11_BIND_SHADER_RESOURCE 플래그 집합만 있는 경우

- Usage 멤버가 D3D11_USAGE_DEFAULT 또는 D3D11_USAGE_IMMUTABLE로 설정된 경우

- CPUAccessFlags 멤버가 0으로 설정된 경우(CPU 액세스 없음)

- SampleDesc 멤버에 1로 설정된 Count 멤버가 있는 경우(MSAA(MultiSample Anti-Aliasing) 없음)

- MipLevels 멤버를 1로 설정합니다(기존 Mip 맵 없음).

  애플리케이션에서 초기 데이터를 제공할 때 형식이 BC1, BC2 또는 BC3가 아닌 경우 질감 형식은 D3D11_FORMAT_SUPPORT_MIP_AUTOGEN에 따라 결정된 것처럼 자동 Mip 맵 생성을 지원해야 합니다. 그렇지 않으면 질감이 수정되지 않고 초기 데이터가 제공될 때 Mip 맵이 생성되지 않습니다.

  질감에 대한 Mip 맵이 자동으로 생성된 경우 질감 샘플링 중 Mip 체인을 사용하도록 `ID3D11Device::CreateShaderResourceView`에 대한 호출이 재생 중 수정됩니다.

## <a name="example"></a>예제
**Mip 맵 생성** 변형은 다음과 같은 코드를 사용하여 재현할 수 있습니다.

```cpp
D3D11_TEXTURE2D_DESC texture_description;

// ...

texture_description.MipLevels = 0; // generate a full mipchain

std::vector<D3D11_SUBRESOURCE_DATA> initial_data(num_mips);

for (auto&& mip_level : initial_data)
{
    // fill mip_level with the application-supplied initial data
}

d3d_device->CreateTexture2D(&texture_description, initial_data.data(), &texture)
```

전체 Mip 체인이 있는 질감을 생성하려면 `D3D11_TEXTURE2D_DESC::MipLevels`를 0으로 설정합니다. 전체 Mip 체인에 있는 Mip 맵 수준 수는 floor(log2(n) + 1)이며, 여기서 n은 텍스처의 최대 크기입니다.

`CreateTexture2D`에 초기 데이터를 제공하는 경우 각 Mip 수준에 대한 D3D11_SUBRESOURCE_DATA 개체를 제공해야 합니다.

> [!NOTE]
> Mip 수준 콘텐츠를 자동으로 생성하는 대신 자체 Mip 수준 콘텐츠를 제공하려는 경우 Mip 맵 질감을 지원하는 이미지 편집기를 사용하여 질감을 생성한 다음 파일을 로드하고 Mip 수준을 `CreateTexture2D`에 전달해야 합니다.

## <a name="see-also"></a>참조
[반기/분기 텍스처 차원 변형](half-quarter-texture-dimensions-variant.md)
