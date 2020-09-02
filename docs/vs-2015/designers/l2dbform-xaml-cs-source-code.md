---
title: L2DBForm.xaml.cs 소스 코드 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 5a40dad3-6763-4576-b3ad-874df3f2c8d9
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3f783161865092f714955b65e6f2fa4791741cbe
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72664282"
---
# <a name="l2dbformxamlcs-source-code"></a>L2DBForm.xaml.cs Source Code
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

이 항목에는 L2DBForm.xaml.cs 파일의 C# 소스 코드에 대한 내용과 설명이 포함되어 있습니다. 이 파일에 포함된 L2XDBForm partial 클래스는 데이터 멤버와 `OnRemove` 및 `OnAddBook` 단추 클릭 이벤트 처리기라는 세 가지 논리 섹션으로 나뉠 수 있습니다.

## <a name="data-members"></a>데이터 멤버
 두 private 데이터 멤버는 이 클래스를 L2DBForm.xaml에 사용되는 창 리소스와 연결하는 데 사용됩니다.

- 네임스페이스 변수 `myBooks`는 `"http://www.mybooks.com"`으로 초기화됩니다.

- `bookList` 멤버는 다음 줄을 사용하여 생성자에서 L2DBForm.xaml의 CDATA 문자열로 초기화됩니다.

    ```
    bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
    ```

## <a name="onaddbook-event-handler"></a>OnAddBook 이벤트 처리기
 이 메서드에는 다음 세 가지 문이 포함되어 있습니다.

- 첫 번째 조건 문은 입력 유효성 검사에 사용됩니다.

- 두 번째 문은 사용자가 **Add New Book** UI(사용자 인터페이스) 섹션에서 입력한 문자열 값에서 새 <xref:System.Xml.Linq.XElement>를 만듭니다.

- 마지막 문은 새 책 요소를 L2DBForm.xaml의 데이터 공급자에 추가합니다. 이렇게 하면 동적 데이터 바인딩을 통해 이 새 항목으로 UI가 자동으로 업데이트되므로 사용자가 추가로 코드를 제공할 필요가 없습니다.

## <a name="onremove-event-handler"></a>OnRemove 이벤트 처리기
 `OnRemove` 처리기는 두 가지 이유 때문에 `OnAddBook` 처리기보다 복잡합니다. 첫째로, 원시 XML에는 유지된 공백이 포함되어 있기 때문에 일치하는 줄 바꿈도 책 항목과 함께 제거되어야 합니다. 둘째로, 편리함을 위해 원하는 항목에 있던 선택 표시가 목록의 이전 항목으로 다시 설정됩니다.

 그러나 선택된 책 항목을 제거하는 핵심 작업은 다음 두 문으로만 수행됩니다.

- 먼저 목록 상자에서 현재 선택된 항목과 연결된 책 요소가 검색됩니다.

  ```
  XElement selBook = (XElement)lbBooks.SelectedItem;
  ```

- 그런 다음 이 요소가 데이터 공급자에서 삭제됩니다.

  ```
  selBook.Remove();
  ```

  동적 데이터 바인딩을 통해 프로그램의 UI가 자동으로 업데이트됩니다.

## <a name="example"></a>예제

### <a name="description"></a>Description

### <a name="code"></a>코드

```csharp
using System;
using System.Linq;
using System.Collections;
using System.Collections.Generic;
using System.Diagnostics;
using System.Text;
using System.Windows;
using System.Windows.Controls;
using System.Windows.Data;
using System.Windows.Input;
using System.Xml;
using System.Xml.Linq;

namespace LinqToXmlDataBinding {
    /// <summary>
    /// Interaction logic for L2XDBForm.xaml
    /// </summary>

    public partial class L2XDBForm : System.Windows.Window
    {
        XNamespace mybooks = "http://www.mybooks.com";
        XElement bookList;

        public L2XDBForm()
        {
            InitializeComponent();
            bookList = (XElement)((ObjectDataProvider)Resources["LoadedBooks"]).Data;
        }

        void OnRemoveBook(object sender, EventArgs e)
        {
            int index = lbBooks.SelectedIndex;
            if (index < 0) return;

            XElement selBook = (XElement)lbBooks.SelectedItem;
            //Get next node before removing element.
            XNode nextNode = selBook.NextNode;
            selBook.Remove();

            //Remove any matching newline node.
            if (nextNode != null && nextNode.ToString().Trim().Equals(""))
            { nextNode.Remove(); }

            //Set selected item.
            if (lbBooks.Items.Count > 0)
            {  lbBooks.SelectedItem = lbBooks.Items[index > 0 ? index - 1 : 0]; }
        }

        void OnAddBook(object sender, EventArgs e)
        {
            if (String.IsNullOrEmpty(tbAddID.Text) ||
                String.IsNullOrEmpty(tbAddValue.Text))
            {
                MessageBox.Show("Please supply both a Book ID and a Value!", "Entry Error!");
                return;
            }
            XElement newBook = new XElement(
                                mybooks + "book",
                                new XAttribute("id", tbAddID.Text),
                                tbAddValue.Text);
            bookList.Add("  ", newBook, "\r\n");
        }
    }
}

```

### <a name="comments"></a>주석
 이러한 처리기에 연결 된 XAML 소스는 [L2dbform.xaml 소스 코드](../designers/l2dbform-xaml-source-code.md)를 참조 하세요.

## <a name="see-also"></a>관련 항목
 [연습: LinqToXmlDataBinding 예제](../designers/walkthrough-linqtoxmldatabinding-example.md) [l2dbform.xaml 소스 코드](../designers/l2dbform-xaml-source-code.md)
