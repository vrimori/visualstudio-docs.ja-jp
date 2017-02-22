---
title: "IDE で実装されるコールバック関数 | Microsoft Docs"
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
  - "ソース管理プラグインをコールバック関数"
  - "コールバック関数、ソース管理プラグイン"
ms.assetid: 4a8833f0-6ac0-4ea7-9400-8275aa991468
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# IDE で実装されるコールバック関数
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

統合することとして可能な限りおよび統一されたエンド ユーザー エクスペリエンスを提供するシームレスな統合開発環境 \(IDE\)、ソース管理プラグイン使用できます、IDE によって実装されるコールバック関数。 プラグインを呼び出せるこれらの関数、IDE に情報を渡すのソース管理操作中に適切なときにIDE では、埋め込みのネイティブ UI 要素としてこの情報を表示できます。 ユーザーは、プラグイン採用独自の UI 場合よりも、このシナリオでは、断片化のエクスペリエンスを持ちます。  
  
 必須ヘッダー ファイルは、scc.h です。 既定の場所は、\\Program Files\\VSIP 8.0\\EnvSDK\\common\\inc\\ です。 \\Program Files\\VSIP にソース コントロールのプラグイン サンプルを持っている VSIP フォルダーにも 8.0\\MSSCCI\\ です。  
  
## このセクションの内容  
 [LPTEXTOUTPROC](../extensibility/lptextoutproc.md)  
 によって使用されているコールバック関数を記述 [SccOpenProject](../extensibility/sccopenproject-function.md) IDE によってプラグインのソース管理からのメッセージを表示します。  
  
 [POPLISTFUNC](../extensibility/poplistfunc.md)  
 によって使用されているコールバック関数を記述 [SccPopulateList](../extensibility/sccpopulatelist-function.md) IDE がない場合は、使用するには、ソース管理プラグイン ファイルのバージョン管理の完全な一覧など、情報を完全にアクセスします。  
  
 [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)  
 によって使用されているコールバック関数の説明、 [SccQueryChanges](../extensibility/sccquerychanges-function.md) 操作します。  
  
 [POPDIRLISTFUNC](../extensibility/popdirlistfunc.md)  
 によって使用されているコールバック関数の説明、 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md) 操作します。  
  
 [OPTNAMECHANGEPFN](../extensibility/optnamechangepfn.md)  
 呼び出しで設定するコールバック関数の説明、 [SccSetOption](../extensibility/sccsetoption-function.md) ソース管理プラグインの名前の変更を元に、IDE を通信できるようにします。  
  
## 関連項目  
 [SccOpenProject](../extensibility/sccopenproject-function.md)  
 プロジェクトを開きます。  
  
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)  
 現在の状態のファイルの一覧を調べます。 さらに、使用、 `pfnPopulate` ファイルに使用される条件に一致しない場合、呼び出し元に通知するため、 `nCommand`です。  
  
 [SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)  
 ディレクトリと、プロジェクトまたはソース管理下にあるプロジェクト内のファイルの一覧を調べます。 各ディレクトリとファイル名が検出されましたが、コールバック関数に渡されます。  
  
 [SccQueryChanges](../extensibility/sccquerychanges-function.md)  
 ファイルの一覧に対して行った名の変更を検証します。 各ファイル名は、その変更の状態とコールバック関数に渡されます。  
  
 [SccSetOption](../extensibility/sccsetoption-function.md)  
 さまざまなオプションを設定します。 各オプションが始まる `SCC_OPT_xxx` おり、独自に定義された値のセットです。  
  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)  
 ソース管理プラグイン SDK のリファレンス セクションの内容について説明します。