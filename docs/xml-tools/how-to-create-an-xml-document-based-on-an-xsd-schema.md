---
title: '方法: XSD スキーマに基づいて XML ドキュメントを作成する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 11ec095bd3228eb2291f77bf9fadceb0b74d8a37
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>方法: XSD スキーマに基づいて XML ドキュメントを作成する

**サンプル XML の生成**機能には、XML スキーマ (XSD) ファイルに基づいてサンプルの XML ファイルが生成されます。

 このオプションは、次のようなシナリオで使用できます。

-   スキーマのさまざまな構造の使用法を理解する。

-   スキーマが意図したとおりに機能しているかどうかを確認する。

**サンプル XML の生成**機能は、グローバル要素でのみ使用し、有効な XML スキーマ セットが必要です。

この機能では、通常は有効な XML ドキュメントが生成されます。 ただし、スキーマに次のものが 1 つ以上含まれていると、有効なサンプルが生成されない可能性があります。

-   `xs:key`、`xs:keyref`、および `xs:unique` の ID 制約

-   `xs:pattern` ファセット

-   `xs:QName` 型の列挙

-   `xs:ENTITY` 型、`xs:ENTITIES` 型、および `xs:NOTATION` 型

また、`xs:base64Binary` の内容は、その型のスキーマで列挙が発生する場合にのみ生成されることに注意してください。

## <a name="to-generate-an-xml-instance-document-based-on-the-xsd-file"></a>XSD ファイルに基づいて XML インスタンス ドキュメントを生成するには

1.  手順に従います[する方法: を作成し、XSD スキーマ ファイルを編集](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)です。

2.  [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)を右クリックし、`PurchaseOrder`グローバル要素。 選択**サンプル XML の生成**です。

     このオプションを選択すると、次のサンプル XML コンテンツの PurchaseOrder.xml ファイルが生成され、XML エディターに表示されます。

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <PurchaseOrder OrderDate="1900-01-01" xmlns="http://tempuri.org/PurchaseOrderSchema.xsd">
      <ShipTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </ShipTo>
      <ShipTo country="US">
        <name>name2</name>
        <street>street2</street>
        <city>city2</city>
        <state>state2</state>
        <zip>-79228162514264337593543950335</zip>
      </ShipTo>
      <BillTo country="US">
        <name>name1</name>
        <street>street1</street>
        <city>city1</city>
        <state>state1</state>
        <zip>1</zip>
      </BillTo>
    </PurchaseOrder>
    ```

## <a name="see-also"></a>関連項目

- [XML データの使用](../xml-tools/working-with-xml-data.md)