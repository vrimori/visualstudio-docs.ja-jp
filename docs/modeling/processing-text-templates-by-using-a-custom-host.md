---
title: "カスタム ホストを使用してテキスト テンプレートの処理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, in application or VS extension
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: d3eabfb846b6b488c99202037ebea90c4f9f04db
ms.sourcegitcommit: f89ed5fc2e5078213e30a6ade4604e34df48181f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2018
---
# <a name="processing-text-templates-by-using-a-custom-host"></a>カスタム ホストを使用したテキスト テンプレートの処理
*テキスト テンプレート変換*処理では、*テキスト テンプレート*ファイルとして入力し、テキスト ファイルを出力として生成します。 テキスト変換エンジンは、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 拡張機能か、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がインストールされているコンピューターで実行中のスタンドアロン アプリケーションから呼び出すことができます。 ただし、提供する必要があります、*テキスト テンプレート ホスト*です。 このクラスは、テンプレートを環境に接続し、アセンブリやインクルード ファイルなどのリソースの検索と、出力およびエラー メッセージの処理を行います。  
  
> [!TIP]
>  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 内で実行されるパッケージまたは拡張機能を作成する場合は、独自のホストを作成するのではなく、テキスト テンプレート サービスを使用することを検討します。 詳細については、次を参照してください。 [VS 拡張機能でテキスト変換を呼び出す](../modeling/invoking-text-transformation-in-a-vs-extension.md)です。  
  
> [!NOTE]
>  サーバー アプリケーションでテキスト テンプレート変換を使用することはお勧めしません。 また、シングル スレッド以外でテキスト テンプレート変換を使用することはお勧めしません。 テキスト テンプレート エンジンでは、単一の AppDomain を再利用して、テンプレートを変換、コンパイル、および実行するためです。 変換されたコードは、スレッド セーフになるように設計されているわけではありません。 デザイン時にはファイルは [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] プロジェクトに含まれているので、このエンジンはファイルを連続的に処理するように設計されています。  
>   
>  実行時のアプリケーション、前処理されたテキスト テンプレートの使用を検討してください。 を参照してください[T4 テキスト テンプレートを使用して実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)です。  
  
 コンパイル時に決定されるテンプレートのセットをアプリケーションで使用する場合は、前処理されたテキスト テンプレートを使用する方が簡単です。 この方法は、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] がインストールされていないコンピューターでアプリケーションを実行する場合にも使用できます。 詳細については、次を参照してください。 [T4 テキスト テンプレートを使用して実行時テキスト生成](../modeling/run-time-text-generation-with-t4-text-templates.md)です。  
  
## <a name="executing-a-text-template-in-your-application"></a>アプリケーションでのテキスト テンプレートの実行  
 テキスト テンプレートを実行するには、<xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName> の ProcessTemplate メソッドを呼び出します。  
  
```  
using Microsoft.VisualStudio.TextTemplating;  
...  
Engine engine = new Engine();  
string output = engine.ProcessTemplate(templateString, host);  
```  
  
 アプリケーションでは、テンプレートを見つけて提供すると共に、出力を処理する必要があります。  
  
 `host` パラメーターでは、<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost> を実装するクラスを指定する必要があります。 これはエンジンによってコールバックされます。  
  
 ホストは、エラーのログ記録、アセンブリとインクルード ファイルへの参照の解決、テンプレートを実行できるアプリケーション ドメインの指定、各ディレクティブの適切なプロセッサの呼び出しを実行できる必要があります。  
  
 <xref:Microsoft.VisualStudio.TextTemplating.Engine?displayProperty=fullName>定義された**Microsoft.VisualStudio.TextTemplating。\*です。0 dll**、および<xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>で定義された**Microsoft.VisualStudio.TextTemplating.Interfaces。\*です。0 dll**です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [チュートリアル: カスタム テキスト テンプレート ホストの作成](../modeling/walkthrough-creating-a-custom-text-template-host.md)  
 テキスト テンプレートの機能を [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の外部で使用できるようにするカスタム テキスト テンプレート ホストの作成方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:Microsoft.VisualStudio.TextTemplating.ITextTemplatingEngineHost>  
  
## <a name="related-sections"></a>関連項目  
 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)  
 テキスト変換のしくみと、カスタマイズできる部分について説明します。  
  
 [カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 テキスト テンプレート ディレクティブ プロセッサの概要を示します。