---
title: '方法: XSD スキーマに基づいて XML ドキュメントを作成する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c2425febfe13aef2797c78251f53a244445be175
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2019
ms.locfileid: "55026048"
---
# <a name="how-to-create-an-xml-document-based-on-an-xsd-schema"></a>方法: XSD スキーマに基づいて XML ドキュメントを作成します。

**サンプル XML の生成**機能には、XML スキーマ (XSD) ファイルに基づくサンプル XML ファイルが生成されます。

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

1.  次の手順では、[方法。作成し、XSD スキーマ ファイルを編集する](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)します。

2.  [XML スキーマ エクスプ ローラー](../xml-tools/xml-schema-explorer.md)を右クリックし、`PurchaseOrder`グローバル要素。 選択**サンプル XML の生成**します。

     このオプションは、PurchaseOrder を選択するとします。*xml*次のサンプル XML コンテンツを含むファイルが生成され、XML エディターで開きます。

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