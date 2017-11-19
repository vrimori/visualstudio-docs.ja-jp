---
title: "方法: XML スキーマから XML スニペットを生成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 1090d1509152aaa507220d3119977bb8e9252876
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2017
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>方法 : XML スキーマから XML スニペットを生成する
XML エディターは、XML スキーマ定義言語 (XSD) スキーマから XML スニペットを生成する機能を備えています。 たとえば、XML ファイルを作成しているときは、要素名の横にカーソルを置いて Tab キーを押すと、その要素のスキーマ情報から生成された XML データを要素に格納することができます。  
  
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
 このセクションでは、スキーマから XML スニペットを生成する XML エディターの機能を使用する手順を示します。  
  
> [!NOTE]
>  この手順を開始する前に、スキーマ ファイルをローカル コンピューターに保存してください。  
  
#### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>新しい XML ファイルを作成して XML スキーマに関連付けるには  
  
1.  **ファイル** メニューのをポイント**新規**、 をクリック**ファイル**です。  
  
2.  選択**XML ファイル**で、**テンプレート**ペインをクリック**開く**です。  
  
     エディターに新しいファイルが開きます。 ファイルには既定の XML 宣言 `<?xml version="1.0" encoding="utf-8">` が含まれています。  
  
3.  ドキュメントのプロパティ ウィンドウで、参照ボタンをクリックします (**.**) で、**スキーマ**フィールドです。  
  
     **XSD スキーマ** ダイアログ ボックスが表示されます。  
  
4.  **[追加]**をクリックします。  
  
     **XSD スキーマを開く** ダイアログ ボックスが表示されます。  
  
5.  スキーマ ファイルを選択し、クリックして**開く**です。  
  
6.  **[OK]** をクリックします。  
  
     これで XML スキーマが XML ドキュメントと関連付けられます。  
  
#### <a name="to-generate-an-xml-snippet"></a>XML スニペットを生成するには  
  
1.  エディターのペインに「`<`」と入力します。  
  
2.  メンバーの一覧に使用可能な項目が表示されます。  
  
     **!--**コメントを追加します。  
  
     **!DOCTYPE**ドキュメント型を追加します。  
  
     **?** 処理命令を追加します。  
  
     **連絡先**ルート要素を追加します。  
  
3.  選択**連絡先**ENTER キーを押して、メンバー リストからです。  
  
     エディターには開始タグ `<Contact` が追加され、要素名の後にカーソルが置かれます。  
  
4.  Tab`Contact` キーを押し、スキーマ情報に基づいて  要素用に XML データを生成します。  
  
### <a name="input"></a>入力  
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
 `Contact` 要素に関連付けられているスキーマ情報に基づいて生成された XML データを次に示します。 項目としてマーク`bold`XML スニペットに編集可能なフィールドを指定します。  
  
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
 [XML スニペット](../xml-tools/xml-snippets.md)   
 [方法 : XML スニペットを使用する](../xml-tools/how-to-use-xml-snippets.md)