---
title: '方法: XSLT のデバッグの開始 |Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8358335a-fcb0-45e0-a37e-45b43e49ec0a
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b5526ad192966e5866fca5fa98aefd197ff03a09
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/22/2018
ms.locfileid: "47536628"
---
# <a name="how-to-start-debugging-xslt"></a>方法 : XSLT のデバッグを開始する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

XSLT デバッガーを使用すると、XSLT スタイル シートや XSLT アプリケーションをデバッグすることができます。 デバッグの際には、コードのステップ イン、ステップ オーバー、またはステップ アウトを行って、コードを一度に 1 行ずつ実行できます。 コードのステップ実行機能を使用するためのコマンドは、XSLT デバッガーを使用する場合と、他の Visual Studio デバッガーを使用する場合とで変わりません。 デバッグを開始すると、XSLT デバッガーのウィンドウが開き、入力ドキュメントと XSLT 出力が表示されます。  
  
## <a name="xml-editor"></a>XML エディター  
 デバッガーは、XML エディターから起動できます。 このため、スタイル シートの設計中にデバッグすることができます。  
  
#### <a name="to-start-debugging-from-a-style-sheet"></a>スタイル シートからデバッグを開始するには  
  
1.  XML エディターでスタイル シートを開きます。  
  
2.  選択**XSL のデバッグ**から、 **XML**メニュー。  
  
#### <a name="to-start-debugging-from-an-xml-input-document"></a>XML 入力ドキュメントからデバッグを開始するには  
  
1.  XML エディターで XML ドキュメントを開きます。  
  
2.  選択**XSL のデバッグ**から、 **XML**メニュー。  
  
## <a name="xslt-from-other-languages"></a>他の言語の XSLT  
 アプリケーションのデバッグ中に XSLT にステップ インすることもできます。 <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> 呼び出しで F11 キーを押すと、デバッガーは XSLT コードにステップ インできます。  
  
> [!NOTE]
>  <xref:System.Xml.Xsl.XslTransform> クラスから XSLT へのステップ インは、サポートされていません。 デバッグ中の XSLT へのステップ インをサポートしている XSLT プロセッサは、<xref:System.Xml.Xsl.XslCompiledTransform> クラスだけです。  
  
#### <a name="to-start-debugging-an-xslt-application"></a>XSLT アプリケーションのデバッグを開始するには  
  
1.  <xref:System.Xml.Xsl.XslCompiledTransform> オブジェクトをインスタンス化するときに、コード内で `enableDebug` パラメーターを `true` に設定します。  
  
     この設定によって、コードがコンパイルされるときにデバッグ情報を作成するように XSLT プロセッサに指示します。  
  
2.  F11 キーを押して、XSLT コードにステップ インします。  
  
     XSLT スタイル シートが新しいドキュメントのウィンドウに読み込まれ、XSLT デバッガーが起動されます。  
  
     または、ブレーク ポイントをスタイル シートに追加し、アプリケーションを実行することもできます。  
  
### <a name="example"></a>例  
 C# XSLT プログラムの例を次に示します。 この例は、XSLT のデバッグを有効にする方法を示しています。  
  
```  
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
 [チュートリアル: XSLT スタイル シートをデバッグします。](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)   
 [コードのステップ実行の概要](http://msdn.microsoft.com/en-us/8791dac9-64d1-4bb9-b59e-8d59af1833f9)

