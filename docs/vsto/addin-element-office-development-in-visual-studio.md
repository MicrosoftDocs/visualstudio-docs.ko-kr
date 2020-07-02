---
title: '&lt;addin &gt; 요소 (Visual Studio에서 Office 개발)'
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: reference
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application manifests [Office development in Visual Studio], <addIn> element
- addin element
- <addin> element
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cf922799301aef67ee70c480dd9e0823382cbd47
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543769"
---
# <a name="ltaddingt-element-office-development-in-visual-studio"></a>&lt;addin &gt; 요소 (Visual Studio에서 Office 개발)
  네임 스페이스의 **addin** 요소에는 `vstav3` Visual Studio를 사용 하 여 개발한 문서 수준 사용자 지정 및 VSTO 추가 기능 Microsoft Office 관련 된 정보가 포함 되어 있습니다.

## <a name="syntax"></a>구문

```xml
<addIn>
  <entryPointsCollection>
    <entryPoints>
      <entryPoint>
      </entryPoint>
    </entryPoints>
  </entryPointsCollection>
  <update></update>
  <postActions>
    <postAction>
      <postActionData>
      </postActionData>
    <postAction>
  </postActions>
  <application>
    <customization>
    </customization>
  </application
</addIn>
```

## <a name="elements-and-attributes"></a>요소 및 특성
 네임 스페이스의 **addin** 요소에는 `vstav3` Office 솔루션 및 Microsoft Office 응용 프로그램에 대 한 정보가 포함 되어 있습니다. 이 요소는 `vstav3=urn:schemas-microsoft-com:vsta.v3`네임스페이스에 있어야 합니다. 자식 요소도 이 네임스페이스에 있어야 합니다.

 `addin` 요소에는 특성이 없습니다.

 `addin` 요소에는 다음 자식 요소가 있습니다.

### <a name="entrypoints"></a>entryPoints
 필수 요소. **진입점** 요소는 [&#60;진입점&#62; 요소 &#40;Visual Studio에서 Office 개발&#41;](../vsto/entrypoints-element-office-development-in-visual-studio.md)에 설명 되어 있습니다.

### <a name="update"></a>업데이트
 필수 요소. **Update** 요소는 [Visual Studio&#41;에서 Office 개발 &#40;&#60;업데이트&#62; 요소 ](../vsto/update-element-office-development-in-visual-studio.md)에 설명 되어 있습니다.

### <a name="postactions"></a>postActions
 선택 사항입니다. **Postactions** 요소는 [Visual Studio&#41;에서 Office 개발 &#40;&#60;postactions&#62; 요소 ](../vsto/postactions-element-office-development-in-visual-studio.md)에 설명 되어 있습니다.

### <a name="application"></a>애플리케이션
 필수 요소. **응용 프로그램** 요소는 [Visual Studio에서 Office 개발&#41;&#40;&#60;응용 프로그램&#62; 요소 ](../vsto/application-element-office-development-in-visual-studio.md)에 설명 되어 있습니다.

## <a name="document-level-customization-example"></a>문서 수준 사용자 지정 예제

### <a name="description"></a>설명
 다음 코드 예제에서는를 사용 하 여 배포 된 문서 수준 Office 솔루션의 **addin** 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.ThisWorkbook">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet1">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet2">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
      <vstav3:entryPoint
        class="ContosoExcelWorkbook.Sheet3">
        <assemblyIdentity
          name="ContosoExcelWorkbook"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
  <vstav3:application>
    <vstov4:customizations
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
      <vstov4:customization>
        <vstov4:document
          solutionId="73e" />
      </vstov4:customization>
    </vstov4:customizations>
  </vstav3:application>
</vstav3:addIn>
```

## <a name="vsto-add-in-example"></a>VSTO 추가 기능 예제

### <a name="description"></a>설명
 다음 코드 예제에서는를 사용 하 여 배포 되는 응용 프로그램 수준 Office 솔루션의 **addin** 요소를 보여 줍니다 [!INCLUDE[ndptecclick](../vsto/includes/ndptecclick-md.md)] . 이 코드 예제는 [Office 솔루션의 응용 프로그램 매니페스트에](../vsto/application-manifests-for-office-solutions.md)제공 된 더 큰 예제의 일부입니다.

### <a name="code"></a>코드

```xml
<vstav3:addIn
  xmlns:vstav3="urn:schemas-microsoft-com:vsta.v3">
  <vstav3:entryPointsCollection>
    <vstav3:entryPoints>
      <vstav3:entryPoint
        class="ContosoOutlookAddIn.ThisAddIn">
        <assemblyIdentity
          name="ContosoOutlookAddIn"
          version="1.0.0.0"
          language="neutral"
          processorArchitecture="msil" />
      </vstav3:entryPoint>
    </vstav3:entryPoints>
  </vstav3:entryPointsCollection>
  <vstav3:update
    enabled="true">
    <vstav3:expiration
      maximumAge="7"
      unit="days" />
  </vstav3:update>
  <vstav3:application>
    <vstov4:customizations
      xmlns:vstov4="urn:schemas-microsoft-com:vsto.v4">
      <vstov4:customization>
        <vstov4:appAddIn
          application="Outlook"
          loadBehavior="3"
          keyName="ContosoOutlookAddIn">
          <vstov4:friendlyName>
            ContosoOutlookAddIn
          </vstov4:friendlyName>
          <vstov4:description>
            ContosoOutlookAddIn - Outlook VSTO Add-in
            created with Visual Studio Tools for Office
          </vstov4:description>
          <vstov4:formRegions>
            <vstov4:formRegion
                name="OutlookAddIn1.FormRegion1">
              <vstov4:messageClass name="IPM.Note" />
              <vstov4:messageClass name="IPM.Contact" />
              <vstov4:messageClass name="IPM.Appointment" />
            </vstov4:formRegion>
          </vstov4:formRegions>
        </vstov4:appAddIn>
      </vstov4:customization>
    </vstov4:customizations>
  </vstav3:application>
</vstav3:addIn>
```

## <a name="see-also"></a>참고 항목

- [Office 솔루션의 응용 프로그램 매니페스트](../vsto/application-manifests-for-office-solutions.md)
- [Office 솔루션에 대 한 배포 매니페스트](../vsto/deployment-manifests-for-office-solutions.md)
- [ClickOnce 응용 프로그램 매니페스트](../deployment/clickonce-application-manifest.md)