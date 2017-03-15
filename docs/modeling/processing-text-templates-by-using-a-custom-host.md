---
title: "カスタム ホストを使用したテキスト テンプレートの処理 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキスト テンプレート, カスタム ディレクティブ ホスト"
  - "テキスト テンプレート, アプリケーションまたは VS 拡張機能"
ms.assetid: affa3296-854d-47d6-9685-285f6d9ba5dc
caps.latest.revision: 33
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 33
---
# カスタム ホストを使用したテキスト テンプレートの処理
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

*テキスト テンプレート変換*プロセスでは、*テキスト テンプレート* ファイルを入力として受け取り、テキスト ファイルを出力として生成します。  テキスト変換エンジンは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 拡張機能か、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がインストールされているコンピューターで実行中のスタンドアロン アプリケーションから呼び出すことができます。  ただし、*テキスト テンプレート ホスト*を提供する必要があります。  このクラスは、テンプレートを環境に接続し、アセンブリやインクルード ファイルなどのリソースの検索と、出力およびエラー メッセージの処理を行います。  
  
> [!TIP]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内で実行されるパッケージまたは拡張機能を作成する場合は、独自のホストを作成するのではなく、テキスト テンプレート サービスを使用することを検討します。  詳細については、「[VS 拡張機能内でのテキスト変換の呼び出し](../modeling/invoking-text-transformation-in-a-vs-extension.md)」を参照してください。  
  
> [!NOTE]
>  サーバー アプリケーションでテキスト テンプレート変換を使用することはお勧めしません。  また、シングル スレッド以外でテキスト テンプレート変換を使用することはお勧めしません。  テキスト テンプレート エンジンでは、単一の AppDomain を再利用して、テンプレートを変換、コンパイル、および実行するためです。  変換されたコードは、スレッド セーフになるように設計されているわけではありません。  デザイン時にはファイルは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトに含まれているので、このエンジンはファイルを連続的に処理するように設計されています。  
>   
>  実行時アプリケーションでは、前処理されたテキスト テンプレートを使用することを検討します。詳細については、「[T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)」を参照してください。  
  
 コンパイル時に決定されるテンプレートのセットをアプリケーションで使用する場合は、前処理されたテキスト テンプレートを使用する方が簡単です。  この方法は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がインストールされていないコンピューターでアプリケーションを実行する場合にも使用できます。  詳細については、「[T4 テキスト テンプレートを使用した実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)」を参照してください。  
  
## アプリケーションでのテキスト テンプレートの実行  
 テキスト テンプレートを実行するには、<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> の ProcessTemplate メソッドを呼び出します。  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 アプリケーションでは、テンプレートを見つけて提供すると共に、出力を処理する必要があります。  
  
 `host` パラメーターでは、<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> を実装するクラスを指定する必要があります。  これはエンジンによってコールバックされます。  
  
 ホストは、エラーのログ記録、アセンブリとインクルード ファイルへの参照の解決、テンプレートを実行できるアプリケーション ドメインの指定、各ディレクティブの適切なプロセッサの呼び出しを実行できる必要があります。  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> は **Microsoft.VisualStudio.TextTemplating.\*.0.dll** で、<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> は **Microsoft.VisualStudio.TextTemplating.Interfaces.\*.0.dll** で定義されています。  
  
## このセクションの内容  
 [チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 テキスト テンプレートの機能を [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部で使用できるようにするカスタム テキスト テンプレート ホストの作成方法を示します。  
  
## 参照  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## 関連項目  
 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)  
 テキスト変換のしくみと、カスタマイズできる部分について説明します。  
  
 [カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 テキスト テンプレート ディレクティブ プロセッサの概要を示します。