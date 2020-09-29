---
title: '연습: 꼭짓점 음영으로 인해 누락된 개체 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: e42b54a0-8092-455c-945b-9ecafb129d93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc3bd288044c9fea1da648b64cabc87148b8463a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "90843432"
---
# <a name="walkthrough-missing-objects-due-to-vertex-shading"></a>연습: 꼭짓점 음영으로 인해 누락된 개체
이 연습에서는 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 그래픽 진단 도구를 사용하여 꼭짓점 셰이더 단계 동안 발생하는 오류로 인해 누락된 개체를 조사하는 방법을 보여 줍니다.

 이 연습에서는 다음 작업을 설명합니다.

- **그래픽 이벤트 목록** 을 사용하여 문제의 잠재적인 원인을 찾습니다.

- **그래픽 파이프라인 단계** 창을 사용하여 `DrawIndexed` Direct3D API 호출의 효과를 확인합니다.

- **HLSL 디버거** 를 사용하여 꼭짓점 셰이더를 검사합니다.

- **그래픽 이벤트 호출 스택** 을 사용하여 잘못된 HLSL 상수의 소스를 찾습니다.

## <a name="scenario"></a>시나리오
 꼭지점 셰이더가 잘못되었거나 예기치 않은 방식으로 개체의 꼭지점을 변환할 때 3D 앱 개체 누락의 일반적인 원인 중 하나가 발생합니다. 예를 들어 개체 크기가 너무 작게 축소되거나 변환되어 카메라 정면이 아닌 뒤에 나타날 수 있습니다.

 이 시나리오에서는 테스트를 위해 앱을 실행할 때 배경은 예상대로 렌더링되지만 개체 중 하나가 나타나지 않습니다. 그래픽 진단을 사용하여 앱을 디버그할 수 있도록 그래픽 로그 문제를 포착합니다. 이 문제는 앱에서 다음과 같이 보입니다.

 ![개체를 볼 수 없습니다.](media/gfx_diag_demo_missing_object_shader_problem.png "gfx_diag_demo_missing_object_shader_problem")

## <a name="investigation"></a>조사
 그래픽 진단 도구를 사용하면 그래픽 로그 파일을 로드하여 테스트 중에 캡처한 프레임을 검사할 수 있습니다.

#### <a name="to-examine-a-frame-in-a-graphics-log"></a>그래픽 로그에서 프레임을 검사하려면

1. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에서 누락된 개체를 보여 주는 프레임이 포함된 그래픽 로그를 로드합니다. 새 그래픽 로그 탭이 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]에 나타납니다. 이 탭의 맨 윗부분에 선택한 프레임의 렌더링 대상 출력이 있습니다. 아래쪽에는 캡처된 각 프레임을 미리 보기 이미지로 표시하는 **프레임 목록**이 있습니다.

2. **프레임 목록**에서 개체가 표시되지 않는 것을 보여 주는 프레임을 선택합니다. 선택한 프레임을 반영하도록 렌더링 대상이 업데이트됩니다. 이 시나리오에서 그래픽 로그 탭은 다음과 같습니다.

    ![Visual Studio의 그래픽 로그 문서](media/gfx_diag_demo_missing_object_shader_step_1.png "gfx_diag_demo_missing_object_shader_step_1")

   문제를 보이는 프레임을 선택한 후에 **그래픽 이벤트 목록**을 사용하여 진단을 시작할 수 있습니다. **그래픽 이벤트 목록** 에는 활성 프레임을 렌더링하여 디바이스 상태를 설정하거나, 버퍼를 만들고 업데이트하거나, 프레임에 나타나는 개체를 그리는 등의 작업을 하기 위해 수행한 모든 Direct3D API 호출이 포함됩니다. 많은 유형의 호출은 앱이 예상대로 작동할 때 렌더링 대상에 항상은 아니지만 종종 해당 변경 사항이 생기므로 흥미롭습니다(예: 그리기, 디스패치, 복사 또는 지우기 호출). 그리기 호출은 각각 앱이 렌더링하는 기하 도형을 나타내므로 특히 흥미롭습니다(디스패치 호출도 기하 도형을 렌더링할 수 있음).

   우리는 렌더링 대상에 누락된 개체가 그려지지 않지만(이 경우) 나머지 화면은 예상대로 그려지므로 **그래픽 파이프라인 단계** 도구와 함께 **그래픽 이벤트 목록** 을 사용하여 누락된 개체의 기하 도형에 해당하는 그리기 호출을 판단할 수 있습니다. **그래픽 파이프라인 단계** 창은 렌더링 대상에 대한 효과에 상관없이 각 그리기 호출에 전송된 기하 도형을 보여 줍니다. 그리기 호출을 진행함에 따라, 파이프라인 단계가 각 호출과 관련된 기하 도형을 표시하도록 업데이트되고, 렌더링 대상 출력도 호출이 완료되면 렌더링 대상의 상태를 표시하도록 업데이트됩니다.

#### <a name="to-find-the-draw-call-for-the-missing-geometry"></a>누락된 기하 도형에 대한 그리기 호출을 찾으려면,

1. **그래픽 이벤트 목록** 창을 엽니다. **그래픽 진단** 도구 모음에서 **이벤트 목록**을 선택합니다.

2. **그래픽 파이프라인 단계** 창을 엽니다. **그래픽 진단** 도구 모음에서 **파이프라인 단계**를 선택합니다.

3. **그래픽 이벤트 목록** 창에서 각 그리기 호출을 진행할 때, 누락된 개체에 대한 **그래픽 파이프라인 단계** 창을 봅니다. 더 쉽게 확인하려면 **그래픽 이벤트 목록** 창의 오른쪽 위 모서리에 있는 **검색** 상자에 "그리기"를 입력합니다. 그러면 목록이 필터링되어 제목에 "그리기"가 포함된 이벤트만 나타납니다.

    **그래픽 파이프라인 단계** 창에서 **입력 어셈블러** 단계는 개체가 변환되기 전 개체의 기하 도형을 보여 주며, **꼭지점 셰이더** 단계는 변환된 후의 동일한 개체를 보여 줍니다. 이 시나리오에서는 누락된 개체가 **입력 어셈블러** 단계에서는 표시되지만 **꼭짓점 셰이더** 단계에서는 아무 것도 표시되지 않을 때 해당 개체를 찾았다는 것을 확인했습니다.

   > [!NOTE]
   > 헐 셰이더, 도메인 셰이더 또는 기하 도형 셰이더 단계와 같은 다른 기하 도형 단계에서 개체를 처리하는 경우, 이러한 단계가 문제의 원인이 될 수 있습니다. 일반적으로 문제는 결과가 표시되지 않거나 예기치 않은 방식으로 표시되는 최초의 단계와 관련이 있습니다.

4. 누락된 개체에 해당하는 그리기 호출에 도달하면 중지합니다. 이 시나리오에서 **그래픽 파이프라인 단계** 창은 기하 도형이 GPU에 만들어졌으나(입력 어셈블러 축소판 그림으로 표시) 꼭지점 셰이더 단계 동안에는 문제가 발생하여 렌더링 대상에 나타나지 않는다는 것(꼭지점 셰이더 축소판 그림으로 표시)을 보여 줍니다.

    ![DrawIndexed 이벤트 및 파이프라인에 대한 효과](media/gfx_diag_demo_missing_object_shader_step_2.png "gfx_diag_demo_missing_object_shader_step_2")

   앱이 누락된 개체의 기하 도형에 대한 그리기 호출을 실행했는지 확인하고 꼭지점 셰이더 단계 동안 해당 문제가 발생하는 것을 검색한 후에는 HLSL 디버거를 사용하여 꼭지점 셰이더를 검사하고 개체의 기하 도형에서 발생한 결과를 확인할 수 있습니다. 실행하는 동안 HLSL 디버거를 사용하여 HLSL 변수의 상태를 검사하고, HLSL 코드를 단계별로 진행하고, 문제 진단을 위한 중단점을 설정할 수 있습니다.

#### <a name="to-examine-the-vertex-shader"></a>꼭지점 셰이더를 검사하려면

1. 꼭지점 셰이더 단계의 디버깅을 시작합니다. **그래픽 파이프라인 단계** 창의 **꼭지점 셰이더** 단계 아래에서 **디버깅 시작** 단추를 선택합니다.

2. **입력 어셈블러** 단계가 꼭지점 셰이더에 유용한 데이터를 제공하고 **꼭지점 셰이더** 단계는 출력을 생성하지 않는 것으로 나타나므로 꼭지점 셰이더 출력 구조 `output`을 확인하려고 할 수 있습니다. HLSL 코드를 단계별로 진행하면 `output` 이 수정되는 경우를 좀 더 자세히 검토할 수 있습니다.

3. `output` 이 처음 수정되면 멤버 `worldPos` 가 기록됩니다.

    !["output.worldPos" 값이 적절한 것으로 보임](media/gfx_diag_demo_missing_object_shader_step_4.png "gfx_diag_demo_missing_object_shader_step_4")

    해당 값에 문제가 없어 보이므로 `output`을 수정하는 다음 줄까지 코드를 계속 단계별로 진행합니다.

4. `output` 이 수정되는 다음 번에 멤버 `pos` 가 기록됩니다.

    !["output.pos" 값이 0이 됨](media/gfx_diag_demo_missing_object_shader_step_5.png "gfx_diag_demo_missing_object_shader_step_5")

    이번에는 `pos` 멤버의 값(모두 0)에 문제가 있어 보입니다. 다음으로 `output.pos` 가 어떻게 모두 0 값을 갖게 되었는지 확인하려 합니다.

5. `output.pos` 는 `temp`라는 변수에서 해당 값을 가져옵니다. 이전 줄에서 `temp` 값은 이전 값을 `projection`이라는 상수와 곱한 결과임을 알 수 있습니다. `temp`의 의심스러운 값이 이러한 곱하기의 결과인지 의심하게 됩니다. `projection`에 포인터를 두면 해당 값 역시 모두 0임을 알 수 있습니다.

    ![프로젝션 매트릭스에 잘못된 변형이 포함되어 있음](media/gfx_diag_demo_missing_object_shader_step_6.png "gfx_diag_demo_missing_object_shader_step_6")

    이 시나리오에서는 검사를 진행하면 `temp`의 의심스러운 값이 `projection`에 의한 곱하기의 결과일 가능성이 크고, `projection` 이 투영 행렬을 포함해야 하는 상수이므로 모두 0이면 안 된다는 것을 알게 됩니다.

   앱에 의해 셰이더로 전달된 HLSL 상수 `projection`이 문제의 원인일 가능성이 있다는 것을 확인한 후에는 앱의 소스 코드에서 상수 버퍼가 채워지는 위치를 찾아야 합니다. **그래픽 이벤트 호출 스택** 을 사용하여 이 위치를 찾을 수 있습니다.

#### <a name="to-find-where-the-constant-is-set-in-your-apps-source-code"></a>앱 소스 코드에서 상수가 설정되어 있는 위치를 찾으려면

1. **그래픽 이벤트 호출 스택** 창을 엽니다. **그래픽 진단** 도구 모음에서 **그래픽 이벤트 호출 스택**을 선택합니다.

2. 호출 스택에서 앱의 소스 코드까지 이동합니다. **그래픽 이벤트 호출 스택** 창에서 최상위 호출을 선택하여 상수 버퍼가 채워지는지 확인합니다. 그러지 않으면 채워진 위치를 찾을 때까지 호출 스택 위로 이동합니다. 이 시나리오에서는 `UpdateSubresource` Direct3D API를 사용하여 `MarbleMaze::Render`라는 함수의 호출 스택까지 상수 버퍼가 채워지고 해당 값이 `m_marbleConstantBufferData`라는 상수 버퍼 개체에서 온 값이라는 것을 확인할 수 있습니다.

    ![개체의 상수 버퍼를 설정하는 코드](media/gfx_diag_demo_missing_object_shader_step_7.png "gfx_diag_demo_missing_object_shader_step_7")

   > [!TIP]
   > 앱을 동시에 디버깅하는 경우 이 위치에 중단점을 설정할 수 있으며 다음 프레임이 렌더링될 때 중단됩니다. `m_marbleConstantBufferData` 의 멤버를 검사하여 상수 버퍼가 채워질 때 `projection` 멤버의 값이 모두 0으로 설정되어 있는지 확인할 수 있습니다.

   상수 버퍼가 채워지는 위치를 발견하고 해당 값을 `m_marbleConstantBufferData` 변수에서 가져온 것인지 확인한 후 다음 단계로 `m_marbleConstantBufferData.projection` 멤버가 모두 0으로 설정된 위치를 확인합니다. **모든 참조 찾기** 를 사용하여 `m_marbleConstantBufferData.projection`값을 변경하는 코드를 빠르게 검색할 수 있습니다.

#### <a name="to-find-where-the-projection-member-is-set-in-your-apps-source-code"></a>앱 소스 코드에서 투영 멤버가 설정되는 위치를 찾으려면

1. `m_marbleConstantBufferData.projection`에 대한 참조를 찾습니다. 변수 `m_marbleConstantBufferData`에 대한 바로 가기 메뉴를 열고 **모든 참조 찾기**를 선택합니다.

2. 앱의 소스 코드에서 `projection` 멤버가 수정된 줄의 위치로 이동하려면 **기호 결과 찾기** 창에서 해당 줄을 선택합니다. 프로젝션 멤버를 수정하는 첫 번째 결과가 문제의 원인이 아닐 수 있으므로 앱 소스 코드의 일부 영역을 검사해야 할 수 있습니다.

   `m_marbleConstantBufferData.projection` 이 설정된 위치를 찾은 후에 주변 소스 코드를 검사하여 잘못된 값의 출처를 확인할 수 있습니다. 이 시나리오에서 `m_marbleConstantBufferData.projection` 값은 다음 줄에서 `projection` 코드가 제공하는 값으로 초기화되기 전에 `m_camera->GetProjection(&projection);` 이라는 로컬 변수로 설정되어 있음을 확인했습니다.

   ![구슬 프로젝션이 초기화 전에 설정됨](media/gfx_diag_demo_missing_object_shader_step_9.png "gfx_diag_demo_missing_object_shader_step_9")

   이 문제를 해결하려면 `m_marbleConstantBufferData.projection` 값을 설정하는 코드 줄을 `projection`로컬 변수 값을 초기화하는 줄 다음으로 이동합니다.

   ![수정된 C&#43;&#43; 소스 코드](media/gfx_diag_demo_missing_object_shader_step_10.png "gfx_diag_demo_missing_object_shader_step_10")

   .코드를 수정한 후 다시 빌드하고 앱을 다시 실행하여 렌더링 문제가 해결되었는지 확인할 수 있습니다.

   ![이제 개체가 표시됩니다.](media/gfx_diag_demo_missing_object_shader_resolution.png "gfx_diag_demo_missing_object_shader_resolution")