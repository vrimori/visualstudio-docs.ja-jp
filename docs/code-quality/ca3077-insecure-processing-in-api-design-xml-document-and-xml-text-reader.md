---
title: 'Ca 3077: API の設計、XML ドキュメントと XML テキスト リーダーで安全でない処理 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-code-analysis
ms.topic: conceptual
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f660ee98462b46e5ac5a8ab23cdf17288c995c87
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
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
 A*ドキュメント型定義 (DTD)*で定義されている 2 つの方法、XML パーサーは、ドキュメントの有効性を確認できますが、 [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)です。 このルールは、信頼されていないデータを受け入れてしまうプロパティとインスタンスを検索し、 [サービス拒否 (DoS)](/dotnet/framework/wcf/feature-details/information-disclosure) 攻撃につながる可能性がある潜在的な [Information Disclosure](/dotnet/framework/wcf/feature-details/denial-of-service) の脅威について開発者に警告します。 このルールは、次の場合にトリガーされます。  
  
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