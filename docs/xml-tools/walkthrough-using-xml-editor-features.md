---
title: 'チュートリアル: XML エディター機能の使用'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: afda2968ece2a18b7abdc2c4c35e4353206cbe42
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693826"
---
# <a name="walkthrough-use-xml-editor-features"></a>チュートリアル: を使用して XML エディターの機能

このチュートリアルの手順では、新しい XML ドキュメントを作成する方法を示します。 ここでは、XML の作成に役立つ XML エディターの機能もいくつか使用します。

> [!NOTE]
> このチュートリアルを開始する前に保存、 *hireDate.xsd*ローカル コンピューターにファイル (このトピックで後述)。

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>新しい XML ファイルを作成し、XML スキーマに関連付ける

1.  **ファイル** メニューのをポイント**新規**、 をクリック**ファイル**です。

2.  選択**XML ファイル**で、**テンプレート**ペインをクリック**開く**です。

     エディターに新しいファイルが開きます。 ファイルには既定の XML 宣言 `<?xml version="1.0" encoding="utf-8">` が含まれています。

3.  ドキュメントのプロパティ ウィンドウで、参照ボタンをクリックします (**.**) で、**スキーマ**フィールドです。

     **XSD スキーマ** ダイアログ ボックスが表示されます。

4.  **[追加]** をクリックします。

     **XSD スキーマを開く** ダイアログ ボックスが表示されます。

5.  選択、 *hireDate.xsd*ファイルし、をクリックして**開く**です。

6.  **[OK]** をクリックします。

     これで XML スキーマが XML ドキュメントと関連付けられます。 この XML スキーマは、ドキュメントの検証に使用されます。 有効な要素のメンバーの一覧を作成する際に、IntelliSense でも使用されます。

## <a name="to-add-data"></a>データを追加するには

1.  エディターのペインに「`<`」と入力します。

     メンバーの一覧に使用可能な項目が表示されます。

    -   **!--** コメントを追加します。

    -   **!DOCTYPE**ドキュメント型を追加します。

    -   **?** 処理命令を追加します。

    -   **従業員**ルート要素を追加します。

2.  選択 **<!--** にコメント ノードとキーを押して追加**Enter**です。

     エディターによってコメントの終了タグが挿入され、コメントの開始タグと終了タグの間にカーソルが置かれます。

3.  入力**Test XML file**です。

4.  新しい行に入力`<`を選択して**従業員**メンバーの一覧からです。

     エディターにより、XML 要素の開始部分として `<employee` が追加されます。 この時点で、要素に属性を追加するか、「`>`」と入力して開始タグを閉じることができます。

5.  「`>`」と入力してタグを閉じます。

6.  エディターによって終了タグが追加されます。 終了タグは、検証エラーを示す波下線付きで追加されます。 **ツールヒント**、メッセージが表示されます:**要素 'employee' に不完全な内容があります。'ID' を期待**です。

7.  型`<`選択**ID**メンバーの一覧からです。 次に、「`>`」と入力します。

     エディターには XML 要素 `<ID></ID>` が追加され、ID 開始タグの後にカーソルが置かれます。

8.  型**abc**です。

     **Abc**テキストに波下線付きです。 **ツールヒント**、メッセージが表示されます: **'ID' 要素がそのデータ型に対して無効な値**です。

9. ID 要素を右クリックし **定義へ移動**です。

     エディターが開きます、 *hireDate.xsd*新しいドキュメント ウィンドウ内のファイルと ID の schema 要素定義にカーソルを位置付けます。

10. XML ファイルに戻るし、置換、 **abc**を含むテキスト**123**です。

     波下線と**ツールヒント**下にある ID 要素の値を消去します。 **ツールヒント**employee 終了タグ今すぐメッセージが表示されます:**要素 'employee' に不完全な内容があります。' Hire date' を期待**です。

11. ID 終了タグの後にカーソルを置き、入力`<`**入社日**を入力し、し、メンバーの一覧から`>`です。

     エディターには XML 要素 `<hire-date></hire-date>` が追加され、hire-date 開始タグの後にカーソルが置かれます。

12. 入力**2003-01-10** hire-date の値。

## <a name="to-format-the-xml-document"></a>XML ドキュメントに書式を設定するには

- 選択、**ドキュメントのフォーマット**XML エディターのツールバーからボタンをクリックします。

    XML ドキュメントの書式が再設定されます。

## <a name="to-save-the-xml-document"></a>XML ドキュメントを保存するには

1.  **ファイル**メニューの **名前を付けて保存**です。

     **ファイルに名前を付けて** ダイアログ ボックスが表示されます。 既定のファイル名は *"XMLFile1"* です。

2.  XML ドキュメントの場所とファイル名を入力し、クリックして**保存**です。

## <a name="hiredatexsd-file"></a>hireDate.xsd ファイル
 このチュートリアルでは、次のスキーマ ファイルを使用します。

```xml
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>関連項目

- [XML エディター](../xml-tools/xml-editor.md)