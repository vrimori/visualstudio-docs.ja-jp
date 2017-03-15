---
title: "CA3077: API のデザイン、XML ドキュメント、および XML テキスト リーダーでの安全ではない処理 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7f33771b-f3c8-4c02-bef6-f581b623c303
caps.latest.revision: 7
caps.handback.revision: 7
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3077: API のデザイン、XML ドキュメント、および XML テキスト リーダーでの安全ではない処理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureDTDProcessingInAPIDesign|  
|CheckId|CA3077|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|中断なし|  
  
## 原因  
 XMLDocument と XMLTextReader から派生する API をデザインする場合、<xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> にご注意ください。  外部エンティティ ソースを参照または解決したり、XML に安全ではない値を設定したりする場合に、安全ではない DTDProcessing インスタンスを使用すると、情報漏えいにつながる可能性があります。  
  
## 規則の説明  
 [文書型定義 \(DTD\)](https://msdn.microsoft.com/en-us/library/aa468547.aspx) は、[World Wide Web コンソーシアム \(W3C\) Extensible Markup Language \(XML\) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)で定義されているように、XML パーサーが文書の妥当性を判別する 2 つの方法のうちの 1 つです。 このルールは、信頼されていないデータを受け入れてしまうプロパティとインスタンスを検索し、[サービス拒否 \(DoS\)](../Topic/Denial%20of%20Service.md) 攻撃につながる可能性がある潜在的な [情報の漏えい](../Topic/Information%20Disclosure.md) の脅威について開発者に警告します。 このルールは、次の場合にトリガーされます。  
  
-   <xref:System.Xml.XmlDocument> クラスまたは <xref:System.Xml.XmlTextReader> クラスがリゾルバーの既定値を DTD の処理に使用している。  
  
-   XmlDocument または XmlTextReader から派生したクラスにコンストラクターが定義されていない。または <xref:System.Xml.XmlResolver> にセキュリティで保護された値が使用されていない。  
  
## 違反の修正方法  
  
-   パス情報の漏えいを防ぐために、XmlTextReader 例外をすべてキャッチし、適切に処理します。  
  
-   XmlResolver の代わりに <xref:System.Xml.XmlSecureResolver> を使用して、XmlTextReader がアクセスできるリソースを制限します。  
  
## 警告を抑制する状況  
 入力が信頼できるソースからのものとわかっているのでない限り、この警告からのルールを抑制しないでください。  
  
## 疑似コードの例  
  
### 違反  
  
```c#  
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
  
### ソリューション  
  
```c#  
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