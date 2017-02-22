---
title: "方法: XSD スキーマに基づいて XML ドキュメントを作成する | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 193b195f-e918-4c79-a1a1-8096a1433bde
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 方法: XSD スキーマに基づいて XML ドキュメントを作成する
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**\[サンプル XML の生成\]** 機能では、XML スキーマ \(XSD\) ファイルに基づいてサンプルの XML ファイルが生成されます。  
  
 このオプションは、次のようなシナリオで使用できます。  
  
-   スキーマのさまざまな構造の使用法を理解する。  
  
-   スキーマが意図したとおりに機能しているかどうかを確認する。  
  
 **\[サンプル XML の生成\]** 機能はグローバル要素に対してのみ使用でき、使用するには有効な XML スキーマ セットが必要です。  
  
 この機能では、通常は有効な XML ドキュメントが生成されます。ただし、スキーマに次のものが 1 つ以上含まれていると、有効なサンプルが生成されない可能性があります。  
  
-   `xs:key`、`xs:keyref`、および `xs:unique` の ID 制約  
  
-   `xs:pattern` ファセット  
  
-   `xs:QName` 型の列挙  
  
-   `xs:ENTITY` 型、`xs:ENTITIES` 型、および `xs:NOTATION` 型  
  
 また、`xs:base64Binary` の内容は、その型のスキーマで列挙が発生する場合にのみ生成されることに注意してください。  
  
### XSD ファイルに基づいて XML インスタンス ドキュメントを生成するには  
  
1.  「[方法: XSD スキーマ ファイルを作成して編集する](../xml-tools/how-to-create-and-edit-an-xsd-schema-file.md)」の手順に従います。  
  
2.  [XML スキーマ エクスプローラー](../xml-tools/xml-schema-explorer.md)で、`PurchaseOrder` グローバル要素を右クリックします。**\[サンプル XML の生成\]** をクリックします。  
  
     このオプションを選択すると、次のサンプル XML コンテンツの PurchaseOrder.xml ファイルが生成され、XML エディターに表示されます。  
  
    ```  
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
  
## 参照  
 [XML データの使用](../xml-tools/working-with-xml-data.md)