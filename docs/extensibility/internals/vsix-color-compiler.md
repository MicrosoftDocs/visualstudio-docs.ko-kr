---
title: VSIX 색 컴파일러 | Microsoft Docs
description: .pkgdef 파일에 Visual Studio 테마의 색을 숨기는 콘솔 애플리케이션인 Visual Studio 확장 색 컴파일러 도구에 대해 알아봅니다.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 92914703ea4b293ac054c841251b37886bbc1d5a
ms.sourcegitcommit: 3fe04d5b931ae459a802a1b965f84186757cbc08
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/08/2021
ms.locfileid: "111588464"
---
# <a name="vsix-color-compiler"></a>VSIX 색 컴파일러
Visual Studio 확장 색 컴파일러 도구는 기존 Visual Studio 테마의 색을 나타내는 .xml 파일을 가져와서 해당 색을 Visual Studio 사용할 수 있도록 .pkgdef 파일로 숨기는 콘솔 애플리케이션입니다. .xml 파일 간의 차이점을 쉽게 비교할 수 있으므로 이 도구는 소스 제어에서 사용자 지정 색을 관리하는 데 유용합니다. 빌드의 출력이 유효한 .pkgdef 파일이 되도록 빌드 환경에 연결할 수도 있습니다.

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

 \<Theme>요소는 전체 테마를 정의합니다. 테마에는 하나 이상의 요소가 포함되어야 \<Category> 합니다. 테마 요소는 다음과 같이 정의됩니다.

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|**Attribute**|**정의**|
|-|-|
|속성|[필수] 테마의 이름|
|GUID|[필수] 테마의 GUID(GUID 서식과 일치해야 합니다.)|

 Visual Studio 대한 사용자 지정 색을 만들 때 다음 테마에 대해 해당 색을 정의해야 합니다. 특정 테마에 대한 색이 없는 경우 Visual Studio 밝은 테마에서 누락된 색을 로드하려고 시도합니다.

|**테마 이름**|**테마 GUID**|
|-|-|
|밝음|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|어두움|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|파랑|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|고대비|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **범주**

 \<Category>요소는 테마의 색 컬렉션을 정의합니다. 범주 이름은 논리적 그룹링을 제공하며 가능한 한 좁게 정의해야 합니다. 범주에는 하나 이상의 요소가 포함되어야 \<Color> 합니다. 범주 요소는 다음과 같이 정의됩니다.

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|**Attribute**|**정의**|
|-|-|
|속성|[필수] 범주의 이름|
|GUID|[필수] 범주의 GUID(GUID 서식과 일치해야 합니다.)|

 **색상**

 \<Color>요소는 UI의 구성 요소 또는 상태에 대한 색을 정의합니다. 색의 기본 명명 체계는 [UI 유형] [상태]입니다. 중복되는 단어 "color"를 사용하지 마십시오. 색은 요소 형식과 상황 또는 색이 적용될 "상태"를 명확하게 나타내야 합니다. 색은 비어 있지 않아야 하며 및 요소 중 하나 또는 모두를 포함해야 \<Background> \<Foreground> 합니다. 색 요소는 다음과 같이 정의됩니다.

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|**Attribute**|**정의**|
|-|-|
|속성|[필수] 색의 이름입니다.|

 **배경 및/또는 전경**

 \<Background>및 \<Foreground> 요소는 UI 요소의 배경 또는 전경에 대한 색의 값과 형식을 정의합니다. 이러한 요소에는 자식이 없습니다.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|**Attribute**|**정의**|
|-|-|
|Type|[필수] 색의 형식입니다. 다음 중 하나일 수 있습니다.<br /><br /> *CT_INVALID:* 색이 잘못되었거나 설정되지 않았습니다.<br /><br /> *CT_RAW:* 원시 ARGB 값입니다.<br /><br /> *CT_COLORINDEX:* 사용하지 않습니다.<br /><br /> *CT_SYSCOLOR:* SysColor의 Windows 시스템 색입니다.<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX Visual Studio 색입니다.<br /><br /> *CT_AUTOMATIC:* 자동 색입니다.<br /><br /> *CT_TRACK_FOREGROUND:* 사용하지 않습니다.<br /><br /> *CT_TRACK_BACKGROUND:* 사용하지 않습니다.|
|원본|[필수] 16진수로 표현되는 색의 값입니다.|

 __VSCOLORTYPE 열거형에서 지원되는 모든 값은 Type 특성의 스키마에서 지원됩니다. 그러나 CT_RAW 및 CT_SYSCOLOR 사용하는 것이 좋습니다.

 **모두 함께**

 유효한 테마 .xml 파일의 간단한 예입니다.

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

|**스위치 이름**|**참고**|**필수 또는 선택 사항**|
|-|-|-|
|명명되지 않은 파일(.xml 파일)|이 매개 변수는 명명되지 않은 첫 번째 매개 변수이며 변환할 XML 파일의 경로입니다.|필수|
|명명되지 않은 파일(.pkgdef 파일)|두 번째 명명되지 않은 매개 변수이며 생성된 .pkgdef 파일의 출력 경로입니다.<br /><br /> 기본값: \<XML Filename> .pkgdef|선택 사항|
|/noLogo|이 플래그를 설정하면 제품 및 저작권 정보의 인쇄가 중지됩니다.|선택 사항|
|/?|도움말 정보를 출력합니다.|선택 사항|
|/help|도움말 정보를 출력합니다.|선택|

 **예제**

- VsixColorCompiler D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColorCompiler D:\xml\colors.xml /noLogo

## <a name="notes"></a>참고

- 이 도구를 사용하려면 최신 버전의 VC++ 런타임을 설치해야 합니다.

- 단일 파일만 지원됩니다. 폴더 경로를 통한 대량 변환은 지원되지 않습니다.

- 도구는 에서 찾을 수 있습니다. `<VS Install Path>\VSSDK\VisualStudioIntegration\Tools\Bin\`

## <a name="sample-output"></a>샘플 출력
 도구에서 생성된 .pkgdef 파일은 아래 키와 유사합니다.

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
