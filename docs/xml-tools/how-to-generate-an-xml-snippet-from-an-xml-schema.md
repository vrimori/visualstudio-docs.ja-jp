---
title: '方法: XML スキーマから XML スニペットを生成する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 31e1805a38d51315c4f0753f363334d1df37ece6
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53864726"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>方法: XML スキーマから XML スニペットを生成します。

XML エディターは、XML スキーマ定義言語 (XSD) スキーマから XML スニペットを生成する機能を備えています。 たとえば、要素名の横に配置する一方、XML ファイルを作成して、キーを押して**タブ**要素にその要素のスキーマ情報から生成された XML データを格納します。

この機能は、要素に対してのみ使用できます。 次の規則も適用されます。

-   要素にはスキーマ型が関連付けられている必要があります。つまり、関連付けられているスキーマに従って、その要素が有効であることが必要です。 スキーマ型は抽象型でない必要があります。また、型には必要な属性や子要素が含まれていなければなりません。

-   エディター内の現在の要素は、属性がなく、空である必要があります。 たとえば、以下はすべて有効になります。

    -   `<Account`

    -   `<Account>`

    -   `<Account></Account>`

-   要素名のすぐ右側にカーソルが置かれている必要があります。

生成されたスニペットには、必須の属性と要素がすべて含まれています。 `minOccurs` が 1 より大きい場合は、その要素の最小限必要な数のインスタンスが、最大で 100 インスタンスまでスニペットに含まれます。 スキーマで見つかった固定値はすべて、スニペットの固定値になります。 `xsd:any` 要素と `xsd:anyAttribute` 要素は無視され、スニペットの構造は追加作成されません。

既定値が生成され、編集可能な値として示されます。 スキーマで既定値が指定されている場合は、その既定値が使用されます。 ただし、スキーマの既定値が空の文字列である場合、エディターでは次の方法で既定値が生成されます。

-   union 型のいずれかのメンバーによって、スキーマ型に enumeration ファセットが直接または間接的に含まれている場合は、スキーマ オブジェクト モデルで最初に見つかった列挙値が既定値として使用されます。

-   スキーマ型が atomic 型である場合、エディターは atomic 型を取得し、atomic 型名を挿入します。 派生した単純型の場合、基本の単純型が使用されます。 list 型の場合、atomic 型は `itemType` になります。 union 型の場合、atomic 型は最初の `memberType` の atomic 型になります。

## <a name="example"></a>例

 このセクションの手順では、スキーマ生成の XML スニペット機能の XML エディターを使用する方法を示します。

> [!NOTE]
> この手順を開始する前に、スキーマ ファイルをローカル コンピューターに保存してください。

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>新しい XML ファイルを作成し、XML スキーマを関連付ける

1.  **ファイル**メニューで、**新規**、 をクリック**ファイル**します。

2.  選択**XML ファイル**で、**テンプレート**ウィンドウをクリックします**オープン**します。

     エディターに新しいファイルが開きます。 ファイルには既定の XML 宣言 `<?xml version="1.0" encoding="utf-8">` が含まれています。

3.  ドキュメントのプロパティ ウィンドウで、参照 ボタンをクリックします (**.。**) で、**スキーマ**フィールド。

     **XSD スキーマ** ダイアログ ボックスが表示されます。

4.  **[追加]** をクリックします。

     **XSD スキーマを開く** ダイアログ ボックスが表示されます。

5.  スキーマ ファイルを選択し、クリックして**オープン**します。

6.  **[OK]** をクリックします。

     XML スキーマが XML ドキュメントに関連付けられています。

### <a name="to-generate-an-xml-snippet"></a>XML スニペットを生成するには

1.  エディターのペインに「`<`」と入力します。

2.  メンバーの一覧に使用可能な項目が表示されます。

     **!--** コメントを追加します。

     **!DOCTYPE**ドキュメントの種類を追加します。

     **?** 処理命令を追加します。

     **連絡先**ルート要素を追加します。

3.  選択**連絡先**メンバーの一覧とキーを押してから **」と入力**します。

     エディターには開始タグ `<Contact` が追加され、要素名の後にカーソルが置かれます。

4.  キーを押して**タブ**XML データを生成する、`Contact`のスキーマ情報に基づいて、要素。

## <a name="input"></a>入力

 このチュートリアルでは、次のスキーマ ファイルを使用します。

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema elementFormDefault="qualified"
           xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:simpleType name="phoneType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Voice"/>
      <xs:enumeration value="Fax"/>
      <xs:enumeration value="Pager"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Contact">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name">
          <xs:simpleType>
            <xs:restriction base="xs:string"></xs:restriction>
          </xs:simpleType>
        </xs:element>
        <xs:element name="Title"
                    type="xs:string" />
        <xs:element name="Phone"
                    minOccurs="1"
                    maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Number"
                          minOccurs="1">
                <xs:simpleType>
                  <xs:restriction base="xs:string"></xs:restriction>
                </xs:simpleType>
              </xs:element>
              <xs:element name="Type"
                          default="Voice"
                          minOccurs="1"
                          type="phoneType"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### <a name="output"></a>出力

 `Contact` 要素に関連付けられているスキーマ情報に基づいて生成された XML データを次に示します。 としてマークされた項目`bold`の XML スニペットの編集可能なフィールドを指定します。

```xml
<Contact>
  <Name>name</Name>
  <Title>title</Title>
  <Phone>
    <Number>number</Number>
    <Type>Voice</Type>
  </Phone>
</Contact>
```

## <a name="see-also"></a>関連項目

- [XML スニペット](../xml-tools/xml-snippets.md)
- [方法: XML スニペットを使用します。](../xml-tools/how-to-use-xml-snippets.md)