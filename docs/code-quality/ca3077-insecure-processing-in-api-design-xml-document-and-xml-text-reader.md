---
title: 'CA3077: API のデザイン、XML ドキュメント、および XML テキスト リーダーでの安全ではない処理'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 21c7d4fcf2ec1e16a225879b7feceef2a61a8161
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: API のデザイン、XML ドキュメント、および XML テキスト リーダーでの安全ではない処理
|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 XMLDocument と XMLTextReader から派生する API をデザインする場合、 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>にご注意ください。  外部エンティティ ソースを参照または解決したり、XML に安全ではない値を設定したりする場合に、安全ではない DTDProcessing インスタンスを使用すると、情報漏えいにつながる可能性があります。

## <a name="rule-description"></a>規則の説明
 A*ドキュメント型定義 (DTD)* で定義されている 2 つの方法、XML パーサーは、ドキュメントの有効性を確認できますが、 [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)です。 このルールは、信頼されていないデータを受け入れてしまうプロパティとインスタンスを検索し、 [サービス拒否 (DoS)](/dotnet/framework/wcf/feature-details/information-disclosure) 攻撃につながる可能性がある潜在的な [Information Disclosure](/dotnet/framework/wcf/feature-details/denial-of-service) の脅威について開発者に警告します。 このルールは、次の場合にトリガーされます。

-   <xref:System.Xml.XmlDocument> または<xref:System.Xml.XmlTextReader>クラスは、DTD の処理のリゾルバーの既定値を使用します。

-   XmlDocument または XmlTextReader から派生したクラスにコンストラクターが定義されていない。または <xref:System.Xml.XmlResolver>にセキュリティで保護された値が使用されていない。

## <a name="how-to-fix-violations"></a>違反の修正方法

-   キャッチし、パス情報の漏えいを回避するには、正しく XmlTextReader 例外をすべてを処理します。

-   使用して<xref:System.Xml.XmlSecureResolver>XmlTextReader がアクセスできるリソースを制限する XmlResolver の代わりにします。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 入力が信頼できるソースからのものとわかっているのでない限り、この警告からのルールを抑制しないでください。

## <a name="pseudo-code-examples"></a>疑似コードの例

### <a name="violation"></a>違反

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass () {} // warn
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2() // warn
        {
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System;
using System.Xml;

namespace TestNamespace
{
    class TestClass : XmlDocument
    {
        public TestClass ()
        {
            XmlResolver = null;
        }
    }

    class TestClass2 : XmlTextReader
    {
        public TestClass2()
        {
               XmlResolver = null;
        }
    }
}
```