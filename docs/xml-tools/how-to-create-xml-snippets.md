---
title: '方法: XML スニペットを作成する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ad0414974946fefe9ab473d120be10deda4b9471
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "54920683"
---
# <a name="how-to-create-xml-snippets"></a>方法: XML スニペットを作成します。

XML エディターを使用して、新しい XML スニペットを作成することができます。 エディターには、新しい XML スニペットを作成する際の定型スニペットである、"Snippet" という名前の XML スニペットが含まれています。

## <a name="to-create-a-new-xml-snippet"></a>新しい XML スニペットを作成するには

 新しい XML コードを作成するスニペットが新しい XML ファイルを作成し、使用、**スニペットの挿入**機能します。

1.  **ファイル** メニューのをクリックして**新規** をクリックし、**ファイル**します。

2.  クリックして**XML ファイル**順にクリックします**オープン**します。

3.  エディター ウィンドウで右クリックして**スニペットの挿入**します。

4.  選択**スニペット**キーを押して、一覧から**Enter**します。

5.  新しいスニペットに必要な変更を加えます。

6.  **ファイル**メニューの  **XMLFile.xml の保存**します。

     **ファイルに名前を付けて** ダイアログ ボックスが表示されます。

7.  新しいスニペットの名前を入力し、選択**スニペット ファイル**から、**型として保存**ドロップダウン ウィンドウ。

8.  使用して、**で保存**ファイルの場所を変更するドロップダウン リスト、 *My documents \visual Studio 2005\Code \xml\my XML Snippets*フォルダーを押してから**保存**します。

## <a name="snippet-description"></a>スニペットの説明

 このセクションでは、定型スニペットの主な要素について説明します。 XML スニペットで使用されるスキーマ要素の詳細については、次を参照してください。[コード スニペット スキーマ リファレンス](../ide/code-snippets-schema-reference.md)します。

### <a name="snippettype-element"></a>SnippetType 要素

 エディターは、2 つのスニペット型をサポートしています。

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

 `Expansion`型を呼び出すときに、スニペットが表示されるかどうかを決定する、**スニペットの挿入**コマンド。 `SurroundsWith`型を呼び出すときに、スニペットが表示されるかどうかを決定する、 **Surrounds With**コマンド。

### <a name="code-element"></a>コード要素

 `Code` 要素は、スニペットが呼び出されたときに挿入される XML テキストを定義します。

> [!NOTE]
> XML スニペットのテキストは、`<![CDATA[...]]>` セクションで囲む必要があります。


 定型スニペットによって作成される `Code` 要素を次に示します。

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

 この `Code` 要素には 3 つの変数が含まれています。

- $name$ はユーザー定義変数です。 この変数によって、編集可能な値を持つ `name` 要素が作成されます。既定値は "name" です。 ユーザー定義変数は、`Literal` 要素を使用して定義されます。

- $selected$ は定義済みの変数です。 この変数は、スニペットを呼び出す前に XML エディターで選択されたテキストを表します。 この変数の配置によって、選択されたテキストが、選択範囲を囲むコード スニペット内のどこに出現するかが決まります。

- $end$ は定義済みの変数です。 押されたとき**Enter**キャレット (^) の移動先をこの変数にコード スニペット フィールドの編集を終了するには、決定します。

  上記の `Code` 要素によって、次の XML テキストが挿入されます。

```xml
<test>
  <name>name</name>
</test>
```

 name 要素の値は、編集可能な領域としてマークされます。

### <a name="literal-element"></a>Literal 要素

 `Literal` 要素は、ファイルへの挿入後にカスタマイズすることができる置換テキストを識別するために使用されます。 たとえば、リテラル文字列、数値、および一部の変数名はリテラルとして宣言できます。 XML スニペット内には任意の数のリテラルを定義することができ、スニペット内では、それらを複数回参照することができます。 既定値が "name" である $name$ 変数を 1 つ定義している `Literal` 要素の例を次に示します。

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

 リテラルは関数を参照することもできます。 XML エディターには、という名前の関数が含まれています。 **LookupPrefix**します。 **LookupPrefix**関数がこのスニペットから呼び出され、存在する場合、その名前空間に定義されている名前空間プレフィックスを返します、コロン (:) が含まれていますにし、XML ドキュメント内の場所からの指定した名前空間 URI を検索その名前。 例を次に、`Literal`を使用する要素、 **LookupPrefix**関数。

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

 この後は、XML スニペット内の任意の場所で $prefix$ 変数を使用できます。

## <a name="see-also"></a>関連項目

- [XML スニペット](../xml-tools/xml-snippets.md)
- [方法: XML スニペットを使用します。](../xml-tools/how-to-use-xml-snippets.md)
- [方法: XML スキーマから XML スニペットを生成します。](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)