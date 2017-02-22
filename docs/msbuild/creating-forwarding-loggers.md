---
title: "転送 logger の作成 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, 転送ロガー"
  - "MSBuild, ログ記録"
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# 転送 logger の作成
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

転送 logger では、マルチプロセッサ システムでプロジェクトをビルドするとき、監視の対象とするイベントを選択できるため、ログの効率を高めることができます。  転送 logger を有効にすることにより、不要なイベントによる中心 logger の過負荷、ビルドの低速化、およびログの煩雑化を回避できます。  
  
 転送 logger を作成するには、<xref:Microsoft.Build.Framework.IForwardingLogger> インターフェイスを実装してそのメソッドを手動で実装するか、<xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> クラスとその定義済みメソッドを使用します。  ほとんどのアプリケーションでは、後者で十分です。  
  
## イベントの登録とイベントへの応答  
 転送 logger は、セカンダリ ビルド エンジン \(マルチプロセッサ システムでのビルドにおいてメイン ビルド プロセスによって作成されるワーカー プロセス\) から報告されるビルド イベントの情報を収集します。  イベントを受け取ると、転送 logger は指定された条件に基づいて中央 logger に転送するイベントを選択します。  
  
 監視の対象とするイベントを処理するためには、転送 logger を登録する必要があります。  イベントを処理する転送 logger を登録するためには、logger において <xref:Microsoft.Build.Utilities.Logger.Initialize%2A> メソッドをオーバーライドする必要があります。  このメソッドには、オプションのパラメーターである `nodecount` が追加されました。このパラメーターをシステムのプロセッサ数に設定できます   \(既定値は 1 です\)。  
  
 監視できるイベントの例として、<xref:Microsoft.Build.Framework.IEventSource.TargetStarted>、<xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>、<xref:Microsoft.Build.Framework.IEventSource.ProjectFinished> などがあります。  
  
 マルチプロセッサ環境では、イベント メッセージが誤った順序で受信される可能性があります。  そのため、転送 logger 内のイベント ハンドラーには、イベントを評価し、どのイベントをリダイレクターに渡して中心 logger に転送するかを判断する機能を組み込む必要があります。  これを行うには、各メッセージにアタッチされた <xref:Microsoft.Build.Framework.BuildEventContext> クラスを使用します。このクラスによって、転送が必要なイベントを特定し、その名前を <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> クラス \(またはそのサブクラス\) に渡すことができます。  このメソッドを使用した場合は、それ以外にイベントを転送するためのコーディングを行う必要はありません。  
  
## 転送 logger の指定  
 転送 logger をアセンブリにコンパイルした後で、[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] に対してビルド プロセスで転送 logger を使用するように指定する必要があります。  そのためには、MSBuild.exe に`/FileLogger`、`/FileLoggerParameters`、`/DistributedFileLogger` の各スイッチを指定します。  `/FileLogger` スイッチは、logger が直接アタッチされていることを MSBuild.exe に通知します。`/DistributedFileLogger` スイッチは、ノードごとにログ ファイルが存在することを示します。  転送 logger にパラメーターを設定するには、`/FileLoggerParameters` スイッチを使用します。  上記およびその他の MSBuild.exe スイッチの詳細については、「[Command\-Line Reference](../msbuild/msbuild-command-line-reference.md)」を参照してください。  
  
## マルチプロセッサ対応の logger  
 マルチプロセッサ システムでプロジェクトをビルドする場合、各プロセッサからのビルド メッセージが自動的に一貫した順序でインタリーブされるわけではありません。  したがって、各メッセージにアタッチされる <xref:Microsoft.Build.Framework.BuildEventContext> クラスを使用して、メッセージ グループ化の優先順位を定義する必要があります。  マルチプロセッサでのビルド処理の詳細については、「[マルチプロセッサ環境でのログ](../msbuild/logging-in-a-multi-processor-environment.md)」を参照してください。  
  
## 参照  
 [ビルド ログの取得](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [ビルド ロガー](../msbuild/build-loggers.md)   
 [マルチプロセッサ環境でのログ](../msbuild/logging-in-a-multi-processor-environment.md)