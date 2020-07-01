---
title: 게임 또는 앱에서 3D 자산 사용
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- VC.Project.ImageContentTask.ContentOutput
- VC.Project.MeshContentTask.ContentOutput
- VC.Project.ImageContentTask.GeneratePremultipliedAlpha
- VC.Project.ImageContentTask.Compress
- VC.Project.ShaderGraphContentTask.ContentOutput
- VC.Project.ImageContentTask.GenerateMips
ms.assetid: ea587909-e434-46a8-abf8-9b3e95a58b4f
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3821262a456f9e3e764555fce5fc883b42d4ae9e
ms.sourcegitcommit: f27084e64c79e6428746a20dda92795df996fb31
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85768659"
---
# <a name="how-to-use-3d-assets-in-your-game-or-app"></a>방법: 게임 또는 앱에서 3D 자산 사용

이 문서에서는 Visual Studio에서 3D 자산을 처리하여 빌드에 포함하는 방법에 대해 설명합니다.

Visual Studio에서 도구를 사용하여 3D 자산을 만들면 그 다음 단계는 만든 자산을 앱에서 사용하는 것입니다. 자산을 사용하려면 DirectX가 인식할 수 있는 형식으로 변환해야 합니다. 자산 변환을 지원하기 위해 Visual Studio에서는 생성할 수 있는 각 종류의 자산에 대해 빌드 사용자 지정을 제공합니다. 빌드에 자산을 포함하려면 빌드 사용자 지정을 사용하도록 프로젝트를 구성하고 프로젝트에 자산을 추가하며 올바른 빌드 사용자 지정을 사용하도록 자산을 구성하기만 하면 됩니다. 그런 다음 앱으로 자산을 로드한 후 다른 모든 DirectX 앱에서 하는 것처럼 DirectX 리소스를 만든 후 채워 자산을 사용할 수 있습니다.

## <a name="configure-your-project"></a>프로젝트 구성

3D 자산을 빌드의 일부로 배포하려면 Visual Studio에서 사용자가 배포하려는 자산의 종류를 알아야 합니다. Visual Studio에서는 이미 여러 일반 파일 형식을 알고 있지만 특정 종류의 앱에서만 3D 자산을 사용하기 때문에 Visual Studio에서는 프로젝트가 이러한 종류의 파일을 빌드할 것이라고 가정하지 않습니다. 각 자산 형식에 대해 제공되는 *빌드 사용자 지정*(Visual Studio에 여러 형식의 파일을 유용한 방식으로 처리하는 방법을 알려주는 파일)을 사용하여 사용자 앱에서 이러한 종류의 자산을 사용한다고 Visual Studio에 알릴 수 있습니다. 이러한 사용자 지정은 프로젝트 단위로 적용되므로 프로젝트에 적절한 사용자 지정을 추가하기만 하면 됩니다.

### <a name="to-add-the-build-customizations-to-your-project"></a>프로젝트에 빌드 사용자 지정을 추가하려면

1. **솔루션 탐색기**에서 프로젝트에 대한 바로 가기 메뉴를 연 다음, **빌드 종속성** > **빌드 사용자 지정**을 차례로 선택합니다.

   **Visual C++ 빌드 사용자 지정 파일** 대화 상자가 표시됩니다.

2. **사용 가능한 빌드 사용자 지정 파일**에서는 다음 테이블에서 설명한 대로 프로젝트에서 사용하려는 자산 형식에 해당하는 확인란을 선택합니다.

    |자산 형식|빌드 사용자 지정 이름|
    |----------------| - |
    |질감 및 이미지|**ImageContentTask(.targets, .props)**|
    |3D 모델|**MeshContentTask(.targets, .props)**|
    |셰이더|**ShaderGraphContentTask(.targets, .props)**|

3. **확인** 단추를 선택합니다.

## <a name="include-assets-in-your-build"></a>빌드에 자산 포함

이제 프로젝트에서는 사용자가 사용하려는 여러 종류의 3D 자산에 대해 알고 있으므로 그 다음으로는 어떤 파일이 3D 파일이고 이러한 파일이 어떤 종류의 자산인지 프로젝트에 알립니다.

### <a name="to-add-an-asset-to-your-build"></a>빌드에 자산을 추가하려면

1. **솔루션 탐색기**의 프로젝트에서 자산의 바로 가기 메뉴를 연 다음 **속성**을 선택합니다.

   자산의 **속성 페이지** 대화 상자가 표시됩니다.

2. **구성** 및 **플랫폼** 속성이 변경 내용을 적용하려는 값으로 설정되어 있는지 확인합니다.

3. **구성 속성** 아래에서 **일반**을 선택한 다음, 속성 표의 **일반** 아래에서 **항목 형식** 속성을 적절한 현재 파이프라인 항목 형식으로 설정합니다. 예를 들어 이미지 또는 질감 파일의 경우 **이미지 콘텐츠 파이프라인**을 선택합니다.

    > [!IMPORTANT]
    > 기본적으로 Visual Studio에서는 Visual Studio에 기본 제공되는 **이미지** 항목 형식을 사용하여 여러 종류의 이미지 파일을 분류한다고 가정합니다. 따라서 이미지 콘텐츠 파이프라인에서 처리하려는 각 이미지의 **항목 형식** 속성을 변경해야 합니다. 3D 모델과 시각적 셰이더 그래픽에 대한 다른 형식의 콘텐츠 파이프라인 원본 파일은 기본적으로 올바른 **항목 형식**으로 설정됩니다.

4. **확인** 단추를 선택합니다.

세 가지 콘텐츠 파이프라인 항목 형식, 연결된 해당 원본 및 출력 파일 형식은 다음과 같습니다.

|항목 종류|원본 파일 형식|출력 파일 형식|
|---------------| - | - |
|**이미지 콘텐츠 파이프라인**|이동식 네트워크 그래픽( *.png*)<br /><br /> JPEG( *.jpg*, *.jpeg*, *.jpe*, *.jfif*)<br /><br /> Direct Draw Surface( *.dds*)<br /><br /> Graphics Interchange Format( *.gif*)<br /><br /> Bitmap( *.bmp*, *.dib*)<br /><br /> Tagged Image File Format( *.tif*, *.tiff*)<br /><br /> Targa( *.tga*)|DirectDraw Surface( *.dds*)|
|**메시 콘텐츠 파이프라인**|AutoDesk FBX 교환 파일( *.fbx*)<br /><br /> Collada DAE 파일( *.dae*)<br /><br /> Wavefront OBJ 파일( *.obj*)|3D 메시 파일( *.cmo*)|
|**셰이더 콘텐츠 파이프라인**|시각적 셰이더 그래프( *.dgsl*)|컴파일된 셰이더 출력( *.cso*)|

## <a name="configure-asset-content-pipeline-properties"></a>자산 콘텐츠 파이프라인 속성 구성

특정 방식으로 빌드할 수 있도록 각 자산 파일의 콘텐츠 파이프라인 속성을 설정할 수 있습니다.

### <a name="to-configure-content-pipeline-properties"></a>콘텐츠 파이프라인 속성을 구성하려면

1. **솔루션 탐색기**의 프로젝트에서 자산 파일의 바로 가기 메뉴를 연 다음 **속성**을 선택합니다.

   자산의 **속성 페이지** 대화 상자가 표시됩니다.

2. **구성** 및 **플랫폼** 속성이 변경 내용을 적용하려는 값으로 설정되어 있는지 확인합니다.

3. **구성 속성** 아래에서 콘텐츠 파이프라인 노드(예: 질감 및 이미지 자산에 대한 **이미지 콘텐츠 파이프라인**)를 선택한 다음, 속성 표에서 속성을 적절한 값으로 설정합니다. 예를 들어 빌드 시간에 질감 자산에 대한 MIP 맵을 생성하려면 **MIP 생성** 속성을 **예**로 설정합니다.

4. **확인** 단추를 선택합니다.

### <a name="image-content-pipeline-configuration"></a>이미지 콘텐츠 파이프라인 구성

이미지 콘텐츠 파이프라인 도구를 사용하여 질감 자산을 빌드하는 경우 다양한 방법으로 질감을 압축하고 빌드 시 MIP 수준을 생성해야 할지 여부를 나타내고 출력 파일의 이름을 변경할 수 있습니다.

|속성|설명|
|--------------|-----------------|
|**압축**|출력 파일에 사용할 압축 형식을 지정합니다.<br /><br /> 사용 가능한 옵션은 다음과 같습니다.<br /><br /> -   **압축 안 함**<br />-   **BC1_UNORM 압축**<br />-   **BC1_UNORM_SRGB 압축**<br />-   **BC2_UNORM 압축**<br />-   **BC2_UNORM_SRGB 압축**<br />-   **BC3_UNORM 압축**<br />-   **BC3_UNORM_SRGB 압축**<br />-   **BC4_UNORM 압축**<br />-   **BC4_SNORM 압축**<br />-   **BC5_UNORM 압축**<br />-   **BC5_SNORM 압축**<br />-   **BC6H_UF16 압축**<br />-   **BC6H_SF16 압축**<br />-   **BC7_UNORM 압축**<br />-   **BC7_UNORM_SRGB 압축**<br /><br /> 다른 버전의 DirectX에서 지원되는 압축 형식에 대한 자세한 내용은 [DXGI 프로그래밍 가이드](/windows/win32/direct3ddxgi/dx-graphics-dxgi-overviews)를 참조하세요.|
|미리 곱한 알파 형식으로 변환|이미지를 출력 파일에서 미리 곱한 알파 형식으로 변환하려면 **예**를 선택하고, 그렇지 않으면 **아니요**를 선택합니다. 출력 파일만 변경되고 원본 이미지는 그대로 남습니다.|
|**MIP 생성**|빌드 시간에 전체 MIP 체인을 생성한 다음 출력 파일에 포함하려면 **예**를 선택하고, 그렇지 않으면 **아니요**를 선택합니다. **아니요**이고 이미 원본 파일에 MIP 맵 체인이 포함되어 있는 경우 출력 파일에 MIP 체인이 있게 됩니다. 그렇지 않으면 출력 파일에 MIP 체인이 없습니다.|
|**콘텐츠 출력**|출력 파일의 이름을 지정합니다. **중요:**  출력 파일의 확장명을 변경하더라도 파일 형식에는 아무런 영향을 미치지 않습니다.|

### <a name="mesh-content-pipeline-configuration"></a>메시 콘텐츠 파이프라인 구성

메시 콘텐츠 파이프라인 도구를 사용하여 메시 자산을 빌드하는 경우 출력 파일의 이름을 변경할 수 있습니다.

|속성|설명|
|--------------|-----------------|
|**콘텐츠 출력**|출력 파일의 이름을 지정합니다. **중요:**  출력 파일의 확장명을 변경하더라도 파일 형식에는 아무런 영향을 미치지 않습니다.|

### <a name="shader-content-pipeline-configuration"></a>셰이더 콘텐츠 파이프라인 구성

셰이더 콘텐츠 파이프라인 도구를 사용하여 셰이더 자산을 빌드하는 경우 출력 파일의 이름을 변경할 수 있습니다.

|속성|설명|
|--------------|-----------------|
|**콘텐츠 출력**|출력 파일의 이름을 지정합니다. **중요:**  출력 파일의 확장명을 변경하더라도 파일 형식에는 아무런 영향을 미치지 않습니다.|

## <a name="load-and-use-3d-assets-at-run-time"></a>런타임 시 3D 자산 로드 및 사용

### <a name="use-textures-and-images"></a>질감 및 이미지 사용

Direct3D에서는 질감 리소스를 만들기 위한 기능을 제공합니다. Direct3D 11에서 D3DX11 유틸리티 라이브러리는 이미지 파일에서 직접 질감 리소스 및 리소스 뷰를 만들 수 있는 추가 기능을 제공합니다. Direct3D 11에서 질감 리소스를 만드는 방법에 대한 자세한 내용은 [질감](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures)을 참조하세요. D3DX11 라이브러리를 사용하여 이미지 파일에서 질감 리소스 또는 리소스 보기를 만드는 방법에 대한 자세한 내용은 [방법: 파일에서 질감 초기화](/windows/win32/direct3d11/overviews-direct3d-11-resources-textures-how-to)를 참조하세요.

### <a name="use-3d-models"></a>3D 모델 사용

Direct3D 11은 3D 모델에서 리소스를 만드는 기능을 제공하지 않습니다. 대신 3D 모델 파일을 읽고 모델에 필요한 3D 모델 및 모든 리소스(예: 질감 또는 셰이더)를 나타내는 꼭짓점 및 인덱스 버퍼를 만드는 코드를 작성해야 합니다.

### <a name="use-shaders"></a>셰이더 사용

Direct3D에서는 셰이더 리소스를 만들어 프로그래밍 가능한 그래픽 파이프라인으로 바인딩하기 위한 기능을 제공합니다. Direct3D에서 셰이더 리소스를 만들고 파이프라인에 바인딩하는 방법에 대한 자세한 내용은 [HLSL 프로그래밍 가이드](/windows/win32/direct3dhlsl/dx-graphics-hlsl-pguide)를 참조하세요.

프로그래밍 가능한 그래픽 파이프라인에서 파이프라인의 각 단계는 파이프라인에서 인식할 수 있는 방식으로 형식이 지정된 결과를 파이프라인의 다음 단계에 지정해야 합니다. 셰이더 디자이너는 픽셀 셰이더만 만들 수 있으므로 셰이더 디자이너에서 수신한 데이터가 예상한 형식인지는 앱에서 확인해야 합니다 프로그래밍 가능한 여러 셰이더 단계(예: 꼭짓점 셰이더, 헐 셰이더, 도메인 셰이더 및 기하 셰이더)는 픽셀 셰이더 이전에 실행되고 기하학적 변환을 수행합니다. 프로그래밍할 수 없는 공간 분할(tessellation) 단계 또한 픽셀 셰이더 이전에 실행됩니다. 이러한 단계 중 어떤 단계가 픽셀 셰이더 바로 이전에 오는지와 상관없이 다음과 같은 형식으로 결과를 제공해야 합니다.

```hlsl
struct PixelShaderInput
{
    float4 pos : SV_POSITION;
    float4 diffuse : COLOR;
    float2 uv : TEXCOORD0;
    float3 worldNorm : TEXCOORD1;
    float3 worldPos : TEXCOORD2;
    float3 toEye : TEXCOORD3;
    float4 tangent : TEXCOORD4;
    float3 normal : TEXCOORD5;
};
```

셰이더에서 사용하는 셰이더 디자이너 노드에 따라 다음 정의에 따른 형식으로 추가 데이터를 제공해야 합니다.

```hlsl
Texture2D Texture1 : register( t0 );
Texture2D Texture2 : register( t1 );
Texture2D Texture3 : register( t2 );
Texture2D Texture4 : register( t3 );
Texture2D Texture5 : register( t4 );
Texture2D Texture6 : register( t5 );
Texture2D Texture7 : register( t6 );
Texture2D Texture8 : register( t7 );

TextureCube CubeTexture1 : register( t8 );
TextureCube CubeTexture2 : register( t9 );
TextureCube CubeTexture3 : register( t10 );
TextureCube CubeTexture4 : register( t11 );
TextureCube CubeTexture5 : register( t12 );
TextureCube CubeTexture6 : register( t13 );
TextureCube CubeTexture7 : register( t14 );
TextureCube CubeTexture8 : register( t15 );

SamplerState TexSampler : register( s0 );

cbuffer MaterialVars : register (b0)
{
    float4 MaterialAmbient;
    float4 MaterialDiffuse;
    float4 MaterialSpecular;
    float4 MaterialEmissive;
    float MaterialSpecularPower;
};

cbuffer LightVars : register (b1)
{
    float4 AmbientLight;
    float4 LightColor[4];
    float4 LightAttenuation[4];
    float3 LightDirection[4];
    float LightSpecularIntensity[4];
    uint IsPointLight[4];
    uint ActiveLights;
}

cbuffer ObjectVars : register(b2)
{
    float4x4 LocalToWorld4x4;
    float4x4 LocalToProjected4x4;
    float4x4 WorldToLocal4x4;
    float4x4 WorldToView4x4;
    float4x4 UVTransform4x4;
    float3 EyePosition;
};

cbuffer MiscVars : register(b3)
{
    float ViewportWidth;
    float ViewportHeight;
    float Time;
};
```

## <a name="related-topics"></a>관련 항목

|제목|설명|
|-----------|-----------------|
|[방법: 밉 맵을 포함하는 질감 내보내기](../designers/how-to-export-a-texture-that-contains-mipmaps.md)|이미지 콘텐츠 파이프라인을 사용하여 미리 계산된 Mip 맵이 포함된 질감을 내보내는 방법에 대해 설명합니다.|
|[방법: 미리 증가된 알파를 사용하는 질감 내보내기](../designers/how-to-export-a-texture-that-has-premultiplied-alpha.md)|이미지 콘텐츠 파이프라인을 사용하여 사전 곱셈된 알파 값이 포함된 질감을 내보내는 방법에 대해 설명합니다.|
|[방법: Direct2D 또는 JavaScript 앱과 함께 사용하기 위해 텍스처 내보내기](../designers/how-to-export-a-texture-for-use-with-direct2d-or-javascipt-apps.md)|이미지 콘텐츠 파이프라인을 사용하여 Direct2D 또는 JavaScript 앱에서 사용할 수 있는 질감을 내보내는 방법에 대해 설명합니다.|
|[게임 및 앱을 위한 3D 자산 작업](../designers/working-with-3-d-assets-for-games-and-apps.md)|Visual Studio에서 질감 및 이미지, 3D 모델 및 셰이더를 비롯한 3D 자산을 만들고 조작할 수 있는 편집 도구에 대해 설명합니다.|
|[방법: 셰이더 내보내기](../designers/how-to-export-a-shader.md)|셰이더 디자이너에서 셰이더를 내보내는 방법을 설명합니다.|
