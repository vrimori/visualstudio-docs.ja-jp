---
title: "ソース管理プラグイン API 関数 |Microsoft ドキュメント"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: source control plug-ins, functions
ms.assetid: 4b0536dd-4f92-4ef2-9031-4548281f37aa
caps.latest.revision: "19"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: beaab13c76b3d50f97662e66c1f72dc83161e96d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="source-control-plug-in-api-functions"></a>ソース管理プラグイン API 関数
ソース コントロールのプラグイン API は、次の関数は、ソース管理プラグインに従ってこの API によって実装する必要がありますを提供します。 ビット フラグに関連付けられている各関数とセマンティクスのシグネチャとその他のパラメーターは、このリファレンスで詳しく説明します。  
  
## <a name="initialization-and-housekeeping-functions"></a>初期化およびハウスキーピング関数  
  
|関数|説明|  
|--------------|-----------------|  
|[SccCloseProject](../extensibility/scccloseproject-function.md)|プロジェクトを閉じます。|  
|[SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)|指定したコマンドの詳細設定オプションのユーザーに求めます。|  
|[SccGetVersion](../extensibility/sccgetversion-function.md)|プラグイン ソース管理のバージョンを返します。|  
|[SccInitialize](../extensibility/sccinitialize-function.md)|ソース管理プラグインを初期化します。 プラグインのインスタンスごとに 1 回呼び出されます。|  
|[SccOpenProject](../extensibility/sccopenproject-function.md)|プロジェクトを開きます。|  
|[SccSetOption](../extensibility/sccsetoption-function.md)|さまざまなオプションを設定するために使用するジェネリック関数。 各オプションから始まります`SCC_OPT_xxx`おり、独自の値の定義済みセットです。|  
|[SccUninitialize](../extensibility/sccuninitialize-function.md)|ときに、ソース管理プラグインは、接続する必要があります。 1 回呼び出されます。|  
  
## <a name="core-source-control-functions"></a>主要なソース管理機能  
  
|関数|説明|  
|--------------|-----------------|  
|[SccAdd](../extensibility/sccadd-function.md)|ソース管理システムへの完全修飾パス名で指定されたファイルの配列を追加します。|  
|[SccAddFromScc](../extensibility/sccaddfromscc-function.md)|ソース管理システムに既に存在するファイルを参照することができ、現在のプロジェクトの場合は、これらのファイル一部します。|  
|[SccCheckin](../extensibility/scccheckin-function.md)|ファイルの配列を確認します。|  
|[SccCheckout](../extensibility/scccheckout-function.md)|チェック アウトする、ファイルの配列。|  
|[SccDiff](../extensibility/sccdiff-function.md)|完全修飾パス名とソース管理下にあるバージョンで指定されたローカル ユーザーのファイル間の相違点を示しています。|  
|[SccGet](../extensibility/sccget-function.md)|一連のファイルの読み取り専用コピーを取得します。|  
|[SccGetEvents](../extensibility/sccgetevents-function.md)|呼び出し元がに関して寄せられるファイルの状態を確認 (を介して`SccQueryInfo`)。|  
|[SccGetProjPath](../extensibility/sccgetprojpath-function.md)|ソース管理プラグインにとって意味があるプロジェクトのパスをユーザーに確認するプラグインをによりします。|  
|[SccHistory](../extensibility/scchistory-function.md)|完全修飾のローカル ファイル名の配列の履歴を表示します。|  
|[SccPopulateList](../extensibility/sccpopulatelist-function.md)|現在の状態のファイルの一覧を調べます。 さらに、使用、`pfnPopulate`ファイルに使用される条件に一致しない場合、呼び出し元に通知する関数、`nCommand`です。|  
|[SccProperties](../extensibility/sccproperties-function.md)|完全修飾ファイルのプロパティを示しています。|  
|[SccQueryInfo](../extensibility/sccqueryinfo-function.md)|現在の状態の完全修飾ファイルの一覧を調べます。|  
|[SccRemove](../extensibility/sccremove-function.md)|ソース管理システムから完全修飾ファイルの配列を削除します。|  
|[SccRename](../extensibility/sccrename-function.md)|ソース管理システムで新しい名前を指定されたファイルの名前を変更します。|  
|[SccRunScc](../extensibility/sccrunscc-function.md)|さまざまなソース管理システムの機能にアクセスします。|  
|[SccUncheckout](../extensibility/sccuncheckout-function.md)|ファイルの配列のチェック アウトを元に戻します。|  
  
## <a name="functions-that-support-additional-capability-version-12-of-the-source-control-plug-in-api"></a>追加機能 (ソース コントロールのプラグイン API のバージョン 1.2) をサポートする関数  
 このグループの関数では、ソース管理プラグイン API のバージョン 1.2 に含まれる追加の機能を定義します。 高度なソース管理機能および機能へのアクセスを提供します。  
  
|関数|説明|  
|--------------|-----------------|  
|[SccBeginBatch](../extensibility/sccbeginbatch-function.md)|バッチ操作を開始します。|  
|[SccCreateSubProject](../extensibility/scccreatesubproject-function.md)|既存の親プロジェクトの下にある指定された名前と、サブプロジェクトを作成します。|  
|[SccDirDiff](../extensibility/sccdirdiff-function.md)|完全修飾パス名とソース管理データベースの場所で指定されたローカル ユーザーのディレクトリの違いを示しています。|  
|[SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)|現在の状態の完全修飾ディレクトリの一覧を調べます。|  
|[SccEndBatch](../extensibility/sccendbatch-function.md)|バッチ操作を終了します。|  
|[SccGetParentProjectPath](../extensibility/sccgetparentprojectpath-function.md)|(プロジェクトが存在する必要があります)、指定されたプロジェクトのパスの親を返します。|  
|[SccIsMultiCheckoutEnabled](../extensibility/sccismulticheckoutenabled-function.md)|ファイルに複数のチェック アウトを許可するかどうかを確認します。|  
|[SccWillCreateSccFile](../extensibility/sccwillcreatesccfile-function.md)|プラグインを作成か MSSCCPRJ を確認します。SCC ファイル。|  
  
## <a name="functions-that-support-advanced-capability-version-13-of-the-source-control-plug-in-api"></a>高度な機能 (ソース コントロールのプラグイン API のバージョン 1.3) をサポートする関数  
 このグループの関数では、ソース管理プラグイン API のバージョン 1.3 に含まれる追加の機能を定義します。 高度なソース管理機能および機能へのアクセスを提供します。  
  
|関数|説明|  
|--------------|-----------------|  
|[SccAddFilesFromSCC](../extensibility/sccaddfilesfromscc-function.md)|ソース管理からファイルの一覧を現在のプロジェクトに追加します。|  
|[SccBackgroundGet](../extensibility/sccbackgroundget-function.md)|ユーザー インターフェイスがない場合、ソース管理からファイルの一覧を取得します。|  
|[SccEnumChangedFiles](../extensibility/sccenumchangedfiles-function.md)|ローカル ファイルとは異なるソース管理内のファイルの一覧を取得します。|  
|[SccGetExtendedCapabilities](../extensibility/sccgetextendedcapabilities-function.md)|ソース管理プラグインでサポートされている拡張機能を指定するフラグを取得します。|  
|[SccGetUserOption](../extensibility/sccgetuseroption-function.md)|ユーザー固有のオプションを取得します。|  
|[SccPopulateDirList](../extensibility/sccpopulatedirlist-function.md)|ディレクトリと、プロジェクトまたはソース管理下にあるプロジェクト内のファイルの一覧を調べます。 検出された各ディレクトリとファイル名は、コールバック関数に渡されます。|  
|[SccQueryChanges](../extensibility/sccquerychanges-function.md)|ファイルの一覧に加えられた名前の変更を調べます。 各ファイル名は、その状態の変更とコールバック関数に渡されます。|  
  
## <a name="requirements"></a>必要条件  
 ヘッダー: scc.h  
  
 (環境 SDK で提供される共通のフォルダーに含まれて、既定では*[ドライブ]*\Program Files\VSIP 8.0\EnvSDK\common\inc; MSSCCI サンプルを使用して、VSIP フォルダーの中でも提供*[ドライブ]*\ProgramFiles\VSIP 8.0\MSSCCI)。  
  
## <a name="see-also"></a>参照  
 [ソース管理プラグイン](../extensibility/source-control-plug-ins.md)   
 [ソース管理プラグインの作成](../extensibility/internals/creating-a-source-control-plug-in.md)