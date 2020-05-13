---
title: VSIX 컬러 컴파일러 | 마이크로 소프트 문서
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 99395da7-ec34-491d-9baa-0590d23283ce
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f414a56bb05a23b6efef19aa7c99292b8a40038a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703898"
---
# <a name="vsix-color-compiler"></a>VSIX 색 컴파일러
Visual Studio 확장 색상 컴파일러 도구는 기존 Visual Studio 테마의 색상을 나타내는 .xml 파일을 가져와 .pkgdef 파일로 덮어 해당 색상을 Visual Studio에서 사용할 수 있도록 하는 콘솔 응용 프로그램입니다. .xml 파일 간의 차이점을 쉽게 비교할 수 있기 때문에 이 도구는 소스 제어에서 사용자 지정 색상을 관리하는 데 유용합니다. 또한 빌드 환경에 연결하여 빌드의 출력이 유효한 .pkgdef 파일이 되도록 할 수도 있습니다.

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

 \<테마> 요소는 전체 테마를 정의합니다. 테마에는 하나 이상의 \<범주> 요소가 포함되어야 합니다. 테마 요소는 다음과 같이 정의됩니다.

```xml
<Theme Name="name" GUID="guid">
      <!-- one or more Category elements -->
</Theme>
```

|||
|-|-|
|**attribute**|**정의**|
|이름|[필수] 테마의 이름|
|GUID|[필수] 테마의 GUID(GUID 서식과 일치해야 있음)|

 Visual Studio용 사용자 지정 색상을 만들 때 다음 테마에 대해 해당 색상을 정의해야 합니다. 특정 테마에 대한 색상이 없는 경우 Visual Studio는 라이트 테마에서 누락된 색상을 로드하려고 시도합니다.

|||
|-|-|
|**테마 이름**|**테마 GUID**|
|라이트|{de3dbbcd-f642-433c-8353-8f1df4370aba}|
|어둡게|{1ded0138-47ce-435e-84ef-9ec1f439b749}|
|파랑|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|
|고대비|{a4d6a176-b948-4b29-8c66-53c97a1ed7d0}|

 **범주**

 \<범주> 요소는 테마의 색상 컬렉션을 정의합니다. 범주 이름은 논리적 그룹을 제공하며 가능한 한 좁게 정의해야 합니다. 범주에는 하나 이상의 \<색상> 요소가 포함되어야 합니다. 범주 요소는 다음과 같이 정의됩니다.

```xml
<Category Name="name" GUID="guid">
      <!-- one or more Color elements -->
 </Category>
```

|||
|-|-|
|**attribute**|**정의**|
|이름|[필수] 범주의 이름|
|GUID|[필수] 범주의 GUID(GUID 서식과 일치해야 있음)|

 **Color**

 \<색상> 요소는 UI의 구성 요소 또는 상태에 대한 색상을 정의합니다. 색상에 대한 기본 명명 구성표는 [UI 형식] [상태]입니다. 중복이기 때문에 "color"라는 단어를 사용하지 마십시오. 색상은 색상이 적용될 요소 유형과 상황 또는 "상태"를 명확하게 나타내야 합니다. 색상은 비어 있지 않아야 하며 \<배경> 및 \<전경> 요소 중 하나 또는 둘 다를 포함해야 합니다. 색상 요소는 다음과 같이 정의됩니다.

```xml
<Color Name="name">
        <Background /> <!-- zero or one Background element -->
        <Foreground /> <!-- zero or one Foreground element -->
 </Color>
```

|||
|-|-|
|**attribute**|**정의**|
|이름|[필수] 칼라의 이름|

 **배경 및/또는 전경**

 \<백그라운드> \<및 전경> 요소는 UI 요소의 배경 또는 전경에 대한 색상 값과 형식을 정의합니다. 이러한 요소에는 자식이 없습니다.

```xml
<Background Type="type" Source="int" />
<Foreground Type="type" Source="int" />
```

|||
|-|-|
|**attribute**|**정의**|
|형식|[필수] 색상의 유형입니다. 다음 중 하나일 수 있습니다.<br /><br /> *CT_INVALID:* 색상이 잘못되었거나 설정되지 않았습니다.<br /><br /> *CT_RAW:* 원시 ARGB 값입니다.<br /><br /> *CT_COLORINDEX:* 사용하지 마십시오.<br /><br /> *CT_SYSCOLOR:* SysColor의 Windows 시스템 색상입니다.<br /><br /> *CT_VSCOLOR:* __VSSYSCOLOREX 비주얼 스튜디오 색상입니다.<br /><br /> *CT_AUTOMATIC:* 자동 색상입니다.<br /><br /> *CT_TRACK_FOREGROUND:* 사용하지 마십시오.<br /><br /> *CT_TRACK_BACKGROUND:* 사용하지 마십시오.|
|원본|[필수] 육각형으로 표시되는 색상 값|

 __VSCOLORTYPE 열거에서 지원하는 모든 값은 Type 특성의 스키마에서 지원됩니다. 그러나 CT_RAW CT_SYSCOLOR 사용하는 것이 좋습니다.

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

 VsixColor컴파일러 \<XML \<파일> PkgDef 파일> \<선택적 아르그>

 **인수**

||||
|-|-|-|
|**이름 전환**|**참고**|**필수 또는 옵션**|
|명명되지 않은(.xml 파일)|이 매개 변수는 이름이 지정되지 않은 첫 번째 매개 변수이며 변환할 XML 파일의 경로입니다.|필수|
|이름 없는(.pkgdef 파일)|이 매개 변수는 이름이 지정되지 않은 두 번째 매개 변수이며 생성된 .pkgdef 파일의 출력 경로입니다.<br /><br /> 기본값: \<XML 파일 이름>.pkgdef|Optional|
|/noLogo|이 플래그를 설정하면 제품 및 저작권 정보가 인쇄되지 않습니다.|Optional|
|/?|도움말 정보를 인쇄합니다.|Optional|
|/help|도움말 정보를 인쇄합니다.|Optional|

 **예**

- VsixColor컴파일러 D:\xml\colors.xml D:\pkgdef\colors.pkgdef

- VsixColor컴파일러 D:\xml\colors.xml /noLogo

## <a name="notes"></a>메모

- 이 도구에는 최신 버전의 VC++ 런타임을 설치해야 합니다.

- 단일 파일만 지원됩니다. 폴더 경로를 통한 대량 변환은 지원되지 않습니다.

## <a name="sample-output"></a>샘플 출력
 도구에서 생성된 .pkgdef 파일은 아래 키와 유사합니다.

```
[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\Environment]
"Data"=hex:3a,00,00,00,0b,00,00,00,01,00,00,00,c3,d9,4e,62,fd,bd,fa,41,96,c3,7c,82,4e,a3,2e,3d,01,00,00,00,0c,00,00,00,41,63,74,69,76,65,42,6f,72,64,65,72,01,cc,ce,db,ff,01,33,31,24,ff

[$RootKey$\Themes\{de3dbbcd-f642-433c-8353-8f1df4370aba}\TreeView]
"Data"=hex:38,00,00,00,0b,00,00,00,01,00,00,00,8e,f0,ec,92,13,8b,f4,4c,99,e9,ae,26,92,38,21,85,01,00,00,00,0a,00,00,00,42,61,63,6b,67,72,6f,75,6e,64,01,f5,f5,f5,ff,01,1e,1e,1e,ff
```
