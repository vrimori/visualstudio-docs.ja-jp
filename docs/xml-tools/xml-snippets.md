---
title: XML スニペット
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.assetid: 348dbf64-3f09-4fff-b47a-a7ecdf3221cc
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 5572e020dba08c7a417c8a7af40f8d20083198a5
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2019
ms.locfileid: "53928316"
---
# <a name="xml-snippets"></a>XML スニペット

XML エディターと呼ばれる、機能を提供する*XML スニペット*、XML ファイルをより迅速にビルドすることができます。 XML スニペットは、ファイルに挿入することで再利用できます。 XML スキーマ定義言語 (XSD) スキーマに基づいて XML データを生成することもできます。

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

 スニペットは 2 つの方法で挿入できます。 **スニペットの挿入**コマンドは、カーソル位置にある XML スニペットを挿入します。 **ブロックの挿入**コマンドは、選択したテキストの周囲の XML スニペットをラップします。 両方のコマンドが使用可能ないずれかから、 **IntelliSense**サブメニュー、**編集**メニュー、またはエディターのショートカット メニューから。

 詳細については、「[方法 :XML スニペットを使用する](../xml-tools/how-to-use-xml-snippets.md)します。

## <a name="schema-generated-xml-snippets"></a>スキーマから生成される XML スニペット
 XML エディターは、XML スキーマから XML スニペットを生成する機能も備えています。 この機能を使用すると、要素に、その要素のスキーマ情報から生成された XML 要素を格納することができます。

 詳細については、「[方法 :XML スキーマから XML スニペットを生成](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)します。

## <a name="create-new-xml-snippets"></a>新しい XML スニペットを作成します。
 含まれているスニペットに加えて[!INCLUDE[msCoName](../xml-tools/includes/msconame_md.md)]Visual Studio の既定も作成して、独自の XML スニペットを使用することができます。

 詳細については、「[方法 :XML スニペットを作成する](../xml-tools/how-to-create-xml-snippets.md)します。

## <a name="see-also"></a>関連項目

- [XML エディター](../xml-tools/xml-editor.md)