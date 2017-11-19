---
title: "XML スニペット |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 4f53c8d55011f52a3ed6ecf6fa4fab77855a9ec3
ms.sourcegitcommit: c0422a3d594ea5ae8fc03f1aee684b04f417522e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2017
---
# <a name="xml-snippets"></a>XML スニペット
XML エディターと呼ばれる、機能を提供する*XML スニペット*、XML ファイルをより速く構築することができます。 XML スニペットは、ファイルに挿入することで再利用できます。 XML スキーマ定義言語 (XSD) スキーマに基づいて XML データを生成することもできます。  
  
## <a name="reusable-xml-snippets"></a>再利用可能な XML スニペット  
 XML エディターには、一般的なタスクを対象としたスニペットが多数含まれています。 これによって、XML ファイルをより簡単に作成できます。 たとえば、XML スキーマを作成している場合、"Complex Type Sequence Element" スニペットと "Simple Type Element" スニペットを使用すると、作成中のファイルに次の XML テキストが挿入されます。 その後で、必要に応じて `name` の値を変更します。  
  
```xml
<xs:element name="name">  
  <xs:complexType>  
    <xs:sequence>  
      <xs:element name="name">  
        <xs:simpleType>  
          <xs:restriction base="xs:string"></xs:restriction>  
        </xs:simpleType>  
      </xs:element>  
    </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 スニペットは 2 つの方法で挿入できます。 **スニペットの挿入**コマンドは、カーソル位置に XML スニペットを挿入します。 **ブロックの挿入**コマンドは、選択したテキストの周囲の XML スニペットをラップします。 両方のコマンドを使用するかから、 **IntelliSense**下にあるサブメニュー、**編集**メニュー、またはエディターのショートカット メニューからです。  
  
 詳細については、次を参照してください。[する方法: XML スニペットを使用して](../xml-tools/how-to-use-xml-snippets.md)です。  
  
## <a name="schema-generated-xml-snippets"></a>スキーマを生成する XML スニペット  
 XML エディターは、XML スキーマから XML スニペットを生成する機能も備えています。 この機能を使用すると、要素に、その要素のスキーマ情報から生成された XML 要素を格納することができます。  
  
 詳細については、次を参照してください。[する方法: XML スニペットを、XML スキーマを生成](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)です。  
  
## <a name="create-new-xml-snippets"></a>新しい XML スニペットを作成する  
 含まれているスニペットに加えて[!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]を作成して、独自の XML スニペットを使用することができますも既定では Visual Studio です。  
  
 詳細については、次を参照してください。[する方法: XML スニペットの作成](../xml-tools/how-to-create-xml-snippets.md)です。  
  
## <a name="see-also"></a>関連項目  
 [XML エディター](../xml-tools/xml-editor.md)