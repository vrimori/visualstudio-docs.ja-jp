---
title: ソース管理プラグイン |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, reference
ms.assetid: 964980ca-21c5-4706-8535-6ea23e1c9cc9
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 4be7a1d0739b6a0c8431d588b05de58a296b809c
ms.sourcegitcommit: 9765b3fcf89375ca499afd9fc42cf4645b66a8a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2018
ms.locfileid: "46495701"
---
# <a name="source-control-plug-ins"></a>ソース管理プラグイン
ソース管理プラグインの SDK のリファレンス セクションには、ソース管理のシステムと統合できるようにする完全なインターフェイスの仕様が含まれています。[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]します。 構文とセマンティクスを持つインターフェイスを実装しなければならないソース管理プラグインのさまざまな関数とデータ型を指定します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]統合開発環境 (IDE) です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ソース管理プラグインの API 関数](../extensibility/source-control-plug-in-api-functions.md)  
 ソース管理プラグイン API に準拠するためにソース管理プラグインによって実装する必要があります関数を一覧表示します。  
  
 [IDE で実装されるコールバック関数](../extensibility/callback-functions-implemented-by-the-ide.md)  
 ソース管理プラグインは、特定のコマンドを実行中に、IDE に情報を渡しますに使用する関数について説明します。  
  
 [列挙子](../extensibility/enumerators.md)  
 ソース管理プラグインが認識する必要がありますソース コントロールのプラグイン API で列挙子のデータ型を一覧表示します。  
  
 [機能フラグ](../extensibility/capability-flags.md)  
 について説明します、`SCC_CAP_xxx`はプロバイダーの機能を示すフラグ。  
  
 [特定のコマンドで使用されるビットフラグ](../extensibility/bitflags-used-by-specific-commands.md)  
 特定のコマンドのコンテキスト内で使用されるフラグを一覧表示します。  
  
 [エラー コード](../extensibility/error-codes.md)  
 としての関数によって返される一般的なエラーの値を一覧表示`SCCTRN`します。  
  
 [ソース管理プラグインを検索するためのキーとして使用される文字列](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)  
 ソース管理プラグインを検索するレジストリにアクセスするためのキーについて説明します。  
  
 [MSSCCPRJ.SCC File](../extensibility/mssccprj-scc-file.md)  
 IDE に不透明な情報を格納しているが、バージョン コントロール内でソリューションまたはプロジェクトを検索するソース管理プラグインによって使用されるクライアント側ファイルについて説明します。  
  
 [ソース管理プラグインを実装するためのベスト プラクティス](../extensibility/best-practices-for-implementing-a-source-control-plug-in.md)  
 ソース管理プラグイン API を実装しているときに覚えておくの重要な技術的な注意事項のコレクションを提供します。  
  
 [文字列長の制限](../extensibility/restrictions-on-string-lengths.md)  
 さまざまな関数で使用される文字列の長さ、ソース管理プラグイン API の制限事項について説明します。  
  
 [用語集](../extensibility/source-control-plug-in-glossary.md)  
 便利な用語と、ソース管理プラグインの SDK ドキュメントを読み取るためには、その定義を提供します。  
  
 [方法: ソース管理プラグインの互換性に関する警告をオフにする](../extensibility/how-to-turn-off-compatibility-warnings-for-source-control-plug-ins.md)  
 警告を無効にする方法について説明します。  
  
## <a name="related-sections"></a>関連項目  
 [ソース管理プラグインのサンプル](https://www.microsoft.com/download/details.aspx?id=55984)  
 ソース管理プラグインの機能のサンプルを提供します。  
  
 [ソース管理プラグイン向けのテスト ガイド](../extensibility/internals/test-guide-for-source-control-plug-ins.md)  
 プラグイン ソース管理に関連するテストの手順について説明します。  
  
 [ソース管理プラグインの作成](../extensibility/internals/creating-a-source-control-plug-in.md)  
 使用しているときに、ソース管理機能を提供するソース管理プラグインを作成する方法について説明します、[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]ソース制御ユーザー インターフェイス (UI)。  
  
 [Visual Studio SDK のリファレンス](../extensibility/visual-studio-sdk-reference.md)  
 参照トピックの一覧を表示します。