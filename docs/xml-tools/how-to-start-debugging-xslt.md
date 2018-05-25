---
title: '方法 : XSLT のデバッグを開始する'
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 01028cd0c2a838335cdaab2705bf5c9bbcd73b44
ms.sourcegitcommit: 697162f54d3c4e30df702fd0289e447e211e3a85
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
# <a name="how-to-start-debugging-xslt"></a>方法: XSLT のデバッグを開始

XSLT デバッガーを使用すると、XSLT スタイル シートや XSLT アプリケーションをデバッグすることができます。 デバッグの際には、コードのステップ イン、ステップ オーバー、またはステップ アウトを行って、コードを一度に 1 行ずつ実行できます。 コードのステップ実行機能を使用するためのコマンドは、XSLT デバッガーを使用する場合と、他の Visual Studio デバッガーを使用する場合とで変わりません。 デバッグを開始すると、XSLT デバッガーのウィンドウが開き、入力ドキュメントと XSLT 出力が表示されます。

## <a name="xml-editor"></a>XML エディター

デバッガーは、XML エディターから起動できます。 このため、スタイル シートの設計中にデバッグすることができます。

### <a name="to-start-debugging-from-a-style-sheet"></a>スタイル シートからデバッグを開始するには

1. XML エディターでスタイル シートを開きます。

1. 選択**XSL のデバッグ**から、 **XML**メニュー。

### <a name="to-start-debugging-from-an-xml-input-document"></a>XML 入力ドキュメントからデバッグを開始するには

1. XML エディターで XML ドキュメントを開きます。

1. 選択**XSL のデバッグ**から、 **XML**メニュー。

## <a name="xslt-from-other-languages"></a>その他の言語の XSLT

アプリケーションのデバッグ中に XSLT にステップ インすることもできます。 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> 呼び出しで F11 キーを押すと、デバッガーは XSLT コードにステップ インできます。

> [!NOTE]
> <xref:System.Xml.Xsl.XslTransform> クラスから XSLT へのステップ インは、サポートされていません。 デバッグ中の XSLT へのステップ インをサポートしている XSLT プロセッサは、<xref:System.Xml.Xsl.XslCompiledTransform> クラスだけです。

### <a name="to-start-debugging-an-xslt-application"></a>XSLT アプリケーションのデバッグを開始するには

1. <xref:System.Xml.Xsl.XslCompiledTransform> オブジェクトをインスタンス化するときに、コード内で `enableDebug` パラメーターを `true` に設定します。

     この設定によって、コードがコンパイルされるときにデバッグ情報を作成するように XSLT プロセッサに指示します。

1. F11 キーを押して、XSLT コードにステップ インします。

     XSLT スタイル シートが新しいドキュメントのウィンドウに読み込まれ、XSLT デバッガーが起動されます。

     または、ブレーク ポイントをスタイル シートに追加し、アプリケーションを実行することもできます。

### <a name="example"></a>例

C# XSLT プログラムの例を次に示します。 この例は、XSLT のデバッグを有効にする方法を示しています。

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\belowAvg.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="see-also"></a>関連項目

- [チュートリアル: XSLT スタイル シートをデバッグします。](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [デバッガーの基本事項](../debugger/debugger-basics.md)