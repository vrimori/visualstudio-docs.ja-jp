---
title: 'CA3076: 安全ではない XSLT スクリプトの実行'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-code-analysis
ms.topic: reference
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 3a6b495572786bc4934d2972dfdfd27642803d3f
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2018
---
# <a name="ca3076-insecure-xslt-script-execution"></a>CA3076: 安全ではない XSLT スクリプトの実行

|||
|-|-|
|TypeName|InsecureXSLTScriptExecution|
|CheckId|CA3076|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因

.NET アプリケーションで XSLT (Extensible Stylesheet Language Transformation) を安全ではない方法で実行すると、攻撃者に機密情報を漏えいする可能性のある、信頼されていない URI 参照がプロセッサにより解決されるおそれがあります。そのことは、サービス拒否攻撃やクロスサイト攻撃につながります。 詳細については、次を参照してください。 [XSLT セキュリティ Considerations(.NET Guide)](/dotnet/standard/data/xml/xslt-security-considerations)です。

## <a name="rule-description"></a>規則の説明

**XSLT** XML データを変換するための World Wide Web Consortium (W3C) 標準です。 通常 XSLT は、XML データを他の形式 (HTML、固定長のテキスト、コンマ区切りのテキスト、または別の XML 形式など) に変換するために、スタイル シートを書き込むのに使用します。 既定では禁止になっていますが、プロジェクトに応じて有効にもできます。

攻撃にさらされないように、このルールはトリガーされるたびに、XslCompiledTransform です。<xref:System.Xml.Xsl.XslCompiledTransform.Load%2A> インスタンスを安全ではない組み合わせを受け取る<xref:System.Xml.Xsl.XsltSettings>と<xref:System.Xml.XmlResolver>、これにより、悪意のあるスクリプト処理します。

## <a name="how-to-fix-violations"></a>違反の修正方法

- 安全ではない XsltSettings 引数を xsltsettings に置き換えます。<xref:System.Xml.Xsl.XsltSettings.Default%2A> または、インスタンスが無効になり、document 関数とスクリプトの実行します。

- <xref:System.Xml.XmlResolver> 引数を null または <xref:System.Xml.XmlSecureResolver> インスタンスに置き換えます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況

入力が信頼できるソースからのものとわかっているのでない限り、この警告からのルールを抑制しないでください。

## <a name="pseudo-code-examples"></a>疑似コードの例

### <a name="violationmdashuses-xsltsettingstrustedxslt"></a>違反&mdash;XsltSettings.TrustedXslt の使用

```csharp
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

### <a name="solutionmdashuse-xsltsettingsdefault"></a>ソリューション&mdash;XsltSettings.Default の使用

```csharp
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

### <a name="violationmdashdocument-function-and-script-execution-not-disabled"></a>違反&mdash;関数とスクリプトの実行を無効になっていないを文書化

```csharp
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

### <a name="solutionmdashdisable-document-function-and-script-execution"></a>ソリューション&mdash;document 関数とスクリプトの実行を無効にします。

```csharp
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

## <a name="see-also"></a>関連項目

[XSLT のセキュリティに関する考慮事項 (.NET ガイド)](/dotnet/standard/data/xml/xslt-security-considerations)