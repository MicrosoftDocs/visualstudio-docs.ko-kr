---
title: '연습: 자바스크립트를 사용하여 SDK 만들기 | 마이크로 소프트 문서'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: a8c89d5d-5b78-4435-817f-c5f25ca6d715
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f3a3fa110bd6521443521449898474299dd267d6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697496"
---
# <a name="walkthrough-create-an-sdk-using-javascript"></a>연습: 자바스크립트를 사용하여 SDK 만들기
이 연습에서는 자바스크립트를 사용하여 간단한 수학 SDK를 시각적 스튜디오 확장(VSIX)으로 만드는 방법을 설명합니다.  연습은 다음 부분으로 나뉩니다.

- [SimpleMathVSIX 확장 SDK 프로젝트를 만들려면](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSimpleMathVSIX)

- [SDK를 사용하는 샘플 앱을 만들려면](../extensibility/walkthrough-creating-an-sdk-using-javascript.md#createSampleApp)

  JavaScript의 경우 클래스 라이브러리 프로젝트 유형이 없습니다. 이 연습에서는 샘플 *산술.js* 파일이 VSIX 프로젝트에서 직접 만들어집니다. 실제로 VSIX 프로젝트에 넣기 전에 **빈 앱** 템플릿을 사용하여 JavaScript 및 CSS 파일을 Windows 스토어 앱으로 먼저 빌드하고 테스트하는 것이 좋습니다.

## <a name="prerequisites"></a>사전 요구 사항
 이 연습을 수행하려면 Visual Studio SDK를 설치해야 합니다. 자세한 내용은 [Visual Studio SDK](../extensibility/visual-studio-sdk.md)를 참조하십시오.

## <a name="to-create-the-simplemathvsix-extension-sdk-project"></a><a name="createSimpleMathVSIX"></a>SimpleMathVSIX 확장 SDK 프로젝트를 만들려면

1. 메뉴 모음에서**새** > **프로젝트** **파일** > 을 선택합니다.

2. 템플릿 범주 목록에서, **Visual C#** 아래에서 **확장성**을 선택한 후 **VSIX 프로젝트** 템플릿을 선택합니다.

3. **이름** 텍스트 상자에서 `SimpleMathVSIX` **확인** 단추를 지정하고 선택합니다.

4. 시각적 **스튜디오 패키지 마법사가** 나타나면 **시작** 페이지에서 **다음** 단추를 선택한 다음 **7페이지 1에서** **완료** 단추를 선택합니다.

     **매니페스트 디자이너가** 열리더라도 매니페스트 파일을 직접 수정하여 이 연습이 간단하게 유지됩니다.

5. **솔루션 탐색기에서** **source.extension.vsixmanifest** 파일에 대한 바로 가기 메뉴를 연 다음 **코드 보기를**선택합니다. 이 코드를 사용하여 파일의 기존 콘텐츠를 대체합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PackageManifest Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vsx-schema/2011" xmlns:d="http://schemas.microsoft.com/developer/vsx-schema-design/2011">
      <Metadata>
        <Identity Id="SimpleMathVSIX" Version="1.0" Language="en-US" Publisher="myname" />
        <DisplayName>Simple Math</DisplayName>
        <Description>Does basic arithmetic calculations.</Description>
      </Metadata>
      <Installation Scope="Global" AllUsers="true">
        <InstallationTarget Id="Microsoft.ExtensionSDK" TargetPlatformIdentifier="Windows" TargetPlatformVersion="v8.0" SdkName="SimpleMath" SdkVersion="1.0" />
      </Installation>
      <Dependencies>
        <Dependency Id="Microsoft.Framework.NDP" DisplayName="Microsoft .NET Framework" d:Source="Manual" Version="4.5" />
      </Dependencies>
      <Assets>
        <Asset Type="Microsoft.ExtensionSDK" d:Source="File" Path="SDKManifest.xml" />
      </Assets>
    </PackageManifest>
    ```

6. **솔루션 탐색기에서** **SimpleMathVSIX** 프로젝트의 바로 가기 메뉴를 연 다음**새 항목** **추가를** > 선택합니다.

7. **데이터** 범주에서 **XML 파일,** 파일 `SDKManifest.xml`이름 지정을 선택하고 **추가** 단추를 선택합니다.

8. **솔루션 탐색기에서** **SDKManifest.xml** 파일의 바로 가기 메뉴를 연 다음 **XML 편집기에서**파일을 표시하려면 **열기를** 선택합니다.

9. **SDKManifest.xml** 파일에 다음 코드를 추가합니다.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <FileList
      DisplayName="Simple Math"
      MinVSVersion="14.0"
      AppliesTo="JavaScript+WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="https://msdn.microsoft.com/">

      <!-- JS -->
      <File Content="js\arithmetic.js" />
    </FileList>

    ```

10. **솔루션 탐색기에서** **SDKManifest.xml** 파일의 바로 가기 메뉴에서 **속성을**선택합니다.

11. **속성** 창에서 **VSIX에 Include** 속성을 **True로**설정합니다.

12. **솔루션 탐색기에서** **SimpleMathVSIX** 프로젝트의 바로 가기 메뉴에서**새 폴더** **추가를** >  `Redist`선택한 다음 폴더 이름을 지정합니다.

13. Redist 아래에 하위 폴더를 추가하여 이 폴더 구조를 만듭니다.

     *\Redist\공통 구성\중립\SimpleMath\js\\*

14. **\\ \js** 폴더의 바로 가기 메뉴에서**새 항목** **추가를** > 선택합니다.

15. **Visual C# 항목에서** **웹** 범주를 선택한 다음 **JavaScript 파일** 항목을 선택합니다. 파일 `arithmetic.js`이름을 지정한 다음 **추가** 단추를 선택합니다.

16. *산술.js에*다음 코드를 삽입합니다.

    ```csharp
    (function (global) {
        "use strict";
        global.Arithmetic = {
            add: function (firstNumber, secondNumber) {
                return firstNumber + secondNumber;
            },

            subtract: function (firstNumber, secondNumber) {
                return firstNumber - secondNumber;
            },

            multiply: function (firstNumber, secondNumber) {
                return firstNumber * secondNumber;
            },

            divide: function (firstNumber, secondNumber) {
                return firstNumber / secondNumber;
            }
        };
    })(this);

    ```

17. **솔루션 탐색기에서** **산술.js** 파일의 바로 가기 메뉴에서 **속성을**선택합니다. 다음 속성을 변경합니다.

    - **VSIX에 포함** 속성을 **True로**설정합니다.

    - **[복사-출력 디렉터리]** 속성을 **항상 복사하도록**설정합니다.

18. **솔루션 탐색기에서** **SimpleMathVSIX** 프로젝트의 바로 가기 메뉴에서 **빌드를**선택합니다.

19. 빌드가 성공적으로 완료되면 프로젝트의 바로 가기 **메뉴에서 파일 탐색기에서 폴더 열기를**선택합니다. **\bin\디버그로\\**이동하여 `SimpleMathVSIX.vsix` 실행하여 설치합니다.

20. **설치** 버튼을 선택하고 설치를 완료합니다.

21. Visual Studio를 다시 시작합니다.

## <a name="to-create-a-sample-app-that-uses-the-sdk"></a><a name="createSampleApp"></a>SDK를 사용하는 샘플 앱을 만들려면

1. 메뉴 모음에서**새** > **프로젝트** **파일** > 을 선택합니다.

2. **자바 스크립트에서**템플릿 범주 목록에서 **Windows 스토어를**선택한 다음 **빈 앱** 템플릿을 선택합니다.

3. **이름** 상자에서 을 `ArithmeticUI`지정합니다. **확인** 단추를 선택합니다.

4. **솔루션 탐색기에서** **산술 UI** 프로젝트의 바로 가기 메뉴를 연 다음**참조** **추가를** > 선택합니다.

5. **Windows에서** **확장을**선택하고 **단순 수학이** 표시됩니다.

6. 단순 **수학** 확인란을 선택한 다음 **확인** 버튼을 선택합니다.

7. **솔루션 탐색기에서** **참조**아래에서 **단순 수학** 참조가 표시됩니다. 그것을 확장하고 **산술.js를**포함하는 **\js\\ ** 폴더가 있다는 것을 알 수 있습니다. **arithmetic.js를** 열어 소스 코드가 설치되어 있는지 확인할 수 있습니다.

8. 다음 코드를 사용하여 *default.htm의*내용을 대체합니다.

   ```html
   <!DOCTYPE html>
   <html>
   <head>
       <meta charset="utf-8" />
       <title>ArithmeticUI</title>

       <!-- WinJS references -->
       <link href="//Microsoft.WinJS.1.0/css/ui-dark.css" rel="stylesheet" />
       <script src="//Microsoft.WinJS.1.0/js/base.js"></script>
       <script src="//Microsoft.WinJS.1.0/js/ui.js"></script>

       <!-- ArithmeticUI references -->
       <link href="/css/default.css" rel="stylesheet" />
       <script src="/js/default.js"></script>
       <script src="/SimpleMath/js/arithmetic.js"></script>
   </head>
   <body>
       <form>
       <div id="calculator" class="ms-grid">
           <input name="firstNumber" id="firstNumber" type="number" step="any">
           <div id="operators">
               <button class="operator" type="button">+</button>
               <button class="operator" type="button">-</button>
               <button class="operator" type="button">*</button>
               <button class="operator" type="button">/</button>
           </div>
           <input id="secondNumber" type="number">
           <button class="calculate" type="button">=</button>
           <input id="result" type="number" name="result" disabled="" readonly="">
       </div>
       </form>
   </body>
   </html>
   ```

9. 다음 코드를 사용하여 *\js\default.js*의 내용을 대체합니다.

    ```csharp
    (function () {
        "use strict";

        var app = WinJS.Application;
        var operation = null;

        function calculateResult() {
            var firstNumber = parseFloat(document.querySelector("#firstNumber").value),
                secondNumber = parseFloat(document.querySelector("#secondNumber").value),
                result = 0;

            if (isNaN(firstNumber) || isNaN(secondNumber)) {
                result = 0;
            }
            else {
                switch (operation) {
                    case "+":
                        result = Arithmetic.add(firstNumber, secondNumber);
                        break;
                    case "-":
                        result = Arithmetic.subtract(firstNumber, secondNumber);
                        break;
                    case "*":
                        result = Arithmetic.multiply(firstNumber, secondNumber);
                        break;
                    case "/":
                        result = Arithmetic.divide(firstNumber, secondNumber);
                        break;
                    default:
                }
            }
            document.querySelector("#result").value = result.toString();
        }

        app.onactivated = function (args) {
            document.querySelector("#calculator").addEventListener("click", function (event) {
                if (event.target.tagName.toLowerCase() === "button") {
                    switch (event.target.className) {
                        case "operator":
                            operation = event.target.innerText;
                            break;
                        case "calculate":
                            calculateResult();
                            break;
                        default:
                            break;
                    }
                }
            });
        };

        app.start();
    })();
    ```

10. *\css\default.css의* 내용을 이 코드로 바꿉니다.

    ```xml
    form {
        display: -ms-grid;
        -ms-grid-rows: 1fr auto 1fr;
        -ms-grid-columns: 1fr auto 1fr;
        height: 100%;
        width: 100%;
    }

    button, input[type=number] {
        margin-right: 5px;
        -ms-grid-row-align: center;
    }

    #calculator {
        -ms-grid-column: 2;
        -ms-grid-row: 2;
        display: -ms-grid;
        -ms-grid-rows: 1fr;
        -ms-grid-columns: auto min-content auto auto auto;
    }

    .ms-grid input {
        width: 5em;
    }

    #firstNumber {
        -ms-grid-column: 1;
        -ms-grid-row-align: center;
    }

    #operators {
        -ms-grid-column: 2;
        -ms-grid-row-align: center;
    }

        #operators button.operator {
            margin-bottom: 5px;
            height: 40px;
        }

    #secondNumber {
        -ms-grid-column: 3;
    }

    button.calculate {
        -ms-grid-column: 4;
        -ms-grid-row-align: center;
        height: 40px;
    }

    #result {
        -ms-grid-column: 5;
    }

    ```

11. **F5** 키를 선택하여 앱을 빌드하고 실행합니다.

12. 앱 UI에서 두 숫자를 입력하고 작업을 선택한 다음 **=** 단추를 선택합니다. 올바른 결과가 나타납니다.

## <a name="see-also"></a>참조
- [소프트웨어 개발 키트 만들기](../extensibility/creating-a-software-development-kit.md)
