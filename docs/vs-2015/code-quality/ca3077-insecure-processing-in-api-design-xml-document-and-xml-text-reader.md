---
title: 'Ca 3077: API の設計、XML ドキュメントと XML テキスト リーダーでの安全でない処理 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 175d655c2283dfe764564d42b6893b12d1f09e22
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47591886"
---
# <a name="ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader"></a>CA3077: API のデザイン、XML ドキュメント、および XML テキスト リーダーでの安全ではない処理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 3077: API の設計、XML ドキュメントと XML テキスト リーダーの処理を安全でない](https://docs.microsoft.com/visualstudio/code-quality/ca3077-insecure-processing-in-api-design-xml-document-and-xml-text-reader)します。

|||
|-|-|
|TypeName|InsecureDTDProcessingInAPIDesign|
|CheckId|CA3077|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 XMLDocument と XMLTextReader から派生する API をデザインする場合、 <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A>にご注意ください。  外部エンティティ ソースを参照または解決したり、XML に安全ではない値を設定したりする場合に、安全ではない DTDProcessing インスタンスを使用すると、情報漏えいにつながる可能性があります。

## <a name="rule-description"></a>規則の説明
 A[ドキュメント型定義 (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) 、XML パーサーは、ドキュメントの有効性を判別できます 2 つの方法のいずれかで定義されている、 [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)します。 このルールはシーク プロパティとインスタンスの可能性について開発者に警告の信頼されていないデータを受け入れている[情報漏えいが起こる](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c)、脅威につながる可能性があります[サービス拒否 (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600)攻撃です。 このルールは、次の場合にトリガーされます。

-   <xref:System.Xml.XmlDocument> または<xref:System.Xml.XmlTextReader>クラスは、DTD の処理の競合回避モジュールの既定値を使用します。

-   XmlDocument または XmlTextReader から派生したクラスにコンストラクターが定義されていない。または <xref:System.Xml.XmlResolver>にセキュリティで保護された値が使用されていない。

## <a name="how-to-fix-violations"></a>違反の修正方法

-   キャッチし、パス情報の漏えいを回避するために適切にすべての XmlTextReader 例外を処理します。

-   使用 <xref:System.Xml.XmlSecureResolver>XmlTextReader がアクセスできるリソースを制限する XmlResolver の代わりにします。

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



