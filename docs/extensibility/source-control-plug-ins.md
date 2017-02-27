---
title: "ソース管理プラグイン | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ソース管理プラグインを参照"
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 17
---
# ソース管理プラグイン
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

ソース管理プラグイン SDK のリファレンス セクションには、ソース管理システムと統合することができる完全なインターフェイスの仕様が含まれています。 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 構文と、ソース管理プラグインは、インターフェイスを実装する必要がさまざまな関数とデータ型のセマンティクスを指定して、 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 統合開発環境 \(IDE\) です。  
  
## このセクションの内容  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)  
 ソース管理プラグインの API に準拠するために、ソース管理プラグインが実装する必要は関数について説明します。  
  
 [IDE で実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)  
 特定のコマンドを実行中に、IDE に情報を渡すため、ソース管理プラグインで使用される関数について説明します。  
  
 [列挙子](../extensibility/enumerators.md)  
 ソース管理プラグインがについて知る必要があるソース コントロールのプラグイン API で列挙データ型を一覧表示します。  
  
 [機能フラグ](../extensibility/capability-flags.md)  
 説明、 `SCC_CAP_xxx` プロバイダーの機能を示すフラグ。  
  
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)  
 特定のコマンドのコンテキスト内で使用されるフラグを一覧表示します。  
  
 [エラー コード](../extensibility/error-codes.md)  
 としての関数によって返される一般的なエラー値を一覧表示 `SCCTRN`します。  
  
 [ソース管理プラグインを検索するためのキーとして使用される文字列](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 ソース管理プラグインを検索するレジストリにアクセスするためのキーについて説明します。  
  
 [MSSCCPRJ します。SCC ファイル](../extensibility/mssccprj-scc-file.md)  
 IDE に不透明な情報が含まれるが、バージョン管理内で、ソリューションまたはプロジェクトを検索するソース管理プラグインで使用されるクライアント側のファイルについて説明します。  
  
 [ソース管理プラグインを実装するためのベスト プラクティス](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 ソース管理プラグインの API を実装しているときに注意して重要な技術的なアラームのコレクションを提供します。  
  
 [文字列長の制限](../extensibility/restrictions-on-string-lengths.md)  
 さまざまな機能で使用される文字列の長さ、ソース管理プラグインの API の制限について説明します。  
  
 [用語集](../extensibility/source-control-plug-in-glossary.md)  
 役立つ用語と、ソース管理プラグイン SDK のドキュメントを読み取るためには、その定義を提供します。  
  
 [方法: ソース管理プラグインの互換性に関する警告をオフにします。](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 警告を無効にする方法について説明します。  
  
## 関連項目  
 [Source Control Plug\-in Sample](http://msdn.microsoft.com/ja-jp/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 プラグインのソース管理機能の例を示します。  
  
 [ソース管理プラグインのテストのガイド](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 ソース管理プラグインに関連するテストの手順について説明します。  
  
 [ソース管理プラグインの作成](../extensibility/internals/creating-a-source-control-plug-in.md)  
 ソース管理プラグインを使用しているときに、ソース管理機能を提供するを作成する方法について説明します [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ソース制御ユーザー インターフェイス \(UI\)。  
  
 [Visual Studio SDK のリファレンス](../extensibility/visual-studio-sdk-reference.md)  
 参照トピックの一覧を表示します。