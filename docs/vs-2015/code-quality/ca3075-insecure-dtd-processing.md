---
title: 'Ca 3075: 安全ではない DTD の処理 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-devops-test
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 65798d66-7a30-4359-b064-61a8660c1eed
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 7c8a7fefe3b39c68040101e73ec678d92a81a875
ms.sourcegitcommit: 99d097d82ee4f9eff6f588e5ebb6b17d8f724b04
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/24/2018
ms.locfileid: "47589215"
---
# <a name="ca3075-insecure-dtd-processing"></a>CA3075: 安全ではない DTD の処理
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

このトピックの最新バージョンをご覧[ca 3075: 安全ではない DTD 処理](https://docs.microsoft.com/visualstudio/code-quality/ca3075-insecure-dtd-processing)します。

|||
|-|-|
|TypeName|InsecureDTDProcessing|
|CheckId|CA3075|
|カテゴリ|Microsoft.Security|
|互換性に影響する変更点|中断なし|

## <a name="cause"></a>原因
 安全ではない <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> インスタンスを使用する場合、または外部エンティティ ソースを参照する場合、パーサーは信頼されていない入力を受け入れ、攻撃者に機密情報を漏えいしてしまう可能性があります。

## <a name="rule-description"></a>規則の説明
 A[ドキュメント型定義 (DTD)](https://msdn.microsoft.com/library/aa468547.aspx) 、XML パーサーは、ドキュメントの有効性を判別できます 2 つの方法のいずれかで定義されている、 [World Wide Web Consortium (W3C) Extensible Markup Language (XML) 1.0](http://www.w3.org/TR/2008/REC-xml-20081126/)します。 このルールはシーク プロパティとインスタンスの可能性について開発者に警告の信頼されていないデータを受け入れている[情報漏えいが起こる](http://msdn.microsoft.com/library/4064c89f-afa6-444a-aa7e-807ef072131c)、脅威につながる可能性があります[サービス拒否 (DoS)](http://msdn.microsoft.com/library/dfb150f3-d598-4697-a5e6-6779e4f9b600)攻撃です。 このルールは、次の場合にトリガーされます。

-   <xref:System.Xml.XmlReader> を使用して外部 XML エンティティを解決する <xref:System.Xml.XmlUrlResolver>インスタンスで、DtdProcessing が有効になっている。

-   XML で <xref:System.Xml.XmlNode.InnerXml%2A> プロパティが設定されている。

-   <xref:System.Xml.XmlReaderSettings.DtdProcessing%2A> プロパティは、Parse に設定されます。

-   信頼されていない入力は、 <xref:System.Xml.XmlResolver> の代わりに <xref:System.Xml.XmlSecureResolver> を使用して処理される。

-   XmlReader。<xref:System.Xml.XmlReader.Create%2A> メソッドが呼び出される、安全でないと<xref:System.Xml.XmlReaderSettings>インスタンスまたはすべてのインスタンスがありません。

-   <xref:System.Xml.XmlReader> 安全でない既定の設定または値で作成されます。

 これらはどのケースでも、結果は同じになります。XML を処理するマシンが共有するファイル システム、またはネットワークからのコンテンツが攻撃者にさらされ、DoS の媒介として使用される可能性があります。

## <a name="how-to-fix-violations"></a>違反の修正方法

-   キャッチし、パス情報の漏えいを回避するために適切にすべての XmlTextReader 例外を処理します。

-   使用して、 <xref:System.Xml.XmlSecureResolver> XmlTextReader がアクセスできるリソースを制限します。

-   許可しない、 <xref:System.Xml.XmlReader>を設定して、外部リソースを開く、<xref:System.Xml.XmlResolver>プロパティを **null**します。

-   <xref:System.Data.DataViewManager.DataViewSettingCollectionString%2A> の <xref:System.Data.DataViewManager> プロパティが信頼できるソースから割り当てられていることを確認します。

 .NET 3.5 以前

-   設定によって信頼されていないソースを扱う場合は、DTD 処理を無効にする、 <xref:System.Xml.XmlReaderSettings.ProhibitDtd%2A>プロパティを **true**します。

-   XmlTextReader クラスには、完全信頼の継承確認要求があります。 参照してください [継承確認要求](http://msdn.microsoft.com/en-us/28b9adbb-8f08-4f10-b856-dbf59eb932d9)詳細についてはします。

 .NET 4 以降

-   DtdProcessing プロパティを設定して信頼されていないソースを扱う場合は、DtdProcessing を有効にしないように[Prohibit または Ignore](https://msdn.microsoft.com/library/system.xml.dtdprocessing.aspx)

-   すべての InnerXml ケースで、Load() メソッドが XmlReader インスタンスを取ることを確認します。

> [!NOTE]
>  このルールは、有効な XmlSecureResolver インスタンスについて誤検知を報告することがあります。 2016 年半ばまでにこの問題を解決できるよう取り組んでいます。

## <a name="when-to-suppress-warnings"></a>警告を抑制する状況
 入力が信頼できるソースからのものとわかっているのでない限り、この警告からのルールを抑制しないでください。

## <a name="pseudo-code-examples"></a>疑似コードの例

### <a name="violation"></a>違反

```csharp
using System.IO;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlSchema schema = XmlSchema.Read(tr, null); // warn
            return schema;
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System.IO;
using System.Xml;
using System.Xml.Schema;

class TestClass
{
    public XmlSchema Test
    {
        get
        {
            var src = "";
            TextReader tr = new StreamReader(src);
            XmlTextReader reader = new XmlTextReader(tr) { DtdProcessing = DtdProcessing.Prohibit };
            XmlSchema schema = XmlSchema.Read(reader , null);
            return schema;
        }
    }
}
```

### <a name="violation"></a>違反

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings();
        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);  // warn
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public XmlReaderSettings settings = new XmlReaderSettings()
        {
            DtdProcessing = DtdProcessing.Prohibit
        };

        public void TestMethod(string path)
        {
            var reader = XmlReader.Create(path, settings);
        }
    }
}
```

### <a name="violations"></a>違反

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseSetInnerXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument() { XmlResolver = null };
            doc.InnerXml = xml; // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class DoNotUseLoadXml
    {
        public void TestMethod(string xml)
        {
            XmlDocument doc = new XmlDocument(){ XmlResolver = null };
            doc.LoadXml(xml); // warn
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System.Xml;

public static void TestMethod(string xml)
{
    XmlDocument doc = new XmlDocument() { XmlResolver = null };
    System.IO.StringReader sreader = new System.IO.StringReader(xml);
    XmlTextReader reader = new XmlTextReader(sreader) { DtdProcessing = DtdProcessing.Prohibit };
    doc.Load(reader);
}
```

### <a name="violation"></a>違反

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            serializer.Deserialize(stream); // warn
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System.IO;
using System.Xml;
using System.Xml.Serialization;

namespace TestNamespace
{
    public class UseXmlReaderForDeserialize
    {
        public void TestMethod(Stream stream)
        {
            XmlSerializer serializer = new XmlSerializer(typeof(UseXmlReaderForDeserialize));
            XmlTextReader reader = new XmlTextReader(stream) { DtdProcessing = DtdProcessing.Prohibit } ;
            serializer.Deserialize(reader );
        }
    }
}
```

### <a name="violation"></a>違反

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XPathDocument doc = new XPathDocument(path); // warn
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System.Xml;
using System.Xml.XPath;

namespace TestNamespace
{
    public class UseXmlReaderForXPathDocument
    {
        public void TestMethod(string path)
        {
            XmlTextReader reader = new XmlTextReader(path) { DtdProcessing = DtdProcessing.Prohibit };
            XPathDocument doc = new XPathDocument(reader);
        }
    }
}
```

### <a name="violation"></a>違反

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = new XmlUrlResolver() };
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        public XmlDocument doc = new XmlDocument() { XmlResolver = null }; // or set to a XmlSecureResolver instance
    }
}
```

### <a name="violations"></a>違反

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Parse };
            XmlReader reader = XmlReader.Create(path, settings); // warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    class TestClass
    {
        private static void TestMethod()
        {
            var reader = XmlTextReader.Create(""doc.xml""); //warn
        }
    }
}
```

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            try {
                XmlTextReader reader = new XmlTextReader(path); // warn
            }
            catch { throw ; }
            finally {}
        }
    }
}
```

### <a name="solution"></a>ソリューション

```csharp
using System.Xml;

namespace TestNamespace
{
    public class TestClass
    {
        public void TestMethod(string path)
        {
            XmlReaderSettings settings = new XmlReaderSettings(){ DtdProcessing = DtdProcessing.Prohibit };
            XmlReader reader = XmlReader.Create(path, settings);
        }
    }
}
```



