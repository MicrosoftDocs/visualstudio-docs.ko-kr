---
title: VSIX 색 컴파일러 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5059a15c483f648c2248321c7ba8271a634d0c69
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85536099"
---
# <a name="vsix-color-compiler"></a>VSIX 색 컴파일러
Visual Studio 확장 색 컴파일러 도구는 기존 Visual Studio 테마에 대 한 색을 나타내는 .xml 파일을 사용 하 여 Visual Studio에서 해당 색을 사용할 수 있도록 .pkgdef 파일로 변환 하는 콘솔 응용 프로그램입니다. .Xml 파일 간의 차이점을 쉽게 비교할 수 있기 때문에이 도구는 소스 제어에서 사용자 지정 색을 관리 하는 데 유용 합니다. 빌드 출력이 .pkgdef 파일이 되도록 빌드 환경에 후크 될 수도 있습니다.

 **테마 XML 스키마**

 전체 테마 .xml 파일은 다음과 같습니다.

```xml
<Themes>
      <!—one or Theme elements -->
      <Theme>
        <!-- one or more Category elements -->
        <Category>
          <!-- one or more Color elements -->
          <Color>
            <!-- zero or one Background element -->
            <Background />
            <!-- zero or one Foreground element -->
            <Foreground />
          </Color>
        </Category>
      </Theme>
</Themes>
```

 **테마**

 \<Theme>요소는 전체 테마를 정의 합니다. 테마에는 요소가 하나 이상 포함 되어야 합니다 \<Category> . 테마 요소는 다음과 같이 정의 됩니다.

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**특성**|**정의**|
|-|-|
|Name|하다 테마의 이름입니다.|
|GUID|하다 테마의 GUID (GUID 형식과 일치 해야 함)|

 Visual Studio에 대 한 사용자 지정 색을 만들 때 다음 테마에 대해 해당 색을 정의 해야 합니다. 특정 테마에 대 한 색이 없는 경우 Visual Studio는 밝은 테마에서 누락 된 색을 로드 하려고 시도 합니다.

|**테마 이름**|**테마 GUID**|
|-|-|
|밝음|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|어두움|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|파랑|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|고대비|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **범주**

 \<Category>요소는 테마에 있는 색의 컬렉션을 정의 합니다. 범주 이름은 논리적 그룹화를 제공 하며 가능한 한 좁은 것으로 정의 되어야 합니다. 범주는 하나 이상의 요소를 포함 해야 합니다 \<Color> . Category 요소는 다음과 같이 정의 됩니다.

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**특성**|**정의**|
|-|-|
|Name|하다 범주의 이름입니다.|
|GUID|하다 범주의 GUID (GUID 형식과 일치 해야 함)|

 **색상**

 \<Color>요소는 구성 요소 또는 UI 상태에 대 한 색을 정의 합니다. 색의 기본 이름 지정 체계는 [UI 유형] [상태]입니다. "Color" 라는 단어는 중복 되므로 사용 하지 마십시오. 색은 요소 유형과 색이 적용 되는 상황 또는 "상태"를 명확 하 게 나타내야 합니다. 색은 비워 둘 수 없으며 및 요소 중 하나 또는 둘 다를 포함 해야 \<Background> 합니다 \<Foreground> . Color 요소는 다음과 같이 정의 됩니다.

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**특성**|**정의**|
|-|-|
|Name|하다 색의 이름입니다.|

 **배경 및/또는 전경**

 \<Background>및 \<Foreground> 요소는 UI 요소의 배경색이 나 배경색을 정의 합니다. 이러한 요소에는 자식이 없습니다.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**특성**|**정의**|
|-|-|
|형식|하다 색의 형식입니다. 다음 중 하나일 수 있습니다.<br /><br /> *CT_INVALID:* 색이 잘못 되었거나 설정 되지 않았습니다.<br /><br /> *CT_RAW:* 원시 ARGB 값입니다.<br /><br /> *CT_COLORINDEX:* 사용 하지 마십시오.<br /><br /> *CT_SYSCOLOR:* SysColor의 Windows 시스템 색입니다.<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX의 Visual Studio 색입니다.<br /><br /> *CT_AUTOMATIC:* 자동 색입니다.<br /><br /> *CT_TRACK_FOREGROUND:* 사용 하지 마십시오.<br /><br /> *CT_TRACK_BACKGROUND:* 사용 하지 마십시오.|
|원본|하다 16 진수로 표현 된 색의 값입니다.|

 __VSCOLORTYPE 열거형에서 지원 되는 모든 값은 Type 특성의 스키마에서 지원 됩니다. 그러나 CT_RAW와 CT_SYSCOLOR만 사용 하는 것이 좋습니다.

 **모두 함께**

 다음은 유효한 테마 .xml 파일의 간단한 예입니다.

```xml
<Themes>
  <Theme Name="Light" GUID="{de3dbbcd-f642-433c-8353-8f1df4370aba}">
    <Category Name="MyCategory" GUID="{0A96238B-70CE-4479-9170-EECEAA3FCD58}">
      <Color Name="MyActiveBorder">
        <Background Type="CT_RAW" Source="FFCCCEDB" />
      </Color>
    </Category>
  </Theme>
</Themes>
```

## <a name="how-to-use-the-tool"></a>이 도구를 사용 하는 방법
 **구문**

 VsixColorCompiler \<XML file> \<PkgDef file>\<Optional Args>

 **인수**

|**스위치 이름**|**참고**|**필수 또는 선택**|
|-|-|-|
|명명 되지 않은 (.xml 파일)|이 매개 변수는 첫 번째 명명 되지 않은 매개 변수 이며 변환할 XML 파일의 경로입니다.|필수|
|명명 되지 않은 (.pkgdef 파일)|이는 두 번째 명명 되지 않은 매개 변수 이며 생성 된 .pkgdef 파일의 출력 경로입니다.<br /><br /> 기본값: \<XML Filename> . .pkgdef|선택 사항|
|/noLogo|이 플래그를 설정 하면 제품 및 저작권 정보 인쇄를 중지 합니다.|선택 사항|
|/?|도움말 정보를 인쇄 합니다.|선택 사항|
|/help|도움말 정보를 인쇄 합니다.|선택|

 **예제**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml/noLogo

## <a name="notes"></a>참고

- 이 도구를 사용 하려면 최신 버전의 VC + + 런타임이 설치 되어 있어야 합니다.

- 단일 파일만 지원 됩니다. 폴더 경로를 통한 대량 변환은 지원 되지 않습니다.

## <a name="sample-output"></a>샘플 출력
 도구에서 생성 하는 .pkgdef 파일은 아래와 유사 합니다.

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
