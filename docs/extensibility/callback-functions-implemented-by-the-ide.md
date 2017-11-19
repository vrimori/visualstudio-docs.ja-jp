---
title: "IDE によって実装されているコールバック関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- source control plug-ins, callback functions
- callback functions, source control plug-ins
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: "24"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fbc71942a87685a4011b13d1054c4855a5e18012
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2017
---
# <a name="callback-functions-implemented-by-the-ide"></a>IDE によって実装されているコールバック関数
統合してには、、統合されたエンド ユーザー エクスペリエンスを提供できるだけシームレスな統合開発環境 (IDE) ソース管理プラグイン使用できますは IDE によって実装されるコールバック関数。 プラグインを呼び出せるこれらの関数、IDE に情報を渡すのソース管理操作中に適切なタイミングでIDE では、ネイティブ UI に埋め込まれた要素として、この情報を表示できます。 ユーザーは、プラグイン採用独自の UI 場合よりも、このシナリオでは、断片化のエクスペリエンスを持ちます。  
  
 必須ヘッダー ファイルは、scc.h です。 既定の場所は \Program Files\VSIP 8.0\EnvSDK\common\inc\\です。 \Program Files\VSIP 8.0\MSSCCI にソース管理プラグインのサンプルを持っている VSIP フォルダーにも\\します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 によって使用されているコールバック関数の説明[SccOpenProject](../extensibility/sccopenproject-function.md) IDE を介してプラグイン ソース管理からメッセージを表示します。  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 によって使用されているコールバック関数の説明[SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE がいないときに、ソース管理プラグインのバージョン管理下にあるファイルの完全な一覧でのみ使用可能な情報を完全にアクセスします。  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 によって使用されているコールバック関数の説明、 [SccQueryChanges](../extensibility/sccquerychanges-function.md)操作します。  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 によって使用されているコールバック関数の説明、 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)操作します。  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 コールバック関数への呼び出しによって設定について説明します、 [SccSetOption](../extensibility/sccsetoption-function.md)名の変更は、IDE にバックアップを通信するためにプラグイン ソース管理を有効にします。  
  
## <a name="related-sections"></a>関連項目  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 プロジェクトを開きます。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 現在の状態のファイルの一覧を調べます。 さらに、使用、`pfnPopulate`ファイルに使用される条件に一致しない場合、呼び出し元に通知する関数、`nCommand`です。  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 ディレクトリと、プロジェクトまたはソース管理下にあるプロジェクト内のファイルの一覧を調べます。 検出された各ディレクトリとファイル名は、コールバック関数に渡されます。  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 ファイルの一覧に加えられた名の変更を調べます。 各ファイル名は、その状態の変更とコールバック関数に渡されます。  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 さまざまなオプションを設定します。 各オプションから始まります`SCC_OPT_xxx`おり、独自の値の定義済みセットです。  
  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)  
 ソース管理プラグイン SDK のリファレンスのセクションの内容について説明します。