---
title: "ツールボックス、[HTML] タブ | Microsoft Docs"
ms.custom: 
ms.date: 06/21/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.toolbox.html
helpviewer_keywords:
- Toolbox, HTML tab
- HTML Designer, setting options
- HTML tab in Toolbox
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: fc52ea4ce28c7fac6f7318eac8e835efc0f11cb1
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2018
---
# <a name="toolbox-html-tab"></a>ツールボックス、[HTML] タブ

ツールボックスの **[HTML]** タブは、Web ページと Web フォームで使用するコンポーネントを提供します。 このタブを表示するには、まず、HTML デザイナーで編集するためのドキュメントを開きます。 **[表示]** メニューで **[ツールボックス]** をクリックし、ツールボックスの **[HTML]** タブをクリックします。

 **[HTML]** タブでツールのインスタンスを作成するには、ドキュメントに追加するツールをダブルクリックするか、またはツールを選択して編集サーフェイスの目的の位置にドラッグします。

## <a name="ui-elements"></a>UI 要素

次のツールは、[HTML] タブで既定で使用できます。

**ポインター**

![ASP.NET モバイル デザイナー HTMLpage ポインター](../../ide/reference/media/vxpointer.gif "vxPointer")

このツールは、任意の [ツールボックス] タブを開いたときに、既定で選択されます。 削除することはできません。 マウス ポインターを使用すると、オブジェクトをデザイン ビュー サーフェイスにドラッグしたり、サイズ変更したり、ページまたはフォーム上で位置を変更することができます。 詳細については、「[ツールボックス](../../ide/reference/toolbox.md)」をご覧ください。

**入力 (ボタン)**

![HTML Web ページ ボタン](../../ide/reference/media/vxbutton.gif "vxButton")

`type="button"` の `input` 要素を挿入します。 表示されるテキストを変更するには、`name` プロパティを編集します。 既定では、`id="Button1"` は最初のボタンに挿入され、`id="Button2"` は 2 番目のボタンという具合に挿入されます。

**入力 (ボタン)** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<input id="Button1" type="button" value="Button" name="Button1">
```

**入力 (リセット)**

![HTMLpageResetButton スクリーンショット](../../ide/reference/media/vxreset.gif "vxReset")

`type="reset"` の `input` 要素を挿入します。 表示されるテキストを変更するには、`name` プロパティを編集します。 既定では、`id="Reset1"` は最初のリセット ボタンに挿入され、`id="Reset2"` は 2 番目のリセット ボタンという具合に挿入されます。

**入力 (リセット)** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<input id="Reset1" type="reset" value="Reset" name="Reset1">
```

**入力 (送信)**

![HTMLpageToolbarSubmitButton スクリーンショット](../../ide/reference/media/vxsubmit.gif "vxSubmit")

`type="submit"` の `input` 要素を挿入します。 表示されるテキストを変更するには、`name` プロパティを編集します。 既定では、`id="Submit1"` は最初の送信ボタンに挿入され、`id="Submit2"` は 2 番目の送信ボタンという具合に挿入されます。

**入力 (送信)** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<input id="Submit1" type="submit" value="Submit" name="Submit1">
```

**入力 (テキスト)**

![HTMLpageToolbarTextField スクリーンショット](../../ide/reference/media/vxtextfield.gif "vxTextfield")

ドキュメントに `type="text"` の `input` 要素を挿入します。 表示される既定のテキストを変更するには、`value` 属性を編集します。 既定では、`id="Text1"` は最初のテキスト フィールドに挿入され、`id="Text2"` は 2 番目のテキスト フィールドという具合に挿入されます。

**入力 (テキスト)** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<input id="Text1" TYPE="text" value="Text Field" name="Text1">
```

> [!IMPORTANT]
>すべてのユーザー入力を検証することをお勧めします。 詳細については、「[Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)」(ASP.NET Web ページ (Razor) サイトにおけるユーザー入力の検証) を参照してください。

**入力 (ファイル)**

![HTML ページ ファイル フィールド](../../ide/reference/media/vxfilefield.gif "vxFilefield")

ドキュメントに `type="file"` の `input` 要素を挿入します。 既定では、`id="File1"` は最初のファイル フィールドに挿入され、`id="File2"` は 2 番目のファイル フィールドという具合に挿入されます。

**入力 (ファイル)** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<input id="File1" type="file" name="File1">
```

> [!IMPORTANT]
> すべてのユーザー入力を検証することをお勧めします。 詳細については、「[Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)」(ASP.NET Web ページ (Razor) サイトにおけるユーザー入力の検証) を参照してください。

**入力 (パスワード)**

![Visual Studio パスワード フィールド](../../ide/reference/media/vxpassword.gif "vxPassword")

`type="password"` の `input` 要素を挿入します。 既定では、`id="Password1"` は最初のパスワード フィールドに挿入され、`id="Password2"` は 2 番目のパスワード フィールドという具合に挿入されます。

**入力 (パスワード)** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<input id="Password1" type="password" name="Password1">
```

> [!IMPORTANT]
> アプリケーションでユーザー名とパスワードを送信する場合、転送を暗号化するため、Secure Sockets Layer (SSL) を使用するように Web サイトを構成する必要があります。 詳細については、「[IIS Operations Guide](http://go.microsoft.com/fwlink/?linkid=47856)」 (IIS 操作ガイド) の「Securing Connections with SSL」 (SSL で接続を保護する) を参照してください。 また、すべてのユーザー入力を検証することをお勧めします。 詳細については、「[Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)」(ASP.NET Web ページ (Razor) サイトにおけるユーザー入力の検証) を参照してください。

**入力 (チェック ボックス)**

![HTML Web ページ ツールボックス チェック ボックス オプション](../../ide/reference/media/vxcheckbox.gif "vxCheckbox")

`type="checkbox"` の `input` 要素を挿入します。 表示されるテキストを変更するには、`name` プロパティを編集します。 既定では、`id="Checkbox1"` は最初のチェック ボックスに挿入され、`id="Checkbox2"` は 2 番目のチェック ボックスという具合に挿入されます。

**入力 (チェック ボックス)** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<input id="Checkbox1" type="checkbox" name="Checkbox1">
```

**入力 (ラジオ)**

![VisualStudioHTMLpageRadioButton スクリーンショット](../../ide/reference/media/vxradio.gif "vxRadio")

`type="radio"` の `input` 要素を挿入します。 表示されるテキストを変更するには、`name` プロパティを編集します。 既定では、`id="Radio1"` は最初のラジオ ボタンに挿入され、`id="Radio2"` は 2 番目のラジオ ボタンという具合に挿入されます。

**入力 (ラジオ)** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<input id="Radio1" type="radio" name="Radio1">
```

**入力 (非表示)**

![HTML ページ非表示項目](../../ide/reference/media/vxhidden.gif "vxhidden")

`type="hidden"` の `input` 要素を挿入します。 既定では、`id="Hidden1"` は最初の非表示フィールドに挿入され、`id="Hidden2"` は 2 番目の非表示フィールドという具合に挿入されます。

**入力 (非表示)** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<input id="Hidden1" type="hidden" name="Hidden1">
```

**テキスト領域**

![HTMLpage ツール バー テキスト領域](../../ide/reference/media/vxtextarea.gif "vxTextarea")

`textarea` 要素を挿入します。 テキスト領域のサイズを変更するか、スクロール バーを使用して表示領域を超える長さのテキストを表示することができます。 表示される既定のテキストを変更するには、`value` 属性を編集します。 既定では、`id="textarea1"` は最初のテキスト領域に挿入され、`id=" textarea 2"` は 2 番目のテキスト領域という具合に挿入されます。

**テキスト領域**をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<textarea id=" textarea 1 name=" textarea 1" rows=2 cols=20></textarea> 
```

> [!IMPORTANT]
> すべてのユーザー入力を検証することをお勧めします。 詳細については、「[Validating User Input in ASP.NET Web Pages (Razor) Sites](/aspnet/web-pages/overview/ui-layouts-and-themes/validating-user-input-in-aspnet-web-pages-sites)」(ASP.NET Web ページ (Razor) サイトにおけるユーザー入力の検証) を参照してください。

**テーブル**

![HTMLpageToolbarTable スクリーンショット](../../ide/reference/media/vxtable.gif "vxTable")

`table` 要素を挿入します。

**テーブル**をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<table cellspacing="1" width="75%" border=1> <tr><td></td></tr></table> 
```

**イメージ**

![HTML ページ イメージ項目](../../ide/reference/media/vximage.gif "vxImage")

`img` 要素を挿入します。 この要素を編集して、要素の `src` と `alt` テキストを指定します。

**イメージ**をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<img alt="" src="">
```

**選択**

![HTML ページ ツールボックス ドロップダウン](../../ide/reference/media/vxdropdown.gif "vxDropdown")

`select` 要素のドロップダウン リスト (`size` 属性なし) を挿入します。 既定では、`id="select1"` は最初のリスト ボックスに挿入され、`id="select2"` は 2 番目のリスト ボックスという具合に挿入されます。

**選択**をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<select id="select1" name="select1"><option selected></option></select>
```

サイズ プロパティの値を増やすことで、複数行の `select` 要素を作成できます。

**水平線**

![HTML ページの水平線項目](../../ide/reference/media/vxhorizontal.gif "vxHorizontal")

`hr` 要素を挿入します。 線の太さを太くするには、`size` 属性を編集します。

**水平線**をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<hr width="100%" size=1>
```

**Div**

![HTML ページ ラベル](../../ide/reference/media/vxlabel.gif "vxLabel")

`ms_positioning="FlowLayout"` 属性を含む `div` 要素を挿入します。 幅と高さを除き、この項目はフロー レイアウト パネルと同じです。 `div` 要素内に含まれるテキストを書式設定するには、`class="stylename"` 属性を開始タグに追加します。

**Div** をデザイン ビュー サーフェイスにドラッグすると、次のように HTML マークアップがドキュメントに挿入されます。

```html
<div ms_positioning="FlowLayout" style="width: 70px; position: relative; height: 15px">Label</div>
```

## <a name="see-also"></a>関連項目

[ツールボックス](../../ide/reference/toolbox.md)
