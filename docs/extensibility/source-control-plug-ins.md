---
title: "ソース管理プラグイン |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4f05a0b41a46adfee827f9cc1a36ab7bdd44cd0a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-ins"></a>ソース管理プラグイン
ソース管理プラグイン SDK リファレンス セクションには、により、ソース管理システムと統合する完全なインターフェイスの仕様が含まれています。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]です。 ソース管理プラグインを持つインターフェイスを実装する必要がある、さまざまな関数とデータ型のセマンティクスと構文を指定、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)  
 ソース管理プラグイン API に準拠するために、ソース管理プラグインで実装する必要があります関数を一覧表示します。  
  
 [IDE で実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)  
 ソース管理プラグインは、特定のコマンドを実行中に、IDE に情報を渡しますに使用する関数について説明します。  
  
 [列挙子](../extensibility/enumerators.md)  
 ソース管理プラグインはについて知る必要がありますソース管理プラグイン API で列挙子のデータ型を一覧表示します。  
  
 [機能フラグ](../extensibility/capability-flags.md)  
 について説明します、`SCC_CAP_xxx`はプロバイダーの機能を示すフラグ。  
  
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)  
 特定のコマンドのコンテキスト内で使用されるフラグを一覧表示します。  
  
 [エラー コード](../extensibility/error-codes.md)  
 としての関数によって返される一般的なエラー値を一覧表示`SCCTRN`です。  
  
 [ソース管理プラグインを検索するためのキーとして使用される文字列](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 ソース管理プラグインを検索するレジストリにアクセスするためのキーについて説明します。  
  
 [MSSCCPRJ.SCC File](../extensibility/mssccprj-scc-file.md)  
 IDE に不透明な情報が含まれるが、バージョン管理でソリューションまたはプロジェクトを検索するソース管理プラグインで使用されるクライアント側のファイルについて説明します。  
  
 [ソース管理プラグインを実装するためのベスト プラクティス](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 ソース管理プラグイン API を実装しているときに注意してください重要な技術的なアラームのコレクションを提供します。  
  
 [文字列長の制限](../extensibility/restrictions-on-string-lengths.md)  
 さまざまな関数で使用される文字列の長さで、ソース管理プラグイン API の制限事項について説明します。  
  
 [用語集](../extensibility/source-control-plug-in-glossary.md)  
 便利な用語と、ソース管理プラグイン SDK のドキュメントを読み取るためには、その定義を提供します。  
  
 [方法: ソース管理プラグインの互換性に関する警告をオフにする](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 警告を無効にする方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [ソース管理プラグインのサンプル](http://msdn.microsoft.com/en-us/61de7d2b-71db-451e-8e3e-d41b11c7a4ca)  
 ソース管理プラグインの機能のサンプルを提供します。  
  
 [ソース管理プラグイン向けのテスト ガイド](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 プラグイン ソース管理に関連するテストの手順について説明します。  
  
 [ソース管理プラグインの作成](../extensibility/internals/creating-a-source-control-plug-in.md)  
 使用しているときに、ソース管理機能を提供するソース管理プラグインを作成する方法について説明します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソース制御ユーザー インターフェイス (UI)。  
  
 [Visual Studio SDK のリファレンス](../extensibility/visual-studio-sdk-reference.md)  
 参照トピックの一覧を表示します。