---
title: "CA3076: 安全ではない XSLT スクリプトの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 53cb7a46-c564-488f-bc51-0e210a7853c9
caps.latest.revision: 5
caps.handback.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA3076: 安全ではない XSLT スクリプトの実行
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|InsecureXSLTScriptExecution|  
|CheckId|CA3076|  
|カテゴリ|Microsoft.Security|  
|互換性に影響する変更点|中断なし|  
  
## 原因  
 .NET アプリケーションで [XSLT \(Extensible Stylesheet Language Transformation\)](https://support.microsoft.com/en-us/kb/313997) を安全ではない方法で実行すると、攻撃者に機密情報を漏えいする可能性のある、[信頼されていない URI 参照がプロセッサにより解決される](http://msdn.microsoft.com/ja-jp/ba3e4d4f-1ee7-4226-a51a-78a1f1b5bd8a)おそれがあります。そのことは、サービス拒否攻撃やクロスサイト攻撃につながります。  
  
## 規則の説明  
 [XSLT](http://msdn.microsoft.com/ja-jp/6377ce5f-3c45-42a6-b7a9-ec8da588b60c) は、XML データを変換するための W3C \(World Wide Web Consortium\) 規格です。 通常 XSLT は、XML データを他の形式 \(HTML、固定長のテキスト、コンマ区切りのテキスト、または別の XML 形式など\) に変換するために、スタイル シートを書き込むのに使用します。 既定では禁止になっていますが、プロジェクトに応じて有効にもできます。  
  
 攻撃にさらされないようにするため、悪意あるスクリプトの処理を許してしまうような、<xref:System.Xml.Xsl.XsltSettings> と <xref:System.Xml.XmlResolver> のインスタンスの安全ではない組み合わせを XslCompiledTransform.<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> が受け取った場合には常に、このルールがトリガーされます。  
  
## 違反の修正方法  
  
-   安全ではない XsltSettings 引数を XsltSettings.<xref:System.Xml.Xsl.XsltSettings.Default%2A> と置き換えます。または、document 関数とスクリプトの実行を無効にしたインスタンスに置き換えます。  
  
-   <xref:System.Xml.XmlResolver> 引数を null または <xref:System.Xml.XmlSecureResolver> インスタンスに置き換えます。  
  
## 警告を抑制する状況  
 入力が信頼できるソースからのものとわかっているのでない限り、この警告からのルールを抑制しないでください。  
  
## 疑似コードの例  
  
### 違反  
  
```c#  
using System.Xml;  
using System.Xml.Xsl;  
  
namespace TestNamespace   
{   
    class TestClass   
    {  
         void TestMethod()   
        {    
             XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
             var settings = XsltSettings.TrustedXslt;   
             var resolver = new XmlUrlResolver();   
             xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn   
        }  
    }   
}   
```  
  
### ソリューション  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        void TestMethod()   
        {   
            XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
            var settings = XsltSettings.Default;   
            var resolver = new XmlUrlResolver();   
            xslCompiledTransform.Load("testStylesheet", settings, resolver);   
        }   
    }   
}  
```  
  
### 違反  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod(XsltSettings settings)   
        {   
            try   
            {   
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
                var resolver = new XmlUrlResolver();   
                xslCompiledTransform.Load("testStylesheet", settings, resolver); // warn   
            }   
            catch { throw; }   
            finally { }   
        }   
    }   
}  
```  
  
### ソリューション  
  
```c#  
using System.Xml;   
using System.Xml.Xsl;   
  
namespace TestNamespace   
{   
    class TestClass   
    {   
        private static void TestMethod(XsltSettings settings)   
        {   
            try   
            {   
                XslCompiledTransform xslCompiledTransform = new XslCompiledTransform();   
                settings.EnableDocumentFunction = false;   
                settings.EnableScript = false;   
                var resolver = new XmlUrlResolver();   
                xslCompiledTransform.Load("testStylesheet", settings, resolver);   
            }   
            catch { throw; }   
            finally { }   
        }   
    }   
}  
```