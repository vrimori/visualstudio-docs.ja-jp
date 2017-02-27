---
title: "T4 テキスト変換のカスタマイズ | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "テキスト テンプレート, API"
  - "テキスト テンプレート, カスタム ホスト"
ms.assetid: 62cd9a3c-a6e1-4b29-93f5-f2a0cf47dc92
caps.latest.revision: 28
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 28
---
# T4 テキスト変換のカスタマイズ
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

テキスト テンプレートは、変換プロセスを通じてプログラム コードやその他のテキスト ファイルを生成できる [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] の機能です。  [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] を使用すると、テキスト テンプレート ディレクティブ プロセッサまたはテキスト テンプレート ホストをカスタマイズすることによって、既定のテンプレート変換プロセスを拡張することができます。  
  
## このセクションの内容  
 [テキスト テンプレート変換プロセス](../modeling/the-text-template-transformation-process.md)  
 テキスト変換のしくみのほか、テンプレート ホストとディレクティブ プロセッサの役割について説明します。  
  
 [カスタム T4 テキスト テンプレート ディレクティブ プロセッサの作成](../modeling/creating-custom-t4-text-template-directive-processors.md)  
 ディレクティブ プロセッサは、テンプレート内のディレクティブ \(`<#@template#>.` など\) を処理します。これはテンプレートのコンパイル中に実行され、アセンブリやその他のリソースを読み込むことができます。  実行時にリソースを読み込むコードを挿入することもできます。  独自のディレクティブ プロセッサを定義することによって、テンプレートを単純化できます。  
  
 [VS 拡張機能内でのテキスト変換の呼び出し](../modeling/invoking-text-transformation-in-a-vs-extension.md)  
 メニュー コマンドやイベント ハンドラーなどの [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 拡張機能を作成する場合は、拡張機能でテキスト テンプレート サービスを使用してテキスト テンプレートを変換できます。  Session オブジェクトを使用してパラメーター データをテンプレートに渡し、`<#@parameter#>` ディレクティブを使用してテンプレート内から値を取得できます。  
  
 [カスタム ホストを使用したテキスト テンプレートの処理](../modeling/processing-text-templates-by-using-a-custom-host.md)  
 ホストは、テキスト テンプレートのコードが実行されたとき、外部ファイルやアプリケーションの状態へのアクセスを可能にします。  たとえば、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] でテキスト変換を実行するホストは、ソリューション エクスプローラーへのアクセスを提供できます。  また、エラー メッセージ ウィンドウにエラーを表示することもできます。  テキスト変換を別のコンテキストで実行する必要がある場合は、そのコンテキストで利用できるサービスへのアクセスを可能にする独自のホストを定義できます。  
  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 拡張機能を作成する場合は、独自のホストを作成するのではなく、既存のテキスト変換サービスを使用することを検討します。  詳細については、「[VS 拡張機能内でのテキスト変換の呼び出し](../modeling/invoking-text-transformation-in-a-vs-extension.md)」を参照してください。  
  
## 関連項目  
 [T4 テキスト テンプレートの作成](../modeling/writing-a-t4-text-template.md)  
  
 テキスト テンプレートのディレクティブと制御ブロックの構文について説明します。